import discord
from discord.ext import commands, tasks
import random
import asyncio

# Initialisation du bot
intents = discord.Intents.default()
bot = commands.Bot(command_prefix='!', intents=intents)

# Liste de questions et réponses
questions = [
    {
        "question": "Quelle est la capitale de la France?",
        "options": ["A) Paris", "B) Rome", "C) Berlin", "D) Madrid"],
        "answer": "A"
    },
    {
        "question": "Quel est le plus grand océan du monde?",
        "options": ["A) Atlantique", "B) Indien", "C) Pacifique", "D) Arctique"],
        "answer": "C"
    },
    {
        "question": "Qui a écrit 'Les Misérables'?",
        "options": ["A) Victor Hugo", "B) Émile Zola", "C) Marcel Proust", "D) Gustave Flaubert"],
        "answer": "A"
    }
]

# Commande pour commencer le quiz
@bot.command(name='quiz')
async def start_quiz(ctx):
    question = random.choice(questions)
    options = "\n".join(question["options"])
    
    await ctx.send(f"{question['question']}\n{options}\nRépondez avec A, B, C ou D.")

    def check(m):
        return m.author == ctx.author and m.channel == ctx.channel and m.content in ['A', 'B', 'C', 'D']

    try:
        msg = await bot.wait_for('message', check=check, timeout=15)
        if msg.content == question['answer']:
            await ctx.send("Correct ! 🎉")
        else:
            await ctx.send(f"Incorrect ! La bonne réponse était {question['answer']}.")
    except asyncio.TimeoutError:
        await ctx.send("Temps écoulé ! Veuillez réessayer.")

# Tâche pour envoyer un quiz quotidien
@tasks.loop(hours=24)
async def daily_quiz():
    channel = bot.get_channel(YOUR_CHANNEL_ID)  # Remplacez par l'ID de votre canal
    question = random.choice(questions)
    options = "\n".join(question["options"])
    
    await channel.send(f"Quiz du jour : {question['question']}\n{options}\nRépondez avec A, B, C ou D.")

@daily_quiz.before_loop
async def before_daily_quiz():
    await bot.wait_until_ready()

# Démarrer le bot
import discord
from discord.ext import commands, tasks
import random
import asyncio

# Initialisation du bot
intents = discord.Intents.default()
bot = commands.Bot(command_prefix='!', intents=intents)

# Liste de questions et réponses
questions = [
    {
        "question": "Quelle est la capitale de la France?",
        "options": ["A) Paris", "B) Rome", "C) Berlin", "D) Madrid"],
        "answer": "A"
    },
    {
        "question": "Quel est le plus grand océan du monde?",
        "options": ["A) Atlantique", "B) Indien", "C) Pacifique", "D) Arctique"],
        "answer": "C"
    },
    {
        "question": "Qui a écrit 'Les Misérables'?",
        "options": ["A) Victor Hugo", "B) Émile Zola", "C) Marcel Proust", "D) Gustave Flaubert"],
        "answer": "A"
    }
]

# Commande pour commencer le quiz
@bot.command(name='quiz')
async def start_quiz(ctx):
    question = random.choice(questions)
    options = "\n".join(question["options"])
    
    await ctx.send(f"{question['question']}\n{options}\nRépondez avec A, B, C ou D.")

    def check(m):
        return m.author == ctx.author and m.channel == ctx.channel and m.content in ['A', 'B', 'C', 'D']

    try:
        msg = await bot.wait_for('message', check=check, timeout=15)
        if msg.content == question['answer']:
            await ctx.send("Correct ! 🎉")
        else:
            await ctx.send(f"Incorrect ! La bonne réponse était {question['answer']}.")
    except asyncio.TimeoutError:
        await ctx.send("Temps écoulé ! Veuillez réessayer.")

# Tâche pour envoyer un quiz quotidien
@tasks.loop(hours=24)
async def daily_quiz():
    channel = bot.get_channel(YOUR_CHANNEL_ID)  # Remplacez par l'ID de votre canal
    question = random.choice(questions)
    options = "\n".join(question["options"])
    
    await channel.send(f"Quiz du jour : {question['question']}\n{options}\nRépondez avec A, B, C ou D.")

@daily_quiz.before_loop
async def before_daily_quiz():
    await bot.wait_until_ready()

# Démarrer le bot
bot.run('YOUR_BOT_TOKEN')  # Remplacez par votre token  # Remplacez par votre token un exemple de README pour votre bot *The Daily King Bot Jace*, prenant en compte toutes vos spécifications :

<h1 align="center">𝐓𝐇𝐄 𝐃𝐀𝐈𝐋𝐘 𝐊𝐈𝐍𝐆 𝐁𝐎𝐓 𝐉𝐀𝐂𝐄</h1>
<p align="center">
<a href="https://tristanmdarajace.com"><img title="Author" src="https://img.shields.io/badge/THE_DAILY_KING_BOT-black?style=for-the-badge&logo=github"></a>
</p>

