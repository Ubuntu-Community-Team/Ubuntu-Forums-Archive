---
title: "roll back to broadcom B43 from broadcom STA"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by Heide264 on 2009-01-15
I was having issues with my broadcom B43 driver as expected (it worked off an on, but wouldn't pick up random networks and such mainly WPA), so I decided to try the broadcom STA driver that I heard was an update. I updated and apparently it wasn't compatible with my chip and now my computer thinks I have two eth connections it seems and no wireless. Is there any way to roll back to the old driver? In hardware drivers where it used to be it has disappeared and only the STA driver is there (and now disabled).

If anybody can give me a pointer to how to go back before following the big ndiswrapper/b43 fwcutter operation (which apparently I didn't have to do in intrepid, i just had to install the firmware simply) it'd really help me out.

If any outputs of anything would help let me know... as of now everything is just outputting it as an unused eth connection.

Thanks

---

### Post by Heide264 on 2009-01-17
Just a follow up to close the topic...

I deactivated the STA driver through the hardware drivers menu option and restarted, and it showed no wlan cards as it normally does. I connected up to the internet hardwired and just ran the b43cutter again and it installed but still not effect. For some reason after two restarts - not one - it picked up and was working as normal. *shrug*

...Just thought I'd put it out there incase somebody has a similar issue

---

### Post by Ayuthia on 2009-01-17
There is a chance that the Broadcom STA module might work for you.  If you want to try it out:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo /etc/init.d/networking restart
```Should allow you to test it.  I think that hte problem with it not working might be because the b43 module was still loaded.

However, if you don't want the wl module to load, you can always add it to the blacklist file:
```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist
```and that should prevent it from loading.

However, deactivating the wl module from Hardware Drivers should produce the same result.

---

### Post by Heide264 on 2009-01-17
Thanks, I just actually ran the first snippet to try out the STA... it renamed my wlan to eth, but it still allows me to scan... otherwise I really see no difference so far. I think I am going to generate a new post about my issue about it actually. I am having a lot of trouble connecting to WPA networks. When scanning threw konsole I find the networks, but the GUI does not see 1/3 of them (normally the one I want to connect to). Sometimes it works, sometimes not.

When I ran a recent version of openSUSE, they had an issue with bluetooh interfering with wlan card scanning and I had to change a couple small numbers... it seems awfully similar but it is beyond my head to tell.

Going to play with it for a bit and keep my ethernet cord handy, thanks for the help, will keep the thread updated.

---

