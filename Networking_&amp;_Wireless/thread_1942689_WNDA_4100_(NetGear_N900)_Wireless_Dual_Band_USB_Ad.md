---
title: "WNDA 4100 (NetGear N900) Wireless Dual Band USB Adapter"
date: 2012-03-18
forum: Networking &amp; Wireless
---

### Post by Immortal Nexus on 2012-03-18
Greetings all. :-)

This is my very first post in these forums. I installed Ubuntu 11.10 about a week ago, and I have to say that I am utterly in love with Linux. I learn and adapt very quickly, and having reached my breaking point of tolerance with Windows (in any version), I finally took the plunge into the Linux world. I've spent every free moment since install exploring and familiarizing myself with this amazing OS. I can say with absolute definitiveness now that I will NEVER go back to Winblows.

Having said that, there is one piece of hardware that Ubuntu did not detect, and presently remains useless : My NetGear N900 Dual Band Wireless Adapter. I've been scourering forums and websites looking for a means of getting this piece of hardware working with 11.10, to no avail. I've tried fake installing the drivers via Wine (actually I even downloaded the source code for Wine 1.3 and modified it for better USB detection, complied it, then installed it, without success), and even installing on another computer, then copying the files, then using Windows Wireless Drivers (Ndiswrapper) to find the INF file to make use of the drivers, without success. No matter what I do, this adapter is not able to be utilized.

The adapter, even though it cannot be used, is indeed being detected by Ubuntu, as the following info verifies: 

lsusb:

Bus 003 Device 002: ID 0846:9012 NetGear, Inc.

It is a Ralink-based chipset.

If anyone happens to know if there is any possible way of getting this adapter to function under Ubuntu 11.10, I'd be ridiculously grateful if they could point me in the right direction. If there is not yet support for this adapter, is there a way to request support somewhere?

Thanks much for any suggestions or advice.

---

### Post by praseodym on 2012-03-18
Hi,

AFAIK there is no Linux driver there for this device. See here:

[http://www.wikidevi.com/wiki/Netgear_WNDA4100](http://www.wikidevi.com/wiki/Netgear_WNDA4100)

Two possibilities:
[LIST=1]
[*]Ask Ralink, which of there drivers may work, and compile it by hand (we will help you ;-) )

[*]Try the windows driver with ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[/LIST]
Any driver disk? Something on it looking like "Linux"?

---

### Post by Immortal Nexus on 2012-03-18
> **praseodym said:**
> Hi,

AFAIK there is no Linux driver there for this device. See here:

[http://www.wikidevi.com/wiki/Netgear_WNDA4100](http://www.wikidevi.com/wiki/Netgear_WNDA4100)

Two possibilities:
[LIST=1]
[*]Ask Ralink, which of there drivers may work, and compile it by hand (we will help you ;-) )

[*]Try the windows driver with ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[/LIST]
Any driver disk? Something on it looking like "Linux"?

Thanks for the reply. I did already try Ndiswrapper with the Windows drivers, without success. So, if I were to go about compiling my own drivers, how might I begin this task? It's interesting...NetGear has no Linux support, yet Ralink does have a tar.bz2 file for Linux to compile. I will certainly do my own homework on how to compile these drivers, but any assistance would be immensely appreciated.

---

### Post by praseodym on 2012-03-18
In 11.10 you need to copy this file:

```
sudo cp /etc/modules.conf /etc/modprobe.d/ndiswrapper.conf
```
Check:

```
ndiswrapper -l
dmesg | grep ndis
iwconfig
lsmod
```

---

### Post by Immortal Nexus on 2012-03-18
> **praseodym said:**
> In 11.10 you need to copy this file:

```
sudo cp /etc/modules.conf /etc/modprobe.d/ndiswrapper.conf
```
Check:

```
ndiswrapper -l
dmesg | grep ndis
iwconfig
lsmod
```

I've pretty much set it into my head at the moment to build Linux native drivers from source provided by Ralink, but I'm feeling a bit in over my head at the moment, as I need to set variables that I don't know enough about yet to set properly. I've attached the readme file for compiling the source. I've been trying to follow instructions for compiling drivers for another USB adapter that also uses a Ralink chipset, but when in the driver source directory I'm unable to ./configure or sudo make. I'm determined to do this...lol.

---

### Post by Immortal Nexus on 2012-03-18
If this helps at all (to see the structure and content of the driver root directory), here is the tarball from Ralink's site for this chipset.

---

### Post by Immortal Nexus on 2012-03-18
OK, I've been reading hordes of posts and experimenting. I ran checkinstall in the terminal from the driver root directory, and I got further than I had in previous attempts, but had an error at the end. Here is the output:

```
Installing with make install...

========================= Installation results ===========================
make -C /home/tydynrain/Desktop/Ralink/Drivers/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/tydynrain/Desktop/Ralink/Drivers/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/tydynrain/Desktop/Ralink/Drivers/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/
install: cannot stat `rt2870sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/tydynrain/Desktop/Ralink/Drivers/os/linux'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.

```

So the rt2870sta.ko module was not found, or could not be created, and hence not installed properly. Any ideas?

---

### Post by Clay85 on 2012-05-01
I also have this device and I would love for it to work. Any progress?

---

### Post by chili555 on 2012-05-01
I have a plan! It is untested because I don't have the same device. I also have no idea if it will work at N speeds or even work at all. If you'd like to proceed, please verify that you have the same device:```
lsusb
```If so, hook up the ethernet temporarily and get the file RT5572USB from here: [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501) 

We also need to install the compiling tools:```
sudo apt-get install linux-headers-generic build-essential
```Of course, you could buy any number of inexpensive well-supported devices as well.

---

### Post by mookiemu on 2012-07-26
I have this device as well and I've trying to compile the same driver but to no avail. Modprobe -l shows that the driver is installed, but that hasn't helped me.
I would love to get this working, has anyone had any luck with this?

I know there are other supported devices out there, but I haven't found any other dual band 450mps usb adapters that work either.

---

### Post by chili555 on 2012-07-26
> **mookiemu said:**
> I have this device as well and I've trying to compile the same driver but to no avail. Modprobe -l shows that the driver is installed, but that hasn't helped me.
I would love to get this working, has anyone had any luck with this?

I know there are other supported devices out there, but I haven't found any other dual band 450mps usb adapters that work either.Do you have the same device?```
lsusb
```Is the driver you compiled called rt5572sta? Please show us:```
lsmod | grep rt5
dmesg | grep rt5
```Thanks.

---

### Post by lkbrow1 on 2012-07-29
I was able to compile and install the driver.  But I still have no functionality.
I did a [user]>make
[user]>su
>make install

driver appears as a ra0 under ifconfig.

---

### Post by praseodym on 2012-07-29
Now remove your current profile and create a new one. Check then:

```
iwconfig
rfkill list
lsmod
dmesg | grep rt5
```

---

### Post by chili555 on 2012-07-29
> **lkbrow1 said:**
> I was able to compile and install the driver.  But I still have no functionality.
I did a [user]>make
[user]>su
>make install

driver appears as a ra0 under ifconfig.Did you make the changes mentioned in the README?> 3> In os/linux/config.mk 
	<snip>
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.If not, please do so and recompile.

---

### Post by eNiNjA on 2012-08-16
I purchased one of these today. I will post my results.

I honestly cannot remember the last time I had a hardware issue with linux, but this is the 2nd Netgear device in week that probably isn't going to work.

I wish my dog hadn't chewed up my alfa =/

---

### Post by ericosaurus on 2012-08-17
Any new info on this?  I'm trying to get it working too.  

I've compiled the package from Ralink just fine, and the module "rt3572sta" shows up when I do lsmod.

But it never shows up under 'ifconfig'

Any tips?

---

### Post by chili555 on 2012-08-17
> **ericosaurus said:**
> Any new info on this?  I'm trying to get it working too.  

I've compiled the package from Ralink just fine, and the module "rt3572sta" shows up when I do lsmod.

But it never shows up under 'ifconfig'

Any tips?Please post:```
lsusb
modinfo rt3572sta
```Thanks.

---

### Post by ericosaurus on 2012-08-17
Here's the lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0846:9012 NetGear, Inc. WNDA4100 N900 Wireless Dual Band USB Adapter
Bus 001 Device 003: ID 1058:1100 Western Digital Technologies, Inc.
Bus 001 Device 008: ID 1058:0748 Western Digital Technologies, Inc.
```

modinfo rt3572sta:
```
filename:       /lib/modules/3.2.0-29-generic/kernel/drivers/net/wireless/rt3572sta.ko
license:        GPL
version:        2.5.0.0
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     D7F6D97B756AC2B0CFC20A9
alias:          usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:
vermagic:       3.2.0-29-generic SMP mod_unload modversions
parm:           mac:rt28xx: wireless mac addr (charp)
```

I'm not sure why it says RT2870 at the top, the Makefile says Chipset = 3572.

Maybe there's another place I need to set it to 3572 before compiling?

---

### Post by chili555 on 2012-08-17
Ralink rewrites a lot of their USB drivers using the RT2870 driver as a template. Its mention here is meaningless.

