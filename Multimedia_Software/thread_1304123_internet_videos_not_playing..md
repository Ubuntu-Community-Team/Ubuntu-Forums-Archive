---
title: "internet videos not playing."
date: 2009-10-28
forum: Multimedia Software
---

### Post by hooah! on 2009-10-28
i recently installed wubi. 9.04 on my presario c700notebook im using the dual boot.(vista)
when i go on youtube it tells me java is either turned off or i need to update it . ok im new to ubuntu and tried some things .. none which have worked at all. so if any of you guys who know linux,can help it would be greatly appreciated. because i was a windows guy before i saw this wonderful os

---

### Post by lrcaballero on 2009-10-28
Go to twiter and try watching a video there!!! see what happens! if it ask you to install flash player, go ahead and do so, then go back to twiter and try watching another video and see what hapens. This is exactly what happened to me!! and I did what I told you and it worked.

Luis

---

### Post by Dark_Stang on 2009-10-29
Applications > Add/Remove Applications. Search for java. You'll want to install the sun-java runtime environment and the web browser plugin. Make sure flash is installed too. Restart your web browser.

---

### Post by hooah! on 2009-10-29
> **Dark_Stang said:**
> Applications > Add/Remove Applications. Search for java. You'll want to install the sun-java runtime environment and the web browser plugin. Make sure flash is installed too. Restart your web browser.


i have sun java 6 runtime installed...and open jdk java 6 (runtime and web start)
and for flash i have gstreamer ffmpeg video plugin , micromedia flash plugin
dude its been 2 days and i still cant seem to get something to happen.... ive tried this also
[SIZE=5][CENTER]**[COLOR=darkred]--PART 2/5, AUDIO & VIDEO STREAMING--[/COLOR]**[/CENTER]
[/SIZE]
 
[CENTER][SIZE=3]**[COLOR=DarkRed]OPTION 1, GECKO MEDIA PLAYER[/COLOR]**[/SIZE][/CENTER]


Gecko Media Player is similar to mplayerplug-in, as it uses GNOME MPlayer to play virtually all formats, but works well without the need of adding any configuration options. Installation and setup is simple, just copy and paste the following commands into the terminal:

**sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin**
 
**sudo apt-get install gnome-mplayer gecko-mediaplayer**

or if you're running Kubuntu, you might want the KDE front-end for MPlayer/Xine:

**sudo apt-get install kmplayer gecko-mediaplayer**

Restart your web browser and test the plug-in [here]("http://www.apple.com/trailers/"). If you have problems viewing the trailers, please refer to the troubleshooting section.

**[COLOR=DarkRed]Note:[/COLOR]** Please [COLOR=DarkRed]**REBOOT**[/COLOR] if you are not carrying on with the rest of the howto, as you have made lot's of changes to your system and could have some strange problems until you start a fresh session. If you still have problems after rebooting, please read the troubleshooting section at the bottom. 


i got it from from here [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by hooah! on 2009-10-29
> **lrcaballero said:**
> Go to twiter and try watching a video there!!! see what happens! if it ask you to install flash player, go ahead and do so, then go back to twiter and try watching another video and see what hapens. This is exactly what happened to me!! and I did what I told you and it worked.

Luis
no i dont think u understand .. java isnt working at all on any web page....i get this grey square over the trailer of whatever is playing with a circle and a play button in the circle all is grey.... i dont know man...

---

### Post by hooah! on 2009-10-29
i went on youtube and clicked on some random video ..it played sound and audio.. then clicked on a recomended video  well that one didnt play at all

---

### Post by Bruce H on 2009-10-29
I've been having a lot of problems with flash video also. Flash in firefox never works, nor in Chrome. I have good luck with it in Epiphany, and it occasionally works in Opera.

I'm running x86_64 version of Ubuntu.

I don't know if running 64 bit is the problem there or not.

---

### Post by NoonienSoong97 on 2009-11-08
I am somewhat new as well to linux. My problem is that I have problems with audio kicking in and out on the java interfaces. I have to restart my computer in hopes for the audio to kick back on in java. I did a reinstall on the java runtime package to see if that worked, and it didn't. I check to see if there were any other open source java programs installed, and there weren't.

Also I do have no script installed on firefox, but made sure to allow for the java to run on the sites I deem reliable. However there could be a problem with no script. I will stop running it and try watching something on hulu see if I get audio that way.

Any other suggestions?

---

### Post by NoonienSoong97 on 2009-11-08
I even tried the javascript debugger, and firefox crashed on me when attempting to debug a heavy java site trying to figure out if there was a problem with the audio on my end. So from the looks of it firefox isn't entirely stable on linux it seems like.

---

