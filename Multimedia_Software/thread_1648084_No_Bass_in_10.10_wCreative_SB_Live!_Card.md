---
title: "No Bass in 10.10 w/Creative SB Live! Card"
date: 2010-12-18
forum: Multimedia Software
---

### Post by digitalmonarch on 2010-12-18
All-

I'm new to Ubuntu, but have some experience with *NIX (specifically Red Hat and AIX.)

I'm not getting any bass out of my 4.1 Logitech THX setup. The surround speakers are operating fine. I know that the bass unit itself is working because I was using it with windows on this computer before I made the switch to Ubuntu. If I run a speaker test from either the sound preferences or the terminal, the speakers work but the bass does not.

I ran this command from a terminal to help with the diagnostic effort, but I'm not entirely sure what I'm looking at: 

```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```

Here is the output of the above command:
[http://www.alsa-project.org/db/?f=594d0b489944c7f230487c0363a4d94d25b89891](http://www.alsa-project.org/db/?f=594d0b489944c7f230487c0363a4d94d25b89891)

I have been searching for an answer to this question for some time now and can't see to find the relevant information anywhere. Any help that someone can provide would be greatly appreciated. I'm not sure what the problem is here, but it's driving me crazy.

Thanks in advance!

---

### Post by digitalmonarch on 2010-12-18
Not sure if it's relevant or not but i should add that in my sound preferences under the hardware tab I have a device called "Internal Audio 1 Output/1 Input" with a profile of "Analog Surround 5.1 Output + Analog Stereo Input".

My motherboard has a built in sound card, but it's about 8 years old. With the SB live card installed, the onboard card should be disabled right? I guess I am wondering if it could be causing a problem?

---

### Post by digitalmonarch on 2010-12-18
Figured it out!

The following setting needs to be added (or uncommented) in your pulseaudio config file (/etc/pulse/daemon.conf)

disable-lfe-remixing = no

Don't ask me why lfe remixing is disabled by default in pulse, but it is. I hope this helps others who are having the same problem.

After you make the edit, restart the pulseaudio daemon or your machine (if you prefer.)

---

