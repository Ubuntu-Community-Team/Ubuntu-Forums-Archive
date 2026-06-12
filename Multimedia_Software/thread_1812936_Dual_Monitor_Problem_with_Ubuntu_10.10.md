---
title: "Dual Monitor Problem with Ubuntu 10.10"
date: 2011-07-27
forum: Multimedia Software
---

### Post by redbikemaster on 2011-07-27
I am currently running 10.10 with dual monitors. My video card is a ATi Radeon 9800XT graphics card. I'm experiencing tearing on my left monitor. It only shows one monitor, labeled "Unknown", in the Monitor Preferences, so I can't span the image across the two screens, they just mirror. I am pretty sure this is a driver problem, but how do I fix it?

Also, graphic-intensive stuff, such as Celestia or Google Earth, used to run smoothly, but now they stutter horribly.

Attached: images of my left monitor. Note, these aren't near the worst of the tearing. They're just what I could capture on my cell camera. Sorry about the lack of quality.

---

### Post by robsoles on 2011-07-28
Hey, not that I will be the one to provide your solution but I reckon you will get a quicker and better solution if you provide a more rounded problem :)

Ubuntu 10.10 huh?

Gnome/KDE/Unity/Other?

Compiz?

Graphic Card make and model?

What's your mobo and CPU?

Thought of anything else that might help them help you? :p


FYI (and my amusement): I have a 1920x1080 Acer 24" monitor and 1360x768 32" TV - under Ubuntu I have it in wide desktop with Acer as main and the TV to the right, there is dead region for my mouse below the TV but no surprise. Under Windows I make it mirror at the only settings they'll share for gaming purposes :)


My crap's NVidia, what's yours?

---

### Post by redbikemaster on 2011-07-28
Gnome, not Unity (still have panels)

No Compiz, therefore no wobbly windows (wish so)

ATi Radeon 9800XT 

ASUS A7N8X Deluxe

AMD Athlon XP 3200+

This was all given to me by the guy who converted me to Linux.

---

### Post by redbikemaster on 2011-07-28
Just read your sig. Funny, I'm redbikemaster everywhere I go. (Except YouTube, someone got the name before I did). I've even used it at Arby's:"Can I get a name for that order?""Red Bike Master""O.....K"

---

### Post by robsoles on 2011-07-28
What driver would you say you are using for 9800XT there? Did the system prompt you that there was a proprietary driver or is it using native drivers?

Please post the contents of the file I hope you find at /etc/X11/xorg.conf - if you don't know how to use [noparse]```
(code here)
```[/noparse] tags then please prompt me to try to show or tell you how first :p

---

### Post by redbikemaster on 2011-07-28
Here's all I got:
```


username@username'scomputer:/etc/X11$ ls
app-defaults             fonts    xinit   Xreset.d    Xsession.d
cursors                  rgb.txt  xkb     Xresources  Xsession.options
default-display-manager  X        Xreset  Xsession    Xwrapper.config