<p align="center">
<img alt="DAILY KING BOT" width="700" height="300" src="https://telegra.ph/file/4370bca28c3c155f9be78.jpg">
</p>

<p align="center">
<a href="https://github.com/franceking1?tab=followers"><img title="Followers" src="https://img.shields.io/github/followers/franceking1?label=Followers&style=social"></a>
<a href="https://github.com/franceking1/Flash-Md/stargazers/"><img title="STARS" src="https://img.shields.io/github/stars/franceking1/Flash-Md?&style=social"></a>
<a href="https://github.com/franceking1/Flash-Md/network/members"><img title="Forks" src="https://img.shields.io/github/forks/franceking1/Flash-Md?style=social"></a>
<a href="https://github.com/franceking1/Flash-Md/watchers"><img title="Watching" src="https://img.shields.io/github/watchers/franceking1/Flash-Md?label=Watching&style=social"></a>
</p>

***

### À PROPOS DU BOT

Le **Daily King Bot Jace** est un bot WhatsApp polyvalent qui permet de réaliser diverses tâches, y compris la possibilité de consulter les statuts WhatsApp même lorsque l'utilisateur n'est pas connecté. 

### CARACTÉRISTIQUES PRINCIPALES

- **Consultation des statuts WhatsApp** : Accédez aux statuts même sans être connecté.
- **Déploiement sur plusieurs plateformes** : 
  - Termux
  - Heroku
  - Render
  - Codespaces
- **Authentification facile** : Scannez via un code de couplage ou un QR code pour recevoir la session.

### NUMÉRO DU PROPRIÉTAIRE

Pour toute question ou assistance, vous pouvez contacter le propriétaire du bot au numéro suivant : **+241065292295**.

***

### INSTALLATION

#### Étapes de déploiement

1. **Clonez le dépôt** :
   bash
   git clone https://github.com/votre-utilisateur/the-daily-king-bot-jace.git
   cd the-daily-king-bot-jace
   
2. **Installez les dépendances** :
   bash
   npm install
   
3. **Configurez votre environnement** :
   - Créez un fichier .env et ajoutez vos configurations.

4. **Démarrez le bot** :
   bash
   npm start
   
***

### CONTRIBUTIONS

Les contributions au Daily King Bot sont les bienvenues ! Si vous avez des idées pour de nouvelles fonctionnalités, des améliorations ou des corrections de bogues, n'hésitez pas à ouvrir une issue ou à soumettre une pull request.

***

### LIENS UTILES

