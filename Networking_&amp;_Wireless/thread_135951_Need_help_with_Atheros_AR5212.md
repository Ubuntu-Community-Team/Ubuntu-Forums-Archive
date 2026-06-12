---
title: "Need help with Atheros AR5212"
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by mazlusus on 2006-02-24
I have an Atheros AR5212 here is the lspci detail on it:

0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
     Subsystem: Askey Computer Corp.: Unknown device 7058
     Flags: bus master, medium devsel, latency 80, IRQ 9
     Memory at c2000000 (32-bit, non-prefetchable) [size=64k]
     Capabilities: <available only to root>

When I run the live cd Ubuntu 5.10 recognizes that I have a wireless card, and allows me to connect but when I run Ubuntu normally it doesn't acknowledge the card...any ideas? Thanks.

---

### Post by Lambert on 2006-02-24
When you say it's not recognized, do you see the card when you run lspci -v on ubuntu install?

You may just need the linux-restricted modules which is where the madwifi driver is.

check if it's installed with this command

dpkg -s linux-restricted-modules-`uname -r`

If it says not installed then you need to install that package to get the driver.

---

### Post by mazlusus on 2006-02-25
Thanks for the advice, it's recognizing the card now and connects, there are still some issues but I see some light in the tunnel now!

---

### Post by Angry penguin on 2006-03-01
I am having the same problem, I have the same chipset, I have the madwifi restricted modules installed, but i cant get the wlan0 to even come up when it is inserted. The card doesn't get any power and the wlan0 doesn't show up in networking.

any ideas?

---

### Post by Lambert on 2006-03-01
Look in your dmesg output for this error.

"unable to attach hardware: Hardware didn&#8217;t respond as expected, (HAL status 3)"

If you see this go here.

[http://madwifi.org/wiki/UserDocs/Troubleshooting#WhenIloadtheath_pcimoduleIgetunabletoattachhardware:HardwaredidntrespondasexpectedHALstatus3](http://madwifi.org/wiki/UserDocs/Troubleshooting#WhenIloadtheath_pcimoduleIgetunabletoattachhardware:HardwaredidntrespondasexpectedHALstatus3)

If not, do you see any other error related to your device?

---

### Post by Angry penguin on 2006-03-01
Im sooo confused i have been looking at every driver howto on these forums, all the while switching back and forth between my working network card and my non-working network card trying to get it to work and browse the forums.

i tried the -ng version of madwifi. isn't this for pci cards?
that might be why this isnt working. 

I am going to reinstall ubuntu and start over because this is a complete mess, i have tried so many of these damn howto's, none have worked and now i will never figure this out.

It would help if someone could point me to ONE howto that WORKS, for the AR5212 chipset in a d-link dwl-g650
thank you.:cry:

---

### Post by Lambert on 2006-03-01
To get this to work, you simply need to install the linux-restricted-modules-XXX package. The XXX=the kernel you're running which breezy by default installs 2.6.12.9 386.

Your first upgrade will upgrade the kernel to 2.6.12.10 386

If the card is inserted during install, the linux-restricted-packages-XXX should install by default.


If your card doesn't work after re-installing run and post the output of these terminal commands here.

sudo lshw -C network
and
cardctl ident

---

### Post by Angry penguin on 2006-03-01
lambert, that seems to have worked. thank you.

although my stage 2 of the installation kinda froze so i might run into problems down the road because of that.

---