The reason I asked for modinfo was so you and I could look in the alias fields for your device, xx:9012. I don't see it. That's because rt357[COLOR="Red"]2[/COLOR]sta is not correct for your device. Please see: [http://www.wikidevi.com/wiki/Netgear_WNDA4100](http://www.wikidevi.com/wiki/Netgear_WNDA4100)> Chip 1: Ralink RT357[COLOR="Red"]**3**[/COLOR] Also please see here: [http://ubuntuforums.org/showthread.php?t=1986992&highlight=3573&page=2](http://ubuntuforums.org/showthread.php?t=1986992&highlight=3573&page=2)

Your device is also *not* mentioned in the files for rt3573sta, so you'll need to follow the same process as I outlined in post #13:```
#endif /* RT35xx */
#ifdef RT3573
	{USB_DEVICE(0x148F,0x3573)}, /* Ralink 3573 */
	{USB_DEVICE(0x7392,0x7733)}, /* Edimax */
	[COLOR="Red"]{USB_DEVICE(0x0846,0x9012)}, /* Netgear */[/COLOR]
	{USB_DEVICE(0x0B05,0x17AD)}, /*ASUS */
#endif /* RT3573 */
	{ }/* Terminating entry */
```It may or may not work; if not, we'll try the rt5572sta package.

Please post back if you need more detailed instructions.

---

### Post by ericosaurus on 2012-08-17
That is fantastic, I got the 3573 driver and added the line you mentioned and it's up now!  

But, it isn't connecting to the router.  It gets a Mac address for the AP, but never gets an ip address.  Is this probably an authentication problem?

I'm using WPA2PSK security mode in the rt2870sta.dat configuration file, should I be using WPA2 + wpa supplicant instead?  How do I know when to use wpa supplicant?

Thanks so much for your help

---

### Post by chili555 on 2012-08-17
> **ericosaurus said:**
> That is fantastic, I got the 3573 driver and added the line you mentioned and it's up now!  

But, it isn't connecting to the router.  It gets a Mac address for the AP, but never gets an ip address.  Is this probably an authentication problem?

I'm using WPA2PSK security mode in the rt2870sta.dat configuration file, should I be using WPA2 + wpa supplicant instead?  How do I know when to use wpa supplicant?

Thanks so much for your helpDid you make this change in config.mk?> 3> In os/linux/config.mk
<snip>
** Build for being controlled by NetworkManager or wpa_supplicant wext functions
Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. If not, please do and recompile:```
sudo su
make clean
make
make install
modprobe -r rt3573sta
modprobe rt3573sta
exit
```

---

### Post by ericosaurus on 2012-08-17
Yes, I had both of those set to "y".

That means I don't need wpa_supplicant, correct?

---

### Post by chili555 on 2012-08-18
You only 'need' wpa_supplicant if you intend to connect to an encrypted network. Ihope and assume yours is. Why do you ask, have you manipulated wpa_supplicant settings in some way?

Are there any informative messages here?```
dmesg | grep -i rt2
dmesg | grep -e rt5 -e wlan
```

---

### Post by ericosaurus on 2012-08-18
I have success!  

I didn't realize that the wpa_supplicant was required always, that flag that I set to yes that said "HAS_NATIVE_WPA_SUPPLICANT_SUPPORT" made me think it was included in the something native to the OS.

Anyways, I was looking over the documentation from ralink carefully and saw the line giving the command to connect using wpa_supplicant, and that worked perfectly.

Sorry to have hijacked the thread, but hopefully my experience can help the OP too.

thanks very much chili!

---

### Post by eNiNjA on 2012-08-18
Yep, can confirm this works.

Thanks Chili!

---

### Post by b00n utnubu on 2012-08-26
Today has been filled with a whole spectrum of emotions for me in regards to my switching from Windows 7 to Ubuntu 12.04...

First was excitement, as I was excited to get off the corporate OS bandwagon...

Then came the nerves, as I had no clue how to use the command line (which is obviously a necessity)

Then came the frustration, as I couldn't get my wireless adapter (same as OP) to work

Then I found this thread and the extremely helpful answers by [chili555]("http://ubuntuforums.org/member.php?u=35909") and my emotions did a complete 180!

I now have my Netgear N900 WNDA4100 wireless adapter working perfectly in Ubuntu 12.04, and I'm a complete n00b! lol

Thank you very much [chili555]("http://ubuntuforums.org/member.php?u=35909")!!!

---

### Post by chili555 on 2012-08-26
Glad it's working! Have fun!

---

### Post by cecilieaux on 2012-09-04
> **chili555 said:**
> Glad it's working! Have fun!
I've gone through this and can't find a clear list of steps to get to where b00n utnubu arrived. I there any way you could summarize what was done, so I could do it?

---

### Post by chili555 on 2012-09-04
> **cecilieaux said:**
> I've gone through this and can't find a clear list of steps to get to where b00n utnubu arrived. I there any way you could summarize what was done, so I could do it?Before we proceed, let's verify what you have. Please run and post:```
lsusb
```

---

### Post by cecilieaux on 2012-09-07
I guess you're interested in the line

Bus 001 Device 004 0846:9012 NetGear, Inc.

Had to copy this on a Windows computer since I can't connect using my ubuntu 12.04 LTS.

---

### Post by chili555 on 2012-09-07
You will need to download and compile rt3573sta and make a few changes. Can you get a wired ethernet connection even temporarily? If not, we can still compile, but it will be a bit difficult. If you can hook up an ethernet cable and get a connection, open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential
```Go here [http://www.wikidevi.com/wiki/Netgear_WNDA4100](http://www.wikidevi.com/wiki/Netgear_WNDA4100) and download the package for rt3573sta. Get it to your desktop so we can find it. Right-click it and select Extract Here. Open the folder that appears called Linux and select the DPO version. Right-click it and select Extract Here. Now we will make some changes to it. Drill down to os/linux/config.mk. Open the file with a text editor and make these changes:> ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.In other words, change the =n to =y in those two lines. Proofread very carefully, save and close the text editor.

Open the file common/rtusb_dev_id.c with any text editor, such as gedit. Add a line as I've highlighted:```
#endif /* RT35xx */
#ifdef RT3573
	{USB_DEVICE(0x148F,0x3573)}, /* Ralink 3573 */
	{USB_DEVICE(0x7392,0x7733)}, /* Edimax */
	[COLOR="Red"]{USB_DEVICE(0x0846,0x9012)}, /* Netgear */[/COLOR]
	{USB_DEVICE(0x0B05,0x17AD)}, /*ASUS */
#endif /* RT3573 */
	{ }/* Terminating entry */
```All other lines before and after are unchanged. Punctuation, spelling, spacing, etc. are crucial so proofread very carefully, save and close the text editor. 

Now we're ready to compile. Open a terminal and do:```
cd Desktop/Linux/DPO
```Press Tab and the remainder will fill in automagiaclly. Press Enter. Now do:```
sudo su
make
make install
modprobe rt3573sta
exit
```Is it working now? Are we there yet?

---

### Post by Superblock on 2012-09-07
Chilli,
   I just wanted to thank you for helping me out with this...
Thing works beautiful no problems connecting and 100 %
Signal Strength. Thanks for the help bro it is appreciated...

                                                              S

---

### Post by cecilieaux on 2012-09-08
Have the time and the computers to try this now. Will let you know. Sound like very complete instructions. If this works, and you already have several successes, this ought to be written into some kind of permanent how-to. I would be willing to help with that, although you seem to write very clearly yourself.

---

### Post by cecilieaux on 2012-09-08
Um, that was meant for chili555 ...

---

### Post by cecilieaux on 2012-09-08
Chili,
First stumble, I can't connect to ethernet (router too far ... in other room) with Ubuntu (installed on "immovable" desktop).

What now?

PS: how do you put taglines on your messages?

---

### Post by chili555 on 2012-09-08
Arrrgh! Post #6 here is a description of how to get the packages build-essential and linux-headers-generic: [http://ubuntuforums.org/showthread.php?t=2050126&highlight=build-essential](http://ubuntuforums.org/showthread.php?t=2050126&highlight=build-essential)

Obviously, when that description gets to compat-wireless for the driver alx, you need to veer off to Ralink for rt3573sta.

As you can see, it is a complex process and may take a couple of tries. As you can also see in post #9, the poster in the thread I linked did so successfully and we are all still friends!

Are you sure you can't borrow or buy a longer ethernet cable? This would be a five minute process if you could. I will be happy to help in any event.> PS: how do you put taglines on your messages? You can set them in your profile > Edit Signature.

---

### Post by cecilieaux on 2012-09-08
For some reason it didn't work.

I managed to download the package (sneaker net) and make the changes requested (the changes have already been made in the first file, not in the second).

[deleted dump]

---

### Post by cecilieaux on 2012-09-08
OK, I figured out there are typos and am fixing them.

---

### Post by cecilieaux on 2012-09-08
YAAYYYYYYYYYYYYYYY!!!!!!!!!!!!!!!!!!!!!!!!!!

I'm posting this from Ubuntu!!!!!!!!!!!

---

### Post by cecilieaux on 2012-09-08
Cried victory too soon ... an ubuntu update made the driver inoperable. This was not a major update, just from 

Ubuntu, with Linux 3.2.0-29-generic-pae

to

Ubuntu, with Linux 3.2.0-30-generic-pae

I've now rebooted with the old one and the connection is fine.

Solutions???

---

### Post by chili555 on 2012-09-08
Good work! When a newer kernel version, also known as linux-image, is installed by Update Manager, you'll need to compile this driver for the later kernel. Open a terminal and do:
```
cd Desktop/Linux/DPO

```
Press Tab and the remainder will fill in automagically. Press Enter. Now do:
```
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe rt3573sta
exit
```Please make a note of these instructions so you'll be ready.

---

### Post by chili555 on 2012-09-08
> **cecilieaux said:**
> Cried victory too soon ... an ubuntu update made the driver inoperable. This was not a major update, just from 

Ubuntu, with Linux 3.2.0-29-generic-pae

to

Ubuntu, with Linux 3.2.0-30-generic-pae

I've now rebooted with the old one and the connection is fine.

Solutions???Sure, see my next post.

---

### Post by cecilieaux on 2012-09-16
> **chili555 said:**
> Good work! When a newer kernel version, also known as linux-image, is installed by Update Manager, you'll need to compile this driver for the later kernel. Open a terminal and do:
```
cd Desktop/Linux/DPO

```
Press Tab and the remainder will fill in automagically. Press Enter. Now do:
```
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe rt3573sta
exit
```Please make a note of these instructions so you'll be ready.

I did this and it seemed to compile without errors, but I can't make a connection with the new kernel. I haver to reboot into the old kernel to connect.

---

### Post by chili555 on 2012-09-16
Booted into the new kernel, please run and post:```
sudo modprobe rt3573sta
dmesg | grep -e rt3 -e wlan
```Thanks.

---

### Post by cecilieaux on 2012-09-17
> **chili555 said:**
> Booted into the new kernel, please run and post:```
sudo modprobe rt3573sta
dmesg | grep -e rt3 -e wlan
```Thanks.

Here's the dump:

> cecilieaux@CM-Workstation:~$ sudo modprobe rt3573sta
[sudo] password for cecilieaux: 
cecilieaux@CM-Workstation:~$ dmesg | grep -e rt3 -e wlan
cecilieaux@CM-Workstation:~$ 


Am I correct in assuming nothing happened?

BTW, I'm going to bed, won't be able to make more progress until tomorrow night.

Thanks so much for your patience!

---

### Post by chili555 on 2012-09-17
Hmmm. Let's dig deeper. Please post:```
modinfo rt3573sta | head -n5
lsusb
sudo modprobe rt3573sta
dmesg | tail -n10
```

---

### Post by jstthe01 on 2012-09-19
Hello ALL!
I am also new to unbuntu, infact I just installed it today.:lolflag:w
I don't really think the command line thing will be a problem even though it is kinda intemidating.:-) Years ago I was a SysOp of a bbs but that was a really a long time ago (before the internet) lol. Does anyone know if the netgear WNDA4100 supports packet injection, if so thats also the usb adapter that I have and would like to make work with Ubuntu, if it does not support packet injection then I will just get another adapter that does. Can you tell me the best N adapter that works best with ubuntu that can supprt packet injection, thanks again in advance for any help. ps I know I will love the os ounce I get used to it but need some help getting started.

---

### Post by feardotcom on 2012-09-22
Ok, so i updated to 3.2.0-30-generic and my wifi adapter stopped working (yes i have the WDNA4100) and then i used my phone to tether to my wifi and did another update to 3.2.0-31-generic and i having the same problems as the other guy, still. 

```
root@chris-pc:/home/chris/Documents/WifiCard/DPO_RT3573_LinuxSTA_V2.5.0.0# sudo modprobe rt3573sta
root@chris-pc:/home/chris/Documents/WifiCard/DPO_RT3573_LinuxSTA_V2.5.0.0# dmesg | grep -e rt3 -e wlan
[   12.719341] usbcore: registered new interface driver rndis_wlan

``` and
```
root@chris-pc:/home/chris/Documents/WifiCard/DPO_RT3573_LinuxSTA_V2.5.0.0# modinfo rt3573sta | head -n5
filename:       /lib/modules/3.2.0-31-generic/kernel/drivers/net/wireless/rt3573sta.ko
version:        2.5.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
root@chris-pc:/home/chris/Documents/WifiCard/DPO_RT3573_LinuxSTA_V2.5.0.0# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bb4:0ffe High Tech Computer Corp. Desire HD (modem mode)
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 002: ID 046d:c043 Logitech, Inc. MX320/MX400 Laser Mouse
root@chris-pc:/home/chris/Documents/WifiCard/DPO_RT3573_LinuxSTA_V2.5.0.0# sudo modprobe rt3573sta
root@chris-pc:/home/chris/Documents/WifiCard/DPO_RT3573_LinuxSTA_V2.5.0.0# dmesg | tail -n10
[   14.388891] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input16
[   14.633951] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   14.633954] vesafb: scrolling: redraw
[   14.633956] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   14.638752] vesafb: framebuffer at 0xdd000000, mapped to 0xffffc90012280000, using 5120k, total 5120k
[   14.638922] Console: switching to colour frame buffer device 160x64
[   14.638943] fb0: VESA VGA frame buffer device
[   24.116438] usb0: no IPv6 routers present
[  197.744865] rtusb init rt2870 --->
[  197.744898] usbcore: registered new interface driver rt2870

