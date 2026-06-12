---
title: "D-Link DWA-140 / Ralink 2870"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by Drewkman on 2010-04-08
I've inherited an oldish XP PC and am attempting to revitalise it with an Ubuntu installation. I have never really used Linux before now and everything so far has been painless-ish. But configuring the wireless has been a total nightmare!

The PC originally had a D-Link PCI card which for the life of me I could not get to work, at all. No respoonse, no lights, no recognition by Ubuntu. I tried and failed many times to get ndiswrapper up and running. I gathered that the chipset for this particular card was quite awkward in Linux and considering that it was quite old, I decided I might as well get a new, more convenient USB wireless n adapter. I found a page of wireless cards and adapters which worked out of the box in Ubuntu.

So now here I am with my D-Link DWA-140 which I was informed would 'just work', running into nothing but dead ends and once again trying and failing to configure ndiswrapper as a last resort. I'm extremely frustrated and frankly can't believe how a fairly popular OS can be so outrageously incompetent when it comes to increasingly ubiquitous technologies like WiFi in the modern world. I want to love Linux, but it's not making it easy for me. ](*,)

Any nuggets of advice?

---

### Post by chili555 on 2010-04-08
First, you probably don't need ndiswrapper. Second, the most common issue is two or more conflicting drivers loading, which is fixed fairly easily with blacklisting.

May we please see:```
lsmod | grep -e ndis -e rt2
ls /etc/modprobe.d | grep -e ndis -e black
```Thanks.

---

### Post by alliance1975 on 2010-04-08
I am having the same nightmare with my railink 2870 usb dongle and will parallel your efforts to get to a solution.

---

### Post by chili555 on 2010-04-08
> **alliance1975 said:**
> I am having the same nightmare with my railink 2870 usb dongle and will parallel your efforts to get to a solution.How about posting the same details?

---

### Post by alliance1975 on 2010-04-08
Will do so this evening. I feel hope once again.

---

### Post by Drewkman on 2010-04-08
Thanks chili555 - I hope it is easy to fix as you say. I've got:

andrew@ubuntu-desktop:~$ lsmod | grep -e ndis -e rt2
andrew@ubuntu-desktop:~$ ls /etc/modprobe.d | grep -e ndis -e black
blacklist
blacklist-ath_pci.conf
blacklist.conf
blacklist.conf~
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf
ndiswrapper

---

### Post by chili555 on 2010-04-08
So, neither the native driver nor ndiswrapper are getting loaded. Let's take the easy way out:```
sudo modprobe ndiswrapper
iwconfig
```Was a wireless interface created? Can you connect?> [COLOR="Red"]blacklist[/COLOR]
blacklist-ath_pci.conf
[COLOR="Red"]blacklist.conf[/COLOR]
blacklist.conf~
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf
ndiswrapper 

Also, you do not need both a blacklist and blacklist.conf file. Let's consolidate. Open a terminal and do:```
cat /etc/modprobe.d/blacklist
```Leave that terminal open and open a new one and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Transfer all the listings in *blacklist* to *blacklist.conf*. Proofread carefully, twice. Save and close gedit. Now do:```
sudo rm /etc/modprobe.d/blacklist
```If the procedure above produces any errors or does not start your wireless, please post:```
lsusb
```Thanks.

---

### Post by Drewkman on 2010-04-08
Thanks - I followed all those instructions. No luck though; I just get 'no wireless extensions for 'lo' and 'eth0'. No wlan entry. The actual USB adapter isn't showing any signs of life either.


andrew@ubuntu-desktop:~$ lsusb
Bus 002 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07d1:3c0a D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by alliance1975 on 2010-04-08
I performed the commands as recommended. The first set is with the usb unconnected.

```
chris@hpdv5k:~$ lsmod | grep -e ndis -e rt2
chris@hpdv5k:~$ ls /etc/modprobe.d | grep -e ndis -e black
blacklist-ath_pci.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf
chris@hpdv5k:~$ 
```

This next set of code is with the usb inserted.
```
lsmod | grep -e ndis -e rt2
chris@hpdv5k:~$ lsmod | grep -e ndis -e rt2
chris@hpdv5k:~$ 
chris@hpdv5k:~$ ls /etc/modprobe.d | grep -e ndis -e black
blacklist-ath_pci.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf
chris@hpdv5k:~$
```

I noticed my code was differetnt from Drewkman so I am pausing.

---

### Post by chili555 on 2010-04-08
@alliance1975 -
May we see:```
lsusb
```We need to know if you have the same device. Your modprobe.d files look fine.

@Drewkman -

Please do:```
sudo modprobe rt2800usb
iwconfig
```Any signs of life? If not, please post:```
dmesg | grep rt2
cat /etc/modprobe.d/blacklist.conf | grep rt2
```Thanks, guys and gals!

---

### Post by alliance1975 on 2010-04-08
lsusb as requested
```
chris@hpdv5k:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 148f:2770 Ralink Technology, Corp. 
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 001 Device 003: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
chris@hpdv5k:~$
```

---

### Post by chili555 on 2010-04-08
@alliance 1975 -
Your device is supported by both rt2870sta *_and_* rt2800usb. They conflict and fight. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot and give us a report. Does your wireless appear in *iwconfig* and Network Manager?

---

### Post by alliance1975 on 2010-04-08
The blacklisting of other railink devices was performed in one of my previous attempts at getting the wlan to work. The end of the blacklist file follows:
```
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```

Please be advised I am communicating now via the onboard Broadcom a/b/g card.

---

### Post by Drewkman on 2010-04-08
Nada. No difference. When I run one of these modprobe commands, I do get the message:
'WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.'

I don't know if that's expected/is a problem.  :-k

```
andrew@ubuntu-desktop:~$ dmesg | grep rt2
[  124.696057] usbcore: registered new interface driver rt2800usb
[  161.523255] phy0 -> rt2800usb_init_eeprom: Error - Invalid RT chipset detected.
[  161.523266] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
andrew@ubuntu-desktop:~$ cat /etc/modprobe.d/blacklist.conf | grep rt2
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```

Doesn't seem particularly healthy.

---

### Post by chili555 on 2010-04-08
> **alliance1975 said:**
> The blacklisting of other railink devices was performed in one of my previous attempts at getting the wlan to work. The end of the blacklist file follows:
```
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```

Please be advised I am communicating now via the onboard Broadcom a/b/g card.Now please do:```
sudo modprobe rt2870sta
```Let us see:```
iwconfig
dmesg | grep rt2
```Thanks.

---

### Post by alliance1975 on 2010-04-08
Code and replies as follows:
```
chris@hpdv5k:~$ sudo modprobe rt2870sta
FATAL: Could not open '/lib/modules/2.6.32-16-generic/kernel/drivers/staging/rt2870/rt2870sta.ko': No such file or directory
chris@hpdv5k:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"DUDEKS"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:5A:D1:7F:1E   
          Bit Rate=48 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

