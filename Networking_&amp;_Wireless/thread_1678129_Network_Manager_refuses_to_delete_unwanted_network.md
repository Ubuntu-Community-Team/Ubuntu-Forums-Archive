---
title: "Network Manager refuses to delete unwanted networks"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by Drifty on 2011-01-29
I am running ubuntu 10.04 and tried to clean up my wireless network settings in Network Manager. For some reason - I have no idea how it got there - I have 3 entries of the same wireless network.

One with the needed wpa- password and the two boxes 'connect automatically' and 'make available to all users' checked. The other two entries are identical, have nothing in their password fields, have their ' connect automatically'- box checked and their 'make available to all users'- box unchecked and grayed-out when trying to edit the settings.

As I need only the first one anyhow, and as that one works just fine - I auto-login as user upon booting the box and wlan connects automatically - I just wanted to delete the two extra entries to have a clean configuration. Clicking on the delete button makes them disappear just fine, but when I then close the edit box and reopen it again they are there again (also after a reboot).

I assume that these settings must be strored in a configuration file somewhere, but I haven't succeeded in finding out just where this is stored so I could delete it there. On the other hand i would expext no difficulties doing this in the GUI editor box.

Could someone please tell me where I can find the settings file to delete these entries manually and/or why the editor box of Network Manager might generate such an unexpected behaviour?

Thanks!

---

### Post by wilee-nilee on 2011-01-29
Use the edit connections function from the wireless icon in the panel click on wireless 2nd tab then delete the ones you want.

---

### Post by Drifty on 2011-01-30
> **wilee-nilee said:**
> Use the edit connections function from the wireless icon in the panel click on wireless 2nd tab then delete the ones you want.
Well, as I explained, that's just what I did. Problem is that the thus deleted entries keep popping up again after closing and reopening the edit function.

Maybe there is something incorrectly set somewhere. I have no clue where to check. Maybe it would help if I just knew where the settings are stored. I would imagine that there must be a configuration file somewhere, but I have not been able to find it. I have searched around quite a bit, but I was not able to find any reasonable hint.

---

### Post by DanCar on 2012-02-04
I have the same issue.  Delete it and it just comes back.

---

