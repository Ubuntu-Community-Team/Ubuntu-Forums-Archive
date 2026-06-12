---
title: "Update/Upgrade killed WPA wireless network (again!)"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by siloko on 2009-02-01
Hi all,

Updated my 8.04 install and it killed my wpa encrypted wireless network - ok connecting to open networks or using a network cable.

Decided to bite the bullet and do a dist upgrade to 8.10 to see if it sorted it out - no luck.

The 8.04 update has caused problems with wpa before. I generally use Network Manager to administer my wireless, although to try and debug these problems I dropped down to using wpa_supplicant from the commandline.

If anyone has a clue as to what is going wrong I have all the relevant output here:

[http://mango.homelinux.net/wlan_debug](http://mango.homelinux.net/wlan_debug)

iwconfig output is here: [http://mango.homelinux.net/wlan_debug/iwconfig.txt](http://mango.homelinux.net/wlan_debug/iwconfig.txt)
ifconfig output is here: [http://mango.homelinux.net/wlan_debug/ifconfig.txt](http://mango.homelinux.net/wlan_debug/ifconfig.txt)
wpa_supplicant output is here: [http://mango.homelinux.net/wlan_debug/wpa_supplicant_output.txt](http://mango.homelinux.net/wlan_debug/wpa_supplicant_output.txt)
and my wpa_supplicant.conf is here: [http://mango.homelinux.net/wlan_debug/wpa_supplicant.conf.txt](http://mango.homelinux.net/wlan_debug/wpa_supplicant.conf.txt)

My call to wpa_supplicant is:

sudo wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant.conf -dd


Any help much appreciated

S

---

### Post by kevdog on 2009-02-01
What wireless chipset are you using?

Can you post
lshw -C network
iwlist scan
lspci -nnm

Thanks

---

### Post by siloko on 2009-02-01
Hi,

Thanks for the reply. I have posted the output of all commands you asked to the same place:

[http://mango.homelinux.net/wlan_debug](http://mango.homelinux.net/wlan_debug)

The device is a standard built in intel wireless card, using the ipw2200. Incidentally I have tried wpa_supplicant passing the proper driver but it uses -Dwext anyway, as I think it has support for more recent functionality/attributes.

Interested if this shows up anything weird because my setup is pretty standard and must be used by thousands of others!

Cheers

S

---

### Post by siloko on 2009-02-02
Ok so this is a bit embarrassing but . . . well firstly I am sure the update to my Hardy install killed my wireless but it's possible the upgrade to Ibex sorted it out . . . however in the meantime I had changed the wireless broadcast channel to 13 (as I am in Europe) and just found out:

dmesg | grep 2200 

returns

ipw2200: Detected geography ZZM (**11** 802.11bg channels, 0 802.11a channels)

giving me only 11 supported channels - so no matter what I did I was never connecting to my network on channel 13. So I dropped down to Channel 1 and all was well!

Thanks to whoever looked at this, apologies for wasting your time

S

---

