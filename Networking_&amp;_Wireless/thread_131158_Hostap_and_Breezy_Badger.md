---
title: "Hostap and Breezy Badger"
date: 2006-02-15
forum: Networking &amp; Wireless
---

### Post by Nyati on 2006-02-15
I need help configuring the hostap driver in the kernel. I've attempted following the wiki but that is only for Hoary Hedgehog. All seems to work until I get to step 5:

#

Install the module

    cd ..
    dpkg -i hostap-modules-XXXXX.deb 

and I get the response:

root@DamuAskari:~# dpkg -i hostap-modules-2.6.12-9-386.deb
dpkg: error processing hostap-modules-2.6.12-9-386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 hostap-modules-2.6.12-9-386.deb

Why?

I have a Zcom XI-325 wireless card that has a Prism2.5 chipset.

Any Help?

Thanks in advance!

---

### Post by mpvano on 2006-02-15
The hostap modules are already installed in breezy.

Where did you get that package - it shouldn't match your kernel if you've kept your breezy up to date. The current breezy kernels are 2.6.12-10... That's why it won't install. If you haven't done anything else to ruin your existing system, you were probablly saved by that fact. DON'T TRY TO INSTALL ANOTHER PACKAGE.

It would help to know why are you trying to use hostap. 

if you just want to use the client driver (I do that, myself), then everything you need is already installed but you might want to install the hostap-utils package which can be useful for some things. I suggest installing it.

For more exotic uses (i.e. access points, sniffers, etc), you will need to install the hostapd package, but this is normally not needed for using the card as a simple wireless client.

Your card should already be working properly WITHOUT hostap before you try to install hostap.

All the cards it supports work with other drivers just fine, and if your card was found, it should already have caused the orinoco, hermes or prism drivers to be loaded, since they are considered the "preferred" drivers.

If you're trying to install the hostap driver because you can't make wireless work and you think that will fix things, that's probably not your problem. Get the card working first with the normal drivers.

I use the hostap drivers because scanning for access points is not currently supported in any of the "preferred" drivers. I find scanning useful for sorting out overlapping access points when I am roaming. Otherwise, the normal drivers work fine.

If (like me), you have such a need for the hostap drivers, you will need to find out what kind of drivers are currently in use for your card, figure out what loaded them, and blacklist them in /etc/hotplug/blacklist.d, /etc/pcmcia/config, /etc/modules, or wherever it was they were being loaded from. or hostap will not be used - it's the last choice...

My card is a pci card so I installed hostap-utils and then had to add the following to /etc/hotplug/blacklist.d in a file I created named "wireless"

orinoco
orinoco_cs
orinoco_pci
prism2
prism54

On the next reboot the hostap drivers were loaded, but your mileage may vary....

By the way, be careful editing files in these blacklist directories. Most of them read ALL files in the directory regardless of name. This means that if your editor keeps backup files, THE BACKUP FILE IS STILL INFLUENCING THE CONFIGURATION.... This can be VERY confusing. Delete any backup files from edits before testing things.

If you have a pcmcia card (not a cardbus card - they look similar)  or are using ndiswrapper as a driver, my example will not suppress loading your existing drivers. Those cards are loaded by different configuration files.

WARNING!: I had a lot of trouble with hostap until I discovered that earlier installs of my wireless drivers had placed an entry in /etc/iftab which forced renaming of my adapter as eth0.

This COMPLETELY broke hostap because it uses very different naming conventions and installs more than one "psuedo-driver".

Commenting out that entry allowed me to use hostap with my prism2 based card with the interface names working reliably as per the hostap documenation.

hope this helps,

Mario

---

### Post by Nyati on 2006-02-15
Hi Mario

Thanks, but I need help with this as I'm clueless to what is happening, after attempting to do this so many times, I've probably broken too many things.

I think my best bet is that I reinstall 5.10. But, before I do this, I have a problem, my card, which is a pcmcia card, is not detected. Do you have an idea why?

Thanks

---

### Post by mpvano on 2006-02-16
Could you provide a little more information? You've not really said enough for anyone to help you. Try answering as many of the following questions as you can.

Are you using a  breezy installation or the live CD?
Are you just trying to connect to an existing network, or trying to do something more complicated?
Have you installed all the current updates?
What make and model of machine - exactly?
What make and model of card - exactly?
Do you know if it is a Cardbus or PCMCIA card?
Is there other networking hardware in the machine, and is it working?
What kind of network are you trying to connect to - exactly?
What kind of access point hardware is it?
How is it connected to the internet?
How is the access point configured?
Does the access point use any sort of security - if so, what kind?
Does the access point use MACID filtering to restrict who can use it?
Is it the ONLY access point within range?
Is the access point working with other machines?
Have you tried the card in another machine?
Have you tried the card in your machine under another OS?
How did you decide your card was "not detected"?
What sorts of things have you already tried?
What other software packages or source modules have you installed or tried to install besides the basic Breezy installation.

