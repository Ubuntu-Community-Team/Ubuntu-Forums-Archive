---
title: "[SOLVED] Problem with atheros wifi AR242x in 8.10"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by Biochem on 2008-12-31
I can detect the wifi card on an Acer Aspire 5100.

the relevant output of **lspci -v** is
```
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device 0428
	Flags: fast devsel, IRQ 16
	Memory at 54000000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath_pci

```

Other possible useful information
```
Biochem@laptop:~$ lsmod | grep ath
ath_pci                99096  0 
wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci

```

```
Biochem@laptop:~$ sudo modprobe ath_pci
Biochem@laptop:~$ dmesg | tail -50
...
[   40.709418] hda-intel: Invalid position buffer, using LPIB read method instead.
[   47.072036] eth0: no IPv6 routers present
[  166.822017] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  166.835596] wlan: 0.9.4
[  166.842774] ath_pci: 0.9.4
[  166.842985] ath_pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  166.842997] ath_pci 0000:02:00.0: setting latency timer to 64
[  166.867618] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[  166.867631] ath_pci 0000:02:00.0: PCI INT A disabled

Biochem@laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


```

I also tried replacing the ath_pci with the ath9k using 
```
sudo modprobe -r ath_pci ath9k
sudo modprobe ath9k
dmesg | grep -e ath -e wlan
iwconfig
```

but it still doesn't work. I'm really clueless on what to do next. Anyone as a suggestion.

Thanks

---

### Post by luks911 on 2008-12-31
The drivers that work are the last madwifi version[0] (before compile and install it you have to disable the ath_pci you are using from System > Administration > Restricted Drivers Manager) or, more simple, the ath5k driver. To use ath5k install linux-backports-modules-intrepid
```
sudo aptitude install linux-backports-modules-intrepid
```
and then you can enable it in System > Administration > Restricted Drivers Manager, where you will saw a driver for Atheros 5xxx.

[0] [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz)

---

### Post by Biochem on 2008-12-31
Thanks Luks, that exactly what I was looking for.

For further reference I needed to blacklist the ath_pci module and load the ath5k module

---

### Post by Blue Snapper on 2009-01-11
Great tip Luks911 ... it seems to work for my HP dv6736nr latop wifi.
Got any idea how I can get a wifi status icon on the Panel?
I had one with 8.04 but seems gone with 8.10.

---

### Post by luks911 on 2009-01-11
In gnmoe you should have the Network Manager Applet (nm-applet). To try it type nm-applet in a terminal.
To add it in the startup go to System > Preferences > Sessions > Startup Program, click on Add and fill the blanks in this way:

Name: Network Manager
Command: nm-applet --sm-disable

and save it.

---

### Post by atsab on 2009-01-29
Hi Guys,
Glad you got your wireless sorted, i have the smae card have followed the instructions, i can see the suport for 5xxx serries in system >> administration >> hardware drives

but what do i do next

what and were do i need to black list

