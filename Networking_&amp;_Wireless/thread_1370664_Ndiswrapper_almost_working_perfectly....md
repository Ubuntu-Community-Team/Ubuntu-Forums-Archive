---
title: "Ndiswrapper almost working perfectly..."
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by Wouter N on 2010-01-02
Hi,

I recently switch from the b43legacy drivers to ndiswrapper on a bcm4306 chipset based wireless interface. The reason for this change is that I found the b43legacy driver to unstable(especially in case of constant speed...)

So I used this guide to install Windows drivers through ndiswrapper.
This worked perfectly, untill I rebooted...
The ndiswrapper modules gets loaded, but the network manager does not indicate active networks(i.e, the devices is not ready), and iwconfig doesn't return wlan0...
I found a 'trick' to make it work anyways:

```

sudo modprobe b43legacy
# now I wait a while, until my network interface connects to my AP with the b43legacy drivers.
# After I'm connect to my AP:
sudo modprobe -r b43legacy
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

```
And then it works too, with the windows drivers through ndiswrapper.
I'm kinda new to linux, and I already learned some interesting things while trying to make my interface work with ndiswrapper.
Now is there something to solve this issue? Does the use of my interface first with b43legacy drivers wake something up, that ndiswrapper needs too?

I'd like to hear...

Thanks in advance,

Wouter

P.S.: I use ubuntu 9.04, freshly installed from the CD

---

### Post by mocoloco on 2010-01-02
You just need to blacklist the b43legacy module.
```
gksu gedit /etc/modprobe.d/blacklist
```

I'm pretty sure that's the file, I know it's now called blacklist.conf but I think that change was since 9.10, if I'm wrong you'll find it.  Just add a line in there and comment if you want it:
```
# Going to use ndiswrapper instead of this
blacklist b43legacy
```

That should do it.

---

### Post by Wouter N on 2010-01-02
Thanks for your reply, but I already blacklisted the b43legacy module, as indicated in the guide I used. When i boot Ubuntu, ndiswrapper is being loaded(I added it to /etc/modules), but does not work. So I load b43legacy again, let my interface connect to my AP, then remove b43legacy again. After this, I remove the ndis
wrapper module with *modprobe -r ndiswrapper*, and then I load it again, resulting in my interface to work...

**Edit:** It seems I do not explicitly let the interface connect to my AP first using the b43legacy drivers, just loading that module for a sec is enough(to afterwards continue with the above mentioned steps)...

**04/01 BUMP**

---

