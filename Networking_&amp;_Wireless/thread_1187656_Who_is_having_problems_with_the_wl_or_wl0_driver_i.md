---
title: "Who is having problems with the wl or wl0 driver in jaunty?"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by kevdog on 2009-06-14
Need to get a handle on who is using the wl or wl0 on jaunty and who is having problems with this?  This would be for broadcom chipset 4311, 4312 and 4322.  I'm sensing a lot of problems with these combinations.  Any input would be appreciated.

---

### Post by Ayuthia on 2009-06-15
I am currently testing out the wl driver in Ubuntu.  I currently use Kubuntu and it does not seem to have any problems with using the NetworkManager-applet.  However, if I use the Ubuntu and its NetworkManager applet, it will look like it has established a connection and but it does not properly connect.

My current workaround for this is to stop the NetworkManager process:
```
sudo /etc/init.d/NetworkManager stop
```and then I connect manually with no issues.  At this time I am currently testing this on a liveCD, so I have not checked to see if I still have the same issues with all the updates applied.

I am currently testing this with my HP tx2-1025dx that has a 4328 card:
> 08:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)

This card is generally not listed in Broadcom's site, but some of the 4328 cards do actually work with the Broadcom STA driver.

EDIT: I have installed the 32-bit version of Ubuntu on my tx2 and the only issue that I was able to encounter was that the ssb module was loaded.  Once I removed it and reloaded the wl driver, the connection worked fine through Ubuntu.  I ran the updates through just in case something changes, but so far all is stable.  I also tested the wl module on my HP dv6338se laptop with the 4311 card and it works fine there also.  At this point, my router is not set with encryption.

My current thought is that the issue could be in NetworkManager.  I am going to also try this with my 4311 card on my other HP laptop.

---

### Post by Ayuthia on 2009-06-15
If anyone else is having problems with the Broadcom STA module, can you let us know which card you have (lspci -nn), if you are using NetworkManager (what comes with Ubuntu) or something else like wicd, and if you are using WEP/WPA/WPA2 or no encryption on your router.  Some of this information may help in finding a workaround until the issue is resolved.

If you are not sure of any of this, please feel free to post what you know.

---

### Post by sobrien on 2009-06-15
I have a Lenovo S10e running Jaunty that has the Broadcom BCM4312.  It uses the wl driver.

It connects just fine to WPA encrypted wireless networks if the SSID is NOT hidden, but it does not connect at all to networks where the SSID is hidden.

I tried downloading the newest driver, compiled and loaded it (after unloading the old version), and it does exactly the same thing.  This netbook connects just fine to SSID hidden networks using Windows XP.

I have tried everything else that I can think of, along with everything that I can find about this problem on the Internet.  Googling:  jaunty wireless won't connect to hidden network  shows up a great many people that are having this exact same problem.

Regards,
Steve

---

### Post by kevdog on 2009-06-15
I'm not certain if the hidden ESSID issue is wl specific since broadcom cards have had problems with hidden ESSIDs sporadically as long as I can remember.

When did the wl driver become listed as wl0?  Is there a difference?

And for the record, thanks for the heads up with Network Manager.  I use WICD so I usually don't even test NWM -- although I know it seems everyone uses it!  I gave up on that program a long time ago.

---

### Post by Ayuthia on 2009-06-16
> **kevdog said:**
> I'm not certain if the hidden ESSID issue is wl specific since broadcom cards have had problems with hidden ESSIDs sporadically as long as I can remember.

When did the wl driver become listed as wl0?  Is there a difference?

And for the record, thanks for the heads up with Network Manager.  I use WICD so I usually don't even test NWM -- although I know it seems everyone uses it!  I gave up on that program a long time ago.

I want to say that wl0 just started in Jaunty however, there really is no difference with it being labeled as wl0.  It might just be a distinction between Ubuntu's version and the one from Broadcom (I haven't tried to compile the Broadcom version lately).  The wl0 is still the wl module and is loaded by modprobe wl and not modprobe wl0.

I am in agreement with the hidden ESSIDs also.  I have always had problems with connecting to hidden ones using the b43 or wl modules.

---

### Post by Ayuthia on 2009-06-16
After searching for patches for the Broadcom STA module for 2.6.30, I have stumbled upon some patches for hidden ESSID.  I have not verified that it works or not yet though.  If you have some experience with patching, you can try the patches from this [link]("http://packages.gentoo.org/package/net-wireless/broadcom-sta?full_cat").

---

### Post by kevdog on 2009-06-17
Are these patches just for hidden ESSID issues or in combination for something else?  I take it that these are kernel version specific.

---

### Post by Ayuthia on 2009-06-17
> **kevdog said:**
> Are these patches just for hidden ESSID issues or in combination for something else?  I take it that these are kernel version specific.

Sorry.  The link that I provided does not seem to show the patch for the hidden ESSID.  It looks like it is loaded in the portage updates.  I have attached the patch in this post.  The patch should work for 5.10.79.10 and the 5.10.91.9 versions of the Broadcom-STA source code.

The patch is not kernel version specifc but source code version specific.  It is also only for the ESSID fix since it is a one line patch.

---

### Post by Inconceivable! on 2009-07-11
> **Ayuthia said:**
> Sorry.  The link that I provided does not seem to show the patch for the hidden ESSID.  It looks like it is loaded in the portage updates.  I have attached the patch in this post.  The patch should work for 5.10.79.10 and the 5.10.91.9 versions of the Broadcom-STA source code.

The patch is not kernel version specifc but source code version specific.  It is also only for the ESSID fix since it is a one line patch.

I'm running Hardy on my Dell Inspiron 1525, and this patch fixed my wireless!  I can now connect to my hidden network.  

I ran into a problem installing the patched module, though...I copied the wl module file into the directory as per the instructions in the Broadcom readme, but for some reason Ubuntu kept replacing the fixed module with the broken one?  Or at least it seemed like this was happening, as I lost wireless on every reboot (file attributes appeared to be resetting).  Anyway, I disabled linux-restricted-modules and installed the module manually to fix this.  Is it ok to have done this?  

Anyway, thanks for finding this patch!

Edit: This patch also fixed my wireless in Jaunty.  Thanks again.

---

### Post by keplerspeed on 2009-07-21
A friend of mine has a dell inspiron with a broadcom chip, with continuing issues with connecting to hidden ESSID network. I want to try the patch supplied by Ayuthia, but I do not know what to do with the patch.

I have extracted the archive and there is a .patch file in there. What do I do with it?

---

### Post by Ayuthia on 2009-07-21
> **keplerspeed said:**
> A friend of mine has a dell inspiron with a broadcom chip, with continuing issues with connecting to hidden ESSID network. I want to try the patch supplied by Ayuthia, but I do not know what to do with the patch.

I have extracted the archive and there is a .patch file in there. What do I do with it?

You should copy the patch into the Broadcom STA source and do the following:
```
patch -p1 < name-of-patch
```
Replace name-of-patch with the actual patch name.  If it patches fine, you should then be able to compile the source.

Hope that helps.

---

### Post by vegesm on 2009-08-05
Hi! I have the same problem as you but I'm completely new to linux so I can't install the patch. Can you give give me a step by step tutrial? I have Ubuntu 9.04 and Broadcom 4312. I can't decide the version of my broadcom sta driver.

Ok, I compiled and installed the driver and it works fine. But after restarting Ubuntu somehow restores the wl driver so after loading I had to copy to file again use modprobe. Any solution for this?

---

