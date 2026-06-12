---
title: "No Flash in Firefox (yes I did a search)"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by C00P88 on 2007-11-14
Hi all,

I'm trying to verify my flash installation in Firefox 2.0.0.8 (why won't it upgrade to 2.0.0.9?) I've verified in the add/remove section and in synaptic that flash and the plugin are installed. I've also installed via the adobe website (the tar.gz file). When I click help, I don't see any option for "about:plugins". Does this mean flash is not installed? When I go to the american express website, the page loads over and over until I close the tab. Is there another way to verify I actually have flash installed correctly? Visiting websites seems hit-and-miss.

---

### Post by Yellow Pasque on 2007-11-14
A little info plz
What version of Ubuntu are you running? (Feisty, Gutsy, etc.) and 32-bit or 64?
Also, I was confused about what you get with the about:plugins comand in FF.

Can you give us output from the following ls commands?:

```

cd /usr/lib/firefox/plugins/
ls
cd /usr/lib/mozilla/plugins/
ls

```

---

### Post by C00P88 on 2007-11-14
Hello,

I'm using Ubuntu 7.10, and Firefox 2.0.0.8 (came with Gutsy). The adobe instructions said to verify the flash install by clicking 'help' then 'about:plugins'. When I click help, I do not see an option for about:plugins. I also checked add-ons, there is nothing listed related to flash. Am I just looking in the wrong places? I ran the commands as you advised, I get the same result:

```
bash: cd/usr/lib/firefox/plugins: No such file or directory
bash: cd/usr/lib/mozilla/plugins/: No such file or directory
```

This makes me wonder where adobe flash installed to?

Edit: I went into my .mozilla folder, and found a firefox folder, a plugins folder, and a pluginreg.dat file. The plugins folder contains a file called libflashplayer.so that cannot be opened. The pluginreg.dat file has a section that says this:

```
[PLUGINS]
/usr/lib/mozilla/plugins/mplayerplug-in.so:$
:$
```

---

### Post by Yellow Pasque on 2007-11-14
Try those commands again, and this time, put  a space between 'cd' and '/' THIS AIN'T DOS!

Also, type about:plugins into the URL bar in Firefox. See if Flash is listed there.

---

### Post by C00P88 on 2007-11-14
ok, I tried agian with the space.


```
coop@Coops-PC:~$ cd /usr/lib/firefox/plugins/
coop@Coops-PC:/usr/lib/firefox/plugins$ ls
flashplugin-alternative.so       libunixprintplugin.so
libflashplayer.so                mplayerplug-in-dvx.so
libjavaplugin.so                 mplayerplug-in-dvx.xpt
libtotem-basic-plugin.so         mplayerplug-in-qt.so
libtotem-basic-plugin.xpt        mplayerplug-in-qt.xpt
libtotem-gmp-plugin.so           mplayerplug-in-rm.so
libtotem-gmp-plugin.xpt          mplayerplug-in-rm.xpt
libtotem-mully-plugin.so         mplayerplug-in.so
libtotem-mully-plugin.xpt        mplayerplug-in-wmp.so
libtotem-narrowspace-plugin.so   mplayerplug-in-wmp.xpt
libtotem-narrowspace-plugin.xpt  mplayerplug-in.xpt
coop@Coops-PC:/usr/lib/firefox/plugins$ cd /usr/lib/mozilla/plugins/
coop@Coops-PC:/usr/lib/mozilla/plugins$ ls
flashplugin-alternative.so       mplayerplug-in-dvx.so
gxineplugin.so                   mplayerplug-in-dvx.xpt
libjavaplugin.so                 mplayerplug-in-qt.so
libtotem-basic-plugin.so         mplayerplug-in-qt.xpt
libtotem-basic-plugin.xpt        mplayerplug-in-rm.so
libtotem-gmp-plugin.so           mplayerplug-in-rm.xpt
libtotem-gmp-plugin.xpt          mplayerplug-in.so
libtotem-mully-plugin.so         mplayerplug-in-wmp.so
libtotem-mully-plugin.xpt        mplayerplug-in-wmp.xpt
libtotem-narrowspace-plugin.so   mplayerplug-in.xpt
libtotem-narrowspace-plugin.xpt
```

Also, typing about:plugins in the url bar shows that shockwaveflash and futuresplash player are enabled. So it looks like flash is installed. I guess the problem is the webpages.

---

### Post by wolfen69 on 2007-11-14
try this:
```
sudo apt-get purge firefox
```
then
```
sudo apt-get install firefox
```
then
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by gypsyjoker on 2007-11-14
ok, i tried those commands because i'm having the same problems. didn't fix it, and the output from cd /usr/lib/firefox/plugins and cd /usr/lib/mozilla/plugins looks the same, and i'm using the same version of firefox

---

### Post by chriss8892 on 2007-11-14
i have the same problem

---

### Post by C00P88 on 2007-11-15
Well, I'll try the purge tomorrow. There's something about Gutsy that will only let me save information to a CD once(I am now out of CDs), and I'd like to backup my bookmarks before removing and re-installing Firefox (I assume that's what those commands do?).

---

### Post by C00P88 on 2007-11-15
I tried the 3 commands above, they didn't seem to make a difference. So I booted into Windows, got the same thing in firefox. Opened Internet Explorer, the page loaded fine. I guess the web designers weren't thinking of Firefox when they built the site.

---

### Post by Asobi on 2007-11-16
did u get it solved? well anyway i had some probs too getting a working flash plugin this is how i did it.

go to adobe flash site (i got redirected)

couldnt get rpm installed, no clue what to do with this (see output below). it doesnt accept the RPM commands, none of them actually. if someone knows why. please, eager to learn.

> paul@paul-desktop:~/Desktop$ sudo # rpm -Uvh flash-plugin-9.0.48.0-release.i386.rpm
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
paul@paul-desktop:~/Desktop$

i did get the tar.gz installed.

u need to extract it and install, its all explained on the website. somewhere during the installation youre asked to find your firefox directory.. it gives as example /usr/lib/mozilla. that one exists too but was empty. and gave a error. wasnt untill i returned to my pc later that i figured there might also be a /usr/lib/firefox directory :)

> Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla): /usr/lib/firefox
dir= /usr/lib/firefox


---

### Post by C00P88 on 2007-11-16
Actually, I'm thinking at this point that the problem is with the particular website I was trying to visit (americanexpress.com). So I just boot into Windows and use Internet Explorer for that one(yuck). Seems to only work for IE. Go figure.

---

