---
title: "Netgear WNA1100 n150 not working in Ubuntu"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by damianvincent on 2010-09-12
Hello all, I'm in *serious *need of some help here. I've always used windows and really, really, want to get into linux, Ubuntu seemed like the best distro to learn on, so I'm giving it a try. Problem is I can't get my wireless adapter to work. Please help me, I've tried, trial and error, for 3 days now ](*,)to make this happen, to no avail. 

sys specs: Gigabyte UD-4, AMD Phenom II x4, GTX 260, Corsair ddr3 1666

Ok. First I installed ubuntu 10.04, I used the wubi windows installer, from Win 7 X64 Ultimate, I installed the 64 bit version of Ubuntu. Through research I learned I needed to install ndiswrapper and ndisgtk. I downloaded and installed, through .deb files ndiswrapper common 1.56-2 all.deb, ndiswrapper utilities 1.9 1.56-2.deb amd64, ndisgtk 0.8.5-1 amd64. I double clicked the .deb for common, utilities, then ndisgtk, all installed fine. 

I then went to system and now windows wireless is available at the bottom of the list. (I'll add at this point I made a copy of all the wireless adapters files installed in windows and pasted them into a file on an external drive, which I then moved into the ubuntu files)  I click windows wireless it asks for driver install (.inf) so I point it to the netathurx.inf (win764) file in the unbuntu file structure I pasted, and it installs and tells me device is present, however no options for wireless connections through the network applet. 

More searching lead me to the comprehensive list of problems listed here, so I'll post the commands I entered...

> damianvincent@ubuntu:~$ ndiswrapper -l
netathurx : driver installed
    device (0846:9030) present> 
damianvincent@ubuntu:~$ uname -m
x86_64> damianvincent@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
***Bus 002 Device 004: ID 0846:9030 NetGear, Inc.*** 
Bus 002 Device 002: ID 059b:0379 Iomega Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub> damianvincent@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 6c:f0:49:50:07:cf
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:28 ioport:ce00(size=256) memory:fddff000-fddfffff(prefetchable) memory:fddf8000-fddfbfff(prefetchable) memory:fdd00000-fdd1ffff(prefetchable)
(wireless card not being shown?) 

> damianvincent@ubuntu:~$ lsmod | grep ndis
ndiswrapper           244768  0 

damianvincent@ubuntu:~$ dmesg | grep -e ndis -e wlan
[   10.624899] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   11.888630] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'DbgPrintEx'
[   11.888635] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[   11.888638] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[   11.888641] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[   11.888648] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'_local_unwind'
[   11.888653] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   11.888656] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   11.888659] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   11.888664] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   11.888667] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[   11.888670] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   11.888673] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[   11.888677] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   11.888684] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   11.888688] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   11.888691] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   11.888694] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   11.888698] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   11.888701] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   11.888704] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   11.888707] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   11.888710] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   11.888714] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   11.888717] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   11.888720] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   11.888723] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   11.888726] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   11.888730] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   11.888736] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   11.888742] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   11.888746] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   11.888749] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   11.888753] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   11.888757] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   11.888760] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   11.888763] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   11.888770] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   11.888777] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   11.888781] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   11.888784] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   11.888788] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   11.888791] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   11.888795] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[   11.888798] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[   11.888801] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   11.888803] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   11.888805] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netathurx'
[   11.889076] ndiswrapper (load_wrap_driver:108): couldn't load driver netathurx; check system log for messages from 'loadndisdriver'
[   11.889116] usbcore: registered new interface driver ndiswrapper
I've tried driver version 1.1, and 1.1.3.21. I installed 1.1 in windows, connected to the internet, copied the installed files to and external HDD, booted into Ububtu loaded the win764 driver netathurx.inf and I get the same info I posted above, ok uninstall 1.1, installed 1.1.3.21, got online, copied those files into a different folder on external HDD, booted into Ubuntu loaded that inf, same info as above.

I am at a loss here and really need some help. I'm at the comp a bit so I'll monitor this thread regularly, any questions, suggestions please I'm all ears.

---

### Post by clrg on 2010-09-12
Does ```
sudo lsusb
``` show the device?

---

### Post by MaindotC on 2010-09-12
Rather than 1 command please consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  There is a section and links dedicated to ndiswrapper.  I'm not even sure you should be using XP, Vista, or 7 drivers with ndis but hopefully you can narrow this down.

---

### Post by damianvincent on 2010-09-12
> **clrg said:**
> Does ```
sudo lsusb
``` show the device?

It does list netgear among the devices. I had it pasted to my external HDD but I didn't save the read out. I'll go get it again, but netgear was listed

---

### Post by damianvincent on 2010-09-12
do I need to pull the .sys files from the system32/drivers folder as well as the files in the netgear folder in program files?

---

### Post by MaindotC on 2010-09-12
If you're using ndiswrapper you just need the single .inf file.  Did you try other versions of the driver as I suggested?

---

### Post by damianvincent on 2010-09-12
> **strAlan said:**
> If you're using ndiswrapper you just need the single .inf file.  Did you try other versions of the driver as I suggested?

