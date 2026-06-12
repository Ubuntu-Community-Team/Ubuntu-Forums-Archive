---
title: "OpenVPN setup, unable to write random state"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by wplate on 2009-04-07
I am following [these directions]("https://help.ubuntu.com/community/OpenVPN") for installing and setting up an OpenVPN server under Ubuntu 8.10 and starting at the ./build-dh command I get the message **unable to write 'random state'**

So far I can't find anything that says if this is a problem and if so how to correct it.

Any advice on this issue?  Thank you.

---

### Post by coutts99 on 2009-04-07
> **wplate said:**
> I am following [these directions]("https://help.ubuntu.com/community/OpenVPN") for installing and setting up an OpenVPN server under Ubuntu 8.10 and starting at the ./build-dh command I get the message **unable to write 'random state'**

So far I can't find anything that says if this is a problem and if so how to correct it.

Any advice on this issue?  Thank you.


Does it do the same if you use sudo?

---

### Post by wplate on 2009-04-07
No, the behavior is different with sudo.  While CDed to **/etc/openvpn** if I enter **sudo ./build-dh** I get

sudo: ./build-dh: command not found

I'm a relative newbie in Linux, why is a command not found in sudo where it works normally?

---

### Post by thunrida on 2009-05-11
check ownership and permissions of .rnd in your home folder.

---

### Post by VTStevenVT on 2010-12-03
YUP! this fixed the error for me. For some reason ~/.rnd was owned by root:root.

---

