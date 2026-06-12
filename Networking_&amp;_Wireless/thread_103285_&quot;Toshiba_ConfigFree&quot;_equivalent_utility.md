---
title: "&quot;Toshiba ConfigFree&quot; equivalent utility?"
date: 2005-12-13
forum: Networking &amp; Wireless
---

### Post by g-a-c on 2005-12-13
Is there anything like Toshiba ConfigFree for Linux, which will

a) Let me set up multiple profiles such as office, home, roaming etc
b) Let me assign wired/wireless network settings to each profile (such as SSIDs, DHCP, etc)
c) Also be able to change proxy server settings?

I guess I could script something very similar with gconf-tool to change the Gnome proxy settings depending on the output of ifconfig (I've already done something similar so that when I open a terminal window it sets http_proxy depending on whether I'm at work or at home). However, I don't know how I can set it up for other programs as not all of them (Firefox, Synaptic, update-manager, etc) seem to use the default I've set in Gnome?

---

### Post by rykel on 2005-12-13
i would be very interested in this topic too, as i am using a toshiba laptop (m40-545) and i use configfree rather frequently when i am in windows.

which toshiba model might you be using? and do you have an nvidia card in it?

high five to a fellow toshiba user!   :KS

---

### Post by 23meg on 2005-12-13
I use a Toshiba as well and totally hate the bloat of ConfigFree. I don't connect to the net with Windows anyway so I have no use for it. The closest thing that comes to mind is Network Manager. I'd try GTKWifi + the usual network settings before that.

---

### Post by rykel on 2005-12-14
[QUOTE=23meg]I use a Toshiba as well and totally hate the bloat of ConfigFree. I don't connect to the net with Windows anyway so I have no use for it. The closest thing that comes to mind is Network Manager. I'd try GTKWifi + the usual network settings before that.[/QUOTE]

i use gtkwifi as well, and yes, it works darn well.

just tat i enjoy eye candy, and was wondering if there was anything as visually appealing as configfree...

btw, is there any way i can get ubuntu breezy to activate my 5-in-1 card reader? seems like it isn't working, altho' i seldom use it...

---

### Post by g-a-c on 2005-12-14
As far as I can see, there isn't a way for GTKWifi or NetworkManager to be able to detect where I am from an IP address (at work we use 2 large /16s, so it's easy to tell when I'm at work) on either a wired or wireless connection and set up proxy settings correctly? I also don't get on with all the graphical crap in ConfigFree but I do like the way it can save things like proxy/firewall settings for each profile, making it easy to switch between work and home automatically/with a single click.

It's a Tecra A5 widescreen with Intel 915 mobile graphics, no Nvidia for me :)

I haven't tried the built in SD reader as I rarely use SD cards anyway, so I have no idea about that.

---

### Post by 23meg on 2005-12-14
[QUOTE=rykel]i use gtkwifi as well, and yes, it works darn well.

just tat i enjoy eye candy, and was wondering if there was anything as visually appealing as configfree...

btw, is there any way i can get ubuntu breezy to activate my 5-in-1 card reader? seems like it isn't working, altho' i seldom use it...[/QUOTE]Network Manager is visually closer to ConfigFree but keep in mind that it's a replacement for the whole Debian ifupdown system, whereas GTKWifi runs on top of the usual stack.

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

---

### Post by g-a-c on 2006-02-01
I'd forgotten about this thread, oops! Network Manager is very nice, but the sk98lin driver I'm using for my Marvell NIC doesn't seem to support link detection (at least not in the manner that Network Manager is expecting). It logs to /var/log/messages OK, and there's a carrier file in /sys/net/whatever but Network Manager can't detect when it comes up and change to it from wireless.

In short it's a nice piece of software, although sadly won't change things like my proxy settings etc, and doesn't work perfectly with my NIC. However, I've also come across whereami which, although a bit messy and hard to get to grips with, looks like it should be able to make the changes I want, maybe alongside Network Manager for actually establishing the links.

---

### Post by aseem_mal on 2006-02-01
Hi Toshiba Laptop owners. This may be a little OT, but its for any Toshiba owner using Ubuntu and Wireless internet.
I recently installed Ubuntu 5.10 on my Toshiba Satellite A75 with built in Atheros wifi. My wireless network works fine with no encryption. But if I enable encryption, WEP or WPA, it doesn't work.
I have tried all kinds of things, including wpa_supplicant. I followed all the steps, but Nothing is working. Any help from someone who has done this successfully will be a big help. I wonder isn't there a simple gui based utility, not terminal based, where I can simply enter my SSID and my pass-phrase, and be connected. Just like the Config Free of windows. I wish. :-k

---

