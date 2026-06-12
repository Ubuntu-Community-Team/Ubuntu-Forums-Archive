---
title: "How to get back to original xorg.conf/video settings?"
date: 2009-06-14
forum: Multimedia Software
---

### Post by BB2008 on 2009-06-14
Hi All:

I am a ubuntu user for about 10 months now - I am currently on 9.04. About 4 months ago, i setup my onboard graphics (ATI 3200 HD) in a  (ATI) crossfire configuration with ATI 3450 HD crossfire supported card. To do this, I had to make changes to my xorg.conf file and install latest ATI drivers, the details of which are available in this thread - [http://ubuntuforums.org/showthread.php?t=1028151](http://ubuntuforums.org/showthread.php?t=1028151).

Anyways, I have since realized that i am not happy with this configuration since it is unstable and leads to crashes. My problem is, I have no idea how to back out my changes and go back to the original config? Can some one please help me here?

Thanks in advance for looking!

---

### Post by mhgsys on 2009-06-14
open a terminal and type:

```

 sudo dpkg-reconfigure xserver-xorg


```

you might want to disable hardware drivers for that card first.

---

### Post by ringing on 2009-06-14
I was in the same situation not long ago.

First you need to get read of 'fgrlx' drivers, completely remove them. Don't be afraid, you'd be able to get them back installed any time you want.

Then you can either use direct way suggested by "mhgsys" or log in to "recovery move" and choose "Try to fix graphic errors". It usually creates a new xorg.conf with 'vesa' drivers enabled.

---

