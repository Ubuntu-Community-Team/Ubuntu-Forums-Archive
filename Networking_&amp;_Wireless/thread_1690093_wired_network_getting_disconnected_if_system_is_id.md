---
title: "wired network getting disconnected if system is idle"
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by Ethan hunt on 2011-02-17
i used to download files using transmission bit torrent client. I download the torrent and once the download starts i will leave the system and check only after 4 or 5 hours later.But when i check the system again, the network connections were automatically disconnected.The download is getting stopped naturally.

why my wired network connection is getting disconnected automatically if the system is idle?(ubuntu 10.10)

please suggest a solution to this problem

---

### Post by grahammechanical on 2011-02-17
What power management settings have you set up? Do not forget the settings in the BIOS. When power management activates things get switched off including network cards. 

Regards.

---

### Post by chargrims on 2011-11-27
I'm having this same problem after upgrading to 11.10. The internet disconnects and asks for my password over and over. When I return to the computer there are multiple password request boxes for the network (with the saved password filled in just awaiting a hit of 'enter'). This is with a wireless network.

---

### Post by CompsGeek on 2011-12-23
> **chargrims said:**
> I'm having this same problem after upgrading to 11.10. The internet disconnects and asks for my password over and over. When I return to the computer there are multiple password request boxes for the network (with the saved password filled in just awaiting a hit of 'enter'). This is with a wireless network.

Exact same thing happens with me i have to restart the computer to get it reset and this happens with my WIRED network..:confused:

---

### Post by praseodym on 2011-12-23
Do you folks have an NVIDIA card with "forcedeth" driver?

Check it with:

```
lspci -nnk | grep -iA2 net
```

This driver needs two things:

1) additional module parameters:

```
echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
```

2) As far as the PM is concerned, this driver and other modules should be unloaded and reloaded using SUSPEND/HIBERNATE. Check, which drivers are affected:

```
lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv' 
```

---

### Post by sailor2001 on 2011-12-24
check this: system/preference/screensaver and uncheck wallpaper

---

