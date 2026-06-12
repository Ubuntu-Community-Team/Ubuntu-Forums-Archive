---
title: "Microphone Problems"
date: 2011-02-02
forum: Multimedia Software
---

### Post by Chrissd on 2011-02-02
Hi,

My microphone on my Aspire works perfectly with sound recorder, but not with Google chat. I tried using pavucontrol but there's no difference between the two levels, but they do both seem to be right down the bottom end of the levels, barely moving. Additionally, I tried Skype briefly, but had exactly the same problem, so not convinced it's a Google chat problem.

Can anyone think of any suggestions?

Many thanks

Chriss

---

### Post by lidex on 2011-02-02
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Chrissd on 2011-02-07
Hi, apologies for the late response, been having ISP issues.


```

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

```

---

### Post by lidex on 2011-02-09
Need the link!!

---

### Post by Chrissd on 2011-02-14
Apologies.


[http://www.alsa-project.org/db/?f=68069e26bafa04a38c735636786afd3b86d93f45](http://www.alsa-project.org/db/?f=68069e26bafa04a38c735636786afd3b86d93f45)


Many thanks once again, I really appreciate your time and effort.

---

### Post by lidex on 2011-02-15
You have these entries in alsa-base.conf that are not helping so remove them:
```
snd-hda-intel: model=acer-aspire position_fix=1
snd-hda-intel: model=acer-aspire position_fix=1

```
Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
**Reboot**
If you're no closer, update your alsa-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by Chrissd on 2011-02-17
Thanks for the reply.

I can't find any alsa-base.conf in /etc/ and there's no obvious /etc/alsa. Google isn't returning anything useful, just a thread on here about an empty alsa-base.conf file. Where abouts might I find alsa-base.conf please?

Edit: I think /etc/modprobe.d/alsa-base.conf is it, as I cannot find an exact match for those lines, but can see the line "options snd-hda-intel model=acer-aspire position_fix=1" twice. Can you just confirm this is what I need to delete from that file, if that is the right file, before I edit this? Apologies for the newbieness scaredness.

---

### Post by lidex on 2011-02-18
> **Chrissd said:**
> Thanks for the reply.

I can't find any alsa-base.conf in /etc/ and there's no obvious /etc/alsa. Google isn't returning anything useful, just a thread on here about an empty alsa-base.conf file. Where abouts might I find alsa-base.conf please?

Edit: I think /etc/modprobe.d/alsa-base.conf is it, as I cannot find an exact match for those lines, but can see the line "options snd-hda-intel model=acer-aspire position_fix=1" twice. Can you just confirm this is what I need to delete from that file, if that is the right file, before I edit this? Apologies for the newbieness scaredness.

I assumed you added those entries and would know where they were. To answer your question, yes.

---

### Post by Chrissd on 2011-02-19
I haven't touched that file before. I'll edit them now and let you know how it goes.

---

### Post by Chrissd on 2011-03-07
Hi!

I've been playing with this a lot and it works! Unfortunately, I have to go into Pulse Audio Volume control, input devices, turn the front left down otherwise no one can hear me!

Thank you for at least getting me working, just wondering if you know how to fix this tiny little problem. It seems to default to locking the channels together for some reason.

---

### Post by lidex on 2011-03-07
This may help. Set up your levels as needed then save the alsa settings with this command:
```
sudo alsactl store 0
```

---

### Post by Chrissd on 2011-03-08
Thanks.

I'll mark this thread as solved and open a new one should any further problems arise in the future!

I'm very grateful! Thank you so much for your help! You're a star!

ChrissD

---

### Post by windozh8ter on 2011-03-14
lidex, forgive me, but I just might LOVE YOU!!! This makes three very major problems you have solved for me today. I had moved my ubuntu 10.10 install to a new computer and the microphone didn't work. In all my tinkering, I ended up killing all of my sound. Then in tinkering some more, I could only boot to a terminal type screen (i.e., no windows interface). After I got my sound back, I clicked on your username and found your other posts, which ended up solving all three of my problems. You are my hero!

---

### Post by lidex on 2011-03-18
> **windozh8ter said:**
> lidex, forgive me, but I just might LOVE YOU!!! This makes three very major problems you have solved for me today. I had moved my ubuntu 10.10 install to a new computer and the microphone didn't work. In all my tinkering, I ended up killing all of my sound. Then in tinkering some more, I could only boot to a terminal type screen (i.e., no windows interface). After I got my sound back, I clicked on your username and found your other posts, which ended up solving all three of my problems. You are my hero!

You can send funds to paypal -- kidding ;-)
One morning, driving to work years ago, I ran out of gas. On the highway in rush-hour traffic I began walking. I was miles away from any gas station and feeling really bad. I got maybe a quarter-mile when a guy pulls over, asks my situation and then offers me a ride. He seemed enthusiastic about the situation even after I told him I had no money (which is why I had no gas - was just trying to get to work on a wing and a prayer).

So he drives to a gas station and fills up his gas can, paying for it himself. He then drove me back to my car and waited while I poured the gas in my tank and got the car started. I returned the can to him and expressed my appreciation. I was a little confused why he would go out of his way for a complete stranger, probably making himself late to work in the process. He told me that once he was in the same boat and another guy helped him out in basically the same fashion. He said he had never forgotten that - and neither have I.

Thanks for that post. You made my day.

---

### Post by tinnudile on 2011-03-18
PLz help me too :( , I dual booted my Ubuntu 10.10 with Windows XP on my acre extensa 4630 laptop , Everything is working fine , but I am getting background noise in audio recorded from Mic . But sound is clear when I record in Windows .  Thanks for your time (^_^)

---