If possible restart your machine without the PCMCIA card installed and then plug in the card run the following commands in a terminal and cut and paste ALL of the results into your next message (NOTE- Replace any security keys with DUMMY ONES in your message)...

sudo lshw -C NETWORK

sudo iwconfig

sudo iwlist scan

cat /etc/network/interfaces


Most of the people who might answer your request in this forum (including me) are just ordinary forum members like yourself, so don't assume you'll get answers immediately, or that we have all of them. We're mostly just sharing our own experiences, but we'll see what we can do...

Mario

---

### Post by Nyati on 2006-02-16
Hi Mario

Are you using a breezy installation or the live CD?         - Breezy Installation

Are you just trying to connect to an existing network, or trying to do something more complicated?            - More complicated, roaming etc.

Have you installed all the current updates?               - Yes

What make and model of machine - exactly?            - IBM T30

What make and model of card - exactly?                   - Zcom XI-325

Do you know if it is a Cardbus or PCMCIA card?         - PCMCIA

Is there other networking hardware in the machine, and is it working?          - No

What kind of network are you trying to connect to - exactly?           - Any wireless network

What kind of access point hardware is it?           - Unknown

How is it connected to the internet?            - Unknown

How is the access point configured?           - Unknown

Does the access point use any sort of security - if so, what kind?           - Unknown

Does the access point use MACID filtering to restrict who can use it?     - Unknown

Is it the ONLY access point within range?           - Unknown

Is the access point working with other machines?           - Unknown

Have you tried the card in another machine?             - No

Have you tried the card in your machine under another OS?           - No

How did you decide your card was "not detected"?            

:~$ sudo lshw -C NETWORK
Password:
  *-network DISABLED
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:c2:d7:42
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.8-k2-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
       resources: iomemory:d0200000-d0200fff ioport:8000-803f irq:11


What sorts of things have you already tried?         - The above plus:

~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ppp0      no wireless extensions.

and

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.

and

$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

What other software packages or source modules have you installed or tried to install besides the basic Breezy installation.              - hostap-utils and hostapd


I haven't tried to edit any of the blacklist files as I don't think that's the key to the problem yet.

I hope this helps!

---

### Post by Nyati on 2006-02-16
Hi Mario, progress I hope

I typed in the following command: sudo ifconfig eth0 up

I then typed in: lshw -C NETWORK

and therefore enabled the ethernet network interface...I think. I got the following:

*-network
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:c2:d7:42
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.8-k2-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
       resources: iomemory:d0200000-d0200fff ioport:8000-803f irq:11

but I still get: 

sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ppp0      no wireless extensions.

and

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.

and

cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0


?

---

### Post by mpvano on 2006-02-16
Hmmm, good job of collecting info.....

It's going to be a little tricky getting you going if you don't have an access point to experiment with - I gather you're playing around in coffee shops or something...

Anyway, Here's what I think the problem is - 

I don't believe that your card is listed in the file /etc/pcmcia/config. This file tells the pcmcia subsystem what to do when a card is plugged in. With no matching entry, no driver is associated with the card.

PCMCIA cards are identified by the computer by means of a unique vendor ID and model number. I did some poking around on google and found some information about a similar card. Unfortunately, it's hard to tell if it's correct or not.

Here's how you find out...

Plug in the card - please report if you hear any beeps, if so, do you hear one or two....

Run the following command:

/etc/pcmcia$ cardctl info

This will display info about pcmcia cards in the two slots...

You should see something like this: (this is the display for a Lucent Orinoco gold card in my IBM T30)

PRODID_1="Lucent Technologies"
PRODID_2="WaveLAN/IEEE"
PRODID_3="Version 01.01"
PRODID_4=""
MANFID=0156,0002
FUNCID=6
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

 If it's a cardbus card, you may not see any information like this. Let me know if both card slot's lines are empty and we'll proceed a different way from there...

For the record, here's the info somebody else supposedly found out about a card like yours...

 product info: " ", "IEEE 802.11 Wireless LAN/PC Card", ""
 manfid: 0xd601, 0x0005
 function: 6 (network)

If your card is really a pcmcia card, what you need to do is add an entry for it in the file /etc/pcmcia/config, since there isn't one there that matches exactly.

