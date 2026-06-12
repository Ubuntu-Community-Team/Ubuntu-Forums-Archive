---
title: "Dell Mini 9 - Hardy Heron - Broadcom Wireless Problem"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by littleHawk0107 on 2009-06-25
For Christmas, my wife and I gave my daughter a Dell Mini 9. She trusted me to make the decision regarding the Operating System. Considering security, speed & size, I opted to try Ubuntu hoping I could build on my very humble knowledge of Linux from work. For a couple of months, the world was good. Then, it happened... we lost the wireless connection. Since February, I have been pursuing this problem part-time. Unfortunately, my daughter is still without wireless, and my wife is almost out of patience. She is encouraging me to consider returning our Mini. So, here I am desperately in need of help...

Dell Mini 9

**Code Perspective**

```
lspci 
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
``````
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:d5:95:d7  
          inet addr:172.16.1.37  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::221:70ff:fed5:95d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4611638 (4.3 MB)  TX bytes:451243 (440.6 KB)
          Interrupt:220 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1028 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51784 (50.5 KB)  TX bytes:51784 (50.5 KB)

sms       Link encap:Ethernet  HWaddr 00:53:49:41:4e:4f  
          UP BROADCAST NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

``````
iwconfig
lo        no wireless extensions.

sms       no wireless extensions.

eth0      no wireless extensions.
``````
lsmod | grep 'wlan'
wlan                  249968  1 ath_pci
``````
dmesg | grep 'wlan'
[   36.963407] wlan: trunk
``````
sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
``````
lsb_release -d
Description:    Ubuntu 8.04.2
``````
uname -mr
2.6.24-24-lpia i686
```**GUI Perspective**

Network Settings
     ---used to display Wireless option beneath Connections tab but not *now*

NetworkManager Applet 0.7.0
     ---used to display Wireless networks in the area but not *now*

System > Administration > Hardware Drivers
     ---used to display Device driver: "wl"
     *---now* displays Device driver: "Broadcom STA wireless driver"
          ------box is checked for "Enabled"
          ------light is red for "Not in use"


I have continued to download updates through the wired connection in hopes that whatever was lost might be restored. Unfortunately, the updates have not resolved the problem. In fact, Dell support encouraged me to return the Mini to allow them to reinstall the OS suspecting the updates may have introduced the problem. I chose not to go that route hoping I could learn something instead from this esteemed group of Ubuntu Gurus...

---

### Post by snowpine on 2009-06-26
The terminal command 'sudo modprobe wl' should load the Broadcom wireless module, if not, any errors/output will be useful for solving the problem. (Copy and paste here)

