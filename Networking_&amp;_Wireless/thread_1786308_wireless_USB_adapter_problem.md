---
title: "wireless USB adapter problem"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by B.Ingimarsson on 2011-06-19
i just installed ubuntu 8.04 on my computer, now everything is working fine except for my wireless USB network adapter(Trendnet TEW-649UB) is not showing up in network settings, i would really like to get it to work so i would presiate any ideas you have :)

im from iceland so dont blame me for my bad english :D

---

### Post by bkratz on 2011-06-19
> **B.Ingimarsson said:**
> i just installed ubuntu 8.04 on my computer, now everything is working fine except for my wireless USB network adapter(Trendnet TEW-649UB) is not showing up in network settings, i would really like to get it to work so i would presiate any ideas you have :)

im from iceland so dont blame me for my bad english :D



8.04 is not supported anymore-any chance of using a newer version?  My Trendnet (mine is the 424) automatically worked in 10.04. The newest version is 11.04.

---

### Post by B.Ingimarsson on 2011-06-19
> **bkratz said:**
> 8.04 is not supported anymore-any chance of using a newer version?  My Trendnet (mine is the 424) automatically worked in 10.04. The newest version is 11.04.
thank you for answering quickly, i got the 10.04 iso file but my laptop which is the only computer in the house with a cd burner doesnt want to burn it so i will try installing through usb key

---

### Post by B.Ingimarsson on 2011-06-20
i installed 10.10 instead but still it does not seem to be working (there is no light on the adapter), im a linux noob :)

---

### Post by Plumtreed on 2011-06-20
No light suggests that there may be a bad connection or the adaptor is faulty......it seems to me that the light should at least blink to suggest it is connected.

Is it a USB connection? How old is your computer?

---

### Post by B.Ingimarsson on 2011-06-20
> **Plumtreed said:**
> No light suggests that there may be a bad connection or the adaptor is faulty......it seems to me that the light should at least blink to suggest it is connected.

Is it a USB connection? How old is your computer?
The adapter worked fine in win XP on same computer, it is Dell OptiPlex GX260 tower, built february 19, 2003 :grin:

---

### Post by Plumtreed on 2011-06-20
Right click on the NetworkManager, go to broadband, click on add and follow the steps.....

...or heve you done that????

---

### Post by B.Ingimarsson on 2011-06-20
> **Plumtreed said:**
> Right click on the NetworkManager, go to broadband, click on add and follow the steps.....

...or heve you done that????

nope, but i tried adding under wireless, this is a network adapter not broadband

---

### Post by Plumtreed on 2011-06-20
Oops sorry, the other thing to try is to run 'hardware Drivers' to see if that will provide any drivers you may need.

---

### Post by B.Ingimarsson on 2011-06-20
I tried to remove the usb an plug it in again then ubuntu messaged "you are now offline" so i think ubuntu does detect it
as network adapter but im not sure what kind of security i have(wep something), is there no way to get list of wireless networks in range like in windows ?

---

### Post by B.Ingimarsson on 2011-06-20
the wireless interface is disabled, when typing sudo lshw -C network i get:
```
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:08:74:f9:73:29
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k6-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:18 memory:ff8e0000-ff8fffff ioport:ecc0(size=64)
  ***-network _DISABLED_**
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:d1:bc:7b:c9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
brynjar@OptiPlex-GX260:~$ 
brynjar@OptiPlex-GX260:~$ 


```
does anyone know how to enable it ? :D

---

### Post by walt.smith1960 on 2011-06-20
Here is a link to a bug report/fix.  Note the error messages in dmesg.  If yours is similar, creating a folder and copying the firmware file should make it work in either 10.04 or 10.10.  This fix has worked for me on a couple different machines.  The adapter should work out of the box in 11.04 and later.
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

---

### Post by B.Ingimarsson on 2011-06-20
thank you that worked... mostly, but i cant connect to any sites like google and ubuntu.com, i can only connect to sites inside my local network like 192.168.1.254 (my router) and 192.168.1.66:8080/gui (my utorrent server) please help :D ?

---

### Post by walt.smith1960 on 2011-06-20
I'm not very helpful with your internet connectivity, I'm afraid.  Perhaps someone more knowledgeable will check in here. I'd guess gateway or DNS problem but that's just a guess.

---