I've tried driver version 1.1, and 1.1.3.21. I installed 1.1 in windows,  connected to the internet, copied the installed files to and external  HDD, booted into Ububtu loaded the win764 driver netathurx.inf and I get  the same info I posted above, ok uninstall 1.1, installed 1.1.3.21, got  online, copied those files into a different folder on external HDD,  booted into Ubuntu loaded that inf, same info as above.

unknown symbol

---

### Post by MaindotC on 2010-09-12
I hope you've been [googling](http://is.gd/f7ub6).  [Here's a solution]("http://ubuntuforums.org/showthread.php?t=723569") using a native Linux driver from RealTek instead using ndiswrapper.

---

### Post by damianvincent on 2010-09-12
> **strAlan said:**
> I hope you've been [googling]("http://is.gd/f7ub6").  [Here's a solution]("http://ubuntuforums.org/showthread.php?t=723569") using a native Linux driver from RealTek instead using ndiswrapper.

I have been googleing, like I said I've spent going on 4 days now trying to get this to work. 

However the link is for a realtek not netgear, it doesn't mention the netgear wna1100 n150 usb adapter. 

I've only been able to find the two drivers for this netgear adapter 1.1 which came on the cd, and I downloaded 1.1.3.21 neither have xp drivers, there is a default driver, which tells me invalid driver, a protocal 64 driver, also says invalid driver when loaded with ngtk, only the win764 will load, and it shows 

damianvincent@ubuntu:~$ ndiswrapper -l
netathurx : driver installed
    device (0846:9030) present
 
driver installed, device present, okay great, but no wireless options in the network applet...

so I ran...

damianvincent@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 6c:f0:49:50:07:cf
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:28 ioport:ce00(size=256)  memory:fddff000-fddfffff(prefetchable)  memory:fddf8000-fddfbfff(prefetchable)  memory:fdd00000-fdd1ffff(prefetchable)


I assume this is my motherboards Ethernet controller, but my wireless card doesn't seem to be showing, so I ran...


damianvincent@ubuntu:~$ lsmod | grep ndis
ndiswrapper           244768  0 

damianvincent@ubuntu:~$ dmesg | grep -e ndis -e wlan
[   10.624899] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   11.888630] ndiswrapper (import:242): ***unknown symbo***l: ntoskrnl.exe:'DbgPrintEx'
[   11.888635] ndiswrapper (import:242): ***unknown symbol***: ntoskrnl.exe:'KeInitializeGuardedMutex'
[   11.888638] ndiswrapper (import:242): ***unknown symbol***: ntoskrnl.exe:'KeAcquireGuardedMutex'
etc. etc. 

this is where I'm stuck

---

### Post by MaindotC on 2010-09-12
Sorry I negletected to see that the RTL8111 is your wired adapter, not wireless.  My bad.  Post the output of lsusb.

---

### Post by damianvincent on 2010-09-12
> **strAlan said:**
> Sorry I negletected to see that the RTL8111 is your wired adapter, not wireless.  My bad.  Post the output of lsusb.

No that's perfectly ok, I appreciate your help. I've seen that others have gotten this card to work in ubuntu, but I can't seem to get it to work, I follow the steps they list, but I get the unknown symbol error which is where I'm stuck.

---

### Post by MaindotC on 2010-09-12
> **damianvincent said:**
> no that's perfectly ok, i appreciate your help. I've seen that others have gotten this card to work in ubuntu, but i can't seem to get it to work, i follow the steps they list, but i get the unknown symbol error which is where i'm stuck.

lsusb plz!

---

### Post by damianvincent on 2010-09-12
damianvincent@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
***Bus 002 Device 004: ID 0846:9030 NetGear, Inc.*** 
Bus 002 Device 002: ID 059b:0379 Iomega Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by MaindotC on 2010-09-12
The reason I asked is b/c now it gives me a term to google.  Oh, and NOW I see you already put it in post #1...I am truly off my game tonight :(  This is the best I can find [http://fostergrant.ubuntuforums.org/showthread.php?p=9119161](http://fostergrant.ubuntuforums.org/showthread.php?p=9119161) - hope you haven't viewed it already :(  Chili seems to be much more knowledgeable on ndiswrapper.  

