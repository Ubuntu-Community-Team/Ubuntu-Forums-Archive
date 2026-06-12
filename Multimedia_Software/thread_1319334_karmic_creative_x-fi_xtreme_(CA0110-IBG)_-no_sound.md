---
title: "karmic: creative x-fi xtreme (CA0110-IBG) -no sound with spdif (optic digital IEC958)"
date: 2009-11-08
forum: Multimedia Software
---

### Post by adamruss on 2009-11-08
As the title states,
i've got a Creative X-FI sound card (CA0110-IBG) - tried hooking it up with the optical output (spdif) - no sound

ubuntu reconizes the card, also has all the right outputs on the mixer settings, still no sound. 

got all big promises that on karmic surround will be default and work out of the box, i used the onboard on jaunty waiting for the release... well it dosent work :(

i googled this for a week, no solution at sight, this is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/463829](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/463829)

the only hope i see is maybe an older 2.6.31 rev will work? looking for other people stuck like me. any clue will be appriciated thanks.

---

### Post by A. J. Rimmer on 2009-11-16
"...looking for other people stuck like me..."

Hi.  Just wanted to chime in and say that I just installed Karmic on my HP Pavilion Elite and have the same problem with my Creative X-Fi Xtreme.  I've had this computer for a couple of months and have been waiting for NVIDIA to release their updated video driver, which came out a couple of weeks ago.  My plan all along has been to dual boot Windows and Ubuntu, which is why I picked the NVIDIA video, but forgot to consider whether or not the Creative sound card would be supported.

My symptoms are the same as yours; everything looks normal as far as the card being recognized, but no sound.  In my case, I'm trying to use the analog output rather than SPIDF, by the way.  That's not a show-stopper for now, and I can use my Logitech USB headset if I really need to hear something, but I would like to see a solution sooner than later.

Seems like I've been fighting with Ubuntu audio on one computer or another since Dapper Drake!

---

### Post by powerpleb on 2009-11-17
Yes, I have the same problem with CA0110-IBG on Karmic using analog output. Sees device but wont produce sound, if I play a file on rythmbox it just stalls. I've tried several different things including removing pulseaudio, installing 'linux-backports-modules-alsa-karmic-generic', ensuring everyone is in the 'audio' group, checking levels on alsamixer all to no avail.

Worse thing is that I bought this card to replace the Audigy I removed because ridiculously it wasn't compatible with Windows 7. Very, very unhappy with Creative right now. 

Guess I'll just have to wait.

---

### Post by 8Kuula on 2009-11-20
Same problem here, posted info to [http://ubuntuforums.org/showpost.php?p=8206457&postcount=486](http://ubuntuforums.org/showpost.php?p=8206457&postcount=486)
No solution from my end yet.

---

### Post by exkend on 2009-11-21
Got the same card and the same problem. Here's to waiting and hoping this is sorted soon.

What soundcards with optical in/out and spdif are supported out of the box by Ubuntu? Any recommendations?

---

### Post by tan0118 on 2009-11-21
Try disabling the onboard sound cards in BIOS.

---

### Post by exkend on 2009-11-22
Thanks for the reply. I have disabled the on-board sound and still no sound.Any more suggestions would be appreciated.

Ex

---

### Post by th3j3ster on 2009-11-24
Same Problem. I don't think there is a fix for it unfortunately...If you just bought the card see if you can still take it back and get something not from creative...I wish I still had that option.

---

### Post by siikah on 2009-11-27
I've been messing with this on and off for months, and that f**k**g card just won't WORK! If anyone has, please give us a hint!

Yeah, the final message at [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/63947](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/63947) is pissing me off. It doesn't help :(

---

### Post by Webe12 on 2009-12-06
I have no sound from my x-fi extreme either using alsa. But I found that if I use OSS, I do get sound working to a point. Not everything works. But I can play audio and most of my videos appear to work. Maybe it will work for you.:)

---

### Post by adamruss on 2009-12-07
> **siikah said:**
> I've been messing with this on and off for months, and that f**k**g card just won't WORK! If anyone has, please give us a hint!

Yeah, the final message at [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/63947](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/63947) is pissing me off. It doesn't help :(

