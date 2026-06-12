---
title: "Sound issue on a Sony Vaio"
date: 2008-07-05
forum: Multimedia Software
---

### Post by dmf518 on 2008-07-05
I've been fighting with this issue since the 7.04 release and i STILL cannot for the life of me get this figured out. I've tried the comprehensive audio guide on this forum, i've tried the irc chat, and i've tried google, all to no prevail. My issue seems simple enough, but i just can't grasp what the problem is. Please take note of all of the issues that i list below before responding... there are several fixes that i've tried that have not worked, and i'm assuming it's because the helper didn't understand the whole story.

Problem: The computer is a sony vgn-cr120e/l (laptop), and i now have ubuntu 8.04 installed. The onboard speakers DO work, however they DO NOT work initially upon boot. To make them work, I have to plug a pair of headphones into the headphone jack, and then unplug them, and then the onboard speakers come on as if nothing was wrong in the first place. As I stated prior, the speakers DO work, i just have to hook up a set of headphones to activate them (i guess that's the right term). I'm hoping that this is a simple fix and that it's just an issue with some default setting I have to change to make the computer default to the onboard speakers rather than headphones.

If you think you have a solution, feel free to post it, any attempts to help are greatly appreciated. Please be very specific in your details- i'm not any kind of veteran with ubuntu, and i only know basic things to work my way around, so i'd rather you assume i know nothing and tell me every step if possible, just to avoid confusion and frustration.

Thanks again to anybody that can help, and to all who read this!
-Dave

---

### Post by dmf518 on 2008-07-20
Anybody have any ideas? I'm still working on this.... :(

---

### Post by dmf518 on 2008-08-21
bump

---

### Post by dmf518 on 2008-08-24
bump

---

### Post by dmf518 on 2008-08-28
bump

---

### Post by markbuntu on 2008-08-28
If your sound chip is a HDA you can try this thread:


[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by Crafty Kisses on 2008-08-28
Post the results of > lspci -v

---

### Post by dmf518 on 2008-08-28
> **markbuntu said:**
> If your sound chip is a HDA you can try this thread:


[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

:0 you are THE man... that worked. thaaaaanks! :)

---

### Post by Crafty Kisses on 2008-08-28
Glad we could help, please mark the thread as solved. :)

---

### Post by Armaniboy on 2008-09-06
Type ALSAMIXER

then when it says external or ext boost at the far right...unmute it or mute it and it should work :)

---

