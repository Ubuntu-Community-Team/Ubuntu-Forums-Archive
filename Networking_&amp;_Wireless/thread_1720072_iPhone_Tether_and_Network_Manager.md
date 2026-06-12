---
title: "iPhone Tether and Network Manager"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by timothyparker@gmail.com on 2011-04-02
This is on Lucid, using a Dell Mini.

I installed the required packages for a USB tether to my iPhone.
Network Manager recognized it immediately as wwan0, but it doesn't connect.

Also, it never asks me for the password to connect to the Personal Hotspot (as it does when I can connect from Windows).

Thanks

---

### Post by timothyparker@gmail.com on 2011-04-02
Oddly, it works perfectly with the KDE Network Manager.
What might be the problem in Gnome?????

---

### Post by johnbyrne on 2011-04-12
I'm using Ubuntu 10.10 64bit on a Dell Inspiron 1501. I'm trying to use my iPhone 4 personal hotspot, however I haven't had success yet. Everything is up to date. I'm running iOS 4.3 and the wifi access point shows up in Wicd, but it won't give me an IP address and so won't connect. It also won't tether via USB. I have the ipheth modules installed, but it just doesn't work. When I connect the phone via USB cable, it recognizes the camera and the music library, but no tethering.

I would so love to get this working. 

Any ideas?

---

### Post by johnbyrne on 2011-04-14
OK, I fixed the USB tethering by compiling the ipheth driver and then running: sudo insmod ipheth.ko

It seems I have to do this every time, so I created an application launcher on my desktop that does it.

Still trying to get wifi to connect to the personal hotspot on the iphone 4, however.

---