and how do i install [http://snapshots.madwifi-project.org...0081204.tar.gz](http://snapshots.madwifi-project.org...0081204.tar.gz)

---

### Post by luks911 on 2009-01-29
> **atsab said:**
> Hi Guys,
Glad you got your wireless sorted, i have the smae card have followed the instructions, i can see the suport for 5xxx serries in system >> administration >> hardware drives

but what do i do next

what and were do i need to black list

and how do i install [http://snapshots.madwifi-project.org...0081204.tar.gz](http://snapshots.madwifi-project.org...0081204.tar.gz)

Hi,
You have to go to system >> administration >> hardware drives
and there enable the suport for 5xxx serries. The system will tell you that you have to reboot. If this works, you don't have to install the madwifi driver ([http://snapshots.madwifi-project.org...0081204.tar.gz](http://snapshots.madwifi-project.org...0081204.tar.gz)) neither put in blacklist the ath_pci module.

---

### Post by atsab on 2009-01-29
Hey thanks for the speedy reply, i selected and restarted the System >> Admin >> Hardware Drivers

Says that the 5xxx driver is activated but not currently in use?

what's my next move?

---

### Post by luks911 on 2009-01-29
Well, try puting the ath_pci module in the blacklist. How? In a terminal:
```
sudo gedit /etc/modprobe.d/blacklist 
```
add a line like this
```
blacklist ath_pci
```
Now, reboot. And if the wifi doesn't work, look again in System > Administration > Hardware Drivers

---

### Post by atsab on 2009-01-29
ok i did as you asked but the driver is still active but not currently in use,

I think i might be missing something 

here is the relevant output of running the  sudo lshw -C network

```
 *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

```

is there any more info that i can provide that might help me to sort this configuration problem?

---

### Post by luks911 on 2009-01-29
Hmmm... well, the terminal is our friend, so you coul try load the module in that way. In a terminal:
```
sudo modprobe ath5k
```
now the wifi should work. If it works, to oad the driver in every start:
```
sudo gedit /etc/modules
```
and there add a line like this
```
ath5k
```

---

### Post by atsab on 2009-01-30
Right thank you so much for your help so far, the last step seems to have things working,
I can now see the other wireless networks in my area.

However i cant see my wireless network!

Iv turned off all encryption on it and made sure the router is broadcasting the essid!

my house mates can all see the wirless network and connect to it

Any idea what the problem is now?

---

### Post by luks911 on 2009-01-30
It's so strange, I don`t know and I'm not a networks expert. However, I can recommend you to install Wicd (wicd.sourceforge.net), that is a replacement for the network-manager and maybe it works better with your network. I paste here the instructions to installing it:

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

   ```
 deb http://apt.wicd.net hardy extras 
```

where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy, intrepid). You'll also need to add the key used for signing Wicd by running the following command in a terminal:

    ```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add - 
```

Now, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily.

---

### Post by atsab on 2009-01-30
Working fine now!

Thanks again for all the help really appreciate it, and you have saved me a lot of time and pain!

---

### Post by luks911 on 2009-01-30
Great! You're welcome.

---

### Post by JeremyA on 2009-01-30
Thank you!  Following your instructions, I have successfully configured the wireless on a new Acer Aspire 5515!

Thank you, thank you, thank you! \\:D/

---

### Post by aweller on 2009-02-08
I can't get this to work, any help is greatly appreciated.

Output of "lspci | grep Atheros":

```
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

The crazy thing is is that this was working perfectly before under "Ubuntu 8.10, kernel 2.6.27-9-generic" but now under "Ubuntu 8.10, kernel 2.6.27-11-generic" nothing...  (This was working under madwifi stuff.)

I have installed "linux-backports-modules-intrepid" and removed madwifi things.

I have double checked support for 5xxx drivers under System > Administration > Hardware Drivers (it's enabled).

I have removed/added "ath_pci" in /etc/modprobe.d/blacklist.

I have removed/added "ath5k" in /etc/modules.

I have installed Wicd.

The other crazy thing is is that I can see my wireless network under Wicd - I have not changed anything (WPA2, etc).  When I try to connect - nothing.  I'm lost and not too sure what to do anymore...

---

### Post by luks911 on 2009-02-08
What do you get in a terminal with iwconfig ?

---

### Post by aweller on 2009-02-08
Thanks for the reply luks911, but somehow this is fixed?!  I didn't do anything on my Ubuntu box, I just updated the firmware on my wireless modem, reset to factory defaults and started again.

A strange one as I didn't change any wireless configurations during/after an update...

---

### Post by canoemoose on 2009-02-08
W00t! This works perfectly on an abit AirPace with the ath5k drivers!!
Cheers muchly!!
Canoemoose

---

### Post by sam0vi on 2009-02-11
It totally worked for me and my LG E500 with am atheros 5007eg with the ar2425 chipset. I disabled the original driver thru system>administration>hardware drivers, rebooted the system, then i followed your instructions with the sudo.... thing, rebooted and it worked. i can't get it to connect (something about the password), but it's a great leap forward. Thanx so much luk911!

---

### Post by qrazi on 2009-02-11
Thanks, this also solved my problem with an Acer eMachines D620-261G16Mi.

---

### Post by drjimm on 2009-02-17
VOILA!  Luks911 was on the money.  I've spent hours on this and his solution did the trick.  Many thanks!  I usually have difficulty wading through forums for solutions. Got lucky this time.

---

### Post by diamondjim08 on 2009-02-17
Ok, with Ubuntu 8.10, I,ve got a new Acer Aspire 5515 with this seemingly very difficult wifi card, AR242X.  I've tried everything in these posts with no results for wifi.  WICD is loaded and works with hard wire but no wifi.  Drivers checked show that the card is using the driver 5xxxx for AR242X. The origional driver was deactivated.  My other notebook shows a wifi station present but this one can't see it.
iwconfig shows:
mashid@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
What should I do next?
Thanks, <> Jim

---

### Post by luks911 on 2009-02-23
> **diamondjim08 said:**
> Ok, with Ubuntu 8.10, I,ve got a new Acer Aspire 5515 with this seemingly very difficult wifi card, AR242X.  I've tried everything in these posts with no results for wifi.  WICD is loaded and works with hard wire but no wifi.  Drivers checked show that the card is using the driver 5xxxx for AR242X. The origional driver was deactivated.  My other notebook shows a wifi station present but this one can't see it.
iwconfig shows:
mashid@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
What should I do next?
Thanks, <> Jim

You could try with madwifi instead of ath5k. To download, compile and install the madwifi, follow the instructions below, one line each time in a terminal (you can copy and paste).

```
echo "blacklist ath_hal" | sudo tee -a /etc/modprobe.d/blacklist
echo "blacklist ath5k" | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get update && sudo aptitude install build-essential gcc binutils autoconf automake linux-headers-$(uname -r)
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3942-20090205.tar.gz
tar xzf madwifi-hal-0.10.5.6-r3942-20090205.tar.gz
cd madwifi-hal-0.10.5.6-r3942-20090205.tar.gz
make
sudo make install
sudo modprobe -a ath_pci wlan_scan_sta
sudo ifconfig ath0 up
echo "ath_pci" | sudo tee -a /etc/modules
```

All these put the ath5k driver in the blacklist, install all the tools that you need to compile, download de madwifi driver, compile and install it, then load the module and do the changes to load in every startup. 
After each kernel update, you will have to repeat this steps:
```
cd madwifi-hal-0.10.5.6-r3942-20090205.tar.gz
make
sudo make install
sudo modprobe -a ath_pci wlan_scan_sta

```
I hope it helps you.

---

### Post by dward526 on 2009-04-09
Thank You Very Much

This worked when the 8.10 upgrade killed my ndiswrapper setup in xubuntu

---

### Post by LesterPalooza on 2009-04-10
> **luks911 said:**
> The drivers that work are the last madwifi version[0] (before compile and install it you have to disable the ath_pci you are using from System > Administration > Restricted Drivers Manager) or, more simple, the ath5k driver. To use ath5k install linux-backports-modules-intrepid
```
sudo aptitude install linux-backports-modules-intrepid
```
and then you can enable it in System > Administration > Restricted Drivers Manager, where you will saw a driver for Atheros 5xxx.

[0] [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz)

Great tips luks. I installed the backport modules as you instructed and my wifi works great. The problem is, when the modules were installing, I think it overwrote my nvidia graphics kernel and im now running on low graphics setting. I tried reinstalling the drivers but didn't work... Please guide me if you can! Thanks a bunch!

---

### Post by ntlam on 2009-05-08
> **luks911 said:**
> You could try with madwifi instead of ath5k. To download, compile and install the madwifi, follow the instructions below, one line each time in a terminal (you can copy and paste).

```
echo "blacklist ath_hal" | sudo tee -a /etc/modprobe.d/blacklist
echo "blacklist ath5k" | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get update && sudo aptitude install build-essential gcc binutils autoconf automake linux-headers-$(uname -r)
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3942-20090205.tar.gz
tar xzf madwifi-hal-0.10.5.6-r3942-20090205.tar.gz
cd madwifi-hal-0.10.5.6-r3942-20090205.tar.gz
make
sudo make install
sudo modprobe -a ath_pci wlan_scan_sta
sudo ifconfig ath0 up
echo "ath_pci" | sudo tee -a /etc/modules
```

All these put the ath5k driver in the blacklist, install all the tools that you need to compile, download de madwifi driver, compile and install it, then load the module and do the changes to load in every startup. 
After each kernel update, you will have to repeat this steps:
```
cd madwifi-hal-0.10.5.6-r3942-20090205.tar.gz
make
sudo make install
sudo modprobe -a ath_pci wlan_scan_sta

```
I hope it helps you.

nice! Thanks!

---

