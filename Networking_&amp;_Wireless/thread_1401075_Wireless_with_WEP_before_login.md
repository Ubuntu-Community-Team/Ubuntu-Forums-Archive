---
title: "Wireless with WEP before login"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by inkhorn on 2010-02-07
Hi all,

I have a laptop, with Ubuntu 9.10, that I never take anywhere outside of my home wireless network.  I want to set it up so that it will log in to my wireless router and gain an internet connection before I log in to my user account using gnome.

My router uses WEP and requires me to log into it using a very long numerical key.  Something like 1234567894561354789543412.  I've tried editing /etc/network/interfaces thinking that this would do the trick.  My file had a stanza similar to the following:

```

auto wlan0
iface wlan0 inet dhcp
    address 192.168.2.11
    netmask 255.255.255.0
    broadcast 192.168.2.255
    gateway 192.168.2.1
    dns-nameservers 192.168.2.1
    wireless-essid MYSSID
    wireless-key 1234567894561354789543412
    wireless-keymode open
```However that didn't work.  I've tried taking away some of the options, changing the 'dhcp' option to 'static', etc etc.  I've even tried setting up wpa_supplicant to work with WEP but i'm not sure that I've done the right thing.

Has anyone managed to configure /etc/network/interfaces to allow their Ubuntu machine to connect to a wireless router with WEP before login?

Inkhorn

---

### Post by chili555 on 2010-02-07
I suggest:> auto wlan0
iface wlan0 inet static
    address 192.168.2.11
    netmask 255.255.255.0
#    broadcast 192.168.2.255
    gateway 192.168.2.1
#    dns-nameservers 192.168.2.1
    wireless-essid MYSSID
    wireless-key 1234567894561354789543412
#    wireless-keymode openI would drop the dns part because I don't see anywhere in *man interfaces* where you can specify DNS nameservers here. I'd just edit */etc/resolv.conf* to add this information.

I also suggest proofreading...twice...the WEP key. Is it 26 characters?

Key mode is open by default.

Last, it will probably never work unless you do:```
sudo apt-get remove --purge network-manager
```For comparison, here is my interfaces file with the WEP key obscured:> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid GBR1
wireless-key 096XXXXXAFE 

#auto eth0
iface eth0 inet dhcp

---

### Post by inkhorn on 2010-02-07
Thank you so much!  I've been obsessing over this all day and I can finally access my computer's SSH server without having to log in to my main user account.  It really seems like the key component was getting rid of network manager!

You rock, chili555 :)

Inkhorn

---

### Post by heitzmann on 2010-04-28
I'm on a wired connection on Lucid and had the problem of no connection before login.

I fixed it by simply checking the option "Available to all users" on my connection properties on the Network Manager.
Maybe this can help you as well.

---

### Post by netcarver on 2010-05-09
I'm looking to solve the same problem as inkhorn except that the access point is using WPA. Would this method work for a WPA key -- or do I need to setup wpa_supplicant too (sorry, new to this.)

Thanks in advance.

---

### Post by chili555 on 2010-05-10
In spite of how complex some posts make WPA look, this simple arrangement works for me:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid mylilrouter
wpa-psk mysecretkey

#auto eth0
iface eth0 inet dhcp
```Pretty simple, eh? The downside is that anyone that has access to your computer and a live CD can read the key in plain text. If my computer is lost or stolen, I will disconnect my router until my ISP cancels the account. My WPA password will be the least of my problems.

---

### Post by netcarver on 2010-05-10
@chili555, many thanks for the reply. However, heitzmann's solution has solved this for me.

Thank you both!

---

