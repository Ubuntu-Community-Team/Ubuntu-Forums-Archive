---
title: "How to: Get the wireless working in ubuntu for the RPI 802.1x network"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by zalberico on 2009-04-07
ubuntu 8.10 - lenovo T61P

1. Click on network manager gnome applet

2. Click on rpi_802.1x

3. A dialogue box will come up, change "LEAP" to "Dynamic WEP (802.1x)"

4. Change Authentication from "TLS" to "Protected EAP (PEAP)"

5. Leave Anonymous Identity Blank

6. Leave CA certificate to None

7. Change PEAP version to version 0

8. Leave inner authentication to MSCHAPv2

9. Enter RCS user name

10. Enter RCS password

11. Select OK, you'll get a warning about having no certificate, click ignore

12. Connect

//This worked for me on April 7, 2009.

---

### Post by thebinz on 2009-04-24
Cool, thanks zman.

I just setup the wireless 802.1x on my Arch box. I've been using the wired ethernet all year for my desktop machine.

I had little success connecting to the RPI network at the beginning of the year... probably because I never changed PEAP to Version 0.

---

### Post by zalberico on 2009-05-02
great, I'm glad it helped you.  I got it put up on the help desk website so it'll be easy for people to find, although I don't know if it still holds true in 9.04

---

### Post by wt200999 on 2009-09-03
This did not work for me, I am using ubuntu 9.04, it just tries to connect for a while, then pops up the box again. I went to the helpdesk and they did the same thing as you wrote and it didn't work.

---

### Post by zalberico on 2009-09-11
ubuntu 9.04 - lenovo T61P

1. Click on network manager gnome applet

2. Click on rpi_802.1x

3. A dialogue box will come up, change "LEAP" to "Dynamic WEP (802.1x)"

4. Change Authentication from "TLS" to "Protected EAP (PEAP)"

5. Leave Anonymous Identity Blank

6. Leave CA certificate to None

**[COLOR="Red"]7. *Leave PEAP Version to Automatic*[/COLOR]**

8. Leave inner authentication to MSCHAPv2

9. Enter RCS user name

10. Enter RCS password

11. Select OK, you'll get a warning about having no certificate, click ignore

12. Connect

//This worked for me on Sep 18, 2009.

---

### Post by birddog165 on 2010-01-30
Dude thank you so much. This works for me on 9.10

---