As an aside: Many Dell users on these forums have complained about the timeliness and quality of updates with the special "Dellbuntu" pre-installed on the Mini. I personally deleted it within 15 minutes of purchasing my Mini, and never looked back. "Regular" Ubuntu 9.04 has full support for the Mini 9, and you are not dependant on Dell (a hardware manufacturer) for software updates: [http://ubuntumini.com/](http://ubuntumini.com/)

---

### Post by littleHawk0107 on 2009-06-27
**Long Term**

Thanks for the recommendation to transition from "Dellbuntu" to "regular" Ubuntu 9.04. As I do not have an external cd drive, I need to explore other methods for installation.

**Short Term**

Thanks for your help troubleshooting. 'sudo modprobe wl' did not generate any output in the terminal. However, when I checked...

System > Administration > Hardware Drivers
     *---*Device driver: "Broadcom STA wireless driver"
          ------box is checked for "Enabled"
          ------[COLOR=SeaGreen]*light changed to green for "In use"*[/COLOR]

Unfortunately, reviewing the other gui and code perspectives, I did not notice any changes. 

Any recommendations for the next step?

---

### Post by superprash2003 on 2009-06-27
also take a look at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by snowpine on 2009-06-27
Hi LittleHawk, that is a promising sign that you're able to load the wl driver without any errors. One really simple thing we can check is whether or not the wireless is disabled in bios. When you boot the computer, you can press 2 for the bios screen. Various hardware components can be enabled/disabled (to save power) so make sure that the wireless card is indeed enabled. If the card is enabled in and wl is loaded, it *should* appear when you use the iwconfig command. 

If you are not able to get wireless working using the Broadcom wl driver, Superprash's suggestion to use ndiswrapper is a good one. I have used the ndiswrapper method on other linux distros (never found it necessary with Ubuntu). Basically ndiswrapper allows you to use the Windows driver (you can download it from the Dell site) in Linux. ndisgtk is a graphical front end for ndiswrapper that makes things easy: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

ps If you decide to bail on Dellbuntu and install a different distro, you don't need an external CD drive, you can use a USB flash drive. There is an application called Unetbootin (available for Linux or Windows) that creates a Live USB device that works just like a Live CD. (On the Dell Mini, turn it on and press 0 to boot from the USB.) [http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by Ayuthia on 2009-06-27
Please post the results of:
```
lsmod
dmesg|grep -e wl -e eth
```It might be possible that there is a wireless module conflict.

Another option might be to install a newer version of the Broadcom STA module from the [Broadcom site]("http://http://www.broadcom.com/support/802.11/linux_sta.php").

---

### Post by littleHawk0107 on 2009-06-27
[B]Gurus...


superprash2003[/B]

Thanks for the suggestion. I will keep ndiswrapper in mind.


**snowpine**

Thanks for the info on the USB. In the meantime, two questions...

1) 'sudo modprobe wl' allows the Broadcom STA wireless driver to be "In use" for the current session. However, with every boot, I find that the driver returns to "Not in use." Can this command be coded to be automatic?

2) PhoenixBIOS > Advanced > WLAN Control: [Enabled]
Would this statement indicate that the wireless card is enabled?


**Ayuthia**

```
lsmod
Module                  Size  Used by
ath_pci               188972  0 
wlan                  249968  1 ath_pci
ath_hal               280288  1 ath_pci
parport_pc             36260  0 
ppdev                  10372  0 
parport                37704  2 parport_pc,ppdev
sms1xxx                42116  0 
mbm                     7424  0 
cdc_ether               7168  1 mbm
cdc_acm                18848  0 
uvcvideo               58116  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
rfcomm                 41232  2 
l2cap                  25600  13 rfcomm
hci_usb                16540  0 
bluetooth              60772  5 rfcomm,l2cap,hci_usb
i915                   32512  3 
acpi_cpufreq           10796  1 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5156  0 
drm                    82324  4 i915
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
snd_seq_midi            9376  0 
snd_seq_oss            35456  0 
snd_seq_dummy           4868  0 
snd_pcm_oss            42144  0 
snd_hda_intel         368304  2 
snd_seq_midi_event      8320  2 snd_seq_midi,snd_seq_oss
snd_rawmidi            25760  1 snd_seq_midi
snd_hwdep              10500  1 snd_hda_intel
snd_pcm                78596  2 snd_pcm_oss,snd_hda_intel
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq                54224  6 snd_seq_midi,snd_seq_oss,snd_seq_dummy,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_midi,snd_seq_oss,snd_seq_dummy,snd_rawmidi,snd_seq
snd                    56996  15 snd_seq_oss,snd_seq_dummy,snd_pcm_oss,snd_hda_intel,snd_rawmidi,snd_hwdep,snd_pcm,snd_mixer_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ieee80211_crypt_tkip    11520  0 
r8169                  34692  0 
ieee80211_crypt         6912  1 ieee80211_crypt_tkip
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
serio_raw               7940  0 
psmouse                68200  0 
fuse                   50324  3 
ahci                   28548  0 
squashfs               49032  0 
unionfs                73168  0 
ehci_hcd               37900  0 
usbhid                 32256  0 
hid                    38912  1 usbhid
isofs                  36132  0 
zlib_inflate           18176  2 squashfs,isofs
```
```
dmesg|grep -e wl -e eth
[   11.270326] Driver 'sd' needs updating - please use bus_type methods
[   11.270388] Driver 'sr' needs updating - please use bus_type methods
[   18.437784] eth0: RTL8102e at 0xf8868000, 00:21:70:d5:95:d7, XID 24a00000 IRQ 220
[   25.683532] r8169: eth0: link up
[   25.683560] r8169: eth0: link up
[   35.624786] eth0: no IPv6 routers present
[   37.374834] usbcore: registered new interface driver cdc_ether
[   38.013052] wlan: trunk
```Let me know if this code reveals a wireless module conflict...

