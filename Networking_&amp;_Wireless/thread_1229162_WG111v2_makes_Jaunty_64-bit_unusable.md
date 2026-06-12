---
title: "WG111v2 makes Jaunty 64-bit unusable"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by WilyWyrm on 2009-08-01
Hi, all.

I hate for my first post about Ubuntu to be one looking to fix it, but here it is.

I got a new desktop computer about a week ago. It's a HP Pavilion p6142 with an AMD Phenom X4 9650 @ 2.3 Ghz and 8GB RAM. Naturally, it's got Vista 64-bit, and Vista dual boots with Jaunty (2.6.28-14-generic).

Rather than have everyone in my house trip over an Ethernet cable like I'm using now, I opted to use wifi with a Netgear WG111v2 USB adapter (RLT8187L chipset, ID 0846:6a00). After reading every ndiswrapper tutorial I could stomach and trying constantly for the past 2 days, I finally got to the point where you would think everything would work, but doesn't. I got Netgear's latest Win XP 64-bit driver's .inf and .sys files (Ndiswrapper still doesn't support Vista's drivers yet, right?) for the model and blacklisted the existing RTL8187 driver. I reloaded Synaptic to check for ndiswrapper updates (Should I try compiling the new 1.55?) and it told me I had the latest in the Ubuntu repositories. I tried Wicd and it didn't help. 

Running

```
ndiswrapper -l
```gives

```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
net111v2 : driver installed
    device (0846:6A00) present (alternate driver: rtl8187)

```so I think ndiswrapper recognizes it.

But when I boot up Ubuntu with the adapter plugged in, it takes longer to get to the login screen. Not very long, but it's noticeable. After logging in is when all heck breaks loose. Or rather, it doesn't because nothing loads! Every icon I usually have in the top right corner disappears and I can't click on anything. Opening up the terminal with a keyboard shortcut works, but when I try to execute any command, it just sits there. Eventually, after 10 or 20 minutes of waiting, I decide to just shut the computer down with the power button. I'd be willing to run all kinds of commands and go through all of this again from scratch if it'll get the adapter working.

If anyone can help this poor newb, it'd be greatly appreciated and the hair that hasn't been pulled out of my scalp will be eternally grateful.

Note: Sorry I didn't give a system log. I don't know which parts to cut out. Also, I had 2 fleeting "Eureka" moments when the adapter started working and crashed the system or stopped working 5 seconds later. Don't know if that helps, but still...

 Oh, and the router is a Netgear WPN824v3 with WEP that I'm planning to change to WPA2.

---

### Post by WilyWyrm on 2009-08-01
Shameless bump.

---

### Post by Crafty Kisses on 2009-08-02
Have you tried blacklisting the conflicting drivers? You need to run as root:
```
gedit /etc/modprobe.d/blacklist
```
Then to my knowledge you need to blacklist the following:
```
blacklist r8187
blacklist islsmusb
blacklist islsm
blacklist islsm_usb
```
Then if you haven't already, load the ndiswrapper module, so as root run:
```
modprobe ndiswrapper
```
Then restart your network by running the following:
```
ifconfig wlan0 down
ifconfig wlan0 up
```
See if you get any different results when you try that.

---

### Post by WilyWyrm on 2009-08-02
Thanks for your reply, but it didn't do anything. Ubuntu still freezes. I even did a reinstall. Whenever I even plug in the adapter, the computer freezes up.

---

### Post by WilyWyrm on 2009-08-02
Bump.

---

### Post by WilyWyrm on 2009-08-03
Anyone? I really need to get this wifi adapter running soon.

---

### Post by WilyWyrm on 2009-08-03
Bump.

---

### Post by WilyWyrm on 2009-08-05
Never mind. I reinstalled Ubuntu again with the adapter plugged in and now the native rtl8187 driver works. Weird.

---