chris@hpdv5k:~$ dmesg | grep rt2
chris@hpdv5k:~$ 
```

---

### Post by chili555 on 2010-04-08
> **Drewkman said:**
> Nada. No difference. When I run one of these modprobe commands, I do get the message:
'WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.'

I don't know if that's expected/is a problem.  :-k

```
andrew@ubuntu-desktop:~$ dmesg | grep rt2
[  124.696057] usbcore: registered new interface driver rt2800usb
[  161.523255] phy0 -> rt2800usb_init_eeprom: Error - Invalid RT chipset detected.
[  161.523266] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
andrew@ubuntu-desktop:~$ cat /etc/modprobe.d/blacklist.conf | grep rt2
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```

Doesn't seem particularly healthy.Let's do some housekeeping:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
sudo updatedb
locate rt3070sta.ko
```Is rt3070sta.ko resident on your system? Let's try:```
sudo rmmod -f rt2800usb
sudo modprobe rt3070sta
iwconfig
```Any new developments?

---

### Post by Drewkman on 2010-04-08
Nothing. :(

It couldn't find 'rt2800usb'.

---

### Post by chili555 on 2010-04-08
@alliance1975 -> FATAL: Could not open '/lib/modules/2.6.32-16-generic/kernel/drivers/staging/rt2870/rt2870sta.ko': No such file or directory
That's pretty weird! It knows where it is, but it can't find it! ???

Can you find it with:```
ls /lib/modules/2.6.32-16-generic/kernel/drivers/staging/ | grep rt2870sta.ko
```

---

### Post by chili555 on 2010-04-08
> **Drewkman said:**
> Nothing. :(

It couldn't find 'rt2800usb'.I'm sure it rejected it and didn't load it when it said this:> rt2800usb_init_eeprom: Error - Invalid RT chipset detected.I assume rt3070sta loaded without complaint. May I see:```
dmesg | grep -e rt2 -e rt3
```Thanks.

---

### Post by alliance1975 on 2010-04-08
The code and reply follows:
```
chris@hpdv5k:~$ ls /lib/modules/2.6.32-16-generic/kernel/drivers/staging/ | grep rt2870sta.ko
chris@hpdv5k:~$
```

Please note, one of my previous attempts to get the usb wlan to work involved following the recommendations of peepingtom, 11/30/2009 entitled "RALINK RT2870STA and RT3070STA USB WiFi Tutorial", the final command in the series is
```
Then delete the version of the rt2870sta module that came with Ubuntu (there might be better ways to do this, but it will allow the newly compiled one will load by default).
Code:

sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/staging/rt2870

Otherwise, you will have to run the above commands whenever you want to use the new driver. You will need to recompile this module every time a new Linux kernel is installed.

```

Apparently I am the culprit.

---

### Post by chili555 on 2010-04-08
@alliance1975 -
Did you compile a tar.gz file or what? What went wrong?

---

### Post by Drewkman on 2010-04-08
I don't get any response; just returned to the prompt:

> andrew@ubuntu-desktop:~$ dmesg | grep -e rt2 -e rt3
andrew@ubuntu-desktop:~$ 

---

### Post by alliance1975 on 2010-04-08
I downloaded the driver package, (2009_0820_RT2870_Linux_STA_V2.2.0.0) from the railink site and extracted it.

Per peepingtom:

> Determining which module you should use:
If a USB WiFi adapter is automatically detected by rt2870sta, rt3070sta or an rt2x00 module, it has likely been verified to function by that module's developers. While the rt2x00 driver has some support for rt2870 chipsets, it seems that rt2870 and rt3070 chipsets work best when controlled by Ralink's drivers. Only one of these modules should be loaded per network adapter.

To determine which modules control your USB WiFi adapter, insert it and run the following command in terminal 
Code:
lsmod |grep rt
rt2870 devices are supported by Ralink's rt2870 driver (module rt2870sta) or by the rt2x00 project's driver (modules rt2800usb, rt2x00lib, rt2x00usb). rt3070 devices are supported by Ralink's rt3070 driver (module rt3070sta)

Blacklisting Modules:

To begin, unplug any Ralink USB WiFi adapters and restart your computer (or unload the modules).

To use rt2870sta and blacklist rt2800usb, run the following commands in terminal:
Code:
gksudo gedit /etc/modprobe.d/blacklist.conf
add these lines to the end of the file:
Code:
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
Save the file, then insert your USB WiFi device.If this didn't work:

Your device either doesn't function with the driver you chose, or your WiFi Adapter's USB Device ID is not detected by that driver. If you're certain of which chipset is in your WiFi Adapter, you can modify and compile a kernel module that will detect and attempt to control any adapter with its USB Dev ID.

Determining Your Device's USB Device ID
You can check your USB Device ID using 
Code:
lsusb
For example, lsusb states that a USB WiFi adapter has a device ID of 1234:7777 
Code:
 oo@oo:~$ lsusb
Bus 001 Device 004: ID 1234:7777 Brand
Compiling a New Kernel Module (Driver)
You'll need a compiler and Linux headers installed
Code:
sudo apt-get install build-essential linux-headers-generic

Modifying and Compiling RT2870STA: 

Download a copy of Ralink's rt2870 USB driver from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
Save it to your Ubuntu computer's desktop, then extract its contents using the following commands in terminal:
Code:
cd ~/Desktop
tar -xvf ~/Desktop/RT2870_LinuxSTA*.tgz
cd ~/Desktop/*2870*
Now you'll make some modifications, to add your device's USB Device ID. The following is an EXAMPLE. Using the lsusb command, it has been determined that an adapter has has the USB Device ID 1234:7777. MODIFY THESE INSTRUCTIONS TO USE YOUR USB DEV ID! You can put whatever you want for comments between */ s, they are meant to document the code.

Edit 
Code:
gedit ~/Desktop/*2870*/common/rtusb_dev_id.c
add to the group:
Code:
{USB_DEVICE(0x1234,0x7777)}, /* Example WiFi Device Name */
Save.

You'll now configure the source to be compiled with support for NetworkManager and wext. NetworkManager is Ubuntu's default graphical method for configuring networking. It provides the icon in the "notification area" aka "system tray".

Edit 
Code:
gedit ~/Desktop/*2870*/os/linux/config.mk
Change 
Code:
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
to 
Code:
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
Save.


In terminal:
Code:
cd ~/Desktop/*2870*
(If you're trying to compile a second time, please note: Run "make clean" before running "make" to remove your previous attempt.)
make
sudo make install
This installs the module rt2870sta.ko, but now you have 2 copies of it: 
one in /lib/modules/`uname -r`/kernel/drivers/net/wireless and another at /lib/modules/`uname -r`/kernel/drivers/staging/rt2870. The one in the staging directory is the one that came with Ubuntu, which obviously doesn't work for you. 

Before you delete your old driver, run the following commands to see if your newly compiled driver actually functions with your USB device.
Code:
sudo modprobe -r rt2870sta
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko
sudo /etc/init.d/networking restart
sudo restart network-manager
If NetworkManager now works, congratulations.

Then delete the version of the rt2870sta module that came with Ubuntu (there might be better ways to do this, but it will allow the newly compiled one will load by default). 
Code:
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/staging/rt2870
Otherwise, you will have to run the above commands whenever you want to use the new driver. You will need to recompile this module every time a new Linux kernel is installed.

Just prior to the last command that removed rt2870 from staging I was getting 100+ Mbs from the railink, (had to disable broadcom). I followed the last command so as to insure the railink would launch every time I booted. Which brings me to here and now.

---

### Post by chili555 on 2010-04-08
> **Drewkman said:**
> I don't get any response; just returned to the prompt:If you loaded rt3070sta, it should have appeared in dmesg, even if it not correct for your device. Let's try again:```
sudo modprobe rt3070sta
dmesg | grep rt3
```Thanks.

---

### Post by chili555 on 2010-04-08
> I followed the last command so as to insure the railink would launch every time I booted. Which brings me to here and now.Meaning that as soon as you removed the staging driver, your device stopped working?

---

### Post by chili555 on 2010-04-08
Other interests beckon, gents; see you tomorrow.

---

### Post by alliance1975 on 2010-04-08
That is when the device ceased to operate.

---

### Post by Drewkman on 2010-04-08
Got something this time:

```
andrew@ubuntu-desktop:~$ dmesg | grep rt3
[ 3329.032946] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.
```

I'm going to have to call it a day now, too. I'm a Brit and it's about to hit 2am over here. I really appreciate the help you've given us, chili555. I'll be back up and running tomorrow.

---

### Post by alliance1975 on 2010-04-09
Am at work and will not have access to hpdv5k until 5:00 PM Eastern. One of the commands recommended by peepingtom was strange.
> Code:
gedit ~/Desktop/*2870*/common/rtusb_dev_id.c
add to the group:
Code:
{USB_DEVICE(0x1234,0x7777)}, /* Example WiFi Device Name */
Save.

The save resulted in a response that the file did not exist. I had to do a save-as and I named it "rtusb_dev_id.c" and proceeded from there.

As it stands the card is being recognized but refuses to connect. I am in an endless loop where network manager tries to connect, asks for the wpa passphrase, tries some more, then asks for the passphrase again.

I thought it might be inteference from the onboard broadcom, but despite disabling it, the looping persisted. Admin-networks does show the card and its mac address but no isp is assigned to it.

If you wish, I can repeat peepingtom's commands and print out the responses. I will await your instructions.

---

### Post by chili555 on 2010-04-09
> As it stands the card is being recognized but refuses to connect. I am in an endless loop where network manager tries to connect, asks for the wpa passphrase, tries some more, then asks for the passphrase again.
In the folder that was created when you extracted the downloaded file, there is a README that has instructions about editing your config.mk file to specify that Network Manager will control your device. Was that done correctly?

I will look for you later.

---

### Post by alliance1975 on 2010-04-09
That question I can quickly answer now and yes I double checked the modifications to that file. I wanted to retain control by network manager and not install/use other networking software. The two lines regarding wpa supplicant were revised from "n" to "y". After saving I went back and verified the changes.

However, my lack of young age may have caused me to err. I shall reverify the revisions upon returning home.

---

### Post by chili555 on 2010-04-09
> my lack of young age may have caused me to err.If you only knew about Dr. Chili!

The other thing that might help is amendments to RT2870STA.dat as outlined in the README. I thought that if you declared that NM was going to do the work, all that would be taken care of. You might take a look and see if you can 'help' NM do the job better.

I will be around later and we can, if you need to, work on this together.

---

### Post by alliance1975 on 2010-04-09
No sooner did I mention how my age seems to enhance my mental clumsiness then I went and looked at the downloaded tar.bz2 files I was working with. It appears I may have performed commands from RT2870_Linux_STA_V2.2.0.0 and not RT2870_LinuxSTA_V2.3.0.0. I have different versions of the driver and I did not keep track of them. 

I apologize for my blunder. I have seen the help you provide to other people on this forum and I had no intention of wasting your time. I am very grateful for you help.

If there is a way to reverse the previous mistakes I made and start the install anew I will do so. Otherwise, I can reinstall the os and start fresh from there.

---

### Post by chili555 on 2010-04-09
> I can reinstall the os and start fresh from there....the nuclear option...not quite yet. Let's try this.

First cd to the 2.2.0.0 directory and do:```
sudo su
make uninstall
```Now, cd to the 2.3.0.0 directory and check the config.mk file for the Network Manager changes and amend if necessary. Then do:```
make clean
make 
make install
modprobe rt2870sta
```Post back and report your progress. If the driver does not grab your device and run, then look at:```
modinfo rt2870sta | grep 2770
```2770 is the last four digits of your usb.id. If it is not listed, we may need to amend a dev.c file somewhere and 'make' again.

I am very glad to help in any way I can. A fair number of issues I work on are unraveling a previous well-intentioned attempt at installation that has gone wrong.

---

### Post by alliance1975 on 2010-04-09
Eureka! It is working. I must remember all I did to recount the events.

Per your instructions I went to V2.2.0.0 and uninstalled.

Went to V2.3.0.0 and likewise uninstalled.

```
sudo apt-get install build-essential linux-headers-generic
```
I heard this was important.

```
gedit ~/Desktop/*2870*/common/rtusb_dev_id.c
```
Confirmed 148f:2770 was listed

```
gedit ~/Desktop/*2870*/os/linux/config.mk
```
Made suplicant revisions "n" to "y"

```
sudo make clean
sudo make
sudo make install
```

```
sudo modprobe -r rt2870sta
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko
sudo /etc/init.d/networking restart
sudo restart network-manager
```

Went to network manager and disconnected Broadcom b/g
RT2870 remains active at 135 Mbps

---

### Post by chili555 on 2010-04-09
Great news and good work! Have fun.

---

### Post by alliance1975 on 2010-04-09
I suppose my next step would be to have the laptop launch the RT2870 on startup. My hpdv5k mostly remains sedentary and the RT2870 will remain connected. Should I unload the Broadcom drivers to prevent usage?

By the way, the last command recommended by peepingtom, (below), was not performed. Staging still contains the rt2870 file.

```
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/staging/rt2870
```

It seems so much of this effort comes down to simple bookkeeping. But without your guidance the path might very well have been very long and time consuming.

All of this was done on Ubuntu 10.04 beta.

---

### Post by chili555 on 2010-04-09
> the last command recommended by peepingtom, (below), was not performed.And it needn't be. When you did 'make install' it made the driver you built the default. It will be loaded when you load rt2870sta and not the staging version.> Should I unload the Broadcom drivers to prevent usage?You certainly can. You could blacklist them or simply add this to */etc/rc.local*:```
ifconfig wlan0 down
```Substitute your Broadcom interface if it's not wlan0.

Now, where is our colleague Drewkman?

---

### Post by alliance1975 on 2010-04-09
Used lsmod and found broadcom is b43. Blacklisted b43 and rebooted. All is flawless.

I wish good luck to Drewkman. If there's anything to learn from Chilli it's don't give up.

Chilli555 Respect

---

### Post by Benedikt1988 on 2010-04-27
Hello,

I´m also trying to install an USB-wlan-stick with a ralink 2870 chip.

I followed peepingtoms instructions. I think it worked but the network manager doesn´t show me any wireless connections.

I hope these informations help you. Please ask, if there´s something you want to know.

(I´m very new to Ubuntu.)


```
maren@maren:~$ lsusb
Bus 001 Device 004: ID 050d:935b Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 002: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

