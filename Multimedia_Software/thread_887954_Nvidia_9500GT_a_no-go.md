---
title: "Nvidia 9500GT a no-go"
date: 2008-08-12
forum: Multimedia Software
---

### Post by Jaxco on 2008-08-12
I have been able to install the drivers but all I get is a black screen when I do.  I have used 173.xx and even the beta 177.xx. I have sniffed all over this site, using a variety of search phrases -no dice same result

My system:

Nforce 4 SLI x16 board
2GB DDR400 in dual channel mode
Opteron 185 (2.6Ghz Dual Core)
PNY 9500GT 512MB of GDDR3
74GB WD Raptor

---

### Post by Jaxco on 2008-08-13
No dice, eh?  :(

---

### Post by Growbag on 2008-08-13
You are being punished because you have such a flashy video card!

Give it to me, and get a cheaper one, that guarantees that it will work ;)

Sorry, I know I'm no help, but I just couldn't resist :D.

:lolflag:

---

### Post by Garratt on 2008-08-13
Go here:

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

and download EnvyNG or:

1. open up synaptic package manager [System>Administration>Synaptic Package Manager].

2. scroll down the left-hand side of the window till you get to get to "Utility" and click it (note this is usually for Ubuntu 7.10, for hardy 8.04 or 8.10 go to the website and get "EnvyNG" as opposed to Envy Legacy(for old ubuntus)).