There's an entry for a similar card like this in that file.

card "ZCOMAX AirRunner/XI-300"
  #version "ZCOMAX", "AirRunner/XI-300"
  manfid 0xd601, 0x0002
  bind "orinoco_cs"

I'd try (using sudo) editing this entry by changing the product info after "card" and the "manfid" line to match the info and the "manfid" numbers from your card - these are the identification used for pcmcia matching in linux.

save the file, making sure to delete any backup files created.

Then try restarting and see what happens when you plug the card in.

If it finds a driver, it will beep twice shortly after you plug the card in.

Try the commands I gave you before again and let's see if the card shows up. Then we can worry about getting it configured....

Mario

---

### Post by Nyati on 2006-02-17
Hi Mario

I added an entry into the config just like you suggested and reinserted the card. It beeped twice.

It also beeped twice before I edited the config.

Anyway, if I run: lshw -C NETWORK

I get *-network DISABLED
......
....
.

and then have to run: ifconfig eth0 up, to enable the network. I presume I need to set this in a config file, I'll have a look.

So, I'm still getting the same print out as before when I type in the commands:

lshw -C NETWORK
iwconfig
iwlist scan
cat /etc/network/interfaces

---

### Post by mpvano on 2006-02-17
I don't see your card in that list. All I see is the wired ethernet ntework adapter in your T30. What you've done is to enable your wired interface.

Did you recover the cardinfo I requested in my last post? This is highly likely to be the cause of your problem. It appears that your card vendor has changed the card identification that allows Ubuntu to recognize the card (or that cardmanager has it wrong).

Note also that lshw doesn't CHANGE anything it just reports on what it finds. Like many of the othre commands we're using here,  It also may give out of date or incomplete information if you don't run it using sudo (but that may just have been  a typo).

Mario

---

### Post by Nyati on 2006-02-17
I've attempted various version to the edit for the ZCOMAX card.

I did some research on the net and found my card to be zcomax card, so i inserted another zcomax card like so:

card "ZCOMAX/XI-325"
   #version "ZCOMAX", "XI-325"
   manfid 0xd601, 0x0002
   bind "orinoco_cs"

I tried the following versions

card "ZCOMAX XI-325"
   #version "ZCOMAX", "XI-325"
   manfid 0xd601, 0x0005
   bind "orinoco_cs"

and

card "ZCOMAX XI-325"
   #version "ZCOMAX", "XI-325"
   manfid 0xd601, 0x0005
   bind "Prism2_cs"

Rebooted, inserted card to the sound of 2 beeps

then proceeded with the following:

sudo cardctl info

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

sudo lshw -C NETWORK
sudo iwconfig
sudo iwlist scan
sudo cat /etc/network/interfaces

The last 4 commands returned the same as before.

---

### Post by mpvano on 2006-02-17
I don't think there's any driver named "Prism2_cs", so I'd b surprised if that did anything, The prism 2 driver is called "prism2", so you might try that instead - but the orinoco_cs entry should also have done something.

It DOES sound like, however, the corrected product ID for the card has made a difference.

It really sounds like we're missing something obvious. The computer beeping twice when you plug in the card normally means your card has been recognized.

Try reviewing the output of lspci and lshw again. You can slso see if it shows up if you use "cardinfo", a gui based card information utility.

You can also try seeing if the driver has been loaded by looking for it in the output of the "lsmod" command. things to look for in this list include any drivers with the following in their names: orinoco, prism, ndiswrapper, hostap, hermes, etc.

Another useful thing to do would be to try monitoring the log file /var/log/daemon.log.  Use the command:

tail -f /var/log/daemon.log

and watch closely for changes in the output as the card is plugged in and the beeps occur. Do the same when the card is removed.

Here's what I get when I plug an (unconfigured) orinoco gold card into my T30 - note of course that though the card is recognized, the ifup fails because I am currently using other cards with drivers that have different names.

Here's what appears when the card is plugged in:
Feb 17 11:06:05 targ3 cardmgr[27439]: socket 0: Lucent Technologies WaveLAN/IEEE Adapter
Feb 17 11:06:05 targ3 cardmgr[27439]: executing: 'modprobe orinoco_cs'
Feb 17 11:06:05 targ3 cardmgr[27439]: executing: './network start eth0'
Feb 17 11:06:05 targ3 cardmgr[27439]: + Ignoring unknown interface eth0=eth0.


and here's what is seen when it's unplugged:

