---
title: "Is it a bad card? &amp; What's a good one? D-Link DWL-G650"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by ArrowHeadVideo on 2011-02-08
So here's the thing - I was runnin' Ubuntu 10.10 for a long time on my Dell Inspiron 1200 and everything was Okay. It doesn't have a built in wireless card, but I had some Netgear one that worked when I installed Ubuntu. Then I lost my card. 

Oh no. So I found another Netgear card which is a WG511 v2 and this is when I learned the sad truth that, *not all wireless cards are created equal. *I would need the Ndiswrapper to fix this problem, but I was running Ubuntu as the sole operating system on this laptop. So I thought, I'll just buy another wireless card that runs when you pop it in like that old Netgear one. Ah so young, anyway I went to this web-page that listed wireless cards that ran with Ubuntu: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) and while searching on E-bay came across this baby: the D-Link DWL-G650 which according to this page: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink) works great.  
 

 I buy the card. I pop it into the laptop. Wait a couple of seconds. Grab a cup of Ovaltine. Nothing. Not even a green light is lighting up on it. It's a cadaver. Then I go back to the latter page and find I need something called Madwifi. Shoot! Long story short I install Madwifi – still not sure that all went okay. I followed the script on this sight [http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)  my computer restarts and still nothing out of the card. I also believe I saw somewhere that in the newer versions of Ubuntu you don't even need this Madwifi stuff. Is that true? I'm running 10.10  
 

 So today I put it into my ancient IBM ThinkPad A22p that's running Windows XP just to see if I can get a heartbeat out of the thing. Nothing. Not even a blinkin' light. I installed the windows drive online: [http://www.nodevice.com/driver/DWL-G650/get33808.html](http://www.nodevice.com/driver/DWL-G650/get33808.html) I tried the new hardware wizard too. Nata'
 

 Here are my questions: Should this wireless card work when I put it in in Ubuntu 10.10? If not, before I do anything should it at least light up? Did I buy a defective card? And lastly, what Wireless cardbus would you-all recommend that I can just jam in the port and start crackin'?  
 

 Thanks,
 Sam

---

### Post by chili555 on 2011-02-09
> Should this wireless card work when I put it in in Ubuntu 10.10?Probably. Let's run some diagnostic tests to see what you have and where you are. Please insert the device and open a terminal and run and post:```
sudo lshw -C network
lspci -nn
iwconfig
```Once we know more, we'll be in a better position to proceed.

If we can't get it running, I am confident we can get the Netgear going.

---

### Post by ArrowHeadVideo on 2011-02-10
Alright, I don't know if this was necessary or not, but I ran the commands in the terminal once for each card.

Another thing I noticed was that the Netgear card doesn't light up either in the card slot. So maybe the D-Link will work. I know when I put it in windows it recognizes that I inserted a card. Alright here's the code for both, but if we can get the D-Link working I'd like that better!

Also, I don't think I mentioned it, but I'm a newbie maybe a newbie+

[PHP]D-Link AirPlus Xtreme G 2.4GHz Cardbus DWL-G650
 

 sudo lshw -C network:  
   *-network                
        description: Ethernet interface  
        product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile  
        vendor: Intel Corporation  
        physical id: 8  
        bus info: pci@0000:02:08.0  
        logical name: eth0  
        version: 03  
        serial: 00:11:43:56:56:67  
        size: 10MB/s  
        capacity: 100MB/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s  
        resources: irq:20 memory:dfdff000-dfdfffff ioport:df40(size=64)  
   *-network UNCLAIMED  
        description: Network controller  
        product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]  
        vendor: Intersil Corporation  
        physical id: 1  
        bus info: pci@0000:03:00.0  
        version: 01  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm cap_list  
        configuration: latency=64 maxlatency=28 mingnt=10  
        resources: memory:54000000-54001fff  
 

 lspci -nn:  
 00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)  
 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)  
 00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)  
 00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)  
 00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)  
 00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)  
 00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)  
 00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)  
 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)  
 00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)  
 00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)  
 00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)  
 00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)  
 00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)  
 02:01.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]  
 02:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile [8086:1068] (rev 03)  
 03:00.0 Network controller [0280]: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890] (rev 01)
 

 iwconfig:  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 

 Net Gear
 

 sudo lshw -C network  
   *-network                
        description: Ethernet interface  
        product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile  
        vendor: Intel Corporation  
        physical id: 8  
        bus info: pci@0000:02:08.0  
        logical name: eth0  
        version: 03  
        serial: 00:11:43:56:56:67  
        size: 10MB/s  
        capacity: 100MB/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s  
        resources: irq:20 memory:dfdff000-dfdfffff ioport:df40(size=64)  
   *-network UNCLAIMED  
        description: Ethernet controller 
        product: 88w8335 [Libertas] 802.11b/g Wireless  
        vendor: Marvell Technology Group Ltd.  
        physical id: 1  
        bus info: pci@0000:03:00.0  
        version: 03  
        width: 32 bits  
        clock: 66MHz  
        capabilities: pm cap_list  
        configuration: latency=0  
        resources: memory:54000000-5400ffff memory:54010000-5401ffff  
 

 lspci -nn:  
 00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)  
 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)  
 00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)  
 00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)  
 00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)  
 00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)  
 00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)  
 00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)  
 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)  
 00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)  
 00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)  
 00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)  
 00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)  
 00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)  
 02:01.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]  
 02:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile [8086:1068] (rev 03)  
 03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)  
 

 iwconfig:  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
[/PHP]

Thanks,
Sam

---

### Post by chili555 on 2011-02-10
> *-network UNCLAIMED  
        description: Network controller  
        product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]  
        vendor: Intersil Corporation  Often these cards simply need firmware to work. You might be able to confirm this with this command:```
dmesg | grep p54
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

If the output is that firmware was requested and not found, you can install it, assuming you can get an internet connection, in System > Administration > Synaptic. Search for and install linux-firmware-nonfree. After a reboot, your wireless should be working.> I'm a newbie maybe a newbie+All of us were newbies at one time, even old Chili and even Linus Torvalds. No worries.

---

### Post by ArrowHeadVideo on 2011-02-10
Alright we're getting somewhere! The problem is not yet solved, but I saw my first green light from the wireless card! I did as you said and installed the linux-firmware-nonfree and rebooted the computer, but a funny thing happened. When I restarted, the computer froze. Then if I take the wireless card out it begins booting again. Once Ubuntu is fully started if I put the D-Link wireless card in it will blink for a few seconds, the wireless option is revealed at the top, and then the system freezes again! Until I eject the card and everything works again.

I'm wondering if me installing Madwifi has anything to do with this? Or any other weird things I may have done in the terminal before this forum. 

I tried putting the Negear card in with no luck. Is there a way I can un-install the madwifi? or is there something else going on? I can't really do anything in the terminal right now with the D-Link card in because it freezes everything. 

Thanks,
Sam

---

### Post by chili555 on 2011-02-10
> Is there a way I can un-install the madwifi? Certainly. How did you install it? Through Synaptic? Just go back and mark the package for removal, with the D-Link removed, of course. If you installed it some other way, post back and let us know.```
is there something else going on?
```Probably. You might do:```
dmesg > arrow.txt
lsmod >> arrow.txt
zip arrow.zip arrow.txt
```You will find a file in your user directory called arrow.zip. Attach it to your reply using the paperclip icon at the top of the reply box and I'll see if there is something else wrong.

My suspicion is that, after wadwifi is removed, you will be all fixed.

---

### Post by ArrowHeadVideo on 2011-02-10
I detailed how I installed madwifi in my first post. It was from this website: [http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html) and I used their script. I'm still not really sure if I did it right, but my computer restarted and all. I'm attaching the file. Thanks for your quick replies! 

-Sam

---

### Post by chili555 on 2011-02-10
Let's remove madwifi; it installs the ath_pci driver that has nothing to do with your D-Link.```
cd /usr/src/madwifi-0.9.3.2
sudo su
make uninstall
gedit /etc/modules
```Remove the line ath_pci. Proofread, save and close gedit.```
exit
```Reboot and insert the D-Link and tell me what happens.

---

### Post by ArrowHeadVideo on 2011-02-10
The first thing I get is:

```
cd /usr/src/madwifi-0.9.3.2
bash: cd: /usr/src/madwifi-0.9.3.2: No such file or directory

```
So I looked in the usr/src folder and there are two madwifi folders!
They are:
madwifi-0.9.3.3 & madwifi-0.9.4

So I ran the first one:
```
/usr/src/madwifi-0.9.3.3
shakes@Paul-Kirk:/usr/src/madwifi-0.9.3.3$ sudo su
root@Paul-Kirk:/usr/src/madwifi-0.9.3.3# make uninstall
./kernelversion.c:13: fatal error: linux/utsrelease.h: No such file or directory
compilation terminated.
Makefile.inc:81: *** Cannot detect kernel version - please check compiler and KERNELPATH.  Stop.
```

Then the second:
```
cd /usr/src/madwifi-0.9.4
root@Paul-Kirk:/usr/src/madwifi-0.9.4# sudo su
root@Paul-Kirk:/usr/src/madwifi-0.9.4# make uninstall
./kernelversion.c:13: fatal error: linux/utsrelease.h: No such file or directory
compilation terminated.
Makefile.inc:81: *** Cannot detect kernel version - please check compiler and KERNELPATH.  Stop.
```

On a brighter note sometimes when I put in the card it doesn't freeze up the screen - or at least takes a bit longer before it does. So maybe I can run something in the terminal with the card in.

I didn't know if I should do the gedit thing without the uninstall working so I haven't done that yet, but I can.

-Sam

---

### Post by chili555 on 2011-02-10
> fatal error: linux/utsrelease.h: No such file or directory
Arrgh! That's what I love/hate about one-siz-fits-all packages; they don't always work as expected. We could jigger the Makefile, but I doubt it will actually be needed. Please proceed with the /etc/modules change, reboot and report back.

---

### Post by ArrowHeadVideo on 2011-02-10
Well you're going to find this interesting! So I put the card in and I noticed that if i bent in in a certain way it seemed to light up more than another. 

So I keep trying it an eventually I was able to load a google page. Then I decided why not jam a piece of paper on the one side and see if that helps - it did! 

So now it seems semi-fully operational with a thick business card folded in half, electrical taped to one side. Enough to post this message anyway. 

Video might be another story. This was my college laptop so it's suffered a lot of abuse in transport especially having a wireless card always sticking out the side!  

Problem solved then?

-Sam

---

### Post by ArrowHeadVideo on 2011-02-10
Nm

---

### Post by chili555 on 2011-02-10
> **ArrowHeadVideo said:**
> NmMeaning? Never mind, it's not solved, or...??

It sounds as if either the card or the PCMCIA slot is faulty. I'm very, very good, but I'm doubtful I can fix it!

---

