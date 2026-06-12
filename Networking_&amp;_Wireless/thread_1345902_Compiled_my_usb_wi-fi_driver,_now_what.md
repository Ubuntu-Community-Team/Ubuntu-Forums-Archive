---
title: "Compiled my usb wi-fi driver, now what?"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by darkod on 2009-12-04
I suspect my usb wi-fi adapter is working slow and to make sure I get maximum out of it I downloaded the driver from Ralink website and compiled it. The driver is RT3070STA and all went fine.
First ubuntu was trying to use rt2800usb and it wasn't working at all like that. I blacklisted that one.
But then it seems ubuntu is trying to use rt2870sta. If I run sudo lsusb it shows:

```
Bus 002 Device 003: ID 148f:3070 Ralink Technology, Corp.

```

I believe that means the chip is actually RT3070, that's why I downloaded and compiled that driver.
Now how do I make it load automatically on boot and how to make sure the usb wi-fi is connected to rt3070sta and not rt2870sta? Blacklisting rt2870sta?

Also in Connection Information in NetworkManager, under driver it just says "usb". What's that? I know earlier it said rt2800usb but that was the wrong one to use and got blacklisted.

Any advice?

---

### Post by chili555 on 2009-12-04
> Blacklisting rt2870sta?Yes. Also, add to */etc/modules*:```
rt3070sta
```Reboot and let us know.

---

### Post by darkod on 2009-12-04
Thanks. I actually got it working, I think. :)
Too tired to write the solution, it's 2:30am here. This weared me down. :)
It seems the drivers need some patch to correctly work in Karmic even if the compile doesn't give errors. I couldn't find the patch for RT3070 so I patched and compiled RT2870 driver, even though I have the RT3070 chip.
So it went the other way around, in /etc/modules I added rt2870sta and blacklisted rt2800usb and rt3070sta just in case my previously compiled driver is still around.
Seems to work even though this was only for ad-hoc network but my adapter created it with 150Mb which is its maximum. Previously it was giving me whole 1Mb speed. :)
Cheers.

---

### Post by nightmicu on 2010-01-12
> **darkod said:**
> Thanks. I actually got it working, I think. :)
Too tired to write the solution, it's 2:30am here. This weared me down. :)
It seems the drivers need some patch to correctly work in Karmic even if the compile doesn't give errors. I couldn't find the patch for RT3070 so I patched and compiled RT2870 driver, even though I have the RT3070 chip.
So it went the other way around, in /etc/modules I added rt2870sta and blacklisted rt2800usb and rt3070sta just in case my previously compiled driver is still around.
Seems to work even though this was only for ad-hoc network but my adapter created it with 150Mb which is its maximum. Previously it was giving me whole 1Mb speed. :)
Cheers.

Greetings,

 I have another thread open on this matter and I have been pulling my hair out for the past two days trying to get a Monoprice USB WiFi card work with Ubuntu 9.10. The USB device ID is 148f:3070, Ralink Corp - same as yours. Can you PLEASE try to provide some step by step instructions or point me in the right direction? So far I think I have been pointed in the direction of rt2800, which I do not think is the correct driver for this model (3070?). Please explain the backlisting, compiling, and patch?

Any help would be GREATLY appreciated

-Ben

---

### Post by darkod on 2010-01-12
Sometimes just blacklisting rt2800usb will get it working, that's the easier option. In terminal open the blacklist file with:

sudo gedit /etc/modprobe.d/blacklist.conf

Add the line:
blacklist rt2800usb

Save and close the file. Open another file:

sudo gedit /etc/modules

Add the line:

rt2870sta

To make the RT2870 driver load on startup. Reboot and see if it worked.

If it didn't, download the patch for RT2870 from comment number #16 here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323)

Download the RT2870 driver for linux from Ralink website. It should be the driver 2009_0820 (from 20th August 2009). Extract the driver from the archive you downloaded, it should create folder 2009_0820_RT2870..... Put the patch also in that folder and execute it with:

patch -p1 < rt2870-2.6.31.patch

In the folder where the driver unpacked, find the file /os/linux/config.mk. Open it and change the WPA Supplicant lines to y (yes) like this:

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

Save and close config.mk. Go back few levels in the folder 2009_0820.... and execute:

sudo make
sudo make install

That compiled the driver to which you previously applied the patch and changed wpa supplicant to Yes. Now you should have your own rt2870sta driver. Reboot and see if it works.

I did this long ago and I had to google now and find info about the steps but I think I didn't miss anything.

---

### Post by qam47 on 2010-05-04
Hi,

I think i figured it out,

simply add the driver in the blacklist file,

like my driver was rt2870sta

just edit :
sudo gedit /etc/modprobe.d/blacklist.conf

and in the end **add** your driver
rt2870sta

dont do:
blacklist rt2870sta

---

### Post by FriarTuck57 on 2010-05-04
Hey  I am a total newb  and I am trying to get these same drivers working
any assistance is greatly appreciated
I have a Hawking HWUN3 USB NIC that uses this same chipset

---

### Post by chili555 on 2010-05-04
> **qam47 said:**
> Hi,

I think i figured it out,

simply add the driver in the blacklist file,

like my driver was rt2870sta

just edit :
sudo gedit /etc/modprobe.d/blacklist.conf

and in the end **add** your driver
rt2870sta

dont do:
blacklist rt2870staIncorrect. If you do:```
blacklist rt2870sta
```and then it *doesn't* work, then your device is using rt2870sta for its driver. Do you want to troubleshoot or leave well enough alone since it's working?

---

### Post by chili555 on 2010-05-04
> **FriarTuck57 said:**
> Hey  I am a total newb  and I am trying to get these same drivers working
any assistance is greatly appreciated
I have a Hawking HWUN3 USB NIC that uses this same chipsetPlease verify with:```
lsusb
```Is the device id the same?> 148f:3070If so, the device should work with the built-in rt2870sta driver.> $ modinfo rt2870sta | grep 3070
alias:          rt3070sta
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Blue"]148F[/COLOR]p[COLOR="Blue"]3070[/COLOR]d*dc*dsc*dp*ic*isc*ip*The trouble is it is also claimed by rt2800usb:> $ modinfo rt2800usb | grep 3070
alias:          usb:v[COLOR="Blue"]148F[/COLOR]p[COLOR="Blue"]3070[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
We shall prevent, or blacklist rt2800usb and it's dependencies from loading:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit.

Now, let's load rt2870sta on boot:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Reboot and let us know.

---