Feb 17 11:06:58 targ3 cardmgr[27439]: executing: './network stop eth0'
Feb 17 11:06:58 targ3 cardmgr[27439]: + eth0: error fetching interface information: Device not found
Feb 17 11:06:58 targ3 cardmgr[27439]: + /sbin/ifdown: interface eth0 not configured
Feb 17 11:06:58 targ3 cardmgr[27439]: executing: 'modprobe -r orinoco_cs'

Since your card is not configured, either, you should see similar network control errors, but the messages should still tell you whether a driver has been loaded or not, and if so, which one.

Mario

---

### Post by Nyati on 2006-02-17
Mario

Progress at last. Changed the driver description in the .config file from Prism2 to prism2 and got a different reponse when I plugged in the card.

Initially when it beeped twice before, the beeps weren't the same, now they are.

Commands produce different results too.

# sudo cardctl info
PRODID_1=" "
PRODID_2="IEEE 802.11 Wireless LAN/PC Card"
PRODID_3=""
PRODID_4=""
MANFID=d601,0005
FUNCID=6
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

# sudo lshw -C NETWORK
  *-network
       description: IEEE 802.11 Wireless LAN/PC Card
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network DISABLED
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:c2:d7:42
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.8-k2-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
       resources: iomemory:d0200000-d0200fff ioport:8000-803f irq:11
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:60:b3:8d:7b:95
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap driverversion=0.4.1 - 2005-05-22 firmware=1.3.6 multicast=yes wireless=IEEE 802.11-DS

# sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Warning: Driver for device wifi0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wifi0     IEEE 802.11-DS  ESSID:"test"
          Mode:Master  Access Point: 00:00:01:7D:E1:B7   Bit Rate:11 Mb/s
          Sensitivity=49076/3
          Retry min limit:49076   RTS thr=6 B   Fragment thr=52096 B
          Encryption key:off
          Power Management period:52.9459s  mode:All packets received

wlan0     IEEE 802.11-DS  ESSID:"test"
          Mode:Master  Access Point: 00:00:01:7D:E1:B7   Bit Rate:11 Mb/s
          Sensitivity=49076/3
          Retry min limit:49076   RTS thr=6 B   Fragment thr=52096 B
          Encryption key:off
          Power Management period:54.0191s  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.

# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

Warning: Driver for device wifi0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wifi0     No scan results
wlan0     No scan results
ppp0      Interface doesn't support scanning.

# sudo cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #3) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801CA/CAM SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
0000:02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:02:08.0 Ethernet controller: Intel Corp. 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)

Card shows up in cardinfo.

Next post following shortly!

---

### Post by Nyati on 2006-02-17
I typed the command while the card was plugged in:

~$ tail -f /var/log/daemon.log
Feb 17 22:46:10 localhost cardmgr[6980]: executing: './network stop wlan0'
Feb 17 22:46:11 localhost cardmgr[6980]: + wlan0: error fetching interface information: Device not found
Feb 17 22:46:11 localhost cardmgr[6980]: + /sbin/ifdown: interface wlan0 not configured
Feb 17 22:46:11 localhost cardmgr[6980]: executing: 'modprobe -r hostap_cs'
Feb 17 22:46:11 localhost cardmgr[6980]: executing: 'modprobe -r hostap'
Feb 17 22:46:14 localhost cardmgr[6980]: socket 0: Zcomax XI-325H 200mW
Feb 17 22:46:14 localhost cardmgr[6980]: executing: 'modprobe hostap'
Feb 17 22:46:14 localhost cardmgr[6980]: executing: 'modprobe hostap_cs'
Feb 17 22:46:14 localhost cardmgr[6980]: executing: './network start wlan0'
Feb 17 22:46:14 localhost cardmgr[6980]: + Ignoring unknown interface wlan0=wlan0.

and when the card was unplugged:

~$ tail -f /var/log/daemon.log
Feb 17 22:46:10 localhost cardmgr[6980]: executing: './network stop wlan0'
Feb 17 22:46:11 localhost cardmgr[6980]: + wlan0: error fetching interface information: Device not found
Feb 17 22:46:11 localhost cardmgr[6980]: + /sbin/ifdown: interface wlan0 not configured
Feb 17 22:46:11 localhost cardmgr[6980]: executing: 'modprobe -r hostap_cs'
Feb 17 22:46:11 localhost cardmgr[6980]: executing: 'modprobe -r hostap'

---

### Post by mpvano on 2006-02-18
It looks like your card is recognized and the hostap driver is being loaded by the ifup/down scripting that is installed with the hostap-utils package.

The unknown interface error just means that there is no entry in the file /etc/network/interfaces telling the system what to do with it.

You should probably do a

cat /etc/network/interfaces

