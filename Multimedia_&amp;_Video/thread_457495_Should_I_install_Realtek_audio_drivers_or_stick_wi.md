---
title: "Should I install Realtek audio drivers or stick with Feisty default?"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by timzak on 2007-05-28
Hi,

Using Feisty and have Realtek ALC888 onboard audio on my motherboard.  I'm a bit confused on the whole audio issue.  Feisty gives me two options out of the box:

1. HDA VIA VT82xx (Alsa mixer)
2. Realtek ALC888 (OSS mixer)

First question, what is the difference and what should I choose?

Second question, I noticed on Realtek's website, they have a Linux audio driver for my sound solution:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2)

Should i install this or stick with one of the Feisty drivers above?

Thanks for any help.

---

### Post by timzak on 2007-05-29
Can anyone help?

Thanks.

---

### Post by dodgePT on 2007-05-29
I guess that, since everything works out of the box, i change it?
I also have one of those audio devices, and everything works without a glitch :)

---

### Post by timzak on 2007-05-29
Yeah, it works fine (Feisty defaults to the ALSA setting) I just want to understand a little background.  Like what are the differences between the ALSA and OSS options and what, if any, are the advantages to installing the driver provided by Realtek.

If anyone can help me understand, I'd appreciate it.  :p

---

### Post by dodgePT on 2007-05-29
[Advanced Linux Sound Architecture (ALSA)]("http://www.alsa-project.org/")

[Open Sound System for Linux]("http://www.4front-tech.com/linux.html")

> The ALSA  (Advanced Linux Sound Architecture) sound driver provides an alternative to the older and more common OSS/Free driver. The ALSA project has been around since early 1998 and has achieved a level of stability that makes it worthy as a substitute for OSS/Free. The project is currently working toward the 0.9 stable release; the third 0.9 beta release came out on March 20. The question that comes up is: why use ALSA?

[ALSA] The ALSA Introduction sheds some light on the question. The goals of the ALSA project include maintaining backwards compatibility with the OSS/Free API while providing a more capable Library API for ALSA based systems. This allows a large number of existing OSS/Free based applications to run with the ALSA driver. The OSS compatibility is provided via an optional set of loadable modules, so those who do not require backwards compatibility need not expend unnecessary system resources on it. In addition to being able to run OSS applications, the ALSA driver has a number of native applications that use the ALSA Library API.

One of the more obvious differences between ALSA and OSS/Free is that a working ALSA based system uses a number of small loadable modules, whereas OSS comes in the form of one large module. If MIDI support is not required, the module need not be loaded. This makes ALSA a good candidate for embedded Linux applications.

The ALSA sequencer code is designed to give better response times for MIDI sequencer functions, making an ALSA based system suitable for a wider variety of uses than just simple playback. The goal of this part of the project is to be able to run real-time MIDI functions on Linux that compare with older Macintosh and Atari ST systems, a non-trivial feat on a multitasking OS like Linux.

The ALSA API is more fully featured than the OSS/Free API and utilizes more of the features found on modern sound cards. It may be necessary to switch to ALSA in order to utilize all of the features of newer sound chips, such as the digital audio input on the nifty CMI8738/PCI chip, which supports true 44.1Khz digital audio input without noisy resampling. The OSS/Free API closely mirrors the hardware design of older SoundBlaster sound cards, but that is a design that is becoming increasingly outdated. Since they have started from the beginning, the ALSA developers have, presumably, been able to study the shortcomings of the older drivers and work on those weaknesses.

ALSA is not currently supported by all of the major Linux distributions, for instance, it is included with SuSE, but not with Red Hat. Installation on a Red Hat system requires removal of the OSS driver and addition of the ALSA modules in the /etc/modules.conf file. This process is detailed in the the ALSA documentation, but is nonetheless a non-trivial job that would likely scare off those who are new to Linux. The SuSE distribution makes the ALSA driver installation fairly easy. ALSA will likely be included in the Linux 2.5 series kernels natively, if that happens, it will probably show up as an option in more Linux distributions. Give ALSA a try, it works rather nicely. 

Hope that answers your question :)

---

### Post by timzak on 2007-05-29
Thanks a lot, sounds like Alsa is the way to go.