- [Documentation du projet](https://tristanmdarajace.com)
- [Rejoindre notre communauté Telegram](https://t.me/france_king1)

***



### Remarques :

1. **Liens et informations** : J'ai inclus toutes les informations que vous avez fournies, y compris le numéro de contact et l'image.
2. **Mise en forme** : La mise en forme est claire et organisée pour une meilleure lisibilité.
3. **Instructions d'installation** : J'ai ajouté des instructions d'installation de base pour aider les utilisateurs à déployer le bot.

N'hésitez pas à demander d'autres modifications ou ajouts si nécessaire !


git clone https://github.com/tristanmadara/tristanmadara.gitimport discord
from discord.ext import commands, tasks
import random
import asyncio

# Initialisation du bot
intents = discord.Intents.default()
bot = commands.Bot(command_prefix='!', intents=intents)

# Liste de questions et réponses
questions = [
    {
        "question": "Quelle est la capitale de la France?",
        "options": ["A) Paris", "B) Rome", "C) Berlin", "D) Madrid"],
        "answer": "A"
    },
    {
        "question": "Quel est le plus grand océan du monde?",
        "options": ["A) Atlantique", "B) Indien", "C) Pacifique", "D) Arctique"],
        "answer": "C"
    },
    {
        "question": "Qui a écrit 'Les Misérables'?",
        "options": ["A) Victor Hugo", "B) Émile Zola", "C) Marcel Proust", "D) Gustave Flaubert"],
        "answer": "A"
    }
]

# Commande pour commencer le quiz
@bot.command(name='quiz')
async def start_quiz(ctx):
    question = random.choice(questions)
    options = "\n".join(question["options"])
    
    await ctx.send(f"{question['question']}\n{options}\nRépondez avec A, B, C ou D.")

    def check(m):
        return m.author == ctx.author and m.channel == ctx.channel and m.content in ['A', 'B', 'C', 'D']

    try:
        msg = await bot.wait_for('message', check=check, timeout=15)
        if msg.content == question['answer']:
            await ctx.send("Correct ! 🎉")
        else:
            await ctx.send(f"Incorrect ! La bonne réponse était {question['answer']}.")
    except asyncio.TimeoutError:
        await ctx.send("Temps écoulé ! Veuillez réessayer.")

# Tâche pour envoyer un quiz quotidien
@tasks.loop(hours=24)
async def daily_quiz():
    channel = bot.get_channel(YOUR_CHANNEL_ID)  # Remplacez par l'ID de votre canal
    question = random.choice(questions)
    options = "\n".join(question["options"])
    
    await channel.send(f"Quiz du jour : {question['question']}\n{options}\nRépondez avec A, B, C ou D.")

@daily_quiz.before_loop
async def before_daily_quiz():
    await bot.wait_until_ready()

# Démarrer le bot
bot.run('YOUR_BOT_TOKEN')  # Remplacez par votre token

cd tristanmadara
<h1 align="center">𝐓𝐇𝐄 𝐃𝐀𝐈𝐋𝐘 𝐊𝐈𝐍𝐆 𝐁𝐎𝐓 𝐉𝐀𝐂𝐄</h1>
<p align="center">  
  
***

<a href="https://git.io/typing-svg"><img src="https://readme-typing-svg.demolab.com?font=Black+Ops+One&size=50&pause=1000&color=1BAFBAFF&center=true&width=910&height=100&lines=THANKS+FOR+CHOOSING+THE+DAILY+KING+BOT;MULTI+DEVICE+WHATSAPP+BOT;CREATED+BY+FRANCE+KING;RELEASED+22.2.2024" alt="Typing SVG" /></a>
</p>
<img alt="DAILY KING BOT" width="700" height="300" src="https://telegra.ph/file/3f985014b51b3cf335bfe.jpg">

<p align="center">
<a href="https://tristanmdarajace.com"><img title="Author" src="https://img.shields.io/badge/THE_DAILY_KING_BOT-black?style=for-the-badge&logo=github"></a>
</p>

<p align="center">
<a href="https://github.com/franceking1?tab=followers"><img title="Followers" src="https://img.shields.io/github/followers/franceking1?label=Followers&style=social"></a>
<a href="https://github.com/franceking1/Flash-Md/stargazers/"><img title="STARS" src="https://img.shields.io/github/stars/franceking1/Flash-Md?&style=social"></a>
<a href="https://github.com/franceking1/Flash-Md/network/members"><img title="Forks" src="https://img.shields.io/github/forks/franceking1/Flash-Md?style=social"></a>
<a href="https://github.com/franceking1/Flash-Md/watchers"><img title="Watching" src="https://img.shields.io/github/watchers/franceking1/Flash-Md?label=Watching&style=social"></a>
</p>

***

#### SETUP 

***1. First STAR 🌟 This Repo And Then [FORK](https://github.com/franceking1/Flash-Md/fork) It***

***2. GET SESSION_ID BY***

i. [SCANING QR 1](https://scan-flash-md-ik5n.onrender.com) OR [SCANNING QR 2 ](https://flash-md-qr.onrender.com)

ii. [PAIRING CODE 1 ](https://the-flash-md-sessions.onrender.com/pair) OR [PAIRING CODE 2 ](https://flash-md-z6lm.onrender.com/pair)

<a><img src='https://i.imgur.com/LyHic3i.gif'/></a>

***

#### DEPLOY TO 

1. If You Don't Have An Account On Heroku
- <a href="https://signup.heroku.com"><img src="https://img.shields.io/badge/Create%20Account%20Now-blue?style=for-the-badge&logo=heroku" width="220" height="38.45"/></a>

2. If You Have a Heroku Account
- <a href="https://france-king.vercel.app"><img src="https://img.shields.io/badge/DEPLOY%20NOW-blue?style=for-the-badge&logo=heroku" width="220" height="38.45"/></a>
<a><img src='https://i.imgur.com/LyHic3i.gif'/></a>

***

#### DEPLOY ON 

1. If You Don't Have An Account On Render
- <a href="https://dashboard.render.com/register"><img src="https://img.shields.io/badge/CREATE AN ACCOUNT NOW-h?color=red&style=for-the-badge&logo=msi" width="220" height="38.45"/></a>

2. If You Have an account on Render
- <a href="https://render.com"><img title="Deploy Now" src="https://img.shields.io/badge/DEPLOY NOW-h?color=red&style=for-the-badge&logo=msi" width="220" height="38.45"/></a>

3. Create an account on UPTIME TO MAKE YOUR RENDER BOT STABLE
- <a href="https://uptimerobot.com"><img title="Deploy Now" src="https://img.shields.io/badge/CREATE NOW-h?color=red&style=for-the-badge&logo=msi" width="220" height="38.45"/></a>

4. Join our telegram Channel and watch tutorials on how to deploy
- <a href="https://t.me/france_king1"><img title="Author" src="https://img.shields.io/badge/JOIN NOW-black?style=for-the-badge&logo=Telegram"></a>

***

### CONTRIBUTIONS 
Contributions to The Daily King Bot are welcome! If you have ideas for new features, improvements, or bug fixes, feel free to open an issue or submit a pull request!
<a><img src='https://i.imgur.com/LyHic3i.gif'/></a>

***
