---
title: "Only some sites load"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by Nonno Bassotto on 2008-12-26
I have a computer with a freshly installed Ubuntu 8.10 and I experience a strange problem while browsing. I'm connecting by wireless to a WPA connection, using a USB wireless adapter. The connection is established, and I can reach the router page. But when I try to access the web, I can only browse some domains. For example I can see the Firefox add-ons and the Mozilla site, or [www.mat.uniroma1.it](www.mat.uniroma1.it). The other sites load partially: sometimes just the title, sometimes the first part of the page, then Firefox hangs at "trasferring data from...".

I should add that the connection works perfectly on windows with the same adapater, and on my laptop with Ubuntu and its internal adapter. Moreover it used to work on the same pc with Ubuntu 8.04 before changing the router (the old one is dead). After changing the router I had these problems, so I tried a fresh install of Ubuntu 8.10 (I had to upgrade anyway) but this didn't solve the issue (which I have with the live cd too).

In my syslog I can see something like, so it may have to do with
```

Nov 4 22:39:35 laptop NetworkManager: <info> (wlan0): supplicant connection state change: 7 -> 6
Nov 4 22:39:35 laptop NetworkManager: <info> (wlan0): supplicant connection state change: 6 -> 7

```
[this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/277634"). But the similarity stops here: for most sites I cannot see anything useful, just the first words.

---

### Post by albandy on 2008-12-26
It looks like a driver or hw bug, but 
Try changing your dns servers, if this not work try changing the mtu size.

to change your mtu size type this:

sudo ifconfig wlan0 mtu 900

Try changing temporaly your wpa key to wep.

---

### Post by Nonno Bassotto on 2008-12-26
No way :(. I didn't try to change to wep, though, because the router is locked. I just can't understand why it actually loads the first few bytes of every site... the title, maybe the favicon, some words... :( :(

---

### Post by albandy on 2008-12-26
In what wireless channel is working the router?

---

### Post by superprash2003 on 2008-12-26
you could try one of these or both incase it still doesnt work [http://www.prash-babu.com/2008/12/websites-loading-very-slowly-or-not.html](http://www.prash-babu.com/2008/12/websites-loading-very-slowly-or-not.html)

---

### Post by Nonno Bassotto on 2008-12-27
I tried using the Windows drivers through ndiswrapper and it still didn't work, so I don't think it's a driver problem. Changing the DNS ot the MTU didn't work either.

I'm at a loss... :( Is there a way I can at least share the connection? I have a laptop with a working wireless connection nearby (also based on Ubuntu). Is there a way I can use the laptop connection, that is Router->Laptop->PC?

---

### Post by Nonno Bassotto on 2008-12-27
I was finally able to change the security settings on the router. The problem persists with WEP or even no security at all. :confused:

---

### Post by albandy on 2008-12-27
Try selecting another wireless channel in the rotuer. I had got some problems with my old router using channels between 10 to 13

---

### Post by Nonno Bassotto on 2008-12-27
Changing the channel didn't work either. I found another laptop with ubuntu and no internal wifi. I checked that the same problem happens on this, using the same usb adapter. So I guess I'll just buy another usb adapter, hoping the new one will work. I'm a bit skeptic about this, though, because the one I'm using now used to work perfectly without the need for any configuration until recently.

---

### Post by Nonno Bassotto on 2008-12-27
Even the new pendrive didn't change anything. Any idea? Please note that I'm able to browse some sites without any problem, it depends on the domain. Yet the DNS is working properly under windows and under the laptop with internal wifi with Ubuntu. Moreover changing DNS didn't solve the problem. What can this mean?

---

### Post by albandy on 2008-12-28
Check if the new wifi device uses the same old wifi device chipset. Maybe is a driver problem.

---

### Post by Nonno Bassotto on 2008-12-29
No, the new device (which by the way I took back to the shop) uses a different chipset and driver, and by the way should be weel supported under linux, so it nota driver problem. It really looks like the ROUTER is not linux frendly, although it works with the laptop and its internal wifi... :confused:

---

