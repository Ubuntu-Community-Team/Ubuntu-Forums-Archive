---
title: "rtl8187se on ubuntu 9.10 karmic"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by maddocks on 2009-12-03
So i quickly learned with my new windbook that the module rtl8187se that comes stock with the 9.10 karmic install does not work with wpa. There are a couple of different modules source for this card online. one being on google code here [http://code.google.com/p/msi-wind-linux/](http://code.google.com/p/msi-wind-linux/) another i guess being put out by realtek themselves, and there a package called rtl8187se-source which I assume is one of the 2 mentioned. The problem is none of these will compile correctly. Heres what i found for a reason why;

"rtl8187se uses wireless extensions so it needs to depend on
WIRELESS_EXT (or select it).

rtl8187se uses fields in struct net_device that are only present
if CONFIG_COMPAT_NET_DEV_OPS=y, so it needs to depend on
that symbol also."

This is the partial reason why it wont compile Kconfig makes no mention of COMPAT_NET_DEV_OPS but it does list WIRELESS_EXT so we go into /usr/src/linux-headers-2.6.31-15/drivers/staging/rtl8187se/Kconfig and change it to read;

config RTL8187SE
 	tristate "RealTek RTL8187SE Wireless LAN NIC driver"
 	depends on PCI
	depends on WIRELESS_EXT && COMPAT_NET_DEV_OPS
 	default N
 	 

now both driver sources get a little bit further but eventually die with 

error: ‘struct net_device’ has no member named ‘foo’

replace foo with a bunch of different things open, stop, tx_timeout  etc. etc. all inside of r8180_core.c which im not sure but i think its compiling sources for a couple different make/models of realtek cards, and if thats true and r8180 is for a different card i dont care about maybe i can convince it to ignore that driver. Any ideas on how to get the rtl8187se working with WPA without using ndiswrapper would be greatly appreciated. thank you

---

### Post by puppywhacker on 2009-12-03
In the earlier ubuntu's I compiled the drivers from a pathed r8180 driver. They apparently are closely related. Since Ubuntu 9.10 the native driver is included and detected automatically. I do not encrypt my wireless link. I do know that the driver uses the ieee80211, which is nowadays the default subsystem by linux, it does support WPA and I noted somewhere that it can use one of the following modules

```
modprobe ieee80211_crypt_tkip-rtl
modprobe ieee80211_crypt_ccmp-rtl

```

It is than the wpa_supplicant that can be used on the commnandline to initiate WPA.

---

### Post by maddocks on 2009-12-03
i had tried to modprobe the ieee80211 modules in my never ending attempts to get this to work, but i never tried or even thought of using wpa_supplicant from cli to get it to work. Why would it work from cli but via nm-applet? is this something that can be fixed, or jerry rigged to work? i know the repos have a gui for wpa_supplicant and im not even a gui kinda guy but when it comes to my wireless connections i simply want it to work. I dont want to have to type commands etc. But alas if its my only way. Any ideas on how to make the module source compile? i hear the driver i mentioned in the 1st post from google code works perfect with nm-applet supports monitor mode etc. I think(hope) someone who knows more then me about compiling, wireless, etc. might be able to figure it out easily.

---

### Post by northd_tech on 2009-12-04
Hi maddocks.  

In all my gesticulating trying to get a working Realtek 8192E PCI wireless interface under Karmic Koala 9.10 64-bit (AMD DuoCore CPUs), both the 8187SE and 8192SE wireless chipsets have come up. 

You might have some luck by reviewing the following threads, and the "SE" seems to be much different than the "E" version (as are the 32-bit and 64-bit sourcecode & firmware, but I've gotten all of them to compile under 64-bit with enough header packages installed, so just because it compiles does not mean that the wireless will work).  

This is probably your best bet- see chili555's method at post #2 here:  
[http://ubuntuforums.org/showthread.php?t=1329254](http://ubuntuforums.org/showthread.php?t=1329254)

The [32-bit version? of the] rtl8192se module sourcecode is available at post #6 here:  
[http://swiss.ubuntuforums.org/showpost.php?p=8402327&amp;postcount=6](http://swiss.ubuntuforums.org/showpost.php?p=8402327&amp;postcount=6)

Also see the following threads if you have no luck there:
[http://ubuntuforums.org/showthread.php?t=1239342](http://ubuntuforums.org/showthread.php?t=1239342)

[http://ubuntuforums.org/showthread.php?t=1313997](http://ubuntuforums.org/showthread.php?t=1313997)

[http://swiss.ubuntuforums.org/showthread.php?p=8239705](http://swiss.ubuntuforums.org/showthread.php?p=8239705)

[http://ubuntuforums.org/showthread.php?t=1281536](http://ubuntuforums.org/showthread.php?t=1281536)

[http://ubuntuforums.org/showthread.php?t=1191590](http://ubuntuforums.org/showthread.php?t=1191590)

---

### Post by freechelmi on 2009-12-29
Hello using SE on 9.10, it works Out of the box BUT using WPA it constantly loose connection or drop below 1 Mbps ... So unusable , I'm stil looking for a solution, ndiswrapper did not really worked

---

### Post by garryknight on 2009-12-29
My Advent 4211-B, which is an MSI Wind clone, has an RTL8187SE which has worked with WPA since I installed Kubuntu 9.04 and has stayed working since upgrading to 9.10. It never loses the connection unless I go out of range, and the speed only seems to be dependent on a) how far I am from the wifi source, and b) how bogged down with traffic that particular wifi hotspot is. At home it works perfectly, picking up the SSID and auto-connecting every time whether I've booted up with the wifi card switched on or whether I switch it on after logging in; and the connection seems to stay stable all day, too. Even when my EeePC refuses to connect because the wireless router has thrown a hissy fit and needs to be rebooted, the Advent still grabs a connection.

Not much help, I know, but I think you stand a good chance of getting it working eventually. It's also fairly easy to swap out the existing wifi card for another one, though if it's not a half-height card you might have to remove the standoff.

---

### Post by freechelmi on 2010-01-17
Hello & thanks

Seeing someone where it works pretty well should help spot what's going wrong. I Guess you did not make anything special with your configuration. 

I reinstalled karmic from scratch, and as it was still giving a lot of problems, I gave Ndiswrapper another try. This time I got the MSI wifi Windows driver that seems to be the same than realtek , but for now it works really great. 


I'm sad to use Ndiswrapper because it is usually a source of problems such as Hibernate failure & so on ....

---

