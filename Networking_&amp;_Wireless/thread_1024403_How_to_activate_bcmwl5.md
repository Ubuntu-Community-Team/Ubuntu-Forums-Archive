---
title: "How to activate bcmwl5"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by DaleFarrell on 2008-12-29
I'm ready to give up and load Windows. I cannot get this bcm4306 to access a wpa encrypted gateway. Have been trying for since Intrepid came out. Have tried wicd, ndis, fwcutter, this fig and that fig and nothing works. Windows Wireless Drivers shows the bcmwl5 installed. Hardware Drivers shows a b43 driver activated, without that I can't see any wireless activity. If I load this :sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwconfig wlan0 essid monkeybiz
sudo dhclient wlan0

sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwconfig wlan0 essid monkeybiz
sudo dhclient wlan0

now I can connect to gateway that has no security, but I have to reload
this code every reboot. I'm using an Emachine laptop. Can anybody help? Dale.

---

### Post by kevdog on 2008-12-29
Here is the workaround -- cut and paste to terminal

echo -e '#ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper


Now everytime ndiswrapper is loaded, the sudo modprobe statement will actually do what you want!!!

---

### Post by DaleFarrell on 2008-12-30
Kevdog I pasted your commands. No connection. If I paste in the first set of commands I can actually log on to the wpa gateway. I am using NetworkManager, not wicd. It doesn't seem right to have the b43 drivers "activated" in HardwareDrivers, and the
bcmwl5 drivers in WindowsWirelessDrivers. It looks like Ndiswrapper and fwcutter are
both working at the same time. Do I have to blacklist one of them, if so which one? I've read that ndiswrapper won't do encrypted security. You have gotten me farther along the path. Dale.

---

### Post by kevdog on 2008-12-31
If you are using the 4306 chipset, there are 3 revisions to that chipset.  You can find your revision number with

lspci -nnm

I'd probably recommend b43 to start. That simply means removing reference to ndiswrapper from the /etc/modules file and then do not manually modprobe ndiswrapper.

lshw -C network will show you the driver currently assigned to the card.

---

### Post by DaleFarrell on 2009-01-01
Here's output of lshw
dalejohnfiorillo@laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: wlan0
       version: 03
       serial: 00:90:96:77:55:b2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+ASUS,03/22/2004, 3.60.7.0 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

So it would appear that ndiswrapper is enabling the bcmwl5. If I re-paste the multiline command i can only connect to the non encrypted gateway.Ayuthia said that the b43 driver will NOT work with the rev3 chipset. I am going to go through all 3 of your suggested tutorials. Thanks for help. Dale.
OK>the top one was over my head, the second seemed irrelevant, and the third succeeded, sort of. If I paste all the commands in step 3, AND paste the commands at the first post I can connect to the wpa gateway. I have to redo this if I reboot. Here is the result of doing step 3:
dalejohnfiorillo@laptop:~$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
dalejohnfiorillo@laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
dalejohnfiorillo@laptop:~$ sudo depmod -a
dalejohnfiorillo@laptop:~$ sudo modprobe ndiswrapper
dalejohnfiorillo@laptop:~$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
dalejohnfiorillo@laptop:~$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

dalejohnfiorillo@laptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration contains directive install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
;you should delete that at /usr/sbin/ndiswrapper-1.9 line 868, <MODPROBE> line 135.
module configuration contains directive install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
;you should delete that at /usr/sbin/ndiswrapper-1.9 line 868, <MODPROBE> line 137.
dalejohnfiorillo@laptop:~$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
dalejohnfiorillo@laptop:~$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicantENABLED=0
dalejohnfiorillo@laptop:~$ 
          SHOULD I delete as it says? Should I ALSO delete as you suggested? It looks like ndiswrapper just get removed and reinstalled in both sets of commands. Very confusing, but I am now writing this with the wireless connection, so I,we,
must be just a command away. It's midnight here in Seattle----Happy New Year      Dale

---

