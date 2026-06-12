---
title: "Broadcom BCM4306 wifi in Xubuntu"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by miocene on 2009-01-07
Hi there, I'm having trouble getting my Belkin 54g wifi card (which has BCM4306 chipset) working in Xubuntu.

I have got ndiswrapper and ndisgtk installed and I loaded some drivers but I cant connect to any networks. I did iwconfig and it returned this:

```


harryg@ubuntu:~$ iwconfig

lo        no wireless extensions.


eth0      no wireless extensions.


wmaster0  no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"D-Link ADSL Router"

              Mode:Managed  Channel:0  Access Point: Not-Associated
              Tx-Power=0 dBm
              Retry min limit:7   RTS thr:off   Fragment thr=2346 B 
              Link Quality:0  Signal level:0  Noise level:0
              Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
              Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
I'm thinking the either drivers aren't working or I've done something wrong. Where can I find drivers that have been proven to work with this chipset?



When I do "iwlist scan" I get "No scan results". Which I'm guessing measn it tries to scan but cant pick anything up. There is a wireless network within range because the computer I'm typing this on is using it

---

### Post by Ayuthia on 2009-01-07
You might try this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Does the Windows Wireless Drivers say that the hardware is present?  You might also go into the Terminal and check for error messages:
```
dmesg|grep ndiswrapper
```

---

### Post by miocene on 2009-01-07
Hi thanks for the reply. I'm pretty confident that I have the right drivers now - ndisgtk says hardware present. I got them off the Dell ftp site via the ndiswrapper page that tells you which driver to get.

Error message check:
```

harryg@ubuntu:~$ dmesg|grep ndiswrapper
[   57.327278] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   57.391309] usbcore: registered new interface driver ndiswrapper
[11049.842570] usbcore: deregistering interface driver ndiswrapper
[11050.133437] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[11050.430556] usbcore: registered new interface driver ndiswrapper
[13020.970700] usbcore: deregistering interface driver ndiswrapper
[13021.360892] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[13021.911598] usbcore: registered new interface driver ndiswrapper

```

The leds on the card do not illuminate

---

### Post by miocene on 2009-01-07
OK I'm getting somewhere.
I found that there is some kind of bug that stops ndiswrapper having control of the card. I solved it via the guide and now when I do *iwlist scan* it identifies my wifi network.

BUT: I cannot connect to it - ie it is not listed in the network manager thing at the top right.

---

### Post by miocene on 2009-01-07
Anyone?

---

