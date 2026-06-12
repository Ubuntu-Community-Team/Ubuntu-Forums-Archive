---
title: "Can't install ATI/AMD Propriatary FGLRX graphic Driver"
date: 2012-04-27
forum: Multimedia Software
---

### Post by headflux on 2012-04-27
Hi,

I have just upgraded to 12.04.  When I try to install the ATI/AMD Propriatary FGLRX graphic Driver (post-release updates), the installation fails with the error message:

"Sorry the installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

This log contains over 6000 lines.

I was able to install this driver under 11.10 and I would like to use the 3D desktop effects.

Can anyone help/advise please?

---

### Post by QIII on 2012-04-27
When you upgraded, did you first uninstall the proprietary driver?

---

### Post by headflux on 2012-04-27
I did a clean install of 12.04

---

### Post by QIII on 2012-04-27
Could you purge what you have (ATI driver), then run the following in the terminal and tell me what happens?

```
sudo apt-get install fglrx amdcccle
```followed immediately by 

```
sudo aticonfig --initial
```Don't shut down just yet (which is required to activate the driver).  Just let me know if there are errors.  If there are, copy and paste them.


Edit:  Sorry, I should have explained what the commands do.

The first installs the driver and the Catalyst Control Center.

The second creates an initial xorg.conf, which is necessary for the ATI driver.  Ubuntu doesn't install with xorg.conf by default.

---

### Post by collisionystm on 2012-04-27
i always use

sudo apt-get install fglrx-updates


fglrx is supposed to be older than fglrx-updates

Also, when installing this way you do not need to do an aticonfig

---

### Post by QIII on 2012-04-27
More than that, of course, is that the command I gave should have been

 ```
sudo apt-get install fglrx fglrx-amdcccle
```

anyway.

Sigh.  The package should still be identified.

And yes, I suppose now that the driver is released (rather than the Beta driver that has been in the repo), -updates should be used.

---

### Post by headflux on 2012-04-27
Hi QIII,I have followed your advice and received no errors.

I guess I'll reboot and see what happens...

---

### Post by headflux on 2012-04-27
Thanks collisionystm, I tried that and I got a message saying I was at the latest version,

---

### Post by collisionystm on 2012-04-27
> **QIII said:**
> More than that, of course, is that the command I gave should have been

 ```
sudo apt-get install fglrx fglrx-amdcccle
```

anyway.

Sigh.  The package should still be identified.

And yes, I suppose now that the driver is released (rather than the Beta driver that has been in the repo), -updates should be used.




amdccc is automatically included when you install fglrx

---

### Post by QIII on 2012-04-27
> **collisionystm said:**
> amdccc is automatically included when you install fglrx

Didn't used to be that way, but things change and old farts should keep up.

Thanks for the heads up.

Not to doubt you, but I am going to check this out on one of my machines when I get home so I can recommend this in good conscience.

---

### Post by Senior_Buckethead on 2012-04-27
I had  a problem with my ATI Radeon 3450 Card fglrx driver not installing:

[http://ubuntuforums.org/showthread.php?t=1962563](http://ubuntuforums.org/showthread.php?t=1962563)

Turns out there is a bug in which make doesn't compile. See Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/947871](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/947871)

Hope you have better luck than me.

Glenn.

---

### Post by QIII on 2012-04-27
He did have good luck.  It worked for him.


> **collisionystm said:**
> Also, when installing this way you do not need to do an aticonfig

fglrx-updates didn't create an xorg.conf for me.

---

### Post by headflux on 2012-04-28
I'm afraid neither suggestion has worked.

I've managed to install the standard ATI/AMD Propriatary FGLRX graphic Driver, but not the (post-release updates) version, which I need for desktop effects.

---

### Post by collisionystm on 2012-04-28
I installed fglrx post updates via jockey on fresh install of 12.04. The install failed. I opened a terminal and ran

sudo apt-get install fglrx-updates ( same thing ) said it was already installed. I ran

sudo apt-get install fglrx-updates --reinstall just to be safe. Everything is working fine. Radeon HD 6380

---

### Post by daniroma on 2012-05-07
**collisionystm** solution worked for me (Oneiric Ocelot, ATI Radeon HD5450):


[LIST=1]
[*]first purge all previous fglrx install (see  [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx) ). I use Synaptic to remove fglrx because there was no /usr/share/ati/fglrx-uninstall.sh
[*]sudo apt-get install fglrx-updates
[*]aticonfig --initial
[*]reboot
[/LIST]

---

### Post by Yellow Pasque on 2012-05-07
> **headflux said:**
> I've managed to install the standard ATI/AMD Propriatary FGLRX graphic Driver, but not the (post-release updates) version, which I need for desktop effects.

fglrx and fglrx-updates are the same version (8.960) at the moment, so that statement doesn't really make sense :?

---

