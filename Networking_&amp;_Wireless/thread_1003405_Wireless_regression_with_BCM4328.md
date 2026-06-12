---
title: "Wireless regression with BCM4328"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by Idefix82 on 2008-12-06
After upgrading my kernel to 2.6.24-22 from -19 (still on Hardy) my Broadcom WiFi card stopped working. It still showed me the available networks but started asking for the key to my router again and did not connect when I entered the key (WEP 128 bit). I have enabled the restricted driver wl but to no avail.

Then I kicked out wl and started ndiswrapper again and WiFi works perfectly again.

Has anybody managed to get the BCM4328 to work in Hardy without ndiswrapper?

---

### Post by BobW on 2008-12-07
I was able to connect, but I have to connect manually every power up and the connection is unstable.

I think the wl driver isn't ready for real use yet.

---

### Post by Ayuthia on 2008-12-07
Have you tried compiling the wl driver from [Broadcom]("http://www.broadcom.com/support/802.11/linux_sta.php") instead of using the updated version in the repository?  It is the original version that was added to Hardy.  The downside to it is that it will not be able to use ssh and possibly some other secure remote connections.

---

### Post by Idefix82 on 2008-12-08
> **Ayuthia said:**
> Have you tried compiling the wl driver from [Broadcom]("http://www.broadcom.com/support/802.11/linux_sta.php") instead of using the updated version in the repository?  It is the original version that was added to Hardy.  The downside to it is that it will not be able to use ssh and possibly some other secure remote connections.

Thanks for the hint. Since ssh is a must for me I will give it a pass and wait until a driver comes out that really works.

---

