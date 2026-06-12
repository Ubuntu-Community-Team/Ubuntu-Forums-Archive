---
title: "Ubuntu Hardy + Amarok mp3 support"
date: 2008-06-18
forum: Multimedia Software
---

### Post by 200mg on 2008-06-18
I have tried everything to get amarok to play mp3's

1.  install libxine1-ffmpeg
2.  install ubuntu-restricted-extras
3.  run /usr/lib/amarok/install-mp3
4.  delete ~/.xine
5.  copy all plugins from /usr/lib/xine to ~./xine
6   I have double checked to make sure amarok is using the xine engine

It worked fine on Feisty, this is not an upgrade, this is a fresh install of hardy.

I mainly use it for podcasts, now I'm using it as my podcast feeder and playing the podcasts using vlc.

Anyone have any ideas.  I guess I could un/reinstall amarok.  {just did, same thing, no suitable demux}

---

### Post by 200mg on 2008-06-19
Bump..I know there is something I haven't tried yet.....Please help me

---

### Post by cozmicharlie on 2008-06-19
Can you play the mp3 using Rythmbox, Totem or some other player?

---

### Post by Snader on 2008-06-19
The topic below might be worth reading, although my problem was solved by deleting ~/.xine. 
[http://ubuntuforums.org/showthread.php?t=833347](http://ubuntuforums.org/showthread.php?t=833347)

---

### Post by 200mg on 2008-06-19
> **cozmicharlie said:**
> Can you play the mp3 using Rythmbox, Totem or some other player?

I am currently using vlc to play mp3's.  I use amarok as a podcast feeder and play them in vlc

---

### Post by cozmicharlie on 2008-06-19
Did you try Snader's suggestion?  If so, did it help - not help?

I don't use Amarok so I don't have it in front of me.  Does it allow you to select the output format such as alsa, pulse, etc?  If so you may want to try different settings.  It appears to me you have installed all the proper codecs so the problem may be due to something else.  Their are a lot of posts about people having problems with Pulse Audio.

---

### Post by 200mg on 2008-06-20
I tried everything on this thread "http://ubuntuforums.org/showthread.php?t=833347"(the one snader posted)  Still no go.  Rhythm gives errors to.  I guess it's vlc for me, until amarok maybe drops a new version or something

Also, I can't seem to figure out how to get gstreamer to show up in Amarok. I have un/reinstalled all of the gstreamer packages but cannot seem to find a way to get GStreamer as an option under "engines" in Amarok.  It only has the option for xine.

The xine extra plugins will not install through synatpic...hrmmm???!?  Maybe it's not synaptic, whats the app that launches when you go to Applications > Add Remove?, thats what's giving the error below



"Xine extra plugins cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type."

---

### Post by cozmicharlie on 2008-06-20
Not sure why it won't let you install the xine plug ins.  Try it in Synaptic rather than add/remove or from a terminal sudo apt-get install xxx.

I also read on the forums, a number of people have been able to play mp3 by starting the program in the terminal.  It is worth a shot - try starting Amarok in the terminal (just type amarok).

---

### Post by threeta on 2008-07-11
I downloaded (well my daughter did) a mp3 file.  I tryed playing it, and get the dreaded amarok cannot currently play mp3s 

I click on the mp3 support button - nothing happens.
I get confused cause i thought all was working with my install
its been upgraded to hardy, and a couple of patch downloads applied

About Amamrok:  1.4.9.1,   kde 3.5.9
using gnome btw

I began hunting around - found this thread, checked checked and checked again, still no luck.  Then got bored and thought i'd just play some older oggs and get over it.  next file i play works fine so i look at it and realise its an MP3  WTF  - what's wrong with the 1 mp3?  looks like its corrupt or somehting.  So advise 200mg is find a known good mp3 and try it??

hope this helps - it can be really frustrating sorting this stuff.:mad:

---

