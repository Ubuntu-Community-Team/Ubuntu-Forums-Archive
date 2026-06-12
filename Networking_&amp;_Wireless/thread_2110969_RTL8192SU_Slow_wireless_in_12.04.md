---
title: "RTL8192SU: Slow wireless in 12.04"
date: 2013-01-31
forum: Networking &amp; Wireless
---

### Post by JohnDillinger43 on 2013-01-31
When I upgraded to 12.04 I suddenly started experience really slow download speeds with my wireless adapter.  I'm using a PremierTek PT-H10DN, which uses the RTL8192SU chipset.  Since it worked perfectly out of the box with 11.10 and the trouble started as soon as I upgraded, I'm assuming this is a driver issue.  I downloaded a driver from the RT site, but when I try to install it it asks for authentication and then says authentication failed.  Not sure why this is, or if installing this driver will even fix the problem.

I've come across a lot of posts of people complaining of the same issue with different wireless adapters.  I tried most of the fixes, e.g., disabling IPv6, but none of them fixed my problem.

---

### Post by ahallubuntu on 2013-01-31
By "authentication" you mean you are asked for a password but it is rejected?  That should be your "sudo" or admin password...

---

### Post by JohnDillinger43 on 2013-02-01
Yeah, I put in my sudo password, I get an error message, it asks again, and then it quits.

The RT help desk guy suggested uninstalling my current wireless driver and then trying again, but I don't know if that's the best course of action.

---

### Post by JohnDillinger43 on 2013-02-04
Any ideas?  I'm starting to wonder if it is a driver issue, because I got some pretty good results with speedtest.net the other morning.  But now I'm back to d/l speeds <1Mbps and u/l speeds around 1Mbps (I consistently get faster upload speeds, no idea why this would be the case).

I'd suspect the positioning of my wireless adapter, but when I stick a laptop right in that spot the speed's just fine.  For the same reason I'm loath to assume it's variability b/c I have cable internet; the other computers in the house always have decent speed.

---

