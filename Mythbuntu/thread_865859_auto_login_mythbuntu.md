---
title: "auto login mythbuntu"
date: 2008-07-21
forum: Mythbuntu
---

### Post by phillipcc on 2008-07-21
hi forum can someone tell me how to make mythbuntu auto login instead of that boring welcome menu where you must put your username and password i am using lastest version of mythbuntu any help most appreciated thanks
phillip

---

### Post by quackquack on 2008-07-21
im not sure if this works in mythbuntu, but in regular ubuntu you go to

system > administration > login window 

and click on the security tab, then you tick "enable automatic login" and then select your user name from the drop-down menu.

---

### Post by .nedberg on 2008-07-21
Applications -> System -> Mythbuntu Control Centre -> Artwork & Login Behavior

---

### Post by phillipcc on 2008-07-22
hi all got this problem fixed thanks to all who replied 
phillip

---

### Post by Gadgetman on 2009-06-09
My Mythbuntu installation always prompts for login! 

I have tried 3 approachs...
The 1st being using 
Applications -> System -> Mythbuntu Control Centre -> Artwork & Login Behavior and it is already set to "auto login" and the original user that I built the Mythbuntu is selected. However it doesnt auto-login!!

The 2nd approach is using 
system > administration > login window 
This too is setup to auto-login , but still propmts for login.

The 3rd approach edit
/etc/gdm/gdm-cdd.conf

[daemon]
#automatic login behavior
AutomaticLoginEnable=true
AutomaticLogin=gadget
TimedLoginEnable=true
TimedLogin=gadget

All 3 look appear to be correct, yet it still prompts for login!!

What is problem here??

All help appreciated.....THANKS

---

### Post by chipppy on 2009-11-11
Good Evening

This is an existing problem read thread 
[http://ubuntuforums.org/showthread.php?t=1308845&highlight=auto+login]("http://ubuntuforums.org/showthread.php?t=1308845&highlight=auto+login")

I have the same issue

Cheers
chipppy

---

