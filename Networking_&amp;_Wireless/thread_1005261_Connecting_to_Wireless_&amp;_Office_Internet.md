---
title: "Connecting to Wireless &amp; Office Internet"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by wordslinger on 2008-12-08
Since the Network Manager Icon cannot be fixed at all in Ubuntu, I was wondering if there is any other way to connect to a wireless service provider and to the Office Internet?

Can someone provide me with some assistance here? I have no problems connecting to my home ADSL service. But, I can't set the dhcp settings to connect to my office network since the network manager icon is missing after a full update on Ubuntu 8.10.

The other thing is, why does the people at Canonical not able solve a simply problem like this? What are they waiting for? It makes life so difficult just to connect to the Internet.

---

### Post by Thanoulis on 2008-12-08
Have you tried to run the Network Manager Applet?
Go to System->Preferences->Sessions, click Add and write:
```
Name:*Network Manager*
Command:*nm-applet --sm-disable*
Comment:*Network Manager applet*
```
Then click save.
Try to logout and log on again, just to verify it works.

P.S:It isn't Ubuntu fall, as all my Ubuntu installs (since 7.04) had the Network Manager Applet icon in the notification area.

---

### Post by superprash2003 on 2008-12-08
here's how you can get the old network manager [http://prash-babu.blogspot.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html](http://prash-babu.blogspot.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html) follow till Step 4

---

### Post by wordslinger on 2008-12-09
Hi,

It is still not working. I can't even get online here in office. What am I suppose to do?

---

### Post by wordslinger on 2008-12-10
Dear SuperPrash,

Thank you so very-very much. I take my hat off to you!

I followed your instructions and I am now online.

Cheers!

---