3. Should be Envy in that, tick the box, then apply changes(if it's not there then go to the website and follow instrucitons).

4. after installation it will be under Applications>System Tools>Envy

5. Click it, and go blah blah next it will uninstall any crappy drivers you have installed incorrectly, then reinstall proper ones over the top.

6. send me $1,000,000.US cause im poor and need to buy blowup dolls. (yes lots of them!)

EDIT: i have a 9600 GT and i thought i had installed the correct drivers and uninstalled the dodgy ones but it still wouldnt work,... until i used this program, now everything works fine and i got sexy animations and stuff and can play every game known to man, and watch hi-def pron!

---

### Post by Growbag on 2008-08-14
> **Garratt said:**
> 6. send me $1,000,000.US cause im poor and need to buy blowup dolls. (yes lots of them!)

lol

Don't waste money on blow up ones, they have real life ones now:

[http://en.wikipedia.org/wiki/Sex_doll](http://en.wikipedia.org/wiki/Sex_doll)

There's a company in the US that makes amazing ones, I'm saving up my pension right now :D

:guitar:

---

### Post by Jaxco on 2008-08-14
EnvyNG was my very first stop for uninstallation and reinstallation.  Interstingly enough, the only 9500 listed in the newer drivers' supported card list is the 9500M GS.  Conspicuously absent is the 9500GT... The 9600GT IS there and it is a much better card than the 9500GT

Guys I truly exhausted myself on this message board, on nvnews (official nvidia forums) 1 guy here claims to have a 9500gt working - i just wanna see it - thats all i am saying lol.

BTW thanks to both of ya!

---

### Post by Growbag on 2008-08-14
Apparently there is a new driver about to be released to fix some issues with KDE4, so maybe that will have support.

Hang in there, there's bound to be a solution just around the corner :).

Also, maybe you could try another distro, see if that is any better.

For newer hardware, maybe Fedora or openSUSE.

---

### Post by Jaxco on 2008-08-14
YEah, the new driver is 177.x  I have already tried it as well :-(  This seems to be a dead-end until Nvidia fixes it, I may trade the card in and pick up a 9800 instead

---

### Post by Jaxco on 2008-08-15
Last call... any ideas folks?

---

### Post by Kubunteando on 2008-08-18
It seems Nvidia has not yet released the driver but it is around the corner:

[http://www.phoronix.com/scan.php?page=news_item&px=NjYyOQ](http://www.phoronix.com/scan.php?page=news_item&px=NjYyOQ)

Once more Linux is in a 2nd row... :-(

---

### Post by gaten on 2008-08-23
I don't know how or why, but I've gotten *two* Nvidia 9500GT cards working in the last couple days. One is a EVGA 512MB ([http://www.newegg.com/Product/Product.aspx?Item=N82E16814130378&nm_mc=AFC-C8Junction&cm_mmc=AFC-C8Junction-_-Video+Cards-_-EVGA-_-14130378](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130378&nm_mc=AFC-C8Junction&cm_mmc=AFC-C8Junction-_-Video+Cards-_-EVGA-_-14130378)) and the other is a Gigabyte 512MB ([http://www.newegg.com/Product/Product.aspx?Item=N82E16814125228&nm_mc=AFC-C8Junction&cm_mmc=AFC-C8Junction-_-Video+Cards-_-GIGABYTE-_-14125228](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125228&nm_mc=AFC-C8Junction&cm_mmc=AFC-C8Junction-_-Video+Cards-_-GIGABYTE-_-14125228)). Here's the odd-should-not-have-worked process I went through.

Installed the EVGA card on my second computer, with 4GB ram and onboard video card. After booting into Hardy for the first time, downloaded the Nvidia drivers from their site and followed the instructions on the Ubuntu NvIdia Binary Howto [(https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")). Rebooted the computer, every thing worked like a dream. I'm running WoW with full settings on 1400x900 in a window through Wine *with* compiz running and I'm getting 120+ fps.

I installed the Gigabyte model on my second computer, with 2GB ram and Hardy. Nothing worked, at all. Installing the binary drivers failed miserably, using manual install and EnvyNG. Even tried the beta drivers. Nvidia settings manager did not even reconize that my system has an Nvidia card installed, and **lspci** gave the following:
```
03:00.0 VGA compatible controller: nVidia Corporation Unknown device 0640 (rev a1)
```

Note: this is also what the other computer reported, but the card still works.

Just before I started to tear my eyes out in frustration, I decided to try the working Xorg config from my other computer, and what do ya know, it worked! No idea why, but I really don't care. 

I'm running WoW on the 2GB computer with modest settings and I'm only getting approx 30fps, I have no idea why. Yes, the other computer has double the ram, but it shouldn't make *that* much difference. I'm also noticing that compiz on my 2BG seems much more sluggish than before, with my 2 Nvidia 6600GT cards. I might experiment and switch the Gigabyte and EVGA cards to see whats up at a later date.

Here's my xorg.conf
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Thu Jul 17 18:39:19 PDT 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I hope that helps you all.

It should be noted that I'm using Nvidias binary drivers from their site, version 173.14.12

---

### Post by arang on 2008-08-23
i'm tempted to buy a 9500GT from gigabyte but i dunno what driver to use? what driver did u use with the eVGA??

---

### Post by gaten on 2008-08-23
Sorry I wasn't more clear. I'm using version 173.14.12 for both cards, it's the latest stable driver for Linux.

---

### Post by spoons on 2008-08-23
A 9800GTX is just a rebadged 8800GTS 512mb. The 9800GTX+ is identical but more power efficient and cooler. You should get an 8800GTS, it would be faster than your current card and the same as a 9800GTX.

---

### Post by oronte on 2008-10-08
@Galen
Thank you very much for posting your config. My new 9500 wouldn't work at all until I replaced mine with yours, now it works perfectly. Go figure.

---

### Post by PacketCollision on 2008-10-11
For my 9500GT, I ran "sudo apt-get install envyng-gtk && sudo update-pciids" and then ran Envy and chose version 173.14.12 manually.  It seems to have worked perfectly.


Unfortunately, I have an unrelated with my 9500GT.  The card shows red lines and static all across the screen when using DVI (both HDMI and the D-SUB adapter work fine).  The lines and static occur even in the BIOS, so it's obviously not Ubuntu's fault.  I don't know what the issue is, but I RMA'ed the card and hopefully will end up with a working one in a few days.

---

### Post by richbl on 2008-10-14
> **PacketCollision said:**
> For my 9500GT, I ran "sudo apt-get envyng-gtk && sudo update-pciids" and then ran Envy and chose version 173.14.12 manually.  It seems to have worked perfectly.


Unfortunately, I have an unrelated with my 9500GT.  The card shows red lines and static all across the screen when using DVI (both HDMI and the D-SUB adapter work fine).  The lines and static occur even in the BIOS, so it's obviously not Ubuntu's fault.  I don't know what the issue is, but I RMA'ed the card and hopefully will end up with a working one in a few days.

Worked like a charm for my eVGA 9500GT.

However, the command string offered here is syntactically incorrect: it's missing an "install" in the apt-get commmand:

```
sudo apt-get install envyng-gtk && sudo update-pciids
```

Otherwise, I'm a happy Nvidia 9500GT user.

---

### Post by PacketCollision on 2008-10-20
> **richbl said:**
> Worked like a charm for my eVGA 9500GT.

However, the command string offered here is syntactically incorrect: it's missing an "install" in the apt-get commmand:

```
sudo apt-get install envyng-gtk && sudo update-pciids
```

Otherwise, I'm a happy Nvidia 9500GT user.

Thanks for pointing that out.  I fixed it in my post above.

I'm waiting on a new card, hopefully that one will work properly.

---

### Post by eldiabolosk on 2008-11-15
Anybody got the 9800 GT working? I have the problem as Jaxco.  

Just got a few fresh reinstalls (in frustration) both on 8.04 and 8.10 and as soon as i install the 177 driver i am dead on blank screen. Any clues?

---

### Post by Skripka on 2008-11-15
> **eldiabolosk said:**
> Anybody got the 9800 GT working? I have the problem as Jaxco.  

Just got a few fresh reinstalls (in frustration) both on 8.04 and 8.10 and as soon as i install the 171 driver i am dead on blank screen. Any clues?

171 driver?  In Ibex, the current stable driver is 177.80, which works like a charm on Kubuntu Ibex---I've heard bad things about 177.x when combined with Gnome and Compiz under Ubuntu.

---

### Post by eldiabolosk on 2008-11-15
Sorry, It was a typo 177.xx I meant.  I run gnome. GDM.  Wha you say is that in KUBUNTU. There is no problem?  If so which Kubuntu that would be? I never run a Kubuntu, never really liked the feel, but I am willing to give it a try in this instance. Maybe I will fall in love (who knows).
Ed.

---

### Post by Skripka on 2008-11-16
> **eldiabolosk said:**
> Sorry, It was a typo 177.xx I meant.  I run gnome. GDM.  Wha you say is that in KUBUNTU. There is no problem?  If so which Kubuntu that would be? I never run a Kubuntu, never really liked the feel, but I am willing to give it a try in this instance. Maybe I will fall in love (who knows).
Ed.

From what I gather-the problem is somewhere in between Gnome and Compiz, I think--Kubuntu is not effected (it seems)-because KDE4/Kubuntu Ibex does not use a seperate Compiz software (it is all integrated into KDE4 to start with in Kwin).  I'm not too suprised-I never had any luck getting Compiz-Fusion (as a 3rd party extension) to work


The 1st I'd heard about Nvidia driver problems on Ubuntu (or Ibex) was yesterday here when someone responded to me about "Ubuntu having problems" with 177.xx....after a bit of discourse it clicked in my head they meant Gnome/Compiz.  YMMV, of course.


I don't have much choice-my GTX260 is only supported 177.xx and above....but no show-stopper problems, and few annoyances/quirks, yet.

---

### Post by rmjohnson144 on 2008-11-21
> **PacketCollision said:**
> For my 9500GT, I ran "sudo apt-get install envyng-gtk && sudo update-pciids" and then ran Envy and chose version 173.14.12 manually.  It seems to have worked perfectly.


Unfortunately, I have an unrelated with my 9500GT.  The card shows red lines and static all across the screen when using DVI (both HDMI and the D-SUB adapter work fine).  The lines and static occur even in the BIOS, so it's obviously not Ubuntu's fault.  I don't know what the issue is, but I RMA'ed the card and hopefully will end up with a working one in a few days.

Thanks for the tip.  I updated with that command and did the manual install as the automatic fails to find my card still.  I too have the static screen, I didn't notice I needed a PCIe power connector. Unfortunately, I still get the static.  so, it looks like I may be doing an rma as well.  Most of it went away though, but it's still there.

Thanks
-=Mark=-

---

### Post by stoodleysnow on 2008-11-27
> **PacketCollision said:**
> For my 9500GT, I ran "sudo apt-get install envyng-gtk && sudo update-pciids" and then ran Envy and chose version 173.14.12 manually.  It seems to have worked perfectly.


Unfortunately, I have an unrelated with my 9500GT.  The card shows red lines and static all across the screen when using DVI (both HDMI and the D-SUB adapter work fine).  The lines and static occur even in the BIOS, so it's obviously not Ubuntu's fault.  I don't know what the issue is, but I RMA'ed the card and hopefully will end up with a working one in a few days.

I have also found the pixellation/static problem, along with an annoying flickering when rendering anything 3D (including screensavers). I'm not entirely convinced it's the card's fault, since so far the pixellation has only happened once, and did not occur during the shutdown splash screen when I ended that particular session. I shall try VGA connection and update the driver. If neither of those works, I'll be inclined to RMA it. So long as I can make it last until I upgrade the whole system, I don't mind using VGA.

---

### Post by rmjohnson144 on 2008-11-27
> **stoodleysnow said:**
> I have also found the pixellation/static problem, along with an annoying flickering when rendering anything 3D (including screensavers). I'm not entirely convinced it's the card's fault, since so far the pixellation has only happened once, and did not occur during the shutdown splash screen when I ended that particular session. I shall try VGA connection and update the driver. If neither of those works, I'll be inclined to RMA it. So long as I can make it last until I upgrade the whole system, I don't mind using VGA.

I think mine was from overheating.  It was working fine at first then got worse over time.  I even switched to windows with the same problem.  I also put it in a Dell machine with windows and it was still doing it.

-=Mark=-

---

