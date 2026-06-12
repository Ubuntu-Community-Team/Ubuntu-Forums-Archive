---
title: "Wireless Network unvaible or disabled on Atheros AR5001"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by nooffswitch on 2010-07-08
A fresh install of Ubuntu however wireless is disabled according to NetworkManager. Wired connection is working fine.


iwconfig---------------------------------------

ben@Zordon:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
------------------------------------------------




ifconfig----------------------------------------
eth0      Link encap:Ethernet  HWaddr 00:1d:72:66:e4:f2  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe66:e4f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35967 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54876951 (54.8 MB)  TX bytes:3492709 (3.4 MB)
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2272 (2.2 KB)  TX bytes:2272 (2.2 KB)
------------------------------------------------------------------------------

/etc/network/interfaces-----------------------------------------------
auto lo
iface lo inet loopback
------------------------------------------------------------------------

That seems to be the info asked for quite alot on the forums.
Anybody know where im going wrong?

---

### Post by nooffswitch on 2010-07-08
after doing sudo apt-get install linux-backports-modules-wireless-lucid-generic
and reinstalling a couple of nvidia display drivers for some reason my wifi card is now installed, however cannot pick up any networks. Any advice?

---

### Post by randomn00b on 2010-07-08
As a disclaimer, I am completely new to linux.  However, I just blew ten hours this weekend trying to install a DWL-G650 wireless card with an Atheros 5001X+ chip on it to Ubuntu 10.04 server edition.  I feel your pain - there are a lot of websites that deal with Atheros chips, but none are quite the AR5001X+, which is different for some reason.  I think it's old enough that people just forgot about it.

So, for whatever it's worth, here are my notes:

- Installed HAL by hand, from internet instructions
- Installed madwifi driver by hand, from internet instructions
- Installed wpa_supplicant
- Changed /etc/network/interfaces to configure ath0 device
- black listed ath5k and un-blacklisted ath_pci
- Added "pre-up sleep 20" command, which seemed to help device lock into specified network (as opposed to nearby linksys network)

The key break seemed to be to get madwifi to work as the driver instead of ath5k, which - despite it's name - doesn't seem to work on Atheros 5001X+ chips.  I don't know if I needed to install HAL or not - I did it before I installed the madwifi driver.  Couldn't tell if it was necessary or not.

This thread was helpful to me (last post in it):
[http://ubuntuforums.org/showthread.php?t=1505100](http://ubuntuforums.org/showthread.php?t=1505100)

---

### Post by reckik on 2010-08-26
TY This finally seems to work. The key for me was adding the following to my /etc/network/interfaces

> # wireless card manual add
auto ath0
iface ath0 inet dhcp
wireless-essid SC1742
wireless-key s:0000000000000

for the first time this is giving me a stable connection on my Acer Aspire One atheros ath5k ar5001 wireless network in Lucid!

---

### Post by pkadetiloye on 2010-11-13
Try this
[http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)

:guitar:

---

### Post by uncaspi on 2010-11-13
If you add any additionally cards in interfaces file they are not handled by the network-manager.

---