Can I ask you one more favor?  I have another thread related to a sound issue with my sound device that's not getting any replies.  Can you visit [www.rush.com](www.rush.com) and see if you hear music playing from the main page?  I haven't had any luck getting the streaming audio to play in Feisty with the Realtek.  I have another Feisty system with a SBLive! and it plays music on that site and my Windows computers play the music no problem.  I'm trying to figure out if it's an issue with Feisty and Realtek and since you have the same sound device, you could help me figure it out.

Thanks.

---

### Post by dodgePT on 2007-05-29
Yeah, i hear it, kind of a hard rock theme. I'm using firefox, i guess that's the same you're using.

Maybe you been messing with the sound settings and disabled something **OR** you need to reinstall flash plugin for firefox (because i checked source code from that page and sound comes from a swf ;) .

---

### Post by timzak on 2007-05-29
Thanks again.  It appears I borked my codecs by messing with Automatix2.  I'm a newb and have been running this (my first) installation of Ubuntu (or any Linux OS) for about a month now.  I've been wanting to do a fresh install anyhow (now that I'm somewhat familiar enough to avoid using Automatix).

Thanks for your help, sir.

Take care.

Tim

---

### Post by dodgePT on 2007-05-30
You're welcome, but i'm still also a noob, at least with ubuntu. But i'm learning :)

---

### Post by auberon on 2007-06-04
I'm curious to know if you ever got the audio streaming to work in Firefox with your Realtek? I'm having problems at the moment with my Realtek audio.

Thanks

---

### Post by timzak on 2007-06-04
Yes I did.  I reinstalled Feisty.  One of the first things I did after the reinstall was visit that same website ([www.rush.com](www.rush.com)) and Firefox immediately asked me if I wanted to install the Adobe Flash plugin because the web page required it.  I said yes, it automatically installed, and the streaming audio worked.  I'm not sure why it broke in the first place because I know that Adobe Flash was installed on my machine before.  The only thing I could think of was I was installing any and every codec I could find and probably had some conflict that broke the Adobe Flash streaming audio.

Let us know if you need more help.  I'm a noob, but I will try if I can!

---

### Post by rhibberd on 2007-06-05
If you do not mine me asking, have you been able to get any Midi apps to play music?  

I also have the same Realtek sound card but none of my Midi apps work:(.  I was looking at the Alsa web site and it did even have Realtek listed.

---

### Post by timzak on 2007-06-05
> **rhibberd said:**
> If you do not mine me asking, have you been able to get any Midi apps to play music?  

I also have the same Realtek sound card but none of my Midi apps work:(.  I was looking at the Alsa web site and it did even have Realtek listed.

I hadn't tried til you asked, so I found a midi file on my Windows partition, double clicked it and Add/Remove popped up asking me to install a midi player.  I chose KMid.  It appears to be playing, but I can't get any sound.  I check my audio properties and tried enabling all the tracks under Preferences, but none of them controlled midi volume.  So I can't get midi to play either.  I'm thinking about throwing an old SoundBlaster Live! (original) in and disabling onboard sounds.  It doesn't seem like support for Realtek's HD Audio is very robust right now.

Let me know if you have any luck with midi.

Take care.

---

### Post by DaVince21 on 2007-10-08
I am a newbie on this forum replying to an old topic. Sorry about that. I just had to reply to this topic I found through Google.

The thing with Realtek audio cards is, they actually don't have MIDI. Windows fixes this by using a soundfont (package of instruments) and an internal software synthesizer to play the MIDIs, but in Linux, you'll have to set up this functionality.

When you installed Feisty, you most likely also installed the "freepats" patch set (kind of a soundfont but scattered over a bunch of files rather than one), and the program Timidity++, which is enough to get MIDI working on your Realtek HD audio sound card.

Timidity++ is a software synthesizer. This means that it can perform the same function as Microsoft's internal one in Windows, only better because it supports more. Here's how you set up Timidity++ to run as a service when you boot Ubuntu:

1. Open /etc/rc.local as the superuser. This is a boot script where you can leave any additional services/commandline programs to start up during boot.
2. Insert the following line before *exit 0*:
```
timidity -Os -iA
```
The -Os flag will make timidity use the ALSA sound driver (rather than the default OSS one, which seems to have a problem with Realtek HD cards (or at least mine)).

The -iA flag will make Timidity++ run as a service, which means it will always stay in the background as a daemon, ready to perform its task (fetch MIDI data and give you real sound based on the freepats sound font).

One more thing you need to do for some applications (like KMid) is to set up the MIDI out source to use one of the 4 Timidity ALSA devices. :) (You'll see those added when you run the command above in the console, or reboot.)

---

