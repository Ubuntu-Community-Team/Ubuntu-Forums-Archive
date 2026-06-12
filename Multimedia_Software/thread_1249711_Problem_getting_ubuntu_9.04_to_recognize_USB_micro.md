---
title: "Problem getting ubuntu 9.04 to recognize USB microphone?"
date: 2009-08-25
forum: Multimedia Software
---

### Post by pppango on 2009-08-25
I had recently bought a usb condenser microphone (condenser microphone SF-910B) and plugged it in, but there was no immediate recognising and I don't know what to do.

I'm running under jaunty.

Can you give me some help on getting this to work and record in skype and audacity?

(I'm not a genius at ubuntu so speak beginner, please :) )

---

### Post by pppango on 2009-08-26
Just bumping this up; didn't see it on the front page.

---

### Post by pppango on 2009-08-26
Bumping it up again, darn this category is fast :P

---

### Post by pppango on 2009-08-27
Bumping this again... x)

---

### Post by emmiesix on 2009-08-27
I also need help with this... I'll let you know if I get anywhere.  It's a logitech.

---

### Post by pppango on 2009-08-27
Okay! Thank you for posting. :3
Good luck on your dilemma!

---

### Post by pppango on 2009-08-27
Bump

---

### Post by pppango on 2009-08-28
> **pppango said:**
> Bump
x_x

---

### Post by Anjrew on 2009-08-29
I'm in the same boat.  I got my front mic jack working finally, of course after that I lost my back mic which was working prior to that.  I tried reverting what I did but it still didn't work.

As far as my USB mic (yes i have 3 mics), that was working fine when I was running Intrepid, and can't remember what I did to activate it.  I made visible all my recording tracks in the volume manager, and that's how I figured out to get the front one turned on, but of the 4 options I have in there, only one of them seems to do anything and that's the front.

I'm not so sure anything's wrong yet, I just need to know how you set up a USB mic assuming nothing is the matter so I know if I've tried that yet or not.

---

### Post by misterfixit on 2009-08-29
I have a Plantronics DSP-100 USB headset/mic combination.   When I plugged it in it was recognized but I had to manually change the selection in the volume control right click panel.  Right now, the mic works with Sound Recorder and Skype.  The earphone does not work no matter which setting I use in the sound controls.  No matter, since I find that the speaker system works OK and I don't need privacy for the reception of audio anyway.

My problem is that I use Echolink -- a Skype-like application which runs under WINE.  WINE does not recognize the headset at all.  I've read on WINE forums that setting controls for the ALSA/OSS combination is supposed to fix the recognition problem.  Seems that WINE developers had a hissy-fit with Pulseaudio and don't support it -- they have posted several reasons which I am sure justifies their position in their own minds.  Hence, it's necessary to use an OSS or ALSA selection except for the USB mic where the ALSA/OSS kluge is supposedly required.  What I've found is that I can use the winetricks application to tweek the settings for other WINE-required programs.  But not for Echolink -- so I am assuming it is an Echolink issue.

All I can recommend is to try every combination of settings in the sound set up, logging off and back on, rebooting, etc., and eventually the USB mic will be recognized.  USB Headphones are another frustrating issue about which there are many posts and requests for assistance.  So far with about 8 or 9 different headsets I have never gotten a USB headphone to work with Ubuntu.  Period.

My 2 cents worth, IMHO. YMMV, HTH, LSMFT.

Dave


This

---

### Post by Gerlads Mod on 2009-08-30
My Logitech USB microphone worked as soon as I installed Ubuntu. Hell, it worked in the CD Live session.

Well, I don't know if this makes a difference but I had it plugged in when I installed Ubuntu.

---

### Post by misterfixit on 2009-08-30
> **Gerlads Mod said:**
> My Logitech USB microphone worked as soon as I installed Ubuntu. Hell, it worked in the CD Live session.

Well, I don't know if this makes a difference but I had it plugged in when I installed Ubuntu.

Granted that microphones seem to be recognized -- usually -- even with tweeking.  However the question is:  did/does the headphone work.  Most likely it doesn't.  Not to detract from your response, and I appreciate the information .. however, the USB headphone issue is a PITA considering that it has become more difficult to find a mini-plug headset of decent quality.

However again, tweeking is part of the Linux experience and I would not have a complete week without having to go to an sudo command and reboot or at least re-log in.

Now, if we really want to talk about problems, let's consider Comcast Internet Cable service ... I've been working since 5 am and my connection to Radio Paradise is up and down, up and down.  When I start BitTorrent to continue the d/l of "Mars Attacks" all hell breaks loose with the stream.  ACK!  :lolflag:

Dave

---

### Post by pppango on 2009-09-01
Any other solutions? Trial and error will just be too difficult.

---

### Post by pppango on 2009-09-01
I just found out that it was made to work with windows XP and it won't work then, either.


What a waste of $12. :(

---