heh, dont get pissed, the funny thing is, if you install 9.04 and install the xfi drivers your self it does work. but 9.10 was supposed to have it build in.
from what i understand, the problem is the xfi driver that is build in the 2.6.31.* kernel. so if you install and older version of the kernel (2.6.28.*) and then install the xfi driver manually it suppose to work.

---

### Post by A. J. Rimmer on 2009-12-07
> **Webe12 said:**
> I have no sound from my x-fi extreme either using alsa. But I found that if I use OSS, I do get sound working to a point. Not everything works. But I can play audio and most of my videos appear to work. Maybe it will work for you.:)

Thanks for the tip, Webe12.  I have been studying this today and will give it a try as soon as I get a chance.  For the possible benefit of others I will briefly summarize what I have found.

1. The Creative X-Fi Xtreme does not use the same chipset as the rest of the X-Fi family.  For this reason, solutions that work for other X-Fi cards may not work with the Xtreme.  Perhaps that explains why the Xtreme doesn't work with Karmic even though it has been stated that the X-Fi is now supported?  Here is a reference:

[http://en.wikipedia.org/wiki/X-fi#X-Fi_Xtreme_Audio](http://en.wikipedia.org/wiki/X-fi#X-Fi_Xtreme_Audio)


2. Here is the Ubuntu Community Document describing how to set up OSS (Webe12, is this how you did it?):

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)


3. Here is a list of equipment supported by OSS.  Note that the only X-FI listed is an "Early Beta," but that the Audigy IS listed.  (Wikipedia claims that the Xtreme is really a rebranded Audigy.):