```
*My username and computer name have been removed due to privacy reasons*

It appears I have no /etc/X11/xorg.conf

---

### Post by robsoles on 2011-07-28
Is there anything like a "System"->"Administration"->"Hardware Drivers" that you can find on one of your desktop panels?

If you can find it, does it list a driver for your video card? (and if it does list your video card, does it offer to install or claim that it is installed?)

---

### Post by redbikemaster on 2011-07-28
All I have is System>Administraion>Additional Drivers, which only says,
> 
"No Proprietary Drivers Are In Use On This System"


---

### Post by robsoles on 2011-07-28
Please tell me what controls the "System"->"Preferences"->"Monitors" dialog box offers you.

---

### Post by redbikemaster on 2011-07-28
Not much. All it shows is a huge monitor labeled "Unknown".

Also, (I'm an idiot), I'm running 11.04. It's on a hard drive I swapped in from a few months ago. I've been swapping drives constantly as I've had two go bad in two weeks.

No Unity. It's just like 10.10, hence my mix-up.

---

### Post by redbikemaster on 2011-07-28
Quick Update: I am down to one monitor right now, so I can't test solutions.

The other one is being loaned out at 0% interest currently.

---

### Post by robsoles on 2011-07-28
mmmh, OK, generous fool huh? :p (dw, me too mostly!)

If you can't find anything related to 'graphics' in the any menuitem under the "System" menu **aside** from "Monitors" (and "Monitors" isn't doing **** for you) then it might be worthwhile trying a driver we can find if we look hard enough: [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

Don't rush into installing that one, I went to [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) and made what I thought to be logical choices - I strongly suggest you fill in the choices and see if you land on the same page I did (at the very least) before you go executing their little .run file :)

From what experience I have dealing with X it's terribly handy if I can find a valid mechanism to write a nicely valid (and operable, does what I was after) /etc/X11/xorg.conf file for me; I get to use the "System"->"Administration"->"NVIDIA X Server Settings" tool to write it for me on my system and systems I build because ATI wasn't as straightforward as NVIDIA **when I was choosing** - Strong probability of a proprietary driver the Ubuntu Devs have tested for NVIDIA, much likelihood of some "native" driver for the ATI device(s) which might be 'complete' and satisfactory but may just as well have issues.


Even without a second monitor plugged in: Can you see a menuitem with "ATI" in it anywhere under your "System" menu?

---

### Post by redbikemaster on 2011-07-29
> Even without a second monitor plugged in: Can you see a menuitem with "ATI" in it anywhere under your "System" menu?
Before or after going to amd.com? (Which I'm doing right now)
Before going, no.
Update: I got the same result you did. I've downloaded that before, but it wouldn't install. I must've been doing it wrong.

---

### Post by robsoles on 2011-07-29
OK, if you are willing to execute it then give the following a BASH (lol - open "Terminal" pal)

Assuming that you downloaded exactly the file I found and your downloader put it at ~/Downloads/ati-driver-installer-9-3-x86.x86_64.run here is what I would do to make it execute: (hopefully your BASH behaves as mine when you become root the way I prefer)
```
rob@rob-desktop:~$ **sudo bash**
[sudo] password for rob:
root@rob-desktop:~# **m[COLOR=Blue]k[/COLOR]d[COLOR=Blue]ir[/COLOR] /root/ati**
root@rob-desktop:~# **cp ~/Downloads/ati-driver-installer-9-3-x86.x86_64.run /root/ati/**
root@rob-desktop:~# **chmod +[COLOR=Red]x[/COLOR] /root/ati/***
root@rob-desktop:/root/ati# **cd /root/ati**
root@rob-desktop:/root/ati# **./ati-driver-installer-9-3-x86.x86_64.run**
```Couple of things to note: DON'T RUSH INTO THIS!!!! and, anything could happen when you execute their crap - could go majestically and make them look horribly clever, could blow up in your face.

I probably haven't pressed enough to find a 'canonical approved' version of the very same driver; It's not going to fry my system, I really do want to impress upon you to research more before dropping this driver in place (other side of the coin, I half expect it will give you a shiny GUI dialog to set your displays as you wish :))

If all goes well with executing their script then it should dump you back as root with a prompt in terminal (may not have focus) - type 'exit' [enter] (no apostrophes) twice to get the hell out of there :p

```
root@rob-desktop:/root/ati# **exit**
rob@rob-desktop:~$ **exit**
```(A healthy "Terminal" closes at this point, just in case this stuff belongs in ABT after all ;))

---

### Post by redbikemaster on 2011-07-29
I'm getting 'md: command not found'
Would mkdir suffice?

---

### Post by robsoles on 2011-07-29
sorry, brain wasn't quite all the way turned on - where I wrote 'md' above I entirely meant 'mkdir'; look, I'll fix it :)

Actually to tell the truth, it wouldn't be the first time a Linux terminal has rejected my attempt to use DOS at it and vice versa the same ;)

---

### Post by redbikemaster on 2011-07-29
Haha, been there. OK, so now what? The app Additional Drivers stil shows nothing.

---

### Post by robsoles on 2011-07-29
mmmh, I wasn't expecting for you to find anything in 'additional drivers' but I was expecting some sort of obvious outcome we wouldn't have to dig for.

I just notice my other error I made in the list of instructions```
[s]chmod +w ....[/s]
chmod +x /root/ati/*
```Much apologies my friend, I wanted to make it executable; It was already writeable enough when it arrived :roll: :embarrased:

If it (apparently) executed anyway (mmmh, not a good thing but let's ignore coz you should be able to make it run now if it didn't before - soz again);

Did you have to reinstall an OS (or switch to another partition, or use the LiveCD) to post back to the forums after running that? :p

Can you remember what got written back to terminal when you executed the ati-driver-installer-9-3-x86.x86_64.run file?

Did it open a sensible looking dialog box in your GUI desktop?

Did you right click on your desktop, choose 'change desktop background' and go to the 'Visual Effects' tab (if it exists in 11.04 the same place) to set "Extra: Provides more ...." ? (After successfully executing that .run file tho)

If it allowed you to select "Extra" Visual Effects then did you open compiz and try to enable wobbly windows and anything else in that? (good indicators that your video is right now..) 


If it did whatever it did 'silently' then we may have to dig up what exactly it did to be sure that's going to be advantageous. 

It may be that we have to round it out with some packages from synaptic (and BASH it a bit more) to make it work properly; try whatever above you haven't yet please.

---

### Post by redbikemaster on 2011-07-30
To answer you questions:

It did nothing to my system, so I did *not* have to reinstall, switch partition, or use LiveCD.

It said something like 'Verifying archive', then did scrolling dots like ```
sudo apt-get update
``` would return. Then it went right back to the prompt with nothing visible happening.

I didn't get any dialog boxes.

Still no 'Visual Effects' tab. I mean NO TAB AT ALL. But it was already that way.

N/A to the last question.

Tried everything else, similar results obtained.

---

### Post by realzippy on 2011-07-30
Don 't want to disturb,but
afaik you cannot install the catalyst driver for your card:

Catalyst < 10.10 isn't working with current xorg-server 

also see the red box on :

[http://wiki.cchtml.com/index.php/Debian](http://wiki.cchtml.com/index.php/Debian)

There is no ati proprietary driver for your card.

---

### Post by robsoles on 2011-07-30
mmmh, that is a little disturbing, but hardly your fault, not sure why you are apologising for being quite so helpful - it is late where I am as I pop into the forums before I nod off; I'll have a hunt around in Google tomorrow for information that will help me make a better response. I was thinking of getting you to collect and then send me the output from terminal when executing their .run file but realzippy makes it real clear that that is a pointless pursuit.

Thanks realzippy, I reckon you deserve a [Trophy]("http://ubuntuforums.org/showthread.php?t=1013559&page=9999") :biggrin:

---

### Post by redbikemaster on 2011-07-30
```
Purging configuration files for xserver-xorg-video-radeon ...
Processing triggers for man-db ...
Setting up ttf-mscorefonts-installer (3.3ubuntu3) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

All fonts downloaded and installed.
Search pattern not terminated at /usr/share/perl5/Debian/Defoma/FontCache.pm line 148.
Compilation failed in require at /usr/share/perl5/Debian/Defoma/Font.pm line 11.
BEGIN failed--compilation aborted at /usr/share/perl5/Debian/Defoma/Font.pm line 11.
Compilation failed in require at /usr/bin/defoma-font line 8.
BEGIN failed--compilation aborted at /usr/bin/defoma-font line 8.
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 9
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
This appears after every 'sudo apt-get' command I run. What on eart is it and how do I get rid of it?

---

### Post by realzippy on 2011-07-30
try
```
sudo apt-get remove ttf-mscorefonts-installer
```

---

### Post by redbikemaster on 2011-07-30
I did the ```
 sudo apt-get remove ttf-mscorefonts-installer
```
This is the result
```
The following packages were automatically installed and are no longer required:
  simgear1.9.1 g++-4.4 libxerces-c28 libstdc++6-4.4-dev libxdot4
  esound-clients
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ttf-mscorefonts-installer
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 221 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 273552 files and directories currently installed.)
Removing ttf-mscorefonts-installer ...
Search pattern not terminated at /usr/share/perl5/Debian/Defoma/FontCache.pm line 148.
Compilation failed in require at /usr/share/perl5/Debian/Defoma/Font.pm line 11.
BEGIN failed--compilation aborted at /usr/share/perl5/Debian/Defoma/Font.pm line 11.
Compilation failed in require at /usr/bin/defoma-font line 8.
BEGIN failed--compilation aborted at /usr/bin/defoma-font line 8.
Processing triggers for fontconfig ...
```

---

### Post by realzippy on 2011-07-31
And still the issue when running apt-get ?
If so,try

```
sudo apt-get -f install
```

---

### Post by redbikemaster on 2011-08-17
Update: My motherboard fried. So I won't be trying to fix this problem for a while.

---

