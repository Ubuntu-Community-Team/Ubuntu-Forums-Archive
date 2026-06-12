---
title: "To anyone having problems with Netgear WG311v3 (PCI version)"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by bpoteet on 2009-04-25
After reading through these forums it seems like I have experienced every set of problems mentioned with this particular card: driver not working, can't connect to WPA networks, etc. What finally did the trick for me was not worrying about Netgear's driver. I found a driver to match the chipset, and voila, everything is fine. If your chipset is listed as:

```
$lspci

02:03.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03

```

...then you should be able to use the following driver with ndiswrapper:

[http://drivers.softpedia.com/progDownload/Marvell-Libertas-MRV-8335-802-11b-g-Wireless-Driver-3213-Download-33894.html](http://drivers.softpedia.com/progDownload/Marvell-Libertas-MRV-8335-802-11b-g-Wireless-Driver-3213-Download-33894.html)

Just extract the files using 7zip or another similar utility and install the appropriate .inf with ndiswrapper. Everything I have tried as far as connection type works with this driver. I have only tested this with a 32 bit install; I  do not know if there is an equivalent 64 bit driver that will work.

Hopefully this may help alleviate some of the headaches I know can come with trying to use this particular card. :)

---

### Post by jtmedin on 2009-05-26
i must be failing to get the right link. All the downloads want is $'s & they will check the pc i am on. I dont connect with the failing pc & what good does it do to check another pc? :-(.

---

### Post by jtmedin on 2009-05-26
See my previous reply, could u email me the driver from Marvell? TIA

---

### Post by jtmedin on 2009-05-28
Unable to locate driver following link. HELP! TIA

---

### Post by bpoteet on 2009-06-03
Try this:

[http://download.softpedia.ro/dl/8ab450f68cc1b1d8e92d901fd79ae36e/4a26f235/300033894/drivers/NETWORK/8335_3.2.1.3.exe](http://download.softpedia.ro/dl/8ab450f68cc1b1d8e92d901fd79ae36e/4a26f235/300033894/drivers/NETWORK/8335_3.2.1.3.exe)

If that doesn't work, then on my first link, hit the link that is titled "Softpedia Mirror RO".

Thanks,

Brian

---

### Post by jtmedin on 2009-06-04
Ok got it & thanks. Guess i get old too quick & smart too late :-)

---