```

Any ideas?

---

### Post by chili555 on 2012-09-22
> yes i have the WDNA4100Where in your *lsusb* do we see it? Please insert the device and try again:```
lsusb
sudo modprobe rt3573sta
dmesg | grep rt3
```

---

### Post by feardotcom on 2012-09-22
Thats the thing...it is inserted but the adapter doesn't have any of the lights on. I noticed when i compiled the drivers the first time that the lights on the adapter didn't come on till after the driver was compiled.

---

### Post by chili555 on 2012-09-22
> **feardotcom said:**
> Thats the thing...it is inserted but the adapter doesn't have any of the lights on. I noticed when i compiled the drivers the first time that the lights on the adapter didn't come on till after the driver was compiled.We don't see it here:> lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bb4:0ffe High Tech Computer Corp. Desire HD (modem mode)
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 002: ID 046d:c043 Logitech, Inc. MX320/MX400 Laser MouseI wonder if the device or the USB port is defective.

---

### Post by feardotcom on 2012-09-22
I noticed that too... but i've tried multiple usb ports and still nothing. maybe i'll try not using the extension cord it came with when i get home and see what happens. But, before i compiled the driver the first on kernel 3.2.0-29-generic i noticed the computer wasn't even recognizing the adapter was plugged in. After i compiled the driver on kernel 3.2.0-29 generic the adapter come right up and was recognized. I've checked the 2 files i had to modify and they are still what i changed them to from your instructions.

---

### Post by andydeforest on 2012-09-23
Does anyone have instructions installing the drivers without an internet connection? Would I be able to download the files and put them on my USB, than boot into Ubuntu and compile them?

---

### Post by chili555 on 2012-09-23
With or without a driver, it ought to appear in *lsusb*. Is there any recognition if you unplug the device and then run:```
sudo tail -f /var/log/syslog
```Plug it in. Any interesting messages?

Close out of *tail* with Ctrl+c.

---

### Post by feardotcom on 2012-09-23
@Chili: So when i got home from work this morning i unplugged the adapter from the extension cord that was plugged up to the back of the computer and then plugged the adapter into the front usb directly(without the extension cord) and it came right up and worked, so i unplugged from the front and plugged it back into the extension cord and it came right up and connected again. So weird, maybe a short in the extension cord, idk.

@Andy: If you have build essentials installed then yes you can install the drivers without the internet. The drivers just come in a zip file. If you dont have build essentials i think Chili added a link somewhere to get instructions on how to download it from a different computer.

---

### Post by cecilieaux on 2012-09-23
> **chili555 said:**
> Booted into the new kernel, please run and post:```
sudo modprobe rt3573sta
dmesg | grep -e rt3 -e wlan
```Thanks.

OK ... finally tried it and here's the output:

cecilieaux@CM-Workstation:~$ modinfo rt3573sta | head -n5
filename:       /lib/modules/3.2.0-30-generic-pae/kernel/drivers/net/wireless/rt3573sta.ko
version:        2.5.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
cecilieaux@CM-Workstation:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9012 NetGear, Inc. 
Bus 002 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 002 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
cecilieaux@CM-Workstation:~$ dmesg | tail -n10
[ 3565.436065] EDAC MC0: CE page 0x16cbe, offset 0xb00, grain 64, syndrome 0xc1, row 0, channel 1, label "DIMM B1": i82975x CE
[ 3566.436083] EDAC MC0: CE page 0x16ebe, offset 0xf00, grain 64, syndrome 0xc1, row 0, channel 1, label "DIMM B1": i82975x CE
[ 3567.436055] EDAC MC0: CE page 0x16cbe, offset 0xb00, grain 64, syndrome 0xc1, row 0, channel 1, label "DIMM B1": i82975x CE
[ 3568.436088] EDAC MC0: CE page 0x16cbe, offset 0xf00, grain 64, syndrome 0xc1, row 0, channel 1, label "DIMM B1": i82975x CE
[ 3569.436086] EDAC MC0: CE page 0x16cbe, offset 0xb80, grain 64, syndrome 0xc1, row 0, channel 1, label "DIMM B1": i82975x CE
[ 3571.436068] EDAC MC0: CE page 0x16cbe, offset 0xb80, grain 64, syndrome 0xc1, row 0, channel 1, label "DIMM B1": i82975x CE
[ 3572.436141] EDAC MC0: CE page 0x16cbe, offset 0xb00, grain 64, syndrome 0xc1, row 0, channel 1, label "DIMM B1": i82975x CE
[ 3573.436065] EDAC MC0: CE page 0x16cbe, offset 0xf00, grain 64, syndrome 0xc1, row 0, channel 1, label "DIMM B1": i82975x CE
[ 3574.440044] EDAC MC0: CE page 0x16cbe, offset 0xb80, grain 64, syndrome 0xc1, row 0, channel 1, label "DIMM B1": i82975x CE
[ 3575.440067] EDAC MC0: CE page 0x16ebe, offset 0xf00, grain 64, syndrome 0xc1, row 0, channel 1, label "DIMM B1": i82975x CE
cecilieaux@CM-Workstation:~$ 

Looks to me like it recognizes the gizmo. Why the eff doesn it work with it like 3.2.0-29-generic-pae, which I am writing to you from, does.

Cecilieaux

---

### Post by chili555 on 2012-09-23
I assume you made the changes here: [http://ubuntuforums.org/showpost.php?p=12179088&postcount=19](http://ubuntuforums.org/showpost.php?p=12179088&postcount=19)

I also assume you re-compiled for the later kernel as outlined here: [http://ubuntuforums.org/showpost.php?p=12226622&postcount=41](http://ubuntuforums.org/showpost.php?p=12226622&postcount=41)

Yes? No?

---

### Post by cecilieaux on 2012-09-24
> **chili555 said:**
> I assume you made the changes here: [http://ubuntuforums.org/showpost.php?p=12179088&postcount=19](http://ubuntuforums.org/showpost.php?p=12179088&postcount=19)

I also assume you re-compiled for the later kernel as outlined here: [http://ubuntuforums.org/showpost.php?p=12226622&postcount=41](http://ubuntuforums.org/showpost.php?p=12226622&postcount=41)

Yes? No?

The answer was No, but I am now connected via the new kernel, so I looked through and fixed what was wrong. 

I have two questions left and I&#314;l leave you alone with enormous gratitude for teaching me something that is still almost magic to me.

1. I am still confused about common/rtusb_dev_id.c. I had edited it before for the previous kernel (else it wouldn't have worked, I assume). But when I went to check, the device-specific line (in my case {USB_DEVICE(0x0846,0x9012)}, /* Netgear */) was not there. It somehow returns to the original?

2. In future, then, every time a new kernel is installed, I should, BEFORE recompiling

a) check the file 
Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/os/linux/config.mk to make sure HAS_WPA_SUPPLICANT= is set to y

b) Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/check common/rtusb_dev_id.c to make sure that everything is as indicated in [http://ubuntuforums.org/showpost.php?p=12179088&postcount=19](http://ubuntuforums.org/showpost.php?p=12179088&postcount=19) (msg #19 of this thread)

Then, if all is well I shoud recompile per d here: [http://ubuntuforums.org/showpost.php...2&postcount=41](http://ubuntuforums.org/showpost.php...2&postcount=41)  (msg #41 of this thread)

Anyway, that's what I did and it worked. Correct?

If this is correc, I'll put the instructions together in one "cheat sheet" file.

Again, thank you so very much!!!!

---

### Post by feardotcom on 2012-09-24
Yes chili, thank you very much, you turned our $60 paper weight back in a wifi adapter

---

### Post by cecilieaux on 2012-09-24
Here is my complete "cheat sheet." Attached.

[ATTACH]224599[/ATTACH]

---

### Post by chili555 on 2012-09-24
If you extracted the tar.gz and then made the changes in the extracted folder, then, no, it shouldn't revert.

If, on the other hand you went all the way back in the instructions to 'right-click, Extract Here' then you have extracted a virgin, if you will, copy. By the way, this is a handy capability when too many ill-considered changes have been made, you can (OK, I can, since I am usually the one to make ill-aadvised changes) get a new un-modified copy.> In future, then, every time a new kernel is installed, I should, BEFORE recompilingIt never hurts to check your work until you are confident.> Then, if all is well I shoud recompile per d here: [http://ubuntuforums.org/showpost.php...2&postcount=41](http://ubuntuforums.org/showpost.php...2&postcount=41) (msg #41 of this thread)Exactly.

You might check the files after 'make clean'; we hope there is no weird reversion script that wipes out our changes.

I'm glad you are both working as expected!

---

### Post by feardotcom on 2012-09-26
So i've got everything set up and i've noticed that my connection will lag out about every 10-15 minutes. I was playing urbanterror and about every 10 mins or so it would flash "connection interruption" for about a minute, and i noticed on youtube and hulu the same thing happens, the video will stop and/or skip for about a minute at random times. Is there a way to fix this?

---

### Post by cecilieaux on 2012-10-01
Just to report that I have just tried the cheat sheet live on a new linux image (had to) and it worked perfectly again. There does not appear to be any weird reversion script at work. (I must have re-extracted a virgin file when I last encountered that problem.)

Phew! I was dreading this. 

Any reason I could not write the commands into a bash script?

---

### Post by chili555 on 2012-10-01
> **cecilieaux said:**
> 

Any reason I could not write the commands into a bash script?None whatever. You might also share the script here for the searchers' benefit.

---

### Post by schms on 2012-10-16
@chhili555

Thank you very much for your solution. It worked out of the box for
the following configuration as well:

Ubuntu, 12.10, quantal

Netgear, WNDA4100, Ralink RT3573, driver: rt3573sta
kernel: 3.5.0-17-generic, x86-64

---

### Post by cecilieaux on 2012-10-16
> **chili555 said:**
> None whatever. You might also share the script here for the searchers' benefit.

OK, so I wrote a script and it fails. But I go back to manually inputting at the terminal as root and it works. I'm very new to script writing, as it will show.

I did something wrong ... what?

Here is my initial script:

> 
#!/bin/sh
cd Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/
sudo su 
make clean
make
make install
modprobe rt3573sta
exit


I realized that since I was changing user, it halted at sudo su. So then I did this, which I attempted to run after changing to the right directory and switching to root:

> 
#!/bin/sh
make clean
make
make install
modprobe rt3573sta
exit


It got a FATAL ERROR that scared the living LinuxCurses out of me. Then I went manual.

Help this idiot newbie, please!

---

### Post by chili555 on 2012-10-16
I'm not a script guy either, but if you don't 'sudo su' you needn't exit. Also, you forgot to  cd Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/. I am not sure how to get around the 'sudo su' step.

---

### Post by jbrenner on 2012-11-02
I'd like to add my thanks to chili555 as well. As far as a script is concerned, just run it as su.
Edit the script and add #!/bin/bash as the first line.

Now make the script executable; chmod 777 "script name"
Last, execute the script; sudo "script name"
If the script is in the current directory then; sudo "./script name"

---

### Post by cecilieaux on 2012-11-03
Thanks, jbrenner!

Will try.

---

### Post by iRy on 2012-11-05
Hi @ all,
I was able to get my WNDA4100 to run through this thread!!! Thank you very much chili555!!

Now I've got a really weird problem:
Sometimes, spontaneously my whole system freezes :( It only happens if I use the stick. The time varies too. Maybe somebody has an idea??

Here are my essential stats:
```
adam@iry:~$ uname -a
Linux iry 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```**LSUSB-OUTPUT**
```
adam@iry:~$ lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0846:9012 NetGear, Inc. WNDA4100 802.11abgn 3x3:3 [Ralink RT3573]
Bus 001 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
```**DMESG-OUTPUT**
```
adam@iry:~$ dmesg
[    1.254205] usb 1-1.2: >new high-speed USB device number 3 using ehci_hcd
[    1.321893] Refined TSC clocksource calibration: 3058.999 MHz.
[    1.321899] Switching to clocksource tsc
[    1.361378] usb 1-1.2: >New USB device found, idVendor=0846, idProduct=9012
[    1.361383] usb 1-1.2: >New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.361386] usb 1-1.2: >Product: WNDA4100
[    1.361389] usb 1-1.2: >Manufacturer: NETGEAR
[    1.361391] usb 1-1.2: >SerialNumber: 1.0
[   13.628644] rtusb init rt2870 --->
[   13.628715] 
[   13.628715] 
[   13.628715] === pAd = ffffc90011a06000, size = 593840 ===
[   13.628715] 
[   13.628813] <-- RTMPAllocTxRxRingMemory, Status=0
[   13.628859] <-- RTMPAllocAdapterBlock, Status=0
[   13.629153] (Reassign Efuse for 3x7x/3x9x/53xx) Size=0x3c [3c0-3fb] 
[   13.629575] usbcore: registered new interface driver rt2870
[   17.851763] RTMP_TimerListAdd: add timer obj ffffc90011a4f6e0!
[   17.851767] RTMP_TimerListAdd: add timer obj ffffc90011a4f758!
[   17.851768] RTMP_TimerListAdd: add timer obj ffffc90011a4f7d0!
[   17.851769] RTMP_TimerListAdd: add timer obj ffffc90011a4f668!
[   17.851771] RTMP_TimerListAdd: add timer obj ffffc90011a4f500!
[   17.851772] RTMP_TimerListAdd: add timer obj ffffc90011a4f578!
[   17.851773] RTMP_TimerListAdd: add timer obj ffffc90011a199e8!
[   17.851774] RTMP_TimerListAdd: add timer obj ffffc90011a08858!
[   17.851775] RTMP_TimerListAdd: add timer obj ffffc90011a088d8!
[   17.851776] RTMP_TimerListAdd: add timer obj ffffc90011a19b78!
[   17.851777] RTMP_TimerListAdd: add timer obj ffffc90011a198f8!
[   17.851779] RTMP_TimerListAdd: add timer obj ffffc90011a19af8!
[   17.853286] -->RTUSBVenderReset
[   17.853417] <--RTUSBVenderReset
[   18.094723] init: plymouth-stop pre-start process (1388) terminated with status 1
[   18.101107] Key1Str is Invalid key length(0) or Type(0)
[   18.101117] Key2Str is Invalid key length(0) or Type(0)
[   18.101127] Key3Str is Invalid key length(0) or Type(0)
[   18.101137] Key4Str is Invalid key length(0) or Type(0)
[   18.101321] 1. Phy Mode = 5
[   18.101322] 2. Phy Mode = 5
[   18.101323] NVM is Efuse and its size =3c[3c0-3fb] 
[   18.231856] 3. Phy Mode = 5
[   18.235445] \x1b[mAntCfgInit: primary/secondary ant 0/1
[   18.235445] \x1b[mRTMPSetPhyMode: channel is out of range, use first channel=1 
[   18.297176] MCS Set = ff ff ff 00 01
[   18.308285] <==== rt28xx_init, Status=0
[   18.309774] 0x1300 = 00064300
[   18.378210] ERROR!!! RTMPSetTimer failed, Halt in Progress!
[   18.825996] RTMP_TimerListAdd: add timer obj ffffc90011a4f6e0!
[   18.826000] RTMP_TimerListAdd: add timer obj ffffc90011a4f758!
[   18.826001] RTMP_TimerListAdd: add timer obj ffffc90011a4f7d0!
[   18.826002] RTMP_TimerListAdd: add timer obj ffffc90011a4f668!
[   18.826004] RTMP_TimerListAdd: add timer obj ffffc90011a4f500!
[   18.826005] RTMP_TimerListAdd: add timer obj ffffc90011a4f578!
[   18.826006] RTMP_TimerListAdd: add timer obj ffffc90011a199e8!
[   18.826007] RTMP_TimerListAdd: add timer obj ffffc90011a08858!
[   18.826008] RTMP_TimerListAdd: add timer obj ffffc90011a088d8!
[   18.826008] RTMP_TimerListAdd: add timer obj ffffc90011a19b78!
[   18.826010] RTMP_TimerListAdd: add timer obj ffffc90011a198f8!
[   18.826011] RTMP_TimerListAdd: add timer obj ffffc90011a19af8!
[   18.827454] -->RTUSBVenderReset
[   18.827583] <--RTUSBVenderReset
[   19.059090] Key1Str is Invalid key length(0) or Type(0)
[   19.059105] Key2Str is Invalid key length(0) or Type(0)
[   19.059121] Key3Str is Invalid key length(0) or Type(0)
[   19.059138] Key4Str is Invalid key length(0) or Type(0)
[   19.059326] 1. Phy Mode = 5
[   19.059328] 2. Phy Mode = 5
[   19.059329] NVM is Efuse and its size =3c[3c0-3fb] 
[   19.204262] 3. Phy Mode = 5
[   19.207773] \x1b[mAntCfgInit: primary/secondary ant 0/1
[   19.207773] \x1b[mRTMPSetPhyMode: channel is out of range, use first channel=1 
[   19.272362] MCS Set = ff ff ff 00 01
[   19.283485] <==== rt28xx_init, Status=0
[   19.285099] 0x1300 = 00064300
[   19.476591] r8169 0000:02:00.0: >eth0: link down
[   19.477301] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.477614] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.823635] /usr/src/DPO_RT3573_LinuxSTA_V2.5.0.0/os/linux/../../common/cmm_asic.c:2583 assert KeyIdx < 4failed
[   19.824228] /usr/src/DPO_RT3573_LinuxSTA_V2.5.0.0/os/linux/../../common/cmm_asic.c:2583 assert KeyIdx < 4failed
[   25.021347] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 534
[   51.825323] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 1085
[   57.630972] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 1348
[   57.631213] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=4)
[   58.916564] RTMP_TimerListAdd: add timer obj ffffc90011a8ab48!
[   60.171941] Rcv Wcid(1) AddBAReq
[   60.171946] Start Seq = 00000000
[   60.171949] RTMP_TimerListAdd: add timer obj ffffc90011a8f368!
[   60.189670] RTMP_TimerListAdd: add timer obj ffffc90011a8abd8!
[   89.698340] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 1083
[  131.923287] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 1348
[  188.136764] 33a, flush one!
[  188.368885] 33b, flush one!
[  191.975100] 36e, flush one!
[  192.093861] 384, flush one!
[  195.236765] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 1445
[  277.685143] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 1180
[  374.514621] DeQueueRunning[0]= TRUE!
[  380.282036] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 1150
[  499.923042] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 1182
[  618.735808] c40, flush one!
[  619.566027] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 1085
[  619.828214] Indicate_Legacy_Packet():flush reordering_timeout_mpdus! RxWI->Flags=128, pRxWI.TID=0, RxD->AMPDU=0!
[  739.225505] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 816
[  851.865517] Indicate_Legacy_Packet():flush reordering_timeout_mpdus! RxWI->Flags=128, pRxWI.TID=0, RxD->AMPDU=0!
[  851.865523] ecc, flush one!
[  855.850273] Indicate_Legacy_Packet():flush reordering_timeout_mpdus! RxWI->Flags=128, pRxWI.TID=0, RxD->AMPDU=0!
[  858.835864] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 887
[  970.183585] 2a, flush one!
[  976.197422] 8a, flush one!
[  976.446622] 8b, flush one!
[  979.380410] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 553
[  998.535007] DeQueueRunning[0]= TRUE!
[ 1098.884939] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 784
```**LSMOD-OUTPUT**
```
adam@iry:~$ lsmod
Module                  Size  Used by
rfcomm                 46619  0 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
bluetooth             209199  10 rfcomm,bnep
binfmt_misc            17500  1 
vesafb                 13797  1 
rt3573sta             716928  1 
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
microcode              22803  0 
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                95552  0 
serio_raw              13215  0 
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
wmi                    19070  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                4715211  169 
snd                    78734  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                17061  0 
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
joydev                 17457  0 
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_logitech           26585  0 
ff_memless             13013  1 hid_logitech
usbhid                 46947  1 hid_logitech
hid                   100366  2 hid_logitech,usbhid
r8169                  61650  0 
usb_storage            48838  0
```**MODINFO RT3573STA-OUTPUT**
```
adam@iry:~$ modinfo rt3573sta
filename:       /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/rt3573sta.ko
version:        2.5.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     8CF7EC9A573CBFE23D79153
alias:          usb:v0B05p17ADd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7733d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0764d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       3.5.0-17-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)
```

Thank you for your help

---

### Post by chili555 on 2012-11-06
> [   18.378210] ERROR!!! RTMPSetTimer failed, Halt in Progress!I am quite confident that this is the problem.

I compiled this package against my 3.5.xx kernel and it spits out many, perhaps dozens of warnings but no errors. When we compile from source code, the proof test is if it actually works. Obviously, in your case, it doesn't. I only have three suggestions.

* You might try the Windows XP driver and ndiswrapper.

* You might email the developers and ask them:> author:         Paul Lin <paul_lin@ralinktech.com>In a few cases, Ralink has sent out a revised package. If you get one, please share it with me so I can make it available in my Dropbox for others in the same circumstance.

* You might try Ubuntu 12.04 LTS that uses a 3.2.xx kernel.

I am sorry I don't have a better solution.

---

### Post by soratheultima on 2012-11-08
Hey Chili555 wanted to say thanks for helping me install the driver. I have one major issue though :/ whenever i use a web browser I get a kernel panic :( and the system is frozen(this is with any web browser) using that wireless device. (if i use Ethernet it wont happen). when i use applications that use the internet they sit and hang. i'm using Ubuntu 12.10 with the 3.5.0.18.?? (don't remember i think its .21) I have also tried this with kubuntu 12.10 and get the same result. i can't show any logs right now due to me being in college atm but i'll be able to later! :). (btw it did show lots of warnings while compiling the driver)

---

### Post by chili555 on 2012-11-08
> **soratheultima said:**
> Hey Chili555 wanted to say thanks for helping me install the driver. I have one major issue though :/ whenever i use a web browser I get a kernel panic :( and the system is frozen(this is with any web browser) using that wireless device. (if i use Ethernet it wont happen). when i use applications that use the internet they sit and hang. i'm using Ubuntu 12.10 with the 3.5.0.18.?? (don't remember i think its .21) I have also tried this with kubuntu 12.10 and get the same result. i can't show any logs right now due to me being in college atm but i'll be able to later! :). (btw it did show lots of warnings while compiling the driver)Please do show us your logs:```
dmesg | grep -i rt
```If you are getting the same errors as above, I'm afraid my solution is also the same as above.

---

### Post by soratheultima on 2012-11-08
> **chili555 said:**
> Please do show us your logs:```
dmesg | grep -i rt
```If you are getting the same errors as above, I'm afraid my solution is also the same as above.

yeah I'm getting the same error. I will try and install 12.04 later tonight and then try compiling the driver again

---

### Post by soratheultima on 2012-11-08
I get the same error on 12.04 with kernel 3.2.0-32 but The drivers actually work now and do not give me a kernel panic :) thanks again! :D

---

### Post by Sabel21210 on 2012-12-01
I realize this is a somewhat older thread but, I admittedly have no idea what i'm doing and this thread is what got my wireless adapter to work in the first place.

 Connecting works fine i can even use my choice of the 5g network or the normal one. It is the stability of the connection that is my problem. I never actually disconnect from the internet but my ping tends to spike pretty often. The main use of my PC is gaming..so connection stability is sort of a big deal for me. I was wondering if it could have anything to do with my driver set up?

---

### Post by chili555 on 2012-12-01
> **Sabel21210 said:**
> I realize this is a somewhat older thread but, I admittedly have no idea what i'm doing and this thread is what got my wireless adapter to work in the first place.

 Connecting works fine i can even use my choice of the 5g network or the normal one. It is the stability of the connection that is my problem. I never actually disconnect from the internet but my ping tends to spike pretty often. The main use of my PC is gaming..so connection stability is sort of a big deal for me. I was wondering if it could have anything to do with my driver set up?Please show us your logs:```
