---
title: "Leadtek DTV1800 H Support"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by reidy90 on 2007-12-23
I am a big fan mythtv and have enjoyed watching analog tv through my Leadtek tv2000xp deluxe card and the improvements a stable media center and reliable program data bring. 

I decided this could be further improved by adding a second digital tuner. I purchased a Leadtek DTV1800 H. I bought it thinking it would be similar enough to the DTV1000 (which is currently supported under Linux) so it would have the correct driver modules. The card I purchased was also the same price as a DTV1000 but also included a second analog tuner on the same board. 

Unfortunately the support is a bit flakey. It is detected by the Hardware Information applet as a video capture device, so I assume the correct modules are installed by default for it. However under mythtv, (scrolling through the top menu of "capture cards" in the mythbackend) it appears under:
[LIST]
[*]Analog V4L Capture Card (Would this be picking up its internal analog tuner correctly?)
[*]MJPEG Capture
[*]and pcHDTV capture card
[/LIST]
each time appearing as a "UNKNOWN/GENERIC [cx8800]"

To make the problem even more difficult there are 4 inputs on the card (composite1, composite2, ...etc) 

No matter what options I try cannot pick up a TV signal :(

Does anyone else have this tv card and have it wotking in mythtv? Does anyone know the right options I should use to pick up a digital tv signal? I have done some googling myself on the issue but there isn't much information out there on using this card under Linux. Is it going to be easier to just swap the card over for a DTV1000?  

I have tried to describe in some detail to help diagnose the problem easier but if any other information is required I can gput it into a follow up post.

Your help is greatly appreciated!

---

### Post by vector on 2008-06-03
anybody got any further on this? id like to know if a dvt1800 can work with ubuntu 8.04

---

### Post by tango11 on 2008-07-02
I'm having the same problem with myth however i did get the picture working with tvtime but cant get sound working yet

---

### Post by jezzbo on 2008-07-09
I also have this card and have not been able to get kdetv or mythtv to pick up a signal, anyone have any more luck with this?

---

### Post by jezzbo on 2008-07-09
Ah ha! Its working :D
Followed the [[translated]("http://translate.google.com.au/translate?hl=en&sl=cs&u=http://www.abclinuxu.cz/show/195174&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dcx2388x%2Bdtv1800%2Bubuntu%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-GB:official%26hs%3Dw7l%26sa%3DG")] instructions from [this site]("http://www.abclinuxu.cz/show/195174").
A basic rundown:
1) Download repository source:
```
hg clone -r 55d60e988b89 http://mcentral.de/hg/~mrec/v4l-dvb-kernel/
```

2) Download patch [here]("http://64.233.179.104/translate_c?hl=en&sl=cs&u=http://www.abclinuxu.cz/data/prilohy/5/4/98945-leadtek_dvt1800h-5612.patch&prev=/search%3Fq%3Dcx2388x%2Bdtv1800%2Bubuntu%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-GB:official%26hs%3Dw7l%26sa%3DG&usg=ALkJrhigVYCpYLpj01RcsTYLwQqvBd2_hQ").

3) Copy the patch file to the v4l-dvb-kernel directory.

5) Apply the patch file:
```
patch -p1 < leadtek_dtv1800h.patch
```

6) Compile and install modules
```
make
sudo make install
```

7) I then had to reboot but the original guide seems to think reloading the modules would work:
```
modprobe cx88xx
modprobe cx8800
modprobe cx8802
```

8 ) I also downloaded and extracted firmware from [here]("http://mcentral.de/firmware/firmware_v5.tgz") to /lib/firmware.
```
tar -xzvf firmware_v5.tgz -C /lib/firmware/
```

After a reboot, kaffeine picked up the card and scanned in all channels!

---

