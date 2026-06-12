---
title: "Problems with new wicd install"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by DiscoStu570 on 2009-09-10
My desktop has been using a Dell 1450 Wireless USB card, and with the Network Manager that comes along with 9.04 Jaunty, it connected no problems.  However, signal strength was always lower than it should be, so I decided to install WICD.

Big mistake.  Now, Wicd consistently says 'No Wireless Networks Found'.  In the terminal, typing in lsusb does display the card as attached (Bus 001 Device 005:ID 413c:8104 Dell Computer Corp. Wireless 1450 Dual-band (802.11a/b/g) USB2.0 Adapter).  However when I type -iwconfig, I get:
lo          no wireless extensions

eth0      no wireless extensions

pan0     no wireless extensions


I didn't have to use ndiswrapper and a windows driver before, but that seemed like a good thing to try after wicd initially failed.  In the Wireless Network Drivers window, after downloading the driver on this computer (my laptop, which thank god i have) and installing it there, says:
bcmwl5   (the driver as provided by teh dell website)
Hardware present: No

So, anybody have any ideas?  I'm hoping to be able to get wicd working, as the alternative at this point is to carry the machine somewhere I can plug into a wired connection and reinstalling network manager.

---

### Post by kerry_s on 2009-09-10
> However, signal strength was always lower than it should be

that display lies, i bet it was just fine. :lolflag:

---

### Post by DiscoStu570 on 2009-09-10
Not really, it had very noticeable issues in gaming situations.

Not that I don't regret my decision, spikey internet with Network Manager is better than non-functional internet with wicd, but the problem was real; whether or not it was a problem with Network Manager I have no idea, but it seemed like it was worth a shot.

---

### Post by kerry_s on 2009-09-10
have you rebooted so wicd can get loaded in the kernel properly?

---

### Post by DiscoStu570 on 2009-09-11
> **kerry_s said:**
> have you rebooted so wicd can get loaded in the kernel properly?

Yea, a couple times, ive tried rebooting both with the wireless card attached, and rebooting with it unplugged then plugging it in, no difference.

---

### Post by speedwell68 on 2009-09-11
If you open the Wicd window and click on preferences, what WPA Supplicant are you using?

---

### Post by DiscoStu570 on 2009-09-11
At the moment ndiswrapper.  Ive also tried madwifi and a few others.  

I don't know if drivers are an issue or not, at present the little green lights on the wifi card itself, which were lit up when the thing was working, aren't lit up, and as i said, when i type iwconfig, it doesn't seem to know the card is present.

---

### Post by DiscoStu570 on 2009-10-14
Bump

---

### Post by mharrison on 2009-10-14
Try opening up Synaptic and installing Network-Manager again (it will remove Wicd for you, and see if that brings your wireless card back to life.

---

### Post by DiscoStu570 on 2009-10-14
> **mharrison said:**
> Try opening up Synaptic and installing Network-Manager again (it will remove Wicd for you, and see if that brings your wireless card back to life.

Would if I could, but I can't reinstall network manager without Internet access which I can't get until I fix wicd.

---

### Post by mharrison on 2009-10-14
> **DiscoStu570 said:**
> Would if I could, but I can't reinstall network manager without Internet access which I can't get until I fix wicd.

Actually, you can...or at least should.....the installer package should be already on your system, or in the worst case scenario, you could activate your installer CD as a source and install it from there.

---

### Post by DiscoStu570 on 2009-10-22
OK, so I wasn't able to reinstall Network-Manager from the CD and packages weren't already on the system, but I was able to reinstall it by bringing the necessary packages over from another system.

The bad news is that this didn't fix the problem, I'm now having the same issues under Network-Manager I had with wicd.  

To reiterate, iwconfig shows lo, eth0, and pan0, all of which say no wireless extensions.  It does not show wlan0.

sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0
sudo ifdown wlan0
ifdown: interface wlan0 not configured

Any ideas?

---

### Post by DiscoStu570 on 2009-11-05
Bump.
 
Been a bit lazy about this, but I need to get this machine working, which means either I fix this wireless problem or else I have a frighteningly long ethernet cable run in my future.
 
Any ideas would be appreciated, and I can provide any information anybody needs.  Network Manager is installed and functioning, lsusb command lists the usb wireless card as present, but the card is not lit up, and iwconfig does not show wlan0 at all.

---