### Post by JohnDillinger43 on 2013-02-05
Still having this issue.  Browsing the internet is like crawling over broken glass.  Ping speeds to both the router and the printer that sites right next to this desktop are in the 100-300ms range (when it doesn't drop packets).  I confirmed it's not a location issue; when I set our netbook next to the adapter and pinged from both computers the netbook got 10-40ms speeds and the desktop hundreds of ms.  Since I disabled IPv6 on the desktop I tried also doing that on my router, but that did nothing.

Any suggestions would be appreciate, or I'd be glad to provide more information.

---

### Post by ahallubuntu on 2013-02-05
Try building the driver again.  It sounds like you didn't succeed the first time.

Go back to the downloaded driver directory in a terminal and type

sudo bash install.sh

It should ask you only once this time.

If it rejects your password, you'll need to figure out what it is, sooner or later, to do any admin stuff in Ubuntu.

---

### Post by JohnDillinger43 on 2013-02-10
Thanks for your post -- I wasn't doing sudo in my initial command (which is why it was asking for authentication), and once I did, the script ran.  However, it didn't finish properly.  I'm getting "Error 2" when I run it.  I did find out using lshw that the driver I'm using is apparently rt2800, which seems very wrong (my chipset is 8192), so perhaps this is the problem.  Now if only I can get the driver to install properly....

---

### Post by JohnDillinger43 on 2013-02-13
I *think* I've got the driver installed.  At the very least, the makefile seemed to work and I didn't get any errors.  However, I'm not sure how to switch the driver over to the new one.  The readme suggested [wireless] down and then up again, which I tried, but doesn't that just turn the wireless off and back on?  Should that prompt it to load a different driver?

---

### Post by ahallubuntu on 2013-02-13
You can verify that the new driver has been installed by doing:

```
sudo lshw -C network
```

or

```
modinfo rtl8192su
```

(Assuming the module is called "rtl8192su" - if it's "8192su" use that instead.)

If the name has changed, you may have to add it to your /etc/modules file - not sure, I haven't used this exact driver before.  With rtl8192cu, you have to blacklist that and load the new module name "8192cu" with /etc/modules .

---

### Post by mikewhatever on 2013-02-13
> **JohnDillinger43 said:**
> I *think* I've got the driver installed.  At the very least, the makefile seemed to work and I didn't get any errors.  However, I'm not sure how to switch the driver over to the new one.  The readme suggested [wireless] down and then up again, which I tried, but doesn't that just turn the wireless off and back on?  Should that prompt it to load a different driver?

You should blacklist the 'old' rtl8192su module, by adding it to /etc/modprobe.d/blacklist.conf. Running the following will do it.
```
echo 'blacklist rtl8192su' | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Blacklisting will prevent it from auto-loading. Reboot, and then rebuild it once again.

PS: The problem with the 8192su is rather old. Here's a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190").

---

### Post by JohnDillinger43 on 2013-02-17
Okay, I tried rebooting, and found that Ubuntu did not load the new driver.  One problem may be the location of the driver?  I downloaded it to and built it in my home folder (just a folder called "wirelessdriver"); is there a centralized location for drivers that I need to move it to?  Or create a link from?

---

### Post by mikewhatever on 2013-02-18
It doesn't matter in which folder you build the modules. Rebooting isn't required, as it should load and work right away.

Have you blacklisted the built in module? There has been a typo (now corrected) in my previous post, rtl8192su and rtl8192cu are not the same. Make sure you blacklist the correct one.

---

### Post by JohnDillinger43 on 2013-02-18
I successfully blacklisted the old driver, but then the wireless didn't work at all -- it didn't load the new driver.  The readme tells me to do the following:

    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

I'm not sure what these commands do, so I'm not sure how to troubleshoot.  The second I gather is supposed to load the new driver (or simply activate the wireless adapter), but when I run it it says no such device.  Should I be using wlan0 instead of ra0?

---

### Post by ahallubuntu on 2013-02-18
> **JohnDillinger43 said:**
> I successfully blacklisted the old driver, but then the wireless didn't work at all -- it didn't load the new driver.  The readme tells me to do the following:

    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

I'm not sure what these commands do, so I'm not sure how to troubleshoot.  The second I gather is supposed to load the new driver (or simply activate the wireless adapter), but when I run it it says no such device.  Should I be using wlan0 instead of ra0?

If you have an RTL8192SU chipset and run the install script and it runs correctly, it will automatically install the driver.  You don't have to "copy" it anywhere.

Are you sure you really have a Realtek chipset?  Why are you messing with an Ralink chipset RT2870 driver above?  They are completely different.  (Not even the same company.)  If you really have a Ralink chipset, running the installer for the Realtek chipset will do nothing, but blacklisting the existing Ralink driver would of course remove the driver so you wouldn't have wireless.

---

### Post by ahallubuntu on 2013-02-18
> **JohnDillinger43 said:**
> When I upgraded to 12.04 I suddenly started experience really slow download speeds with my wireless adapter.  I'm using a PremierTek PT-H10DN, which uses the RTL8192SU chipset.

According to this, it uses the Ralink (not Realtek) RT3072 chipset:

[http://www.premiertek.net/products/networking/PT-H10DN-1W.html](http://www.premiertek.net/products/networking/PT-H10DN-1W.html)

---

### Post by JohnDillinger43 on 2013-02-19
Yep, you're right -- it's ralink, not realtek.  The driver I'm trying to use isn't actually 2870; I copied and pasted that from the (out of date) readme.  The actual driver file I have is rt5370sta.ko.  That's what was created by the makefile in the tar the tech support guys sent me; there's a line in the makefile that says CHIPSET = 5370, but I'm not sure how to properly change it (just changing that line throws up errors), or if that's necessary/best.

---

### Post by JohnDillinger43 on 2013-04-09
I messed around with this a bit more and still no luck.  I'm revisiting it now because I just had to reinstall Ubuntu, and whereas my connection was slow but functional before it is now unusable.  The connection works, it's just so slow that most things I try to access time out.  I tried rebuilding the driver, but I'm a little confused because in the makefile it has "CHIPSET = 5370", whereas my adapter uses RT3072.  Am I misunderstanding, or is there something wrong with that?  I tried changing the line in the makefile but then it won't compile.  I've emailed the tech support guys at PremierTek, but they seem loath to give me any useful information, so any further suggestions would be much appreciated.

---

