---
title: "hp elitebook 8540w wireless issue"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by elitebooker on 2011-05-21
I just bought a hp elitebook 8540w and installed ubuntu 11, everything works but only wireless is not working.  It is always disabled.  I tried this command and it say blocked.

sudo rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Anyone can kindly help? thx

---

### Post by prshah on 2011-05-21
> **elitebooker said:**
> 
    Hard blocked: yes

This means your wireless "switch" is off. If you don't have a physical "slide" or "toggle" switch, in most HP notebooks, the wireless light is also a touch sensitive switch. Just swipe your finger over the wireless indicator and it should be enabled again.

---

### Post by elitebooker on 2011-05-21
I have wireless switch off from win7 side (dual boot), once switch back on and boot again in ubuntu.  Wireless finally working.  thanks

---

### Post by kommisar on 2011-06-27
I have the exact same problem using Puppy Lucid 5.2 which is based on Ubuntu repositories.  The problem is that my install CD did not have the necessary microcode driver iwlwifi-6000-4.ucode or something like that.  I found version of this microcode that matched my kernel version, 2.6.33.2, and copied the microcode to the file system using  the puppy package manager.  Upon reboot my wireless was enabled and I was able to connect to my router.

---

