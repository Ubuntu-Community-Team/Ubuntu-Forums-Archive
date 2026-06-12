---
title: "Atheros AR242X wifi"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by diamondjim08 on 2009-02-18
On a brand new Acer 5515 notebook, Ubuntu 8.10 was installed.  However, as many posts have stated, the Atheros AR242X wifi simply will not work.  I have done many things mentioned in the posts but no luck.  Here is what I've done:
1. Installed backports modules, enabled Atheros 802 support, installed WICD manager as suggested.  No Luck.
2. Next I tried the madwifi routine using Subversion, compiling, intalling but no luck.
3. Then there are some posts about Compat-wireless and so I installed using instructions on the forum.  No Luck.
4. I found NDISWRAPPER instructions on this forum and insatlled the net5211.inf driver. No luck.
5. Bluetooth is disabled.

6. This is the present iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
All of the above installs were w/o errors... that I know of.
I live in a condo and I see secured and unsecured networks on my older Compaq notebook wifi just fine - Ubuntu 8.10.  But none of them show up on this blasted Atheros wifi!! :-(
What WPA supplicant driver should I use in WICD? None have worked - wext, ndiswrapper, madwifi or the others listed.
What should I do to fix this?  I've never had this much trouble installing Ubuntu before!  BTW, I am still new to this sport so solutions should be easy to understand.
Thanks for any help!
<> Jim

---

### Post by Ketara on 2009-02-18
For the ndiswrapper route, it's possible that you have the wrong driver.

It's been a while since I did mine but if I remember correctly there's a bug in Intrepid that causes lspci to call several similar but different Atheros chipsets 242x. The driver I use is called "netathw.inf"

---

### Post by Crafty Kisses on 2009-02-18
Let's see if we can't make this wireless card work with an ndiswrapper, first make sure you have ndiswrapper installed:
```
sudo apt-get install ndiswrapper
```
Once you have ndiswrapper installed, you need to grab the driver for you wireless card, which you can get right [here.]("http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz") Once you have that installed, it's time to install the driver, so run the following:
```
sudo ndiswraper -i net5007.inf
```
Remember I'm just assuming the driver is called net5007.inf, so replace net5007.inf with the actual driver name, so once you have done that, make sure the driver is installed correctly:
```
sudo ndiswrapper -l
```
Then make sure the ndiswrapper module loads on every start, so run the following command:
```
sudo ndiswrapper -ma
```
Now blacklist these modules, first you need to open your blacklist configuration file, run the following:
```
sudo nano /etc/modprobe.d/blacklist
```
Once you're in the text file, add the following lines:
```
blacklist ath_pci
blacklist ath_hal

```
Then restart your computer by running the following:
```
sudo shutdown -r now
```
Reboot and your wireless should be working.

---

### Post by diamondjim08 on 2009-02-18
Thanks for the hint.  I just loaded that driver while running Live CD to try ans see if a "clean system" would run it.  NOT!  This computer runs the wifi under Vista but not in Ubuntu.
I'll try this new driver in the installed system and see what happens.  Thanks again.

---

### Post by diamondjim08 on 2009-02-18
Thanks for the hint. I just loaded that driver while running Live CD to try ans see if a "clean system" would run it. NOT! This computer runs the wifi under Vista but not in Ubuntu.
I'll try this new driver in the installed system and see what happens. Thanks again.

---

### Post by Ketara on 2009-02-18
Have you tried the .inf file that is in your Vista partition with ndiswrapper?

---

### Post by ralphieb2000 on 2009-02-18
I set up one of those Acer netbooks for a friend last weekend.

Hold the kennel at version: Ubuntu 8.10, kernel 2.6.27-7-generic

Edit this file: /etc/modprobe.d/blacklist
add
blacklist ath_pci
blacklist ath_hal

Edit this file: /etc/sources/sources.list

Look for this entry: do as directed, you may have to uncomment the back port server addresses.



## Uncomment the following two lines to add software from the 'backports'
repository.
##N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

next step:

sudo apt-get install linux-backports-modules-intrepid

then reboot.

Worked for me.

---

### Post by binbash on 2009-02-19
This is how i got it working : [http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

---

### Post by diamondjim08 on 2009-02-19
You guys gave me some great ideas on backports, ndiswrapper and madberry (madwifi) for AR242 Acer Wifi. I followed them to the "T", BUT we are not there yet.
sudo ndiswrapper -l gives this respnse:
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath5k)
The "ath5k" driver is in this directory:
/home/mashid/Desktop/compat-wireless-2009-02-17/drivers/net/wireless

Is there a train wreck here with these driver/module installs?  
By far, the ndiswrapper method is the cleanest install and if we can get it to work, great!
The other installs, madwifi & compat-wireless are still on the machine. Do I have to remove them or disable them to get this to work??

OR do I have the wrong driver for this new Acer 5515?
Still chasing my tail!!!!
Thanks guys for taking the time to help out with this problem!
<> Jim

---

### Post by Ketara on 2009-02-19
Yes, you want to make sure you only have one driver attempting to claim the card. ath5k is a madwifi driver, and will not work with ndiswrapper.

Go into a terminal and enter:

gksudo gedit etc/modprobe.d/blacklist

(note: be very careful whenever you open a gedit file with root priveleges, as accidents can cause serious system damage.)

Look in that file for any of the following lines:

blacklist ath_hal
blacklist ath_pci
blacklist ath5k
blacklist ath9k

If they are there but commented (have a # before them) then remove the #. If they are not there, add them at the bottom.

Then, in terminal:

sudo modprobe ndiswrapper
sudo reboot

If you have the correct windows driver, hopefully that will get it working.

---

### Post by Crafty Kisses on 2009-02-19
Let's see if this will work, let's remove the driver first, so run the following:
```
sudo ndiswrapper -l
```
Make sure the driver is there, now what you want to do is remove the driver by running the following:
```
sudo ndiswrapper &#8211;e drivername
```
Once you have done that, let's try another method, install the following package:
```
sudo apt-get install ndisgtk
```
Once you have ndisgtk installed, run the following in the Terminal:
```
sudo ndisgtk
```
Then click on "Install new driver" then find the .inf file, and click "Install driver" and you should see "Hardware present" and then see if you can connect to the internet.

---

### Post by diamondjim08 on 2009-02-19
Ketara,
After following your advice, blacklisting and rebooting WICD stills says no wireless connection and the supplicant driver is wext.  
In terminal, ndiswrapper -l still reports alternate driver is ath5k. Either there are other ath5k references or I have the wrong driver (net5211) for ndiswrapper.
iwconfig for wlan1 is the same as reported in the my previous posts.
I suspect the solution is closer but need to know what else to do.
My other notebook sees wireless stations in this condo complex, so there are signals to read.  Also, this wifi works in Vista so the hardware is ok.
I know this is like getting a hair cut over the phone, but if I can keep trying I know I win!
Thanks,
<> Jim

---

### Post by diamondjim08 on 2009-02-19
Codename,
After sudo ndiswrapper -e ath5K, system reports "couldn't delete /etc/ndiswrapper/ath5k
Makes some sense if ath5k is a madwifi driver, then it wouldn't be in the ndiswrapper directory?
Since I had previously installed madwifi thinking that would work, a search shows a bunch ath5k files in the directory:desktop/compat-wireless-2009-02-17/drivers/wireless.  This where I expanded the tar file when trying to install compat-wireless.  If I delete these files what awaits me? :-)
Thanks, <> Jim

---

### Post by Crafty Kisses on 2009-02-19
You need to try removing the "net5211" driver, and even possibly remove MadWifi and start from scratch, my guess is there are some conflicts between the drivers going on here, but here try the following command:
```
sudo ndiswrapper -e net5211.inf
```
Once that is removed, you can try my other method, but to my knowledge the net5211 driver is the correct driver for the Atheroes AR242X wireless card, if I'm wrong someone please correct me. I've given this driver out before to other people that were having issues with this card and it has worked.

---

### Post by Ketara on 2009-02-20
Net5211 is the correct driver.

ndiswrapper can be extremely finicky, it does not like other programs and other drivers playing with your card while it is doing anything.

I think Codename is right, the thing to do here is to delete the backports modules and the madwifi drivers and just start from scratch. That will be the easiest way to make sure that there isn't something messy going on.

---

### Post by diamondjim08 on 2009-02-20
Here is some new information re the driver & module:

Lspci -v says:
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device 0428
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f0200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ndiswrapper
	Kernel modules: ath5k
It would appear that there is a conflict here.  How do I resolve it?
Thanks,
<> Jim

---

### Post by Ketara on 2009-02-20
That is very weird, because mine is working properly with ndiswrapper, and the output is nearly identical.

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
Subsystem: Hewlett-Packard Company Device 137a
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at f2000000 (64-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>
Kernel driver in use: ndiswrapper
Kernel modules: ath5k, ath_pci

I have ath5k and ath_pci blacklisted and it works fine.

Jim, doublecheck hardware drivers and make sure everything is disabled, and doublecheck windows wireless drivers and make sure you have net5211.inf as the Atheros driver.

You might also look at network-manager. There was a guy two days ago who's Atheros card didn't work and we realized it was because Wicd for some reason didn't add wlan0 to his wireless interface tab in preferences.

---

### Post by Crafty Kisses on 2009-02-20
Hey there Diamond! Post the results of this command, I want to see if the drivers are even present:
```
sudo ndiswrapper -l
```

---