``````
maren@maren:~$ lsmod |grep rt
snd_mpu401_uart         6940  1 snd_via82xx
snd_rawmidi            22176  2 snd_mpu401_uart,snd_seq_midi
rt2870sta             554844  1 
snd                    59204  16 snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             31940  1 
parport                35340  3 ppdev,lp,parport_pc
gameport               11368  3 snd_via82xx,ns558
agpgart                34988  3 ttm,drm,via_agp

``````
maren@maren:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA  ESSID:"Apfel"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: 06:DC:38:94:15:E7   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``````
maren@maren:~$ ifconfig
eth1      Link encap:Ethernet  Hardware Adresse 00:11:d8:0b:16:88  
          inet Adresse:192.168.178.24  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6-Adresse: fe80::211:d8ff:fe0b:1688/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:3308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2966 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:3049503 (3.0 MB)  TX bytes:466116 (466.1 KB)
          Interrupt:23 Basisadresse:0x6000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:5846 (5.8 KB)  TX bytes:5846 (5.8 KB)

ra0       Link encap:Ethernet  Hardware Adresse 00:22:75:a3:1e:4d  
          inet6-Adresse: fe80::222:75ff:fea3:1e4d/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:547 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:39592 (39.5 KB)

ra0:avahi Link encap:Ethernet  Hardware Adresse 00:22:75:a3:1e:4d  
          inet Adresse:169.254.5.239  Bcast:169.254.255.255  Maske:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1

```Thank you very much,
Benedikt

---

### Post by chili555 on 2010-04-27
> think it worked but the network manager doesn´t show me any wireless connections.Network Manager is designed to not allow a wireless connection if you have a wired ethernet connection, which you do:> eth1      Link encap:Ethernet  Hardware Adresse 00:11:d8:0b:16:88  
          inet Adresse:[COLOR="Red"]192.168.178.24[/COLOR] Please detach the wire, wait a few moments to let NM notice the change of state and then click the NM icon and see if you see your network and connect.

---

### Post by Benedikt1988 on 2010-04-27
Thanks for your comment.

I detached the wire but NM still won´t show me a wireless network.
The Stick´s LED is blinking irregulary.

---

### Post by PhilLord on 2010-04-28
I too am having problems with the DWA-140/ralink 2870, following an upgrade to
10.04. This is a bit confusing as it worked (with fiddling!) under 9.10. 

The device appears to be working. It has been recognised by the system, with
the LED blinking irregularly. It recognises the network that it is supposed to
but the connection never completes, and I can get no connection through it. 

During 9.10 installation, I added this to blacklist.conf

blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb

To my memory I didn't need to do anything else, however I foolishly didn't
document this. 

lsusb shows....



```

