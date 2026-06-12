---
title: "How To: Enabling multimedia support in Ubuntu"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by LukeCarrier on 2007-08-28
Hello everybody,
As I'm sure you know, Ubuntu doesn't come with all the multimedia codecs you need for playing music and watching movies on your computer. This is because the codecs required are of questionable legality, and nobody wants to see their favourite operating system to go down the pipe do they? To enable playback of the codec you want, just follow its instructions below. These instructions are for Feisty users only. You must add the repository first.

[SIZE=4][B]Add the repository
[/B][SIZE=2]**1. Open Terminal**
Click Applications > Accessories > Terminal
**2. Open the sources file**
Type[/SIZE][/SIZE][FONT=Lucida Console]
sudo gedit /etc/apt/sources.list
[/FONT] And press enter.
**3. Add the sources to the file**
Just copy and paste this onto the bottom of the sources file:
[FONT=Lucida Console]deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free[/FONT]
Save that file, then close it.[B]
4. Add the security key[/B]
Paste this into the Terminal:
[FONT=Lucida Console]wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -[/FONT]
And press enter.
[B]5. Reload the package lists
[/B]Paste this into Terminal and press enter:
[FONT=Lucida Console]sudo aptitude install libdvdcss2[/FONT]
**6. You're done**
You can now download any of the software listed below.

[B][SIZE=4]DVD[/SIZE]
[SIZE=2]1. Open Terminal
[/SIZE][/B][SIZE=2]Click Applications > Accessories > Terminal[B]
2. Run the command[/B]
Type:
[/SIZE][FONT=Lucida Console]sudo aptitude install libdvdcss2 w32codecs[/FONT]
and press enter. At this point you may be asked for your password, just type it in and press enter.
**3. Say yes to the prompt**
Just press 'Y' on your keyboard and press enter to confirm the installation.

---

