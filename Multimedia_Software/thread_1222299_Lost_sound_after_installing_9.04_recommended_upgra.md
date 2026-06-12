---
title: "Lost sound after installing 9.04 recommended upgrades"
date: 2009-07-24
forum: Multimedia Software
---

### Post by luangwa on 2009-07-24
I am running Ubuntu 9.04 on my Dell 3250 with its Sound Blaster Live sound card. When I check the alsamixer -Dhw everything is fine, nothing is muted but when I check the pluse audio control under the Output Devices my Dell Sound card shows that it is muted. I tried clicking on the speaker symbol but with no response.

I have followed the instructions on [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) on pulseaudio fixes which is where I am stuck.

When I put in a CD and run PulseAudio Volume Control I can see that the signal is being pickup in the Playback & Output devices. Every slider is up to 100% but still no sound.

How do I resolve this problem? Thanks for your anticipated assistance.

---

### Post by igorzwx on 2009-07-24
you can easily find at least 100 similar stories in this forum

---

### Post by igorzwx on 2009-07-24
this was story of today
** 	[COLOR=#980101][B][ubuntu]**[/COLOR] Sound output only as root  [/B]
[http://ubuntuforums.org/showthread.php?t=1221919](http://ubuntuforums.org/showthread.php?t=1221919)

---

### Post by kakyoism on 2009-07-25
1. put your user under pulse, pulse-base, pulse-rt user groups
2. the most helpful tip I found is that you need to find the "codename" of your laptop model and fill out the following line correctly in /etc/modprobe.d/alsa-base.conf

```
options snd-hda-intel model = <YOUR LAPTOP MODEL CODE NAME>
```

Beware, the codename can be rather dramatic, e.g., 
my HP dv-3's codename is "dell-m4-1"

Look for this info on this forum, I got a long list in another post, forgot where....search with "laptop"

But mind you I still have the stupid stuttering sound everywhere, but at least I can hear everything clearly

---