I wish there was like, a list of google searches we could collaborate on and mark as read/unread so I would know before posting redundant searches that you've already done.  We've got [the Official Ubuntu documentation](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).  You could also try [the wiki](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page) which has a link to their forums and also the IRC channel.  Probably be better getting real-time help instead of playing forum-tag.  You should also file a [Bug report](http://sourceforge.net/tracker/?group_id=93482&atid=604450) even though others have gotten theirs working.

I want your device to work and for you to experience all the other benefits of using Ubuntu but I'm not sure I can help you further.  I hope those links give you a new angle to receiving better help.

---

### Post by iClouseau88 on 2010-09-13
Hi,

Google search terms "WNA1100+linux" gives:

[http://comments.gmane.org/gmane.linux.drivers.ath9k.devel/3835]("http://comments.gmane.org/gmane.linux.drivers.ath9k.devel/3835")

It appears the driver that works for this adapter is madwifi's [COLOR="Blue"]ath9k_htc[/COLOR]. 

Here's another link that has a GUI program to install ath9k_htc:

[http://sourceforge.net/projects/ath9k-htc/]("http://sourceforge.net/projects/ath9k-htc/")

Good luck!

---

### Post by MaindotC on 2010-09-13
Please be advised this device is not listed on the [supported devices](http://linuxwireless.org/en/users/Drivers/ath9k_htc/devices).  It may work anyway - if it does be sure to let us know and I will have further directions for you.

---

### Post by damianvincent on 2010-09-13
> **iClouseau88 said:**
> Hi,

Google search terms "WNA1100+linux" gives:

[http://comments.gmane.org/gmane.linux.drivers.ath9k.devel/3835](http://comments.gmane.org/gmane.linux.drivers.ath9k.devel/3835)

It appears the driver that works for this adapter is madwifi's [COLOR=Blue]ath9k_htc[/COLOR]. 

Here's another link that has a GUI program to install ath9k_htc:

[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)

Good luck!

OMG, thank you so much!!!! It's now working, and I"m posting from unbuntu. I can't say thank you enough, I've spent day's trying to get this to work, you have no idea how happy this makes me.

---

### Post by MaindotC on 2010-09-13
Please create a [lauchpad account]("https://launchpad.net/") if you haven't already, then edit the [ath9k_htc driver wiki]("http://linuxwireless.org/en/users/Drivers/ath9k_htc/") and post your information so their list shows the WNA1100 N150 as a supported device.  Imagine how easy it would have been if you saw this information before - now you have a chance to help others with the same wireless card.

---

### Post by apoth on 2010-09-25
> **iClouseau88 said:**
> 
Here's another link that has a GUI program to install ath9k_htc:

[http://sourceforge.net/projects/ath9k-htc/]("http://sourceforge.net/projects/ath9k-htc/")

I had a few issues installing the installer(!) but this worked:

```
sudo dpkg -i --force-overwrite ath9k_htc-installer_1-0_all.deb
```

Although I've only got it working on G. Has anyone had any luck connecting on N and if so, how?

---

### Post by apoth on 2010-09-29
Ok. I've connected on N by disabling the G network on the router so it's N only.

Thing is, it's only about 10% faster I get with G. This seemed to be a likely culprit:

```
$ sudo iwconfig wlan1
wlan1     IEEE 802.11bgn  ESSID:"NETGEAR-DualBand-N"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 30:46:9A:32:F3:7E   
          **Bit Rate=1 Mb/s**   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

So I tried:

```
$ sudo iwconfig wlan1 rate 11M
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan1 ; Operation not supported.
```

Wireless in Linux is probably the one thing that still frustrates me massively!

---

### Post by leemaster81 on 2011-01-03
I was wondering if you ever got the "NETGEAR WNA1110" to work. I have one. It works on my P4 laptop, Ubuntu 9.10 using ndiswrapper(XP drivers) . But on my Phenom ii x4 whole nother story. I've been trying for weeks. Google, Google, Google. Please help!!!!!

---

### Post by walt.smith1960 on 2011-01-04
Have you tried the Ath9K installer referenced earlier in this thread?  I have this adapter and the installer from SourceForge has worked beautifully.  Just remember that installer is a 2 stage process. First install the .deb file then look in applications -> system tools and run the ath9k installer. Once the adapter is working, it will quit if the kernel is upgraded.  If that happens, run the ath9k installer again.  You don't have to repeat the first step, just the second.  Other good news is that the next release of Ubuntu (11.04) should recognize the Netgear WNA1100 adapter natively. The alpha release does now.

---

### Post by leemaster81 on 2011-01-08
I finally got it to work using the ath9k_htc installer thank you. I did every thing but that.:KS:popcorn::KS

---

### Post by walt.smith1960 on 2011-01-09
One thing about the ath9K installer--it seems like it'll nuke any other wireless adapters.  I tried plugging an RealTek RTL8187B adapter into the machine that has the ath9K installed.  This RTL8187B adapter has worked on several machines without fail. It would not work on the machine that has ath9K installed. On another machine I installed the ath9K installer just to check its function.  Same behavior, it would not recognize the RTL8187B adapter.  When I uninstalled the ath9k installer, the RTL 8187B was again recognized.

It looks like Natty (11.04) will recognize the WNA1100 out of the box, no installer required.

---

### Post by GECKYL on 2011-05-28
Thank you!  I was having a terrible time with this.  Once again the Ubuntu community shines!   -Mike Linux Mint 10
:popcorn:

---

### Post by Bango19 on 2011-10-20
hi, i got the .deb package installed, but im running crunchbang, so i dont have an applications or system tools folder.  i went into terminal and did a 

```
sudo ath9k_htc-installer
```

and it came up with a bunch of errors saying compat-wireless and all the log files dont exist.  i dont know what is going wrong with this ive been working on this problem for a couple days now.  if you could help i would appreciate it.  thanks!

---

