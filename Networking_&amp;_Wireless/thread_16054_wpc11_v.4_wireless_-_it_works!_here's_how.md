---
title: "wpc11 v.4 wireless - it works! here's how:"
date: 2005-02-18
forum: Networking &amp; Wireless
---

### Post by sounddoc on 2005-02-18
i thought i'd post here how i got my linksys wireless card (WPC11, version 4) to work under ubuntu. you'll need the following;

ndiswrapper. 

wireless-tools (iwlist, iwconfig, iwspy, etc...)

dhclient.

except for wireless tools, i think the others are both installed with a standard ubuntu setup.

WARNING*****
i am by no means an expert in linux or wireless networking. in trying to get my wireless card to work, i came across a lot of sites that said that this particular card, the WPC11 Version 4, will never work with any distro of linux. that was a challenge for me ;) keep in mind that if your computer spawns hell-monkeys, puts a republican in office in 2008, or any other such nastiness, i am not responsible! if anybody has any suggestions, clarifications or comments, please POST THEM HERE! or write me at [email]pkemble@gmail.com[/email]

that said, here it is:


let's say for example that my router is broadcasting on channel 6 and the SSID is "ubuntu". i do not secure it as of now, as i'm still learning with this stuff, but i think that wireless-tools comes with enough info to set that up (extra iwconfig options)