---

### Post by Ayuthia on 2009-06-27
> **littleHawk0107 said:**
> 

Thanks for the info on the USB. In the meantime, two questions...

1) 'sudo modprobe wl' allows the Broadcom STA wireless driver to be "In use" for the current session. However, with every boot, I find that the driver returns to "Not in use." Can this command be coded to be automatic?

Try this:
```
echo wl | sudo tee -a /etc/modules
```This command will add the wl module to load when the system boots.

> 2) PhoenixBIOS > Advanced > WLAN Control: [Enabled]
Would this statement indicate that the wireless card is enabled?It does mean that the wireless card is on provided that the proper drivers are loaded.

```
lsmod
Module                  Size  Used by
ath_pci               188972  0 
wlan                  249968  1 ath_pci
ath_hal               280288  1 ath_pci
ieee80211_crypt_tkip    11520  0 
ieee80211_crypt         6912  1 ieee80211_crypt_tkip

```
This shows that you have an Atheros module loaded along with the encryption modules for the Broadcom card.

If you do:
```
sudo modprobe wl
```does your wireless card work?

---

### Post by snowpine on 2009-06-27
> **littleHawk0107 said:**
> 
**snowpine**

Thanks for the info on the USB. In the meantime, two questions...

1) 'sudo modprobe wl' allows the Broadcom STA wireless driver to be "In use" for the current session. However, with every boot, I find that the driver returns to "Not in use." Can this command be coded to be automatic?

2) PhoenixBIOS > Advanced > WLAN Control: [Enabled]
Would this statement indicate that the wireless card is enabled?



1) add wl to your /etc/modules file ('sudo nano /etc/modules' or 'gksu gedit /etc/modules')

2) looks good, I guess that wasn't the problem (always good to check the simple things)

3) the ath_pci module looks suspicious, since you have a broadcom card, not atheros. Try 'sudo rmmod ath_pci ath_hal'

---

### Post by Brandon Williams on 2009-06-27
When you ran 'lshw -C network', it did not give any indication that there was a driver associated with the network interface. Does the output from the command change after loading the wl driver? Specifically, does it still say 'UNCLAIMED'? And does the configuration line indicate that the device is associated with the wl module?

Also, after loading the wl module, if the card does associate with the module and stop saying 'UNCLAIMED' in the lshw output, you should check that the radio is on, that network-manager is running, and that wireless is not disabled in network-manager.

To check wifi status on the mini with Dellbuntu:
```
$ sudo /usr/bin/aircraft-manager-util WIFI status
	Status WIFI
status = 17
Wifi on
```

To check whether network-manager is running:
```
~$ ps -C NetworkManager -C nm-applet
  PID TTY          TIME CMD
 4638 ?        00:00:02 NetworkManager
 4898 ?        00:00:03 nm-applet
```
There should be a line for both NetworkManager and nm-applet.

And to check whether wireless is disabled in network-managee (assuming that NetworkManager is running):
```
$ sudo dbus-send --system --type=method_call --print-reply --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager  org.freedesktop.DBus.Properties.Get string:org.freedesktop.NetworkManager string:WirelessEnabled
method return sender=:1.5 -> dest=:1.50 reply_serial=2
   variant       boolean true
```

Some of the above assumes that you are running a fully up-to-date Dellbuntu with aircraft-manager installed. It sounds like this is probably true.

---

### Post by littleHawk0107 on 2009-06-29
[B]Gurus...