$ lsusb
Bus 005 Device 003: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 005 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 002 Device 002: ID 093a:2468 Pixart Imaging, Inc. Cammaestro 2.5DU/X-EYE/Orite SC-120/ICGear TravelCam/Easy Snap Snake Eye Webcam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 07d1:3c09 D-Link System DWA-140 802.11n Adapter [ralink rt2870]
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


iwconfig shows ...


```


[phillord@dinley:/home/phillord]$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"pands"  Nickname:"RT3070STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:24:01:A7:33:E4   
          Bit Rate=24 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-62 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```


While it is connecting, or this once it times out...

```

[phillord@dinley:/home/phillord]$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-68 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

lsmod shows the following. I don't understand why rt2x00usb and rt2x00lib are
there, as I have blacklisted them also. Then, I don't understand what
blacklisting is doing. 

```

$ lsmod |grep -e rt* 
aes_generic            26863  1 aes_i586
arc4                    1153  0 
rt73usb                22434  0 
crc_itu_t               1371  1 rt73usb
rt2500usb              18141  0 
rt2x00usb               9703  2 rt73usb,rt2500usb
rt2x00lib              27509  3 rt73usb,rt2500usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              204922  2 rt2x00usb,rt2x00lib
cfg80211              126485  2 rt2x00lib,mac80211
softcursor              1189  1 bitblit
snd_mixer_oss          13746  1 snd_pcm_oss
snd_rawmidi            19056  1 snd_seq_midi
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29297  1 i915
snd                    54148  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162471  3 i915,drm_kms_helper
parport_pc             25962  1 
rt2870sta             461811  1 
soundcore               6620  1 snd
serio_raw               3978  0 
parport                32635  3 ppdev,parport_pc,lp
agpgart                31724  2 drm,intel_agp

```


Finally, dmesg

```

$ dmesg | grep -e rt2870*
[   14.791684] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   14.837954] usbcore: registered new interface driver rt2870

```

Any help is gratefully received! I'm out of ideas and a bit disappointed since
I was hoping that this would work through the upgrade, but these things happen. I'd love to get it fixed, though, since my wireless G adaptor is struggling a bit with the range to the router; the wireless N solution worked fine. 

Thanks for any pointers. 

Phil

---

### Post by chili555 on 2010-04-28
> rt73usb                22434  0 
crc_itu_t               1371  1 rt73usb
rt2500usb              18141  0 
rt2x00usb               9703  2 rt73usb,rt2500usb
rt2x00lib              27509  3 rt73usb,rt2500usb,rt2x00usb
I notice that rt73usb is all wound up in there, too; I imagine it is dragging rt2x00lib and rt2x00usb in. Please add to your blacklist file:```
blacklist rt73usb
```Reboot and let us know if the behavior improves.

---

### Post by chili555 on 2010-04-28
> **Benedikt1988 said:**
> Thanks for your comment.

I detached the wire but NM still won´t show me a wireless network.
The Stick´s LED is blinking irregulary.Please detach the wire and do:```
sudo iwconfig ra0 mode managed
sudo iwlist ra0 scan
```If you get no scan results, post any errors or warnings as well as:```
dmesg | grep ra0
```Thanks.

---

### Post by Benedikt1988 on 2010-04-28
```
maren@maren:~$ sudo iwconfig ra0 mode managed
maren@maren:~$ sudo iwlist ra0 scan
ra0       No scan results

maren@maren:~$ dmesg | grep ra0
maren@maren:~$ 

```As you see, no reaction on "sudo iwconfig ra0 mode managed" and "dmesg | grep ra0".
Seems a bit strange, doesn´t it?

edit:
```
maren@maren:~$ sudo dmesg | grep ra0
[ 1005.556395] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=ra0!
[ 1017.648013] ra0: no IPv6 routers present

