---
title: "Wireless Only Works w/ LiveCD"
date: 2006-01-12
forum: Networking &amp; Wireless
---

### Post by OPaul on 2006-01-12
When I boot of the Ubuntu 5.10 Live CD my wireless card works fine. However after installing Ubuntu and fully updating it the card no longer will detect any wireless networks. It appears fine in the Device Manager. The card is a USR2210 that uses a TI chip. Could one of the updates I did have caused the card to stop detecting networks?

---

### Post by Mr_Grieves on 2006-01-12
Weird.. and you tried the Wireless troubleshooting guide?
[http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)

---

### Post by OPaul on 2006-01-12
Yea, the kernel seems to load the device fine but it just doesn't pick up any networks even though they are there. When I run **iwlist wlan0 scan** it says "Interface doesn't support scanning".

When I run **lsmod** under the "Used by" column only 0 is listed for wlan.

---

### Post by OPaul on 2006-01-12
I ran **iwlist wlan0 scan** again, I had forgotten to Reactivate the device. This time I got "No scan results". This makes no sense, it works perfectly fine with the LiveCD.

---

### Post by OPaul on 2006-01-17
Does anyone have any idea how I could get this working?

---

### Post by jsteele on 2006-02-03
Hi,

I am having the same problem. I'm using a Dlink 650+ wireless card and it works fine with the LIVE cd but doesn't with the installation of ubuntu.

Has anyone solved this problem?

I could see other networks including mine when running the LIVE cd and I see no networks on the INSTALLATION.

---

### Post by bscbrit on 2006-02-03
How far through this troubleshooting guide do you get before you encounter problems: [http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643) ?

---