Ayuthia, snowpine & Brandon Williams,[/B]

Joy! :guitar:

Following...

```
sudo rmmod ath_pci ath_hal
sudo modprobe wl
```Wireless is restored! Conflict resolution is good. Many, many, many thanks!

Next step... automation. I have the code to add wl to /etc/modules, but how do I automate 'sudo rmmod ath_pci ath_hal'?

---

### Post by snowpine on 2009-06-29
Great news!

I am not 100% sure it's the same in Ubuntu, but in Debian, I would add the unwanted modules (ath_pci and ath_hal) to /etc/modprobe.d/blacklist.conf.

Glad you got it working. :)

---

### Post by Ayuthia on 2009-06-29
It is the same.  You might also want to make sure that the ath_pci module is not in /etc/modules.  If it is, it should be removed.

---

### Post by littleHawk0107 on 2009-06-29
**snowpine & Ayuthia,**

Regarding automation...

1) I checked /etc/modules to make sure ath_pci module was not there. 

2) When I did not find "/etc/modprobe.d/blacklist.conf," I created the file. To this file, I added...

```
blacklist ath_pci
blacklist ath_hal
```When this approach did not remove the mods automatically, I removed the file and appended "/etc/modprobe.d/blacklist" with the same commands as above. Unfortunately, this did not work either. Is my syntax wrong?

---

### Post by snowpine on 2009-06-29
Try removing the word 'blacklist'?

```
ath_pci
ath_hal
```

---

### Post by Ayuthia on 2009-06-29
You are using Hardy so using /etc/modprobe.d/blacklist is the correct option.  It looks like you might need to also blacklist wlan.  It looks like ath_pci needs to have ath_hal and wlan.  Once you add it to the blacklist, you can try the following:
```
sudo modprobe -r ath_pci ath_hal wlan
sudo modprobe wl
sudo update-initramfs -u
```

The last command will update the initramfs file that is used when the system is booting.  Sometimes it could be loading the ath_pci module before the blacklist file is read.  However, initramfs has its own blacklist file which can be updated by using the update-initramfs command.

Hopefully that will do it.

By the way, you will need to keep the blacklist in front of those modules.  Without them, the blacklist file will spit out errors.

---

### Post by littleHawk0107 on 2009-09-10
My daughter enjoyed internet access for a while. She manually typed the necessary commands we discovered as I had difficulty automating the commands. Unfortunately, a few days later, she encountered difficulty once again. When I checked...
System > Administration > Hardware Drivers. I received the following message, "No proprietary drivers are in use on this system." Sometimes this message would appear while at other times the Broadcom STA wireless driver would be available. 

Obviously, some time has passed since last we investigated this issue, but my schedule has finally allowed me to return to troubleshooting. Any recommendations?

---

### Post by Ayuthia on 2009-09-18
> **littleHawk0107 said:**
> My daughter enjoyed internet access for a while. She manually typed the necessary commands we discovered as I had difficulty automating the commands. Unfortunately, a few days later, she encountered difficulty once again. When I checked...
System > Administration > Hardware Drivers. I received the following message, "No proprietary drivers are in use on this system." Sometimes this message would appear while at other times the Broadcom STA wireless driver would be available. 

Obviously, some time has passed since last we investigated this issue, but my schedule has finally allowed me to return to troubleshooting. Any recommendations?

Can you check the following:
```
lsmod|grep wl
```If it is there and loaded, it should provide a result.

```
modprobe -l|grep wl
```Once again, if it exists, it will show up.  If it does not, we will need to see how we can activate the wl module again.

---

### Post by littleHawk0107 on 2009-09-18
Following...

```
sudo rmmod ath_pci ath_hal wlan
sudo modprobe wl
```and...

```
lsmod|grep wl
```the results...

wl                   1487188  0 
ieee80211_crypt         6912  2 wl,ieee80211_crypt_tkip

Following...

```
modprobe -l|grep wl
```the results...

