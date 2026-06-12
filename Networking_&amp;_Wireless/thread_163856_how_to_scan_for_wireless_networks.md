---
title: "how to scan for wireless networks?"
date: 2006-04-21
forum: Networking &amp; Wireless
---

### Post by andyanderso on 2006-04-21
I have a WPC 11 ver. 3 wirless card and whenever I try to iwlist scan i get a message saying that eth1 (my wireless card) does not support scanning.  I have looked through the forums and only found one possible fix so far and that is here: [http://ubuntuforums.org/showthread.php?t=12340&highlight=wpc11+scan](http://ubuntuforums.org/showthread.php?t=12340&highlight=wpc11+scan)

However when I go to try it after I type the make command I get this message:
root@hermes:/home/andy/Desktop/orinoco-0.15rc4 # make install Makefile:8: *** Kernel tree not found - please set KERNEL_PATH.  Stop.

There must be another way to get my wireless card to scan or maybe someone can help me with using "makefile."  As I am obviously not very good with it....

Please help!

andy

---

### Post by ivansv on 2006-04-22
if ur device is wlan0, the proper command would be `iwlist wlan0 scan'. the dev name of your card must be there.good luck.

---

### Post by andyanderso on 2006-04-22
[QUOTE=ivansv]if ur device is wlan0, the proper command would be `iwlist wlan0 scan'. the dev name of your card must be there.good luck.[/QUOTE]


I tried that command as well as using eth1 as the name of my wireless card here is what they both return:

andy@hermes:~$ sudo iwlist eth1 scan
eth1      Interface doesn't support scanning : Operation not supported

andy@hermes:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.


Any other ideas????

---

### Post by st0kes on 2006-04-22
Can you post the output of iwconfig on its own?

---

### Post by andyanderso on 2006-04-23
[QUOTE=st0kes]Can you post the output of iwconfig on its own?[/QUOTE]

Sure, this is what I get with iwconfig

root@hermes:/home/andy # iwconfig eth1
eth1      IEEE 802.11-DS  ESSID:"GAPTER"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:78:1B:31
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=30/92  Signal level=-80 dBm  Noise level=-141 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


or if I do it for all my network devices:

root@hermes:/home/andy #
root@hermes:/home/andy # iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"GAPTER"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:78:1B:31
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=30/92  Signal level=-78 dBm  Noise level=-141 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It all looks very kosher to me, but maybe not?

thanks
andy

---

### Post by st0kes on 2006-04-23
That looks cool to me. Have you already got the kernel-tree package installed? You might then be able to use your make command. 

Using synaptic have a look for linux-tree-2.6.12 (presuming you are using a stock 2.6.12 kernel).

---

### Post by andyanderso on 2006-04-23
[QUOTE=st0kes]That looks cool to me. Have you already got the kernel-tree package installed? You might then be able to use your make command. 

Using synaptic have a look for linux-tree-2.6.12 (presuming you are using a stock 2.6.12 kernel).[/QUOTE]

I tried that and I still get the same thing:

root@hermes:/home/andy # cd Desktop/orinoco-0.15rc4
root@hermes:/home/andy/Desktop/orinoco-0.15rc4 # make
Makefile:8: *** Kernel tree not found - please set KERNEL_PATH.  Stop.
root@hermes:/home/andy/Desktop/orinoco-0.15rc4 # make install
Makefile:8: *** Kernel tree not found - please set KERNEL_PATH.  Stop.
root@hermes:/home/andy/Desktop/orinoco-0.15rc4 #


iwconfig still outputs the same thing...doh.

andy

---

