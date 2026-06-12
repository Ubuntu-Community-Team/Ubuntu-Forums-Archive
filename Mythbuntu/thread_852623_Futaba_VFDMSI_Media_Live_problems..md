---
title: "Futaba VFD/MSI Media Live problems."
date: 2008-07-07
forum: Mythbuntu
---

### Post by jmail524 on 2008-07-07
I am having a miserable time getting the VFD on my MSI MediaLive to work with Mythbuntu 8.04.

I have downloaded the latest Futaba source and compiled/installed it using the instruction from the Futaba/Myth Wiki.  When I run "sudo LCDd" the VFD screen shows me:

     LCDProc Server
     Cli:0 Scr:0

However, the screen never changes no matter what I do in Mythbuntu.  I have configured the LCD in the Mythbuntu/Setup screen. I don't know what to try now.

Thanks.
Brian

---

### Post by dan_linder on 2008-07-15
Did you happen to try the steps in this link:
[http://www.mythtv.org/wiki/index.php/Futaba]("http://www.mythtv.org/wiki/index.php/Futaba")

I'll be getting a MSI Media Live MS-6421 ([http://www.mythtv.org/wiki/index.php/MSI_Media_Live]("http://www.mythtv.org/wiki/index.php/MSI_Media_Live")) with one of these displays shortly.  If I get it to work I'll try to report back.

Dan

---

### Post by mastermrp on 2008-09-05
Hi,

I had the same problem getting my VDF running on my MSI MediaLive.
I recognized some things.
At first I've done the same as jmail524 did.
And how could it else be. I had the the following Problems.

1. When I rebooted my Mythbuntu 8.04 the VFD stayed black.
2. Then I did a "sudo killall LCDd" an a "sudo LCDd" and the VDF illuminated with the text: 

LCDProc Server
Cli:1 Scr:7

3. After starting Mythtv the panel still showed the same message.
4. But when I switched to Live TV the panel began to show TV information.
5. Turning back to the Main menu the Panel worked as it should do.

So far so good. But when I rebooted everything started at point 1.

To skip point 2. (killall and restart LCDd) I disabled LCDd in run level 2, 3 and 4. Now it only starts at run level 5 and shows:
LCDProc Server
Cli:1 Scr:7
after a Mythbuntu reboot.
To get the VDF show Mythtv information I have to switch to Live TV and back to the Main menu. Then everything is ok.
For the moment this state is enough for me, but if someone knows how to get the VDF show the Mythtv information from the beginning after a reboot it would be nice if you will tell.

Hope this will help a bit.

MasterMRP

Sorry for my bad English. I hope it is understandable.

---

