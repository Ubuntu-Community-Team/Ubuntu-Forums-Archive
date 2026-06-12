---
title: "Asus Eee PC 1001HA with RA3090 for dummies! (WEP)"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by Beauxjangles on 2010-05-18
Hi everyone,

I'm not one for compiling so I wanted to find the "dummies" way of setting the whole thing up.

If you have an Asus Eee PC 1001HA with an RT3090 wireless setup and you wish to run Ubuntu 10.04 LTS (Netbook edition) then this thread will make the entire process easy enough that even your 90 year old great-grandmum could set it up!

I made a point of installing the latest drivers for the RT3090 by downloading them from:
[http://www.ralinktech.com/support.php]("http://www.ralinktech.com/support.php")
Whether you do so is up to you, I just can't guarantee the installation will work if you don't. ;)

Please note: My network security is WEP based, so I am unsure if this will be successful for WPA, etc.

Ok, nice and simple...

**1.** Google and download:

ndiswrapper-common.deb
ndiswrapper-utils.deb
ndisgtk.deb

There will be many different versions, I simply downloaded the first result returned and it worked fine.

**2.** Chuck them all in the same folder so it makes the next step easy to execute...

**3.** Install each of the above in the listed order (common, utils, ndisgtk). This step should be as easy as double clicking on each of them and following the steps.

**4.** Make sure you know where to find the inf file required. Because I updated the drivers in XP and went with the default path, it was found:

C: (Filesystem in Ubuntu) -> Documents and Settings -> All Users -> Application Data -> Ralink Driver -> RT2860 Wireless LAN Card -> Driver -> rt2860.inf

If you chose to install the drivers elsewhere, make a point of knowing exactly where they are located.

**5.** Now, in Ubuntu, head over to:

System -> Administration -> Windows Wireless Drivers

From here, click on "Install New Driver" and hunt down RT2860.inf. Click "Open". Click "Install".

**6.** You should now have RT2860 listed with "Hardware present: Yes" below it.

**7.** Go and configure your network by simply clicking on the "Configure Network" button in the lower right hand corner.

**8.** Guess what? Great-Grandmum just finished setting up your wireless network card!

Again, I use WEP security, so I am unsure whether you will have equal measures of success with a WPA setup. From what I have read around these forums there is no "one-size-fits-all" approach.

If you have any trouble finding the .deb files for the ndiswrapper, etc I listed above, let me know and I'll be happy to provide you with the torrent for the files required.

I hope this helps anyone who is a bit of an Ubuntu "dummy" like myself.

---

