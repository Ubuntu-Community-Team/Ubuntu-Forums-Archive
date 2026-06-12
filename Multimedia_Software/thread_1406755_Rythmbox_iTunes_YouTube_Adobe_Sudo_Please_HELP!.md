---
title: "Rythmbox? iTunes? YouTube? Adobe? Sudo? Please HELP!"
date: 2010-02-14
forum: Multimedia Software
---

### Post by NotGiantPanda on 2010-02-14
Ok.  I am incredibly new to Ubuntu and Linux.  For all my life I've had Windows, although I have dabbled with my brother's Apple Macbook Pro.  Recently my computer got a crippling virus, and I had to have the hard drive wiped -.-' My computer guy told me about how he could install two different operating systems on one computer, and told me all about Linux's strong points.  I loved the virus-free part.  Wonderful.  So I had him do it.  I mostly use the Linux Ubuntu side, but I go on my Windows XP side when I'm typing something or doing something with my printer or for pictures.  It has no anti-virus, and I DO NOT go on the internet for it.  Well, at least I'm not supposed to.  I don't even think I have internet explorer any more. Idk. I have Mozilla Firefox for this Linux side.  Now, my computer guy asked me if I wanted anything to be saved when he wiped the hard drive, and I paid him to keep all of my music files.
My computer guy says my software is "debian Ubuntu Linux v 9.04." I don't think I've installed any new versions, but the annoying update manager thing keeps coming up and says 9.10 is available. Should I install that? Would it make any changes?
Anyway, my true purpose for coming to these forums:  I can't get multimedia to work properly!! :( I have "Rythymbox" for my music player, and I have no clue how to use it with my iPod.  I was able to download a few songs off Limewire and put them on it, and I was able to delete a few songs.  However, there are many songs that AREN'T on my iPod that Rhythmbox likes to say are, and I can't put CD's on it.  Nor can I put some songs I downloaded on it.  It is very frustrating, and I miss iTunes :( So here is one question: How do I download iTunes!? I follow instructions it says on various websites (like eHow) and I even downloaded WINE from the Ubuntu website, and when I go to software sources it does say "WIneHQ - Unbuntu 9.04 "Jaunty Jackalope" and all that jazz that I dont really understand.  But, when I go into that SCARY terminal and enter "winecfg," I get:
owner@owner-desktop:~$ winecfg
The program 'winecfg' is currently not installed.  You can install it by typing:
sudo apt-get install wine
bash: winecfg: command not found
owner@owner-desktop:~$ sudo apt-get install wine
[sudo] password for owner: 
Wtf is this "sudo password?" It won't let me type anything in for it.  What do I do? Is there an easier way to install iTunes on Linux?
I also have an issue with YouTube. I get AWFUL lag, and the videos freeze after a few seconds in. The frames are skippy, I only see about three different ones and then it freezes.  To pause I click the screen, which is very weird, but then it stays like that with the play arrow.  I try to click the play arrow, and nothing happens to it or the video, but then I get skippy and repetitive audio.  I try and pause it and wait for the faded red load bar to show up at all, but it never does, it's just the bright red play one.  I even leave my computer for an hour or so.  Is there any way to fix this problem? Is there any better software I can use?
Also, when I try to watch website videos, like missed episodes of "The Secret Life of the American Teenager" from abcfamily.com, it tells me that I can't watch the videos because I don't have the latest version of adobe.  It gives me a link and I click it, taking me to the adobe flash player download site.  I download it for Linux Ubuntu, and I open it as a package as opposed to saving it.  When it's done downloading, it takes me to a small window with the details and everything, but there is a red error message saying I already have a later version installed. Wtf? I don't have the latest version, but I already have the latest version installed? What do I do? Is there anywhere I can go to check the status and details of my current adobe flash player? Where do I see these things? Once again, I am incredibly new to Linux and I don't really know how to work it...
So, these are my current issues. I'm almost positive I'll run into more, but I'm trying to take these things one step at a time. I want to keep Linux, and I want to get better at using it, ao please don't tell me I'm out of luck... As a girl I tried to include as much detail as possible, so sorry if this was a little bit of a read.
Thank you! Please tell me if you have any ideas about my multimedia issues!

---

### Post by flyingsliverfin on 2010-02-14
Sorry, but there is no Itunes for Linux

sudo is needed to give you extra permissions. whenever you use it you will have to enter your password (hence the sudo password) Just enter your password there.

---

### Post by django0909 on 2010-02-14
You'd have probably got a better response typing this in Absolute Beginner Help...

iTunes is a windows program, you can't use it in Ubuntu. Songbird is a good alternative, is free, and should recognise your iPod. If you need help finding linux alternatives to programs, try here: [http://www.linuxalt.com](http://www.linuxalt.com).

sudo means Super User - Do...in literal terms you're asking the computer to perform an action and give full access to the machine whilst doing so. When you type in your password you won't see anything, but it is there, just type and hit return.

I'd be a bit worried if your computer guy tells you you have Debian Ubuntu, it would be Debian, or Ubuntu, not both.

Might I suggest someone moves this to Absolute Beginner, so the OP can get more help?

---

### Post by nothingspecial on 2010-02-14
Your computer guy should have given you an administrative password.

Open a terminal and type```


sudo apt-get install ubuntu-restricted-extras
```

When it asks for the password use the one you log on with.

If that doesn`t work post back.

---

### Post by sailthesea on 2010-02-14
Hello and welcome:)

You have a great many questions and I'm sure I don't have all the answers
but I will try and give you a start and other users will fill in the rest
[PHP]
My computer guy says my software is "debian Ubuntu Linux v 9.04." I don't think I've installed any new versions, but the annoying update manager thing keeps coming up and says 9.10 is available. Should I install that? Would it make any changes?[/PHP]

Don't upgrade or even update for now otherwise the "Scary sudo thing" will be after you;)

Seriously though, take the time to look at ways of doing what you want with media and your iPod A good place to start is looking at the "sticky" threads that are at the top of each subforum page covering everything from basic terminal command (sudo again) to syncing your pod with open source media players
 If you post some specs about your machine and software it will make it easier to get help

Good luck! (bet audiomick got in before me again!)

---

### Post by localhost8080 on 2010-02-14
if I were you I would install the update to 9.10!
the sudo password is the main password for the 'root' user - the root user is the one that can hose your system if you dont know what you are doing!
but yeah, download and install all the updates for your system - the pace of development on linux is very fast - its not like windows - with windows they only bring out a newer version every 5 or so years, with linux they bring out a completely new version almost every day. if something doesnt work today, chances are that in a couple of months it will - ipod support has improved vastly since 9.04 so again, my advice is to install all the updates =)

---

### Post by 2hot6ft2 on 2010-02-14
> **NotGiantPanda said:**
> 
My computer guy says my software is "debian Ubuntu Linux v 9.04." I don't think I've installed any new versions, but the annoying update manager thing keeps coming up and says 9.10 is available. Should I install that? Would it make any changes?
I always prefer a clean install after backing up "home" and then restoring it so I still have my settings. So I'll wait for someone that upgrades to jump in on that one.
> **NotGiantPanda said:**
> I have "Rythymbox" for my music player, and I have no clue how to use it with my iPod.  I was able to download a few songs off Limewire and put them on it, and I was able to delete a few songs.  However, there are many songs that AREN'T on my iPod that Rhythmbox likes to say are, and I can't put CD's on it.  Nor can I put some songs I downloaded on it.
To install gtkpod-aac for managing your iPod just open a terminal
Applications > Accessories > Terminal
and use:
```
sudo apt-get install gtkpod-aac
```
Hit Enter
**Enter your password (the same one you use to log into ubuntu) which wont be displayed and hit Enter**
Wait for it to finish and it will be in
Applications > Sound and Video > gtkpod iPod Manager
> **NotGiantPanda said:**
> 
[sudo] password for owner: 
Wtf is this "sudo password?" It won't let me type anything in for it.  What do I do?
**Enter your password (the same one you use to log into ubuntu) which wont be displayed and hit Enter**

There's a start

---

