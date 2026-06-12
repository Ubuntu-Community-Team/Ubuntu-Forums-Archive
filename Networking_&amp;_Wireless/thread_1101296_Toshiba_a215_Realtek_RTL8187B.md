---
title: "Toshiba a215 Realtek RTL8187B"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by pimpinjg on 2009-03-20
ok well i installed ubuntu on my toshiba a215 im running 8.10 intrepid my wireless drivers were supported by default when i installed (yay!) but randomly and i mean randomly wireless will disconnect wich never happened in _windows_ (<- -.-") it wont stay connected more than 2 hours without dropping then i need to reboot


Lsusb
```
pimpinjg@alexis:~$ lsusb
Bus 006 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
pimpinjg@alexis:~$ 

```

iwconfig

```

pimpinjg@alexis:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"LOLWIRELESS"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:81:10:D0   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=60/100  Signal level:-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
pimpinjg@alexis:~$

```

anything else needed post it here if i have to go back to windows there will be a smashed toshiba laptop on the floor

thanks :D

---

### Post by pimpinjg on 2009-04-26
After a quick email to realtek and a 3 day wait i was supplied with the linux drivers for this card! and sense they havent been posted on this forum yet ive attatched them with readme 


the reply received from Realtek

"Dear Sir,

Thanks for your e-mail, attached file please find RTL8187B latest linux driver source for you reference.

Regards,

Fred"


if i helped you out reply!

---

### Post by Neodarkness on 2009-04-27
Great! I've had this issue since Hardy. Back then my wireless worked flawlessly with the windows driver and ndiswrapper. Intrepid made it work out-of-the-box but with the issue you mentioned. I was too lazy to figure out ndiswrapper with intrepid or jaunty. I'll try this and report back.
BTW, i'm on the satellite a215-s7437, same as yours? How is your video card doing? Mine is flickering like hell since Jaunty...
Regards

---

### Post by Ropechoborra on 2009-04-27
> **pimpinjg said:**
> After a quick email to realtek and a 3 day wait i was supplied with the linux drivers for this card! and sense they havent been posted on this forum yet ive attatched them with readme 


the reply received from Realtek

"Dear Sir,

Thanks for your e-mail, attached file please find RTL8187B latest linux driver source for you reference.

Regards,

Fred"


if i helped you out reply!

Excelent ! Now is working ! :) Thank you very much.

---

### Post by Neodarkness on 2009-04-27
I compiled it using make and checkinstall. The installed de .deb, and after reboot no wireless (I don't know how to connect using the command line, only tried through network-manager).
Any ideas?

---

### Post by pimpinjg on 2009-04-27
> **Neodarkness said:**
> Great! I've had this issue since Hardy. Back then my wireless worked flawlessly with the windows driver and ndiswrapper. Intrepid made it work out-of-the-box but with the issue you mentioned. I was too lazy to figure out ndiswrapper with intrepid or jaunty. I'll try this and report back.
BTW, i'm on the satellite a215-s7437, same as yours? How is your video card doing? Mine is flickering like hell since Jaunty...
Regards

Yeah i had that problem too if your not to worried about desktop effects, i.e you dont use compiz and you like a more simple gnome desktop go to appearance > visual affects > none

or install fluxbox :p

> **Ropechoborra said:**
> Excelent ! Now is working ! :) Thank you very much.

Your welcome!

> **Neodarkness said:**
> I compiled it using make and checkinstall. The installed de .deb, and after reboot no wireless (I don't know how to connect using the command line, only tried through network-manager).
Any ideas?

Download the drivers to your desktop then follow like this:


cd Desktop 
mv rtl8187B_linux_26.1052.0225.2009.release.tar.gz ..
cd ..
tar -xvf rtl8187B_linux_26.1052.0225.2009.release.tar.gz
cd rtl*
sudo make
sudo make install
(remember to blacklist the old driver that comes default with ubuntu..)
sudo reboot

Now the new drivers should be manageable via gnome network manager ;)

thats how i did it and its working fine if anyone else got results doing it a different way please do post how you did it!

---

### Post by Neodarkness on 2009-04-27
HEHEHE, Sorry for asking dumb questions, but how do I blacklist the old driver?, and how do I find out the name of the old driver?
Thanks!

---

### Post by pimpinjg on 2009-04-27
> **Neodarkness said:**
> HEHEHE, Sorry for asking dumb questions, but how do I blacklist the old driver?, and how do I find out the name of the old driver?
Thanks!


well if your using the drivers that come default with the latest release of ubuntu youll be using the rtl8187 drivers with native rtl8187b support but they suck and are drastically unstable, to see if your running the unstable driver do this:

dmesg |grep 818

if you get an output like loaded rtl8187: detected driver rtl8187 and it says its expiremental or something like that you have the default ubuntu drivers just type 

