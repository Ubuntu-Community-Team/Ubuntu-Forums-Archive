---
title: "High voice in Hangouts"
date: 2017-10-08
forum: Multimedia Software
---

### Post by Andreyshel on 2017-10-08
Hello.
My grandma has a problem with sound during Hangouts calls.
Her voice sounds like, she breathed in some helium and nobody is able to understand what she is saying.
I collected some useful information about her desktop computer.

Ubuntu release(lsb_release -a)
 ```
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

```

lsusb

```
**Bus 001 Device 004: ID 046d:0825 Logitech, Inc. Webcam C270**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 1a2c:2d23 China Resource Semico Co., Ltd 
Bus 004 Device 021: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Kernel revision(uname -a)
```
Linux Lusy-PC 4.4.0-96-generic #119-Ubuntu SMP Tue Sep 12 14:59:54 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

Google Chrome 56.0.2924.87 and Pulseaudio 8.0 is in use

Problem seems to be present only in Hangouts. Soundcheck using arecord passed successfully. 
Does anybody have ideas?
Thank you in advance

---

### Post by Kirboosy on 2017-10-10
This sounds like an issue within google-chrome. I would suggest the following plan of action.

1. Update the system completely. (Google Chrome is in the 61.* as of this post)
2. Reboot computer just for good measure
3. Test to see if issue is resolved

If that doesn't work I would suggest downloading the [Google Hangouts Plugin]("https://tools.google.com/dlpage/hangoutplugin") and testing a call in Firefox.

Hope that helps!
~Caboose

---

### Post by denismc on 2017-10-12
I remember this being a common problem with hangouts due to a conflict with Google Now but this is the first time hearing this problem on a desktop.  But good to hear it was solved via some form of upgrade.  Was it due to an upgrade to the desktiop or to Hangouts or Ubuntu?

---

### Post by Kirboosy on 2017-10-13
> **denismc said:**
> Was it due to an upgrade to the desktop or to Hangouts or Ubuntu?

I'm guessing it was the update to Chrome that fixed it. After initial install of Chrome it updates through the Ubuntu system updates via PPA. Keeping the system up to date is always a good idea anyway.

---

### Post by Andreyshel on 2017-10-14
Did dist-upgrade(Chrome was  included in it via official repo)
Also think that Chrome was the key part.

---

