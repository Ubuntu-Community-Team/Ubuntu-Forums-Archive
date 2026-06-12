---
title: "Wireless problem with Asus eee pc1005HAB - Ubuntu 11.04"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by ana.evelia10 on 2011-07-28
Hi! I have recently installed ubuntu 11.04 on my asus eeepc1005hab. And I've had problems with the wifi. I can connect via ethernet, but the wireless won't connect. I can see the connection, but my wifi never connects. I've tried many things but it still won't work. Can any one help? Thanks!

---

### Post by fi2 on 2011-07-28
Did you check if WLAN is enabled in the Bios menu?
(Reboot > F2 > Advanced > Onboard Devices Configuration)

---

### Post by chili555 on 2011-07-28
First, let's see what kind of wireless card you have; then we'll troubleshoot it. Please open a terminal and run and post:```
rfkill list all
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by ana.evelia10 on 2011-07-28
I checked and it is enabled.

_________________

rfkill list all
0: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
lspci -nn | grep 0280
02:00.0 Network controller [[COLOR=Red]0280[/COLOR]]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

(the 0280 is red)
Thanks!

---

### Post by chili555 on 2011-07-28
Your card uses the driver module *ath9k* which is usually pretty reliable. Is your network set to WPA and WPA2 mixed mode? That is often troublesome. If you can, try WPA2 only. You might also try:```
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
```Any improvement?

---

### Post by ana.evelia10 on 2011-07-28
I'm a noob, so how would I change the wpa and wpa2 mixed mode? and I"ve tried the code but this happens:

```
ana@aphrodite:~$ sudo rmmod -f ath9k
[sudo] password for ana: 
ERROR: Removing 'ath9k': No such file or directory
ana@aphrodite:~$ sudo modprobe ath9k nohwcrpt=1
FATAL: Error inserting ath9k (/lib/modules/2.6.38-11-generic-pae/updates/cw-2.6.39/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

---

### Post by chili555 on 2011-07-28
> /lib/modules/2.6.38-11-generic-pae/[COLOR="Red"]updates/cw-2.6.39[/COLOR]/ath9k.koDid you fail to tell old Chili about installing the compat-wireless package?? Which version of the package did you install? It's in the name of the folder that was created when you extracted the tar.bz2. For example, compat-wireless-2011-07-15.

---

### Post by ana.evelia10 on 2011-07-28
Oh! It seems I did...sorry.

I installed compat-wireless-3.0-2.tar.bz2 (that's the title of the .tar.bz2. file)

---

### Post by chili555 on 2011-07-28
I suggest you uninstall it and then see if it connects. If not, try this: [http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball](http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball)

I think the version you installed is for kernel version 3.0 and you have 2.6.38.

---

### Post by ana.evelia10 on 2011-07-28
THANK YOU!!! It worked! I reinstalled ubuntu and did the ```
 
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
```
and it worked! 
Thanks!

---

### Post by chili555 on 2011-07-28
Well, a reinstall is drastic but certainly effective. To make the driver parameter persistent, let's do:```
sudo gedit /etc/modprobe.d/ath9k.conf
```Add one line:```
options ath9k nohwcrypt=1
```Proofread, save and close gedit and you should be all set.

Please use thread tools at the top and Mark Solved. Have fun!

---

### Post by ana.evelia10 on 2011-07-28
I'm wondering if it is normal that I can't connect to the Internet via wireless if I have 2~3 bars? The signal fluctuates but it's not connecting unless it is in the same room as the router.

AND when I tried doing the code you told me, I got this:

```

(gedit:2551): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.FS3CZV': No such file or directory

(gedit:2551): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2551): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.AXESZV': No such file or directory

(gedit:2551): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

** (gedit:2551): CRITICAL **: _gedit_tab_save_as: assertion `(tab->priv->state == GEDIT_TAB_STATE_NORMAL) || (tab->priv->state == GEDIT_TAB_STATE_EXTERNALLY_MODIFIED_NOTIFICATION) || (tab->priv->state == GEDIT_TAB_STATE_SHOWING_PRINT_PREVIEW)' failed

** (gedit:2551): CRITICAL **: _gedit_tab_save_as: assertion `(tab->priv->state == GEDIT_TAB_STATE_NORMAL) || (tab->priv->state == GEDIT_TAB_STATE_EXTERNALLY_MODIFIED_NOTIFICATION) || (tab->priv->state == GEDIT_TAB_STATE_SHOWING_PRINT_PREVIEW)' failed

(gedit:2551): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.QRIJZV': No such file or directory

(gedit:2551): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```

---

### Post by chili555 on 2011-07-28
When I ...ahem... accidentally connect to my neighbor with two bars, it's a bit unstable; three or four are OK. Does your router have a signal strength setting? Is it dialed up to maximum? See attached.> (gedit:2551): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.FS3CZV': No such file or directoryYou might try gksu: [https://bbs.archlinux.org/viewtopic.php?id=118892](https://bbs.archlinux.org/viewtopic.php?id=118892)

---

### Post by ana.evelia10 on 2011-07-28
It worked with gsku - thanks!
As for the connecting from my room instead of the living room (where the router is) I don't get why it won't connect from my room. Like I said, the signal fluctuates from 1-3 bars in my room and it doesn't matter. I have to go to the other room with the laptop to be able to connect. *shrugs* I'll find out soon enough. Thanks though!

---

### Post by Teoclaid on 2013-02-11
> **fi2 said:**
> Did you check if WLAN is enabled in the Bios menu?
(Reboot > F2 > Advanced > Onboard Devices Configuration)

Thank you so much - this solved my eee wifi problem straightaway. Phew! :D

---

