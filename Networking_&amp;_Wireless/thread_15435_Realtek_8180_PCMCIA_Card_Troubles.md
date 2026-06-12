---
title: "Realtek 8180 PCMCIA Card Troubles"
date: 2005-02-14
forum: Networking &amp; Wireless
---

### Post by dirtbiker on 2005-02-14
Hi there,

I'm new to linux, and i've managed to install Ubuntu Warty on an old Gericom T3 laptop. I've got everything working and am on the net through my wired LAN. The laptop is a 900mhz Celeron, with 120mb ram and a 10gb HDD.

Basically i've got a Twinmos B-Series WIFI PCMCIA card that i want to use with this laptop to set up an ad-hoc network with my other laptop (running XP)

Ive used the wifi card with the gericom laptop before, under windows 98, so i know it works.

I've installed drivers using ndiswrapper and on typing "ndiswrapper -l" i am presented with:"Installed ndis drivers: net8180 hardware NOT present"

The strange thing is that the card is listed in the hardware manager as being connected.

Any help/input appreciated!  :wink:

---

### Post by az on 2005-02-14
I think linux is picky about the cardus settings.  Try playing around with your bios.

---

### Post by dirtbiker on 2005-02-15
Thanks for that, ive looked into the bios, but i can't find any Cardbus settings...

I've got AMIBios version 1.30 if thats any help?

Thanks again  :wink:

---

### Post by slow'puter on 2005-02-21
Try this:

this is the method that worked for me.
 
Using the Synaptic Package Manager, download from the Universe the following packages: (you can download on another computer and fit these files in a USB memory stick)
 
 1. fakeroot, build-essentials, linux-headers-2.6
 2. Download ndiswrapper from ndiswrapper.sf.net (file name ndiswrapper-1.0.tar.gz)
 3. As ROOT (sudo -s, or open a ROOT terminal window and copy ndiswrapper-1.0.tar.gz to the  **/usr/src** folder
 4. On the command line of the terminal window type **tar zxvf ndiswrapper-1.0.tar.gz**
 5. Change to the new ndiswrapper directory by typing [b]cd /ndiswrapper-1.0
 [/b]6. Type **make deb **and the installation of ndiswrapper is automatic
 7. Type **dpkg -i ndiswrapper*** to set ndiswrapper
 
 Now that ndiswrapper is all set, proceed to install the driver.
 
At ndiswrapper.nf.net you can find the drivers for your specific wireless card, but for the purpose of this guide, we will use the Realtek rtl8180l driver. The driver is a standard Windows XP .inf file.
 
 8. Once the driver is copied to a convenient location, type [b]ndiswrapper -i [i]filename.inf
 [/i][/b]9. Type** ndiswrapper -l** to verify the status of the installed driver. You should see something like:
 
 Installed ndis drivers
 *drivername* driver present, hardware present
 
 10. To load the module type **modprobe ndiswrapper**
 11. If no errors were generated, you should see the transmit light on your card flash. 
 12. If you dmesg, near the end you should see something like:
 wlan0: ndiswrapper ethernet device xx : xx : xx : xx :xx : xx
 
Now all you need to do is establish connection with your AP. Use the networking app and you are all done!

---

### Post by jayson23 on 2005-03-22
I'm having a similar problem with this. I've got a Netgear ma521, so it should use the  net8180.inf in order to work. I got that from Realtek, and used ndiswrapper to install it. 
When I type "ndiswrapper -i net8180.inf" it seems to work, but when I use "ndiswrapper -l", I get a message "net8180 invalid driver!"

this should be the correct driver. any ideas?

---

### Post by slow'puter on 2005-03-22
Is your card realtek 8180 based? If not, that might be the problem. MAke sure you are using the inf file, not the sys.

Keep us posted so we can help you.

---

### Post by jayson23 on 2005-03-22
Thanks for the fast reply. The Netgear MA521 uses a Realtek 8180 chipset. I'm using the .inf file.

---

### Post by xy77 on 2005-04-14
Same problem here:

```

net8180 invalid driver!

```

I used to get this pcmcia card to work on Gentoo with exactly the same inf file.

Any hints or solutions so far?

- David (xy77)

---

### Post by bsammon on 2005-04-22
For the benefit of google:
[http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)

---

### Post by xy77 on 2005-04-26
Thank you for the hint. This is quite nice, if it works.

I made it until (after installing some kernel-header stuff, gcc and libncurses-dev):
```

# sudo ./modules_load
insmod: error inserting 'ieee80211_crypt-r8180.ko': -1 Invalid module format
insmod: error inserting 'ieee80211_crypt_wep-r8180.ko': -1 Invalid module formatinsmod: error inserting 'ieee80211-r8180.ko': -1 Invalid module format
insmod: error inserting 'r8180.ko': -1 Invalid module format

```

Any ideas or knowledge how to solve this would be appreciated. TIA.

- David (xy77)

EDIT:
note to self: always check dmesg!

I got ```
ieee80211_crypt_r8180: version magic '2.6.10-5-686 preempt PENTIUMIII gcc-3.3' should be '2.6.10-5-686 preempt 686 gcc-3.3'
ieee80211_crypt_wep_r8180: version magic '2.6.10-5-686 preempt PENTIUMIII gcc-3.3' should be '2.6.10-5-686 preempt 686 gcc-3.3'
ieee80211_r8180: version magic '2.6.10-5-686 preempt PENTIUMIII gcc-3.3' should be '2.6.10-5-686 preempt 686 gcc-3.3'
r8180: version magic '2.6.10-5-686 preempt PENTIUMIII gcc-3.3' should be '2.6.10-5-686 preempt 686 gcc-3.3'

```

because I thought to improve the kernel configuration to fit my processor. Stupid me, all modules and the current kernel are 686 Pentium Pro.

---