[http://mercurial.opensound.com/?raw-file/f794ffc6c185/devlists/Linux](http://mercurial.opensound.com/?raw-file/f794ffc6c185/devlists/Linux)


4. The third reference (above) mentions NVIDIA High Definition Audio.  This is of particular interest to me since I have NVIDIA graphics with HDMI output.  I would think that this would give me a second option for sound output, but the NVIDIA card is not detected by Ubuntu at all.  Perhaps switching to OSS will change that?


5. Finally, as a workaround I dug out a cheap ($10) USB sound card that I had bought a while ago.  (It is about the size of a small thumbdrive.)  With it plugged in to a USB port and my powered speakers plugged in to that, at least I have sound for now.

Hope this is of use to some of you.

---

### Post by A. J. Rimmer on 2009-12-08
I'm one step closer....

I followed the Ubuntu Community Documentation that I listed in #2 in my previous post.  I'm still not getting any sound out yet, but:

1. Audio applications will now play, rather than freeze.

2. I can open up the OSS mixer panel and I get sound level indications (green - yellow - red bars) corresponding to the audio level.  The mixer panel shows sliders for all of the audio input and output jacks.

3. When I installed OSS it correctly detected and identified my sound card (Creative X-FI Xtreme).  However, in the Multimedia System Selector it still indicates "Device:" as Unsupported, even though OSS is selected as the plugin.

I'm going back over the procedure to see if I missed anything.

UPDATE --

I ran sudo soundoff then sudo soundon, and then was able to get output when I ran osstest.  Still no output from Totem, but I'm sure there is a way.  Lost of troubleshooting and configuring documentation available.

I've had enough for today, but will try to attach this again tomorrow.

---

### Post by adamruss on 2009-12-08
> **A. J. Rimmer said:**
> I'm one step closer....

I followed the Ubuntu Community Documentation that I listed in #2 in my previous post.  I'm still not getting any sound out yet, but:

1. Audio applications will now play, rather than freeze.

2. I can open up the OSS mixer panel and I get sound level indications (green - yellow - red bars) corresponding to the audio level.  The mixer panel shows sliders for all of the audio input and output jacks.

3. When I installed OSS it correctly detected and identified my sound card (Creative X-FI Xtreme).  However, in the Multimedia System Selector it still indicates "Device:" as Unsupported, even though OSS is selected as the plugin.

I'm going back over the procedure to see if I missed anything.

UPDATE --

I ran sudo soundoff then sudo soundon, and then was able to get output when I ran osstest.  Still no output from Totem, but I'm sure there is a way.  Lost of troubleshooting and configuring documentation available.

I've had enough for today, but will try to attach this again tomorrow.

if you changed to OSS you probebly need to change in " gstreamer-properties" in order to hear totem, try VLC.

---

### Post by A. J. Rimmer on 2009-12-08
> **adamruss said:**
> if you changed to OSS you probebly need to change in " gstreamer-properties" in order to hear totem, try VLC.

Thanks for the suggestion.  When I run gstreamer-properties I just get the Multimedia System Selector box, where I get the "Unsupported" indication (see #3 in my post above).  At least I think that's what's happening -- I just rebooted into Windows before I got your message so I can't double check.

Anyway, I will try to apply your suggestion tomorrow and also give VLC a try.  I did try Flash video briefly and got no sound.  I'm sure I can get this sorted out one way or another; so far everything looks as expected except the gstreamer-properties box.  System sounds are not a concern for me, but ultimately I hope to get MythTV running on this box (I have had pretty good luck with MythTV on other installations.)

More tomorrow, I hope!

---

### Post by powerpleb on 2009-12-08
I'm just going to wait for it to be fixed. Apparently, it is in the pipeline.
[http://article.gmane.org/gmane.linux.alsa.devel/69098](http://article.gmane.org/gmane.linux.alsa.devel/69098)

---

### Post by 8Kuula on 2009-12-09
Great :)
Maybe it finaly works in 10.04, or am I hoping too mutch?

---

### Post by A. J. Rimmer on 2009-12-09
Progress report:

Well, I seem to have sound about half the time.  osstest always gives me sound, both from my rear and front "green" jack.

Using the test function in the Multimedia Systems Selector (also known as gstreamer-properties) gives a test tone on roughly half the attempts.

Trying to play something with Totem results in success maybe less than half the time.

Still pondering; out of time and energy for tonight.

---

### Post by A. J. Rimmer on 2009-12-14
OK, I think I have this just about solved.  To recap,

1. I followed these instructions for setting up OSS:

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

2. I experienced seemingly random behavior with sound; sometimes it was there and sometimes not.

3. Today I tried editing various settings in:

/usr/lib/oss/conf/osscore.conf

Nothing seemed to help much until I uncommented vmix_disabled and changed its value from 0 to 1:

vmix_disabled=1

4. Sound now works consistently to a limited degree.  I'm not getting sound from things like Frozen Bubble, but I am getting sound from Totem.  Flash video won't play in Firefox (not just no audio but won't play at all) and I just tried to play an Ogg video file from Linux Journal in the browser and it won't play.  However, when I downloaded the .ogv file then it did play (with sound).

5. This site has configuration information for specific applications; guess I will work through that next:

[http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)

Hope you guys are having some luck with your systems.

---

### Post by Kuoi on 2011-02-27
The "Worider" trick worked for me !!!

[http://ubuntuforums.org/showthread.php?p=10346176](http://ubuntuforums.org/showthread.php?p=10346176)

Good luck , Kuoi

BTW : It's working for the analog output , I didn't tried digital , and won't try now !
I have sound , ... I use digital only in wdos ;-)

---

### Post by A. J. Rimmer on 2011-03-27
Kuoi --

This works for me too!  Thanks so much for digging up this old thread and letting us know about this.  I've been using OSS but it is only a half solution.  I now have full audio for everything including games and myth-tv.

Presently running Lucid Lynx LTS

:D

---

### Post by Vinencre on 2011-06-05
> **Kuoi said:**
> The "Worider" trick worked for me !!!

[http://ubuntuforums.org/showthread.php?p=10346176](http://ubuntuforums.org/showthread.php?p=10346176)

Good luck , Kuoi

BTW : It's working for the analog output , I didn't tried digital , and won't try now !
I have sound , ... I use digital only in wdos ;-)
It works for me too. Thanks a lot, I was looking for it for days !!!:)

---

### Post by bfuzze on 2011-07-01
Worider worked for me too...
[http://ubuntuforums.org/showthread.php?p=10346176](http://ubuntuforums.org/showthread.php?p=10346176)

Ubuntu 10.04 2.6.32-32-generic

---