```

On a second attempt I got this result, but all new attempts show nothing, like in the first try.

Thanks,
Benedikt

---

### Post by chili555 on 2010-04-28
> Seems a bit strange, doesn´t it?It's not at all strange that you issued a command to change the mode to managed and it returned nothing; that is, no errors or warnings. I think it's a good thing.

I do think it's odd that there were no scan results. Are you near a wireless network?

This part usually occurs when the interface tries to connect or actually connects!! > ra0: no IPv6 routers presentIs there any sign of activity in Network Manager? What does this tell us?```
sudo cat /var/log/syslog | grep -e ra0 -e rt2
```

---

### Post by PhilLord on 2010-04-29
> **chili555 said:**
> I notice that rt73usb is all wound up in there, too; I imagine it is dragging rt2x00lib and rt2x00usb in. Please add to your blacklist file:```
blacklist rt73usb
```Reboot and let us know if the behavior improves.

I'm afraid adding this to the blacklist didn't make any difference.

Phil

---

### Post by chili555 on 2010-04-29
> **PhilLord said:**
> I'm afraid adding this to the blacklist didn't make any difference.

Phil
Please post:```
lsmod | grep -e rt2 -e rt7
demsg | grep -e rt7 -e rt2
```Thanks.

---

### Post by Benedikt1988 on 2010-04-29
> **chili555 said:**
> It's not at all strange that you issued a command to change the mode to managed and it returned nothing; that is, no errors or warnings. I think it's a good thing.

I do think it's odd that there were no scan results. Are you near a wireless network?

This part usually occurs when the interface tries to connect or actually connects!! Is there any sign of activity in Network Manager? What does this tell us?```
sudo cat /var/log/syslog | grep -e ra0 -e rt2
```

Hello,

I moved now exactly in front of my WLAN-router. No changes.

edit: NM contains a column for wireless networks, but won´t display any. The LED blinks continously when I´m trying to connent to a hidden network.

The output for:
```
sudo cat /var/log/syslog | grep -e ra0 -e rt2
``````
maren@maren:~$ sudo cat /var/log/syslog | grep -e ra0 -e rt2
Apr 29 14:10:32 maren NetworkManager: <info>  (ra0): taking down device.
Apr 29 14:12:35 maren kernel: [   94.970586] usbcore: registered new interface driver rt2870
Apr 29 14:12:35 maren NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:10.4/usb1/1-3/net/ra0, iface: ra0)
Apr 29 14:12:35 maren NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:10.4/usb1/1-3/net/ra0, iface: ra0): no ifupdown configuration found.
Apr 29 14:12:35 maren NetworkManager: <info>  (ra0): driver does not support SSID scans (scan_capa 0x00).
Apr 29 14:12:35 maren NetworkManager: <info>  (ra0): new 802.11 WiFi device (driver: 'usb')
Apr 29 14:12:35 maren NetworkManager: <info>  (ra0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 29 14:12:35 maren NetworkManager: <info>  (ra0): now managed
Apr 29 14:12:35 maren NetworkManager: <info>  (ra0): device state change: 1 -> 2 (reason 2)
Apr 29 14:12:35 maren NetworkManager: <info>  (ra0): bringing up device.
Apr 29 14:12:50 maren kernel: [  109.966428] <==== rt28xx_init, Status=0
Apr 29 14:12:50 maren NetworkManager: <info>  (ra0): preparing device.
Apr 29 14:12:50 maren NetworkManager: <info>  (ra0): deactivating device (reason: 2).
Apr 29 14:12:50 maren NetworkManager: <info>  (ra0): supplicant interface state:  starting -> ready
Apr 29 14:12:50 maren NetworkManager: <info>  (ra0): device state change: 2 -> 3 (reason 42)
Apr 29 14:12:51 maren avahi-daemon[762]: Registering new address record for fe80::222:75ff:fea3:1e4d on ra0.*.
Apr 29 14:13:00 maren kernel: [  120.368020] ra0: no IPv6 routers present
Apr 29 14:13:03 maren NetworkManager: <info>  (ra0): taking down device.
Apr 29 14:13:03 maren avahi-daemon[762]: Withdrawing address record for fe80::222:75ff:fea3:1e4d on ra0.
Apr 29 14:13:03 maren NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:10.4/usb1/1-3/net/ra0, iface: ra0)
Apr 29 14:13:03 maren NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:10.4/usb1/1-3/net/ra0, iface: ra0): no ifupdown configuration found.
Apr 29 14:13:03 maren NetworkManager: <info>  (ra0): driver does not support SSID scans (scan_capa 0x00).
Apr 29 14:13:03 maren NetworkManager: <info>  (ra0): new 802.11 WiFi device (driver: 'usb')
Apr 29 14:13:03 maren NetworkManager: <info>  (ra0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 29 14:13:03 maren NetworkManager: <info>  (ra0): now managed
Apr 29 14:13:03 maren NetworkManager: <info>  (ra0): device state change: 1 -> 2 (reason 2)
Apr 29 14:13:03 maren NetworkManager: <info>  (ra0): bringing up device.
Apr 29 14:13:04 maren kernel: [  123.780876] <==== rt28xx_init, Status=0
Apr 29 14:13:04 maren NetworkManager: <info>  (ra0): preparing device.
Apr 29 14:13:04 maren NetworkManager: <info>  (ra0): deactivating device (reason: 2).
Apr 29 14:13:04 maren NetworkManager: <info>  (ra0): supplicant interface state:  starting -> ready
Apr 29 14:13:04 maren NetworkManager: <info>  (ra0): device state change: 2 -> 3 (reason 42)
Apr 29 14:13:05 maren avahi-daemon[762]: Registering new address record for fe80::222:75ff:fea3:1e4d on ra0.*.
Apr 29 14:13:14 maren kernel: [  134.144017] ra0: no IPv6 routers present
maren@maren:~$ 

```Thanks,
Benedikt

---

### Post by chili555 on 2010-04-29
> driver does not support SSID scans (scan_capa 0x00).Wow. I never saw that before! Will it connect if you explicitly specify the network name?

Right-click the Network Manager icon and select Edit Connections. Select the Wireless tab and click Add. Fill in the name of your network. The case, spelling, etc. must be perfect. 

Select the Wireless Security tab and fill in your encryption details. Click Apply and then left-click the NM icon and see if you can connect.

As you can see in syslog, it's trying!

---

### Post by Benedikt1988 on 2010-04-29
> **chili555 said:**
> Wow. I never saw that before! Will it connect if you explicitly specify the network name?

Right-click the Network Manager icon and select Edit Connections. Select the Wireless tab and click Add. Fill in the name of your network. The case, spelling, etc. must be perfect. 

Select the Wireless Security tab and fill in your encryption details. Click Apply and then left-click the NM icon and see if you can connect.

As you can see in syslog, it's trying!

Unfortunately this doesen´t work either. I checked case, spelling, etc 3 times. Doesn´t show up.

I have to say that I tried the easy way with ndiswrapper and ndisgtk before compiling the linux drivers. I uninstalled all ndiswrapper related drivers, and "lsmod |grep rt" shows only the "rt2870sta" being loaded. Might there still be a problem? Could a reinstall of Ubuntu solve this?

Thanks for your time,
Benedikt

edit: Is it necessary to fill in the IPv4 options by manual too?

---

### Post by chili555 on 2010-04-29
Do you have a file /etc/Wireless/RT2870STA/RT2870STA.dat? Is it correctly configured? If in doubt, post it here for our examination.

---

### Post by Benedikt1988 on 2010-04-29
Here is my RT2870STA.dat file:
I don´t know if it´s configuered correctly, is all very complicated with Ubuntu. :(
And yes, I´m based in Austria, as my writing might unveiled earlier.

At the manual configuration of the wlan, is it also necessary to fill in the IPv4 information by hand?

Thanks,
Benedikt

```
#The word of "Default" must not be removed
Default
CountryRegion=1
CountryRegionABand=1
CountryCode=AT
ChannelGeography=1
SSID=WLAN
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
PSP_XLINK_MODE=0
```

---

### Post by chili555 on 2010-04-29
I would change the following; I have highlighted my suggested changes. Of course, substitute your details to suit:> #The word of "Default" must not be removed
Default
CountryRegion=1
CountryRegionABand=1
CountryCode=AT
ChannelGeography=1
SSID=[COLOR="Red"]your-network-name[/COLOR]
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=[COLOR="Red"]OPEN,SHARED,WEPAUTO,WPAPSK,WPA2PSK,WPANONE[/COLOR]  <== Select your encryption mode.
EncrypType=[COLOR="Red"]NONE,WEP,TKIP,AES[/COLOR]  <==Select your type.
WPAPSK=[COLOR="Red"]Insert key here, if approriate.[/COLOR]
DefaultKeyID=1
I do not use that driver, but, if I did, my file would look like:```
#The word of "Default" must not be removed
Default
CountryRegion=1
CountryRegionABand=1
CountryCode=US
ChannelGeography=1
SSID=mylilrouter
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=WPA2PSK
EncrypType=AES
WPAPSK=mysecretkey
--- snip ---

```The remainder of the file is unchanged.> is it also necessary to fill in the IPv4 information by hand?Nope, Network Manager is supposed to figure that out for you.

---

### Post by PhilLord on 2010-05-05
> **chili555 said:**
> Please post:```
lsmod | grep -e rt2 -e rt7
demsg | grep -e rt7 -e rt2
```Thanks.


Sorry for the delay in replying. Been a bank holiday and had visitors all weekend!

I have found that the rt73usb module that you saw last time was indeed pulling in rt2x00lib and rt2x00usb. This module was present because it driving my wireless G adaptor; this was connected, so I could read the forums. 

I've tried with and without this wireless G device connected. Without I get this...

```

[phillord@dinley:/home/phillord]$ lsmod | grep -e rt2 -e rt7
rt2870sta             461811  1 
[phillord@dinley:/home/phillord]$ dmesg | grep -e rt2 -e rt7
[   14.965228] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   15.006505] usbcore: registered new interface driver rt2870
[phillord@dinley:/home/phillord]$ 

```

With this

```

[phillord@dinley:/home/phillord]$ lsmod | grep -e rt2 -e rt7
rt2870sta             461811  1 
rt73usb                22434  0 
crc_itu_t               1371  1 rt73usb
rt2500usb              18141  0 
rt2x00usb               9703  2 rt73usb,rt2500usb
rt2x00lib              27509  3 rt73usb,rt2500usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              204922  2 rt2x00usb,rt2x00lib
cfg80211              126485  2 rt2x00lib,mac80211
[phillord@dinley:/home/phillord]$ dmesg | grep -e rt2 -e rt7
[   15.656865] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[   15.656920] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   15.657032] usbcore: registered new interface driver rt2500usb
[   16.019918] Registered led device: rt73usb-phy1::radio
[   16.019950] Registered led device: rt73usb-phy1::assoc
[   16.019981] Registered led device: rt73usb-phy1::quality
[   16.020563] usbcore: registered new interface driver rt73usb
[   16.788495] rt73usb 1-4:1.0: firmware: requesting rt73.bin
[  143.422682] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[  143.435523] usbcore: registered new interface driver rt2870
[phillord@dinley:/home/phillord]$ 

