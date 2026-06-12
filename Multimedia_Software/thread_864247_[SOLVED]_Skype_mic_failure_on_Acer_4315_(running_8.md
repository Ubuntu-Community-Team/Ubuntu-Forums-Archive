---
title: "[SOLVED] Skype mic failure on Acer 4315 (running 8.04)--not the usual suspects"
date: 2008-07-19
forum: Multimedia Software
---

### Post by doubleij on 2008-07-19
Hello,

My skype (including internal mic) was working fine until the most recent kernel update. A week after the update I tried to call someone and my built-in mic was dead. I checked the Gnome Volume Control and everything was up to 100% (capture, mic boost, front mic, etc.). I tried switching to front mic and the computer started to produce a scratchy sound. When I switched back to mic again the machine produced a high-pitched shriek that wouldn't go away unless I muted general audio. I have been able to reproduce this issue again, so I suspect it's a bug. The shriek will go back to scratches if I go to front mic. Neither mic input option worked when I made a skype test call.

After the shrieking sound, I rebooted and tried a couple other options. I checked to make sure I'm using Alsa and not PulseAudio. I also checked the options tab in Skype and ran through the different sound output options. Two of those were invalid and the other one didn't make a difference.

Sound works in other applications and incoming sounds works in skype. I haven't tested the audio in/out jacks since I rarely use them (no headset in the house).

I'm out of ideas. Does anyone have any suggestions? I can't think  why the kernel update would mess up the mic for skype, but that seems to be the only conclusion. The computer hasn't been dropped or anything, so it's not a hardware issue.

---

### Post by doubleij on 2008-07-20
The silence has been discouraging.

Update: the bug has now proceeded to kernel panic on shutdown (unpredictably). I've filed a bug over here.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250230](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250230)

---

### Post by tqprvn on 2008-07-31
same problem here, so giving this a hopeful bump.

---

### Post by doubleij on 2008-07-31
Update: I am declaring this threat solved. Since no one on the forums seemed to know anything about the problem I kept looking around the net for answers.

I found a sound fix at this site
[http://www.hbclinux.net.nz/acer4315-804.html](http://www.hbclinux.net.nz/acer4315-804.html)

The fix is listed at the bottom under Some Issues and I'd missed it before. Note that the mic is not listed as a problem for this fix on the web page. The problem was listed as quiet speakers which wasn't my issue. Anyways, I tried the fix and it worked for the mic issue. 

1. Simply insert this line at the end of the 
/etc/modprobe.d/alsa-base    file.

options snd-hda-intel model=acer

2. Reboot and open your Gnome Volume Control. Your options will be different than they were before. Play with them until you can get the mic to start recording. I don't remember exactly what my settings were, but it only took about 2 minutes to get the settings right.


Note also: the wireless fix listed on the link is helpful. I have created a bash script to automate the wireless fix if anyone is interested. I've tested it and it works on my machine but the usual caveats apply.

---

### Post by tqprvn on 2008-08-04
do headphones work as well?

---

### Post by doubleij on 2008-08-04
> **tqprvn said:**
> do headphones work as well?

Headphones weren't affected by my sound issue. I tested the jack and got ok sound. I haven't tested the jack since the fix because I rarely use it, but I assume it works fine now as well.

---

