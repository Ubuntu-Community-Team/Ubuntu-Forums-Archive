---
title: "Problems with wireless (alternate CD) - rtl8187se"
date: 2010-10-02
forum: Networking &amp; Wireless
---

### Post by edsmaffs on 2010-10-02
Hi.

I'm attempting to install a command-line version of Maverick, from the alternate CD. I'm using the 64-bit version.

The installation has gone fine - however, I'm having troubles getting the wireless to work. I've installed wireless-tools by carting the *.deb archive over from another computer - this seemed to go fine, and iwconfig shows my wireless card as "wlan0".

However, even after setting the essid and the WEP key I can't connect to the internet (tested this using apt-get). I know that this wireless card requires the "rtl8187se" module, which automatically loads with the desktop version of Maverick - however, it isn't working on the command-line. 
Running "sudo modprobe rtl8187se" pings back an error message saying that the module can't be found. Is there a way for me to manually install it or "find" it? Thank you.

---

### Post by edsmaffs on 2010-10-03
Sorry, realise it would probably help if I supplied more information. I'm not used to working *only* with the command line... good learning experience trying to cart the information over! :)

Here is the line from lspci finding the wireless card:
```
04:00.0 Network Controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)

```
It's under iwconfig as "wlan0". It seems to have changed driver - I found that it's using the "r8187se" module instead of the "rtl8187se" module (that I knew it had used before).

The commands I tried to get it working were
```
sudo iwconfig wlan0 essid <hidden>
sudo iwconfig wlan0 key <hidden>
```
I knew these commands were sufficient to get it working before (from the command line), but it isn't working now.

"ping 192.16.0.1" complains that the network isn't working (or something similar - I will aim to find out the exact error message). I've run "sudo lshw -C network" and it's told me that networking on wlan0 is "DISABLED", so this appears to be where the problem lies. How do I fix this?

Thanks again.

---

