---
title: "No wireless internet on HP 2230s with intel 5100 AGN"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by Sportingfan on 2009-01-20
Hey there,

a couple of days ago, i bought my first laptop, a hp 2230s. I downloaded Intrepid and installed it. Everything worked fine except the speakers. But this was easily solved.

The next day after the installation, I copied my home folder from my desktop machine to my new laptop. I logged out and back in, in order to load all settings, and suddenly my wireless Internet didn't work anymore.
The reason why it didn't work is because the wpa key got corrupted. So i changed it back, but the system did not save it.

Then i got rid of the network manager applet and installed wicd. This didn't work either. Wicd could not find a wireless network.

So i started googling and found a lot of solutions for similar problems, but non of them seemed to be the same.

After 2 days of googling around, i came here to ask for help.

As said, i have a hp 2230s laptop.
It has a Intel PRO/Wireless 5100 AGN network card.

iwconfig produces:

```
wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

```

iwlist wlan0 scan gives:

```
wlan0     No scan results
```

Any solution?

For some reason i don't like the solution called ndiswrapper. Some time ago i was messing around with ndiswrapper without success.

Thx

---

### Post by Sportingfan on 2009-01-20
I forgot to tell:

I did a fresh install of intrepid after i found out that my wireless didn't work. But the problem remained.
I tried the hardy live cd, but no wireless Internet either.

---

### Post by Sportingfan on 2009-01-20
I tried to use seahorse to set the wpa key correctly. I also changed the permissions of network-manager-applet to read and write for this keyring.

The key also changed in the network-manager-applet but it was unable to connect. Network-manager-applet keeps  asking for the password. The password which it shows is correct, so i click connect, after which it asks permission to enter the default key.

---

### Post by Sportingfan on 2009-01-21
I solved it!:p

I downloaded the firmware from the intel/linux site: [http://intellinuxwireless.org/?n=Info](http://intellinuxwireless.org/?n=Info)

downloaded the iwlwifi-5000-ucode-5.4.A.11.tar.gz file and extracted it to /usr/lib/firmware/

I had to create the folder first. Also, make sure you extract all files to this main firmware folder (not to /usr/lib/firmware/iwlwifi-5000-ucode-5.4.A.11/).

Reboot and it works!

---

