---
title: "feisty, usb headset &amp; mic with teamspeak"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by dunkemdeep on 2007-04-09
being new to linux I have managed to get my head around all the things i have come up against like dual booting feisty with xp on a fake raid 0. I am just about getting there with programs and such but I have hit a problem that I can't seem to find a solution too.
i use a set of sennheiser usb 155 headphones with built in mic. feisty recognizes my setup but i can't get anything but the test beep through them. plus i have just installed teamspeak were my problem is.
I have set up teamspeak to find that I am muted, here is the mic settings I have at the moment:
in the volume control (sennheiser usb headset(alsa mixer))
playback the mic is turned up full along with the speakers
recording microphone capture is turned up full and unmuted, the toggle audio recording from microphone capture is turned off.
switches both the bass boost and auto gain control are ticked

in sound preferences/ devices i have everything on usb audio and they all test ok apart from sound capture, it lets me test it but i don't hear anything.

in teamspeak settings, the sound driver is set to default (oss /dev/dsp)
if I change this to default network (8780:L) then i become unmuted but unable to speak.

please can someone help by either telling me what I'm doing wrong or give me a link to ort it out
thanks in advance:confused: :)

---

### Post by dunkemdeep on 2007-04-09
anyone any ideas please:(

---

### Post by PWill on 2007-04-16
I have this problem too.

---

### Post by trmentry on 2007-04-28
I have just the opposite problem.

My sound card is a Realtek onboard sound card on an nvida nforce 4 board.

Anyway, after some futzing around, I got sound working and I can hear the mic working however the mic is really really low on its volume to others.  There is a hum also from the mic when its activated.  

I don't get this issue when using TS via windows, so its not my sound card or headset.  I believe this is something to do with /dev/dsp which is was TS is using.

But I'm nto sure where to go from here.

Thanks

---

### Post by misconfiguration on 2007-04-30
I  have a logitech USB headset, I changed my device settings to /dev/dsp0 and I"m able to hear TS audio in my headset speakers, but I am not able to talk, I think a lot of people are having the issue. I cannot find it an TS forums either =/

---

### Post by amlucent23 on 2007-04-30
I also have a logitec headset with an nforce 3 250 mobo (onboard sound). I dont know how much help this is but I found that no one could hear me unless I enabled mic boost (under properties i think, then check the box). Also TS would not pick up any of my sound card unless that was the only program launched using audio ( i think this is driver configuration)

---

### Post by misconfiguration on 2007-04-30
> **amlucent23 said:**
> I also have a logitec headset with an nforce 3 250 mobo (onboard sound). I dont know how much help this is but I found that no one could hear me unless I enabled mic boost (under properties i think, then check the box). Also TS would not pick up any of my sound card unless that was the only program launched using audio ( i think this is driver configuration)

I'm definitly going to check that out, but the problem for me is; I'm using a USB headset/mic, I don't go through my sound card, TS comes in and out strictly VIA headset. Thanks for your suggestion, I'm going to try that when I get home today.

Another thing I was thinking about doing is this.. mount /dev/dsp to /mnt/headset and setting that in TS to see if that will work. I don't think it will but it's worth a shot!

---

### Post by misconfiguration on 2007-05-04
Everyone I got my USB headset working with TeamSpeak on my gaming rig. I have a logitech USB headset/mic, first what I had to do is;

Open the Gmixer application, click USB input and turn my boom volume up, and click the REC (record) button. 

Then I set (IN TEAMSPEAK) my headset as /dev/dsp2, before I tried /dev/dsp and /dev/dsp1 I was able to hear with /dev/dsp1 but unable to speak. dsp2 solved this, I have one problem now, I can't play WoW and speak on TS at the same time, once I start to game ALSA only allows one thing to work. But I can listen to music and game, wtf?

---

### Post by neo2k on 2007-05-06
misconfiguration,
did you use the alsa-oss wrapper ?
how are your settings in gnome-sound-properties ?

I've got my via82xx card as the first sound device, my usb-headset as the second, was wondering how you got rhythmbox or what app you might be using for music to work at the same time as ts.

---

### Post by misconfiguration on 2007-05-07
> **neo2k said:**
> misconfiguration,
did you use the alsa-oss wrapper ?
how are your settings in gnome-sound-properties ?

I've got my via82xx card as the first sound device, my usb-headset as the second, was wondering how you got rhythmbox or what app you might be using for music to work at the same time as ts.

neo2k;

I do not use any AOSS wrapper, I'm currently able to use TS, Listen to music AND play games at once, I didn't do anything fancy besides using Gmixer to edit my mic sound.

I have a X-FI sound card, and a USB headset.

---

### Post by ethanphoto on 2007-05-10
where can i get Gmixer i can not find it under synaptic

thanks,
ethan

---

### Post by Unix_Wizard on 2007-05-11
It's part of gnome-applets and installed by default.(Volume control)

---

