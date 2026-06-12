---
title: "iwconfig wireless setup"
date: 2006-02-28
forum: Networking &amp; Wireless
---

### Post by ate50eggs on 2006-02-28
I'm trying to install a minimal system on an old crappy laptop (pII 64M). I got the wireless card working with ndiswrapper. iwconfig gives:

wlan0   IEEE 802.11b ESSID: off/any
           Mode:Managed  Frequency:2.437 GHz Access Point: 00:00:00:00:00:00
           Bit Rate:1 Mb/s   Sensitivity=-200 dBm
           RTS thr:2346 B    Fragment thr:2346 B
           Power Management: off
           Link Quality:100/100 Signal level:-94 dBm Noise level:256 dBm
           Rx invalid nwid:0    Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0   Invalid misc:1   Missed beacon:0

but sudo ifup wlan0 gives:

Ignoring unknown interface wlan0=wlan0.

I was able to get everything setup with the default desktop's tools, but the computer is too slow for the wm/desktop. I'm out of my depth setting this up with the command line. I need to enter my WEP key and probably some other stuff. not sure of all the stuff I have to do and in what order. Been playing around with *iwconfig wlan0 *enc and other stuff, but I'm ready to admit I don't know what I'm doing.

---

### Post by direwolf on 2006-02-28
sudo ifconfig wlan0 up 

then use iwconfig to set other settings like 

sudo iwconfig wlan0 mode managed 
sudo iwconfig wlan0 essid yourssid 

etc.

---

### Post by Jova on 2006-02-28
direwolf is right

edit /etc/network/interfaces

and add all iwrelated as 

iface wlan0 inet dhcp
wireless_mode XXX
wireless_essid XXX
wireless_nick XXX
wireless_rate XXX
wireless_txpower XXX

change xxx with proper setings

---

### Post by ate50eggs on 2006-02-28
awsome. this is very helpful. not sure how to fill in the x's in these commands:

iface wlan0 inet dhcp
wireless_mode XXX
wireless_nick XXX
wireless_rate XXX
wireless_txpower XXX

which are necessary? how do i figure out how to fill in the rest?

---

### Post by oyvindh on 2006-03-01
To find out what values to use for the different settings you can read the iwconfig manual 'man iwconfig'

---

### Post by aosmith on 2006-03-01
chances are you dont need most of them...

---

### Post by ate50eggs on 2006-03-02
Everthing works now. It was easier than I thought, the man pages can make things very intimidating.

---