and show the result, but we'll fix that later. Let's see if we can confirm that the driver is actually loaded:

lsmod | grep hostap

should display some lines containing modules that are loaded that contain the word 'hostap' in their names.

Also please show the output of  

sudo iwconfig wlan0

again.

Please confirm that you have installed the package named "hostap-utils", and also please confirm that you have NOT tried to build the hostap package from source files - if you tried to rebuild these packages instead of using the ones supplied with ubuntu, you probably have installed corrupted modules or installed unknown scripts to modify the behavior of your system.

Otherwise, It looks like your attempts to install hostap succeeded - let's try and make sure hostap works with your card, and that you only have one driver loaded. Send the output of the following commands as well.

lsmod | grep prism
lsmod | grep orinoco

hang in there... we're actually getting somewhere

Mario

---

### Post by Nyati on 2006-02-18
Mario

Firstly the commands

:~$ lsmod | grep hostap
hostap_cs              53528  1
hostap                102152  1 hostap_cs
pcmcia                 24584  5 hostap_cs
pcmcia_core            44932  4 hostap_cs,pcmcia,yenta_socket,rsrc_nonstatic

:~$ sudo iwconfig wlan0
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11b  ESSID:"test"
          Mode:Master  Access Point: 00:00:00:00:00:00   Bit Rate:11 Mb/s
          Sensitivity=1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I have installed 'hostap-utils' from the repository, not source files.

:~$ lsmod | grep prism

no results

:~$ lsmod | grep orinoco

no results

:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

---

### Post by mpvano on 2006-02-20
Hi:

Sorry I didn't check in with you for a while. I had other concerns here....

I've kind of lost track of how we got here (!), but it appears that hostap is now loaded and running.

In theory, you should be able to associate with an access point if you are in range of one. The gnome network-manager applet is used by a lot of people with success, but I've never found it to be particularly reliable. If you'd like, you can give that a try.

Here's the approach I use, and it works well for me. One benefit of the hostap driver is that scanning works (it is broken in the other prism drivers). This means that if you are in range of one or more access point it should show up in a "sudo iwlist wlan0 scan" command. This means that you SHOULD be able to get complete information about connecting to an access point by running the command.

I then use this information to construct an /etc/network/interfaces file for the access point and keep it filed away ready for use. I use a simple scripting system to run an "ifdown -a" to disable the existing networking, swap in the correct files for different access points, and then run an "ifup" command as appropriate to start the networking up again.

To have any luck with this at all, you'll need to read the "interfaces" and "ifup" man pages - I can't really be much help remotely.

To get you started, however, here's a skeleton network interfaces file that may work for you if you can find an open access point that's not in an area with overlapping coverage. Even if there's overlapping coverage, you may be able to use it as a starting point by adding more specific essid, channel and other wireless commands as needed....

In theory, if you edit /etc/network/interfaces to look like this (you can skip the comment lines), you should be able to ifup and ifdown eth0 and wlan0 as needed to enable and disable them, and the wireless network should be enabled at boot or wakeup.

In reality, you may need to add a lot more detail to make things work as you expect. In particular, you need to remember that everytime you connect to anything by DHCP, it will change your DNS settings to values that probably only work on that network. The interfaces file allows adding a lot of additional lines to copy files, run arbitrary shell commands and use more complex wireless configuration commands as needed to enable closed network keys, etc....

I'm not sure at the moment if hostap accepts the "any" essid value. You may need to get the actual essid of the access point  (using sudo iwlist wlan0 scan) and insert it into the file instead of any"

-------------------------------------------------------------

# auto defines which interfaces the ifup -a command will start
# This is used widely at boot, wake-up etc to configure networking
auto lo wlan0

# The loopback network interface definition
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# that can be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map wlan0 eth0

# This describes what to do to "ifup" wlan0
# This simple example works with some cards for open networks
# other cards need more detailed wireless-... commands (which are
# actually used to run iwconfig commands during ifup...
iface wlan0 inet dhcp
wireless-key off
wireless-essid any

# This definition is used to bring up your wired interface, but it
# is always needed so that ifdown knows how to shut it down.
# You may need to change this to eth1 for your machine, or if
# you have more than one interface, you may need both eth0 and eth1
# definitions
iface eth0 inet dhcp

#--------------------------------- end of file


From here you should be able to find out a lot more from the dozens of threads on this subject in this forum and from the Ubuntu wiki entries on wireless. Be careful to take everything with a grain of salt, however, and make sure you know how to undo anything you've done...

Mario

---

### Post by Nyati on 2006-02-21
Thanks for all your help!

---

