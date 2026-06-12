---
title: "Help a newbie!! Terminal is not opening!"
date: 2022-11-28
forum: MINT
---

### Post by ezowyn on 2022-11-28
Hello everyone!

I recently downloaded linux mint 21 Vanessa to my laptop. After the installations of my programs ( brave web browser, discord, spotify, pycharm, python 11), I closed the terminal and when I need it I wanted to open it again but it didn't open. So I restarted the mint but than things got worse. 

The menu bar was gone, terminal was not opening in anyways (except ctrl alt f1) and  the mouse pointer was changed (became black cross sign like x)

I consulted to someone and he suggested me to do some stuff (I donno I am a total newbie) than I wrote this code: 

sudo pkill -u ezowyn 

Logins screen opened. Than I changed software environment from Cinnamon (default) to Cinnamon (software rendering) 

Now my desktop came back. Still terminal is not working (except ctrl alt f1). Other apps look okay tho.
 Edit: Settings and System Reports are not opening too.

Can someone help me??? And does changing the desktop environment ok? Enlighten me!

---

### Post by slickymaster on 2022-11-28
Thread moved to **MINT** for a better fit

---

### Post by ezowyn on 2022-11-28
ok thanks

---

### Post by The Cog on 2022-11-28
I think that probably needs reinstalling. I'm very suspicious of your having installed some applications. Was it working OK before you installed them (I'm guessing yes)?
How did you install those other applications? Particularly, pycharm and "python 11"?

---

### Post by TheFu on 2022-11-28
Python is used in the system for all sorts of things.  Replacing the system version of python with any other version is a way to break the entire OS.  That's why we have virtual environments to have multiple versions of python installed, as needed, but not touch what the OS is using.

I've not used Mint in about 6 yrs and only for a few days back then.  Many friends use it and like it, so if anything bad is happening, I suspect it is either hardware incompatibility or something manually done that broke the system.

BTW, you should always look up every command BEFORE running them.  Learn to read the man-pages.  It is a skill and initially, it will be difficult, but once you get the hang of it, you'll see the genius in how manpages are organized like a front-page news paper article.  The stuff at the top provides the most important information. To learn more, read farther down.  All options should be clearly described in a manpage.

---

### Post by ezowyn on 2022-11-28
@The Cog
Yeah as you suspect it, after installing python 11 things happened. I didn't have a slightest clue that linux has on its own python. How can I take those back or re install things to recover?

---

### Post by ezowyn on 2022-11-28
> **TheFu said:**
> Python is used in the system for all sorts of things.  Replacing the system version of python with any other version is a way to break the entire OS.  That's why we have virtual environments to have multiple versions of python installed, as needed, but not touch what the OS is using.

I've not used Mint in about 6 yrs and only for a few days back then.  Many friends use it and like it, so if anything bad is happening, I suspect it is either hardware incompatibility or something manually done that broke the system.

BTW, you should always look up every command BEFORE running them.  Learn to read the man-pages.  It is a skill and initially, it will be difficult, but once you get the hang of it, you'll see the genius in how manpages are organized like a front-page news paper article.  The stuff at the top provides the most important information. To learn more, read farther down.  All options should be clearly described in a manpage.


Ohhh, this is really bad than. When I install pycharm, I realized it uses python 10 and got confused. I thought why it doesn't have python 11 so I wanted to update but obviously I messed up. lol Is there a way for me to change it back?

---

### Post by TheFu on 2022-11-28
> **ezowyn said:**
> Ohhh, this is really bad than. When I install pycharm, I realized it uses python 10 and got confused. I thought why it doesn't have python 11 so I wanted to update but obviously I messed up. lol Is there a way for me to change it back?

Sure. Restore from the full system backup you made before this foolishness happened.  ;)
Otherwise, nope. Do a fresh install.  sudo is very powerful. Don't use it when you don't know what you are doing.  It will let you shoot yourself in the toe, foot, thigh, chest, or head.  Your choice, since you are the admin.  Power to the people!   

Unix can't tell of what you are asking to do is stupid or genius.  Sometimes both apply. ;)  As the admin, it is up to you to decide.

---

### Post by The Cog on 2022-11-28
TheFu is right, as usual. Reinstall from scratch is the way to go. Mint has a built-in backup system called timeshift, but with python broken it won't be able to restore, and I guess you didn't back up anyway.

Before installing stuff not from Mint's repository, check by asking the forums (either here or Mint's own forum). I don't think there is any such thing as python 10 or 11. Vanessa comes with python3, and has python2 in the repository if you have a particular need for that. For a beginner, I would strongly advise sticking with whatever is in the official repositories.

P.S. If you're just setting out to learn python, then I recommend using the python3 that comes installed as part of the Ubuntu or Mint system. It will likely be a long time before you find a need for a different version for any reason

---

### Post by ezowyn on 2022-11-28
Thank you both of you!! I'll reinstall the mint. While we are here, could you recommend me a tutorial or video series to learn more about linux :D If things go like that, I'll be reinstalling a lot I guess :D

---

### Post by TheFu on 2022-11-28
> **ezowyn said:**
> Thank you both of you!! I'll reinstall the mint. While we are here, could you recommend me a tutorial or video series to learn more about linux :D If things go like that, I'll be reinstalling a lot I guess :D

Depends on your goal.  Back when I was teaching Linux, I was asked that question all the time.  My answer is here: [https://blog.jdpfu.com/2017/03/31/learning-linux-condensed](https://blog.jdpfu.com/2017/03/31/learning-linux-condensed) and
[https://blog.jdpfu.com/2014/12/28/learning-linux](https://blog.jdpfu.com/2014/12/28/learning-linux)

But it depends on your goal.  End-users need to know much less than programmers or admins.  And admins need to know different stuff than programmers.

The long time Linux users have decades of experience, so take our suggestions for current stuff as guesses.  Around 10 yrs ago, I worked through a full Beginning Linux course in an afternoon because I was bored.  So, depending on the style of learning that works best for you, there are very different answers.  I like the learn the basics via the "it sucks method of reading a book" first, followed by the "scratch a personal itch" method where I try to setup stuff that I need myself.  I find listening to videos much too slow and boring.

If I had any recommendations, it is to 
a) learn Linux/Unix file permissions
b) learn to use the CLI/shell.  GUIs seem to change every 3 yrs, but the CLI is basically the same since 1990. Learn it and you'll be able to do desktops, servers, and not need to relearn how-to every few years, since it doesn't change much.
c) learn to use tab-completion in your shell.  This is also known as command-completion.  

Perhaps the tab-completion should be first. [https://youtu.be/UH4rNs_-2is](https://youtu.be/UH4rNs_-2is) is a 30 second intro to tab-completion.  It isn't just for files and directories, but for commands and command options too.  I use it so much that I don't even think about it and haven't since around 1995 when it was first available in tcsh. The default shell, bash, supports it nicely.

---

### Post by ezowyn on 2022-11-28
Thank you for your time TheFu. I'll check those resources.

---

### Post by yancek on 2022-11-29
The link below has an installation guide for Linux Mint and if you scroll down the page, you will find another link where you can download a User Guide.

[https://www.linuxmint.com/documentation.php](https://www.linuxmint.com/documentation.php)

---

### Post by ezowyn on 2022-11-29
Thank you yancek!

---