```

In neither case does the wireless N device work. My interpretation here (which could be wrong, or I wouldn't be asking:-) is that the correct modules are being loaded. Therefore, what worked with 9.10 is not working with 10.04 and this appears to be a different bug. 

Not good. 

Any suggestions gratefully received. I'm considering reverting to 9.10.

---

### Post by jandante on 2010-05-08
Hi,

a new case for you guys :). I've followed the complete thread and haven't been able to get it to work.

The solution for alliance1975 didn't work for me. But it gave me something. Before i never got anything when i typed iwconfig. no it says:

```

dante@Concept-IT:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

So i think Ubuntu has found my wireless usb stick (the led doesn't blink or doesn't go on at all but something shows up in iwconfig) thanks to the steps alliance1975 listed.

But in NetworkManager i get no networks. Even not after restart. The staging driver rt2870 has been removed and the one compiled gets loaded on startup.

Then maybe also relevant is the output of sudo cat /var/log/syslog | grep -e ra0 -e rt2

```

dante@Concept-IT:~$ sudo cat /var/log/syslog | grep -e ra0 -e rt2
May  8 11:15:18 Concept-IT kernel: [ 4520.827172] phy0 -> rt2800usb_init_eeprom: Error - Invalid RT chipset detected.
May  8 11:15:18 Concept-IT kernel: [ 4520.827179] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
May  8 11:15:18 Concept-IT kernel: [ 4520.827239] usbcore: registered new interface driver rt2800usb
May  8 11:18:07 Concept-IT kernel: [ 4689.067438] usbcore: deregistering interface driver rt2800usb
May  8 11:26:29 Concept-IT NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ra0, iface: ra0)
May  8 11:26:29 Concept-IT NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ra0, iface: ra0): no ifupdown configuration found.
May  8 11:26:29 Concept-IT NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/ra0: couldn't determine device driver; ignoring...
May  8 11:26:29 Concept-IT kernel: [ 5191.359882] usbcore: registered new interface driver rt2870
May  8 11:26:52 Concept-IT NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ra0, iface: ra0)
May  8 11:26:52 Concept-IT NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ra0, iface: ra0): no ifupdown configuration found.
May  8 11:26:52 Concept-IT NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/ra0: couldn't determine device driver; ignoring...
May  8 11:35:06 Concept-IT kernel: [ 5708.414512] usbcore: deregistering interface driver rt2870
May  8 11:35:06 Concept-IT kernel: [ 5708.414541] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=ra0!
May  8 11:35:07 Concept-IT NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ra0, iface: ra0)
May  8 11:35:31 Concept-IT NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ra0, iface: ra0)
May  8 11:35:31 Concept-IT NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ra0, iface: ra0): no ifupdown configuration found.
May  8 11:35:31 Concept-IT NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/ra0: couldn't determine device driver; ignoring...
May  8 11:35:31 Concept-IT kernel: [ 5732.601636] usbcore: registered new interface driver rt2870
May  8 11:35:46 Concept-IT NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ra0, iface: ra0)
May  8 11:35:46 Concept-IT NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ra0, iface: ra0): no ifupdown configuration found.
May  8 11:35:46 Concept-IT NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/ra0: couldn't determine device driver; ignoring...
May  8 11:39:48 Concept-IT kernel: [   10.212302] usbcore: registered new interface driver rt2870
May  8 11:39:48 Concept-IT NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ra0, iface: ra0)
May  8 11:39:48 Concept-IT NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ra0, iface: ra0): no ifupdown configuration found.
May  8 11:39:48 Concept-IT NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/ra0: couldn't determine device driver; ignoring...

```

I hope someone can help.

---

