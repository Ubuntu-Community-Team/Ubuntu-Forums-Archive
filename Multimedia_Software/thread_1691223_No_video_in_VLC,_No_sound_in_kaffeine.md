---
title: "No video in VLC, No sound in kaffeine"
date: 2011-02-19
forum: Multimedia Software
---

### Post by fpgdu on 2011-02-19
I'm trying to play the stream "RetroEDU" from Shoutcast TV. It will play in kaffeine with no sound and it will play in VLC with no video. How can I get it to work in either player with both sound and video at the same time?

[http://173.193.48.140:8888](http://173.193.48.140:8888)

---

### Post by cjhabs on 2011-02-19
> **fpgdu said:**
> I'm trying to play the stream "RetroEDU" from Shoutcast TV. It will play in kaffeine with no sound and it will play in VLC with no video. How can I get it to work in either player with both sound and video at the same time?

[http://173.193.48.140:8888](http://173.193.48.140:8888)

When I had a problem with VLC not playing anything, the following fixed it for me:

[I]vlc --reset-config --reset-plugins-cache


[/I]

---

### Post by fpgdu on 2011-02-19
> **cjhabs said:**
> When I had a problem with VLC not playing anything, the following fixed it for me:

[I]vlc --reset-config --reset-plugins-cache


[/I]

I ran that, then VLC started. Do I need to open the link in that VLC instance? If so, how do you do that? I tried playing the stream in a new VLC window after I had run *vlc --reset-config --reset-plugins-cache*, and it was still the same.

---

### Post by cjhabs on 2011-02-19
Sorry - you'll have to wait for someone more versed in vlc than me - I just ran it and after that anything I've tried to play just works!

---

### Post by SleepWalkerX on 2011-02-20
Weird, I'm getting no video in Kaffeine and VLC, but audio in both.  Might have something to do with the codec?  It appears to be VP6.  

Install pavucontrol and run that while playing the stream.  Your audio stream should be showing up.  Make sure to select the proper audio device.

---

### Post by fpgdu on 2011-02-21
> **SleepWalkerX said:**
> Weird, I'm getting no video in Kaffeine and VLC, but audio in both.  Might have something to do with the codec?  It appears to be VP6.  

Install pavucontrol and run that while playing the stream.  Your audio stream should be showing up.  Make sure to select the proper audio device.

Didn't work, with VLC or kaffeine.

---

### Post by SleepWalkerX on 2011-02-21
What do you mean didn't work.  When you ran pavucontrol did you see an application audio stream?

---

### Post by fpgdu on 2011-02-21
> **SleepWalkerX said:**
> What do you mean didn't work.  When you ran pavucontrol did you see an application audio stream?

For  VLC yes. For kaffein (the one that had video but no sound) no.

---

### Post by fpgdu on 2011-02-21
ok there is no sound period in kaffeine, no matter what I play.  There is video though.

---

### Post by fpgdu on 2011-02-21
what's this? [IMG]http://oi51.tinypic.com/2rhy0xy.jpg[/IMG]

---

### Post by fpgdu on 2011-02-21
For above: the thing circled in red in the bottom left corner of Kaffeine.

---

### Post by fpgdu on 2011-02-21
bump

---

### Post by gordintoronto on 2011-02-21
Shoutcast tells me: "We are sorry, there were no radio stations matching 'retroEDU'"

What did you do? What did you expect?

---

### Post by fpgdu on 2011-02-22
> **gordintoronto said:**
> Shoutcast tells me: "We are sorry, there were no radio stations matching 'retroEDU'"

What did you do? What did you expect?

It's a TV station, so it's in a separate directory. Please try the link provided in the first post.

---

### Post by fpgdu on 2011-02-25
bump

---

### Post by Yellow Pasque on 2011-02-25
It looks like you're using kaffeine in gnome? I'm guessing you don't have phonon configured correctly. Do you know what phonon backend you have installed? Do you have the systemsettings package installed? systemsettings is the KDE configuration GUI that allows one to configure phonon (unfortunately, it can drag a lot of KDE dependencies in with it).

---

### Post by fpgdu on 2011-02-25
> **Temüjin said:**
> It looks like you're using kaffeine in gnome? I'm guessing you don't have phonon configured correctly. Do you know what phonon backend you have installed? Do you have the systemsettings package installed? systemsettings is the KDE configuration GUI that allows one to configure phonon (unfortunately, it can drag a lot of KDE dependencies in with it).

I don't think I can afford to lose a lot of  RAM resources, but I have phonon-backend-xine, which apparently is the  default for  kaffeine. (No I don't have systemsettings as I am using gnome ubuntu)

---

### Post by fpgdu on 2011-02-26
bump

---

### Post by fpgdu on 2011-02-28
bump

---

### Post by fpgdu on 2011-03-01
bump

---

### Post by fpgdu on 2011-03-01
bump

---

### Post by Yellow Pasque on 2011-03-01
Please don't bump more than once a day. Try installing phonon-gstreamer backend and removing the xine one.

---

### Post by fpgdu on 2011-03-02
> **Temüjin said:**
> Please don't bump more than once a day. Try installing phonon-gstreamer backend and removing the xine one.

Sorry. Thanks, I tried that but it didn't solve the problem. Some additional information: kaffeine appears to not play sound on any streams at all, not just RetroEDU. It does play videos with sound though. Also: RetroEDU  doesn't play at all in movieplayer (neither sound nor video).

---

### Post by fpgdu on 2011-03-03
bump

---

### Post by fpgdu on 2011-03-05
slap

---

### Post by fpgdu on 2011-03-06
punch

---

### Post by fpgdu on 2011-03-07
anyone?

---

### Post by fpgdu on 2011-03-12
bump

---

### Post by fpgdu on 2011-03-23
headbump

---

