---
title: "ATI driver fail - Palit Revolution 700"
date: 2014-04-06
forum: Multimedia Software
---

### Post by njwalczak on 2014-04-06
Hi

I have just installed 13.10 64 bit on a gaming PC. I had it working fine using the default "gallium" display drivers and Portal worked fine from steam... but Minecraft was very slow so I went in search of some more specific gfx drivers... there are none at all available for this card - the manufacturer doesn't even seem to want to admit to having manufactured it! But it's basically a radeon HD4870 x2

...so I downloaded:
amd-driver-installer-12-4-x86.x86_64.run

I first ran this from a terminal session and got errors relating to a device still in use.

I then ran it after exiting from the lightDM and got a little further but the error log reported the following header file as missing:

/lib/modules/3.11.0-19-generic/build/include/linux/version.h

(I checked, the directory is correct by that header is not there)

Now, I cannot log in to the GUI - it draws the desktop background and the login menu - but when I put my password in, the screen flickers and returns me to the login menu.

This is similar to an error here:
[http://askubuntu.com/questions/176593/cant-login-after-amd-catalyst-driver-installation](http://askubuntu.com/questions/176593/cant-login-after-amd-catalyst-driver-installation)

BUT the solution suggested does not work for me.

Any help on how to proceed would be great. If not, I would just like to restore the default drivers. Thanks.

---

### Post by njwalczak on 2014-04-06
I got myself out of a hole using this page (section at the bottom):
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

According to this:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I already had the correct driver "gallium RV770" - I don't know what Minecraft's problem was...

---

### Post by Yellow Pasque on 2014-04-06
The proprietary fglrx/Catalyst driver no longer supports your card, and if you want to run the Catalyst Legacy driver, you need to use a much older version of Ubuntu (12.04.1). Please mark thread solved.

---

### Post by njwalczak on 2014-04-06
The open source driver is fine. Got HDMI sound working now too. Apart from that - and my overzealousness, it was actually perfect out-of-the-box which is very nice to see. :)

---