### Post by jtmedin on 2009-06-05
Spent a lot of time without sucess & then relized i have a 64 bit machine & ubuntu(64). Think that is my problem :-(.

---

### Post by jtmedin on 2009-06-05
OK color me confused. I do have a 64 bit machine but installed ubuntu 32bit.
Gave up & shut down then tried one more time. When i rebooted vola the wireless was working. Go figure & thanks for all ur patients with me :D.

---

### Post by rpi+ on 2009-06-20
To bpoteet:

Your posting helped me to get things running immediately! :D

[SIZE=2]Thanks a lot! [/SIZE]

ubuntu 9.04 jaunty ;  netgear wg311v3 with chipset marvell 88w8335 ; WPA WPA-PSK

With ubuntu 8.10 intrepid everything worked (of course with the help of ndiswrapper and netgear driver files),
but with ubuntu 9.04 jaunty on the same machine i spent many hours and  i had no success.

Following your link, i downloaded the driver file 8335_3.2.1.3.exe and I used the Windows 2000 driver files with ndiswrapper and everything worked after one reboot.

rpi.

> **bpoteet said:**
> After reading through these forums it seems like I have experienced every set of problems mentioned with this particular card: driver not working, can't connect to WPA networks, etc. What finally did the trick for me was not worrying about Netgear's driver. I found a driver to match the chipset, and voila, everything is fine. If your chipset is listed as:

```
$lspci

02:03.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03

```...then you should be able to use the following driver with ndiswrapper:

[http://drivers.softpedia.com/progDownload/Marvell-Libertas-MRV-8335-802-11b-g-Wireless-Driver-3213-Download-33894.html](http://drivers.softpedia.com/progDownload/Marvell-Libertas-MRV-8335-802-11b-g-Wireless-Driver-3213-Download-33894.html)

Just extract the files using 7zip or another similar utility and install the appropriate .inf with ndiswrapper. Everything I have tried as far as connection type works with this driver. I have only tested this with a 32 bit install; I  do not know if there is an equivalent 64 bit driver that will work.

Hopefully this may help alleviate some of the headaches I know can come with trying to use this particular card. :)

---

### Post by FNM on 2009-06-22
For anyone using 64-bit Ubuntu, there is a 64-bit Windows driver that works with ndiswrapper available at 

[http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=](http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=)

just load the driver, modprobe ndiswrapper, and the GNOME NetworkManager applet should come to life.

---

### Post by jagtesh on 2009-07-27
Thanks FNM!

Gonna give the 64bit driver a shot. Like jtmedin, I'd lost all hopes and surrendered to the x86 version. My fingers are crossed with this one. Will give you guys a shout if it does work indeed!

---

### Post by Floyd770 on 2009-09-12
bpeteet,

Thank you so much for this.  I've been searching for a couple days, trying unsuccesfully trying to get two of these Marvell cards working.

Most of the posts here suggest using the wg311v3 driver for the Marvell 88w8335 chipset.

I tried that, and was able to connect only to an unsecured network, which if my neighbors knew, they probably wouldn't like.

Other people have suggested using Wicd.  I tried this as well, and only got the same results.

After I found your post, I thought I'd give this driver a try, and Voila!  It works great, with wpa2!

So, just for reinforcement, and my kudos to you, I'll post my entire process, starting with having the wg311v3 driver installed, and Wicd, in case this helps others.  You should already have ndiswrapper-common and ndiswrapper-utils installed at this point, if not, there are lots of great how-to's on ndiswrapper.  

I should also point out, that I'm using Jaunty

I'm still pretty new to linux, and learning as I go, though I'll admit, for me, this was a pretty big breakthrough.  I'll try to make this as simple as possible.

--------------------------------------------------------------------------
Download the Marvell drivers from here 
[http://drivers.softpedia.com/progDownload/Marvell-Libertas-MRV-8335-802-11b-g-Wireless-Driver-3213-Download-33894.html](http://drivers.softpedia.com/progDownload/Marvell-Libertas-MRV-8335-802-11b-g-Wireless-Driver-3213-Download-33894.html)

I used the Windows2000 drivers from that set.  They seem to work great.

Copy the Windows 2000 folder from that archive into your /home directory.

Rename the Windows 2000 folder to Windows2000 (no spaces, I can't seem to navigate into a folder with spaces in terminal for some reason, probably basic, I know, but this is my workaround for now)

Inside that Windows2000 folder there should be 4 files.  Leave all 4 of them there.  The files should be:
mrc8335.cat - 8.3k
mrv8335.inf - 22k
MRV8335.sys - 274k
MRV8335XP.sys - 274k

This sort of threw me for a loop here.  In many threads, people stress having only 1 .sys file in the folder you are installing the .inf from.  I tried moving the file MRV8335XP.sys file somewhere else, and when I installed mrv8335.inf with ndiswrapper, I got an error.  So, I moved MRV8335XP.sys back, and it worked fine.


**If you have _NOT[U] installed wicd yet, then network manager should still be running._[/U]**

Open a terminal window
Type:
```
ndiswrapper -l
```
This will list any installed drivers.  If you've already installed the wg311v3 driver, it should be listed, in addition, on the last line of output, should list this

device (11AB:1FAA) present

This is your PCI Wireless card, if installed correctly.

In the teminal window again,
Type:
```
cd /etc/ndiswrapper
```

This will take you to the /etc/ndiswrapper directory where the current installed driver lives.

In Terminal,
Type:
```
ls
```

This should list one file, it should be 'wg311v3' if that is the current driver you have installed.  If you have a different driver installed, it will be different.

In terminal
Type:
```
sudo ndiswrapper -e wg311v3
``` 

This uninstalls the current driver.

In terminal
Type:
```
ndiswrapper -l
```

This command tells ndiswrapper to list any installed drivers.  It should have no output at this point.

In terminal
Type:
```
cd /home/(your username)/Windows2000
```

Your username should be just that, your username, this takes you to the directory you copied the Marvell drivers into.  Don't forget, directories are case sensitive.

In Terminal
Type:
```
ls
```

It should output these 4 files.

mrv8335.cat  mrv8335.inf  MRV8335.sys  MRV8335XP.sys

Ok, now we're ready to install the new driver.

In terminal
Type:
```
sudo ndiswrapper -i mrv8335.inf
```

It should output 'installing' then return to prompt.

To make sure it installed, 

In terminal
Type:
```
ndiswrapper -l
```

Again, this lists installed drivers.  It should output something like this.

mrv8335 : driver installed
	device (11AB:1FAA) present

Almost there!

To be honest, I don't yet fully understand what the following commands do, (I'm still learning)  but from what I gather, it ensures that the driver module will be loaded each time at boot.  

In Terminal
Type:
```
sudo modprobe ndiswrapper
```

In terminal
Type:
```
sudo ndiswrapper -m
```

This supposedly updates a config file to keep the current driver settings.

Again, I'm not sure exactly what that does, but I've read this in many threads now that it should keep the settings saved.

Ok, Now if Network Manager hasn't already started searching for networks and trying to connect, then click on the Network Manager icon in the tray and connect!!!

------------------------------------------------------------------------

**If you have wicd installed**

You will need to get Network Manager installed.  wicd will likely work given you are now using the correct drivers, but I haven't tried it yet, I'm just happy to have my wifi connection back.  I'll try wicd again I'm sure, but for now, this works.

There are lots of threads about how to install Network Manager without a connection.

-------------------------------------------------------------------------

Good luck!  I'm sorry for the lack of technical details, but I figured I'd write this out as simply as possible for those like myself, who are just getting started.  

If anyone has any insight or wants to add exactly what modprobe does as I'm not sure I'm using it right.  When I reboot, I have to open a terminal and run 'sudo modprobe ndiswrapper' to get my wireless card turned on again.  Surely there is a better way to do this.

-Floyd

---

### Post by Ozzman on 2009-12-15
Thanks guys, you just saved me from a huge headache

---

### Post by iSephy on 2009-12-21
Oh. My. God. Thank you so much! :D I have been looking for this for about 3 days, and-- being close to Christmas-- I haven't had time to REALLY look at this stuff. When I first saw this, I forgot to install Wine, so I had an immense headache, then realized that I needed to install Wine! xD Once I installed Wine, everything ran smooth! This was an awesome guide! I reiterate, thank you so much! :D

---

### Post by iSephy on 2009-12-22
Um... When I restarted, the drivers didn't stay... D:

---

### Post by Vietchia on 2009-12-25
To get ndiswrapper to start on boot, after you "modprobe ndiswrapper", as root,
```
ndiswrapper -mi
```

---

### Post by vroberts on 2010-01-01
> **rpi+ said:**
> To bpoteet:

8335_3.2.1.3.exe and I used the Windows 2000 driver files with ndiswrapper and everything worked after one reboot.

rpi.

How do I extract the driver from a Windows EXE file on Linux?  7Zip has been suggested but it does not appear to work with EXE files.

---

### Post by vroberts on 2010-01-01
> **vroberts said:**
> How do I extract the driver from a Windows EXE file on Linux?  7Zip has been suggested but it does not appear to work with EXE files.

OK - I just figured it out.  I renamed the EXE to ZIP and then just used the gnome file manager extract tool.

---

### Post by kidambi502002 on 2010-04-20
Many thanks to Floyd770 for the detailed instructions. I am happy I could get connected to Inet in Ubuntu 9.10 with my PCI netgear wifi.  I was struggling to get info on this.  I was so far using usb pen drive belkin which had no problem connecting to inet.  thanks again.

---