first ndiswrapper is a must. get the windows driver (i used the WindowsXP driver from the linksys website [ftp://ftp.linksys.com/pub/network/WPC11v4_SW2.2.zip](ftp://ftp.linksys.com/pub/network/WPC11v4_SW2.2.zip) ). extract it in /var/tmp or something.

the file i used was called LSWLNDS5.INF. So, here we go, try these commands:

ndiswrapper -i LSWLNDS5.INF

ndiswrapper -m (to make it load at boot time)

iwconfig wlan0 channel 6 essid "ubuntu"

dhclient wlan0

and that should do it! for ease i put the last two commands in a small script in my home directory to activate it.

the following commands might be needed the first time, i'm not sure. i read that these helped when trying to initally set up the card, so i did them, but it might have been a first-time only type setup, or might not be needed at all. if the commands up top don't work, try these in addition the first time:

ifconfig wlan0 up

route add default gw 192.168.1.1 (this should be the IP of the router)

dhclient wlan0

---

### Post by songochain on 2005-02-20
Hi! I've installed windows drivers and ndiswrapper -l says: ```
songochain@ximian64:~$ ndiswrapper -l
Installed ndis drivers:
sis162u driver present, hardware present

``` but when i do a modprobe ndiswrapper, linux freeze and i've to do a reset.
When i do iwconfig:```
songochain@ximian64:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

sit0      no wireless extensions.

```
I supuse that sit0 is something related with wireless?
Thanks

---

### Post by sounddoc on 2005-02-21
i've only gotten the linksys wpc11 version 4 card to work. are you using the windows drivers for your card with ndiswrapper? some things to try, try also the windows 2000 or windows 98 versions of the drivers. the drivers i used came right from the linksys website, for windows XP, WPC11 version 4 (wireless B adapter)

good luck!

---

### Post by songochain on 2005-02-21
LOL dude the driver that i use it was for win32bits version but i'm using hoary for amd64, so i have to wait until sis realeases a driver for winxp 64bits
See u

---

### Post by Imagist on 2005-02-21
If it wouldn't be too hard, would you write out an explanation of how to do this really simply for a newbie to linux?  I finally got linux to install, but I can't get my Wireless B notebook adapter to work, mainly because I haven't the slightest idea how to install the ndiswrapper.

---

### Post by songochain on 2005-02-21
[QUOTE=Imagist]If it wouldn't be too hard, would you write out an explanation of how to do this really simply for a newbie to linux?  I finally got linux to install, but I can't get my Wireless B notebook adapter to work, mainly because I haven't the slightest idea how to install the ndiswrapper.[/QUOTE]
 Ok dude :) firts if u use i386 version of ubuntu (not amd64, in this case, u've to compile sources like me):
1) sudo apt-get install ndiswrapper
2) and if all it was ok, sudo ndiswrapper -i your_windows_driver.inf
3) sudo modprobe ndiswrapper
4) ndiswrapper -m (to make it load at boot time)
5) configure your wlan :) (u can do it with network-admin)
Hope this help u
See u

---

### Post by Imagist on 2005-02-22
Okay, so I've copied both the folder containing ndiswrapper and the folder containing my windows driver into a file on my desktop called "Network Driver."  I then try step 1 from above, and it says it can't find the package.  Help?

---

### Post by songochain on 2005-02-22
[QUOTE=Imagist]Okay, so I've copied both the folder containing ndiswrapper and the folder containing my windows driver into a file on my desktop called "Network Driver."  I then try step 1 from above, and it says it can't find the package.  Help?[/QUOTE]
 Well, what version of ubuntu have u? i386 or amd64?? if u has i386 version u dont need a folder with ndiswrapper source because u can install it using synaptic or typing in a console: sudo apt-get install ndiswrapper.
If u have a amd64 version, go to folder when u have ndiswrapper (in a console) source and then type: tar xvfz ndiswrapper*. Then cd ndiswrapper* and make && make install. To do this u must have kernel headers and kernel restricted packages of your kernel (uname -a to know what kernel u have. Use synaptic to download all).
Then > 2) and if all it was ok, sudo ndiswrapper -i your_windows_driver.inf
3) sudo modprobe ndiswrapper
4) ndiswrapper -m (to make it load at boot time)
5) configure your wlan  (u can do it with network-admin)
See u!
PD:sorry for my poor english

---

### Post by Imagist on 2005-02-22
[QUOTE=songochain]Well, what version of ubuntu have u? i386 or amd64?? if u has i386 version u dont need a folder with ndiswrapper source because u can install it using synaptic or typing in a console: sudo apt-get install ndiswrapper.
If u have a amd64 version, go to folder when u have ndiswrapper (in a console) source and then type: tar xvfz ndiswrapper*. Then cd ndiswrapper* and make && make install. To do this u must have kernel headers and kernel restricted packages of your kernel (uname -a to know what kernel u have. Use synaptic to download all).
Then 
See u!
PD:sorry for my poor english[/QUOTE]
 I have the i386 version, but whenever I try "sudo apt-get install ndiswrapper" it says:

Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package ndiswrapper

Sorry to bother you.

---

### Post by Imagist on 2005-02-22
Nevermind, I was able to get both steps 1 and 2 done.  Now when I do "sudo modprobe ndiswrapper" it says "FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-2-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted"

The previous error messages I had some idea of how to fix them.  This one I'm entirely lost.

---

### Post by keeee on 2005-02-23
It's kernel 2.6.10 that gives you that error, with kernel 2.6.8 ndiswrapper should work fine.

---

### Post by songochain on 2005-02-23
[QUOTE=Imagist]Nevermind, I was able to get both steps 1 and 2 done.  Now when I do "sudo modprobe ndiswrapper" it says "FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-2-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted"

The previous error messages I had some idea of how to fix them.  This one I'm entirely lost.[/QUOTE]
 Hi dude, if u dont find ndiswrapper it causes because u've to uncomment some lines in your source.lst Try with universe and multiuniverse lines (if u've this last line) and then sudo apt-get update, sudo apt-get install ndiswrapper. I dont use i386 version so i dont know where ndiswrapper is.
U cant do sudo modprobe ndiswrapper (u will get a error like yours) until u've installed windows driver using ndiswrapper. I think u will have to install kernel headers and kernel restricted (if u've a 2.6.10-3 kernel, kernel-restricted-2.6.10-3 for example)
Sorry dude for my english but i cant write better
See u

---

