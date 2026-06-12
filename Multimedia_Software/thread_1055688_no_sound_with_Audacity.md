---
title: "no sound with Audacity"
date: 2009-01-31
forum: Multimedia Software
---

### Post by knordal on 2009-01-31
I am running 8.04 and I had a issue with audacity both not recording and not playing back.  This is how I solved by issue.  I hope that it helps you.

- First of all assure that you are plugged into the right jack (obvious I know but worth the check)


next run asoundconf list
 
This should tell you what cards you have installed.  Often with built in cards plus any other cards you have installed on your system Ubuntu can become confused.  (thus the question about which jack you are plugged into)

after determining the right card to use the command

asoundconf set-default-card XXXX (X being your card name)

now that also knows what card to use you can run 

alsamixer

alsamixer allows you to adjust the parameters of your sound card like volume and gain on the mic.  The trick is that [tab] moves you between mic and play back.  The left -right arrow keys select the channel and the up arrow increases the volume.  I increased the volume on everything and unmuted everything.

MIC options [CAPTURE]

after tabbing to the capture options I increased all the options to 100 percent.  This resolves the low volume issue with the mic.  Granted depending on your mic you may have to reduce the settings if it starts to distort.  You will have to play around with this.

start audacity and select edit/preferences/Audio I/O

select the correct ALSA device for play back and capture.

test recording.


Now play back:

first back sure nothing else is using your sound device

sudo lsof /dev/snd/*

It can be Firefox or for me it was JACKd.  I killed the process and then audacity started to work.

That is it.

---

