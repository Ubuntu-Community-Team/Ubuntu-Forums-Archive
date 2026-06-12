---
title: "Installing Spore On Hardy"
date: 2008-09-14
forum: Multimedia Software
---

### Post by standardeviant on 2008-09-14
Hey all!

I'm trying to install using Wine on 8.0.4 and I'm coming across some problems. I've heard the game works like a charm on Ubuntu and so far I've had no luck. I get an error at the installation screen  and the installer doesn't show up just off the DVD (I have to run it through wine, through the Terminal) . Is there anyone who has successfully installed the game and could help? I really dislike having to go on my Windows machine to play the only game that requires it (I have installed and played Half Life 2 and other Steam games) Help would be really appreciated! :)

---

### Post by Indubitableness on 2008-11-27
I've done a little tampering with Spore in wine myself, i'm currently running 1.1.9 of wine. I just recently figured out how to make the installer run, BUT it crashed on the EA Download Manager install. The game still seems to have installed successfully, and it even tries to run, but it tells me "This program needs to access the internet in order to verify ownership, please verify that your computer is connected to the internet and try again" or some such bullsh*t. After three tries it prompts me for my CD Key again and then tells me the same thing.

  If you want to run the installer here's what you do, put your Spore cd or DVD or whatever it is in the drive, and open a terminal, then go to your Spore CD directory

$ cd /media/cdrom

then type

$ wine installer

and the installer will run.

Don't expect it to move quickly, and don't expect the ******* game to run. I can't even get it to run on windows anymore and god damn EA isn't friggen helping me at all.

I defended EA and their DRM vehemently until i realized this ******* DRM is preventing me from playing the legitimate copy on my legitimate machines.

 It'll probably take me all week, but i'm going to get this mother ****** running

---

