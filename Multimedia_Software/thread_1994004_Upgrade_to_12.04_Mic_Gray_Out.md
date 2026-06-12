---
title: "Upgrade to 12.04 Mic Gray Out"
date: 2012-06-02
forum: Multimedia Software
---

### Post by bojo on 2012-06-02
Hi All,

I just upgraded ubuntu 64 bit from 11.10 to 12.04 and the Mic is grayed out
[IMG]http://ubuntuone.com/5ybkSDMHqeS42C2QMWTdps[/IMG]

I can not mute or unmute - no any control.
The sound otherwise works.

Strange is - when I check with other tools I can actually record the sound
For example - Multimedia Systems Selector will recognize it on a test.
[IMG]http://ubuntuone.com/161aBekGXQysgh0Qg3DFQe[/IMG]

Also if I decide to record it with Audacity - it still works 
[IMG]http://ubuntuone.com/2JzDCgtOOE0mJD4I6zRT2s[/IMG]
[IMG]http://ubuntuone.com/5084se6wSNwwvMKvo23hXO[/IMG]

A challenge comes when I start virtualbox 4.1 - the mute on the mic from the application level does not have any effect 
[IMG]http://ubuntuone.com/0PaBZxaw85ErqvGPMychsT[/IMG]

Any advice? I would really hate to re install the complete system just for fixing the mike. I checked the forums and don't seem to find anything exactly like this.

I am using DELL XPS 15 L502X

Please help,

Thank you,

B

---

### Post by bojo on 2012-06-09
Sadly nobody replied...
Any way - there are a few "fixes" that you will find googling around. 
However - the onnly one that worked for me is below - in case you stumble on it. By the way - this is observed on 2 machines - both times happen with upgrade.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/946232]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/946232")

Big thanks to David from the above thread.

---