dmesg | grep -i rt
cat /var/log/syslog | grep etwork | tail -n20
```Thanks.

---

### Post by Sabel21210 on 2012-12-01
This is what i got for the first one

```
[39877.144201] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[39996.872974] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[40116.693816] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360
[40183.613347] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360
[40236.433919] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[40356.229181] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[40475.969548] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[40595.713902] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[40715.285340] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[40787.106574] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[40835.832519] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360
[40955.420938] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 575
[41074.997595] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 575
[41088.524454] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 575
[41194.569673] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[41315.160810] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[41389.993756] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[41434.716980] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360
[41554.305670] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[41674.888582] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[41691.423798] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[41794.445674] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[41914.045176] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[41992.905243] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[42033.605750] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[42154.408618] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360
[42273.972896] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[42294.538690] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[42393.529232] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[42513.101695] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[42595.984746] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[42633.672741] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[42753.249160] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[42872.821601] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[42897.406182] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[42992.389772] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[43112.980794] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360
[43198.876008] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360
[43232.545499] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[43352.097700] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427
[43472.661248] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360
[43500.253615] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360
[43592.217450] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360
```


And this for the second one

```
sabel@Sabel:~$ cat /var/log/syslog | grep etwork | tail -n20
Dec  1 00:42:50 Sabel NetworkManager[954]: <info> Activation (ra0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Dec  1 00:42:50 Sabel NetworkManager[954]: <info> Activation (ra0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Dec  1 00:42:50 Sabel NetworkManager[954]: <info> Activation (ra0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Dec  1 05:04:19 Sabel NetworkManager[954]: <info> (ra0): supplicant interface state: completed -> disconnected
Dec  1 05:04:19 Sabel NetworkManager[954]: <info> (ra0): supplicant interface state: disconnected -> scanning
Dec  1 05:04:24 Sabel NetworkManager[954]: <info> (ra0): supplicant interface state: scanning -> associating
Dec  1 05:04:25 Sabel NetworkManager[954]: <info> (ra0): supplicant interface state: associating -> completed
Dec  1 06:55:17 Sabel NetworkManager[954]: <info> (ra0): supplicant interface state: completed -> disconnected
Dec  1 06:55:17 Sabel NetworkManager[954]: <info> (ra0): supplicant interface state: disconnected -> scanning
Dec  1 06:55:23 Sabel NetworkManager[954]: <info> (ra0): supplicant interface state: scanning -> associating
Dec  1 06:55:23 Sabel NetworkManager[954]: <info> (ra0): supplicant interface state: associating -> completed
Dec  1 08:46:17 Sabel NetworkManager[954]: <info> (ra0): supplicant interface state: completed -> disconnected
Dec  1 08:46:17 Sabel NetworkManager[954]: <info> (ra0): supplicant interface state: disconnected -> scanning
Dec  1 08:46:23 Sabel NetworkManager[954]: <info> (ra0): supplicant interface state: scanning -> associating
Dec  1 08:46:23 Sabel NetworkManager[954]: <info> (ra0): supplicant interface state: associating -> completed
Dec  1 12:03:27 Sabel NetworkManager[954]: <info> (ra0): DHCPv4 state changed reboot -> renew
Dec  1 12:03:27 Sabel NetworkManager[954]: <info>   address 192.168.1.9
Dec  1 12:03:27 Sabel NetworkManager[954]: <info>   prefix 24 (255.255.255.0)
Dec  1 12:03:27 Sabel NetworkManager[954]: <info>   gateway 192.168.1.1
Dec  1 12:03:27 Sabel NetworkManager[954]: <info>   nameserver '192.168.1.1'
```

---

### Post by chili555 on 2012-12-01
That's ugly! I assume you have the same device and followed the same process as here: [http://ubuntuforums.org/showpost.php?p=12179088&postcount=19](http://ubuntuforums.org/showpost.php?p=12179088&postcount=19)

If not, let's dig deeper:```
lsusb
```

---

### Post by Sabel21210 on 2012-12-01
> **chili555 said:**
> That's ugly! I assume you have the same device and followed the same process as here: [http://ubuntuforums.org/showpost.php?p=12179088&postcount=19](http://ubuntuforums.org/showpost.php?p=12179088&postcount=19)

If not, let's dig deeper:```
lsusb
```


That's how i got it running in the first place honestly here is the Lsusb anyway though

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0846:9012 NetGear, Inc. 
Bus 001 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver

```

---

### Post by chili555 on 2012-12-01
What version did you build? I notice there is a 9-11-2012 version here. You might repeat the steps with the presumably improved version. Note any warnings at the 'make' stage and we'll try to fix them.

[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

---

### Post by Sabel21210 on 2012-12-01
Honestly if you or anyone has a wireless USB adapter i could look for at Best Buy that would work easier I'm headed to the city tomarrow. Im running Ubuntu 12.4 LTS to be clear and i will need to run at gaming speeds. It also needs to be able to reach through a floor..

Unless of course this is an east fix in which case il do that instead.

---

### Post by Sabel21210 on 2012-12-01
I haden't noticed your previous post before i had posted me last one..my apologies for the double post. 

I downloaded the top file from the link you last sent me and have been following the steps as previously. It already had "Netgear" in the bit you had us add it previously but instead it had it labled exactly by name.

```
#endif /* RT35xx */
#ifdef RT3573
	{USB_DEVICE(0x148F,0x3573)}, /* Ralink 3573 */
	{USB_DEVICE(0x7392,0x7733)}, /* Edimax */
	{USB_DEVICE(0x0846,0x9012)}, /* Netgear */
	{USB_DEVICE(0x0B05,0x17AD)}, /*ASUS */
#endif /* RT3573 */
	{ }/* Terminating entry */
```

Here is the Dump from the Make command

```
root@Sabel:/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO# makemake -C tools
make[1]: Entering directory `/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/tools'
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/Makefile
make -C /lib/modules/3.2.0-34-generic/build SUBDIRS=/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-34-generic'
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_md5.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_aes.o
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Wrap’:
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_aes.c:1466:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat]
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Unwrap’:
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_aes.c:1561:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat]
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/mlme.o
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/mlme.c:562:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/mlme.c:562:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_wep.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/action.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_data.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rtmp_init.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_aes.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_sync.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/eeprom.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_info.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_radar.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/spectrum.o
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/spectrum.c:1972:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat]
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rt_channel.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_profile.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_asic.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/rt_profile.o
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/rt_profile.c: In function ‘STA_MonPktSend’:
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/rt_profile.c:402:9: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat]
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../chips/rtmp_chip.o
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../chips/rtmp_chip.c: In function ‘RTMPReadChannelPwr’:
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../chips/rtmp_chip.c:1336:2: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/assoc.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/auth.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/sync.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/sanity.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/connect.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/wpa.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rt_os_util.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/rt_linux.o
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/rt_linux.c:508:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
/usr/src/linux-headers-3.2.0-34-generic/arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/rt_linux.c:510:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
/usr/src/linux-headers-3.2.0-34-generic/arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/rt_linux.c:662:20: warning: assignment makes integer from pointer without a cast [enabled by default]
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsPktInit’:
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/rt_linux.c:681:2: warning: assignment makes integer from pointer without a cast [enabled by default]
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/rt_linux.c:708:15: warning: assignment makes integer from pointer without a cast [enabled by default]
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../rate_ctrl/alg_grp.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/ba_action.o
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/ba_action.c:1553:2: warning: assignment makes integer from pointer without a cast [enabled by default]
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rt_led.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_mac_usb.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rtusb_io.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rtusb_data.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_data_usb.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/ee_prom.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/ee_efuse.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rt_rf.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rtusb_bulk.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/rt_usb.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../chips/rt28xx.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../chips/rt30xx.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../chips/rt35xx.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../chips/rt3593.o
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../chips/rt3593.c: In function ‘RT3593_ChipSwitchChannel’:
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../chips/rt3593.c:855:16: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../chips/rt3593.c:872:16: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../chips/rt3593.c:890:15: warning: comparison of distinct pointer types lacks a cast [enabled by default]
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/rt_usb_util.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../os/linux/usb_main_dev.o
  CC [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/frq_cal.o
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/frq_cal.c: In function ‘FrequencyCalibration’:
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/frq_cal.c:198:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/frq_cal.c:211:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/frq_cal.c:227:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/frq_cal.c:252:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/frq_cal.c:265:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/frq_cal.c:281:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
  LD [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/rt3573sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/rt3573sta.mod.o
  LD [M]  /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/rt3573sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-34-generic'
cp -f /home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/rt3573sta.ko /tftpboot
root@Sabel:/home/sabel/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO# 
```

I'm not sure if it will work exactly so i was posting this before i finished the steps. Sorry if this is too much info or too many posts.

---

### Post by chili555 on 2012-12-01
> Sorry if this is too much info or too many posts.Not at all, no problem at all.> I'm not sure if it will work exactly There's only one way to find out:```
sudo su
make install
modprobe rt3573sta
exit
iwconfig
```Does it connect?

---

### Post by Sabel21210 on 2012-12-02
It did connect but i'm not sure if it changed anything at all. I was using the Adapter while i was doing all of that which..im not sure if was a problem. i didn't even lose connection for a second when i modprobe'd


Also tested on a game and still wobbly connection speed. I'm actually on my windows ATM Just Freshly installed 8 and im downloading a rather large file now and getting some wierd connection as well. Can't tell if it's the source of my download currently or something with the dongle. 

I was connected directly to the modem earlier today with a different laptop with..no noticeable problems...I was also connected by sharing the connection with said laptop by having the laptop connected to the wireless and myself plugging into the laptop with an ethernet cable and had a stable connection..so i'm assuming it's either the dongle itself or the drivers...Seeing as how i may be having trouble with it not on a fresh windows install...it's got me thinking it's probably the dongle itself. 


This Linux troubleshooting can't hurt though.

What's strange about the whole thing is that if i run a speed test at Speedtest.net it comes up with normal speeds for my internet connection when it's working properly..

---

### Post by DanielWEWO on 2013-01-12
I want to bump this thread, I'm really new to Linux and Ubuntu. I've got it running on my laptop pretty well right now, but I want to get it running on my desktop. I'm going to be learning Unix shell and Programming, and most likely using some distro of linux to do so. I've got a $60 Wifi card that is basically unusable in Ubuntu. I've read through this thread and though a few solutions were posted, I wasn't exactly sure how to implement them. 

Is there a way to get this working on my desktop? If so, can you guys guide me through getting it working? 

Sorry if this is demanding, but I don't want to have to go and spend more money just for a Wifi connection when I've got a perfectly good card right in front of me.

Thanks so much guys!
Daniel.

---

### Post by praseodym on 2013-01-12
You may try the RT5572 driver Version 2.6.1.3.

[http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)

---

### Post by DanielWEWO on 2013-01-12
I gotta be tripping out, on that page it seems like there's no way to download the file. I clicked on the text and it brings me to a page with no download link, and I tried clicking the floppy and it brings me to a page that has no release information when it should lol.

I searched around the internet and couldn't find anything that didn't link me to this page also.

I'm such a noob I'm sorry.

---

### Post by praseodym on 2013-01-13
Klick on the driver name. Then you have to confirm the licence (scroll down)

---

### Post by kurt18947 on 2013-01-13
> **praseodym said:**
> Klick on the driver name. Then you have to confirm the licence (scroll down)

You also have to enter a name and email address.  It doesn't look like they have to be real;).

---

### Post by DanielWEWO on 2013-01-13
Yeah, that's what I didn't get at first. I thought entering that was so that I could get support for the product.


So, I'm super noob but after some poking around on the interwebz to figure out how to install a tar.bz2 package I have to have an installer installed. Unfortunately to get this installer I have to be connected to the internet. I had another USB Wifi card lying around but I'm having trouble getting connected with that one too.

I'm tired of things being a pain in the *** to actually get working on Ubuntu.

I've got the tar.bz2 file on my desktop computer right now but how do I install it if I don't have access to the internet to get an installer?

No, I don't have a possibility of wiring in to the router. I tried sharing the connection from my laptop, but that wasn't working, it was a never ending cycle of connecting and disconnecting.

Ubuntu really isn't easy if I don't already know what I'm doing.

So, my super noob *** needs to figure out how to install this freaking driver. 

Thanks for being patient with me guys. I'm not computer illiterate (at least I don't think I am) I've built my own, and done plenty of graphic design, audio production etc. but when it comes to Linux I feel like my grandma using a computer.

---

### Post by jrwizzard on 2013-01-31
Thank You Chili555, my WNDA4100 works great.

---

### Post by darawk on 2013-03-15
To anyone who tried everything in this thread and is still having trouble with this, there is a bug in the way this driver handles sk_buff structures on 64-bit systems that was causing a kernel panic when any packets over a certain size were sent.  I wrote a patch for it that you can grab here:

[https://github.com/ashaffer/rt3573sta](https://github.com/ashaffer/rt3573sta)

I'll email ralink and hopefully they'll have an official version of this soon, but in the meantime you can use mine.

---

### Post by ericosaurus on 2013-03-15
Very cool, thanks for posting this darawk.  

I know it's hard to say, but do you think that bug could have caused a recurring system crash after a day or two of use?  That's a problem I've been having with the n900.

---

### Post by darawk on 2013-03-15
> **ericosaurus said:**
> Very cool, thanks for posting this darawk.  

I know it's hard to say, but do you think that bug could have caused a recurring system crash after a day or two of use?  That's a problem I've been having with the n900.

That seems like it could be possible.  For me the bug manifested almost immediately - I could connect to my local network, and I could send ping packets out, but as soon as I tried to send anything larger it would crash.  If you grep your syslog for 'panic' and you see something that looks like this:

[  148.889884] skbuff: skb_over_panic: text:ffffffff81568980 len:1523 put:105 head:ffff8801d01a7000 data:ffff8801d01a70ac tail:0xd01a769f end:0x640 dev:<NULL>

Then my patch should help you, otherwise your problem may be different.  Either way it's probably worth a try with my version if you're having consistent problems.

---

### Post by dalaron on 2013-03-19
Following chili555's instruction on page 4 of this thread I was able to get my adapter to work on my PC.

One day ago, however, it just decided to stop working for me. A disconnected from network notification would flash up when I logged in.

 The solution I found was to repeat the last few steps of chili555's instructions:

```
 
sudo su 
make 
make install 
modprobe rt3573sta 
exit

```

I think I was repeating some un-necessary steps, but my wirless is working again anyway!

---

### Post by djfye on 2013-03-30
Thanks for the fix darawk. I had been using a different card with ndiswrapper that would drop connection quite a bit. I went back to searching for getting this card working and found your post.

---

### Post by ManfredU on 2013-04-09
> **darawk said:**
> [...] I wrote a patch for it that you can grab here: [https://github.com/ashaffer/rt3573sta](https://github.com/ashaffer/rt3573sta) [...]

Thank you, I'm using your version for a TRENDnet TEW-684UB.

---

### Post by Oceola on 2013-04-14
Built a new system and wanted to place wireless internet on it.
Was really stumped, not understanding the differences in the use of similar words.
This thread made it a whole lot easier.
When i went to purchase the wifi the store personnel recommended the Netgear 600 as being virtually plug and play.
Made an assumption if that would work the higher rate NetGear 4100 would work, nope.
Drivers on the disc were Windows only.

Followed the instructions in this thread and it works great.
Compile, a scary word to some of us, could not have been easier.

I've made paper copies of the instructions and re-do for  the kernel changes and will be delivering them to the store which sold me the device.
Maybe it will help some other knucklehead as well. ;)

Thanks to all.

---

### Post by zoff_ita on 2013-05-05
Hi!
I followed the instructions here and it seems to be working.

Just for comparison I would like to try windows drivers throgh ndiswrapper but I'm getting some trouble in getting it working.

First thing I did was to blacklist linux module putting 'blacklist rt3573sta' in /etc/modprobe.d/blacklist.conf.
Then I installed the driver in ndiswrapper through .inf with:
```
sudo ndiswrapper -i netr28ux.inf
```

All seems fine 'cause:
```
$ lsusb | grep NetGear
Bus 001 Device 004: ID 0846:9012 NetGear, Inc. WNDA4100 802.11abgn 3x3:3 [Ralink RT3573]
$ sudo depmod -a
$ sudo modprobe ndiswrapper
$ lsmod | grep ndiswrapper
ndiswrapper           283323  0 
$ sudo ndiswrapper -l
netr28ux : driver installed
```

...but the adapter doesn't appear neither in ifconfig and iwconfig.

Any idea?

---

### Post by chili555 on 2013-05-05
> $ sudo ndiswrapper -l
netr28ux : driver installedIf it doesn't also report 'device present' that strongly suggests that the netr28ux.inf file doesn't cover your device:> ID [COLOR="#FF0000"]0846:9012[/COLOR] NetGear, Inc. WNDA4100 802.11abgn 3x3:3 [Ralink RT3573]Where did you get the file? Is it for Windows XP? Are there any clues here?```
dmesg | grep ndis
```

---

### Post by zoff_ita on 2013-05-05
I got the file from a Windows 7 64bit installation.

dmesg doesn't display anything usefull about ndiswrapper.

---

### Post by chili555 on 2013-05-05
> **zoff_ita said:**
> I got the file from a Windows 7 64bit installation.

Here is a snip from *man ndiswrapper*:> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install  Win&#8208;
       dows  XP drivers and kernel module to load the Windows XP drivers. Both
       are called ndiswrapper.I suggest you remove your 7 drivers and try again. Post back if you need additional guidance.

---

### Post by zoff_ita on 2013-05-05
Where do I get xp drivers?

On the driver's disk there's only a Setup.exe.

---

### Post by chili555 on 2013-05-05
You might check Ralink's website. Usually, their files are zipped.

---

### Post by zoff_ita on 2013-05-05
> **chili555 said:**
> You might check Ralink's website. Usually, their files are zipped.

Already tried... If I download Windows Driver i get a .exe

---

### Post by praseodym on 2013-05-05
Right-click on the EXE and open it with the archive manager. Extract all files into a new folder. There should be the INF-file

---

### Post by zoff_ita on 2013-05-05
Already tried that too.
What I get are two files that file command recognize as "data".

---

### Post by chili555 on 2013-05-05
> **zoff_ita said:**
> Already tried that too.
What I get are two files that file command recognize as "data".Do you have or does a friend have a Windows computer you can install the exe on? You can then grab the XP files and after we're sure it's working on Ubuntu, remove it. Be sure to get both 32- and 64-bit versions along with the .inf, .sys and .cat files. Better to have everything.

---

### Post by praseodym on 2013-05-05
Did you install Wine? If so, make a fake installation of the driver via Wine and copy the files.

---

### Post by zoff_ita on 2013-05-05
> **praseodym said:**
> Did you install Wine? If so, make a fake installation of the driver via Wine and copy the files.

already tried.
installation fails

---

### Post by chili555 on 2013-05-05
> **zoff_ita said:**
> already tried.
installation failsFor wine, me, too.

---

### Post by praseodym on 2013-05-05
Try it with cabextract:
```

sudo apt-get install cabextract unshield 
```

---

### Post by chili555 on 2013-05-05
> **praseodym said:**
> Try it with cabextract:
```

sudo apt-get install cabextract unshield 
```I failed to extract it with cabextract, unshield, unrar or unzip.

---

### Post by zoff_ita on 2013-05-07
bump

---

### Post by chili555 on 2013-05-07
> **zoff_ita said:**
> bumpDo you have or does a friend have a Windows computer you can install the exe on? You can then grab the XP files and after we're sure it's working on Ubuntu, remove it. Be sure to get both 32- and 64-bit versions along with the .inf, .sys and .cat files. Better to have everything. 

I'm afraid that's all I can suggest.

---

### Post by zoff_ita on 2013-05-09
> **chili555 said:**
> Do you have or does a friend have a Windows computer you can install the exe on? You can then grab the XP files and after we're sure it's working on Ubuntu, remove it. Be sure to get both 32- and 64-bit versions along with the .inf, .sys and .cat files. Better to have everything. 

I'm afraid that's all I can suggest.

Ok, I managed to get a WindowsXP 32bit virtual machine, I found .sys and .bin file in C:\WINDOWS\System32\Drivers but I can't file .inf file needed by ndiswrapper.
There's no C:\WINDOWS\Inf folder and search utility of windows XP finds only "rt2870.sys" and "rt2870.bin" starting from C:\

Any idea?

---

### Post by zoff_ita on 2013-05-09
Ok, some progress have been made :D

I found an archive with a compatible driver for any windows version at this address: [http://202.221.139.247/pub/asustw/wireless/USB-N66/DR_USB_N66_1007.zip](http://202.221.139.247/pub/asustw/wireless/USB-N66/DR_USB_N66_1007.zip)

 I attached the driver for windows xp I'm using right now.

I'll write back after some test.

---

### Post by chili555 on 2013-05-09
I look forward to your report. Remember, dmesg will show all kinds of useful information:```
dmesg | grep ndis
```

---

### Post by zoff_ita on 2013-05-09
I needed 64bit driver so I attached in previous message that too.

Here dmesg:
```
[  375.977145] usbcore: deregistering interface driver ndiswrapper
[  375.980564] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[  376.163342] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExEventObjectType'
[  376.163351] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'__chkstk'
[  376.163475] ndiswrapper (load_sys_files:199): couldn't prepare driver 'rt2870'
[  376.163650] ndiswrapper (load_wrap_driver:121): couldn't load driver 'rt2870'
[  376.163709] usbcore: registered new interface driver ndiswrapper
```

---

### Post by chili555 on 2013-05-09
> ndiswrapper (import:232): unknown symbol:[COLOR="#FF0000"] ntoskrnl.exe[/COLOR]:'ExEventObjectType'I thought this was fixed in the latest version of ndiswrapper. Is yours the standard 13.04 64-bit ndiswrapper install or did you compile it from the ndiswrapper website? You will probably need to compile.

By the way, if this is an rt2870 device and actually *works*, I owe Mrs. Chili US$1000.

---

### Post by zoff_ita on 2013-05-09
It should be the latest version, I'm on an up-to-date Ubuntu 13.04:
```
$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/3.8.0-19-generic/updates/dkms/ndiswrapper.ko
version:        1.58
vermagic:       3.8.0-19-generic SMP mod_unload modversions
```

---

### Post by chili555 on 2013-05-09
I suggest you try compiling the latest: [http://ubuntuforums.org/showthread.php?t=1695036&page=13&p=12527981#post12527981](http://ubuntuforums.org/showthread.php?t=1695036&page=13&p=12527981#post12527981)

Reboot and check again:```
dmesg | grep ndis
```

---

### Post by zoff_ita on 2013-05-09
Done.
Same error.

Full log:
```
./ndiswrapper-1.58$ make
make -C utils
make[1]: ingresso nella directory "/media/data/ndiswrapper-1.58/utils"
gcc -g -Wall -I../driver  -o loadndisdriver loadndisdriver.c
make[1]: uscita dalla directory "/media/data/ndiswrapper-1.58/utils"
make -C driver
make[1]: ingresso nella directory "/media/data/ndiswrapper-1.58/driver"
make -C /usr/src/linux-headers-3.8.0-19-generic M=/media/data/ndiswrapper-1.58/driver
make[2]: ingresso nella directory "/usr/src/linux-headers-3.8.0-19-generic"
  LD      /media/data/ndiswrapper-1.58/driver/built-in.o
  MKEXPORT /media/data/ndiswrapper-1.58/driver/crt_exports.h
  MKEXPORT /media/data/ndiswrapper-1.58/driver/hal_exports.h
  MKEXPORT /media/data/ndiswrapper-1.58/driver/ndis_exports.h
  MKEXPORT /media/data/ndiswrapper-1.58/driver/ntoskernel_exports.h
  MKEXPORT /media/data/ndiswrapper-1.58/driver/ntoskernel_io_exports.h
  MKEXPORT /media/data/ndiswrapper-1.58/driver/rtl_exports.h
  MKEXPORT /media/data/ndiswrapper-1.58/driver/usb_exports.h
  MKSTUBS /media/data/ndiswrapper-1.58/driver/win2lin_stubs.h
  CC [M]  /media/data/ndiswrapper-1.58/driver/crt.o
  CC [M]  /media/data/ndiswrapper-1.58/driver/hal.o
  CC [M]  /media/data/ndiswrapper-1.58/driver/iw_ndis.o
  CC [M]  /media/data/ndiswrapper-1.58/driver/loader.o
  CC [M]  /media/data/ndiswrapper-1.58/driver/ndis.o
  CC [M]  /media/data/ndiswrapper-1.58/driver/ntoskernel.o
  CC [M]  /media/data/ndiswrapper-1.58/driver/ntoskernel_io.o
  CC [M]  /media/data/ndiswrapper-1.58/driver/pe_linker.o
  CC [M]  /media/data/ndiswrapper-1.58/driver/pnp.o
  CC [M]  /media/data/ndiswrapper-1.58/driver/proc.o
  CC [M]  /media/data/ndiswrapper-1.58/driver/rtl.o
  CC [M]  /media/data/ndiswrapper-1.58/driver/wrapmem.o
  CC [M]  /media/data/ndiswrapper-1.58/driver/wrapndis.o
  CC [M]  /media/data/ndiswrapper-1.58/driver/wrapper.o
  CC [M]  /media/data/ndiswrapper-1.58/driver/usb.o
  AS [M]  /media/data/ndiswrapper-1.58/driver/win2lin_stubs.o
  AS [M]  /media/data/ndiswrapper-1.58/driver/lin2win.o
  LD [M]  /media/data/ndiswrapper-1.58/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /media/data/ndiswrapper-1.58/driver/ndiswrapper.mod.o
  LD [M]  /media/data/ndiswrapper-1.58/driver/ndiswrapper.ko
make[2]: uscita dalla directory "/usr/src/linux-headers-3.8.0-19-generic"
make[1]: uscita dalla directory "/media/data/ndiswrapper-1.58/driver"
./ndiswrapper-1.58$ sudo make install
[sudo] password for zoff: 
make -C driver install
make[1]: ingresso nella directory "/media/data/ndiswrapper-1.58/driver"
mkdir -p -m 755 /lib/modules/3.8.0-19-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/3.8.0-19-generic/misc
/sbin/depmod -a 3.8.0-19-generic
make[1]: uscita dalla directory "/media/data/ndiswrapper-1.58/driver"
make -C utils install
make[1]: ingresso nella directory "/media/data/ndiswrapper-1.58/utils"
mkdir -p -m 755 /sbin
mkdir -p -m 755 /usr/sbin
install -m 755 loadndisdriver /sbin
install -m 755 ndiswrapper /usr/sbin
install -m 755 ndiswrapper-buginfo /usr/sbin
make[1]: uscita dalla directory "/media/data/ndiswrapper-1.58/utils"
mkdir -p -m 755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
./ndiswrapper-1.58$ sudo rmmod ndiswrapper
./ndiswrapper-1.58$ sudo rmmod ndiswrapper
Error: Module ndiswrapper is not currently loaded
./ndiswrapper-1.58$ sudo modprobe ndiswrapper
./ndiswrapper-1.58$ dmesg | grep ndis
[....]
[ 3937.450644] usbcore: deregistering interface driver ndiswrapper
[ 3940.378960] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 3940.560960] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExEventObjectType'
[ 3940.560970] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'__chkstk'
[ 3940.561094] ndiswrapper (load_sys_files:199): couldn't prepare driver 'rt2870'
[ 3940.561284] ndiswrapper (load_wrap_driver:121): couldn't load driver 'rt2870'
[ 3940.561340] usbcore: registered new interface driver ndiswrapper
```

---

### Post by chili555 on 2013-05-10
Other than trying a 32-bit install and the native driver, I'm afraid I have no other ideas.

---

### Post by ejmcelfresh on 2013-05-25
I also have the WNDA4100 adapter, and I run a 64 bit system. Literally the only thing keeping me from jumping to Ubuntu is this single driver not being here as it's not possible to set up my system near my router. If some one would be able to produce a driver for this adapter, I would be very appreciative, as I've been trying to ditch windows for a long time now. I'm interested in Ubuntu version 13.04 or 13.10.  I've sent an email to Netgear inquiring about this as well.

---

### Post by praseodym on 2013-05-25
Hi,

maybe I am lost now in this thread. The device ID for this stick can be added to the rt2800usb driver. Try this one-liner with ndiswrapper uninstalled:
```

echo 'install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "0846 9012" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf
sudo modprobe -rfv ndiswrapper
sudo modprobe -v rt2800usb
```
Replug the stick and check:
```

iwconfig
lsmod
sudo iwlist scan
dmesg | grep rt2
```
Alternatively, the drivers rt5572 and rt5372 can be tested, but the ID still lacks in this drivers.

---

### Post by ejmcelfresh on 2013-05-25
I just received an email from netgear, they stated they absolutely do not support linux, so there will be no help from them. Is there a list of verified, supported adapters? I would really like to have something with dualband 450 and 5GHz support. ( as the one I have now is).

---

### Post by praseodym on 2013-05-25
That does not matter, because its a Ralink chipset. Ralink support normally is pretty good.

---

### Post by ejmcelfresh on 2013-05-25
I found the new ralink site and this list of linux drivers: [http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)

---

### Post by praseodym on 2013-05-26
Did you try adding the device ID?

---

### Post by boblizar on 2013-07-07
i have the step down in speed, single band.  its ath9k_htc and works a charm, 7 bucks on ebay.

0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]

---

### Post by kHQ4JpJ on 2013-08-25
Just posting to thank all previous posters for all I learned to get this adapter working.  I had trouble at first but was using RT5572sta package, which appeared to support the adapter.  Then I switched to 20120911_RT3573sta package and worked flawlessly.  Thanks again, I couldn't have got it to work without ya's.

---

### Post by dunmireg on 2013-09-06
I apologize for being a noob to ubuntu and resurrecting dead thread. I just installed ubuntu successfully and followed the steps outlined by chilli on page 4 and the driver worked fine, everything lit up and I connected to the wireless network. However when I took out my ethernet and tried to use my wifi my entire system just froze. This happened multiple times. Has anyone encountered this and know a way to fix it? I am using ubuntu 12.04 and the wnda4100 card by the way. Thanks
I'm coming back to edit this because I've been doing some searching and I wonder, could the problem be that I'm running a 64 bit ubuntu? Is there any way to fix that?

---

### Post by chili555 on 2013-09-07
> **dunmireg said:**
> I apologize for being a noob to ubuntu and resurrecting dead thread. I just installed ubuntu successfully and followed the steps outlined by chilli on page 4 and the driver worked fine, everything lit up and I connected to the wireless network. However when I took out my ethernet and tried to use my wifi my entire system just froze. This happened multiple times. Has anyone encountered this and know a way to fix it? I am using ubuntu 12.04 and the wnda4100 card by the way. Thanks
I'm coming back to edit this because I've been doing some searching and I wonder, could the problem be that I'm running a 64 bit ubuntu? Is there any way to fix that?It depends on many things, all of which I think we ought to explore in your own new thread. Please include:```
uname -r
lsmod | grep rt
lsusb
```I think the 64-bit issue is probably the cause, however, we may have a better way! If I don't catch your thread right away, please send me a private message.

---

### Post by El_Papi on 2013-09-23
I trying to make procedure on page 4 to work on a BeagleBoard Xm (ARM board) but have trouble with apt-get [COLOR=#000000][FONT=Ubuntu Mono]install linux-headers-generic **not found**

Thanks,

[/FONT][/COLOR]

---

### Post by praseodym on 2013-09-23
Which Ubuntu version do you use?
```

uname -a
lsb_release -a
```
please

---

### Post by El_Papi on 2013-09-23
Thank you for your replay praseodym !,

ubuntu@omap:~$ uname -a
**Linux omap 3.0.6-x3 #1 SMP Wed Oct 5 12:46:18 UTC 2011 armv7l armv7l armv7l GNU/Linux**
ubuntu@omap:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.10
Release:        11.10
Codename:       oneiric
ubuntu@omap:~$ 

Netgear wnda4100 wasn't plugin !

my question is in reference to [COLOR=#000000][FONT=Ubuntu Mono]linux-headers-generic  how to install it ?

if  i do a :
apt-get install linux-headers-generic , its fails with not found .

How do you compile ?

Thanks,

[/FONT][/COLOR]

---

### Post by praseodym on 2013-09-24
Obviously, you are using an outdated Ubuntu version and kernel. I strongly recommend using 12.04 instead

---

### Post by El_Papi on 2013-09-25
hi [COLOR=#000000]praseodym ,
[/COLOR]
I upgrade to 12.10 quantal and can't get to install [COLOR=#000000][FONT=Ubuntu Mono]linux-headers .
[/FONT][/COLOR]Is there a place where i could get/ build for arm processor ?

ubuntu@arm:~$ uname -a
Linux arm 3.7.10-x13 #1 SMP Wed Jun 26 15:48:09 UTC 2013 armv7l armv7l armv7l GNU/Linux
ubuntu@arm:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.10
Release:        12.10
Codename:       quantal
ubuntu@arm:~$

---

### Post by Xserch on 2013-09-27
Hello guys. I'm new to this forum and I was wondering if somebody could help me. I have the WNDA4100 wireless adapter and Im able to find it in airmon-ng as ra0. My problem is that im unable to connect to a network WiFi. If I use Wicd I always get bad password. Yes I had the password in properties. Also when running a airmon-ng start ra0 I always get:

root@bt:~# airmon-ng

Interface Chipset Driver

ra0 Ralink 2560 PCI rt2500

root@bt:~# airmon-ng start ra0

Found 3 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID Name
3694 dhclient
3712 dhclient
4790 dhclient3
Process with PID 4790 (dhclient3) is running on interface ra0

Interface Chipset Driver

ra0 Ralink 2560 PCI rt2500 (monitor mode enabled)

How do I find if the monitor mode is really working ?

Also do I have to kill the process that is conflicting ?

How can I test if injeccion is working ?

Running a wash -i ra0 i get 

] Found packet with bad FCS, skipping...
[!] Found packet with bad FCS, skipping...

over and over.

THANKS ALOT.

And yes I know what google is if you are wondering. Just need a little bit more help.

(How do I paste console outputs in those tables that do size small ?)

---

