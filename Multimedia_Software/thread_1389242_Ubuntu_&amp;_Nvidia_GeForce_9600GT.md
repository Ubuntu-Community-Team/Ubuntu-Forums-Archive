---
title: "Ubuntu &amp; Nvidia GeForce 9600GT"
date: 2010-01-24
forum: Multimedia Software
---

### Post by madejo on 2010-01-24
Hello fellows,

I am a relatively new user of ubuntu.I have installed Ubuntu 9.10
- the Karmic Koala and in general terms everything seems to be working fine. 

Though at the moment i am dealing with 2 issues:

1. I have onboard Nvidia's GeForce 9600GT and i have installed the recommended drivers for ubuntu {system-)administration-)hardware drivers-)nvidia aceelarated driver version 185.

Graphics and visual effects seem to work but under the following constrain. 
When i open a normal .avi file (or another video format) sometimes colors are twisted. By that i mean white doesn't look white, red appears green etc. In other words colors seem twisted. 
The strange thing about that is that it doesn't happen every time even when i test it with the same file. I cannot predict when it will happen again. So i was wondering if anybody has any idea of what is going wrong and how can i fix it.

2. i cannot find a software to extract rar files. Any suggestions. I have tried arc software but i cannot extract rar files yet.
Any suggestions???

Thank you in advance fellows.

Cheers

---

### Post by inobe on 2010-01-24
welcome to the forums

the first thing to do is run the system updates if you haven't already done so !

the second thing is to get restricted extras, it has multiple packages including one that will extract .rar files.

assuming your attempting to play a video format and are experiencing distortion' you may be able to resolve it also with restricted extras.

go to system> administration> synaptic

search for **ubuntu-restricted-extras** and select then install.

---

### Post by manoriax on 2010-01-24
If that "strange-color-thing" is not fixed by the restricted-extras, check this out: [http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu](http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu)

---

### Post by madejo on 2010-01-24
> **manoriax said:**
> If that "strange-color-thing" is not fixed by the restricted-extras, check this out: [http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu](http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu)


Actually the problem i had just described before is exactly like the one your link is presenting....

Well done you diagnosed it accurately. Thank you so much.

I wish though the solution to be applied for vlc player.

Anyway i will test it through.

Cheers

Nick

---

### Post by madejo on 2010-01-24
hey guys,

check this, it appears that the problem is related to HUE settings which need to be 0 insted of anything else

[https://bugs.launchpad.net/totem/+bug/395476](https://bugs.launchpad.net/totem/+bug/395476)

the thing is how to apply this value permanently since every time i open a new video HUE value is changing back again.

Any suggestions??

PS: i am mostly interested in vlc player solution

cheers

---

