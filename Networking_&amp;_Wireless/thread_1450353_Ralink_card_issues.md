---
title: "Ralink card issues"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by mreyes000 on 2010-04-08
I'm running v10.04 and I just installed a new Intellinet wireless pci card model 524810.  I tried downloading and installing the ralink drivers but I can't seem to get the card going.  Any help is greatly appreciated.

I've attached the lspci and iwconfig outputs, I'm currently online using a usb wireless adapter and the intellinet card is installed but not even the lights are on it. it works in my windows boot.

---

### Post by chili555 on 2010-04-09
Did you accidentally mark this as [SOLVED]? Is it solved?

Your lspci looks like a module rt3562sta is associated with your device. Let's take a look at:```
dmesg | grep rt3
```Thanks.

---

### Post by mreyes000 on 2010-04-18
Thanks for the response. Originally I marked it solved because somehow the card just started working. Out of nowhere and I couldn't figure out how to remove the original thread. However, after updating to the latest kernel, my card stopped working again, and i can't use the wireless usb adapter I was using before either. It's the same card, same issue. the dmesg | grep rt3 does nothing.

I had to connect to the internet by tethering my android phone.  Here's the outputs I have now:

---