/lib/modules/2.6.24-24-lpia/madwifi/wlan_tkip.ko
/lib/modules/2.6.24-24-lpia/madwifi/wlan_scan_sta.ko
/lib/modules/2.6.24-24-lpia/madwifi/wlan_acl.ko
/lib/modules/2.6.24-24-lpia/madwifi/wlan_wep.ko
/lib/modules/2.6.24-24-lpia/madwifi/wlan_scan_ap.ko
/lib/modules/2.6.24-24-lpia/madwifi/wlan_ccmp.ko
/lib/modules/2.6.24-24-lpia/madwifi/wlan_xauth.ko
/lib/modules/2.6.24-24-lpia/madwifi/wlan.ko
/lib/modules/2.6.24-24-lpia/kernel/net/ipv4/ipvs/ip_vs_wlc.ko
/lib/modules/2.6.24-24-lpia/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-24-lpia/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-24-lpia/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko
/lib/modules/2.6.24-24-lpia/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_rc80211_simple.ko
/lib/modules/2.6.24-24-lpia/ubuntu/wireless/marvell/8686_wlan/sd8686.ko
/lib/modules/2.6.24-24-lpia/ubuntu/wireless/marvell/8688_wlan/8688_a2.ko
/lib/modules/2.6.24-24-lpia/volatile/wl.ko

---

### Post by Ayuthia on 2009-09-19
The only thing that I can think of that would cause the Broadcom STA module to disappear is if there was a kernel update.  I am not for sure if Hardy had an update recently or not.

If you want to try to automate the steps, you can try adding the commands to /etc/rc.local.  You can edit that file by doing the following:
```
gksu gedit /etc/rc.local
```and add the following before the exit 0 line:
```
rmmod ath_pci ath_hal wlan
modprobe wl
```

As for the reason why this is happening, I am not for sure.  As far as I know, the Atheros modules should not be loading on your system because it does not have that card installed.  For some reason, this netbook wants to keep on using it.

The Hardware Drivers application does occasionally report things incorrectly.  I usually like to check the system by using the lsmod and modprobe -l commands to verify that the modules are still there.  There have been occasions where the system does not automatically start up the restricted modules also so Broadcom STA module does not appear.

Hardy was the introduction to the Hardware Drivers and the Broadcom STA module.  That wireless module was made for that card but of course it was the first release of it so this driver is still being improved upon.

Hopefully the rc.local script will help you out.

---

### Post by littleHawk0107 on 2009-09-19
I revised rc.local...

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod ath_pci ath_hal wlan
modprobe wl

exit 0

How do I change the execution bits?

---

### Post by Ayuthia on 2009-09-19
> **littleHawk0107 said:**
> I revised rc.local...

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod ath_pci ath_hal wlan
modprobe wl

exit 0

How do I change the execution bits?

You should not need to change it because it is called while the system is loading so it will be run as root.  So as long as:
```
ls -l /etc/rc.local
```shows something like:
```
-rwxr-xr-x 1 root root 306 Aug  3 14:15 rc.local
```
You should not need to do anything.  If it does not show -rwxr-xr-x, you can do the following:
```
sudo chmod 755 /etc/rc.local
```and that should fix it.

---

### Post by littleHawk0107 on 2009-09-28
I was afraid you were going to say that... The permissions are set appropriately, yet for some reason, these commands do not seem to be automating. For example, after booting, ath_pci, ath_hal & wal are still visible with lsmod.

---

### Post by Ayuthia on 2009-09-28
> **littleHawk0107 said:**
> I was afraid you were going to say that... The permissions are set appropriately, yet for some reason, these commands do not seem to be automating. For example, after booting, ath_pci, ath_hal & wal are still visible with lsmod.

Can you do me a favor and post the /etc/modules file?  It is strange that the two files are still loading even after the /etc/rc.local command.  From what I understand, the rc.local file is run after all the kernel modules are loaded.  Also, can you change the rmmod to modprobe -r in /etc/rc.local?  I doubt that it will change anything, but it should not hurt anything.

---

