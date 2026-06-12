---
title: "No ethernet or wireless Dell Inspiron 1764"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by dhill13 on 2011-06-17
Hi everyone,

I'm a new poster and will try to keep this brief. I'm running on 11.04 on my Dell Inspiron 1764, and so far haven't been able to achieve internet access through either a direct wired connection or wireless.

Wireless network controller: Broadcom BCM4312 802.11b/g LP-PHY (rev 01)

Ethernet controller: Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02) 

Fixes I've tried so far:

Wired - Attempted to install the r8168 driver and remove the r8169 driver as is done in this thread:

[http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489)

Wireless - managed a fleeting wired connection yesterday, during which time I installed the Broadcom STA driver through Additional Drivers.

Also attempted to install the firmware-b43-lpphy-installer, following these instructions:

[http://crunchbanglinux.org/forums/topic/13542/getting-crunchbang-to-work-with-my-network-card/](http://crunchbanglinux.org/forums/topic/13542/getting-crunchbang-to-work-with-my-network-card/)

but to no avail (under Synaptic Package Manager, the firmware-b43-lpphy-installer still remains unchecked after I install it through terminal) 

If you need any terminal output just let me know. Thanks in advance for the help! :)

---

### Post by chili555 on 2011-06-17
How about we check:```
lsmod | grep -e dell -e b4 -e wl
rfkill list all
```Thanks.

---

### Post by DirtyPC on 2011-06-17
follow this thread: [http://ubuntuforums.org/showthread.php?t=1784034](http://ubuntuforums.org/showthread.php?t=1784034)

---

### Post by dhill13 on 2011-06-17
Thanks chili555. Here are the outputs:

:~$ lsmod | grep -e dell -e b4 -e wl
dell_wmi               12681  0
sparse_keymap          13898  1 dell_wmi
wl                   2568244  0
dell_laptop            13827  0
dcdbas                 14438  1 dell_laptop
lib80211               14991  2 lib80211_crypt_tkip,wl
:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: brcmwl-0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

---

### Post by chili555 on 2011-06-17
> **harrylucas1 said:**
> follow this thread: [http://ubuntuforums.org/showthread.php?t=1784034](http://ubuntuforums.org/showthread.php?t=1784034)Does dhill13 have the same device? We haven't yet seen lspci -nn.

---

### Post by dhill13 on 2011-06-17
donal@dhill13:~$ lspci -nn
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)


Forgot to mention: I am running a dual boot with Windows 7, but have checked to ensure that wake on lan is enabled.

Also I have removed network manager during my attempts to fix the problem

---

### Post by DirtyPC on 2011-06-17
> **chili555 said:**
> Does dhill13 have the same device? We haven't yet seen lspci -nn.
It does not matter. They are the same variants.

---

### Post by chili555 on 2011-06-17
Please try:```
sudo rmmod -f dell-laptop
```Since you removed NM, are you going to populate /etc/network/interfaces or just try to connect by command line or...what?```
sudo iwconfig eth1 essid <yourrouter>
sudo iwconfig eth1 key 12345
sudo dhclient eth1
```It's hard to do with WPA2, which I hope you are using.

---

### Post by dhill13 on 2011-06-17
I had previously appended /etc/network/interfaces to include:

auto eth1
iface eth1 inet static
address <my address>
netmask 255.255.255.0
gateway <my gateway>

but didn't seem to get very far. I'm using WPA2 indeed, thought it might be difficult. I'll try the above and let you know how it goes :)

---

### Post by dhill13 on 2011-06-17
sudo iwconfig eth 1 key <my_key>
Error for wireless request "Set Encode" (8B2a) :
   SET failed on device eth1; Invalid argument.

---

### Post by chili555 on 2011-06-17
> **dhill13 said:**
> I had previously appended /etc/network/interfaces to include:

auto eth1
iface eth1 inet static
address <my address>
netmask 255.255.255.0
gateway <my gateway>

but didn't seem to get very far. I'm using WPA2 indeed, thought it might be difficult. I'll try the above and let you know how it goes :)Please try:```
auto eth1
iface eth1 inet static
address <my address>
netmask 255.255.255.0
gateway <my gateway>
wpa-essid <yourrouter>
wpa-psk <yourwpakey>
```Then do:```
sudo ifdown eth1 && sudo ifup eth1
```Be sure the address you select is outside the range of any DHCP server in the router.

---

### Post by superduperlinuxperson on 2011-06-17
sorry, but i do not understand the problem; is your firmware missing, or is it something else

---

### Post by dhill13 on 2011-06-17
ifdown: interface eth1 not configured
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
SIOCARDRT: No such process
Failed to bring up eth1.

---

### Post by dhill13 on 2011-06-17
@ superduperlinuxperson: In terms of wireless, I have tried all of the suggested drivers (STA and b43-lpphy) with no success.

In terms of wired, lsmod | grep r816* returns nothing. I guess this means that no such drivers (r8168 or r8169) are installed.

I have tried to install the r8168 driver manually, which was successful but didn't allow network access. Unfortunately after I reboot, the r8168 module seems to disappear. Strange!

---

