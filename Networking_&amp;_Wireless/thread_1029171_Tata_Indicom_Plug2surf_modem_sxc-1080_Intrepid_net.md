---
title: "Tata Indicom Plug2surf modem sxc-1080 Intrepid network-applet"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by beyboo on 2009-01-03
The Network manager applet V0.7 shipped with Intrepid fails to retrieve data from the Tata Indicom plug2surf USB CDMA 1x Modem [epivalley sxc-1080]("http://eng.sungiltel.com/products/sxc-1080.html") modem 

As a result, when I plug in the USB modem, a wireless broadband profile is present, but since it fails to retrieve modem, network manager applet is unable to set the profile to work. 

The modem works perfectly with wvdial command.

Bug has been documented at launchpad [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/305395")

Encourage you to subscribe to this if you use intrepid and this USB modem.

---

### Post by sandip26879 on 2009-01-18
I also have the same problem.

---

### Post by sandip26879 on 2009-01-18
Success at last.
Follow my steps :--

1.  There is an entry for TATA INDICOM Plug2surf.
    Choose that and then edit. Change the phone number to #777.
    Also change user name to internet and password to internet.

2.  Then choose Connect automatically.

3.  Now right click on Network Manager applet and unselect enable networking and
    reselect it. It will fail at first attempt.

4.  Then again go to mobile broadband. You will see that Auto CDMA broadband has been
    added. Edit that and set the correct phone number, user name and password. Also
    remember to check Connect Automatically.

5. Now it's done.

---

