---
title: "Wireless on a ASUS U-56e"
date: 2012-04-22
forum: Networking &amp; Wireless
---

### Post by apgujohn on 2012-04-22
Hello!

I'm a newbie to Ubuntu and Linux so I wholeheartedly apologize if this question is really, really ridiculously basic and/or has already been covered.

So I recently tried to connect to a wifi hot spot and couldn't. I found a fix on this forum. Basically, all I had to do was enter these commands:

sudo modprobe -r iwlagn
sudo modprobe iwlagn bt_coex_active=0

Once I have entered these commands it works like a charm. Sadly, once I restart my computer, it doesn't work and I have to re-enter the commands. 

So I found another thread that said to make the changes permanent I must enter this: 

gsku gedit /etc/modprobe.d/iwl.conf

Copy/paste this line into the new file:
options iwlagn bt_coex_active=0

Save and quit.


I have absolutely no idea what the poster means by this and nothing comes up when I try to enter the first line into the terminal. I haven't been able to figure it out.

Thanks for the help!

---

### Post by chili555 on 2012-04-22
No apologies necessary; we were all new once, even me!> I have absolutely no idea what the poster means by this and nothing comes up when I try to enter the first line into the terminal. I haven't been able to figure it out.I hope you meant *gksu* and not:```
[COLOR="Red"]gsku[/COLOR] gedit /etc/modprobe.d/iwl.conf
```Additionally, I suggest the file be named iwlagn.conf. So, please open a terminal and do:```
gksu gedit /etc/modprobe.d/iwlagn.conf
```You should get a pop-up asking for your password; only the super-user can permanently edit configuration files. After entering your password, the text editor gedit will open a new empty file. Enter the text all on one line:```
options iwlagn bt_coex_active=0
```Proofread carefully, save and close gedit. Please see attached.

Upon reboot, you should be all set. If it doesn't go as perfectly as I described, certainly post back and I'll be happy to help.

---

### Post by apgujohn on 2012-04-22
Thank you kindly!

:guitar:

---

### Post by apgujohn on 2012-05-01
Alright,

This worked like a charm. My system, and particularly my wireless connection, were running like a finely engineered European sports car. Everything was going great. Then I got cocky and decided to upgrade to 12.04. After the upgrade, my wireless situation has reverted to what it was before. My computer is able to find networks, but unable to connect to them.

I'm running an Asus U-56e system which has an Intel Centrino Wireless-N + WiMAX 6150 wireless card. Anybody know what's going on here?

---

### Post by chili555 on 2012-05-01
> After the upgrade, my wireless situation has reverted to what it was before. My computer is able to find networks, but unable to connect to them.Is the file above still in place?```
ls /etc/modprobe.d
```If it is, please amend it because the name of the module is changed. It now needs to read:```
options [COLOR="Red"]iwlwifi[/COLOR] bt_coex_active=0
```Does it work well now?

As a side note, iwlwifi doesn't work well with 802.11N and we may need to disable N as well.

---

### Post by apgujohn on 2012-05-01
> **chili555 said:**
> 
As a side note, iwlwifi doesn't work well with 802.11N and we may need to disable N as well.

Works well so far! Thanks again, kind stranger. :)

By the way, what do you mean by disable the N? Newbie :confused:

---

### Post by chili555 on 2012-05-01
The driver iwlwifi, formerly known as iwlagn, evidently chokes trying to associate with 802.11N routers and will connect but not pass any traffic. If you, like me, have no N router, it's no problem at all. If you do, you probably already know about and have solved the issue. If needed, we can add another parameter to the .conf file: 11n_disable=1

---

