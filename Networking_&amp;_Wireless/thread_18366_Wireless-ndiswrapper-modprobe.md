---
title: "Wireless-ndiswrapper-modprobe"
date: 2005-03-06
forum: Networking &amp; Wireless
---

### Post by Patrol on 2005-03-06
Hi, I have a problem when I try to use my wireless card ( linksys WMP45G).
I downloaded a recent version of ndiswrapper and installed it ( I already got a problem there because I had to give the path to kernel sources for make && make install. Is it normal ?. I gave the path and that did the trick).
I made "ndiswrapper -i filename.inf" to install the driver.
With "ndiswrapper -l", I saw that my driver was well installed.
The problem appears when I type : "modprobe ndiswrapper". I get : "FATAL: Error inserting ndiswrapper
 (/lib/modules/2.6.8.1-3-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid module format"
I tried to reinstall the ndiswrapper package but there was no change.
I downloaded and installed the kernel sources ( 2.6.8.1), without success.
I see I'm not the only one with this problem. 
Maybe I have a problem with my kernel sources. I tried to find kernel sources for 2.6.8.1-3-386 but I only found 2.6.8.1 -> is it essential to find 2.6.8.1-3-386 for my problem?
I have been looking for it for 3 days now and I  don't know what to do. 
I hope you will help me.
I am not very qualified in this field.
(sorry for my English...)

---

### Post by BiGBuG on 2005-03-07
download wireless-tools too and try...

ndiswrapper -m

this solved my issues, -m tell to modprobe how to load ndiswrapper module.

---

### Post by Patrol on 2005-03-07
I'll try , thank you

---

### Post by jimmt on 2005-03-07
When I compiled the ATI and ALSA modules for my kernel under Ubuntu I had to link my GCC to GCC.295 in order  to resolve this problem. The issue is the kernel is compiled using a different version of GCC than the version you are using to compile the ndiswrapper module.  

To link do the following ln -s /usr/bin/gcc-2xx /usr/bin/gcc

If that version does not work try a different version till you get the one that your kernel was compiled with. Good idea to apt-get all versions of GCC. 

Jim

---

### Post by burlap on 2005-03-07
If you use Warty, all you need is ndiswrapper-tools package as ndiswrapper module is included in the standard Ubuntu kernel. With this package you can simply do "ndiswrapper -i driver.inf" and "ndiswrapper -m" and set up your network with gnome-network or whatever app you prefer.

---

### Post by Patrol on 2005-03-07
@ Burlap & BiGBuG : I got the same error with modprobe...
@ jimmt : I get an error when I type "ln -s /usr/bin/gcc-2xx /usr/bin/gcc"
                (invalid command).

I thank you for your help.
It must be a detail... 
I wonder if it is not a problem with my kernel sources : look at the error message when I type "modprobe ndiswrapper" .
I use the 2.6.8.1-3-386 kernel but I only found 2.6.8.1 sources.
Perhaps it's the problem. I don't know.

---

### Post by burlap on 2005-03-07
Which ndiswrapper have you compiled?

> I use the 2.6.8.1-3-386 kernel but I only found 2.6.8.1 sources. 
2.6.8.1 sources are ok as long as you keep everything under control with apt/ synaptic (2.6.8.1-3-386 is a kernel package compiled from 2.6.8.1 sources). 

> I had to give the path to kernel sources for make && make install. Is it normal ? 
It is quite common to set path to kernel headers in different makefiles...

Try to uninstall ndiswrapper you compiled ("make uninstall" from the directory you compiled ndiswrapper). Try to insert the module now. If there is no ndiswrapper at all, try to reinstall kernel package and ndiswrapper-tools package. Forget about compiling for a while. Always try to find a package first (via Synaptic for expamle) and if that doesn't work, compile (unless you want bleeding edge software). 

(I have this "invalid module format" error with Hoary, but I do not normally use it, so no problem as long as Warty works fine. However I have seen somewhere - wiki? forum? - solution to this problem for Hoary).

---

### Post by jimmt on 2005-03-08
[QUOTE=Patrol]@ Burlap & BiGBuG : I got the same error with modprobe...
@ jimmt : I get an error when I type "ln -s /usr/bin/gcc-2xx /usr/bin/gcc"
                (invalid command).

I thank you for your help.
It must be a detail... 
I wonder if it is not a problem with my kernel sources : look at the error message when I type "modprobe ndiswrapper" .
I use the 2.6.8.1-3-386 kernel but I only found 2.6.8.1 sources.
Perhaps it's the problem. I don't know.[/QUOTE]

Sorry, replace "xx" with your version; example ln -s /usr/bin/gcc-2.95 /usr/bin/gcc 

In command line you can hit <tab> to auto fill what you are typing and to list possible choices.  Example: /usr/bin/gcc <tab key> will auto fill all things with gcc in it. THis is how you can get you exact version.

Jim

---

### Post by Patrol on 2005-03-08
I spotted the problem : my ndiswrapper-utils version was wrong ...
"Modprobe ndiswrapper" is OK. My wireless card is OK.
But I can't find any IP adresse and I can't enter any ESSID.
I don't see what to do.

---

### Post by Patrol on 2005-03-10
Please I need help. 
I don't understand why I can't enter my ESSID...

---

### Post by Patrol on 2005-03-11
I also noticed that when I enter *ifconfig *  I get "wlan0" and characteristics, but if I enter *iwconfig* , I don't have "wlan0" anymore. There must be the problem...

---

