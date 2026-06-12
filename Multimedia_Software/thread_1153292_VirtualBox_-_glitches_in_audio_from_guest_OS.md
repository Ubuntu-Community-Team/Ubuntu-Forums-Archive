---
title: "VirtualBox - glitches in audio from guest OS"
date: 2009-05-08
forum: Multimedia Software
---

### Post by owainsutton on 2009-05-08
I'm having trouble with VirtualBox, with the audio from a virtual machine not playing cleanly, and this seems to be independent of the guest OS and of the hardware.

I'm hoping to use Windows XP as a virtual machine on a Ubuntu 9.04 setup, specifically to use music notation software for which there's not a suitable alternative.  Everything is installed and working, but for major glitches and stuttering in audio being played on XP.  This is the case whether playing through VirtualBox's AC97 or Soundblaster emulations, through Pulseaudio or Alsa (I'd try OSS, but haven't got that working), or with an external USB sound card (Alesis io2) assigned to the virtual machine.  I've also tried out with Ubuntu as a guest OS, installed on a separate virtual machine, and the same problem occurs.  Giving the virtual machines up to 1GB ram doesn't help.

Any suggestions of how to start troubleshooting?  This is on an Acer Aspire 7730 laptop.

---

### Post by wuliman on 2009-05-10
I'm having the same problem. I have 9.04 installed on my system and am using Virtualbox to load XP so I can play some games. Whenever a sound is made in XP, I get choppy audio at best. Does any one know of a sound driver that we can install that will work with XP in Virtualbox?

---

### Post by owainsutton on 2009-05-13
Bump?

---

### Post by nickbolton2705 on 2009-05-13
I'm having similar problems, here's my specs:

VirtualBox 2.2.2
Guest: Ubuntu 9.04
Host: Windows Vista
Sound card: SoundBlaster Audigy 2 SE

When I play sound on my Ubuntu guest system, it sounds glitchy, sometimes pauses, and makes high pitched sounds occasionally. I have installed the guest additions.

Where might I start looking for a solution? Feel free to suggest google queries :)

---

### Post by NikAmi on 2009-05-22
I don't know if this will help you guys, but I too was having pops/stutters in the audio when watching videos on my VirtualBox'd Windows 7. What I did, was to change to audio output in MPC to the option labeled "Speakers Intel..." and the pops/stutters went away. Also, my video wasn't fullscreening properly so I changed the video output to make sure that it wasn't set to renderless. Any of the first three options should work, but I just stick with system default. In your games, I would look for an audio setting where you can set the output and then change it to the most direct output you can find. Even choosing DirectSound with the Intel label continued to give me the distortion. Look for the speaker option.

---

### Post by CryptiniteDemon on 2009-06-13
I'm having this same problem.  The audio from windows 7 is poppy and scratchy.

---

### Post by owainsutton on 2009-06-18
It looks like the problem has disappeared - I can only assume this is due to one of the Ubuntu updates over the past week or two.

---

### Post by NikAmi on 2009-06-24
Wow...you're lucky. After getting some updates, my popping and choppiness is worse than ever. I don't know what happened but my streaming lectures are now pretty much unwatchable.

---

### Post by sheoyong on 2009-06-25
I am using Ubuntu 9.04 and Virtualbox 2.2.2. I used to have the same problem.

So I tried to solve this problem. I found that switch sound from OSS to pulseaudio will improve it.  Not eliminate the problem entirely, but will improve it. Poppy sound will appear less often.

You can try.

---

### Post by Solrac924 on 2009-08-12
try this:

double-click Volume Control
Change Device to Playback: ALSA PCM...via DMA (PulseAudio Mixer)

launch VirtualBox
when the "machine" is powered off, click Settings
click Audio
uncheck "Enable Audio" & check it again to enable it
select PulseAudio
click OK

---

### Post by blackmail on 2009-08-12
I would also suggest messing around with the sound card, or with it's drivers, but i can't suggest anything for sure, never had a problem with virtualbox, look at the settings in virtualbox, and see if there is also something tto tune...

---

### Post by navaburo on 2009-08-13
I have the same problem on Ubuntu 9.04 with VB 2.1.4_OSE. Pops and studders, not bad, but it makes Rosetta Stone less than desirable to use. Worked fine on ArchLinux.

---

### Post by owainsutton on 2009-08-13
I spoke too soon about the problem disappearing - it's still reappeared from time to time.  However, putting Windows on a fixed-size virtual disk rather than a dynamically expanding one seems to have got rid of glitches.

---

### Post by usererror on 2010-02-09
This is an old post, but i found the solution to the problem for the scratchy-ness for me.

Check out this post: [http://forums.virtualbox.org/viewtopic.php?p=51237#p51237](http://forums.virtualbox.org/viewtopic.php?p=51237#p51237)

create the .asoundrc file with the statements in it, then restart your virtualbox and the vm, problem gone for me!

I am using win7 in vbox.

---

### Post by andydbzee on 2010-09-05
i boosted the Memory Availabe option in settings, as well as changed audio drivers to ALSA from Pulse. this worked for me

---

### Post by HaroldTyler123 on 2010-09-05
I have 9.04 installed on my system and am using Virtualbox to load XP so I can play some games. Whenever a sound is made in XP, I get choppy audio at best.



__________________________
[Malaysia Vacations]("http://www.malaysia.com/tours.html")
[Malaysia Holiday]("http://www.malaysia.com/tours.html")

---

