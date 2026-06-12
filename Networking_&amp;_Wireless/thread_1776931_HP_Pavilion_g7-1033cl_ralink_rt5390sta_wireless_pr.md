---
title: "HP Pavilion g7-1033cl ralink rt5390sta wireless problem"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by R3cKL3SS_aM on 2011-06-07
[COLOR="Red"]First off i do realize this post has been issued/resolved before but i have tried everything possible and I am still having troubles.[/COLOR]

I just got a new laptop, Model: HP Pavilion g7-1033cl (64bit) and it has a Ralink RT5390STA wireless card.

Anyways...When i install Ubuntu 11.04 w/wubi.exe i am having troubles getting it to find my wireless connection, i have tried to manually enter in my SSID all that good jazz and still no success, i have also gone to "additional drivers" and it finds nothing. I have even google searched it and found some solutions but i seem to fail at following them.

Here is what i have been following: [http://atinfinity.wordpress.com/2011/05/21/ralink-rt5390-wi-fi-driver-on-ubuntu-11-04/](http://atinfinity.wordpress.com/2011/05/21/ralink-rt5390-wi-fi-driver-on-ubuntu-11-04/)
then when i get to entering the command into terminal i get "No such file or directory" 

[SIZE="4"]**Here is my main problem. Please help!**[/SIZE]
[img]http://gyazo.com/1abc3728f452b26263815734d51ad5ca.png[/img]

---

### Post by R3cKL3SS_aM on 2011-06-07
No one? Would really appreciate any and all tips/help!

---

### Post by chili555 on 2011-06-07
Your problem is a common one and simple to resolve. According to your terminal prompt:> eddie@ubuntu:~$The terminal is in your user directory, abbreviated in Linux-land as ~. That is not where the RT5370 Makefile and patches are located. So, first, you need to change directories (cd) to the correct location. Where did you download and extract the RT5370 files? To your desktop? To the folder called Downloads? Let's assume it's on your desktop. Then you need to do:```
cd Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
```If you then list the contents of the folder (ls) and you see the Makefile and all the patch files listed, you are good to go!```
ls
```Then run your patches as outlined in the tutorial you linked and continue with the compile and installation.

---

### Post by R3cKL3SS_aM on 2011-06-07
> **chili555 said:**
> Your problem is a common one and simple to resolve. According to your terminal prompt:The terminal is in your user directory, abbreviated in Linux-land as ~. That is not where the RT5370 Makefile and patches are located. So, first, you need to change directories (cd) to the correct location. Where did you download and extract the RT5370 files? To your desktop? To the folder called Downloads? Let's assume it's on your desktop. Then you need to do:```
cd Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
```If you then list the contents of the folder (ls) and you see the Makefile and all the patch files listed, you are good to go!```
ls
```Then run your patches as outlined in the tutorial you linked and continue with the compile and installation.

Thank you so so much. You just made my life 10x easier. Worked perfectly with no problems whatsoever.

---

