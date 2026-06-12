---
title: "S-Video Ubuntu 9.04 + Ubuntu 9.10 (Beta)"
date: 2009-10-02
forum: Multimedia Software
---

### Post by KingBongo on 2009-10-02
Hi. I am trying to connect my computer (Nvidia XT5500 card) to my old TV (CRT) via S-Video. I have tried both 9.04 and 9.10 (Beta) to no prevail. I can understand the 9.10 Beta version maybe isn't working, but what about 9.04? 

The situation is as follows. In the "Nvidia control center" (sorry, don't remember name) I can see two screens. But when I try to enable "Xview" (cloned screen, not TwinView) and then save the changes to the config file, I get a notification similar to "the XXX.backup file cannot be saved" and that was that.

What is wrong here? Do I have some kind of permissions problem or is something else wrong? This is on a completely fresh install by the way.

Please help me to resolve this issue and complete the mission. I really want to watch movies on my old TV.

PS. I am on another computer right now, therefore I don't remember everything exactly.

---

### Post by KingBongo on 2009-10-03
No help? Please!

---

### Post by DC^ on 2009-10-03
> **KingBongo said:**
> No help? Please!
Have you tried to update you Nvidia drivers ?
Which version you are using ?

---

### Post by KingBongo on 2009-10-03
I have the newest driver available from the "Hardware Drivers" administration tool, version 173. No worky.

PS. By the way, TwinView works.

---

### Post by jchambers on 2009-10-03
this thread here fixed all my issues - its kind of strange but the last one on the list sent 800x600 out to my tv - mine was working on the boot and than would stop when it went to the login screen - I hope yours works after this too - I am not excited about the resolution so far but one step at a time 

[http://ubuntuforums.org/showthread.php?t=1149711](http://ubuntuforums.org/showthread.php?t=1149711)

 	Code:
 	#!/bin/sh

xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard ntsc
xrandr --addmode S-video 800x600
xrandr --output S-video --same-as VGA-0
xrandr --output S-video --mode 800x600 
Save the file with the extension sh (for example screen_script.sh) and remember where you saved it. Then go to System > Preferences > Startup Applications > Add and select your script. Now it should run every time your computer boots up.

---

### Post by KingBongo on 2009-10-03
jchambers:
Thank you, will try. 

The part I don't understand is that it works perfectly in TwinView, but not with cloned screens. Why? I don't get it. What's the difference? How can it be so difficult to just clone a screen when I obviously have connection to the TV and all.

---

### Post by KingBongo on 2009-10-04
Ok. First of all, when trying the first command "jchambers" posted, "xrandr --output S-video --set load_detection 1" I get a similar error message as others have. I don't know how to resolve that.

Second, I tried installing Mythbuntu 9.10 Beta. There I got a picture, but only black and white. Tried to fix that, but no. Back to Ubuntu.

Third, I unplugged the S-Video cable from the back of my TV (into Scart) and put it into the side of my TV. Then my computer lost all contact with the TV, and removed the "TV-0" from the Nvidia X center (something like that), and I have not gotten any picture back at all (even after moving cable to the back of TV), not even during boot. When putting in a live CD (9.04) I could see some seriously flickering and distorted text.

Yes, I also tried the Mythbuntu installation again. It is on a completely different disk which is connected by unplugging the Karmic disk physically, so they must have different boot loaders. Mythbuntu is also lost. No picture any more.

What's going on? Did I change some settings on the card (hardware), for example changing from 50Hz (PAL) to 60Hz (NTSC). Wrong frequency sometimes gives you a seriously distorted picture like I had. Any ideas? This is driving me nuts!

PS. I really like(d) Linux, but this is getting out of hands. I have to struggle with everything I try: Graphics Card, Wireless, TV Out, you name it. Not funny!

---