sudo nano /etc/modprobe.d/blacklist

and at the end of the line just add something like this:

# old drivers
blacklist rtl8187 then exit out of nano and sudo reboot when you reboot your drivers should be ready to go


:P

---

### Post by Neodarkness on 2009-04-27
Finally got it working! (had to install wicd, cause network-manager won't work with the new driver).
Thanks man!
BTW, somehow the installation changed my wifi name from wlan0 to wlan1, so network manager won't work and conky needed changing (curious).

---

### Post by pimpinjg on 2009-04-27
> **Neodarkness said:**
> Finally got it working! (had to install wicd, cause network-manager won't work with the new driver).
Thanks man!
BTW, somehow the installation changed my wifi name from wlan0 to wlan1, so network manager won't work and conky needed changing (curious).

Yeah it got changed to wlan1 because you installed the new driver before blacklisting the old ones and rebooting :p post what you did exactly so other people can follow the steps and get it working like you did ^^

---

### Post by Roasted on 2009-04-27
You guys know how long I fought trying to get the 8187B working with the A215? It got to the point I gave up, stuck with XP on the laptop, got bored of the laptop because XP is boring to me, and ended up giving the laptop (XP Pro installed) to my girlfriend who has been using it ever since, since she doesn't have a computer and I had about 7. :lolflag:

Glad to hear fellow A215 users are working wirelessly with Ubuntu now. Wish I coulda gotten it working on mine, but, ahh... I have a Precision M4300 by Dell that work supplied me with, so I dual boot that sucker and wireless works there too. :)

Does the A215 support WPA/WPA2 security with the drivers Realtek supported?

---

### Post by pimpinjg on 2009-04-27
> You guys know how long I fought trying to get the 8187B working with the A215? It got to the point I gave up, stuck with XP on the laptop, got bored of the laptop because XP is boring to me, and ended up giving the laptop (XP Pro installed) to my girlfriend who has been using it ever since, since she doesn't have a computer and I had about 7.

Glad to hear fellow A215 users are working wirelessly with Ubuntu now. Wish I coulda gotten it working on mine, but, ahh... I have a Precision M4300 by Dell that work supplied me with, so I dual boot that sucker and wireless works there too.

Does the A215 support WPA/WPA2 security with the drivers Realtek supported?


Thats what the readme inside the tar said that i got from realtek but i havent tried it myself i dont even use wep because i have wifi access filtering for certain mac's so im not worried about kids getting on my network :p

and yeah i got mad too i hate windows been running linux on every computer ive had so far (even my p3 128 mb ram dell runs debian :P)

but hopefully this thread will save people alot of time i went looking for days before i thought to myself why dont i email the vendor and ask for linux drivers and then he supplied i was rather happy 

note: i dont run ubuntu i run mint close enough to the same so i figured id post here

edit: neodarkness i tried running wicd with the realtek drivers on ubuntu jaunty jackalope and the internet is so slow its unbareable is it working ok for you? 

Regards

---

### Post by SpideRius on 2009-04-28
[LEFT]great thanks, it works! your help and deleting the default network-manager
[/LEFT]

---

### Post by pimpinjg on 2009-04-28
> **SpideRius said:**
> [LEFT]great thanks, it works! your help and deleting the default network-manager
[/LEFT]

Ugh i dont really understand your question can you rephrase?

---

### Post by TraBruno on 2011-04-09
Hello,

I downloaded the driver and followed the instructions but 'make' and 'make install' renders error messages and there is no change at all.

This is what I get with 'make':
```
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_softmac.o
  CC [M]  /home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/dot11d.o
  CC [M]  /home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_rx.o
  CC [M]  /home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_tx.o
  CC [M]  /home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_wx.o
  CC [M]  /home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_module.o
/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_module.c: In function ‘alloc_ieee80211_rtl’:
/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_module.c:121: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [all] Error 2
```

And then 'make install':
```
kernel/drivers/net/wireless/rtl818x/rtl8187.ko: kernel/net/mac80211/mac80211.ko kernel/drivers/leds/led-class.ko kernel/net/wireless/cfg80211.ko kernel/drivers/misc/eeprom/eeprom_93cx6.ko
make[1]: Entering directory `/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211'
make -C /lib/modules/2.6.35-28-generic/build M=/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211 CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_module.o
/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_module.c: In function ‘alloc_ieee80211_rtl’:
/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_module.c:121: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[3]: *** [/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_module.o] Error 1
make[2]: *** [_module_/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211'
make: *** [install] Error 2
```

I'm not an expert so these messages don't really speak to me. Anyone any suggestions? I have abandoned ubuntu once for this same problem years ago and would like to give it another try now. A lot of stuff got better, but wifi is still very unstable with this realtek driver.

Thanks in advance,
B

---

