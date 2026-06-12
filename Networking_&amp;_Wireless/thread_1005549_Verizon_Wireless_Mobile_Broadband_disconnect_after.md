---
title: "Verizon Wireless Mobile Broadband disconnect after 2.5 minutes, intrepid ibex 8.10"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by thebigkevdogg on 2008-12-08
Hello,

I recently did a fresh install of Intrepid Ibex 8.10 on my laptop after a hard drive crash, and am trying to get my Verizon Wireless mobile broadband card working.

I was originally incredible impressed with how it worked right out of the box with the new version of the Network Manager Applet. It showed up right away after plugging it in, and connected easily. The only problem is that I get disconnected after exactly 2.5 minutes every time. Here is what shows up in /var/log/messages:

```
Dec  8 08:27:14 milner pppd[6134]: No response to 4 echo-requests
Dec  8 08:27:14 milner pppd[6134]: Serial link appears to be disconnected.
Dec  8 08:27:14 milner pppd[6134]: Connect time 2.5 minutes.
Dec  8 08:27:14 milner pppd[6134]: Sent 58868 bytes, received 620152 bytes.
Dec  8 08:27:14 milner pppd[6134]: Connection terminated.
Dec  8 08:27:15 milner pppd[6134]: Exit.
```

I then went into the connection settings and thought that the problem might be not specifying a username/password, so I added my username of 'xxxxxxxxxx@vzw3g.com' (where the x's are my 10 digit number) and the password of 'vzw', but that didn't make a difference. Anyone have any ideas? This happens every 2.5 minutes to the second.

Card info:
Qualcomm 3G CDMA
3229B-NVWXV620
ExpressCard|34

Thanks a lot!
Kevin

---

### Post by thebigkevdogg on 2008-12-08
OK I figured it out with a little help from this page: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117554]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117554")

It turns out that Verizon just doesn't respond to the echo requests, and leaving the "Send PPP echo packets" option unchecked in the network manager configuration dialog didn't actually disable it.

I had to edit /etc/ppp/options as root, and disable echo manually:

changed settings:

```
lcp-echo-interval 0

lcp-echo-failure 0
```

Hopefully this will help someone else!

---

### Post by thebigkevdogg on 2008-12-08
oops...repost!

---

### Post by matt.matolcsi on 2009-03-16
Awesome! This probably saved me 2-3 hours of hacking and reading through random man pages. 

Big Thanks, bro! I can confirm that this also solves my problems with tethering through Sprint. (FWIW, I'm on the SERO plan.)

---

### Post by johnnylavah on 2009-03-29
i cannot seem to get my pc5750 to connect, although ubuntu recognizes the card.  any ideas?

---

