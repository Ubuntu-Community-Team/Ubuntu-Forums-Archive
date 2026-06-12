---
title: "Compiz and ubuntu 11.04 - Eyecandy not working"
date: 2011-08-03
forum: Multimedia Software
---

### Post by dmsgg on 2011-08-03
Hello. 

I'm a User of Ubuntu for approximately a little more than a year now. One of the things I love is that the visual and 3D effects of "compiz config setting manager" are so extremely cool that when you put a well configured ubuntu os with compiz a Mac and a PC together and that you start showing off your effects, the other two computers just have to shut up XD

BUT, I have a big problem. I bought a new laptop and I installed ubuntu 11.04 and compiz (I think compiz was already there, but I did sudo apt-get before knowing that) and the 3D effects DONT WORK :'(

I still think ubuntu is pretty good OS, but without the visual effects its just not the same !!!!

Could you tell me what could possibly be the problem, I have no idea where to start ???

More infos about my laptop and ubuntu :

Ubuntu 11.04 - 64 bits
I used the live CD to install "alongside Windows 7"
Ubuntu 11.04 is in my second disk drive, Windows 7 (64 bits) is in my first disk drive
Compuetr : Asus - Laptop - K73SV-TY083V 
Intel Core i5 2410M (Sandy Bridge) - 
4096 Mo
NVIDIA GeForce GT 540M 
17.3 LED HD+ (1600x900)
Windows 7 Home Premium 64

Actually this is my computer : [http://www.magicpc.fr/Ordinateur_portable/Asus_K73SV-TY083V/p-20517/?ekid=52755125b44422ae215b2b24743dd0c1](http://www.magicpc.fr/Ordinateur_portable/Asus_K73SV-TY083V/p-20517/?ekid=52755125b44422ae215b2b24743dd0c1)

Do you have any idea what could be the problem ??? THX, I really appreciate... I need to show my two roomates (windows fan and mac fan) that ubuntu ROCKS

---

### Post by pages on 2011-08-03
I had similar problems with my laptop bought the same one as you i think.

[http://ubuntuforums.org/showthread.php?t=1684701](http://ubuntuforums.org/showthread.php?t=1684701)

Apparently the software might be windows only. Although this was a few months ago so things may have changed.

---

### Post by fyfe54 on 2011-08-03
I found this very useful.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by realzippy on 2011-08-03
> **dmsgg said:**
> 

Do you have any idea what could be the problem ??? 

Optimus is your problem:

[http://ubuntuforums.org/showthread.php?p=10304516#post10304516](http://ubuntuforums.org/showthread.php?p=10304516#post10304516)

---

### Post by dmsgg on 2011-08-04
Well, thanks for your help. Indeed it must be the Optimus technology. For what I understood so far I have an integrated intel graphic card and a dedicated Nvidia graphic card that is more powerfull (3d andd stuff). 

Optimus technology changes from one to another when needed (if you run an application that needs the powerfull one it changes to Nvidia and if you run basic "light" applications it uses the intel one. 

However this only works in Windows and Nvidia doesn't have plans to fix this. I found a project called bumblebee that tries to solve the problem (google it). I tried but didn't work. But I will try soon some other options. 

The stange thing is that I got some effects working after a new reinstallation. The only difference withe the first installation (that didnt work) is that in the live CD i didn't enable the options : 

Install updates while installing ubuntu
Install third party software

And the cube kind of worked (with only two sides, not four) but I think metacity stoped working (cause my windows close, minimize and maximize buttons dissapeared and I couldnt mowe my windows anymore)

Anyway, I hadn't give up, I will re-install and re-install until I succeed (Linux is in a different HDD than windows so I cas ess it up, format end reinstall eternally)

I'll keep you posted, but if you find any solution or clues please post them in reply here.

:)

---

### Post by CatKiller on 2011-08-04
> **dmsgg said:**
> The stange thing is that I got some effects working after a new reinstallation. The only difference withe the first installation (that didnt work) is that in the live CD i didn't enable the options : 

Install updates while installing ubuntu
Install third party software

It's the second that's the important one. You definitely mustn't install the proprietary driver, AIUI. It won't work because the driver doesn't know that it's 1996 again. The open source driver will at least let you unleash the awesome power of those Intel graphics until someone can get the hang of Optimus.

> 
And the cube kind of worked (with only two sides, not four) but I think metacity stoped working (cause my windows close, minimize and maximize buttons dissapeared and I couldnt mowe my windows anymore)You weren't using Metacity. You were using Compiz. You didn't have a cube because your workspaces were still in the Desktop Wall configuration. Compiz-decorator does seem to be one of the less robust Compiz plugins. You can restart it to get your window decorations back with ```
compiz-decorator --replace
```

---

### Post by dmsgg on 2011-08-08
Catkiller yo are indeed right. I was not using metacity. In fact I figured it out and I now have the effects of compiz (cube, water, fire, scale, etc) with mu nvidia geforce and optimus. I didnt believe it cause in the net they say it is impossible for the moment but it isn't. 

WHAT DIDNT WORK : 

Intalling third party during ubuntu isntallation
Installing the nvidia driver
Installing bumblebee (but maybe I did something wrong there)

I had to re-install ubuntu like 5 times with different settings, and my friends moqued me but now it is cooler than everything and I can tell my friends : 

"They say I was crazy"

and then laugh histerycally. Anyway, 

"sorry for my bad ortography but I wont apologize :)"

WHAT DID WORK : 

1. Installed ubuntu 11.04 from live CD 
2. Choose option install alongside windows
3. Do not choose "install upgrades" or "install 3rd party software"
4. In login screen choose user then in the bottom bar choose "ubuntu classic"
5. Install via ubuntu software center "ubuntu restricted extras"
6. Install via terminal "sudo apt-get install compizconfig-setting-manager"
7. DO NOT install nvidia drivers or open source equivalent
8. Open compiz and enable the cube. The cube will work but your windows wont (controls disappear)
9. Shutdown computer
10. Login again and choose compiz. Enable the plugins "windows decoration" and "move windows"

VOILA !!!

Hope it helps somebody. Ubuntu rocks but what I really love is the support of the community. Noobs and hardcore geeks working together, lol.

Byeeeee

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

