---
title: "HELP with Ralink 3070/Monoprice USB 802.11G!"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by nightmicu on 2010-01-11
I have been trying for the past two hours to try and connect to a wireless network using a Monoprice USB 802.11G adapter with no luck. I am running a 64 bit distro of Ubuntu 9.10

The packaging advertises Linux compatibility, and Ubuntu 9.10 does recognize that a wireless device is present, but the wireless network is not being displayed in the drop-down network menu.

When I ran lsusb in Terminal, it shows the device as 148f:3070, Ralink Technology, Corp. I have spoken with several Monoprice tech support agents and only one knew the first thing about Linux, telling me that it used the 2870 chipset. I followed the instructions from this thread: [http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593) and the network is still not displayed. Also, after following the instructions there, it mentions something about 3070 -- does that mean I was misinformed by the agent? If so, are there drivers/instructions available for that device?

Here is a link to the product page for this USB adapter: [http://www.monoprice.com/products/product.asp?c_id=105&cp_id=10501&cs_id=1050105&p_id=5336&seq=1&format=2](http://www.monoprice.com/products/product.asp?c_id=105&cp_id=10501&cs_id=1050105&p_id=5336&seq=1&format=2)

Time is a factor, I am trying to setup my fiance's college computer by the morning... her dorm only appears to have WiFi access working and this is on a desktop.

---

### Post by chili555 on 2010-01-11
I think this is supposed to work with a driver already in the kernel!! Please open a terminal and do:```
sudo modprobe rt2800usb
```Does it spring to life? If not, please run:```
dmesg | tail 
lsmod | grep rt2
```Post the results.

---

### Post by nightmicu on 2010-01-11
Here are the details.... suggestion does not appear to have worked.

[   14.824134] CPU0 attaching NULL sched-domain.
[   14.824141] CPU1 attaching NULL sched-domain.
[   14.851339] CPU0 attaching sched-domain:
[   14.851344]  domain 0: span 0-1 level MC
[   14.851346]   groups: 0 1
[   14.851352] CPU1 attaching sched-domain:
[   14.851353]  domain 0: span 0-1 level MC
[   14.851355]   groups: 1 0
[   36.186223] ISO 9660 Extensions: Microsoft Joliet Level 3
[   36.203606] ISOFS: changing to secondary root

lsmod-
rt2800usb              40800  0 
rt2x00usb              13600  1 rt2800usb
rt2x00lib              34624  2 rt2800usb,rt2x00usb
led_class               5256  1 rt2x00lib
input_polldev           4720  1 rt2x00lib
mac80211              209912  2 rt2x00usb,rt2x00lib
cfg80211              109144  2 rt2x00lib,mac80211
crc_ccitt               2336  1 rt2800usb

---

### Post by nightmicu on 2010-01-12
Anyone have any other ideas? Could this be another 9.10 64 bit compatibility issue? I'm also confused because this appears to be a 3070 chipset and everyone is giving me instructions for 28xx or what have you.

Nothing I do seems to change anything, still shows that there is a wireless device connected but will not display the network in the list.

---

### Post by chili555 on 2010-01-12
> still shows that there is a wireless device connectedI am not quite sure what you mean here. Do you mean that the Network Manager icon doesn't show any networks when you click on it? Please see attached.

Let's see:```
iwconfig
dmesg | grep rt2
```Thanks. Do you have a wired ethernet connection going at the same time? If so, please disconnect the wire, reboot and let us know if the performance improves.

---

### Post by nightmicu on 2010-01-12
Okay, reinstalled with Ubuntu 9.10 32 bit, hoping that this may be yet another issue I've been having with 64 bit. No such luck, however I have not yet attempted to install drivers... before I attempted to install rt2800 drivers and it would not work.

The network manager drop-down in the notification area shows the Wireless Networks label but it does not list available networks, simply says Disconnected. When the USB module is removed, "Wireless Networks" disappears from the list.

Here is the output of the commands you requested:

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

dmesg | grep rt2
```
[   74.314796] Registered led device: rt2800usb-phy0::radio
[   74.314809] Registered led device: rt2800usb-phy0::assoc
[   74.314821] Registered led device: rt2800usb-phy0::quality
[   74.315140] usbcore: registered new interface driver rt2800usb
[   74.348754] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   74.351893] usbcore: registered new interface driver rt2870
[   74.381774] Error: Driver 'rt2870' is already registered, aborting...
[   74.381778] usbcore: error -17 registering interface     driver rt2870
[   74.473557] rt2800usb 1-6:1.0: firmware: requesting rt2870.bin
```

Thanks for your help on this... took the machine home for the remainder of the week so I can work on debugging this

---

### Post by nightmicu on 2010-01-12
Okay, an update - just put the USB ID in Google and I found this thread: [http://osdir.com/ml/linux-wireless/2009-10/msg00438.html](http://osdir.com/ml/linux-wireless/2009-10/msg00438.html)
Could this be a problem with 9.10? I am not entirely a newbie but things like this just totally confuse me, line after line of command output in Terminal.

---

### Post by chili555 on 2010-01-12
> **nightmicu said:**
> Okay, an update - just put the USB ID in Google and I found this thread: [http://osdir.com/ml/linux-wireless/2009-10/msg00438.html](http://osdir.com/ml/linux-wireless/2009-10/msg00438.html)
Could this be a problem with 9.10? I am not entirely a newbie but things like this just totally confuse me, line after line of command output in Terminal.It seems like a different problem to me. I think maybe the modules rt2800usb and rt2870sta are fighting each other:> [   74.314796] Registered led device: rt2800usb-phy0::radio
[   74.314809] Registered led device: rt2800usb-phy0::assoc
[   74.314821] Registered led device: rt2800usb-phy0::quality
[   74.315140] usbcore: registered new interface driver rt2800usb
[   74.348754] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   74.351893] usbcore: registered new interface driver rt2870
[   74.381774] Error: Driver 'rt2870' is already registered, aborting...
Let's blacklist rt2800usb by doing:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a single line:```
rt2800usb
```Proofread, save and close gedit. Reboot and see if the wireless sees networks and connects.

---

### Post by nightmicu on 2010-01-12
> **chili555 said:**
> Let's blacklist rt2800usb

THAT DID IT!!! FINALLY!! Thank you VERY much for your help and patience, I am off to share the solution with Monoprice Tech Support. They're really nice folks over there, just not very Linux savvy.

Thanks again!

---

### Post by chili555 on 2010-01-12
For the benefit of the searchers, here is the issue. This device has the vendor and product code, or pciid of 148f:3070, as shown in the original post. Both the module rt2800usb:> modinfo rt2800usb | grep 3070
--- snip ---
alias:          usb:v[COLOR="Blue"]148F[/COLOR]p[COLOR="Blue"]3070[/COLOR]d*dc*dsc*dp*ic*isc*ip*As well as the module rt2870sta:> modinfo rt2870sta | grep 3070
--- snip ---
alias:          usb:v[COLOR="Blue"]148F[/COLOR]p[COLOR="Blue"]3070[/COLOR]d*dc*dsc*dp*ic*isc*ip**Both* claim the device! One has to be blacklisted for the device to work correctly. I have read suggestions elsewhere that rt2870sta is the module that should be blacklisted. I believe you should first try blacklisting rt2800usb and, if you are not successful, try the other.

---

### Post by alof8k on 2010-03-21
THANK YOU!!!!

I have been pulling the hair off my head for the past 24 hours trying to figure out why my ebay bought RALink wifi usb card was not working.  Just like the above poster, mines was detected but could not detect any access points.  

But blacklisting the rt2800usb module (and then rebooting) did the trick!

---

### Post by nightmicu on 2010-03-22
> THANK YOU!!!!

I have been pulling the hair off my head for the past 24 hours trying to  figure out why my ebay bought RALink wifi usb card was not working.   Just like the above poster, mines was detected but could not detect any  access points.  

But blacklisting the rt2800usb module (and then rebooting) did the  trick! 	

Woohoo! I was very frustrated by this as well. Hopefully the manufacturer of the USB WiFi adapter I bought wrote down this solution when I told them about it, they advertised Linux support on the packaging but did not seem to know how to make it work lol

---

### Post by alof8k on 2010-03-28
Feeling a little adventurous, I've installed a fresh copy of lucid beta 1 on the system.  This time I have tried to blacklist the rt2800usb module but for some reason the wifi would not connect to my router.  It seems the card is detected and queries for a list of wifi connections near me (and detects my router) but does not connect when putting in my WPA password.

Anyway know what's going on?

---

### Post by chili555 on 2010-03-28
Betas are sorta like that!

You could look around in /var/log/syslog and try to figure out what's going wrong:```
sudo tail -n50 /var/log/syslog
```I believe there is a specific forum here for Lucid: [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

---

### Post by alof8k on 2010-03-31
> **chili555 said:**
> Betas are sorta like that!

You could look around in /var/log/syslog and try to figure out what's going wrong:```
sudo tail -n50 /var/log/syslog
```I believe there is a specific forum here for Lucid: [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

I found the solution! 

Well actually it's more of a work around, but a very simple one.  According to [this launchpad bug discussion]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524867") , it seems that the driver in lucid only connects to WPA2 and not WPA.  So I logged into my router's admin panel and switched the security from WPA+WPA2 to just WPA2.  The mixed environment caused the connection issue.

---

### Post by w2vy on 2010-07-24
Also works for Sabrent USB-G802 ($21 inclding shipping!)

Did not like my 128bit WEP; I may need to update all the devices anyway.

All these wireless devices need a common security...

I'll try WPA2 as noted above...

---

### Post by mattisking on 2010-07-29
Thanks a lot guys. This also worked for me with a generic USB 802.11n device (RT3070). Once I blacklisted rt2800usb I was good to go.

---

### Post by 130s on 2010-08-02
Hi all,

I have similar problem using MWN-USB 150N WIRELESS N ADAPTER and still can't
get it work on my linux machine. I'd appreciate if someone think of any solutions.

I'm using Redhat, not ubuntu, I understand this post might not be suitable for this site. But since the phenomenon is similar, I'm just trying to see someone has suggestions.

- Problematic phenomenon
While at building the driver,
> 
[robot@localhost linux]$ sudo /sbin/insmod rt3070sta.ko 
insmod: error inserting 'rt3070sta.ko': -1 Unknown symbol in module
- Workaround tried already
sudo emacs /etc/modprobe.d/blacklist.conf
added "rt2800usb" and "rt2870sta", and rebooted.

- Addtional platform info. that someone in this thread previously asked to the questioner

> 
[robot@localhost RT3070_LinuxSTA_V2.3.0.1_20100208]$ dmesg | tail
i2c-adapter i2c-1: unable to read EDID block.
pci 0000:00:02.0: LVDS-1: no EDID data
type=1400 audit(1280779678.001:5): avc:  denied  { read } for  pid=1744 comm="kdm" name=".Xauthority" dev=dm-0 ino=11278 scontext=system_u:system_r:xdm_t:s0-s0:c0.c1023 tcontext=system_u:object_r:user_home_dir_t:s0 tclass=file
type=1400 audit(1280779678.002:6): avc:  denied  { unlink } for  pid=1744 comm="kdm" name=".Xauthority" dev=dm-0 ino=11278 scontext=system_u:system_r:xdm_t:s0-s0:c0.c1023 tcontext=system_u:object_r:user_home_dir_t:s0 tclass=file
i2c-adapter i2c-0: unable to read EDID block.
pci 0000:00:02.0: VGA-1: no EDID data
i2c-adapter i2c-0: unable to read EDID block.
pci 0000:00:02.0: VGA-1: no EDID data
i2c-adapter i2c-1: unable to read EDID block.
pci 0000:00:02.0: LVDS-1: no EDID data
> 
[robot@localhost RT3070_LinuxSTA_V2.3.0.1_20100208]$ lsmod | grep rt3
[robot@localhost RT3070_LinuxSTA_V2.3.0.1_20100208]$ lsmod | grep rt2
(No result shown for both)
- Platform
Linux version 2.6.29.4 (root@localhost) (gcc version 4.4.1 20090725
(Red Hat 4.4.1-2) (GCC) ) #1 SMP Wed Aug 26 17:44:01 EDT 2009

---

### Post by w2vy on 2010-08-02
> **130s said:**
> 

[robot@localhost linux]$ sudo /sbin/insmod rt3070sta.ko
insmod: error inserting 'rt3070sta.ko': -1 Unknown symbol in module 

It says "Unknown Symbol" the module is not linking properly.
It is looking for a function that is not included.

Maybe you do not have the make file configured properly for the right target?

tough one

tom

---

### Post by jimmybarcelona on 2010-10-27
So this post as gotten me closer, but still no go. I started off with the Ralink 3070 usb stick. The computer would see the wireless, but no networks. I blacklisted rt2800usb and restarted. I can now see my home wireless network. I just can't connect to it. The only difference I can see is that i'm running kubuntu 10.04 instead of ubuntu. Should this change anything? I can see the network, it's signal strength, everything. Why can't I connect to it?

---

### Post by nightmicu on 2010-10-27
> **jimmybarcelona said:**
> So this post as gotten me closer, but still no go. I started off with the Ralink 3070 usb stick. The computer would see the wireless, but no networks. I blacklisted rt2800usb and restarted. I can now see my home wireless network. I just can't connect to it. The only difference I can see is that i'm running kubuntu 10.04 instead of ubuntu. Should this change anything? I can see the network, it's signal strength, everything. Why can't I connect to it?

Not sure if this might be your problem or not, I was a complete novice when I experienced this issue. Be sure that you have exactly "blacklist rt2800usb" in the file. Kubuntu should not make any difference.

-Ben

---

### Post by jimmybarcelona on 2010-10-29
> **nightmicu said:**
> Not sure if this might be your problem or not, I was a complete novice when I experienced this issue. Be sure that you have exactly "blacklist rt2800usb" in the file. Kubuntu should not make any difference.

-Ben

Double checked, it's in there correctly. I tried blacklisting the rt2870sta driver instead of this one, and that didn't work either. 
I'm sure that I blacklisted this driver correctly, though, because before I blacklisted it I couldn't find any networks. Now I can see my home wireless network, I just cannot connect to it. 

I'm wondering if it's a kubuntu issue. My network is visible in knetworkmanager. When I try and click on it I don't get an unable to connect message or anything of the sort. When I click on it to connect, nothing happens at all. It doesn't even try to connect. Any ideas?

---

### Post by jimmybarcelona on 2010-10-29
UPDATE: 
I boot from a ubuntu live cd, and the stick just works. It's something with kubuntu. At least now I have more of a direction to go in.

---

### Post by clemens.caspar on 2010-12-14
> **nightmicu said:**
> I have been trying for the past two hours to try and connect to a wireless network using a Monoprice USB 802.11G adapter with no luck. I am running a 64 bit distro of Ubuntu 9.10

The packaging advertises Linux compatibility, and Ubuntu 9.10 does recognize that a wireless device is present, but the wireless network is not being displayed in the drop-down network menu.

When I ran lsusb in Terminal, it shows the device as 148f:3070, Ralink Technology, Corp. I have spoken with several Monoprice tech support agents and only one knew the first thing about Linux, telling me that it used the 2870 chipset. I followed the instructions from this thread: [http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593) and the network is still not displayed. Also, after following the instructions there, it mentions something about 3070 -- does that mean I was misinformed by the agent? If so, are there drivers/instructions available for that device?

Here is a link to the product page for this USB adapter: [http://www.monoprice.com/products/product.asp?c_id=105&cp_id=10501&cs_id=1050105&p_id=5336&seq=1&format=2](http://www.monoprice.com/products/product.asp?c_id=105&cp_id=10501&cs_id=1050105&p_id=5336&seq=1&format=2)

Time is a factor, I am trying to setup my fiance's college computer by the morning... her dorm only appears to have WiFi access working and this is on a desktop.
Hey, I use an Edimax 77711UAn, with a RT3070 chipset (as far as I understand the manual), in  Maverick Meerkat environment.
The command sudo modprobe rt2800usb help me installing the stick without further action (well, I had th enter the key-phrase in the network setup).
Thanks!
Clemens

---

### Post by clemens.caspar on 2010-12-14
Hey, I use an Edimax 77711UAn, with a RT3070 chipset (as far as I understand the manual), in  Maverick Meerkat environment.
The command sudo modprobe rt2800usb help me installing the stick without  further action (well, I had th enter the key-phrase in the network  setup).
Thanks!
Clemens

---

