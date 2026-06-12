---
title: "Wireless issue on Gateway Laptop"
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by jhargis1012 on 2011-01-16
Hello.

I am using a Gateway laptop (model MT6458, several years old) and am very inexperienced with Linux.

I recently downloaded Ubuntu 10.04. It seems to work fairly well as I have sound, good picture, and can get on the Internet with an Ethernet cable. However, Ubuntu currently does not recognize my internal wireless card.

I realize there are countless threads addressing this very issue. I have been trying to work through them, but have run into some problems. Currently, I'm trying to follow this guide:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I've gotten to point 3.1 and am stuck on all that "blacklist" stuff. I don't understand what it is I need to type exactly. I was thinking I was supposed to take that text box word for word (except substituting all the instances of blacklist for blacklist.conf). I did this, and I'm not sure if it worked. Here's what I see:

jhargis1012@jhargis1012-laptop:~$ echo -e "blacklist.conf bcm43xx\nblacklist.conf b43\nblacklist.conf b43legacy\nblacklist.conf ssp"
blacklist.conf bcm43xx
blacklist.conf b43
blacklist.conf b43legacy
blacklist.conf ssp
jhargis1012@jhargis1012-laptop:~$ sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password for jhargis1012: 

After that, I typed in my password, hit enter, and nothing seemed to happen. Did it work?

Also, I know the lspci command lists hardware, but I can't figure out what the title of my wireless card is from looking at the output (I believe I need this information to use the graphical version of ndiswrapper to find a windows driver to use later on):

jhargis1012@jhargis1012-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 2a08 (rev 03)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
jhargis1012@jhargis1012-laptop:~$ 

(I'm guessing it's that Marvell Technology... Device 2a08, etc...)

I'd appreciate any help as I would really like to get this working wirelessly. Thanks a bunch.

---

### Post by chili555 on 2011-01-16
May we see:```
lspci -nn | grep -i ether
```Thanks.

Do you have the Windows XP ethernet driver; i.e. .inf file for your ethernet card? If not, ndiswrapper is useless.

---

### Post by jhargis1012 on 2011-01-16
jhargis1012@jhargis1012-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:2a08] (rev 03)
08:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
08:09.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
08:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
jhargis1012@jhargis1012-laptop:~$ 


When I typed "grep -i ether" nothing happened.

About the .inf file, I can probably get that from the card manufacturer's website, correct?

Just to reiterate, I am trying to get only the wireless to work at this point. The ethernet port works just fine.

---

### Post by chili555 on 2011-01-16
> When I typed "grep -i ether" nothing happened.
That's because it's:```
lspci -nn | grep -i ether
```All in one command using the pipe symbol | located on the right side of my US keyboard along with \.

I believe this is a wireless card:> 05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:2a08] (rev 03)More in a few minutes; I'm looking for the .inf.

---

### Post by chili555 on 2011-01-16
Make sure your ethernet is connected so you can download things. Open System > Administration > Synaptic. Search for ndisgtk and install it if it's not already. Also install cabextract, unshield and unzip. Now in a terminal, do:```
mkdir wireless
cd wireless
wget http://firmware.netgear-forum.com/WN511T/wn511t_3_0_setup.zip
unzip wn511t_3_0_setup.zip
cabextract wn511t_3_0_setup.exe
cd Disk1
unshield x data1.cab
cd Win2KXP_Target/ && ls
```There is your .inf and needed .sys files. Now do:```
ndisgtk
```A little window will open and ask you to browse to the .inf file. Point it to wireless > Disk1 > Win2KXP_Target and then to NetMW14x.inf. Now in the terminal, do:```
sudo ndiswrapper -a 11ab:2a08 netmw14x
sudo modprobe ndiswrapper
iwconfig
```Now do you have a wireless interface wlan0? Detach the ethernet cable, click the Network Manager icon and connect.

---

### Post by jhargis1012 on 2011-01-17
Thanks a bunch for getting back to me.

I followed all the steps, but I don't think it is working.

Here's what I see for the last bit:


jhargis1012@jhargis1012-laptop:~$ sudo ndiswrapper -a 11ab:2a08 netmw14x
Driver 'netmw14x' is already used for '11AB:2A08'
jhargis1012@jhargis1012-laptop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
jhargis1012@jhargis1012-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jhargis1012@jhargis1012-laptop:~$ 


When I unplug the ethernet, I lose the connection. When I go to the wireless networks section of the connections manager, I don't see anything.

---

### Post by chili555 on 2011-01-17
Let's have a peek at:```
ndiswrapper -l
```That's a lower-case L for 'list.'

---

### Post by jhargis1012 on 2011-01-17
jhargis1012@jhargis1012-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netmw14x : driver installed
	device (11AB:2A08) present
jhargis1012@jhargis1012-laptop:~$ 


There ya go.

Side note: In the network settings, I thought maybe I needed to manually set up a wireless connection (by putting in the SSID, WEP key and whatnot). I tried that, but still nothing.

---

### Post by jhargis1012 on 2011-01-17
(oops, don't know why the eight next to a bracket transformed into a smiley. lol)

---

### Post by chili555 on 2011-01-17
That looks pretty healthy. Let's see if there are any messages that will tell us why an interface, wlan0 probably, isn't created.```
dmesg | grep -e ndis -e wlan
```Thanks.

---

### Post by jhargis1012 on 2011-01-18
Tried it twice, nothing happens.

jhargis1012@jhargis1012-laptop:~$ dmesg | grep -e ndis -e wlan
jhargis1012@jhargis1012-laptop:~$ dmesg | grep -e ndis -e wlan
jhargis1012@jhargis1012-laptop:~$

---

### Post by chili555 on 2011-01-18
That suggests that ndiswrapper is not loading on boot. Let's load it and see if there are any interesting messages:```
sudo modprobe ndiswrapper
dmesg | grep -e ndis -e wlan
```Thanks.

---

### Post by jhargis1012 on 2011-01-18
Ok, wow, my wireless suddenly started working. I just booted up for the first time this morning, pulled up the forums, saw your post, and started entering the command lines. I suppose it was immediately after entering the first command ("sudo modprobe ndiswrapper"), and then a window popped up asking for my WEP key. What does that first command do? Did it make the wireless work suddenly, or was that just coincidence? If this command starts up the necessary driver, will I need to run this at startup to make the wireless work?

Wow, I'm so happy it's working. I really appreciate your help.

---

### Post by chili555 on 2011-01-18
ndiswrapper is the apparatus that uses the Windows driver for your card. For some reason, it doesn't load on boot. Let's fix it. Please do:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```It ought to start on boot from now on. Have fun and, if you agree, use the thread tools at the top to mark the problem 'Solved.'

---

### Post by jhargis1012 on 2011-01-18
Yep, it works perfectly. Thanks again!

---

### Post by jhargis1012 on 2011-01-18
Yep, works perfectly. Thanks again!!

---

