---
title: "RT2860 Signal Jumping &amp; Sometimes Disconnect"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by AdamShumpisxXx on 2009-04-28
I run Ubuntu Intrepid due to some Jaunty inadequacies and I'm having a problem with my RT2860 based Wireless N PCI card in my Desktop. I get odd signal decreases at various times. Sometimes (maybe once every 2 days?) I get a complete signal drop without the option to reconnect unless I restart my computer.

I installed the latest driver from here without issue:

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

I also edited my RT2860STA.dat file to mirror:

#The word of "Default" must not be removed
Default
WirelessMode=5

This has not solved my problem. I also run the newest Tomato 1.23 on my WRT54GL router which broadcasts a Wireless G signal. Does anyone know enough to help me? I would be willing to update my kernel or whatever but I am not willing to upgrade to Jaunty as it doesn't allow me to run my ATI Sapphire x1950xt the way I would like. Thank you in advance!

---

### Post by AdamShumpisxXx on 2009-04-28
Oh I should also add a couple things.

I'm on a wireless only Desktop. I don't have the option to plug an ethernet cord into my computer. I tried WICD but I got NO SIGNAL and I was unable to connect to any wireless networks. The signal also seems to get worse when I use more bandwidth, strangely.

Thanks again. Sorry for the shameless bump, haha!

---

### Post by mauro24 on 2009-04-29
hey adam, I'm looking for help, could you show me how to install that driver, I new to linux, I don't know the commands, I'm running Ubuntu 9.04 on my eee box pc, the network manager sees the wireless networks, but it can't connect, it keeps asking me for the password, it could work if i install that new driver v2.1.1.0

---

### Post by AdamShumpisxXx on 2009-04-30
OK. Here's the tutorial I used. I will edit it slightly to mirror the new driver version. You should not have to use this though as Jaunty has this driver in the kernel already...

--------------------------------------------------------------------------

First you are going to need the driver package, which can be downloaded from: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

You are looking for the "RT2860PCI/mPCI/PCIe/CB(RT2760/RT2790/RT2860/RT2890" package. Download it and save it to your home directory.

Start a terminal and install the build-essential and linux-headers packages (if you don't have them already):

sudo aptitude install linux-headers-`uname -r` build-essential

Now, in your home folder untar the Ralink package.Open "2009_0424_RT2860_Linux_STA_V2.1.1.0.tgz" and extract the full contents into the same folder. It should come out as a folder called "2009_0424_RT2860_Linux_STA_V2.1.1.0".

Edit the 2009_0424_RT2860_Linux_STA_V2.1.1.0/os/linux/config.mk file to allow network-manager to manage the card:

Code:

gedit 2009_0424_RT2860_Linux_STA_V2.1.1.0/os/linux/config.mk

Where it says:

Quote:
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Manager
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

Make sure that both lines have a "y" after them (by default they have an "n"), then save the file.

Now enter the 2009_0424_RT2860_Linux_STA_V2.1.1.0 directory, compile and install the driver as root:

Code:

cd 2009_0424_RT2860_Linux_STA_V2.1.1.0/
sudo su
make && make install

It is important here not to use "sudo" alone, but "sudo su" because with sudo for some reason the installation script fails to create the necessary files and folders in among others /etc. This is what caused me some trouble before I figured it out.

Now, while still root modprobe the driver module:

Code:

modprobe rt2860sta

Give it a minute to create the ra0 device node, and network manager should now be able to display all visible wireless networks in your area, meanwhile you can stop being root and make sure that the module was probed correctly by checking the output of lsmod looking for the rt2860sta module.

Code:

exit
lsmod | grep rt2860sta

It should output something like "rt2860sta 525400 1". To make sure that ra0 is up and running as it's supposed to you can run "iwconfig" which should output something like this:

Code:

iwconfig

lo        no wireless extensions.

eth1      no wireless extensions.

ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point:   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-29 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Hopefully all of this worked and your wireless card is now functional. Use network manager to set your WEP/WPA(2) or what have you and connect to your network.

To make sure the module is loaded when you reboot, add it to the /etc/modules file:

Code:

sudo su
echo rt2860sta >> /etc/modules

--------------------------------------------------------------------------

I hope this helps you. Can anyone help me?

---

### Post by AdamShumpisxXx on 2009-04-30
Oh man. I can't believe I didn't catch that before! I doubt your problem is with your driver. You're being asked for a password because your wireless connection is protected. You need to know the WEP/WPA password the router is looking for. Try connecting to another wireless router without protection and see how that goes OR just type in the password if you know it.

Also, please make a new thread separate from this as our issues seem to be completely different.

Any help for me now? Hahaha!

---

### Post by AdamShumpisxXx on 2009-05-01
Bump...

---

### Post by mauro24 on 2009-05-12
Thanks for the help, I worked out perfectly after I installed the driver,sorry for no responding fast enough.  Later:P

---

