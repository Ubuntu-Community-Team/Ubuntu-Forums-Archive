---
title: "Problems with being able to connect to a Linksys wireless network."
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by James652 on 2011-09-04
Hi,Today I dualbooted Windows 7 and Ubuntu 11.04 together. Everything is fine, apart from it won't allow me to connect.
Here is what I did, I clicked the WiFi signal bar thing, Clicked on my Wireless Router's SSID ( Linksys ) And it comes up with " Authentication required by wireless network

In the wireless security dropdown, I'm pretty sure it doesnt say the security I have, since I have WEP with 64Bit encryption.
My router password is A182B23F11
Heres what the dropdown has:
WEP40/128-bit Key ( Hex or ASCII)
WEP 128-bit Passphrase
LEAP
Dynamic WEP ( 802.1x)

So I'm pretty sure none of those are my security, Nether the less, I just try clicking on one at a time.
The only ones that I think I had the details for was WEP 40 / 128-Bit Key ( Hex or ASCII )and WEP 128-bit passphrase.

I know it has the ability to connect, since it could connect to a tempory one set up by my phone.


Please remember that I'm just starting with ubuntu, I've only ever ran it on VirtualBox before.

The OS is Ubuntu 11.04 x64

Btw, I can do anything you want me to try, since ubuntu machine is next to me.

---

### Post by wildmanne39 on 2011-09-04
Hi, welcome to the forum! please run these commands in a terminal you can open it by hitting ctrl+alt+t:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
lsusb
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

