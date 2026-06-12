---
title: "radio streaming"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by ken johnson on 2007-11-12
I can not listen to various radio stations over the internet-most of the time!

Sometimes, but rarely, everything works fine. Usually, like right now, none of the stations I try work- like the BBC, the CBC etc. Sometimes, like yesterday BBC streaming worked when I tried in the morning but then never worked again that day and is not working now and none of the other stations I tried worked except the BBC.

I have had two technical support companies come to my house and neither has been able to diagnose why radio streaming is not working on my PC (Acer Model T670)
They have both verified that I have the right audio drivers, the latest version of Wondows Media Player 9 and all the latest updates, that my modem (Efficiency Networks Speedstream 6300) is fine and has all the latest firmware, that my high speed internet connection is working fine (and it is) etc etc.

The fact that it sometimes works suggests the issue is not software related- either software works or it doesn't. The fact that I can surf the net to any web site suggests that it is not my internet connection or router.

But I can not get radio streaming to work.

I am out of ideas or places to seek help to resolve this issue. Anyone with any ideas?
Thx
Ken

---

### Post by Metaljaz on 2007-11-12
What version of Ubuntu are you using? Have you thought about trying mplayer or realplayer to play your radio streams? You may have to install one of the plugins for linux.


The below links are guides for installing different programs using feisty and gusty. If you are using another version you can get to the wiki from one of the below links. Check under the multimedia section to see if you have all codecs installed.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

Just suggestions...

---

### Post by Metaljaz on 2007-11-12
This may make a little more sense to you.
You can remove totem player and if you have mplayer installed it will become your default player.
You can remove totem via synaptic (uninstall totem, totem-gstreamer and totem-mozilla),  Just don't uninstall libtotem-plparser7. After they are completely uninstalled install totem-xine.
Now, if mplayer is installed it will become your default player when using firefox.

another suggestion....

---