### Post by PhilLord on 2010-05-08
> **PhilLord said:**
> 
In neither case does the wireless N device work. My interpretation here (which could be wrong, or I wouldn't be asking:-) is that the correct modules are being loaded. Therefore, what worked with 9.10 is not working with 10.04 and this appears to be a different bug. 

Not good. 

Any suggestions gratefully received. I'm considering reverting to 9.10.

Well, it appears that my interpretation was correct. The problem was not that the wrong modules were being loaded, it's that the module being loaded is not behaving well. 

I read up on the information here. 

[http://wiki.debian.org/rt2870sta](http://wiki.debian.org/rt2870sta)

And solved the problem by switching over to TKIP, although I did this router side. So, it's the authentication that is breaking. 

Very simple in the end -- aren't these things always so? 

Thanks for the help; it's always appreciated that people are willing to give feedback, helping to solve others problems. 

Phil

---

### Post by themoddingden on 2010-06-08
hey guys  if we use all the software in that source file do we get the software ap as well???

---

### Post by edubidu on 2010-09-26
Hello,

I installed the ra2870 driver, version 2.4.0.1 from the [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) site.
the driver is working, but I have an eternal random with this:
tail -f /var/log/syslog

[HTML]Sep 26 13:22:11 edubidu kernel: [ 1146.555588] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.556375] Key2Str is Invalid key length(0) or Type(0)
Sep 26 13:22:11 edubidu kernel: [ 1146.556421] Key3Str is Invalid key length(0) or Type(0)
Sep 26 13:22:11 edubidu kernel: [ 1146.556468] Key4Str is Invalid key length(0) or Type(0)
Sep 26 13:22:11 edubidu kernel: [ 1146.580947] 1. Phy Mode = 9
Sep 26 13:22:11 edubidu kernel: [ 1146.580953] 2. Phy Mode = 9
Sep 26 13:22:11 edubidu kernel: [ 1146.629399] 3. Phy Mode = 9
Sep 26 13:22:11 edubidu kernel: [ 1146.637403] MCS Set = ff ff 00 00 01
Sep 26 13:22:11 edubidu kernel: [ 1146.647985] <==== rt28xx_init, Status=0
Sep 26 13:22:11 edubidu kernel: [ 1146.659577] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659584] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659637] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659639] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659641] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659644] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659646] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659649] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659651] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659653] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659656] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659658] 0x1300 = ffffff10
Sep 26 13:22:11 edubidu NetworkManager: <info>  (ra0): driver does not support SSID scans (scan_capa 0x00).
Sep 26 13:22:11 edubidu NetworkManager: <info>  (ra0): new 802.11 WiFi device (driver: 'usb')
Sep 26 13:22:11 edubidu NetworkManager: <info>  (ra0): exported as /org/freedesktop/NetworkManager/Devices/3
Sep 26 13:22:11 edubidu NetworkManager: <info>  (ra0): now managed
Sep 26 13:22:11 edubidu NetworkManager: <info>  (ra0): device state change: 1 -> 2 (reason 2)
Sep 26 13:22:11 edubidu NetworkManager: <info>  (ra0): preparing device.
Sep 26 13:22:11 edubidu NetworkManager: <info>  (ra0): deactivating device (reason: 2).
Sep 26 13:22:11 edubidu NetworkManager: <info>  (ra0): supplicant interface state:  starting -> ready
Sep 26 13:22:11 edubidu NetworkManager: <info>  (ra0): device state change: 2 -> 3 (reason 42)
Sep 26 13:22:13 edubidu kernel: [ 1148.256303] -->RTUSBVenderReset
Sep 26 13:22:13 edubidu kernel: [ 1148.256424] <--RTUSBVenderReset
Sep 26 13:22:13 edubidu kernel: [ 1148.546574] CfgSetCountryRegion():CountryRegion in eeprom was programmed
Sep 26 13:22:13 edubidu kernel: [ 1148.546590] CfgSetCountryRegion():CountryRegion in eeprom was programmed
Sep 26 13:22:13 edubidu kernel: [ 1148.547225] Key2Str is Invalid key length(0) or Type(0)
Sep 26 13:22:13 edubidu kernel: [ 1148.547271] Key3Str is Invalid key length(0) or Type(0)
Sep 26 13:22:13 edubidu kernel: [ 1148.547318] Key4Str is Invalid key length(0) or Type(0)
Sep 26 13:22:13 edubidu kernel: [ 1148.549237] 1. Phy Mode = 9
Sep 26 13:22:13 edubidu kernel: [ 1148.549241] 2. Phy Mode = 9
Sep 26 13:22:13 edubidu kernel: [ 1148.592764] 3. Phy Mode = 9
Sep 26 13:22:13 edubidu kernel: [ 1148.601018] MCS Set = ff ff 00 00 01
Sep 26 13:22:13 edubidu kernel: [ 1148.611582] <==== rt28xx_init, Status=0
Sep 26 13:22:13 edubidu avahi-daemon[708]: Joining mDNS multicast group on interface ra0.IPv4 with address 192.168.1.105.
Sep 26 13:22:13 edubidu kernel: [ 1148.613895] 0x1300 = 00064300
Sep 26 13:22:13 edubidu avahi-daemon[708]: New relevant interface ra0.IPv4 for mDNS.
Sep 26 13:22:13 edubidu avahi-daemon[708]: Registering new address record for 192.168.1.105 on ra0.IPv4.
Sep 26 13:22:14 edubidu ntpdate[3444]: can't find host ntp.ubuntu.com
Sep 26 13:22:14 edubidu ntpdate[3444]: no servers can be used, exiting
Sep 26 13:22:15 edubidu avahi-daemon[708]: Registering new address record for fe80::21c:f0ff:fe1a:d32f on ra0.*.
Sep 26 13:22:15 edubidu wpa_supplicant[873]: WPS-AP-AVAILABLE 
Sep 26 13:22:15 edubidu kernel: [ 1150.557860] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1070
Sep 26 13:22:15 edubidu NetworkManager: <info>  Activation (ra0) starting connection 'Auto 2816-Modem'
Sep 26 13:22:15 edubidu NetworkManager: <info>  (ra0): device state change: 3 -> 4 (reason 0)
Sep 26 13:22:15 edubidu NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 26 13:22:15 edubidu NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Sep 26 13:22:15 edubidu NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Sep 26 13:22:15 edubidu NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Sep 26 13:22:15 edubidu NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Sep 26 13:22:15 edubidu NetworkManager: <info>  (ra0): device state change: 4 -> 5 (reason 0)
Sep 26 13:22:15 edubidu NetworkManager: <info>  Activation (ra0/wireless): connection 'Auto 2816-Modem' requires no security.  No secrets needed.
Sep 26 13:22:15 edubidu NetworkManager: <info>  Config: added 'ssid' value '2816-Modem'
Sep 26 13:22:15 edubidu NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Sep 26 13:22:15 edubidu NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Sep 26 13:22:15 edubidu NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Sep 26 13:22:15 edubidu NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> disconnected
Sep 26 13:22:15 edubidu NetworkManager: <info>  Config: set interface ap_scan to 1
Sep 26 13:22:16 edubidu wpa_supplicant[873]: Associated with 00:1c:df:76:d9:99
Sep 26 13:22:16 edubidu wpa_supplicant[873]: CTRL-EVENT-CONNECTED - Connection to 00:1c:df:76:d9:99 completed (auth) [id=0 id_str=]
Sep 26 13:22:16 edubidu NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> associated
Sep 26 13:22:16 edubidu NetworkManager: <info>  (ra0): supplicant connection state:  associated -> completed
Sep 26 13:22:16 edubidu NetworkManager: <info>  Activation (ra0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '2816-Modem'.
Sep 26 13:22:16 edubidu NetworkManager: <info>  Activation (ra0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 26 13:22:16 edubidu NetworkManager: <info>  Activation (ra0) Stage 3 of 5 (IP Configure Start) started...
Sep 26 13:22:16 edubidu NetworkManager: <info>  (ra0): device state change: 5 -> 7 (reason 0)
Sep 26 13:22:16 edubidu NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep 26 13:22:16 edubidu NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Sep 26 13:22:16 edubidu NetworkManager: <info>  Activation (ra0) Stage 3 of 5 (IP Configure Start) complete.
Sep 26 13:22:16 edubidu NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP4 Configure Get) started...
Sep 26 13:22:16 edubidu NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep 26 13:22:16 edubidu NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP6 Configure Get) started...
Sep 26 13:22:16 edubidu NetworkManager: <info>  Activation (ra0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep 26 13:22:16 edubidu NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP6 Configure Get) complete.
Sep 26 13:22:16 edubidu NetworkManager: <info>  Activation (ra0) Stage 5 of 5 (IP Configure Commit) started...
Sep 26 13:22:17 edubidu NetworkManager: <info>  (ra0): device state change: 7 -> 8 (reason 0)
Sep 26 13:22:17 edubidu NetworkManager: <info>  Policy set 'Auto 2816-Modem' (ra0) as default for routing and DNS.
Sep 26 13:22:17 edubidu NetworkManager: <info>  Activation (ra0) successful, device activated.
Sep 26 13:22:17 edubidu NetworkManager: <info>  Activation (ra0) Stage 5 of 5 (IP Configure Commit) complete.
Sep 26 13:22:17 edubidu kernel: [ 1152.190598] Rcv Wcid(1) AddBAReq
Sep 26 13:22:17 edubidu kernel: [ 1152.190605] Start Seq = 00000001
Sep 26 13:22:19 edubidu ntpdate[3634]: adjust time server 91.189.94.4 offset 0.019121 sec
Sep 26 13:22:24 edubidu kernel: [ 1158.948020] ra0: no IPv6 routers present
Sep 26 13:22:34 edubidu wpa_supplicant[873]: Trying to associate with 00:1c:df:76:d9:99 (SSID='2816-Modem' freq=2462 MHz)
Sep 26 13:22:34 edubidu kernel: [ 1169.050427] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1070
Sep 26 13:22:34 edubidu kernel: [ 1169.050944] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
Sep 26 13:22:34 edubidu wpa_supplicant[873]: Association request to the driver failed
Sep 26 13:22:34 edubidu NetworkManager: <info>  (ra0): supplicant connection state:  completed -> associating
Sep 26 13:22:34 edubidu wpa_supplicant[873]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 26 13:22:34 edubidu NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected
Sep 26 13:22:34 edubidu wpa_supplicant[873]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 26 13:22:35 edubidu wpa_supplicant[873]: last message repeated 2 times
Sep 26 13:22:35 edubidu wpa_supplicant[873]: Associated with 00:1c:df:76:d9:99
Sep 26 13:22:35 edubidu wpa_supplicant[873]: CTRL-EVENT-CONNECTED - Connection to 00:1c:df:76:d9:99 completed (reauth) [id=0 id_str=]
Sep 26 13:22:35 edubidu NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> associated
Sep 26 13:22:35 edubidu NetworkManager: <info>  (ra0): supplicant connection state:  associated -> completed
Sep 26 13:22:46 edubidu kernel: [ 1181.075891] Rcv Wcid(1) AddBAReq
Sep 26 13:22:46 edubidu kernel: [ 1181.075898] Start Seq = 00000001
Sep 26 13:23:14 edubidu kernel: [ 1209.306377] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 1014
Sep 26 13:23:20 edubidu kernel: [ 1214.996355] 5, flush one!
Sep 26 13:23:20 edubidu kernel: [ 1215.528335] 7, flush one!
Sep 26 13:23:23 edubidu kernel: [ 1218.491866] f, flush one!
Sep 26 13:23:27 edubidu kernel: [ 1222.475495] 13, flush one!
Sep 26 13:24:14 edubidu kernel: [ 1269.554348] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 1000[/HTML]tail -f /var/log/messages

