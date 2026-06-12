---
title: "Flash that Works?"
date: 2009-02-01
forum: Multimedia Software
---

### Post by star38hero on 2009-02-01
All right, so I've tried every method in the sticky "Complete Multimedia How-to" with getting flash to work over and again dozens of times.  I've searched other methods on the forums to similar reults.  I don't know how on earth to make Flash work in Firefox.  I'm running 8.04 and am willing to try anything.  Can someone please give me some tips on how to get this working ,or at least point my in the right direction so I can explain why the current strategy is bust?

Thanks,

RJ

---

### Post by disabuse on 2009-02-01
Well if you want to use the closed source Flash, download it from adobe.
I prefer the .tar.gz, 

open a terminal "tar -zxvf install_flash_player_10_linux.tar.gz"
"cd install_flash_player_10_linux"
"chmod a+x flashplayer-installer"
"./flashplayer-installer"

Direct the installer to where you have firefox, mine is /opt/firefox 

( dont have firefox open at the time )

edit: to check if it is installed properly 

"about:config" in firefox url bar
firefox will warn about warranty and what not just hit you understand

---

### Post by star38hero on 2009-02-02
rj@rj-laptop:~$ tar -zxvf install_flash_player_10_linux.tar.gz
tar: install_flash_player_10_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
rj@rj-laptop:~$

---

### Post by SunnyRabbiera on 2009-02-02
did you try the binary installer?
Also do you run ubuntu 64bit?

---

### Post by Therion on 2009-02-02
Open Synaptic.
Search on "Gnash".
Mark any found gnash-related packages for removal.
Close Synaptic.
Open a Terminal and enter the following:

```
sudo apt-get install ubuntu-restricted-extras
```
Follow the prompts and install the packages.

---

### Post by wolfen69 on 2009-02-02
if at some point you are ready to give up, you could just install [Kiwi Linux]("http://kiwilinux.org/en/"). it is basically regular ubuntu (even the theme is the same) with flash and all codecs preinstalled. very nice actually. good luck.

---

### Post by stderr on 2009-02-02
> **star38hero said:**
> rj@rj-laptop:~$ tar -zxvf install_flash_player_10_linux.tar.gz
tar: install_flash_player_10_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
rj@rj-laptop:~$

It sounds very much like you didn't download the installer first ;)

You need to e.g. visit adobe's website, download the installer (for example to your home directory), 'cd' to the directory you've downloaded it to, and then follow those instructions.

The tar xxxxxxxxx line just extracts the compressed file you were meant to have downloaded. You could alternatively use Archive Manager to do that from within Nautilus file manager, if you prefer using a GUI. The rest of his instructions just make the installer executable (you can also do this through Nautilus if you prefer) and then execute it; it's best to run installers etc through the Terminal, so you can actually see the output.

There are many ways of installing flash ;) Basically 1) ensure that all remnants of the previous installation attempts are **purged** from your computer and 2) either use installations via Synaptic/apt/whatever you choose to call it, from Ubuntu sources, OR download an offical installer from adobe and follow instructions they give you, or the instructions you were given before (if you grab the .tar.gz installer)

Good luck :D

---

### Post by gandaran on 2009-02-03
see [this]("http://gandaran.com.sapo.pt/ubuntu.html") for installing flash, if you running ubuntu 64-bits get the 64-bits adobe flash[ here]("http://labs.adobe.com/downloads/flashplayer10.html")

---

### Post by Hugene on 2009-02-03
Originally, I had installed flash using the official download from Adobe (command line script). While watching movies online, Flash would freeze, then Firefox and then the whole Ubuntu would freeze. Often I need a hard reboot.

Then I followed the amazing instructions "Complete Multimedia How-to" and the same problem keeps appearing! 

It's currently my number 1 issue with Ubuntu, and even though my Win XP is virus infected I am still forced to use it, because my home computer is basically for entertainment only. 

Any suggestions? Could it be that the flash player from Adobe has not been completely de-installed?

---

### Post by gandaran on 2009-02-03
> **Hugene said:**
> Originally, I had installed flash using the official download from Adobe (command line script). While watching movies online, Flash would freeze, then Firefox and then the whole Ubuntu would freeze. Often I need a hard reboot.

Then I followed the amazing instructions "Complete Multimedia How-to" and the same problem keeps appearing! 

It's currently my number 1 issue with Ubuntu, and even though my Win XP is virus infected I am still forced to use it, because my home computer is basically for entertainment only. 

Any suggestions? Could it be that the flash player from Adobe has not been completely de-installed?
this looks more of a video card driver problem (can you provide hardware details and driver installed) but then it can also be due to something else, use synaptic package manager, search for flash and make sure you don't have gnash flash plugin, swfdec flash plugin and just one adobe flash package installed.

---