[HTML]Sep 26 13:22:11 edubidu kernel: [ 1146.555588] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.556375] Key2Str is Invalid key length(0) or Type(0)
Sep 26 13:22:11 edubidu kernel: [ 1146.556421] Key3Str is Invalid key length(0) or Type(0)
Sep 26 13:22:11 edubidu kernel: [ 1146.556468] Key4Str is Invalid key length(0) or Type(0)
Sep 26 13:22:11 edubidu kernel: [ 1146.580947] 1. Phy Mode = 9
Sep 26 13:22:11 edubidu kernel: [ 1146.580953] 2. Phy Mode = 9
Sep 26 13:22:11 edubidu kernel: [ 1146.629399] 3. Phy Mode = 9
Sep 26 13:22:11 edubidu kernel: [ 1146.637403] MCS Set = ff ff 00 00 01
Sep 26 13:22:11 edubidu kernel: [ 1146.647985] <==== rt28xx_init, Status=0
Sep 26 13:22:11 edubidu kernel: [ 1146.659577] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659584] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659637] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659639] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659641] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659644] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659646] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659649] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659651] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659653] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659656] UsbVendorReq_semaphore get failed
Sep 26 13:22:11 edubidu kernel: [ 1146.659658] 0x1300 = ffffff10
Sep 26 13:22:13 edubidu kernel: [ 1148.256303] -->RTUSBVenderReset
Sep 26 13:22:13 edubidu kernel: [ 1148.256424] <--RTUSBVenderReset
Sep 26 13:22:13 edubidu kernel: [ 1148.546574] CfgSetCountryRegion():CountryRegion in eeprom was programmed
Sep 26 13:22:13 edubidu kernel: [ 1148.546590] CfgSetCountryRegion():CountryRegion in eeprom was programmed
Sep 26 13:22:13 edubidu kernel: [ 1148.547225] Key2Str is Invalid key length(0) or Type(0)
Sep 26 13:22:13 edubidu kernel: [ 1148.547271] Key3Str is Invalid key length(0) or Type(0)
Sep 26 13:22:13 edubidu kernel: [ 1148.547318] Key4Str is Invalid key length(0) or Type(0)
Sep 26 13:22:13 edubidu kernel: [ 1148.549237] 1. Phy Mode = 9
Sep 26 13:22:13 edubidu kernel: [ 1148.549241] 2. Phy Mode = 9
Sep 26 13:22:13 edubidu kernel: [ 1148.592764] 3. Phy Mode = 9
Sep 26 13:22:13 edubidu kernel: [ 1148.601018] MCS Set = ff ff 00 00 01
Sep 26 13:22:13 edubidu kernel: [ 1148.611582] <==== rt28xx_init, Status=0
Sep 26 13:22:13 edubidu kernel: [ 1148.613895] 0x1300 = 00064300
Sep 26 13:22:15 edubidu kernel: [ 1150.557860] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1070
Sep 26 13:22:17 edubidu kernel: [ 1152.190598] Rcv Wcid(1) AddBAReq
Sep 26 13:22:17 edubidu kernel: [ 1152.190605] Start Seq = 00000001
Sep 26 13:22:34 edubidu kernel: [ 1169.050427] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1070
Sep 26 13:22:34 edubidu kernel: [ 1169.050944] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
Sep 26 13:22:46 edubidu kernel: [ 1181.075891] Rcv Wcid(1) AddBAReq
Sep 26 13:22:46 edubidu kernel: [ 1181.075898] Start Seq = 00000001
Sep 26 13:23:14 edubidu kernel: [ 1209.306377] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 1014
Sep 26 13:23:20 edubidu kernel: [ 1214.996355] 5, flush one!
Sep 26 13:23:20 edubidu kernel: [ 1215.528335] 7, flush one!
Sep 26 13:23:23 edubidu kernel: [ 1218.491866] f, flush one!
Sep 26 13:23:27 edubidu kernel: [ 1222.475495] 13, flush one!
Sep 26 13:24:14 edubidu kernel: [ 1269.554348] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 1000
Sep 26 13:25:34 edubidu kernel: [ 1348.890299] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1169
Sep 26 13:27:14 edubidu kernel: [ 1449.318554] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1143
Sep 26 13:27:37 edubidu kernel: [ 1472.446254] ACT - Update2040CoexistFrameAndNotify. BSSCoexist2040 = 1. EventANo = 1. 
Sep 26 13:27:37 edubidu kernel: [ 1472.446262] ACT - BuildIntolerantChannelRep , Total Channel number = 1 
Sep 26 13:27:37 edubidu kernel: [ 1472.446266] ACT-BuildIntolerantChannelRep(Size=4)
[/HTML]Here is what my RT2870STA.dat is looking:

[HTML]#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=CH
ChannelGeography=1
SSID=2816-Modem
NetworkType=Infra
WirelessMode=9
Channel=11
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=1
Key1Str=mypassword
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
FastRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4[/HTML]When I use WPA2PSK key it's even worse. It don't connect for the most time but at random it connects :confused:

iwconfig
[HTML]ra0       Ralink STA  ESSID:"2816-Modem"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:1C:DF:76:D9:99   
          Bit Rate=81 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=84/100  Signal level:-79 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/HTML]my config.mk is like this:
[HTML]# Support ATE function
HAS_ATE=n

# Support QA ATE function
HAS_QA_SUPPORT=n

# Support XLINK mode
HAS_XLINK=n

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

#Support Net interface block while Tx-Sw queue full
HAS_BLOCK_NET_IF=n

#Support DFS function
HAS_DFS_SUPPORT=n

#Support Carrier-Sense function
HAS_CS_SUPPORT=n

# Support for Multiple Cards
HAS_MC_SUPPORT=n

#Support for IEEE802.11e DLS
HAS_QOS_DLS_SUPPORT=n

#Support for EXT_CHANNEL
HAS_EXT_BUILD_CHANNEL_LIST=n

#Support for Net-SNMP
HAS_SNMP_SUPPORT=n

#Support features of 802.11n Draft3
HAS_DOT11N_DRAFT3_SUPPORT=y

#Support features of Single SKU.
HAS_SINGLE_SKU_SUPPORT=n

#Support features of 802.11n
HAS_DOT11_N_SUPPORT=y
#Support features of Single SKU.
HAS_SINGLE_SKU_SUPPORT=n

#Support features of 802.11n
HAS_DOT11_N_SUPPORT=y

HAS_KTHREAD_SUPPORT=n

#Support statistics count
HAS_STATS_COUNT=y

#Client support WDS function
HAS_CLIENT_WDS_SUPPORT=n

#Support for Bridge Fast Path & Bridge Fast Path function open to other module
HAS_BGFP_SUPPORT=n
HAS_BGFP_OPEN_SUPPORT=n

#Support MAC80211 LINUX-only function
HAS_CFG80211_SUPPORT=n

#Support RFKILL hardware block/unblock LINUX-only function
HAS_RFKILL_HW_SUPPORT=n

HAS_RESOURCE_PRE_ALLOC=y
(...)[/HTML]


I had an older driver working on Hardy Heron, it worked without any problems. What am I doing wrong?


please help !

---

### Post by biltong on 2010-11-28
Hi everyone,

I also have a DWA-160 and it works fine out of the box with Maverik.... but only for a short while.

It pretty much makes a conenction (tried both WEP & WPA) I get full signal then after 2 Min. the connection drops. 

I also tried installing the new drivers from ralink, however I get compile errors (during make). "make: *** [LINUX] Error 2"

---

### Post by nanook62 on 2013-02-12
> **chili555 said:**
> First, you probably don't need ndiswrapper. Second, the most common issue is two or more conflicting drivers loading, which is fixed fairly easily with blacklisting.

May we please see:```
lsmod | grep -e ndis -e rt2
ls /etc/modprobe.d | grep -e ndis -e black
```Thanks.

Hi ! Well i did that and now I can't even find my D-Link DWA 140 USB-Dongel. Thank's a lot. How do i undo these things ?

---

### Post by kurt18947 on 2013-02-12
> **nanook62 said:**
> Hi ! Well i did that and now I can't even find my D-Link DWA 140 USB-Dongel. Thank's a lot. How do i undo these things ?

This is a pretty old thread.  You might have better luck starting a new one.

---

### Post by QIII on 2013-02-12
'nuff said.

Thread closed

---

