---
title: "RaLink RT61 Wireless Solved"
date: 2006-02-19
forum: Networking &amp; Wireless
---

### Post by judgekaster on 2006-02-19
This is a mini-howto setup the RaLink RT61 Wireless. 

**[COLOR="Red"]August 2, 2006 update:** Thanks to reharpernc's [post]("http://ubuntuforums.org/showpost.php?p=1310334&postcount=117"), I think a solution to the "No DHCPOFFERS Received" error is now available.[/COLOR] See further down for a summary.

It seems several Ubuntu users have posted on the forums their troubles with setting up the RT61 Wireless as this is not properly identified and configured by Ubuntu Breezy 5.10. I myself encountered the same problems and had to google around for a solution.

I got it up and running and would want to share my experience.

(a) "lspci" identifies the RT61 wireless chipset as

```

0000:01:02.0 Network controller: RaLink: Unknown device 0302

```

(b) If you have this hardware, obtain the RT61 driver from the RaLink website:

[http://www.ralinktech.com/drivers/Linux/2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz](http://www.ralinktech.com/drivers/Linux/2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz)

(c) Untar and follow the instructions in the included readme file. Basic steps would be:
```

$ sudo cp Makefile.6 Makefile
$ sudo make all
$ sudo mkdir /etc/Wireless/RT61STA/
$ sudo cp *.bin /etc/Wireless/RT61STA/.
$ sudo cp rt61sta.dat /etc/Wireless/RT61STA/.
```

(d) Edit the /etc/Wireless/RT61STA/rt61sta.dat as a binary file. The recommended way of doing this is:
```

$ cd /etc/Wireless/RT61STA
$ sudo vi -b rt61sta.dat

```

Enter the necessary information to access your network. Refer to the readme file for options.

(e) copy the rt61.ko driver file to the modules directory then load it

```

$ sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/.
$ sudo depmod
$ sudo modprobe rt61

```

(Note that the rt61 will automatically be loaded the next time you boot your Ubuntu machine.)

(e) check if the driver was loaded

```

$ iwconfig

```

should show information for "ra0"

(f) connect to the network

to set a static IP address, do:

```

$ sudo ifconfig ra0 {IP ADDRESS} up

```

to obtain an IP address from your DHCP server:

```

$ sudo dhclient ra0

```

(g) write a short script containing (f) to run at startup. 

```

$ sudo gedit /etc/init.d/rt61up

```

Enter the following lines:

```

#!/bin/sh
echo "Bringing up ra0"
# obtain an IP address from a DHCP server
dhclient ra0

# alternately, you can uncomment the following line to set a static IP address
# ifconfig ra0 {IP ADDRESS} up
# if you uncomment the line above, make sure to comment line #4

```

make it executable:

```

$ cd /etc/init.d
$ sudo chmod +x rt61up

```

(h) make a symbolic link in /etc/rcS.d so that it will run at boot up

```

$ cd /etc/rcS.d
$ sudo ln -s /etc/init.d/rt61up S33rt61up

```

That's it! ;) 

**Some additional notes:**

(a) *Do not* use the "Networking" tool (network-admin). You will get a lock-up at boot time at the point where the network interfaces are bieng configured. If you have used the Networking tool, you will have to comment out the entries in the file "/etc/network/interfaces." to do this:

```

$ sudo vi /etc/network/interfaces   # replace vi with your editor of choice (nano, gedit, kate etc.)

```

it should look like this:

```

auto lo
iface lo inet loopback

#iface ra0 inet dhcp
#wireless-essid xxxx
#auto ra0

```

(b) _rt61 in Dapper_

Ubuntu 6.06 (Dapper Drake) comes with the rt61 driver. However, you will still have to copy the firmware files to /etc/Wireless/RT61STA. 

[INDENT]1. Download [http://www.ralinktech.com/drivers/Linux/RT61_Firmware_V1.2.zip]("http://www.ralinktech.com/drivers/Linux/RT61_Firmware_V1.2.zip")
and copy it to /tmp then do the following:

```

$ cd /tmp
$ unzip RT61_Firmware_V1.2.zip
$ cd RT61_Firmware_V1.2
$ sudo mkdir /etc/Wireless/RT61STA
$ cp *.bin /etc/Wireless/RT61STA/.

```

2. Download the attached [rt61sta.dat.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=10560&stc=1&d=1149423981") and copy it to /tmp then do the following:

```

$ cd /tmp
$ tar zxvf rt61sta.dat.tar.gz -C /etc/Wireless/RT61STA

```

Edit /etc/Wireless/RT61STA/rt61sta.dat as shown in (d) above.

3. Do steps (f) to (h) above.

[/INDENT]

(c) _"No DHCPOFFERS Received"_

A lot of people have posted in this thread complaining about the error "No DHCPOFFERS Received" error when they try "sudo dhclient ra0". I myself have encountered this error when trying to connect to one of the APs in the building where I work. However, I couldn't find a solution and thus could not reply to their posts. Until I read reharpernc's [post]("http://ubuntuforums.org/showpost.php?p=1310334&postcount=117") which suggested using "iwpriv" instead of "iwconfig". [For more information on "iwpriv", type "man iwpriv" in your terminal.]

So for people who have encountered this problem, try:

```

sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=SHARED
sudo iwpriv ra0 set EncrypType=WEP
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set Key1=<my wep key>
sudo iwpriv ra0 set SSID=<my essid>

```

then try to connect to your AP with

```

sudo dhclient ra0

```

If this works for you, you might want to include the above lines in the "/etc/init.d/rt61up" script so that it will run at startup. Please do post a reply if whether this worked for you or not.

That's it!

# Edited Sun Jun  4 18:53:32 PHT 2006 in response to posts made in this thread. Thanks to all the inputs!

(a) made some steps more newbie-friendly

(b) instead of making the symbolic link in /etc/rc2.d, suggested that it be made in /etc/rcS.d

(c) added note about not using network-admin 

(d) added note about installing in dapper

# Edited Monday, 19 June 2006 07:55 PM 

(a) under Dapper instructions, corrected #3, should be steps (f) to (h) instead of (f) to (g). thanks to ferenczi and KuifjePDX

# Edited Wed Aug  2 20:22:03 PHT 2006

(a) added possible solution to "No DHCPOFFERS Received" problem.

---

### Post by Henry Rayker on 2006-03-10
I get to the part about the rt61.ko copy and everything just falls apart. I get an error "No such file or directory" referring to rt61.ko...could there be anything that was omitted?

---

### Post by melquiades on 2006-03-12
many thanks for the mini-howto, it worked perfectly for my setup. kudos, kudos! \\:D/

---

### Post by morpheus2485 on 2006-03-12
i'm trying to complete the "make all" command but i get the following error:
"/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found".

i've installed the kernel headers that came on my kubuntu install cd and all of the gcc, gcc-4.0, c++, etc compilers i could find on my install cd

any help?

---

### Post by morpheus2485 on 2006-03-12
maybe if someone could just e-mail me the binary i could get it going that way.... [email]morpheus2485@gmail.com[/email]

---

### Post by melquiades on 2006-03-13
what name should I put in the symbolink link in /etc/rc2.d pointing to /etc/init.d/rt61ip ? I tried S15rt61, and after that my system would freeze on bootup, specifically on the Configuring network interfaces portion.

---

### Post by h0me5k1n on 2006-03-19
[QUOTE=morpheus2485]i'm trying to complete the "make all" command but i get the following error:
"/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found".

i've installed the kernel headers that came on my kubuntu install cd and all of the gcc, gcc-4.0, c++, etc compilers i could find on my install cd

any help?[/QUOTE]

You need to install gcc-3.4 (the kernel is compiled with gcc-3.4 not gcc-4.0 I believe) and build-essential

```
sudo apt-get install gcc-3.4 build-essential
```

The instructions for editing the rt61sta.dat to get encryption (WPA/WEP) to work are in the tar.gz file from ralink too.

---

### Post by Stone123 on 2006-03-19
ok i fixed my rt61 on dwl-g510 rev c1 , fw :5 , 
EDITED(i could not get bootup connection with interface so i created a boot sript (and there is nothing more in /etc/network/interfaces file only lo loop )) and i removed wifi-radar , that was freezing the system or gdm in dapper 

:~$  sudo gedit /etc/init.d/xrt61
CODE:
> 
 #!/bin/bash
sudo /sbin/modprobe rt61
sleep 3
sudo /sbin/dhclient ra0

:~$ cd /etc/init.d
:~$ sudo update-rc.d xrt61 default
:~$sudo chmod 777 /etc/init.d/xrt61

Unlink runlevel 0 and 6. 
:~$ sudo rm /etc/rc6.d/K20xrt61 
:~$sudo rm /etc/rc0.d/K20xrt61 
//or just do ls /etc/rc6.d/ |grep xrt61  and ls /etc/rc0.d/ |grep xrt61 and remove them with rm


#cat /etc/network/interfaces :
> 
#empty


and i have  : 

cat /etc/modprobe.d/rt61d

> 
alias ra0 rt61


$sudo cat /etc/Wireless/RT61STA/rt61sta.dat
> 
[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=Default                  #essid
NetworkType=Infra
Channel=0 
AuthMode=OPEN              # open buy router settings @  [http://192.168.0.1/](http://192.168.0.1/) 
EncrypType=WEP              # i use wep so that is changed
DefaultKeyID=1
Key1Type=0                      # 0 = password in hex
Key1Str=7274363164      #key in hex 
Key2Type=1                      # 1 = password in ascii
Key2Str=rt61d                  #key in ascii
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
#WPAPSK=abcdefghijklmnopqrstuvwxyz
TxBurst=0
PktAggregate=0
TurboRate=0
WmmCapable=0
AckPolicy1=0
AckPolicy2=0
AckPolicy3=0
AckPolicy4=0
BGProtection=0
ShortSlot=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
PSMode=CAM
TxPreamble=0


:~$ cd /etc/Wireless/RT61STA/
:~$ sudo apt-get install tofrodos
:~$ dos2unix rt61sta.dat
:~$sudo chmod +x  /etc/Wireless/RT61STA/rt61sta.dat

---

### Post by UbuntuJohan on 2006-03-20
Hi, 

I have now tried this two times with my D-link DWL-G510 REV.C card.
But I still can't get it to work.
The card is recognised but as soon as I try to configure it I get a crash e.g.

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Channel:0
          RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
/etc/dhcp3/dhclient-script: line 139:  7913 Killed                  ifconfig $interface 0 up
```

Any ideas??

Has anyone managed to use these rt61 drivers on a 64 bit system?

Cheers
//Johan

---

### Post by Henry Rayker on 2006-03-21
try as I may, I can't even get my card to be recognized, let alone try to configure it...

---

### Post by Stone123 on 2006-03-23
[QUOTE=UbuntuJohan]Hi, 

I have now tried this two times with my D-link DWL-G510 REV.C card.
But I still can't get it to work.
The card is recognised but as soon as I try to configure it I get a crash e.g.

Any ideas??

Has anyone managed to use these rt61 drivers on a 64 bit system?

Cheers
//Johan[/QUOTE]
Did you fix the dat file in /etc/Wirless/rt2561~/ .dat ? whatever it's called
read readme file that comes with drivers. scroll down at the end and see. 
and use some gui program to connect . wifi radar and such . 
Anyway i cant connect on boot only from gnome network tool.

---

### Post by UbuntuJohan on 2006-03-23
Yes I have been trying to configure that file in various ways but it doesn't make a difference.

Do you have any example of your file that I can compare with?

I get the same crash when I try with gnome network-admin.

I will also install a 32-bit Breezy partion and see if it works better there.

Cheers
//Johan

---

### Post by evilsim on 2006-03-24
judgekaster u are the man. im pleased to say with some effort, ive gotten my RT61 card up at last! Ubuntu 5.10 "Breezy Badger" is my current flavour.
im using (ubuntu 5.10 cd) 2.6.12-9-386 kernel, P3 cpu, D-Link G-510 C1 Ver 5.00 & of course an Ubuntu breezy CD.

```
[4296457.850000] rt61: module license 'unspecified' taints kernel.
[4296457.882000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[4296457.882000] RT61: Vendor = 0x1814, Product = 0x0302
```

Now let's get to it.
Insert your ubuntu CD, boot from it, type 'server'.
Once your system is installed log in as your chosen username and password.

```

sudo -s (enter your user's password)
wget http://www.ralinktech.com/drivers/Linux/2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz
tar zxvf 2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz
cd RT61_Linux_STA_Drv1.0.3.0_200512230/Modules
cp Makefile.6 Makefile
apt-get install ssh (dont leave home without it)
apt-get install linux-headers-2.6.12-9-386 linux-source-2.6.12 make build-essentials gcc-3.4 (hope i didnt forget any)
cd /usr/src
tar -xjfv linux-source-2.6.12.tar.bz2
cd /home/[TAB][ENTER]
cd RT61_Linux_STA_Drv1.0.3.0_200512230/Modules
make all
(should take a while to build it, took >1minute on my 933mhz)
cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/.
depmod
modprobe rt61
dmesg |tail
(you should see a result like the one at the top of this post)
mkdir /etc/Wireless/
mkdir /etc/Wireless/RT61STA/
cp *.bin /etc/Wireless/RT61STA/.
cp rt61sta.dat /etc/Wireless/RT61STA/.
vi -b /etc/Wireless/RT61STA/rt61sta.dat

```

Thats where im upto.
Next, follow judgekaster's post from "$ iwconfig".
Again judgekaster thanks for your help getting this damn D-Link card working and inspiring this text. (although I almost wish I'd just bought the Linksys card at first) Also thanks to Christian & Matt @ sol1.

---

### Post by Stone123 on 2006-03-24
-> moved to page 1

---

### Post by UbuntuJohan on 2006-03-24
Now after installing 32 bit breezy on annother partition. 
I'm running wireless with my D-LINK DWL-G510 Rev.C and this RT61 driver on 32 bit Brezzy.

So this driver doesn't work in 64 BIT. But there are so many other benefits with 32 bit at the moment so I'll stick to that for now.

Finally I can move on to the mythtv installation 8) 

Cheers
//Johan

---

### Post by wrwills on 2006-03-28
It appears that rt61 chipsets will soon be supported under the rt2x00 sourceforge project.  They've also had problems with freezes, but they seem to be making some progress...  Maybe in a couple of weeks we'll be able to use this card under a 64bit system.
[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=924&postdays=0&postorder=asc&start=0](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=924&postdays=0&postorder=asc&start=0)

---

### Post by ridcully on 2006-03-30
Hi, 

I just wanted to add, that my Edimax EW-7128g works fine with WPA on breezy.

Thanks to judgekaster for the howto :)

---

### Post by Rocketeer on 2006-04-02
I can't get the compiler to work.

I get strange errors when typin "make all"

```
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/home/tristan/temp/RT61_Linux_STA_Drv1.0.3.0_200512230/Module modules
make[1]: Entering directory `/lib/modules/2.6.12-10-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-386/build'
make: *** [all] Error 2

```

I am using Ubuntu 5.10 (BB) with 2.6.12-10

Could someone please just send me the binary on ( t h a u s e r  a t  s m  i l e . c h) or the solution to my compile problem?

---

### Post by izakage on 2006-04-02
I'm having the same problem as Rocketeer.  Any help would be greatly appreciated!

---

### Post by crocovin on 2006-04-03
I'm having the same problem. 
What is "modules" in the make file below? Should I replace it with something else. 

---

[I]all: 
	make -C /lib/modules/$(shell uname -r)/build SUBDIRS=$(shell pwd) modules[/I]

---

---

### Post by PonchoWare on 2006-04-03
You need kernel header or src.

sudo apt-get install linux-headers-$(uname -r)

Sorry for my very poor english.

---

### Post by Rocketeer on 2006-04-04
....well they are installed. :-/

---

### Post by Rocketeer on 2006-04-06
Managed to solve my (and others problem):

In the Modules directory of the RA driver:

Info:
Maybe you need to download the correct sources 
(apt-get install linux-source-2.x.x) and unpack it.....

After that you should do:
make -C /usr/src/linux-source-2.6.xyz SUBDIRS=$PWD modules
instead of "make all"

Cheers!

PS: 
You can download my compiled version here:
[http://www.hochlager.ch/upload/RT61_Driver_2_6_12-10.zip](http://www.hochlager.ch/upload/RT61_Driver_2_6_12-10.zip)
(Ubuntu Kernel Version: 2.6.12-10)

---

### Post by ?@yk0&amp;^4 on 2006-04-06
[QUOTE=melquiades]what name should I put in the symbolink link in /etc/rc2.d pointing to /etc/init.d/rt61ip ? I tried S15rt61, and after that my system would freeze on bootup, specifically on the Configuring network interfaces portion.[/QUOTE]

I have this same problem. I've tried booting in recovery mode, and this gives an error message:

Unable to handle kernel NULL pointer deference at virtual address 00000008
and some more error stuff - not sure how to get this lot to you without typing it all out!

Has anybody got any good ideas as to why this might be happening, and what I can do about it? The computer did crash as I was trying to configure, but then worked briefly until I rebooted again.

If this is a problem with the driver source code (as indicated by some posts here: [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=924&postdays=0&postorder=asc&start=0](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=924&postdays=0&postorder=asc&start=0) - this is another project to write working linux drivers for these cards), is there anything I can do to work around the problem? (like preventing the module from loading during boot and automatically running modprobe rt61 somehow? - I'm not sure how to do this...)

The rt2x00 drivers require a later kernel version, otherwise I'd try the latest version of them.

Thanks,
Greg.

---

### Post by Stone123 on 2006-04-06
read my comment:

:~$ sudo gedit /etc/init.d/xrt61
type this into that file:
> 
#!/bin/bash
sudo /sbin/modprobe rt61
sleep 3
sudo /sbin/dhclient ra0

save and exit 
then again in terminal: 
:~$ cd /etc/init.d
:~$ sudo update-rc.d xrt61 default

// comment out all ra0 : auto ra0 , end rest of ra0. in /etc/network/interfaces

reboot

---

### Post by ?@yk0&amp;^4 on 2006-04-07
[QUOTE=Stone123]read my comment:

:~$ sudo gedit /etc/init.d/xrt61
type this into that file:

save and exit 
then again in terminal: 
:~$ cd /etc/init.d
:~$ sudo update-rc.d xrt61 default

// comment out all ra0 : auto ra0 , end rest of ra0. in /etc/network/interfaces

reboot[/QUOTE]

I have done this, and no longer get a kernel panic, but I can't connect to the network, and iwconfig will not let me set the ESSID. Presumably I shouldn't use the Gnome Networking applet to confgure the interface as this relies on /etc/network/interfaces, right?

I am using Rocketeer's compiled drivers on kernel version 2.6.12-10-386 with a configured .dat file in /etc/Wireless/RT61STA/

My readouts are as follows:

sudo lshw includes this:
```
           *-network:0
                description: Network controller
                product: RaLink
                vendor: RaLink
                physical id: 7
                bus info: pci@01:07.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=rt61
                resources: iomemory:fdff8000-fdffffff irq:9
```

sudo iwconfig ra0 gies this:
```
ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Channel:0
          RTS thr=0 B   Fragment thr=0 B
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

sudo iwlist ra0 scan gives a 'Segmentation fault' and then refuses to work again...
sudo iwconfig doesn't work after this either...

After running sudo iwlist ra0 scan, when I reboot I get a Permission denied error relating to /etc/rt6.d/k20xrt61 and then it hangs on 'Deconfiguring network interfaces'.

If after pressing the reboot button and booting up again, I don't run sudo iwlist ra0 scan, it doesn't hang but I still get a Permission denied error.

Do I need to modify permissions somewhere? If so, how do I go about doing this?

Many thanks for all your help!
Greg.

---

### Post by Stone123 on 2006-04-07
Segmantation foult. 
(sudo iwlist ra0 scanning ) works here . 
//$ lsmod |grep rt61
// rt61                  223616           1

Rocketeer's compiled drivers on kernel version 2.6.12-10-386 
//Try bulding your own drivers and see if it works.  

but try this first :
:~$ cd /etc/Wireless/RT61STA/
:~$ sudo apt-get install tofrodos
:~$ dos2unix rt61sta.dat

---

### Post by ?@yk0&amp;^4 on 2006-04-07
[QUOTE=Stone123]Segmantation foult. 
(sudo iwlist ra0 scanning ) works here . 
//$ lsmod |grep rt61
// rt61                  223616           1

Rocketeer's compiled drivers on kernel version 2.6.12-10-386 
//Try bulding your own drivers and see if it works.  

but try this first :
:~$ cd /etc/Wireless/RT61STA/
:~$ sudo apt-get install tofrodos
:~$ dos2unix rt61sta.dat[/QUOTE]

I tried, but I couldn't get it to work. I'm going to start again tomorrow with a fresh Breezy install and do the following. Should it be okay?

```
wget http://www.ralinktech.com/drivers/Linux/2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz

tar zxvf 2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz



sudo apt-get install linux-headers-$(uname -r) build-essential gcc-3.4

sudo cp Makefile.6 Makefile

sudo make all



sudo mkdir /etc/Wireless

sudo mkdir /etc/Wireless/RT61STA

sudo cp *.bin /etc/Wireless/RT61STA

sudo cp rt61sta.dat /etc/Wireless/RT61STA



cd /etc/Wireless/RT61STA

sudo vi -b rt61sta.dat
edit file as required for network settings

apt-get install sysutils

sudo dos2unix rt61sta.dat




sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net

sudo depmod

sudo modprobe rt61



iwconfig
check driver is loaded (should show information for "ra0")

sudo iwconfig ra0 essid "MyNetworkName"

sudo iwconfig ra0 channel 7

sudo dhclient ra0



check that I can ping people



sudo gedit /etc/init.d/xrt61
type this into that file:
	#!/bin/bash
	sudo /sbin/modprobe rt61
	sleep 3
	sudo /sbin/dhclient ra0
save and exit

cd /etc/init.d
sudo update-rc.d xrt61 default



reboot and test network again
```

How do I check that the .dat file is a binary before loading? Should the dos2unix do this for me?

And is it best to steer clear of the /etc/network/interfaces file and the Gnome Networking applet completely, and use iwconfig to configure the interface? I did manage to get the card working before on Breezy with the off-the-cd kernel and using the Gnome Networking applet, but it crashed on reboot (due to not having written in the booting script, perhaps...)

Sorry to be such a newbie, but I'm having a frustrating time trying to work out the exact method I should use!

Many thanks for your help.
Greg.

---

### Post by ?@yk0&amp;^4 on 2006-04-08
I've finally managed to get it working! Hurray!! I had to modify permissions on the xrt61 file to allow all users to execute, and the permissions on the .dat file to allow me to edit it!

The network configured itself using the .dat file, and iwlist ra0 scanning now works too. For anyone trying to set this thing up, DO NOT use the Gnome Networking applet to configure your card, or /etc/network/interfaces: this causes a kernel panic on boot for me!

Many thanks to everyone who's contributed to this thread, particularly Stone123.

The only slightly weird thing happening now is that the DHCP software displays some stuff when I shut down, but presumably this doesn't rerally matter at all?

Many thanks again,
Greg.

---

### Post by Stone123 on 2006-04-08
[QUOTE=gregswinford]

The only slightly weird thing happening now is that the DHCP software displays some stuff when I shut down, but presumably this doesn't rerally matter at all?
.[/QUOTE]
Well thats my foult, i did fast solution
You know that  sudo update-rc.d xrt61 default  , updates all run levels and by that run level 6 that is reboot. So it even configures network under reboot. 
[http://en.wikipedia.org/wiki/Runlevel#Linux](http://en.wikipedia.org/wiki/Runlevel#Linux)

just do :
sudo rm /etc/rc6.d/K20xrt61 
or what ever the name is ,  do ls -l in that map /etc/rc6.d/ and remove xrt61, thats it.

---

### Post by ?@yk0&amp;^4 on 2006-04-08
[QUOTE=Stone123]Well thats my foult, i did fast solution
You know that  sudo update-rc.d xrt61 default  , updates all run levels and by that run level 6 that is reboot. So it even configures network under reboot. 
[http://en.wikipedia.org/wiki/Runlevel#Linux](http://en.wikipedia.org/wiki/Runlevel#Linux)

just do :
sudo rm /etc/rc6.d/K20xrt61 
or what ever the name is ,  do ls -l in that map /etc/rc6.d/ and remove xrt61, thats it.[/QUOTE]

Okay thanks. I know a little about run levels, but haven't come across that method. Should I do the same for runlevel 0 as well? (I'm not sure whether it does the same when shutting down...)

Many thanks,
Greg.

---

### Post by Stone123 on 2006-04-08
Yes you are right. run level 0 too .
And you are welcome 
I wrote that explanation on run levels  for all people that are new to linux and read this  thread and want to know how it works. And i hope thay read it before asking about  the same.

---

### Post by ?@yk0&amp;^4 on 2006-04-08
[QUOTE=Stone123]Yes you are right. run level 0 too .[/QUOTE]

Okay cheers. Many thanks for all your help. I've now got the network working with WEP encryption.

---

### Post by crazycarl on 2006-04-10
i have the driver installed and can use the wireless network fine as long as i have encryption disabled on both the wireless router and in the rt61sta.dat file.  as soon as i set the "AuthMode" line to "WPA2PSK" and set the EncrypType to AES and then type in my passkey in the WPAPSK line, dhclient will just time out on acquiring an ip address.
also, even though I am connected and can browse the web, I am unable to ping the router or access the router configuration menu.  it's totally weird i have no idea what's going on... :(
i have already tried commenting out the DefaultKeyID and all the Key1...Key4 entries which I believe are all related to WEP? which I do not want to use.
I can't for the life of me figure out what is happening... I have downloaded wifi radar and that does not seem to be able to set up wpa2, nor does the basic networking gui tool that comes with this... ](*,) 
can anyone help me out?

---

### Post by tenshu on 2006-04-11
this is a known problem (see malone)

I can set my wifi with no encryption
but if a try wep or WPA every thing seems to work 
but nothing can be ping =(

The buh is assign to Ben Collins, we are waiting for a fix...

edit:
see:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/28464](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/28464)
and
[https://launchpad.net/distros/ubuntu/+bug/35474](https://launchpad.net/distros/ubuntu/+bug/35474)

---

### Post by Kasanax on 2006-04-11
Having a bit of a problem here...

I went through the walkthrough, and iwconfig lists the interface properly, but when I try and change anything (such as setting the essid with iwconfig, or even if I try and scan with iwlist), a get a bunch of text which ends with a segmentation fault. After that, any time I try and use dhclient, iwconfig, iwlist, etc., the terminal locks up and won't repond.

I can't list the output right now, since it's on a different machine, but if it helps, I can try posting it from that machine later.

Any thoughts on what to do?

Thanks!

---

### Post by Stone123 on 2006-04-12
[QUOTE=Kasanax]Having a bit of a problem here...



I can't list the output right now, since it's on a different machine, but if it helps, I can try posting it from that machine later.

Any thoughts on what to do?

Thanks![/QUOTE]
Did you read the whole thread?  Maby its a bug , or you did something wrong. 
You will have to explain bit more .And did you try any of the solutions in the thread. 
So you can connect to one netwrok and try to change to other? 
If i was changing essid then i would unload driver with script 
 
#!/bin/sh 
modprobe -r rt61
sed -ie 's/current-ESSID/new-ESSID/g' /etc/Wireless/RT61STA/rt61sta.dat
chmod +x /etc/Wireless/RT61STA/rt61sta.dat
modprobe rt61
dhclient ra0

---

### Post by Kasanax on 2006-04-14
I originally tried using this walkthrough:

[http://www.ubuntuforums.org/showthread.php?t=156075]("http://www.ubuntuforums.org/showthread.php?t=156075")

and ended up with this error. THinking it was something specific to the walkthrough, I decided to start from scratch with this how-to. So, I recompiled my kernel (which I had been meaning to do anyway), and followed the steps in this howto (and I believe I followed all the steps correctly...).

Again, I'm having the same issues. After loading the module:

```
sudo modprobe rt61
```

the iwconfig command gives me this output:

```
root@rizzle:/home/rizzle# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Channel:0
          RTS thr=0 B   Fragment thr=0 B
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

which seems like it should be good. The problem comes when I try and do anything or change anything related to the card. For example, setting the SSID for my network ("simple"):

```
root@rizzle:/home/rizzle# iwconfig ra0 essid simple
Segmentation fault

```

After this, if I try to change or do anything, the terminal simply gives me an extra blank line, and locks up:

```
root@rizzle:/home/rizzle# iwconfig ra0 essid simple



```

I've been doing all of this in gnome-terminal. If I do this in one of the virtual terminals, I get a much more involved error message before the seg fault. Anyone know how I could copy over the output from the virtual terminal into something that I could post here? Tried piping output to a file, but that didn't seem to work...

I'll try running through the how-to again, to check and see if I did something wrong...

EDIT:

Another question - I now have a module (rt61) which doesn't work, but keeps getting loaded at boottime... how do I go about getting rid of the module, without causing problems? I'm guessing I probably can't just remove the files from the /lib/modules/.../drivers/net/ directory...

---

### Post by Stone123 on 2006-04-16
[QUOTE=Kasanax]I originally tried using this walkthrough:

[http://www.ubuntuforums.org/showthread.php?t=156075]("http://www.ubuntuforums.org/showthread.php?t=156075")

and ended up with this error. THinking it was something specific to the walkthrough, I decided to start from scratch with this how-to. So, I recompiled my kernel (which I had been meaning to do anyway), and followed the steps in this howto (and I believe I followed all the steps correctly...).
[/QUOTE]
Yes poster of that thread had some problems if you read next post in that howto , and i think he answerd the solution in this thread on how to solv it , just read the full thread

And i know that driver doesnt work with 64 kernels and smp kernels. So watch out for those. 
[QUOTE=Kasanax]
Another question - I now have a module (rt61) which doesn't work, but keeps getting loaded at boottime... how do I go about getting rid of the module, without causing problems? I'm guessing I probably can't just remove the files from the /lib/modules/.../drivers/net/ directory...[/QUOTE]
[/QUOTE]
You can remove auto loading if you remove  comment out #alias ra0 rt61
And you can blacklist it in /etc/modprobe.d/blacklist~
And you can unload while running in kernel  with modprobe -r rt61 .
Your choice.

---

### Post by ph0t0n on 2006-04-19
I'm having no luck at all with this. I'm new to Linux/Ubuntu and that probably has a lot to do with it.

I can't get "Make" to complete. I had to manually create a directory "build" in "/lib/modules/2.6.12-10-686/" because I dont have permissions (no su access in ubuntu). I assume this is ok.

Now when I try and "make all" I get the following errors:
```

*** No rule to make target `modules'. Stop.
```

I assume that the Make All creates the driver file "rt61.ko" because it is not located anywhere. Without this file I can't get anywhere.

```
(d) copy the rt61.ko driver file to the modules directory then load it
```

I can't find this file so I am stuck.

Help!

---

### Post by vinfred on 2006-04-20
There's a very good explanation on how to configure network in section 10 of [http://www.us.debian.org/doc/manuals/reference/reference.en.html](http://www.us.debian.org/doc/manuals/reference/reference.en.html)

Section 10.8.1 specifies that you should "Never list PCMCIA interfaces in auto stanzas. The PCMCIA cardmgr is started later in the boot sequence than when /etc/rcS.d/S40networking runs."

I've also noticed that, when using the Network administration, it adds that auto stanza to /etc/network/interfaces
[-X Therefore you should NOT use the network administration GUI to start your PCMCIA card (in my case DWL-G630 rev E1. using RT61 drivers from ralink). Anyway, as the SSID and the WEP key are already defined in /etc/Wireless/RT61STA/rt61sta.dat, there is no need to duplicate this information into /etc/network/interfaces.

Section 10.8.2 explain what you should do to activate correctly your PCMCIA card when inserted or at boot time

Add a map stanza to the mapping hotplug stanza
Add necessary ip configuration with iface.

The final /etc/network/interfaces looks like this:

Auto lo
Iface lo inet loopback

mapping hotplug
[INDENT]   script grep
   map eth0
   map ra0[/INDENT]

iface eth0 dhcp

iface ra0 dhcp

I didn't modify anything else to get my card automagically connect as soon as the card is inserted, as well as at boot time if already inserted.=D> 
Be careful about services depending on your network that must be started/stopped when inserting/removing card : see section 10.8 for how to achieve this.

Vinfred

---

### Post by tapeshag on 2006-04-29
Hi,

I was having tough time getting my DLINK wireless card DWL-G630 (built on rt61 chipset) to make it working on ubuntu 6.06 release (which is in beta now)
My kernel was crashing as i insert the card. Then I downloaded the latest version of drivers from 
[http://www.ralinktech.com.tw/supp-1.htm](http://www.ralinktech.com.tw/supp-1.htm)
 (remember to download the firware also)

and it is working fine. If anyone needs help, feel free to contact me.

(BTW i heard about ubuntu just 4 days back....so it is not difficult for newbies to do such tasks.....wonderful linux)

Enjoy!
Tapesh

---

### Post by fiikske on 2006-05-04
Tapesh,

yes, I'd be very much interested in your help... I've got a brand new pc here, I'm playing around with ubuntu, and desperate to have that wireless thing working... 

Many thanks!
Fiikske

---

### Post by tenshu on 2006-05-05
Me too

I would like to know what is your kernel
and the encryption you are using.

Because i compiled those drivers,
i set my network with wep key
Everything seems to be good
But in fact i can't even ping anything.

If i reboot the system hang before bootsplash.

should i use an un-encrypted network (with mac filtering?)

---

### Post by pshnfry on 2006-05-07
How do you save the edited binary file rt61sta.dat?

---

### Post by cvrse on 2006-05-09
[QUOTE=pshnfry]How do you save the edited binary file rt61sta.dat?[/QUOTE]

from within sudo vi press 'esc' key once you've finished editing the file and type ':wq!' (without the quotes) as the file is set to read only by default

---

### Post by tenshu on 2006-05-15
any news for dapper?

---

### Post by noelferreira on 2006-05-17
hi!

this howto works great running 32 bits. However i need it under amd64. I tried and i tried but nothing. Please tell me when rt61 works on amd64.

thanks, noel ferreira

---

### Post by tenshu on 2006-05-21
you get it working under a 32 bit dapper
could you tell me how?

---

### Post by noelferreira on 2006-05-22
hi,

You have just to  follow the instructions in the beginning of this post. 
Be carefully editing the rt61sta.dat file. Edit that file with your usual text editor, copy the text, and create a new one with 'vi -b rt61sta.dat' pasting the text in it.

everything should work.

tell me if you get problems.

thanks, noel ferreira

---

### Post by noelferreira on 2006-05-22
You have just to  follow the instructions in the beginning of this post. 
Be carefully editing the rt61sta.dat file. Edit that file with your usual text editor, copy the text, and create a new one with 'vi -b rt61sta.dat' pasting the text in it.
To save and quit vi editor tpe ':wq'.

everything should work.

tell me if you get problems.

---

### Post by noelferreira on 2006-05-22
ok tenshu,

i read your posts. i guess your problem has nothing to do with driver.
allow the wireless card mac adress in your router configuration.

noelferreira

---

### Post by Canuck on 2006-05-31
Hello,

So far everything has worked but I get the following when running  **dhclient ra0**
:

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ra0/00:15:e9:a8:d1:92
Sending on   LPF/ra0/00:15:e9:a8:d1:92
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


But when I run **dhclient** no problem...  Any idea how I can fix this.

Also the connection is enabled in the network manager but my laptop receives no signal from the card...

Thanks

Canuck

---

### Post by hgpuke on 2006-05-31
Hi! Unfortunately I bought a Dlink DWL-G510 card that turned out to be a "rev C". After much googling I found this thread and thought "Great, this will solve it". However, it seems that the download link for the driver does no longer work! Could anyone send the driver to me, please?

My e-mail is hans-goran (at) puke (dot) se

Thanks!

Hans-Göran Puke, Sweden

---

### Post by Canuck on 2006-05-31
hgpuke,

I attached the current driver for you, figured it would be easier that way.

Canuck

---

### Post by Stone123 on 2006-06-01
[QUOTE=hgpuke]Hi! Unfortunately I bought a Dlink DWL-G510 card that turned out to be a "rev C". After much googling I found this thread and thought "Great, this will solve it". However, it seems that the download link for the driver does no longer work! Could anyone send the driver to me, please?

My e-mail is hans-goran (at) puke (dot) se

Thanks!

Hans-Göran Puke, Sweden[/QUOTE]
Hej
I have the same card . Since dapper will be out soon , rt61 is allready in kernel. All you need is firmware in dapper(*.bin).

---

### Post by hgpuke on 2006-06-01
Thanks,
but exactly what do you mean by "All you need is firmware in dapper(*.bin)."? :confused:
I have tried the dapper beta and I could not get it to work, at least not automatically. Does this mean that a) I have to perform some manual procedure, or b) the support was not in the beta but will be in the final version?

If I need to take some manual steps, could you please provide me with detailed instructions?

Also, since the machine I am installing to is very limited on resources (PII, 350MHz, 192MB RAM), I am expecting to run into problems
](*,) with normal Ubuntu, and therefore I am thinking about using XUbuntu instead. Would this mean anything as far as my Wifi problems (and solution) is concerned?

---

### Post by noelferreira on 2006-06-01
has anyone have this driver working on amd64?

thanks

noel ferreira

---

### Post by raphy3 on 2006-06-02
[QUOTE=Rocketeer]Managed to solve my (and others problem):

In the Modules directory of the RA driver:

Info:
Maybe you need to download the correct sources 
(apt-get install linux-source-2.x.x) and unpack it.....

After that you should do:
make -C /usr/src/linux-source-2.6.xyz SUBDIRS=$PWD modules
instead of "make all"

Cheers!

PS: 
You can download my compiled version here:
[http://www.hochlager.ch/upload/RT61_Driver_2_6_12-10.zip](http://www.hochlager.ch/upload/RT61_Driver_2_6_12-10.zip)
(Ubuntu Kernel Version: 2.6.12-10)[/QUOTE]

Hmm, I tried what you suggested.  It did get me one step past "no rules to make target modules", but now I get about a thousand errors passing by the screen, ending with "'wpastate' is already defined" and it exits with two errors total...
Has anyone else seen this?

EDIT: my bad, forgot to sudo make.

---

### Post by Stone123 on 2006-06-02
[QUOTE=hgpuke]
I have tried the dapper beta and I could not get it to work, at least not automatically. Does this mean that a) I have to perform some manual procedure, or b) the support was not in the beta but will be in the final version?

If I need to take some manual steps, could you please provide me with detailed instructions?
[/QUOTE]

a) yes i got it to work in beta flight 4 i think (its about kernel not ubuntu anyhow, just that they include driver in config)
b) dont know anything about ubuntu support on that .
In HOWTO on first page skip the part about copying driver to kernel. and do the rest . you can check my post on configuring network too or just browse this thread for  /etc/network/interfaces configuration
edit here:
[http://www.ubuntuforums.org/showpost.php?p=938949&postcount=41](http://www.ubuntuforums.org/showpost.php?p=938949&postcount=41)

(i dont know much about GUI stuff, kwifi , network manager and such)

---

### Post by Stone123 on 2006-06-03
1.enable repos 
[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repos%29]("https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repos%29") 
2. download attached file rt61.tar.gz
3. extract it to /home/(your username ??)/
4. open terminal  :
5. run the attached file:
 sudo sh testscript

6. read redme file end edit config file.

7. remove all ra0 from /etc/network/interfaces

8.reboot

content of tescript :
> 
#!/bin/bash  
sudo mkdir /tmp/rt61dapper
cd /tmp/rt61dapper
sudo wget [http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz](http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz)
sudo tar zxvf RT61_Linux_STA_Drv1.0.4.0.tar.gz
cd RT61_Linux_STA_Drv1.0.4.0/Module
sudo cp Makefile.6 Makefile
sudo apt-get install linux-headers-$(uname -r)  make build-essential  gcc-3.4 tofrodos 
cd RT61_Linux_STA_Drv1.0.4.0/Module
sudo make all
sudo modprobe rt61
sudo mkdir /etc/Wireless/
sudo mkdir /etc/Wireless/RT61STA/
sudo cp *.bin /etc/Wireless/RT61STA/
sudo cp rt61sta.dat /etc/Wireless/RT61STA/
sudo echo "#!/bin/bash" > /etc/init.d/xrt61dapper
sudo echo "sudo /sbin/modprobe rt61" >> /etc/init.d/xrt61dapper
sudo echo "sleep 3" >> /etc/init.d/xrt61dapper
sudo echo "sudo /sbin/dhclient ra0" >> /etc/init.d/xrt61dapper
cd /etc/init.d/
sudo update-rc.d xrt61dapper defaults
sudo chmod +x /etc/init.d/xrt61dapper

sudo rm /etc/rc6.d/K20xrt61dapper
sudo rm /etc/rc0.d/K20xrt61dapper
sudo echo "alias ra0 rt61" >> /etc/modprobe.d/rt61dapper
sudo dos2unix -f /etc/Wireless/RT61STA/rt61sta.dat
sudo chmod +x /etc/Wireless/RT61STA/rt61sta.dat
sudo gedit /etc/Wireless/RT61STA/rt61sta.dat




---

### Post by Stone123 on 2006-06-03
Anyone up for making  editing tool in gambas for rt61sta.dat
soupel of comboboxes and such?
(Delete).

---

### Post by raphy3 on 2006-06-03
[QUOTE=Stone123]1.enable repos 
[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repos%29]("https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repos%29") 
2. download attached file rt61.tar.gz
3. extract it to /home/(your username ??)/
4. open terminal  :
5. run the attached file:
 sudo sh testscript

6. read redme file end edit config file.

7. remove all ra0 from /etc/network/interfaces

8.reboot

content of tescript :[/QUOTE]


Well I finally got mine working.  The advice of Rocketeer is what did it for me, changing make -C to the source directory and not the build subdir in modules.  I'm wondering how this ended up working for people who didn't have to do this....
I like the fact that you're trying to make a universal install script.  Also an editor for rt61sta.dat would definitely make it a lot more user friendly; it could check for user input error, etc.  Too bad I know nothing about the API you suggested or making GUI's in general.  :-k 
Thanks to everyone in the thread for help.

P.S. It looks like the connection quality of this rt61 version of the ZEW1601 that I have is much much better under linux than my last ZEW1601 was using rt2500 (that card was retired to a windows machine).

---

### Post by chrism66 on 2006-06-04
Ok, I screwed up before I found this post. I am complete newbie to Linux/Ubnutu. So I tried to activate my wirelesss from the Network option fron the administration. I  am hanging up  during boot due to the fact that I have the dreaded ra0 entries in the etc/network/interface, how can I deletw these entries inthis file from the commnad lin in recovery mode or console? Any help to get me back on the road to Ubuntu would be greatlt appreciated!!! Thanks in advance:-D .

Chris

---

### Post by Titus A Duxass on 2006-06-04
I have the same problem, tried to sudo pico /etc/network/interfaces but it causes a hang-up.

I tried deleting the file with sudo rm /etc/network/interfaces but that also did not work.

---

### Post by sophtpaw on 2006-06-04
I have this Ralink wireless card. I had to have my computer guru come and set it up, way back in Breezy. 

On DD i upgraded to Dapper and touched Networking in System/Administration. Well, my computer went into a loop and upon reboot my system was lost - i had to do a fresh/clean install all over.

My question is should i make a wide berth around the gui-network configuration tool? or can i risk trying to use it to configure my ralink? It sees it but i don't know how to fill out the empty fields to configure it. 

On the other hand is this how to made for Breezy still good and applicable in Dapper? 

Many Thanks,

--
sophtpaw

---

### Post by Stone123 on 2006-06-04
[QUOTE=chrism66]Ok, I screwed up before I found this post. I am complete newbie to Linux/Ubnutu. So I tried to activate my wirelesss from the Network option fron the administration. I  am hanging up  during boot due to the fact that I have the dreaded ra0 entries in the etc/network/interface, how can I deletw these entries inthis file from the commnad lin in recovery mode or console? Any help to get me back on the road to Ubuntu would be greatlt appreciated!!! Thanks in advance:-D .

Chris[/QUOTE]
type: sudo vi /etc/network/interfaces
key commands:

" i " key= insert (use it to edit)
> 
(edit all lines that you need safest way is to add # at the begining of the line)
ex:
auto  ra0
change to:
#auto ra0

" esc " key= exit editing (like pressing menu bar)

now to save file and exit use:
"Shift" key  and ":" key  

type : wq!

done

---

### Post by chrism66 on 2006-06-04
Stone123 thanks for the help!!! It worked perfectly!! The 'Bonehead' move I was making was that I kept editing 'interface' when I should have been editing 'interfaces'. Well it is going to a very fun and interesting process moving to Ubuntu/Linux.

Chris

---

### Post by lastrite on 2006-06-04
Thanks Stone123! \\:D/ 

I nearly installed suse out of desperation :oops:

---

### Post by tapeshag on 2006-06-07
I am trying to get my RT61 card with AMD64. (it worked perfectly fine on 32 bit machine). But on 64 platform the driver crashes. I have done the exact steps as I follwed on 32 bit platform.
Is there any known bug in the ralink driver for 64 bit platform? (I went to ralinktech.com website but it is in chinese so could not figure out much)

---

### Post by chrism66 on 2006-06-07
I am also having the same probelem with AMD64. Have it working perfectly on a 32bit box. 

Chris

---

### Post by tapeshag on 2006-06-08
Following the ralinktech forum
[http://61.222.76.235/phpbb2/viewtopic.php?t=1554&highlight=rt61+amd64](http://61.222.76.235/phpbb2/viewtopic.php?t=1554&highlight=rt61+amd64)

It seems that driver source code has to be modified in order to get working on AMD64 machine. (I also suspected same as same driver code cant work both on 32bit and 64 bit)

I read more and found it is not possibel :(
[http://61.222.76.235/phpbb2/viewtopic.php?t=1763&highlight=rt61+amd64](http://61.222.76.235/phpbb2/viewtopic.php?t=1763&highlight=rt61+amd64)

so I think I have to look for some other shipset to work on 64 bit platform

---

### Post by Drachenfaenger on 2006-06-10
@judgekaster:

I followed your instruction, but on "dhclient ra0", the interface can't get an address.

It reports

DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
and so on 

ad then 

No DHCPOFFERS received

What is wrong?

Michael

---

### Post by judgekaster on 2006-06-10
drachenfaenger....

were you able to associate your wireless device with an accesspoint? you can check the output of 
```

sudo iwconfig ra0

```

if it is already associated, the second problem i would check would be whether the DHCP is up. are other clients in the network able to get a IP address and connect to the network? 

jk

---

### Post by KuifjePDX on 2006-06-11
I think that for installation in Dapper you also need to do step (h) to make it boot. At this time I can use networked drives and printers but my internet is not working. I *CAN* do a traceroute and ping to google.com but I cannot get any pages to load in my browser (Firefox). I'm using a clean install of Edubuntu 6.06 LTS on a newly partitioned and formatted drive. After the fresh install this morning I did do an upgrade of about 20 components through the automated update manager.

This is a multi-boot system and my Windows XP can browse the web without a problem using the latest revision of Firefox.

Any thoughts?

Doei!

PS. The device manager in Edubuntu does not recognize the wireless card even though ra0 works for my LAN. Should I go through the steps and compile the RaLink Linux driver to make the device manager recognize the card?

---

### Post by Drachenfaenger on 2006-06-11
[QUOTE=judgekaster]drachenfaenger....

were you able to associate your wireless device with an accesspoint? you can check the output of 
```

sudo iwconfig ra0

```

if it is already associated, the second problem i would check would be whether the DHCP is up. are other clients in the network able to get a IP address and connect to the network? 

jk[/QUOTE]

hi jk!

iwconfig shows a connection to an accespoint (ESSID="Whatever") and the DHCP is up, because other WLAN-Stations get an IP-Address.

What should I do?

---

### Post by judgekaster on 2006-06-11
if i were in your place, i would open two terminals, in the first

```

tail -f /var/log/messages /var/log/syslog

```
while in the other
```

sudo dhclient ra0

```

I would also try to check the logs in the DHCP server and check whether there are errors while you try to connect.

---

### Post by ferenczi on 2006-06-18
it seems to me also that you have to do step (h) in dapper too. my wireless functions now that I did it.
it is a clean install from an alternate 6.06 CD, with eighty-something updates I installed yesterday.
judgekaster: many thanks!

---

### Post by mpa on 2006-06-19
My Digitus DN-7006GA is detected in Ubuntu and able to see the access point. Unfortunately I am having the same problem as many other, namely  the box is unable to get ip address through DHCP.


DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
and so on
No DHCPOFFERS received

Could really use some help here.

---

### Post by judgekaster on 2006-06-19
mpa,

after trying to connect with "sudo dhclient ra0", could you 

```

tail -n 25 /var/log/messages > output.txt

```
and post the contents of "output.txt" here?

jk

---

### Post by snowboard975 on 2006-06-20
First, thanks a lot for your very useful article.
It worked!! (It didn't work at first, but it worked after I rebooted my computer)
My wireless LAN card is NE-54GPCI with RT2561 chip sold by Netami.
I followed the Dapper solution because my OS is dapper.

Second, it would be better if some misprints are corrected as following:

$ sudo /etc/network/interfaces 
should be 
$ sudo vi /etc/network/interfaces

and

$ ln -s /etc/init.d/rt61up S33rt61up
should be 
$ sudo ln -s /etc/init.d/rt61up S33rt61up

That's it!
Thank you again!

---

### Post by Zahlerstreik on 2006-06-25
I followed the instructions for dapper to the t, but when  i do "dhclient ra0" i get a line error and the message "Killed"
i also get  "Killed" if i do ifconfig ra0 ipaddr up

any suggestions/

this is what i did

$ cp  *.bin /etc/Wireless/RT61STA
$ cp rt61sta.dat /etc/Wireless/RT61STA

then i confirmed that the files were indeed coppied.

configured the dat file w/ vi for use with my network, according to the driver's readme.

$ dhclient ra0

COMPUTER CRASHES :(

---

### Post by tapeshag on 2006-06-25
Zahlerstreik,
I am assuming that u built the driver from the source. The default driver (shipped with Ubuntu) crashes.
Also the DHCP doesnt work with RT61. So you have to assign the static IP.
Rest I can help you over messenger. 
- Tapesh

---

### Post by judgekaster on 2006-06-26
[QUOTE=snowboard975]... 
It would be better if some misprints are corrected ...
[/QUOTE]
The text has been corrected. Thank you for pointing out the errors.

---

### Post by judgekaster on 2006-06-26
This might just be a typographical error on your part
[QUOTE=Zahlerstreik]...
$ cp  *.bin /etc/Wireless/RT61STA
$ cp rt61sta.dat /etc/Wireless/RT61STA
[/QUOTE]
But if not, the line should be typed out correctly as follows:
> 
$ cp  *.bin /etc/Wireless/RT61STA/.
$ cp rt61sta.dat /etc/Wireless/RT61STA/.

Notice the "slashdot" ("/.") at the end of the line.

---

### Post by Zahlerstreik on 2006-06-26
i got it working.
the 64 bit edition was doing nothing for me so i decided to go the 32 bit one. i think the problem was the firmware files in the post...i think they're meant for 64 bit. Anyways, once i booted my 32 bit version i proceeded to install make, gcc, etc. then i coppied the firmware files and the config dat file, edited the dat file, and rebooted. to my amazement the card worked! it's still a little buggy though, my connection drops out once in a while. this may be caused by my config: im a windows user so the only wireless config i've seen is GUI style with detailed explinations for each setting, unlike the readme for the rt61 which has one sentence.

anyway im now trying to install kismet but having problems. something to do with my compiler. bleh. at least i can browse now.
thanks!

---

### Post by neveceral on 2006-06-28
[QUOTE=judgekaster]
to obtain an IP address from your DHCP server:
```

$ sudo dhclient ra0

```
[/QUOTE]

Hi,
in ubuntu 6.06 i have all *.bin files and *.dat in /etc/Wireless/RT61STA but in step f) i didn't get IP address from my DHCP server. :confused: 
What's wrong? Router Linksys WRTP54G is OK, DHCP is OK (tested on lan) Thank you for help.

---

### Post by judgekaster on 2006-06-28
[QUOTE=neveceral]Hi,
in ubuntu 6.06 i have all *.bin files and *.dat in /etc/Wireless/RT61STA but in step f) i didn't get IP address from my DHCP server. :confused: 
What's wrong? Router Linksys WRTP54G is OK, DHCP is OK (tested on lan) Thank you for help.[/QUOTE]
Make sure that everything in the rt61sta.dat is edited correcty to suit your setup. Then, after trying to connect to the dhcp server ("sudo dhclient ra0"), type in:
> 
tail -n 25 /var/log/messages > output.txt

and post the content of "output.txt". Let us see if we can figure out the problem.

jk

---

### Post by neveceral on 2006-06-29
First of all, thank you for helping me. I found the problem - it was WPA, it didn't work well, so i used "OPEN" authmode and everything was OK, but after rebooting - boot hangs up everytime at
"[I]Bringing up ra0
Internet System Consortium DHCP Client v3.0.3
Copyright....
All rights...
For info, please..[/I]."

and i don't know, what to do?

---

### Post by judgekaster on 2006-06-30
Do you mean you were able to connect when you tried "OPEN"? Try putting back "WPA" instead of "OPEN" and see if it will still hang your computer at boot time....

[QUOTE=neveceral]First of all, thank you for helping me. I found the problem - it was WPA, it didn't work well, so i used "OPEN" authmode and everything was OK, but after rebooting - boot hangs up everytime at
"[I]Bringing up ra0
Internet System Consortium DHCP Client v3.0.3
Copyright....
All rights...
For info, please..[/I]."

and i don't know, what to do?[/QUOTE]

---

### Post by neveceral on 2006-06-30
Yes, i am able to connect only in OPEN mode and not in WPE or WPA. My problem is DHCP, because i set rt61 up and in OPEN mode it is working without any problem but only to reboot, after reboot i don't get IP from DHCP and booting hangs up so much, that i need to reinstall ubuntu :-/. Why i don't get IP only after reboot but before i got it? What's wrong? As AP i am using Linkys WRTP54G and wifi card is Linkys WMP54G ver.4.1

---

### Post by judgekaster on 2006-06-30
Were you able to change the AuthMode setting to "OPEN" then connect to a network without rebooting? Did you edit the rt61sta.dat file and rmmod'ed and modprobe'd the rt61 module? 

[QUOTE=neveceral]Yes, i am able to connect only in OPEN mode and not in WPE or WPA. My problem is DHCP, because i set rt61 up and in OPEN mode it is working without any problem but only to reboot, after reboot i don't get IP from DHCP and booting hangs up so much, that i need to reinstall ubuntu :-/. Why i don't get IP only after reboot but before i got it? What's wrong? As AP i am using Linkys WRTP54G and wifi card is Linkys WMP54G ver.4.1[/QUOTE]

---

### Post by neveceral on 2006-07-01
[QUOTE=judgekaster]Were you able to change the AuthMode setting to "OPEN" then connect to a network without rebooting? [/QUOTE]
Yes
[QUOTE=judgekaster]Did you edit the rt61sta.dat file [/QUOTE]
yes
[QUOTE=judgekaster]and rmmod'ed and modprobe'd the rt61 module?[/QUOTE]
no, i did only what you wrote on 1.page for ubuntu 6.06 + f)-h). I'm linux newbie and so i don't even know what and how i have to "rmmod'ed" and "modprobe'd"? sorry, i found something with modprobe only for ubuntu 5.10, so i didn't do it
Daniel

---

### Post by Stone123 on 2006-07-02
[QUOTE=neveceral]Yes

yes

no, i did only what you wrote on 1.page for ubuntu 6.06 + f)-h). I'm linux newbie and so i don't even know what and how i have to "rmmod'ed" and "modprobe'd"? sorry, i found something with modprobe only for ubuntu 5.10, so i didn't do it
Daniel[/QUOTE]

When drivers is loadeding up it reads the config dat file before it starts and sets it self up. So you have to stop and run driver betwean changes(safest). I dont know if iwconig can change it under running but i would guess not allways.

So 
$sudo rmmod rt61           or(modprobe -r rt61)
$ sudo gedit/etc/Wireless/RT61STA/rt61sta.dat
$ modprobe rt61

---

### Post by neveceral on 2006-07-02
[QUOTE=Stone123]
$sudo rmmod rt61           or(modprobe -r rt61)
$ sudo gedit/etc/Wireless/RT61STA/rt61sta.dat
$ modprobe rt61[/QUOTE]

I tryed it and nothing happened. It is again the same as before - wifi is working again only to reboot and next boot computer hangs up by configuring network so much, that i need to reinstall ubuntu :-/. I don't know what i have to do  differently?

---

### Post by Stone123 on 2006-07-02
Quick Check:
-No Smp kernel
-No 64 bit kernel 
-nothing in /etc/network/interfaces about wlan or ra[0-~]
-no wifi GUI like wifi -radar or something that is brought up after connection
and ndiswraper that mbight be fighting(hoging) for same resource.
-------------------------------------------------------------------------

---

### Post by neveceral on 2006-07-02
[QUOTE=Stone123]Quick Check:
-No Smp kernel
-No 64 bit kernel 
-nothing in /etc/network/interfaces about wlan or ra[0-~]
-no wifi GUI like wifi -radar or something that is brought up after connection
and ndiswraper that mbight be fighting(hoging) for same resource.
-------------------------------------------------------------------------[/QUOTE]
everything no
i have P4 2.4GHz, ram 512MB, Asus p4p800-e deluxe, 120GB HDD Samsung sata, nvidia fx5700, combo Teac dw522g, dvd burner LG H20L, wifi linksys wmp54g ver4.1, AP router linksys wrtp54g


**I found a special thread for this problem, please could you move the discussion [there]("http://www.ubuntuforums.org/showthread.php?t=182460&highlight=rt61")**
Thank you very much, Daniel

---

### Post by kangt_qc on 2006-07-03
hi there,

1st thanks a lot for the tutorial, it s really great to find things like that :)
2nd, in fact i have 1 problem, i need to switch between 2 wireless network... WPA at work and WEP at home.... is there an esay way or do i have to modify the script .dat and reboot ?

Thanks a lot

Kangt

---

### Post by dougmwpsu on 2006-07-04
i'm having alot of troubble with this.

when i first ran dhclient, the card was able to get an ip and i was properly connected to the internet.  i then updated to the newest packages and followed the rest of the guide, copying the bin and dat files into /ect/wireless/st61sta(sp) 

i wasn't able to very effectivly edit the dat file because i couldn't find the readme you referenced, but i did type in the name of my access point. i het a snag in the next part of the guide, setting up the boot script. gedit wouldn't open, so i rebooted.

after the reboot, i was no longer able to connect using dhcp, i'm getting the same timeout error that others have been getting. i'm not sure if it was the updates or the configuration, but i was able to confirm that i am still able to connect using dhclient in the live cd.

---

### Post by dougmwpsu on 2006-07-04
an update: i reinstalled dapper and ran automatix and got all the latest updates. my wireless still works with a simple dhclient command. i have not tried installing the firmware or setting up the boot script, as i'm afraid that i'll screw everything up again.

---

### Post by Lord Dagoth on 2006-07-10
Hey everyone, I'm a HUGE Linux n00b and am trying to get my wireless card to work. I'm trying to get the firmware to work on Dapper and when ever I get to this:

```
cp *.bin /etc/Wireless/RT61STA/.
```

I get this:
```

cp: cannot create regular file '/etc/Wireless/RT61STA/./FILENAME.bin': Permission denied
```

I'm sure this problem is easily fixed, but like I said, I'm a huge Linux n00b.

All help will be appreciated.

---

### Post by jesi on 2006-07-10
First make sure youre in the directory with the .bin files:

```
ls *.bin
```

If you don't see anything youre in the wrong directory.

if You do type:

```
sudo cp *.bin /etc/Wireless/RT61STA/
```

---

### Post by uhajo on 2006-07-11
judgekaster, you saved my life!
Thanks for this extremely helpful how-to. Followed it line by line and it all worked. I was just about to give up on Ubuntu (third WLAN-Card I tried) and go back to Windows. (Imagine ;-)

Happyly,
uhajo

---

### Post by Tao-Tao on 2006-07-12
First,

Judgekaster, thank you for the howto.  I was literally mere minutes away from switching completely to windows before I found your guide.  And I have been using Gentoo and now Ubuntu for quite a while... ...funny how a simple wlan-card can get one so hopeless...  Well, if the card had come with the rt2500 chipset it was supposed to when I bought it...

Second,

Can someone confirm that he/she has managed to get WPA-PSK to work in Dapper using Dapper's native rt61-driver, with Ralink's firmware and editing the .dat -file?  For me it doesn't work, so I just wonder if someone has gotten it to work?

There isn't a clear consensus on the articles I've found that is it working or not, so this would just give a bit of a light to the end of the tunnel for me...  be it a oncoming train or not.

---

### Post by zlurp on 2006-07-12
I did not have managed to get WPA-PSK to work with Dapper, but I would be glad if someone could give me a hint how to do.

And I have got a question on my own: Don't I have to tell the system where to find the firmware and the rt61sta.dat? How does it know that it has to look at /etc/Wireless/RT61STA? I had expected that I would have to edit any conf-file for that.

---

### Post by sblanzio on 2006-07-12
EDIT: read below ---

please, help!

I'm trying to make work a Edimax EW-7128g RT61 in ubuntu 6.06. x86 version (2.6.15)

I'v downloaded the last linux drivers from Ralink site (which is not the one you talked about but now it's this one:
[http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz](http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz)
However it seems to be similar to the old one.

I've "apt-getted" the build-essentials + linux-source2.6.15 (and tar them) + linux-headers...

when I'm in the RT61_Linux_STA_Drv1.0.4.0/Module/ directory and I type
make all

I get an error message something like it cannot find a directory. So I type:

sudo make -C /usr/src/linux-source-2.6.15/ SUBDIRS=$PWD modules

I get an infinite list or warnings and errors like 
"include/linux/types.h:37: error: syntax error before .(something)."
"include/linux/types.h:37: warning: type defaults to .something. in declaration of *somethingelse*"
and so on for an infinite time.. so I have to stop it.

I tried to substitute "linux-source" with "linux-headers" but despite it seems to work a little more I get anyway a long list of errors and warnings.

Hey.. you all seem to have overcome this "make all" point, but i'm still here... where is my fault? :(

I pray you can help me... please save me from bill'z software! ](*,) 

thanks
sblanzio


EDIT: I've solved reinstalling ubuntu from scratch and using the script you can find in pag 7 of this thread.
Now i'm gonna do some tests, if I'll have more problems I'll let you know.
By know, THANK YOU VERY MUCH! This community is wonderful! I can throw the WinXP cd to trash! :D

---

### Post by GuitarHero on 2006-07-13
i followe the how to for dapper with a linksys WMP54G v4.1 wireless card with an ra61 chipset and it did not work.  boot took longer with the added steps but the internet still doesnt work.

---

### Post by Generic_TSS on 2006-07-14
THANK YOU so much for writing this guide, i had just installed xubuntu dapper and had been pulling my hair out with frustration trying to get my linksys wmp54g 4.1 to work! i went through about 5 reinstalls and endless configuration nightmares until i saw this guide... worked like a charm! like the others, i was a few minutes away from going back to windows; you are a lifesaver!

---

### Post by ilex on 2006-07-14
> **Henry Rayker said:**
> I get to the part about the rt61.ko copy and everything just falls apart. I get an error "No such file or directory" referring to rt61.ko...could there be anything that was omitted?

You need to install the kernel headers. If you use Synaptic they are in the development section and called linux-headers-2.6.xx-xx-xxx. Choose the one thats right for you. You could check your kernel version with the command uname -r.

---

### Post by FooAtari on 2006-07-16
Hi

This guide seems to have brought me closer to getting my card working, thanks.  But still few problems...

Ubuntu now seems to recognise the card but still no connection...

When I run iwconfig I get this:

lo no wireless ext

eth0 no wireless ext

ra0 RT61 Wireless ESSID:'flat'
Mode Managed Channel:6 Access Point XXXXXXX
Bit Rate = 48Mb/s
RTS thr: off Fragment thr: off
Link Quality = 69/70 Signal level: -72 dBm Noise level:-95dBm
Rx Invalid nwid: 0 Rx Invalid crypt: 0 Rx Invalid frag: 0
Tx excessive retries: 0 Invalid misc: 0 Missed beacon: 0

sit0 no wireless connection

I can ping the router.

It's a clean install, all I have done is follow the instructions listed for Ubuntu 6.06 as detailed towards the end of the guide.

What else should I have done? I get the feeling it's something to do with the default gateway or dns... But dont know where or how to set these up. The guide stated not to use Networking as it can cause system to hang on start up

I think I am a few simple steps from wireless heaven, help!

---

### Post by Stone123 on 2006-07-17
sudo route add default gw 192.168.*.* 

and *.* is set in your router mine is 0.1 . If you have more connections you can use -net ip gw .
Dns :
[http://www.die.net/doc/linux/man/man5/resolv.conf.5.html](http://www.die.net/doc/linux/man/man5/resolv.conf.5.html)

I think you should try and restart your router first.

---

### Post by reckahn on 2006-07-20
A utility for RT61 based cards has been released but it currently only works with DHCP and WEP is untested.  

[http://sourceforge.net/projects/ra0dar](http://sourceforge.net/projects/ra0dar)

---

### Post by arunsub on 2006-07-25
I have bought Zonet ZEW1602 (PCI) and installed it in my desktop. Ubuntu Dapper didn't recognize the card. I installed network manager and ndiswrapper-utils and that didn't help. I then tried what was given at the start of this thread and that too didn't help. I then tried this link [http://doc.gwos.org/index.php/Rt2x00drivers](http://doc.gwos.org/index.php/Rt2x00drivers) . It didn't help. Does anyone have any idea?
ps: I already have 2 ethernet port in the computer. One is built in and the other one is PCI. The built in one is disabled and I'm using the 2nd one for wired connection.

---

### Post by paulyche on 2006-07-26
I've got my edimax 7128g *mostly* working in 6.06 using this guide. I have a bit of a complex setup where I connect to a Netgear wireless router which itself connects to a wired router/modem which then connects to the net.

I've set the netgear router to be 192.168.10.1 and be DHCP server and I've set the modem/router to be 192.168.1.1. 

I can ping google.com and other external ips and domain names. I can also download updates through apt-get at ~150-200kb/s. I can SLOWLY connect to these forums using firefox.

However web browsing is VERY slow. I can't connect to google at all and the same for about half the other sites I access. I haven't changed any DNS of default gateway stuff 'cause I don't really know what I'm doing.

Browsing works fine in XP.

Any ideas?

Here's my iwconfig and google ping output

```
lo        no wireless extensions.

ra0       RT61 Wireless  ESSID:"toftwoodrouter"
          Mode:Managed  Channel:6  Access Point: 00:14:6C:3E:BE:10
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=71/70  Signal level:-69 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

------

PING www.l.google.com (216.239.59.99) 56(84) bytes of data.
64 bytes from www.google.com (216.239.59.99): icmp_seq=1 ttl=232 time=48.8 ms
64 bytes from www.google.com (216.239.59.99): icmp_seq=2 ttl=232 time=47.1 ms
64 bytes from www.google.com (216.239.59.99): icmp_seq=3 ttl=232 time=47.7 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2007ms
rtt min/avg/max/mdev = 47.113/47.908/48.873/0.750 ms

```

---

### Post by paulyche on 2006-07-26
Fixed by turning ipv6 off. Should have done a better phrased forum search there's loads there.

---

### Post by Airyshone on 2006-07-26
I have gone through this and many other walkthroughs before, all to varying degrees of success. My current problem is as follows:

I can configure everything happily and it all seems to work soundly until i use: 

dhclient ra0

This produces an error many people have posted but i haven't seen a solution yet. it ends in: 

No DHCPOFFERS received

At the moment i'm trying different sources of the driver, but i'm nearing the point where i think i'll just reinstall ubuntu. I have a suspicion that on a previous attempt to solve this problem i have messed with a file i shouldn't have.

Any ideas on how i can solve this would be great. If not, does anyone know how to reinstall ubuntu on a dual boot machine? :)

---

### Post by reharpernc on 2006-07-28
well done Judgekaster an excellent mini how-to.

Like quite a few people I to had the problem with dhclient ra0 never getting a valid ip address and iwconfig never returning the correct essid. That is until I discovered the iwpriv command.Apparently iwconfig cannot always set the private wireless settings.

I entered the following

sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=SHARED
sudo iwpriv ra0 set EncrypType=WEP
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set Key1=<my wep key>
sudo iwpriv ra0 set SSID=<my essid>

then when I ran the sudo dhclient ra0 everything just worked

Also I was a bit confused on what to set inside of rt61sta.dat - so for those that were asking for some help - here is mine that works for me 

[[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=<my essid here>
NetworkType=Infra
Channel=0
AuthMode=SHARED
EncrypType=WEP
DefaultKeyID=1
Key1Type=0
Key1Str=<my WEP key in hex>
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
#WPAPSK=abcdefghijklmnopqrstuvwxyz
TxBurst=0
PktAggregate=0
TurboRate=0
WmmCapable=0
AckPolicy1=0
AckPolicy2=0
AckPolicy3=0
AckPolicy4=0
BGProtection=0
ShortSlot=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
PSMode=CAM
TxPreamble=0
 
HTH

Russ

---

### Post by coolmig on 2006-07-28
Well, I have two desktops in my home, the first one with Ubuntu Dapper i386 with zero problems! (RT2500 Wireless configured graphically with Network Admin) I wanted to install the same Ubuntu Dapper in the second Desktop (Airlink101 Wireless - RT2600 based) so I did it trusting it was going to work properly as with the live CD, which seemed to recognize the Wireless Card.

So, at next reboot... hanged at "Configuring Network Interfaces...", I discovered that a simple Ctrl-C would let it finish the boot, but when it entrered the gnome login splash screen it would not start the desktop, new hang so arggghhhh... it was worse even, if I managed to login in a terminal it would hang with a simple command... I thought it was a no go for Ubuntu in this machine... :( So I found this thread, and the instructions to remove the Network-Admin default interfaces were key to get my Ubuntu alive again. Managing to access the files of the Ubuntu Installation from the Live CD and following the other instructions on my other Desktop I solved the problem, thanks a lot!!! Now with two Ubuntu desktops in a network I will keep learning a lot of Linux! Who will say that Ubuntu is bad when it was capable to run a totally Wireless home network? Ubuntu rules!!!

Sorry for my bad english... thanks for this great solution!!! :D

---

### Post by Morphit on 2006-07-30
Like Airyshone, I'm getting the ```
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```problem. iwconfig looks like the connection is active (though no 'link' light comes on on my card) but dhclient cant obtain an ip and assigning a static ip with ifconfig, again, seems to work, but pings and data cant get onto the network.
I'm at a loss really, ubuntu performs great apart from this. And while I can proxy a web connection from another machine nearby, I need real network access for server applications.
Does anyone know when this user-friendly networking panel is gonna stop breaking ubuntu and start connecting it?

---

### Post by jdavies on 2006-08-01
I'm also getting the "No DHCPOFFERS received" message when trying to run the dhclient command.

I've run the above original guide for ubuntu 6.06.  I modified the rt61sta.dat file to connect with my wirelesss router, but still getting the message.  Also, if I run a "sudo iwlist scan" command I get the following for ra0 - 

ra0     Scan completed :
        Cell 01 - Address: (address shows up here)
        Mode:Managed
        ESSID:"WLAN"
        Encryption key:off
        Channel:6

So I know my card is working trying to find my router.  Also, when I run GUI networking and setup my connection at this point, I can get a connection, but then of course have the hang up issues at boot up.  

I'm a brand new XP convert to the system and would love to make this work, however I'm starting to get a bit discouraged with the overall experience. (been at this for a couple days).  I agree with Morphit completely that the real fix for this is to fix the user-friendly network gui application so that it actually works with this card.. seems like a ton of people have it.  It's a bit much to ask a newbie to get it up and going when non of the guides seem to be helping....

---

### Post by judgekaster on 2006-08-02
thanks reharpernc! a lot of people have been complaining about "No DHCPOFFERS received" when they try to get an IP address. I once had experienced this too but could not figure out what to do, thus failing to offer any solution. until i read your post, tried "iwpriv" which magically solved my problem. i will include this solution in this rt61 mini-howto in the hope that it will solve the "No DHCPOFFERS" problem.

---

### Post by felippe miranda on 2006-08-02
Thank you very much - your excellent how-to guided me configuring my rt2561 card in DAPPER

---

### Post by judgekaster on 2006-08-03
glad i could help...

---

### Post by osaeris on 2006-08-04
Just a quick thanks for posting a great article. I got my Belkin PCI Wireless card working following your instructions on a Dell precision 410 Dual Processor running Dapper 6.06.

I also learned something new and managed to fix an issue on a Dell C600 (dapper) with a DLink G450 card in it. It was necessary to do a sudo /etc/init.d/networking restart on it before the Dlink card would wake up. I place a script in /etc/init.d then symlinked into /etc/rcS.d/ and bingo!

Thanks again

Steve

---

### Post by [eXr] on 2006-08-04
In my case the "iwpriv solution" didn't solve the "No DHCPOFFER" problem. I've found another solution.

Tested all the alternatives to the RT61 module the solution was in the "mod" by the rt2x00 team in serialmonkey.

[http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)

The same steps. Ungzip, make, cp files, modprobe...

In my case, and after a lot of tests with all modules known by the human race =:), the modules doesn't read the "rt61stat.dat" file (in the first tests it does, but now /ignore me). My solution was in "iwconfig". Here is an example of my init.d script for the wifi (the real one is more complex reading the exit status of all the commands)

```
#!/bin/sh
. /lib/lsb/init-functions

## CONFIGURANDO
log_begin_msg 'Configuring RT61...'
iwconfig ra0 essid wifissid
if [ $? != 0 ]; then
        log_end_msg 1
else
        iwconfig ra0 mode managed
        iwconfig ra0 channel 5
        iwconfig ra0 key open
        iwconfig ra0 key [1] 0123456789
        iwconfig ra0 key [1]
        log_end_msg 0
fi

## CONECTANDO
log_begin_msg 'Connecting wifi...'
dhclient ra0 2> /dev/nul && log_end_msg 0 || log_end_msg 1
```

See "man iwconfig" for the parameters details.

I hope this could help someone.

Have a nice day =o)

---

### Post by M.Verkerk on 2006-08-04
Great stuff!

For me worked (6.0.6):

1. Copying the the firmware files to /etc/Wireless/RT61STA
2. Editing the rt61sta.dat
3. The following /etc/init.d/rt6 script:

-- Cut --

#!/bin/bash
echo "Bringing up ra0.."

ifconfig ra0 up
iwconfig ra0 essid <ESSID Name>       <- Instead of SSID id
iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=OPEN           <- Watch the CAPITALS
iwpriv ra0 set EncrypType=WEP
iwpriv ra0 set DefaultKeyID=1
iwpriv ra0 set Key1=<Your WEP key>
dhclient ra0

-- Cut --

4. Making the link to rc.S directory

Thanks! This adapter cost me a few evenings but finally it works!

---

### Post by hfthomp on 2006-08-04
Thanks so much for this information!  Worked like a charm.

---

### Post by nation on 2006-08-05
Great guide, although it unfortunately hasn't stopped me from having headaches...

Thanks to Stone123 for this line:

> sudo route add default gw 192.168.*.* 

I'm going through a router and that solved it for me, although I still can't use DHCP.  I haven't tried all the different solutions here (since I'm lazy), but I'm fine with a static IP anyway.  But I added that line to the startup script after the static IP line and it works great now.  I'm running a clean install of Dapper, btw.

---

### Post by xkalvin on 2006-08-06
It works, it works!!!!

I didn't modified my rt61sta.dat, I just follow your notes (in dapper), and edit my init file, introducing your notes about iwpriv...and simply perfect.
My wireless working with dhcp perfectly.

Incredible, after a month,  thaks a lot!!!!


Xavi

---

### Post by juicejuice on 2006-08-06
Just wanted to share my success with an RT61 using the info in the first post of this thread. My card is Gigabyte Aircruser G (WP01GS), on some ancient slot 1 board. lspci identifies card as:

0000:00:09.0 Network controller: RaLink: Unknown device 0301

I am using Ubuntu 6.06 LTS, with the built-in driver. I didn't need to do download any firmware or other stuff. Using the network admin GUI causes the lockup on boot, using iwconfig to set the ESSID also strangely causes a segfault in the driver.

I simply use the following script (don't ask me why I need to set the key twice):

```
#!/bin/sh
iwconfig ra0 key AABBCCDDEE
iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=SHARED
iwpriv ra0 set EncrypType=WEP
iwpriv ra0 set DefaultKeyID=1
iwpriv ra0 set Key1=AABBCCDDEE
iwpriv ra0 set SSID=my_wlan
ifconfig ra0 up
dhclient ra0
```

Thanks to all posters in this thread, this has been very helpful.

---

### Post by [eXr] on 2006-08-07
Sort the commands, you're setting the key before the SSID and other stuff.

"iwcofig ra0 key XXXXX" doesn't work for me too :confused: try something like this:
```
iwconfig ra0 key open
iwconfig ra0 key [1] 0123456789
iwconfig ra0 key [1]
```
This works with an hex key, if you use an ascii string for the key then change the middle line to:
```
iwconfig ra0 key [1] s:mykey
```
I think this could help you :-k

---

### Post by clauskalus on 2006-08-16
I can't seem to find the file $ sudo cp **_rt61.ko_** /lib/modules/`uname -r`/kernel/drivers/net/. Can anyone tell me where it is (its not in the RT61_Linux_STA_Drv1.0.4.0/Modules or -WPA-Supplicant)

---

### Post by clauskalus on 2006-08-16
> **clauskalus said:**
> I can't seem to find the file $ sudo cp **_rt61.ko_** /lib/modules/`uname -r`/kernel/drivers/net/. Can anyone tell me where it is (its not in the RT61_Linux_STA_Drv1.0.4.0/Modules or -WPA-Supplicant)
Never mind, i need to install some kernel headers as i found out when i looked through the pages.

---

### Post by mrfreddy on 2006-08-19
Thanks to earlier posters but running Dapper 6.06.1-LTS amd64-server on an AMD 3800+ X2 with MSI MSI K9NGM2-FID Mobo & using a D-Link DWL-G510 Rev C1 PCI card the only driver to work was the latest beta rt61 from serialmonkey:
[http://prdownloads.sourceforge.net/rt2400/rt61-1.1.0-b1.tar.gz?download]("http://prdownloads.sourceforge.net/rt2400/rt61-1.1.0-b1.tar.gz?download")

The stock one included just locked the terminal up hard when trying: "ifup ra0" or even an "ifconfig". With v1.04 from RaLink's own site I just got a screen full of error message.

Hope this helps some (AMD64 X2) user

---

### Post by mrfreddy on 2006-08-22
My solution above *DID NOT* work for my AMD64 3000+ GA-K8VM800M  single core with Dapper 6.06.1 amd desktop :-k . Issuing the command
```
ifup ra0
```
would fail & any subsequent use of ifconfig or iwconfig would lock the terminal. Following that I could launch gedit or any of the graphical admin tools. Any attempt at restarting would lock at the "deconfiguring network devices" stage & I'd need to press the reset button.

I solved it finally by patching the code from the daily cvs tarball with the patch in a thread on the serialmonkey forums(Note that this patch introduces a small memory leak, hopefully nothing serious & the code should hopefully be refined & integrated into CVS in the near future. But I was desperate to get any form of connectivity :( )
The thread:
[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=1663]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=1663")
The daily cvs build from serial monkey:
[http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz]("http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz")
(It's an attachment to this reply)

(I will presume you have installed kernel headers as per instructions at the beginning of this thread)
unzip the tarball & copy the patch into the Module directory
```
cd /tmp;gunzip rt61-cvs-daily.tar.gz
cd rt61-cvs-2006XXXXXX/Module
cp /path/to/amd64_patch.txt .
patch -p2 <amd64.patch
```
Note that the directory name is dependant of the date the daily-cvs tarball was packed hence the 2006XXXXXX.
Don't worry if patch reports few errors like this:
```
patch unexpectedly ends in middle of line
patching file rtmp_data.c
patch unexpectedly ends in middle of line
Hunk #1 succeeded at 3822 with fuzz 2.
```
Now just compile & install the binaries in the directories mentioned in this thread:
```
make all
cd $(dirname $(find /lib/modules -name "rt61.ko"))
sudo mv rt61.ko rt61.ko-ORIG
sudo cp /tmp/rtrt61-cvs-2006XXXXXX/Module/rt61.ko .
sudo cp /tmp/rtrt61-cvs-2006XXXXXX/Module/*.bin /etc/Wireless/RT61STA
```

now try removing the old module, inserting the new  & try a few iwconfig commands before issuing ifup:
```
sudo rmmod -v rt61
sudo modprobe -v rt61
sudo ifconfig ra0 up
```

and the terminal won't lock up (hopefully ;) )

now just set the mode Wep/WPA keys as mentioned in earlier posts & you're away.

---

### Post by hfthomp on 2006-08-23
Hey everyone.  This is my first crack at Linux, and last night, following the directions on the first page, I was able to get my Linksys PCI card in my desktop working.  Then I rebooted, and the internet connection wasn't there automatically.  I had to open up a terminal and type in

dhclient ra0

This got my connected to my router and everything working again.  Is there something I can do so this is done automatically at start up?  Thanks in advance.

P.S. I am running Dapper

---

### Post by judgekaster on 2006-08-23
> Is there something I can do so this is done automatically at start up? Thanks in advance.

Did you creat the file rt61up as suggested at the start of this mini-howto? If yes, did you make that file executable, i.e.

```
sudo chmod a+x /etc/init.d/rt61up
```

and created a link to that file in "/etc/rc2.d/", i.e.

```
sudo ln -s /etc/init.d/rt61up S33rt61up
```

Otherwise, the script won't be run at startup.

---

### Post by ~damned~ on 2006-08-25
hello, 
i followed the steps above, and my mini pci card gets recognized (has a hardwareadress), and it has also an internet adress (ipv6).. but no ip. i think the reason could be the wpa key.. but how to configurate it?

---

### Post by dragonlor20 on 2006-08-25
> **gregswinford said:**
> I've finally managed to get it working! Hurray!! I had to modify permissions on the xrt61 file to allow all users to execute, and the permissions on the .dat file to allow me to edit it!

The network configured itself using the .dat file, and iwlist ra0 scanning now works too. For anyone trying to set this thing up, DO NOT use the Gnome Networking applet to configure your card, or /etc/network/interfaces: this causes a kernel panic on boot for me!

Many thanks to everyone who's contributed to this thread, particularly Stone123.

The only slightly weird thing happening now is that the DHCP software displays some stuff when I shut down, but presumably this doesn't rerally matter at all?

Many thanks again,
Greg.



How did you get the .dat file to let you edit it? Mine says that it is read-only and won't let me save even when I am sudo...??

---

### Post by oocce on 2006-08-26
First: Thanks for awesome howto! Everything works fine.

But what if I wanna go to public [COLOR="Red"]open[/COLOR] WLAN-area? Should I do some kind of script or what?

---

### Post by judgekaster on 2006-08-26
> **oocce said:**
> First: Thanks for awesome howto! Everything works fine.

But what if I wanna go to public [COLOR="Red"]open[/COLOR] WLAN-area? Should I do some kind of script or what?

That's right. You might want to create some script to automate it. Something like:
```


# just off the bat... might not work
#
# 
SSID=$1
KEY=$2

echo "Setting key"
iwconfig ra0 key $KEY

echo "Setting essid"
iwconfig ra0 essid $SSID

echo "Releasing ra0"
dhclient -r ra0

echo "Setting up ra0 through DHCP"
dhclient ra0

```
save this as "connect-ra0", 'chmod +x' it and run it as

```

./connect <AccessPointName> <Key>

```

Modify the script above to your liking....

---

### Post by oocce on 2006-08-26
> **judgekaster said:**
> That's right. You might want to create some script to automate it. Something like:
```


# just off the bat... might not work
#
# 
SSID=$1
KEY=$2

echo "Setting key"
iwconfig ra0 key $KEY

echo "Setting essid"
iwconfig ra0 essid $SSID

echo "Releasing ra0"
dhclient -r ra0

echo "Setting up ra0 through DHCP"
dhclient ra0

```
save this as "connect-ra0", 'chmod +x' it and run it as

```

./connect <AccessPointName> <Key>

```

Modify the script above to your liking....

Thank you! I have to test this.

---

### Post by dragonlor20 on 2006-08-26
> (c) "No DHCPOFFERS Received"

A lot of people have posted in this thread complaining about the error "No DHCPOFFERS Received" error when they try "sudo dhclient ra0". I myself have encountered this error when trying to connect to one of the APs in the building where I work. However, I couldn't find a solution and thus could not reply to their posts. Until I read reharpernc's post which suggested using "iwpriv" instead of "iwconfig". [For more information on "iwpriv", type "man iwpriv" in your terminal.]

So for people who have encountered this problem, try:

Code:

sudo iwpriv ra0 set NetworkType=Infra sudo iwpriv ra0 set AuthMode=SHARED sudo iwpriv ra0 set EncrypType=WEP sudo iwpriv ra0 set DefaultKeyID=1 sudo iwpriv ra0 set Key1=<my wep key> sudo iwpriv ra0 set SSID=<my essid>


then try to connect to your AP with

Code:

sudo dhclient ra0




This method didn't work for me... Does anyone else have any other fixes? I have followed this HOWTO exactly 3 times, and I just want this to work! Coule someone please troubleshoot this for me???

---

### Post by Morphit on 2006-08-26
I did try the iwpriv method a while back, seemingly to no avail, but after leaving things alone for a while it seems to have been resolved. Thanks again to judgekaster. I've now got things working on boot-up and am now having great fun running server applications and the like :)

---

### Post by dragonlor20 on 2006-08-26
I don't think leaving it alone is exactly the solution that is going to work for me...

---

### Post by judgekaster on 2006-08-26
> **dragonlor20 said:**
> I don't think leaving it alone is exactly the solution that is going to work for me...

You might want to share some information to give us an idea where to start. For starters, kindly post the output of the following:

```

sudo iwconfig    # to let us know whether your adapter has been detected

```

also

```

sudo iwlist ra0 scan   # to know whether it is able to scan for an AP 

```

We sure do would like to see you wirelessly connected....

---

### Post by dragonlor20 on 2006-08-27
> **judgekaster said:**
> You might want to share some information to give us an idea where to start. For starters, kindly post the output of the following:

```

sudo iwconfig    # to let us know whether your adapter has been detected

```

also

```

sudo iwlist ra0 scan   # to know whether it is able to scan for an AP 

```

We sure do would like to see you wirelessly connected....



Thanks for the reply!

My /etc/network/interfaces looks like this

```
auto lo
iface 
lo inet loopback



#auto eth1

#iface eth1 inet dhcp



#auto eth2

#iface eth2 inet dhcp



#auto ath0

#iface ath0 inet dhcp



auto wlan0

iface wlan0 inet dhcp



#auto ra0

#iface ra0 inet dhcp

#wireless-essid rlwa6668


```

And for iwconfig i get:

```
lo        no wireless extensions.

ra0       RT61 Wireless  ESSID:""  
          Mode:Auto  Frequency:1 MHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

```

And for iwlist i get:

```
ra0       Scan completed :
          Cell 01 - Address: 00:14:6C:7B:B9:2C
                    Mode:Managed
                    ESSID:"Valhalla"
                    Encryption key:off
                    Channel:1
          Cell 02 - Address: 00:02:6F:31:13:D5
                    Mode:Managed
                    ESSID:"rlwa6668"
                    Encryption key:off
                    Channel:1
          Cell 03 - Address: 00:16:B6:CB:A3:EC
                    Mode:Managed
                    ESSID:"linksys"
                    Encryption key:on
                    Channel:6
          Cell 04 - Address: 00:14:BF:62:E3:25
                    Mode:Managed
                    ESSID:"Linksys_SES_46938"
                    Encryption key:on
                    Channel:6
          Cell 05 - Address: 00:02:6F:31:50:A8
                    Mode:Managed
                    ESSID:"rlwa6656"
                    Encryption key:off
                    Channel:6
          Cell 06 - Address: 00:06:25:C6:D2:D2
                    Mode:Managed
                    ESSID:"ss"
                    Encryption key:on
                    Channel:6
          Cell 07 - Address: 00:13:46:B6:9A:66
                    Mode:Managed
                    ESSID:"silence"
                    Encryption key:on
                    Channel:6
          Cell 08 - Address: 00:11:50:F0:4A:4A
                    Mode:Managed
                    ESSID:"te0h"
                    Encryption key:on
                    Channel:8
          Cell 09 - Address: 00:0F:B3:BD:6F:7D
                    Mode:Managed
                    ESSID:"QC3E7"
                    Encryption key:on
                    Channel:9
          Cell 10 - Address: 00:09:5B:DF:69:08
                    Mode:Managed
                    ESSID:"Cliff Eight"
                    Encryption key:off
                    Channel:11
          Cell 11 - Address: 00:17:3F:02:C2:6E
                    Mode:Managed
                    ESSID:"JMBC"
                    Encryption key:on
                    Channel:11

```

Thanks for any and all help! Obviously Ubuntu is useless to me without internet... and wireless is my only internet. I have a windows machine next to it to return any info about my network if that helps....

---

### Post by judgekaster on 2006-08-28
Sorry for keeping you waiting...

Have you tried 

```

sudo iwconfig ra0 essid Valhalla
sudo iwconfig ra0 key off
sudo dhclient -r ra0
sudo dhclient ra0

```

Do post your results...

Also, in your interfaces file, you have a section referring to wlan0? do you have such a device. if none, i suggest you comment out those lines.

---

### Post by jorn on 2006-08-30
Judgekaster, you are unbeatable. Theese were exactly the commands I nedded to get my Linksys WMP54gv.4.1 work properly.
The only cange is that I use static ip. I don't use keys but instead the mac-filter on the router where I can allow only the adpters I apply to access the router. Shouldn't that be sufficent?
This is my /etc/init.d/rt61 file:
> # obtain an IP address from a DHCP server
#dhclient ra0
# alternately, you can uncomment the following line to set a #static IP address
ifconfig ra0 192.168.1.100 up
# if you uncomment the line above, make sure to comment line #4

#sudo iwpriv ra0 set NetworkType=Infra
#sudo iwpriv ra0 set AuthMode=SHARED
#sudo iwpriv ra0 set EncrypType=WEP
#sudo iwpriv ra0 set DefaultKeyID=1
#sudo iwpriv ra0 set Key1=<my wep key>
#sudo iwpriv ra0 set SSID=linksys

sudo iwconfig ra0 essid linksys
sudo iwconfig ra0 key off

Thank you for your great help. This is the only guide I have been able to find that works for me.

---

### Post by UphillSkier on 2006-08-30
Judgekaster, thanks for these good looking instructions.

I'm trying to install a wmp54g ver 4.1 card on my dapper system

The link you give for the drivers 

[http://www.ralinktech.com/drivers/Linux/2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz](http://www.ralinktech.com/drivers/Linux/2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz)

comes up in Chinese for me.  I finally found the firmware at
[http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

---

### Post by Stone123 on 2006-08-31
I think we should ask ubuntu staff to include these into restricted-modules, So it takes only one command to install it. 

Just testing edgy clean install  and so far it looks like it will be breezy howto for this one . No startup script needed.

[https://launchpad.net/distros/ubuntu/+ticket/1665](https://launchpad.net/distros/ubuntu/+ticket/1665)

---

### Post by Beastmouth on 2006-09-03
I just want to thank you for this!  This post here ends 2 entire weeks of trying to get wireless working on my Ubuntu machine...  2 weeks, 3 different cards, how many hours.

Now, sir, I raise a glass of fine Kentucky Bourbon to you!

CHEERS!  : - )> **judgekaster said:**
> Sorry for keeping you waiting...

Have you tried 

```

sudo iwconfig ra0 essid Valhalla
sudo iwconfig ra0 key off
sudo dhclient -r ra0
sudo dhclient ra0

```

Do post your results...

Also, in your interfaces file, you have a section referring to wlan0? do you have such a device. if none, i suggest you comment out those lines.

---

### Post by DrepmoreH on 2006-09-03
> **Beastmouth said:**
> I just want to thank you for this!  This post here ends 2 entire weeks of trying to get wireless working on my Ubuntu machine...  2 weeks, 3 different cards, how many hours.

Now, sir, I raise a glass of fine Kentucky Bourbon to you!

CHEERS!  : - )

I can certify that this worked for me too although I had to enter a few other commands to get it working.

sudo iwconfig ra0 key “s:MYKEY”
sudo iwpriv ra0 set SSID=MYSSID
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set Key1=MYKEY

sudo dhclient -r ra0

sudo ifconfig ra0 up
sudo iwconfig ra0 essid MYSSID

sudo dhclient ra0

It looks very scrappy but it works for me! I could probably erase a few of those commands and it would still work but I don't want to risk anything at the moment!

---

### Post by tdshiv on 2006-09-03
thanks for doing this howto, it's been awesome. With your dapper setup it worked really well after you using your solution for the dhclient. for the editing of th rt61sta.dat file, i found gedit to be much simpler just to add that in there.

---

### Post by judgekaster on 2006-09-03
> **Beastmouth said:**
> I just want to thank you for this!  This post here ends 2 entire weeks of trying to get wireless working on my Ubuntu machine...  2 weeks, 3 different cards, how many hours.

Now, sir, I raise a glass of fine Kentucky Bourbon to you!

CHEERS!  : - )

I'll drink to that!

---

### Post by RichLouth on 2006-09-06
Worked like a charm. Thanks. Was really worried the card I bought (Linksys WMP54G, rt61) wouldn't work but without too much trouble it's working just fine:)

A little confusion switching between directories following the howto but otherwise perfect! Once again, Cheers.

---

### Post by judgekaster on 2006-09-06
Glad to have helped you out.. I'll take note of the directory switching confusion and try to improve the howto.

---

### Post by shooby on 2006-09-07
I got this working using WEP, but I have been using WPA for months and wish to use WPA-PSK.  What files would I have to edit and how would I edit them in order to use my WPAPSK?

Thank you!

P.S. I am a total linux newbie

---

### Post by judgekaster on 2006-09-07
I don't have any experience with WPA. I hope some others can help.

---

### Post by Cuppa-Chino on 2006-09-09
> **shooby said:**
> I got this working using WEP, but I have been using WPA for months and wish to use WPA-PSK.  What files would I have to edit and how would I edit them in order to use my WPAPSK?

Thank you!

P.S. I am a total linux newbie

no worries.

just edit the **/etc/Wireless/RT61STA/rt61sta.dat** file as described in the how to and make sure you fill in the following bits:
```

[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=4
**SSID=your-network-name here**
NetworkType=Infra
Channel=3
**AuthMode=WPAPSK  ### select WPAPSK here**
**EncrypType=TKIP  ### select TKIP if you are using that , not sure if AES works**
DefaultKeyID=1
Key1Type=0
Key1Str=10_CHAR_WEP_KEY
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
**WPAPSK=your-passphrase-here ### put your passphrase here, ASCII works**
TxBurst=12
PktAggregate=0
TurboRate=0
WmmCapable=0
AckPolicy1=0
AckPolicy2=0
AckPolicy3=0
AckPolicy4=0
BGProtection=0
ShortSlot=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
PSMode=CAM
TxPreamble=0

```

the rest to be changed as you like or not

---

### Post by oocce on 2006-09-09
Hi! I asked previously how I can connect to Open wlan, and someone made a script for me (didnt work). But I got this whole thing early working with:
```

 ifconfig ra0 up
 iwconfig ra0 essid MYSSID
 iwpriv ra0 set NetworkType=Infra
 iwpriv ra0 set AuthMode=OPEN
 iwpriv ra0 set EncrypType=WEP
 iwpriv ra0 set DefaultKeyID=1
 iwpriv ra0 set Key1=KEY
 dhclient ra0

```
But now Im testing/working with script which should connect to Open wlan. It seems that this EncrypType and Key remains in memory because I can only connect to wlan with encryption.

script:
```

 #!/bin/bash
 echo "Bringing up ra0.."

 SSID=$1
 KEY=$2

 ifconfig ra0 up
 iwconfig ra0 essid $1
 iwpriv ra0 set NetworkType=Infra
 iwpriv ra0 set AuthMode=OPEN
 iwpriv ra0 set EncrypType=WEP
 iwpriv ra0 set DefaultKeyID=1
 iwpriv ra0 set Key1=$2
 dhclient ra0

#put to /bin/connect_wlan ; run $sudo connect_wlan SSID KEY

```
Now SOME WISE GUY tell me how to disable with iwpriv this encryption nonsense! =) Cant find any manuals about iwpriv (or something wich works)!



**SOLVED** have to change:```
 iwpriv ra0 set EncrypType=NONE 
```

---

### Post by theak on 2006-09-10
Judgekaster your a star =D> 

> Can someone confirm that he/she has managed to get WPA-PSK to work in Dapper using Dapper's native rt61-driver, with Ralink's firmware and editing the .dat -file?

I can indeed. Below is my /etc/Wireless/RT61STA/rt61sta.dat, just replace the NetworkID and WPAkey and it should work for you.

```

[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=4
SSID=NetworkID
NetworkType=Infra
Channel=0
AuthMode=WPAPSK
EncrypType=TKIP
DefaultKeyID=1
Key1Type=0
Key1Str=10_CHAR_WEP_KEY
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=WPAkey
TxBurst=12
PktAggregate=0
TurboRate=0
WmmCapable=0
AckPolicy1=0
AckPolicy2=0
AckPolicy3=0
AckPolicy4=0
BGProtection=0
ShortSlot=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
PSMode=CAM
TxPreamble=0

```

---

### Post by OBB on 2006-09-10
Thanks a lot, judgekaster, it worked very well. At least, far enough to get my card to detect the network. When I tried to get an IP address, I got the 'No DHCPOFFERS Received' problem, as described by others here as well. I tried reharpernc's solution, but got the message 

'Interface doesn't accept private ioctl...'

in reply to

$ sudo iwpriv ra0 set Key1=<key>

The other five commands gave no trouble at all; it's just this one. Being the noob I am, I have tried various childish variants such as:
- adding 's:' before the key, since it is an ascii key,
- putting the key between quotation marks, same reason as above
- changing the command to '... set Key1Str=<key>', since in rt61sta.dat it says 'Key1Str' rather than 'Key1'

...but none of them helped, so I assume there is some greater mystery at hand here, that is as yet beyond my power to grasp.
Anyone any ideas on how to solve this?

---

### Post by unknownkadath on 2006-09-11
reharpernc,

Thanks!  Whatever that list of commands you posted was supposed to do, it worked.  You, sir, win the internet. :)

unknownkadath

---

### Post by oocce on 2006-09-12
Has anybody solved how you can see all available wlan-networks in the area?
Pretty hard to connect to ssid without knowledge of available open wlan-networks!!
Or anybody got working any script which connects to network so long it gets connected? Im using laptop at school and this shit doesnt connect well to network in some ares of school (others does :D).

---

### Post by judgekaster on 2006-09-12
try:
> 
iwlist ra0 scan

to get a list of access points in the area.

---

### Post by oocce on 2006-09-13
> **judgekaster said:**
> try:

to get a list of access points in the area.

Thanks a lot!!

---

### Post by ninjaboy13 on 2006-09-13
For the DHCP Address problem the solution is to edit your /etc/Wireless/RT61STA/rt61sta.dat and set the channel to 0.

It will figure out the correct channel once you connect.

Ed

---

### Post by OBB on 2006-09-14
Update on my problem, which is still not solved:

It appears that the problem lies in the length of the key. The one I'm dealing with (I haven't picked it myself, but I'm trying to get into an existing network of which the owner gave me the key) is 12 ascii characters, and when I try the command

sudo iwpriv ra0 set Key1=<12-character key>

...I get the message

Interface doesn't accept private ioctl

...but when I give it a 13-character (or 26, hex) key, it is accepted. But, of course, that doesn't help, since the right key is not 13 characters long. So, does anyone know how to enable WEP-keys that are not exactly 13 ascii characters long? Help would be appreciated very much...

---

### Post by mb108 on 2006-09-16
This guide worked great for my Edimax 7128g that would not work with rt2500... one of those "oops! there's a new version." I did have to enter the extra iwpriv commands. I am using Dapper.

My only comment is that the use of vi for the rt61sta.dat edit makes this guide a toughie for command line newbies. 

Thanks for the help!!

---

### Post by brm on 2006-09-17
I have had slightly different experiences with an AirLink101 AWLC3026T PCMCIA / CardBus adapter. Using Dapper, it is reported as a slightly different device to others discussed on this thread:

Network controller: RaLink: Unknown device 0301
(transcribed from memory, I am running now under the Edgy LiveCD)

Other participants on this thread have reported an "Unknown device 0302".

This card does *_not_* require installing and editing the firmware file discussed at length on this forum. It associates with its access point with a straightforward: ifconfig ra0 up; dhclient ra0 .

Nonetheless, the stability is "brittle": if I take down the interface and bring it back up again, the card will not associate with the access point, even after entering the iwpriv set commands listed in earlier posts. It reports NO DHCPOFFERS RECEIVED. To get the card to associate, a reboot is necessary. Similarly, a command that touches the interface while it is down hangs the terminal; the process cannot be killed and the terminal can be recovered only by rebooting (Ubuntu bug 48087).

I have been unable to get this adapter to associate to the access point using the Edgy Eft LiveCD, no matter what I try; I get the same NO DHCPOFFERS RECEIVED error. A more modern laptop with the built-in Intel wireless chipset and running Dapper associates consistently and flawlessly.

---

### Post by WijbrandSchaap on 2006-09-18
Hi, I am still having trouble getting my wmp54g-eu to work. Have done the whole howto twice, but to no avail. I'm running Dapper. 
At the moment, all I get after IWconfig is > lo        no wireless extensions.

ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Frequency:1 MHz  Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-47 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

So it doesn't show my essid. But when I type iwscan ra0, my essid is recognised, as are those of my neighbours, but I still can't connect. Running Wifiradar gives me my static IP-address, as being connected to "NONE", whilst my essid shows up in the window.
Am I going crazy? Yes.](*,) 
By the way, i'm using WPA, which works perfectly on my laptop on a Belkin card with a RT2500 driver.
Can anyone please help?

---

### Post by parushow on 2006-09-18
judgekaster definitely the best!!

i wasted a lot of hours tring to get workin my dwl g510, then i found your howto, awesome

i m using Dapper, and i tried to add the code

sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=SHARED
sudo iwpriv ra0 set EncrypType=WEP
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set Key1=<my wep key>
sudo iwpriv ra0 set SSID=<my essid>

to the rt61up file, but i still cannot connect at boot.

i m totally new with linux, and actually i have no idea on how should this 
 rt61up file look like. now it is

iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=OPEN
iwpriv ra0 set EncrypType=WEP
iwpriv ra0 set DefaultKeyID=1
iwpriv ra0 set Key1=xxxxxxxxxxxxx
iwpriv ra0 set SSID=default

#!/bin/sh
echo "Bringing up ra0"
# obtain an IP address from a DHCP server
dhclient ra0

# alternately, you can uncomment the following line to set a static IP address
# ifconfig ra0 {IP ADDRESS} up
# if you uncomment the line above, make sure to comment line #4


should it work or i did some mistake?


Thank a lot!!

---

### Post by WijbrandSchaap on 2006-09-18
Regarding my previous post, this afternoon, I hav actually got a working wireless network, using the RT61. Although not using WPA, but WEP. Had to reconfigure the AP, paste in the code and then the miracle happened. So i'm off the hook. 
Over to parushow: You did right in removing the 'sudo's' when adding the lines to your rt61up. However, I think you have put the lines in the wrong place. I have it working by keeping the line #!/bin/sh at the very beginning of the file. This tells the system that it actually is a script. The lines before #!/bin/sh are not taken into account. So: just change the order and make it look like this: 
> 
#!/bin/sh
echo "Bringing up ra0"
iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=OPEN/SHARED*
iwpriv ra0 set EncrypType=WEP
iwpriv ra0 set DefaultKeyID=1
iwpriv ra0 set Key1=*YOUR KEY*
iwpriv ra0 set SSID=*YOUR ESSID*

# obtain an IP address from a DHCP server

dhclient ra0

Edit: maybe you need to make your key 'SHARED'...

But then again, i still have a problem with wpa: is there a way to get WPA working as smoothly as it goes with WEP?

---

### Post by judgekaster on 2006-09-19
parushow, WijbrandSchaap is right. you should paste the "iwpriv" lines after the "shebang" (#!/bin/sh) line. the "shebang" line tells the system what interpreter to use.

---

### Post by judgekaster on 2006-09-19
> Nonetheless, the stability is "brittle": if I take down the interface and bring it back up again, the card will not associate with the access point, even after entering the iwpriv set commands listed in earlier posts. It reports NO DHCPOFFERS RECEIVED. To get the card to associate, a reboot is necessary. Similarly, a command that touches the interface while it is down hangs the terminal; the process cannot be killed and the terminal can be recovered only by rebooting (Ubuntu bug 48087).
Have you tried unloading the module and reloading it, i.e.
```

# sudo rmmod rt61
# sudo modprobe rt61

```

---

### Post by parushow on 2006-09-19
Thanks guys!
but unfortunately the WijbrandSchaap's script (with my options) is not workin

just a question: to have a connection icon on my desktop (to start up with a double click)i could write e file like rt61up and make it executable?

---

### Post by judgekaster on 2006-09-20
> **parushow said:**
> Thanks guys!
but unfortunately the WijbrandSchaap's script (with my options) is not workin

just a question: to have a connection icon on my desktop (to start up with a double click)i could write e file like rt61up and make it executable?
You can create a launcher (right click on the desktop), point it to your script and make sure you enable the option to make it run in a terminal.

---

### Post by binbucket on 2006-09-29
Thanks, the Dapper method worked fine with 6.06.1 and my Edimax MIMO Cardbus adapter, on an old 500MHz P3 laptop.

---

### Post by tenshu on 2006-09-30
any idea if their a solution for edgy ?

---

### Post by thenriques45 on 2006-10-02
I'm having problem with Edgy too. Dapper identify my RaLink Rt61 as "wlan0" and it work just fine. After upgrade to edgy my card still identified as wlan0 but appears a "wmaster0" or something like that, and this "new card" doesn't appears to work for nothing... The wlan0 card find de access point however can't connect...

Anyone know some solution?


PS: Sorry by the english, it's not my native language.

---

### Post by foxxx on 2006-10-02
ok, i now "solved" my problem with my pc54G3 wireless card from msi. i dunno how, but it works...
the last 2 days i tried to fix it, compiled several drivers, installed everything, but to no avail.
so i thought ndiswrapper would be my last solution.
yesterday, before i went to sleep i checked some software packs @ synaptic and also installed a wireless network assistant (i dunno exactly what it´s called in english).
-> today: boot, tried that assistant, and woohooo! it works!

my conclusion: compile those drivers, make sure you did everything right in your configs (wpa, wpapsk, channel, modem/router config...) and REBOOT!
dunno why it didnt work from the beginning, but its possible to get that thing going!

---

### Post by noelferreira on 2006-10-02
hi, does anyone have this card working on an amd64 machine?

thanks, noel ferreira

---

### Post by thenriques45 on 2006-10-03
Ok, i'm trying to compile the rt61 drivers on Edgy and the make thing complain that the /lib/modules/2.6.17-10-386/build doesn't exist.

I had already installed the sources, kernel headers, gcc, make and a lot of other stuff, but I the problem persist.

Anyone had any clue about it?

PS: My english still being crap... Sorry.

---

### Post by mgazelle on 2006-10-04
Thank you for the nice how to.

Just a small update for the driver url [http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz](http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz)

---

### Post by OBB on 2006-10-06
New problem:

I have recently moved, and in my new room there is a new network, this time with a key that doesn't give any trouble (see previous replies to this thread). I have tried 'iwlist ra0 scan' and 'iwconfig ra0' and that all worked; the scan found some networks, including the one I was trying to connect to, and iwconfig showed information for ra0. Only when I try 'ifconfig ra0', it says

HWaddr ..:..:..:..:..:.., showing the address of the accesspoint I was trying to connect to in my previous room. It only shows this after I have given the command

sudo ifconfig ra0 up

before giving that command, it just says HWaddr 00:00:00:00:00:00. So, I assume that this old access point address has been saved somewhere, but I have no clue as to how to change this. Any ideas? I am at your mercy...

---

### Post by zakhooi on 2006-10-09
I went through this whole topic (and a lot website too) but still can't get it to work.
I have a sitecom wl-112 with the ralink chipset and need to get rt61 working.
Besides that I need to get wpa-psk working.
The card can be detected and the interface ra0 is available.
The problem is with dhcp, I can't get rid of the error "No DHCPOFFERS received". I tried all things mentioned here.
My OS is Ubuntu Dapper 6.06 (all packages are updated).

A little info about my config:

root@laptop:~# modinfo rt61
filename:       /lib/modules/2.6.15-26-386/extra/rt61.ko
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
description:    Ralink RT61 802.11abg WLAN Driver 1.1.0 CVS CVS
license:        GPL
vermagic:       2.6.15-26-386 preempt 486 gcc-4.0
depends:
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
srcversion:     A5A54024A1F171DB9CDDE85
parm:           ifname:Network device name (default ra%d) (charp)
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (int)

root@laptop:~# cat /etc/Wireless/RT61STA/rt61sta.dat
[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=4
SSID=<Ive put my SSID of my AP here>
NetworkType=Infra
Channel=0
AuthMode=WPAPSK
EncrypType=TKIP
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=<Ive put my encrypted WPA-PSK key here>
TxBurst=12
PktAggregate=0
TurboRate=0
WmmCapable=0
AckPolicy1=0
AckPolicy2=0
AckPolicy3=0
AckPolicy4=0
BGProtection=0
ShortSlot=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
PSMode=CAM
TxPreamble=0


Any ideas? I'm desperate...

---

### Post by Quamper on 2006-10-11
These directions worked great for me on Dapper using a Linksys WMP54G.

I was using WPA2 so simply changing AuthMode to WPA2PSK and EncrypType to TKIP along with setting WPAPSK to my Key value it worked brilliantly.

Is there some kind of applet I can run that will monitor/show signal strength without messing up these changes I've made?

---

### Post by foxxx on 2006-10-11
try Wireless Assistant 0.5.5 (dunno what the synaptic package is called)

---

### Post by tdehoog on 2006-10-12
Hey thanks a lot man!!!

This really helped me out. I have a Linksys WMP54g v4.1 and it's working great so far :)

the dhclient trick works like a charm :D

---

### Post by Aflex on 2006-10-16
Just followed the instructions as mentioned for dapper drake for Sitecom WL-171, and it works flawlessly.

Thanks!

---

### Post by bunnybash on 2006-10-23
i am so new to linux and i think that the biggest problem that my friends and family are having with ubuntu is wifi...

i have a lappy and a desktop that i only have wifi access and i cannot for the life of me get the wifi cards working... they are based on Ralink 2500 chipset, seriously this is the only issue keeping me using microsoft?  i know that it cant be that insanely hard to build in the support for ralink 2500 cause they offer FOSS drivers for their stuff... why is this so hard!!!!  

i feel like the only way i could figure this out would be someone standing over my shoulder showing me, but the problem is that i cant access the internet on these machines when they are booted into ubuntu, so i find myself going back to XP... hmmm i dream of the day when ubuntu will not make me feel like going postal cause the wifi wont work... this is the 3rd edition of ubuntu i have tried now... i must be an idiot, or like the other 90% of computer users, just used to stuff working...](*,)

---

### Post by bretnj on 2006-10-23
I have the same question as on the previous page.  Is there some sort of systray type applet that will just monitor the wireless signal w/o affecting my configurations?  I saw wireless assistant said, but that looks like you have to use the app to connect to the  router and then it will show the icon.  I'm worried that would alter my configurations that I have at boot already.  Thanks guys.

---

### Post by neveceral on 2006-10-26
any idea about solution for edgy ? I have linksys wmp54g and it isn't working Thank you.

---

### Post by foxxx on 2006-10-26
@bretnj: i also had trouble installing those ralink drivers, but after the right configuration it worked. (although my wireless card is still "unknown")
installing wireless assistant did in fact nothing at all, i just happenend to install it out of curiousity and desperation - although it let´s you connect and configure your wireless networks. as long as you use it as a monitor, it´s not even needed to run at startup to keep your wireless card working.

---

### Post by bretnj on 2006-10-26
oh ok, good info.  so if i run it after startup, it will just show the signal strength?  Perfect! 

As far as your device still showing up as unknown, I figured that one out.  Update your pci.ids.  Ubuntu is running an older one by default.

cd /tmp
wget [http://pciids.sourceforge.net/pci.ids](http://pciids.sourceforge.net/pci.ids)

I'm not sure exactly where the pci.ids is, but just run find / -name pci.ids and then cp the new one over there.  'lspci' and it should now show your card.

---

### Post by cbarba on 2006-10-26
It' s should works
sudo update-pciids

---

### Post by aloysius on 2006-10-26
desperate for a solution for edge (kubuntu) here as well. has anyone got this working using edgy?

---

### Post by blackest_knight on 2006-10-27
hi 
this is for the Edimax EW-7128g PCI card in Dapper

I will run through what I did and where I went wrong!

[http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980) 
I followed this first post in general but with a few differences. 
hopefully you will have a Driver CD with the Debian Drivers in there. 

a) lspci my unknown device was 0301
b) skip b because no net connection instead copy debian folder to Desktop
from the CD
c) no net access no headers never mind ;) can't compile anything
just go into the debian folder and find the .bin files and the .Dat file

$ sudo mkdir /etc/Wireless/RT61STA/
$ sudo cp *.bin /etc/Wireless/RT61STA/.
$ sudo cp rt61sta.dat /etc/Wireless/RT61STA/.

(when your in the Debian folder with the bin files and Dat file that should be ok 

(d) Edit the /etc/Wireless/RT61STA/rt61sta.dat as a binary file. The recommended way of doing this is:
Code:

$ cd /etc/Wireless/RT61STA $ sudo vi -b rt61sta.dat

basically you need to read up on vi a bit 
[http://www.cs.colostate.edu/helpdocs/vi.html](http://www.cs.colostate.edu/helpdocs/vi.html)
If your network is open all you need do is change the Essid to your Essid and save it. (forget security for now!)

[B](e) copy the rt61.ko driver file to the modules directory then load it

Code:

$ sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/. 
$ sudo depmod 
$ sudo modprobe rt61

(Note that the rt61 will automatically be loaded the next time you boot your Ubuntu machine.)
[/B]

DO Not do this !
in your Debian directory is rt61.ko but it doesn't work on ubuntu, to make things worse it will appear to work because ubuntu will have already loaded rt61.ko from an existing folder 

/lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2600/rt61.ko
go to that folder and then

$ sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/. 
$ sudo depmod 
$ sudo modprobe rt61

you need the existing rt61.ko file from rt2600 not the one from the debian
folder on the CD.
because ubuntu dapper detects your card it will have loaded the rt61.ko module when it booted. when you reboot using the debian one it will fail because it isn't compatible (dont worry the bin files are ok).

carry on do e) f) g) and h)

by this point wireless should be working, however if you did put in the wrong rt61.ko file next reboot your wireless will be broken.

if you look at an existing dapper system thats had a few kernel upgrades the ra0 kernel modules are the same. just duplicates under different kernel 

I gather with Edgy things have changed a bit however probably still ships with the right rt61.ko module if not you will need to build it.

the relationship betweenra0, bin, dat, and ko files is probably something like this. the Dat file is just configuration values like the Essid, ra0 is an alias for the specific driver needed kind of like saying printer instead of epsom cx45 or lexmark z23 the os is taking care of what specific device will be used. The ko file takes the generic requests and translates these requests into something the interface of the hardware requires so the os talks to ko who talks to bin. ko and bin have   a protocol or strictly defined language to talk to each other. bin on the other hand is an interperator for the particular device , the particular device implimentation can change and the device manufacturer will change bin internally to suit but bin still talks the same protocol ko understands. the consistant interface is essential  

if hardware is too different you need a new protocol and thus a new driver. Anyway I think thats roughly the relationship
with edgy the os has changed big time ra0 is now wlan0 or is it wmaster (very confusing) so a new rt63.ko is needed to talk to the same old bin file dappers rt63.ko used to talk to.

hope this helps

---

### Post by Cuppa-Chino on 2006-10-27
> **aloysius said:**
> desperate for a solution for edge (kubuntu) here as well. has anyone got this working using edgy?

this thread: [http://ubuntuforums.org/showthread.php?p=1674249](http://ubuntuforums.org/showthread.php?p=1674249)

now shows this work around: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117/comments/11](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117/comments/11)


FIXED with the launchpad and other thread help mine is (finally) working

---

### Post by neveceral on 2006-10-28
to blackest_knight
i did it with ralink drivers 1.0.4 and now i have not any wifi - no wlan no wmaster in Networks and linksys wmp54g still don't work ...

---

### Post by blackest_knight on 2006-10-28
I did post about the edimax pci card not the linksys wmp54g.
and it was for dapper not edgy.

assuming you have rt61 chipset take a look at this post
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117/comments/11](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117/comments/11)

with dapper, ubuntu's half of the driver rt61.ko included by default but not the .bin files this is why i was able to copy the existing rt61.ko file and make it work. 

if you read the linked post he's neatly sidestepping the problems with wlan wmaster. 
it looks like to me is 
ubuntu boots detects card looks for a driver sees rt61pci and trys to use it to create the wlan0/ wmaster0 network card. 
this appears to be broken

so what he does is blacklist the rt61pci driver so now ubuntu doesnt load it and uses the dapper method to create a device ra0 instead.

sorry I can't help further I am not an expert.
[http://ubuntuforums.org/showthread.php?t=283442](http://ubuntuforums.org/showthread.php?t=283442)
this thread lists some cards that are working without issues in edgy, you might want to consider one of them as a quicker solution to your wifi problems.

---

### Post by foxxx on 2006-10-28
@bretnj: yup, just shows the signal strength (at least for me)
and thx for the tip about "unknown wireless card", but i like to follow a simple principle: never change a running system
better safe than sorry ;)

edit: and why did i spill the beans?? WTF?!?

---

### Post by Cuppa-Chino on 2006-10-28
> **blackest_knight said:**
> I did post about the edimax pci card not the linksys wmp54g.
and it was for dapper not edgy.

assuming you have rt61 chipset take a look at this post
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117/comments/11](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117/comments/11)

with dapper, ubuntu's half of the driver rt61.ko included by default but not the .bin files this is why i was able to copy the existing rt61.ko file and make it work. 

if you read the linked post he's neatly sidestepping the problems with wlan wmaster. 
it looks like to me is 
ubuntu boots detects card looks for a driver sees rt61pci and trys to use it to create the wlan0/ wmaster0 network card. 
this appears to be broken

so what he does is blacklist the rt61pci driver so now ubuntu doesnt load it and uses the dapper method to create a device ra0 instead.

sorry I can't help further I am not an expert.


yes the workaround looks nice but I still have a couple of questions: [http://ubuntuforums.org/showpost.php?p=1674249&postcount=21](http://ubuntuforums.org/showpost.php?p=1674249&postcount=21)

as some steps are not 100% clear

---

### Post by kanchata on 2006-10-28
Hello, I´re new on the site, searching help about ralink chipset & linux, I´make download lates Xubuntu release to install on Pc x86, with the thread only want put one comment, :::> Your are referred to a install Ralink legacy drivers for RT chips elsewere, this is not for rt2x00 testing drivers developped for rt2x00.serialmonkey to implement of a vary features not enclossed on a legacy drivers.
Only  the point is a point, nothing.
Thank´s, see your later.
Kanchata

---

### Post by Mike_Longbow on 2006-10-31
Hi everyone.
I got a problem with my rt61 card... I installed it according to judgekaster howto using the dapper native driver (I'm running Xubuntu Dapper) and it worked fine the first time. Then, after a reboot, it was no longer working: when I try to set an static IP I get a:
**Segmentation fault.**
The same if a try to use "dhclient ra0", and then the kernel crashes and terminal stops responding...
Could anyone tell me what's going on and how to fix it??!!
Please!!! I'm desperate, I've been trying to get this working for about a month...

PLEASE

---

### Post by Kurdt on 2006-11-01
I run over a similar situation Mike, and.. i gave up.. I bought an usb wireless from Encore and is working fine (with ndiswrapper)

I suggest that if you can change it for another card, do it.

---

### Post by Mike_Longbow on 2006-11-03
> **Kurdt said:**
> I run over a similar situation Mike, and.. i gave up.. I bought an usb wireless from Encore and is working fine (with ndiswrapper)

I suggest that if you can change it for another card, do it.

Perhaps I'll have to do that also...
I mean, I made it work (at last!), I was just that I missed a line in the scrip for boot up...

Anyway, and move a lot, and a need to access to many networks, but since this card only works with a single one (at my home) I think I'll have to get another adapter :neutral: 

DOES ANYONE KNOWS A WAY TO MANAGE DIFFERENT NETWORKS WITH THIS CARD? (I've tried ra0dar, but I can't get it working)

Greetings.
Mike.

---

### Post by Kurdt on 2006-11-04
I suggest looking on ndiswrapper site, is constantly updating support for many cards...

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

---

### Post by aldin on 2006-11-05
> **Mike_Longbow said:**
> Hi everyone.
I got a problem with my rt61 card... I installed it according to judgekaster howto using the dapper native driver (I'm running Xubuntu Dapper) and it worked fine the first time. Then, after a reboot, it was no longer working: when I try to set an static IP I get a:
**Segmentation fault.**
The same if a try to use "dhclient ra0", and then the kernel crashes and terminal stops responding...
Could anyone tell me what's going on and how to fix it??!!
Please!!! I'm desperate, I've been trying to get this working for about a month...

PLEASE

hi, if u have dapper just use dapper's rt61 mudule that ships with kernel, no some external drivers it works great...

in file:

/etc/network/interfaces

just add:

auto ra0
iface ra0 inet dhcp

reboot (though there is faster way but...)

after reboot try iwconfig u should have ur card set, after that ifconfig ra0 ...

ps:
i wass getting "segmentation fault" if no "ra0" in /etc/network/interfaces

---

### Post by yet another newbie on 2006-11-05
(c) _"No DHCPOFFERS Received"_

A lot of people have posted in this thread complaining about the error "No DHCPOFFERS Received" error when they try "sudo dhclient ra0". I myself have encountered this error when trying to connect to one of the APs in the building where I work. However, I couldn't find a solution and thus could not reply to their posts. Until I read reharpernc's [post]("http://ubuntuforums.org/showpost.php?p=1310334&postcount=117") which suggested using "iwpriv" instead of "iwconfig". [For more information on "iwpriv", type "man iwpriv" in your terminal.]

So for people who have encountered this problem, try:

```

sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=SHARED
sudo iwpriv ra0 set EncrypType=WEP
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set Key1=<my wep key>
sudo iwpriv ra0 set SSID=<my essid>

```

then try to connect to your AP with

```

sudo dhclient ra0

```

If this works for you, you might want to include the above lines in the "/etc/init.d/rt61up" script so that it will run at startup. Please do post a reply if whether this worked for you or not.

That's it!

# Edited Sun Jun  4 18:53:32 PHT 2006 in response to posts made in this thread. Thanks to all the inputs!

(a) made some steps more newbie-friendly

(b) instead of making the symbolic link in /etc/rc2.d, suggested that it be made in /etc/rcS.d

(c) added note about not using network-admin 

(d) added note about installing in dapper

# Edited Monday, 19 June 2006 07:55 PM 

(a) under Dapper instructions, corrected #3, should be steps (f) to (h) instead of (f) to (g). thanks to ferenczi and KuifjePDX

# Edited Wed Aug  2 20:22:03 PHT 2006

(a) added possible solution to "No DHCPOFFERS Received" problem.[/QUOTE]

Number 1 --- THANK YOU, THANK YOU! :-D I'm finally connected using Ubuntu

My only question is on the is on the script to create: should I include the last line "sudo dhclient ra0"

A couple of short notes for other newbies: under rt61 in Dapper (b) you will need to make a Wireless directory first
put sudo in front of cp to copy the files to the RT61STA directory
put sudo in fron of the tar command to extract

Again -- many, many thanks judgekaster and all who contributed to this thread!

---

### Post by aldin on 2006-11-05
carefully look at outputs, it works great even on edgy, just downgrade kernel (u can take it from edubuntu 6.06 cd - apt-get install linuximage-2.6.15...) and do what i said in previous post (about /etc/network/interfaces),

again i say, no need for Ralink drivers cause they ship with ubuntu kernel allthough there is no kernel modules for this card on mandriva suse etc...

aldin@kanta:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"
aldin@kanta:~$ 
-----
aldin@kanta:~$ lspci|grep -i ralink
00:0a.0 Network controller: RaLink Unknown device 0302
aldin@kanta:~$ 
-----
aldin@kanta:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""  
          Mode:Auto  Frequency:1 MHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-121 dBm  Noise level:-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ppp0      no wireless extensions.

aldin@kanta:~$ 
-----

aldin@kanta:~$ uname -a
Linux kanta 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
aldin@kanta:~$ 
-----

aldin@kanta:~$ lsmod|grep rt61
rt61                  223616  1 
aldin@kanta:~$ 
-----

aldin@kanta:~$ modinfo rt61
filename:       /lib/modules/2.6.15-23-386/kernel/drivers/net/wireless/rt2600/rt61.ko
author:         Paul Lin <paul_lin@ralinktech.com>
description:    RT61 Wireless Lan Linux Driver
vermagic:       2.6.15-23-386 preempt 486 gcc-4.0
depends:        
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
srcversion:     E2030945E2D3013D967EB7F
aldin@kanta:~$

---

### Post by yet another newbie on 2006-11-06
Has anyone been able to get the start up script to run automatically without errors?

I'd like to have these commands run at boot up:
sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=SHARED
sudo iwpriv ra0 set EncrypType=WEP
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set Key1=<my wep key>
sudo iwpriv ra0 set SSID=<my essid>
sudo dhclient ra0

Thanks in advance for your help

---

### Post by judgekaster on 2006-11-06
> **yet another newbie said:**
> Has anyone been able to get the start up script to run automatically without errors?

I'd like to have these commands run at boot up:
sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=SHARED
sudo iwpriv ra0 set EncrypType=WEP
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set Key1=<my wep key>
sudo iwpriv ra0 set SSID=<my essid>
sudo dhclient ra0

Thanks in advance for your help

what errors have you been encountering?

---

### Post by Kurdt on 2006-11-07
BUT that solution at the beginning of this thread do not works with WPA Encryption. A must have if you want security...

---

### Post by reler on 2006-11-07
> **Kurdt said:**
> BUT that solution at the beginning of this thread do not works with WPA Encryption. A must have if you want security...

Absolutely. 

Having done this:
   ](*,) 
for several days, first trying to get ubuntu installed on an ancient PC (which needed the "alternate" disc image before it got past hardware config), then trying to get my EW7128 configured, I finally got somewhere by following blackestnight's advice in post 199 of this thread. Thanks.

However, I too am getting the "No dhcp offers" problem and cannot use the suggested workaround because I have to use WPAPSK with AES. So far, I have drawn a blank and having spent waaaay tooo long on this "short term" project already, cannot afford to do this:
  ](*,) 
any longer.

Plus (boohoo), I am a Linux noob so everything takes 10 times longer.

Does anybody know how to get this wretched card working with dapper in WPAPSK mode ?

Thanks

Reler

---

### Post by reler on 2006-11-07
Finally seem to have got it to work with WPA and am using it to make this post ! How ?

Was able to get my router to recognise the MAC address of the adapter and to always assign it a fixed IP address (forgot to say before that I was trying to get a dynamic address using dhclient).

Even then, I wasn't not convinced that the .dat file parameters are being picked up. I manually entered all of these commands: 
   sudo iwpriv ra0 set SSID=<my SSID>
   sudo iwpriv ra0 set AuthMode=WPAPSK
   sudo iwpriv ra0 set EncrypType=AES
   sudo iwpriv ra0 set WPAPSK=<my key>
Then it worked ! :D 

Many thanks to all those who wrote in this thread (and others) and which left clues.

All I need to do now is to make sure it survives a boot and then get FTP, Apache, MySQL & PHP working ! Wish me luck.

Reler

---

### Post by Ny_linux_bruger on 2006-11-07
I am totally new to Ubuntu and Linux. All my experience with computers is from using Windows for the last 15 years. 

I have installed Ubuntu 6.06 Dapper Drake. The download and installation of Ubuntu proceded without any problems.

I have bought a D-Link Model No.: DWL-G510 H/W rev.: C2 F/W Ver.: 5.00 wireless network card, because I need a wireless connection.

I then searhced the web with the phrase "ubuntu RT61" and thereby found this thread which looked very credible to me.

I have then tried to follow the howto regarding "(b) rt61 in Dapper" in the first post by judgekaster to try to get the wireless network card up running.

But when I get to "3. Do steps (f) to (h) above." it seems like the driver is not running.

From MS Windows I would expect that I would have to start the driver somehow, but is this done automatically in Ubuntu? 

What have I missed or done wrong?

I have reinstalled Ubuntu once and then one more time very carefully tried to follow the howto in post #1 but it didn't change anything.

I have read all 22 pages in this thread to see if there was any hints hidden there but I didn't find anything that could help me.

As I read the howto there should be no need to move the following file:
"/lib/modules/2.6.15-27-386/kernel/drivers/net/wireless/rt2600/rt61.ko"
Is that correct?

Below is a listing that I have copied from the terminal window

The listing is from when I try to proceed with step (f)

```
m01@edubuntu:/etc/Wireless/RT61STA$ ls
rt2561.bin  rt2561s.bin  rt2661.bin  rt61sta.dat

m01@edubuntu:/$ sudo dhclient ra0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
ra0: ERROR while getting interface flags: No such device
ra0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

m01@edubuntu:/$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:02.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:02.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:02.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:02.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:12.0 Network controller: RaLink: Unknown device 0302
0000:00:14.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 0c)
0000:01:01.0 VGA compatible controller: S3 Inc. Trio 64 3D (rev 01)

m01@edubuntu:/$ sudo find -name 'rt61.ko'
Password:
./lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/rt2600/rt61.ko
./lib/modules/2.6.15-27-386/kernel/drivers/net/wireless/rt2600/rt61.ko
```

Any suggestions to help me succeed with the installation of this wireless card will be appreciated very much

---

### Post by judgekaster on 2006-11-07
Seems that the module (driver) has not yet been loaded. Try modprobe'ng it and see if the device was recognized (iwconfig). Use the following commands:

> $ sudo modprobe rt61 
iwconfig


Good luck!

---

### Post by Ny_linux_bruger on 2006-11-08
Thank you for your advice judgekaster.

Ufortunately it doesn't really seem to change anything.

Here is a screendump:

What do I do wrong?

```
m01@edubuntu:~$ sudo modprobe rt61
Password:
m01@edubuntu:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

m01@edubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:02.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:02.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:02.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:02.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:12.0 Network controller: RaLink: Unknown device 0302
0000:00:14.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 0c)
0000:01:01.0 VGA compatible controller: S3 Inc. Trio 64 3D (rev 01)

```

---

### Post by scottws on 2006-11-08
judgekaster,

Thank you for your excellent guide on getting wireless cards with the RALink RT61 chipset working in Ubuntu.

I finally got rid of my Motorola WPCI810G (based on Broadcom) in favor of a card with the RALink chipset.  I received my Gigabyte Technology GN-WP01GS on Monday, and decided to give Linux another shot now that I would actually be able to get the Internet working.

I was delighted to see a wireless adapter listed in the Networking tool, and I could verify that it was partially working because it detected my network's SSID.  So I went ahead and configured the WEP key and activated it.  It didn't seem to ever acquire an IP address, so I did things like retype the WEP key, enable the IPv6 DHCP support on my router, go into the terminal and bring up and down the internet and the networking services as a whole.  Eventually, my system locked up, and would hang on boot at configuring the network.

It was then I did some searching and discovered that my GN-WP01GS has the RALink RT61 chipset, not the better-supported-in-Linux RT2xxx.  Once I learned this, searches quickly lead me to this thread.

I couldn't be happier.  Your guide is very clear and well organized, and the best part is that your instructions worked flawlessly!

Thanks!

---

### Post by ogami1972 on 2006-11-08
Super Rock!!
Your guide got my card working!!

airlink101 802.11g wireless adapter
dell dimension 8400
edgy eft 2.6.17-10-386

!!

thanks for all your hard work!!!

now, about this netgear card.....](*,)

---

### Post by Biozid on 2006-11-10
Has anyone got their card up and running with dhcp and wpa?

---

### Post by neveceral on 2006-11-10
yes, linksys WMP54G in edgy :-) Look here [http://ubuntuforums.org/showthread.php?t=285072&page=4&highlight=edgy+rt61](http://ubuntuforums.org/showthread.php?t=285072&page=4&highlight=edgy+rt61)

---

### Post by zakhooi on 2006-11-11
Finally I got it to work with Edgy.
I used this procedure:  [http://www.ubuntuforums.org/showthread.php?t=296822](http://www.ubuntuforums.org/showthread.php?t=296822)

And in my case any other wifi device needs to be disconnected at boot time.

---

### Post by huygens on 2006-11-19
> **zakhooi said:**
> Finally I got it to work with Edgy.
I used this procedure:  [http://www.ubuntuforums.org/showthread.php?t=296822](http://www.ubuntuforums.org/showthread.php?t=296822)

And in my case any other wifi device needs to be disconnected at boot time.

I confirm, I also used the procedure you are mentionning and it worked perfectly :-)

---

### Post by Ny_linux_bruger on 2006-11-24
This is a continuation of my story in post #218 and #220

I finally managed to get my wireless card to work with WPA and DHCP. Trying many things without geting "ra0" listed by using iwconfig I finally tried to physically remove my ethernet card. And suddenly I was able to se "ra0" when using iwconfig.

I then put the ethernet card back into the computer (an old IBM 300GL) and I was still able to see "ra0" on the list when using iwconfig.

I then played around with different commands for a while. After using the following command the wireless card again ceased to work

```
iwpriv ra0 set ResetCounter=0
```

I then tried to shutdown the computer but the ra0 device had now disappeare

```
m01@edubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

m01@edubuntu:~$
```

I then once again removed the ethernet card, booted the computed one time without the ethernet card in place. I then put it back into the computer and booted the computer. And then the card worked again!

I then continued experimenting with different command line input which I finally put into the file rt61up by using ```
$ sudo gedit /etc/init.d/rt61up
``` as described by judgekaster in post #1. Here is what I ended up with: 

```
#!/bin/sh
echo "Bringing up ra0"

# configure a static IP address simply to make it possible to use iwpriv
# change later to use DHCP server
ifconfig ra0 100.100.100.100 up

# Configure network to infrastructure
iwpriv ra0 set NetworkType=Infra

# Configure wireless interface to use 11b/g mixed
iwpriv ra0 set WirelessMode=0

# Configure wireless interface to use WPAPSK and TKIP 
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=TKIP

# set SSID and password
iwpriv ra0 set SSID="My SSID"
iwpriv ra0 set WPAPSK="My password"
iwpriv ra0 set SSID="My SSID"

# change from static IP and obtain an IP address from a DHCP server
dhclient ra0

```

I still very new to Linux/Ubuntu and I really don't know what the following command does but I have executed it as described by judgekaster in post #1 and now every thing seems to work!

```
$ cd /etc/rcS.d
$ sudo ln -s /etc/init.d/rt61up S33rt61up
```

There is doubt that I would never have got this card to work without this forum and especially the post #1 by judgekaster so thank you one more time!

---

### Post by K.Mandla on 2006-11-28
One more note of thanks. This got my WMP54G v4 running with DHCP and WEP under Edgy. I did have one hiccup: I needed the nvidia-glx-legacy drivers for my video card, so after I got online and updated, I had to do the entire process a second time for the 386 kernel ... which meant I needed the linux-headers-386 package as well. 

If there was an easier way to do that than going through the whole process again, somebody let me know. ... :)

---

### Post by Baf on 2006-12-06
Has anyone gotten the RT61 Chipset drivers to work under 64 bit? Or successfully tried this guys post in this thread? [http://ubuntuforums.org/showpost.php?p=1407529&postcount=135](http://ubuntuforums.org/showpost.php?p=1407529&postcount=135)

I've tried the original How-To in the beginning of this thread and my terminal gets locked up when I try:

```
sudo dhclient ra0
```

I've noticed a few others that have had the same problems. I'm wondering if anybody has gotten this to work under 64 bit whether it be by new and updated drivers, updated OS, etc? I'm running Dapper. It looks like it's fairly easy in a 32 bit enviornment so I may, with reluctance, switch to 32 bit. Input would be appreciated!

---

### Post by christoph.macho on 2006-12-10
well thank's for the this excellent guid, i have still problems with my dwl g510 rev C2 fw5.00 in dapper 6.06.
card is in but i cant set essid. 

iwconfig looks like

lo        no wireless extensions.

ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Channel:6  Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-78 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

christoph@christoph:~$ sudo cat /etc/Wireless/RT61STA/rt61sta.dat
Password:
[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=macho13a
NetworkType=Infra
Channel=0
AuthMode=OPEN
EncrypType=WEP
DefaultKeyID=1
Key1Type=0
Key1Str=012AD56BC7
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=abcdefghijklmnopqrstuvwxyz
TxBurst=0
PktAggregate=0
TurboRate=0
WmmCapable=0
AckPolicy1=0
AckPolicy2=0
AckPolicy3=0
AckPolicy4=0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0

christoph@christoph:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:0e.0 Network controller: RaLink: Unknown device 0302
0000:00:0f.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage XL AGP 2X (rev 65)

christoph@christoph:~$ iwlist ra0 scanning
ra0       Scan completed :
          Cell 01 - Address: 00:17:9A:62:A7:31
                    ESSID:"macho13a"
                    Mode:Managed
                    Channel:6
                    Encryption key:on

anyone who can help me? 
when i do iwconfig essid 

christoph@christoph:~$ sudo iwconfig ra0 essid "macho13a"
christoph@christoph:~$ iwconfig
lo        no wireless extensions.

ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Channel:6  Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-78 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
:-k  
don't know what i should try more,
anyone who can help me?

---

### Post by DuckFish on 2006-12-10
**Thank you, judgekaster!**

It works! (Ubuntu 6.06, GNOME)

I'm new to Linux; I don't know how to use vi, so I edited rt61sta.dat using gedit, then copied it to /etc/Wireless/RT61STA.
At first, I tried to use the Network Admin, but it locked up on boot, so I reinstalled Ubuntu. And I tried it again...then found this and changed the interfaces file to look the same as in yours. Hopefully, it won't lock up on boot again!

---

### Post by cirorodrigues on 2006-12-11
Hi, thanks by your how-to. It gave me at least some clues to configure my DWL-G510 rev.C. It still doesn't work :-k , as when I tried to load the new rt61 module I go "invalid module format". Command dmesg shows me some advice like as compile with gcc-4.0 instead of gcc3.4 (sorry, I'm not in front of my Ubuntu box). Maybe gcc used to compile the module was not the same used to compile the kernel?
 
Just one additional point: I compiled a new rt61.ko and copied it over the original one. **How to recover the original rt61 module from cd or internet?** I'm using Dapper Drake.
 
Ciro

---

### Post by maral on 2006-12-20
I have fedora core4, but I think it's the same. When i try **$ modprobe rt61**, I get this answer: **FATAL: Error inserting rt61 (/lib/modules/2.6.16-1.2107_FC4/kernel/drivers/net/rt61.ko): Invalid module format**I have it save in *.ko but it says it is invalid format. I do not know why. Can some body help me?:-k

---

### Post by cirorodrigues on 2006-12-21
I've run dmesg after this error message and it says something related to version of gcc. My impression is that new rt61.ko module compiled accordingly to this thread used a gcc version newer than gcc used to compile the kernel. I'm a newbie in Linux, but my guess is gcc was updated after installing Ubuntu, so the kernel was compiled with gcc 3.x and the new modules are been compiled with gcc 4.x. I don't know how to force the use of gcc 3.x to recompile rt61.ko and even if is it possible. Other way could be recompile whole kernel, but I think there should be an easier path to follow.:confused:

---

### Post by r_a_trip on 2006-12-21
> **cirorodrigues said:**
> I don't know how to force the use of gcc 3.x to recompile rt61.ko and even if is it possible.

It is possible. Use " export CC=/usr/bin/gcc-3.4 " on the commandline (without quotes) and then start compiling the module.

The reason that the kernel is compiled with gcc 3.4 is because of issues with compiling that kernel version with gcc 4.x.

---

### Post by potatochip on 2006-12-22
The link to download the driver has changed.

[http://www.ralinktech.com/ralink/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz](http://www.ralinktech.com/ralink/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz)

It might be worthwhile putting this in the initial post.

Going to try and get it working now after a clean install. :)

---

### Post by cirorodrigues on 2006-12-26
> **r_a_trip said:**
> It is possible. Use " export CC=/usr/bin/gcc-3.4 " on the commandline (without quotes) and then start compiling the module.

The reason that the kernel is compiled with gcc 3.4 is because of issues with compiling that kernel version with gcc 4.x.

Thank you.
Finally I have my DWL-G510 wifi card working properly (WPAPSK-TKIP) with native Dapper RT61 driver. I didn't use the new RT61 v1.1 driver. I got it, but at end I used the one shipped with Dapper. What I did:
1) downloaded drivers and firmware from ralink website as described above in other posts.
2) created /etc/Wireless/RT61STA/.
3) copied firmware files (*.bin) and rt61sta.dat to this folder.
4) edited rt61sta.dat with vi, accordingly to readme file included in drivers package, adjusting to my own settings (WPAPSK, TKIP, keys, channel and SSID).
5) edited /etc/network/interfaces, commenting all references to wlan, ath interfaces (which refers to others wifi networks). I've added the following commands at end of file:
[INDENT][/INDENT]auto ra0
[INDENT][/INDENT]iface ra0 inet dhcp
6) rebooted
7) verified with ifconfig: I got IP from access point
8) verified with iwconfig: ssid, wpa, etc were all ok (loaded from rt61sta.dat)
Note: I couldn't make Gnome Network-Manager to work with wifi. I think it's because of wpapsk setting. But I'll not cry for this...

Hope this help others. There's some light at end of tunnel...

---

### Post by cirorodrigues on 2006-12-26
After posting I saw an formatting error. On item 5, the lines added to the file were:
auto ra0
iface ra0 inet dhcp

---

### Post by Jeremiah Griffin on 2007-01-01
I have been searching the Internet for help on installing the Zonet ZEW1602 card on Ubuntu for about three months. The only things that came back were questions about how to do it. The ZEW1602 is the only solution I have for connecting to the Internet. I can't use a LAN cable to my router because it's on the other end of the house. My TRENDnet USB connector broke somehow, so that's not an option. Neither this guide or NdisWrapper have helped. Can someone **please** help me get this wireless card to work? ](*,)

---

### Post by csparks1982 on 2007-01-01
I have finally got mine up and running.

Here is some pointers for people looking.

Running 6.1 is a big hassle, besides the wireless issues I encountered, I noticed a few other things as well.

So if you are running 6.1, I would recommend downgrading to 6.06, I did and I had my internet working within a few minutes.

---

### Post by Oldbones on 2007-01-03
> **Henry Rayker said:**
> I get to the part about the rt61.ko copy and everything just falls apart. I get an error "No such file or directory" referring to rt61.ko...could there be anything that was omitted?

howdy, I hit a n00b wall here too!  If your like me, you got stumped on the 

sudo cp rt61.ko /lib/modules/'uname -r'/kernel/drivers/net/.

really, the 'uname -r' is can be spotted by browsing through your folders up through the /lib directory.  My 'uname' started with a "2" 

once I figured that out.  the rest was easy.:KS

---

### Post by Nordicnurse on 2007-01-03
I managed to get Ralink working on 6.10 fairly easily, thanks to Judgekaster's excellent howto. I was having some problems with dhcp, but careful edit of rt61sta.dat helped - so I advice anyone having problems to look there again... :D 
Luck to those still having problems

---

### Post by giacco on 2007-01-03
Hello, I followed this guide but I have a noob doubt. Once installed the driver I entered ```
 lspci
``` I still get ```
00:0c.0 Network controller: RaLink Unknown device 0302

```
Is that normal or there is something missing?
I followed all the steps in this guide. Doing iwconfig I get ra0 and all the information about the wireless card that is a MSI MP54G5 (chipset RT2561T).
```
ra0       RT61 Wireless  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
monitor mode and the other things work ok. Was my installation right?. what do you get doing lspci?thank you.

---

### Post by PeterHoward on 2007-01-06
Thanks for a great resource - it has worked a treat for me with Ubuntu 6.06 (Dapper Drake), on a Dell with Pentium D820, and Belkin F5D7000 PCI 802.11g card (RaLink RT61 chipset).

I have one suggestion: I was temporarily confused when you referred to the readme to explain the rt61sta.dat configuration file. I couldn't figure out at first which readme you were referring to. If found it by experiment by downloading the driver and finding it among the contents, but of course if you follow the route explained for Ubuntu 6.06 - you do not normally  download the driver. It seems the obvious place to look in hindsight - but confused me at the time!

In answer to the person who asked if this worked on 64-bit platforms - Yes.

---

### Post by dilaudid on 2007-01-10
Hi, I was having terrible problems on stage "(e) check if the driver was loaded" - when I ran iwconfig I could not see ra0 - just wmaster0 and wlan0. Then when I tried dhclient ra0 I would get the following:
```
rs0: ERROR while getting interface flags: No such device
```
The solution to this, after 1 hour ](*,)  was to finish steps f-h and reboot. Then everything was found fine. Thanks for the tips Judgekaster and everyone.

---

### Post by i386DX on 2007-01-15
//edit: never mind...

---

### Post by galorin on 2007-01-15
Good guide, just got my laptop working with it at home.  I've got a problem though, as I also use the laptop at College, where they have their own open auth wireless network, with varying SID's around campus (need to go through a logged proxy server though)

iwlist tells me that there are no wireless extensions, but I can get SSID from iwpriv ra0 get_site_survey, but is there some way of automatically connecting to a network with this chip?

---

### Post by neilford on 2007-01-15
I am a newbie, here. I have followed this thread and things are not quite working:

1) When I ran "make all" I got a number of warnings
ie: mlme.c:5893 warning: 'R66' may be used uninitialized in this function. Is this normal?

2) I edited rt61sta.dat in vi with a -b, but when I run "file" on it, it comes up as a text file.
Is this okay?

3) iwconfig yields: ra0  no wireless extensions

4) lspci identifies the card and the RT61 chipset

I have done everything with, apparently, no change .

neilford

---

### Post by galorin on 2007-01-15
In reply, 

1) yes this is normal for compiling software, just stuff that developers might need, nothing we need to worry about.

2)  that should be fine, didn't notice that when I edited it, but vi -b $FILENAME should do the trick.

3) this is normal as far as I can tell, until after the interface is up and connected.  iwlist doesn't work on my system.

What specifically isn't happening?

---

### Post by neilford on 2007-01-15
I was assuming when I ran iwconfig that I would see something I haven't seen before regarding ra0. Should I be seeing no wireless extensions for ra0? Thanks.

neilford

> **galorin said:**
> In reply, 

1) yes this is normal for compiling software, just stuff that developers might need, nothing we need to worry about.

2)  that should be fine, didn't notice that when I edited it, but vi -b $FILENAME should do the trick.

3) this is normal as far as I can tell, until after the interface is up and connected.  iwlist doesn't work on my system.

What specifically isn't happening?

---

### Post by neilford on 2007-01-15
Okay. I am very close. The only issue I can see at the moment is I cannot seem to connect to a network. I assigned my default essid in the rt61sta.dat file. It didn' take. When I run iwconfig I see ESSID:"". When I run iwlist ra0 scanning, I see all the networks around me including my own. I tried assigning the network using
sudo iwconfig ra0 essid my-network, but no go. 

I ran dmesg and got: 

    ra0: no IPV6 routers present
    ra0  (WE) : Driver using old /proc/net/wireless support, please fix driver !
What is wrong here? Thanks.

neilford

---

### Post by gbpacker on 2007-01-17
Hello,

I tried following the instructions on my AMD 64 bit machine.  I am running drapper 6.06 version. 

But my system is stuck while rebooting. It says:

Bringing up ra0
Internet Systems Consortium DHCP client V3.0.3
interface inet 0 upnt-script: line 155: 3716 killed ifconfig $interface int 0 up

And it hangs here. 

Can anyone pls suggest how to revert back the changes or how do I bypass this step?

Thanks

---

### Post by IrregularShed on 2007-01-19
Well, I'd just like to say thanks for this guide - it's proved invaluable for me. It's taken me an hour and a half to get a box to connect to our WLAN and most of that has been fighting a flaky DHCP server.

Thanks!

---

### Post by aequanimus on 2007-01-21
> **reler said:**
> Finally seem to have got it to work with WPA and am using it to make this post ! How ?

Was able to get my router to recognise the MAC address of the adapter and to always assign it a fixed IP address (forgot to say before that I was trying to get a dynamic address using dhclient).

Even then, I wasn't not convinced that the .dat file parameters are being picked up. I manually entered all of these commands: 
   sudo iwpriv ra0 set SSID=<my SSID>
   sudo iwpriv ra0 set AuthMode=WPAPSK
   sudo iwpriv ra0 set EncrypType=AES
   sudo iwpriv ra0 set WPAPSK=<my key>
Then it worked ! :D 

Many thanks to all those who wrote in this thread (and others) and which left clues.

All I need to do now is to make sure it survives a boot and then get FTP, Apache, MySQL & PHP working ! Wish me luck.

Reler

Thanks for the post reler, I was close to giving up but your commands got it working! Thanks to judgekaster for the excellent guide. =D>

---

### Post by lukew on 2007-01-22
Hi,

Just wanted to say thanks for this Howto; worked a treat!!!

Only a couple of points I wanted to make for other people with frezzing problems.

My WPA Key had to be hex and not ascii; this was locking my computer up eery time!!
MY computer was locking up the firs time I:

```
sudo dhclient ra0
```

I commented out eth0 from:

[HTML]/etc/network/interfaces  [/HTML]

And not everything works great.

judgekaster  thank you!!!

---

### Post by blazercist on 2007-02-01
Ok, Ive got the rt61 on my MSI-1039 and I've followed the instructions exactly, only I have two problems.  This laptop has a hard button to turn the wifi/bluetooth on/off, if the wifi is not turned on at boot time I cannot turn it on afterwards and access the internet via wifi, iwconfig shows a blank ESSID, and sudo iwpriv ra0 set ssid does not work.

Also, if the wifi is on at boot time and everything goes well I can use the internet via wifi, however after just a minute or two the whole laptop freezes dead in its tracks, no error messages, just freezes and I cannot move my mouse or do anything, I have to hard restart to get it back.

Any idea what could be wrong?

BTW I'm using OPEN WEP with an ASCII KEY, *** I HAVE TRIED USING HEX KEY, I get the same problems*** also dhclient sends to 255.255.255.255, my subnet is 255.255.255.0 is it supposed to be like that?

The above post says to comment out eth0 from /etc/network/interfaces but won't that render my wired connection useless in the case that I want to connect physically?

---

### Post by liambre on 2007-02-04
I have a slight problem here, the ralink link to download the driver is broken. If anyone could send or re-direct me to a new one, I would be more than greatful.

[http://www.ralinktech.com/drivers/Linux/2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz](http://www.ralinktech.com/drivers/Linux/2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz)

---

### Post by Dr. Drone on 2007-02-04
> **liambre said:**
> I have a slight problem here, the ralink link to download the driver is broken. If anyone could send or re-direct me to a new one, I would be more than greatful.

[http://www.ralinktech.com/drivers/Linux/2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz](http://www.ralinktech.com/drivers/Linux/2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz)

Yeah, I really need those Drivers.

---

### Post by Dr. Drone on 2007-02-04
YAY!

I FOUND THEM! =D

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

:]

---

### Post by Botany Bay on 2007-02-10
judgekaster (and phq) please accept my heartfelt thanks for helping me get my wifi card working. Your how-to proved invaluable. It's taken me a couple of weeks to to do it but finally - success!

I'm not a programmer or anything but I've been meaning to try Linux for years so when I bought an old Dell P3 laptop off eBay it was the perfect opportunity when it proved difficult to install XP without the right propriety Dell set-up discs. 

Ubuntu Edgy installed like a treat and after a little bit of faffing about trying to get the laptop monitor to work (Xfree86 – I thank you) it was an absolutely great introduction to Linux. Except for the wifi support. Now solved and I've learnt a bit about Linux on the way. 

I'm aware I sound like an *** but I'm still stunned its actually working!

---

### Post by booljayj on 2007-02-11
I followed the step-by-step instructions and successfully enabled my rt61 shared WEP connection. However, the next day after I installed it, edgy seems to have no idea that the device ra0 ever existed. I used automatix2 to install firestarter and clamav, then uninstalled clamav because I thought I didn't need it. However, when I started up firestarter it recognized the eth0 connection I am using now and a new connection called sit0 (totally inactive). ra0 is nowhere to be found. All of the changes that I made when installing the new rt61 driver are still there, but the device is no longer present. What would cause this, and how do I fix it?

---

### Post by judgekaster on 2007-02-14
> **booljayj said:**
> ... However, when I started up firestarter it recognized the eth0 connection I am using now and a new connection called sit0 (totally inactive). ra0 is nowhere to be found. All of the changes that I made when installing the new rt61 driver are still there, but the device is no longer present. What would cause this, and how do I fix it?

My guess is that firestarter and clamav have nothing to do with your problem.

Can you open a terminal and see whether the rt61 driver was loaded, by doing the ff:

```

sudo lsmod | grep rt61

```

If nothing comes up, that means your rt61 driver was not loaded. Then you can try:

```

sudo modprobe rt61

```

That should load it. If an error comes up saying that the module was not found, you probably forgot to copy your the rt61.ko module to the /lib/modules/`uname -r`/net directory.

---

### Post by a2c39a on 2007-02-22
Hi Folks,

Thanks for this thread. I have followed it and now have a working wireless internet connection via the Ralink Mini PCI card in my Medion MD96400 laptop.

In addition to the 'Mini How To' I needed to disable the 'ra61pci' driver that exists in Ubuntu 6.10 before it would work.

I also suffered the loss of wireless connection once I had carried out the (135) on-line updates.
I just needed to copy 'rt61.ko to /lib/modules/2.6.17-11-generic/kernel/drivers/net
and kill 'rt61pci.ko' in /lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless/rt2x00
also copy back the 'DHCP' script and symbolic link, to get it working again.

However, I have a problem!

When I am at home and my wireless network is present, all works fine.

When I am at work and no wireless network is present, then booting Ubuntu starts fine but then reaches a point where it hangs (presumably it is trying to establish the wireless connection - unsuccessfully) for about 2 minutes!! It is easily possible to think the machine has locked at this point but if you are patient, then booting eventually continues (with no prompting) and brings up the log-in screen as normal. Once logged in the ra0 icons on the top bar show zero signal and a small orange block at the bottom of the pillar icon (which is full height green at home of course) as would be expected.

Is there any way to enable automatic connection when at home (which works fine at present) but without the horribly long boot delay, when away from home with no wireless network?

Many thanks in advance for your help, John.

---

### Post by machi on 2007-02-27
Thank you very much about the step-by-step how-to, I have my RT61 card up and running great in my laptop now.

Just have an little question here.
After updated the .dat file, I found out there is only 1 SSID line. What if I would like to setup 2 SSID? would that works if I add another line with SSID=2nd-ssid and Key2Str=2nd-key-for-the 2nd-ssid? Anything that I can do to make my laptop to, automatically, pick up my home wireless network when I am at home, and pick up my school's wireless network when I am in school?](*,) ](*,) ](*,) 

Thanks

machi

---

### Post by machi on 2007-02-27
> **a2c39a said:**
> 

When I am at work and no wireless network is present, then booting Ubuntu starts fine but then reaches a point where it hangs (presumably it is trying to establish the wireless connection - unsuccessfully) for about 2 minutes!! It is easily possible to think the machine has locked at this point but if you are patient, then booting eventually continues (with no prompting) and brings up the log-in screen as normal. Once logged in the ra0 icons on the top bar show zero signal and a small orange block at the bottom of the pillar icon (which is full height green at home of course) as would be expected.

Is there any way to enable automatic connection when at home (which works fine at present) but without the horribly long boot delay, when away from home with no wireless network?

Many thanks in advance for your help, John.

Hi John,

I have that experience too, when the machine booting up, and when it is trying to looks for the wireless network, but can't find it, then the GUI is gone, and the CLI comes, and somelines looks like 255.255.255.0 something for a multiple times, right?

what I do is when I know I am not in my pre-set wireless network range, I will pull the PC-card out, then the boot up process probably will bypass the wireless configuration process. when I forgot to pull the PC-card out. I will hit Ctrl+D to stop that 255.255.255.0 searching CLI and go on to the boot up step. At least, it won't hang your machine.

Hope this can help you to solve your problem.

machi

---

### Post by omegahelix on 2007-02-28
Could someone who has the RT61 card working with WPA-PSK please post their rt61sta.dat file?  If I have my file in the /etc/Wireless/RT61STA directory then my system hangs when I try to bring up the interface with ifconfig.  If I remove the file it comes up but is not configured to connect to my router.  I edited the file using vim -b.  Maybe I have the wrong stuff entered in the file (see it here: [http://www.ubuntuforums.org/showpost.php?p=2212242&postcount=239]("http://www.ubuntuforums.org/showpost.php?p=2212242&postcount=239"))?  I have not yet tried dos2unix on the file.  Thanks for your help.  This is so annoying!

---

### Post by brodiepearce on 2007-03-02
[QUOTE=judgekaster]
(f) connect to the network

to set a static IP address, do:

```

$ sudo ifconfig ra0 {IP ADDRESS} up

```
[/QUOTE]

Should the brackets be removed?  I can't tell because either way my system is still hanging on the interface configuration. Also:

[QUOTE=judgekaster](a) *Do not* use the "Networking" tool (network-admin). You will get a lock-up at boot time at the point where the network interfaces are bieng configured. If you have used the Networking tool, you will have to comment out the entries in the file "/etc/network/interfaces." to do this:

```

$ sudo vi /etc/network/interfaces   # replace vi with your editor of choice (nano, gedit, kate etc.)

```

it should look like this:

```

auto lo
iface lo inet loopback

#iface ra0 inet dhcp
#wireless-essid xxxx
#auto ra0

```
[/QUOTE]

Does this mean that even if we have a static IP configured in the script file we should still leave the /etc/network/interfaces file as DHCP?

---

### Post by judgekaster on 2007-03-03
In my experience, it is best to comment out the lines in /etc/network/interfaces pertaining to the ra0 interface. Instead just place the following line in the rt61up script:

```

# set static address
# replace 10.10.10.5 with your ip address
ifconfig ra0 10.10.10.5 up

```

instead of

```

# get ip address from dhcp server
dhclient ra0

```

cheers!

---

### Post by brodiepearce on 2007-03-03
Thanks man I'll give it a try, I think I'm close to getting this to work.

*edit* OK I set the static IP in the rt61up script, and commented out all ra0 references in /etc/interfaces/network, as a consequence Ubuntu actually does boot properly now (every method I've tried up till now have resulted in it hanging at 'Configuring Network Interfaces', so to get this far by it self is extremely pleasing).  

However, the wireless does not connect automatically with the script, and I can't even get it to connect using the network manager through Administration.  :(  I have also reserved the static IP with my router using the MAC address as it generally doesn't like having static IPs forced on it, I think perhaps I should set DHCP on my PC and just have the router dish the static IP out as I *THINK* that's how I ended up doing it with Windows.

---

### Post by brodiepearce on 2007-03-03
I tried doing DHCP with reharpernc's [method]("http://ubuntuforums.org/showpost.php?p=1310334&postcount=117") and I still don't receive any DHCP offers.

I have this entered in the rt61up script:
```

#!/bin/sh
echo "Bringing up ra0"
# obtain an IP address from a DHCP server
sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=OPEN
sudo iwpriv ra0 set EncrypType=NONE
sudo iwpriv ra0 set SSID=MY_SSID
dhclient ra0

# alternately, you can uncomment the following line to set a static IP address
# ifconfig ra0 {IP ADDRESS} up
# if you uncomment the line above, make sure to comment line #4

```

I also have the following set in my rt61sta.dat file:
```


[[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=4
SSID=MY_SSID
NetworkType=Infra
Channel=11
AuthMode=OPEN
EncrypType=NONE
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
#WPAPSK=abcdefghijklmnopqrstuvwxyz
TxBurst=0
PktAggregate=0
TurboRate=0
WmmCapable=0
AckPolicy1=0
AckPolicy2=0
AckPolicy3=0
AckPolicy4=0
BGProtection=0
ShortSlot=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
PSMode=CAM
TxPreamble=0

```

Due to all the *sudo iwpriv ra0 set ... * commands in the rt61up script, I also get this error (presumably when Ubuntu attempts to run the script):
```

Interface doesn't accept private ioctl... set (8BE2): Network is down.

```

:(

---

### Post by steffen on 2007-03-04
I haven't been able to get this to work properly on Edgy. I'm able to connect to the network (I can remote-desktop and SSH into the computer), but I'm not able to connect the same box to the internet. Don't know why that is.

Can anyone report whether this driver is working properly under the latest Feisty herd?

---

### Post by akjerryo on 2007-03-15
Thank you so much for posting this how to, i have tried many different things to get my wireless working, and this worked on Edgy... You are a life saver :)

---

### Post by jtwyrrpirate on 2007-03-18
Hey just a point of information for everybody, do like the howto says and don't edit the rt61sta.dat using gedit! Definitely use vi -b and you will save yourself at least several hours of "what am I doing wrong, I'm sure all the settings are right!" (not that I would know from experience or anything) :lolflag:

---

### Post by skot on 2007-03-19
does anyone have a new link for the "2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz" file.

the address list in the first post is not working.  then when searching google the only hits were to this site haha.  any help would be great.   or if someone could just attach it to there post that would be good too.

thanks
skot

---

### Post by viergeame on 2007-03-25
I, also, am having problems finding a place to download this driver.  I poked around on google and everything brought me back to here.

---

### Post by huygens on 2007-03-26
> **viergeame said:**
> I, also, am having problems finding a place to download this driver.  I poked around on google and everything brought me back to here.

Just use Google and type "ralink" :-)
For the first link, it gives you some alternatives like [the Linux link for ralink support]("http://www.ralinktech.com/ralink/Home/Support/Linux.html").
Anyway the direct link for the latest driver as of today is: [http://www.ralinktech.com.tw/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz](http://www.ralinktech.com.tw/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz)

But you should always check the [Ralink Linux support link]("http://www.ralinktech.com/ralink/Home/Support/Linux.html").

PS: RT61 seems to be "renamed" RT2501...

---

### Post by echo15 on 2007-03-27
Hi!
I'm new to linux and followed the instructions from page 1 to get my Edimax card to work.  It works great when using DHCP but I can't seem to connect to the internet when I try to use static IP.
When I use static, i can ping my router/modem, but i can't ping any internet site.  What could be wrong?
Any help would be greatly appreciated!
Thanks!

---

### Post by huygens on 2007-03-28
> **echo15 said:**
> [...] I can't seem to connect to the internet when I try to use static IP. When I use static, i can ping my router/modem, but i can't ping any internet site. [...]

Just a suggestion, but did you set up your modem router as the gateway to the internet? That could be the problem.
Just to be sure about this, you could try the following command. You need to go in the Applications menu, under Accessories you have an item called Terminal, just click it. You should now see a new window, that is what people refer to as the command line, terminal or console.
Just type in the following command:
```
route
```Could you post the result here?

---

### Post by tictacman on 2007-03-29
Thanks to judgekaster.  I've been wondering I've been getting alot of lock ups at boot time with rt61.  Now I know :) Cheers

---

### Post by echo15 on 2007-03-29
> **huygens said:**
> Just a suggestion, but did you set up your modem router as the gateway to the internet? That could be the problem.
Just to be sure about this, you could try the following command. You need to go in the Applications menu, under Accessories you have an item called Terminal, just click it. You should now see a new window, that is what people refer to as the command line, terminal or console.
Just type in the following command:
```
route
```Could you post the result here?

Hi, Huygens.

sorry, i can't post the exact output as i'm at work.  But it gave the gateway as 192.168.1.0 which is not the ip of my router/modem. I did a "route add default gw" and that solved that. Do I need to add the route everytime i boot up? or is this automatically "remembered"?

Thanks!

---

### Post by rukus on 2007-03-29
erm.. first post here, been trying all sorts with my edimax EW7108PCg to no avail, then installed feisty fawn (7.04 beta) and the card popped into life with a link to my(currently - for testing) unencrypted network.  This is the best result I'd had, and all out of the box from the livecd.  

So now, on to a fresh disk install and try to get the encryption working.  

Just thought I'd let everyone know, it's looking good so far :-)

Cheers
Ruk

---

### Post by huygens on 2007-03-30
> **echo15 said:**
> sorry, i can't post the exact output as i'm at work.  But it gave the gateway as 192.168.1.0 which is not the ip of my router/modem. I did a "route add default gw" and that solved that. Do I need to add the route everytime i boot up? or is this automatically "remembered"?

OK, so no need to post the output. That is good news :)
When you use the route add thing, it is just for the current session and will be lost after next reboot.
How did you configure your static IP address? Did you modify the /etc/network/interfaces to do so? Or another file?
If you have modified and set-up the static IP address in the /etc/network/interfaces file, you could follow the example given here: [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=show&redirect=Rt61WirelessCardsHowTo#head-55e88e8e2391e6620307aa0e2e4574a9d1ccf94f](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=show&redirect=Rt61WirelessCardsHowTo#head-55e88e8e2391e6620307aa0e2e4574a9d1ccf94f)
Simply edit the file I just mentioned and apply the example of static IP configuration given in the above link to your own settings. After you have modified this file just type this to restart your network without rebooting:
```
sudo ifdown ra0 && sudo ifup ra0
```In case, you have used another way to set-up your static IP address, could you give more information so we could find out how to help you defining your gateway?

---

### Post by Arko on 2007-04-01
After hours of trying, finally I got my DWL-G510 card working. I have tried everything I found on tutorials and forums and did the following script that I put in /etc/init.d directory to start on boot (Ubuntu 7.04):

```

#!/bin/bash
ifconfig ra0 192.168.0.128 up
route add default gw 192.168.0.1 ra0
route del default
ifconfig ra0 down
ifconfig ra0 192.168.0.128 up
iwconfig ra0 mode managed
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=TKIP
iwconfig ra0 essid MYHOME
iwpriv ra0 set WPAPSK=d23fd94e6c344514adce7549591dc7b265426e793aabb13b767b06958c9c7b1c
iwconfig ra0 essid MYHOME
ifconfig ra0 192.168.0.128 up
route add default gw 192.168.0.1 ra0

```

But there is still a problem: about 50% of boots I do not get Internet working. Then I have to run "route del default gw; ifconfig ra0 down; ifconfig ra0 192.168.0.128 up; route add default gw 192.168.0.1 ra0" as root to get it working again. Eventually I have to type that three or four times, which is very annoying.

Please, any help for that?

---

### Post by tictacman on 2007-04-03
Arko, I experienced a very similar problem when I tried to get the card working with wpa_supplicant, I created a startup script to shutdown the card bring it up, etc and even then it only worked some of the time. 

More recently i tried the card with a new motherboard which had a via chipset and found that irq problems were causing the card to shut down when the system loaded the via graphics driver.  Try selecting recovery mode in the grub menu and seeing if the card will connect before making any changes.

---

### Post by rwnz on 2007-04-06
I´m having trouble getting my wireless card working despite spending hours looking through forums, though it doesn´t help that I´m very new to Linux so don´t know what even the basic commands are. Can you please help – I expect that I´ve missed something simple somewhere so my apologies if you need to state the obvious!

PC: Toshiba Satellite 1800 Notebook
	PIII 850MHz
	256MB RAM
Installion OS file: Xubuntu 6.10-alternate-i386.iso
Wireless card: D-Link DWL-G650+A
	H/w ver.: E1
	F/w ver.: 5.00

By typing ¨lspci¨ into the terminal I obtained the line reading ¨Network Controller: RaLink Unknown Device 0302¨. From looking at forums etc I understand that the chipset is RaLink and not some others I´ve seen mention of such as Texas or Prism which look to be for previous hardware versions of the DWL-G650+.

Searching for info on the RaLink got me to this forum, and I followed page 1 steps a to d (except that I downloaded the driver curently at [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) which is RT61_Linux_STA_Drv1.1.0.0.tar.gz) and in step (d) I found that ¨vi -b¨ would display but not allow me to edit the file, but ¨nano -w¨ edits it fine.

My huge problem is the next step (e). 
(e) copy the rt61.ko driver file to the modules directory then load it
Code:
$ sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/.
$ sudo depmod
$ sudo modprobe rt61

¨$ sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/.¨ tells me there is no rt61.ko. Looking through the forum I understand that this file is not standard with 6.10. and isn´t included in the downloaded driver files. However somewhere I read that installing linux headers (whatever that means) would make this file available so I ran ¨sudo apt-get install linux-headers-`uname -r`¨. When I later ran it again it confirmed that all headers are present:
rsudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 104 not upgraded.

However $ sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/ still gives the result that rt61.ko does not exist.

Thus is a summary of what I´ve done, though I´ve actually tried lots of things and have got quite confused so this may not be 100% accurate. The card seems to be recognised in some regard as when I type the command ¨sudo iwlist scanning¨ I get the result:
wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:99:27:14
                    ESSID:"Walkers Wireless"
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:13/94  Signal level:-62 dBm  Noise level:-154 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202

I don know if the signal levels are good or bad, but the channel is the same as my router and changes if I change the router setting. My guess is that the card is working but not talking to the networking part of the OS as rt61.ko is the missing interface. 

I´ve seen a few questions in this thread asking about the missing rt61.ko but found no answers that solve it for me, so please advise how I install rt61.ko
:confused:

---

### Post by IanW on 2007-04-06
Did you run the 
```
sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/ 
```
command from WITHIN the untarred driver folder containing that file?

---

### Post by rwnz on 2007-04-06
Thanks IanW. My problem was that I could not find rt61.ko in any directory so that I could go there to perform the cp and I could find nothing to explain where it should be or how it gets there. However, I´ve gone through the process again, also looking at the ReadMe that is in the downloaded tar.gz file and it looks like my first attempt at Makefile.6 ./Makefile didn´t work because now rt61.ko is present in the untarred folder whereas it wasn´t after I´d downloaded it, which means that the Makefile process generates it.
...... So now on to the next step.

---

### Post by peterhs on 2007-04-08
Everything worked fine except for when I rebooted my laptop, specs at end.  After the reboot, the connection shutdown and gave me nothing except a complete shutdown of all services, and an error of:

BUG: soft lockup detected on CPU#0!

That error kept driving me crazy because i could not determine why my system was randomly crashing on me.  The keyboard was locking up and nothing was happening.  I installed Ubuntu 6.10 amd 64, and the same problem came up except earlier, immedietly after loading the rt61 module.  

steps taken:

followed guide up until before the modprobe rt61 step, before i loaded the rt61 module, i rmmod rt61pci

i then loaded the rt61 mod and got the error of a soft lockup on CPU#0

wireless cards bcm4311 & edimax 7608pg MIMO (rt61 chipset) both cards work with windows, but neither with any distro of linux, frustrating!!!
amd turion 64 x2 TL50
2Gb ram
dvd-rw

dmesg log file:

[  507.076577] Unloading module: rt61pci - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[  507.257700] ACPI: PCI interrupt for device 0000:09:00.0 disabled
[  511.020307] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 20 (level, low) -> IRQ 185
[  511.020315] rt61 1.1.0 CVS CVS [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[  511.020528] RT61: Vendor = 0x1814, Product = 0x0401 
[  525.229138] RT61: RfIcType= 4
[  530.490816] ra0: no IPv6 routers present
[  533.461414] BUG: soft lockup detected on CPU#0!
[  533.461421] 
[  533.461422] Call Trace: <IRQ> <ffffffff802b5faa>{softlockup_tick+250}
[  533.461456]        <ffffffff80299d47>{update_process_times+87} <ffffffff8027d563>{smp_local_timer_interrupt+35}
[  533.461473]        <ffffffff8027dcd1>{smp_apic_timer_interrupt+65} <ffffffff8026634e>{apic_timer_interrupt+98}
[  533.461488]        <ffffffff884babf0>{:rt61:MlmeAuthReqAction+0} <ffffffff80242604>{lock_timer_base+36}
[  533.461532]        <ffffffff80242609>{lock_timer_base+41} <ffffffff80250c98>{try_to_del_timer_sync+24}
[  533.461546]        <ffffffff802643b4>{del_timer_sync+4} <ffffffff802643bc>{del_timer_sync+12}
[  533.461561]        <ffffffff884bac8c>{:rt61:MlmeAuthReqAction+156} <ffffffff884afa37>{:rt61:MlmeEnqueue+247}
[  533.461616]        <ffffffff884b15f7>{:rt61:MlmeHandler+263} <ffffffff884ba620>{:rt61:AuthTimeout+0}
[  533.461661]        <ffffffff80299668>{run_timer_softirq+344} <ffffffff8021195f>{__do_softirq+95}
[  533.461681]        <ffffffff802669aa>{call_softirq+30} <ffffffff802733ec>{do_softirq+44}
[  533.461693]        <ffffffff80271f00>{default_idle+0} <ffffffff8026634e>{apic_timer_interrupt+98} <EOI>
[  533.461712]        <ffffffff80213270>{tcp_poll+0} <ffffffff80271f29>{default_idle+41}
[  533.461733]        <ffffffff8024ecfe>{cpu_idle+158} <ffffffff8060885b>{start_kernel+523}
[  533.461750]        <ffffffff80608293>{_sinittext+659}


if this matters at all, i get no sound

ps, i have spent ~50+ hrs trying to get linux on my laptop, trying different distros and debugging these two wireless cards, i bought the Edimax one because it is compatible with linux out of the box ;)

---

### Post by tictacman on 2007-04-08
> i bought the Edimax one because it is compatible with linux out of the box

peterhs  - welcome to the wonderful world of edimax, hours of fun for the linux hobbiest:) .
I have an edimax card as well, the claim that its compatible with linux is a bit funny considering the time people spend trying to get it working.  Like you I lost a whole weekend trying to get it work.  I also experienced the scary soft lockups you talkied about, in fact I had so many problems I was convinced it was a mobo problem and went out and bought a new board and chip (I am convinced now there's nothing wrong with the original board).

I read in one post that softlocks are due to using /etc/interface to control the card.  I have blanked out all references to ra0 in that file and use a script to boot the card.  Since I done that I haven't had any problems

Do you have via chipset on your board?  I found that the board was turning the card off after the via graphics driver loaded.  I only noticed it when I booted into recovery mode and found my card had loaded perfectly, but failed to work in normal  mode.

If so you might want to have a look at some of my other posts, just click on my name at the top of the post host header and select view other posts.  I think I wrote a large post on a different rt61 thread on Monday where I outlined all the steps I took to get the card working for me.

---

### Post by peterhs on 2007-04-08
> **tictacman said:**
> 
I read in one post that softlocks are due to using /etc/interface to control the card.  I have blanked out all references to ra0 in that file and use a script to boot the card.  Since I done that I haven't had any problems

Do you have via chipset on your board?  I found that the board was turning the card off after the via graphics driver loaded.  I only noticed it when I booted into recovery mode and found my card had loaded perfectly, but failed to work in normal  mode.

If so you might want to have a look at some of my other posts, just click on my name at the top of the post host header and select view other posts.  I think I wrote a large post on a different rt61 thread on Monday where I outlined all the steps I took to get the card working for me.

Thanks for the help, but i still get these lockups whenever i boot with the card already inside the laptop or insert the card into the laptop when it is running.  I tried all of your methods and i could not succeed. No via chipset, and commenting out the ra0 in /etc/network/interfaces did not help because network manager kept writing a new ra0 block of script after I commented the ra0 out.  It writes a new script after I try ifdown ra0, ifup ra0, ... newscript written, any suggestions about that?

This is so frustrating because it works after the initial steps, I reboot and it crashes on me.  

Now to rant: I am going to try some other distro next weekend to try to get a stable wireless connection.  If all else fails, I will stop trying and try again in about six months, it is kind of like a semi-annual ritual, i try to switch to linux, burn about 10 cd's and 3 dvd's cannot get it to work, ask for help and then use windows for about 6 months and repeat.  I kind of think my laptop hates every other OS besides Windows.  It has become a: its not you, it is me relationship with my laptop and linux.  I just wish my connection was a hard-wire one, because my laptop worked when attached to my router, but not wirelessly.

---

### Post by tictacman on 2007-04-08
Sorry to hear that your not having much luck with the card, I'm not sure why /etc/interface is being re-written. Have you being using the network manager utility to try and configure the card?  How about reinstalling and reconfiguring the driver from scratch.  I did this a couple of times with different drivers until I hit upon a method that worked for me.  Also, if you havent already, you might try reading through the other rt61 thread created by phq [http://ubuntuforums.org/showthread.php?t=296822]("http://ubuntuforums.org/showthread.php?t=296822") 

I also did a bit of googling for you on the cpu softlock and found a bug report that might be worth a look:  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63418]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63418")


Yeah I know what you mean about having a tough time ubuntu/linux and going back to windows.  I used to do that about once a year for the past 6 years and until I was finally able to get everything working to my satisfaction.

Best of luck.

---

### Post by darkwill on 2007-04-12
Thank You SOOOOOOOOOOOOO Much!!!!!!!! I've been trying for days on end to get a network setup and thanks to this (knock on wood) it finally works!!!!!!!!

(I know I over used the ! but you have NO IDEA how frustrating this has been,.... well .. maybe you do :p)


Thanks again
Will

---

### Post by jskulski on 2007-04-13
I have a Gigabyte GN-WP01GS and am having some trouble getting it to work. I have a fresh install of ubuntu 6.10. 

The driver is loaded ok, (lspci recognizes it) and there are a wlan0 device and wmaster0 device.

I installed the firmware and the *binary* rt61sta.dat file in /etc/Wireless/RT61STA as suggested. dhclient wlan0 gives me No DHCPOFFERS received. 

iwpriv is a little different than what is mentioned in the howto:

it seems to want something like

iwpriv wlan0 param NetworkType Infra 

but when i enter that it tells me that the interface does not accept private ioctl.

Any ideas on where to go? Any diagnostics to check? Thanks!

---

### Post by steffen on 2007-04-15
After having struggled with getting this card up on my Ubuntu desktop, here's what I did:

1) I ****** up my computer so I had to reinstall the OS.

2) I installed Ubuntu 6.10, but immediately dist-upgraded (as of 13 April 2007) to Feisty (7.04).

3) I opened System | Networks and de-activated Nomad Mode on my ra0 card. My WEP 64 encrypted network was available from the drop-down, and I inserted my HEX code.

4) I chose DHCP.

Result: Card works great! :)

---

### Post by blazercist on 2007-04-17
Oh steffen, that would be great if feisty actually booted with network-manager installed... I cannot get it to boot with network-manager installed at all.

---

### Post by huygens on 2007-04-17
> **blazercist said:**
> Oh steffen, that would be great if feisty actually booted with network-manager installed... I cannot get it to boot with network-manager installed at all.

On Feisty, the network card driver is correctly installed and working :-) then network manager is also up and running after the installation of Feisty. However, it works only if your network is unencrypted or uses WEP encryption. If it uses WPA or WPA2 encryption, network manager in combination with rt2x00 (the RT61 driver) will not work.

---

### Post by steffen on 2007-04-20
> **huygens said:**
> On Feisty, the network card driver is correctly installed and working :-) then network manager is also up and running after the installation of Feisty. However, it works only if your network is unencrypted or uses WEP encryption. If it uses WPA or WPA2 encryption, network manager in combination with rt2x00 (the RT61 driver) will not work.

I must admit, I'm using WEP, not WPA. So don't get your hopes up :(

However, I wasn't able to get it working automagically with Edgy - so the world's moving forward :)

---

### Post by biker_bits on 2007-04-21
WEP key entry format of XXXX-XXXX-XX i.e the need to insert '-'  after each group of 4 characters -- does it still apply in Fiesty? 
My Gigabyte PCI (Ralink based) card seems to be recognised OK by 7.04 (so drivers are loaded by Fiesty upon installation I assume), but upon entry of network ESSID and WEP Hex key does not do a lot at all. No ACT or LINK lights on at any time. Router is set up for WEP and DHCP. My laptop (running 6.10) configured fineon the network.
Any ideas for what to check?

---

### Post by lukaszJarochowski on 2007-04-22
To get WPA working with rt61 driver from ralink i've made this: [http://ubuntuforums.org/showthread.php?t=415693]("http://ubuntuforums.org/showthread.php?t=415693")

it worked like charm.

---

### Post by codeslicer on 2007-04-26
here's a good link:
[http://susewiki.org/index.php?title=Setting_up_RT61_Wireless_Cards#For_RT61_Cards]("http://susewiki.org/index.php?title=Setting_up_RT61_Wireless_Cards#For_RT61_Cards")

First, go to [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads") and download the latest rt61 driver. Then under the list, there is a link to a graphical utility: [http://cbbk.free.fr/bonrom/]("http://cbbk.free.fr/bonrom/") Sometimes the link works...sometimes it doesn't. 

After you downloaded those files, extract the files, and go to the directory where they extracted to in the Terminal using the cd command. Then cd to the Module directory. Then type in make. This is pretty much what it should look like:

Note that when you run the commands you don't actully write the # symbols. Written for Linux newbies by a Linux newbie :)
```

#cd Desktop/rt61-1.1.0-b1.tar.gz/
#cd Module/
#make

```

Now the code should complie. A few warnings should appear. That's okay. Errors, however, shouldn't occur - you may need the development packages. You should get stuff like this:
```

Building modules, stage 2.
  MODPOST
  CC      /home/fred/work/rt61-cvs-2007011312/Module/rt61.mod.o
  LD [M]  /home/fred/work/rt61-cvs-2007011312/Module/rt61.ko
make[1]: Leaving directory `/usr/src/linux-2.6.18.2-34-obj/i386/default'

```

After that, do this:
```

#make install

```

 Next, download Dos2Unix here:
[http://www.thefreecountry.com/tofrodos/index.shtml]("http://www.thefreecountry.com/tofrodos/index.shtml")
Get the tofrodos gzipped format and install it.
Now we have to copy the config files so do this:
```

#dos2unix rt61sta.dat
#mkdir -p /etc/Wireless/RT61STA
#cp *.bin /etc/Wireless/RT61STA
#cp rt61sta.dat /etc/Wireless/RT61STA

```

I haven't tried doing this yet, but I'm going to shortly. I'll see how it goes. . .

---

### Post by blazercist on 2007-05-01
No no, you are not understanding.  I have a MS-1039 laptop it has a rt61 based wifi card built-in, with a hard on/off button.  Feisty will crash on boot just before X starts if the network-manager package is installed on the system.  If i go into recovery mode and do sudo apt-get remove network-manager i can boot normally.

So I dunno what to tell you, I read that feisty fixes rt61, and I have been able to get it to work manually with scripting, but i'd rather do it the automagic way with network-manager.

---

### Post by peterhs on 2007-05-01
> **blazercist said:**
> No no, you are not understanding.  I have a MS-1039 laptop it has a rt61 based wifi card built-in, with a hard on/off button.  Feisty will crash on boot just before X starts if the network-manager package is installed on the system.  If i go into recovery mode and do sudo apt-get remove network-manager i can boot normally.

So I dunno what to tell you, I read that feisty fixes rt61, and I have been able to get it to work manually with scripting, but i'd rather do it the automagic way with network-manager.

I think it is a bug in 7.04, I had the same problem, it would not start with the card loaded, and if i loaded the card, (pcmcia type, edimax 7608-pg) then the system would go into a soft-lockup, bug #40.  changing back to 6.10 solved that problem.

---

### Post by blazercist on 2007-05-02
> **peterhs said:**
> I think it is a bug in 7.04, I had the same problem, it would not start with the card loaded, and if i loaded the card, (pcmcia type, edimax 7608-pg) then the system would go into a soft-lockup, bug #40.  changing back to 6.10 solved that problem.

Yea yea but still can't make it work automagically, it needs scripting in 6.10 also to work, not to mention that the driver needs to be downloaded and compiled and installed as opposed to 7.04 where its already there just a dud.

---

### Post by gatoruss on 2007-06-01
I have been wrestling with wifi and Feisty for over a week. Everything worked fine until I upgraded to 7.04!

Well, after some tinkering, I have gotten the wifi to work following the tutorial mentioned in this thread, as modified by [http://ubuntuforums.org/showthread.php?t=415693]("http://ubuntuforums.org/showthread.php?t=415693"). However, it only boots up manually and I cannot get wifi to fire up on start up...I need to manually launch every time I boot up?" But it does not fire up wifi on start up....any suggestions?

---

### Post by dolphin_oracle on 2007-06-01
in your /etc/network/interfaces file you can add an auto line to your configuration.  I'm at work right now, and can't remember exactly what it looks like, but at the end of your ra0 settings, add 

auto ra0

---

### Post by Cuppa-Chino on 2007-06-19
> **tictacman said:**
> Sorry to hear that your not having much luck with the card, I'm not sure why /etc/interface is being re-written. Have you being using the network manager utility to try and configure the card?  How about reinstalling and reconfiguring the driver from scratch.  I did this a couple of times with different drivers until I hit upon a method that worked for me.  Also, if you havent already, you might try reading through the other rt61 thread created by phq [http://ubuntuforums.org/showthread.php?t=296822]("http://ubuntuforums.org/showthread.php?t=296822") 

I also did a bit of googling for you on the cpu softlock and found a bug report that might be worth a look:  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63418]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63418")


Yeah I know what you mean about having a tough time ubuntu/linux and going back to windows.  I used to do that about once a year for the past 6 years and until I was finally able to get everything working to my satisfaction.

Best of luck.

well this is what has affected me all of a sudden.

I get the softlock and only blacklisting rt61 in **/etc/modprobe.d/blacklist** seems to fix it. Odd thing is that I have used the card sucessfully in Dapper, Edgy and Feisty for a year and all of a sudden this error totally freezes me today . it is really winding me up!

anyhow last thing I installed was skype 1.4 beta but that booted up fine yesterday, so I am pretty clueless any help?:confused::cry:

---

### Post by Cuppa-Chino on 2007-06-20
wow
* de-installed skype 1.4 beta
* reinstalled kernel and headers (just from synaptic)
* then tried to boot wiht nosplash noapic lockup
* then knoppix fsck again no errors all okay
* then boot and all running again

I am so confused.. skype?

it gets better !

today I reinstall skype (after making a partimage!!!) and it all works again.... odd might have been a kernel file went belly up????

---

### Post by pat5star on 2007-06-26
Wow, just got to say a major thank you. I had tried a dozen things to no avail before finding this article. Once I followed it, it worked perfectly. Thank you very much!

-Pat

---

### Post by Kzap333 on 2007-06-28
> **Aflex said:**
> Just followed the instructions as mentioned for dapper drake for Sitecom WL-171, and it works flawlessly.

Thanks!
Hello I have a WL-171 wireless could you say where these > instructions as mentioned for dapper drake for Sitecom WL-17
Help please. I realy don't have the time to read though all the posts on this fourm.

---

### Post by jcw122 on 2007-06-29
```
~/RT61_Linux_STA_Drv1.1.0.0/Module$ **make all**
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/-----/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/------/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/home/------/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_probe’:
/home/------/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:197: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/-------/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_open’:
/home/---------/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/------/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/--------/RT61_Linux_STA_Drv1.1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [all] Error 2

```

I need some help. I'm following everything right, but when I type in "Make all" it gives me this^^

What do I do?

---

### Post by ontelo on 2007-07-27
I can't find** rt61.ko** from anywhere?

---

### Post by eglober on 2007-07-31
A huge thank you to the thread starter and all other contributors - I am one happy UbuntuHead now!

I am on Dapper with a Gigabyte GN-WP01GS card...iwpriv was the way to go! I do have to reboot yet, so keep your fingers crossed and once again, thank you all.

---

### Post by Rocky101 on 2007-08-14
(c) "No DHCPOFFERS Received"

A lot of people have posted in this thread complaining about the error "No DHCPOFFERS Received" error when they try "sudo dhclient ra0". I myself have encountered this error when trying to connect to one of the APs in the building where I work. However, I couldn't find a solution and thus could not reply to their posts. Until I read reharpernc's post which suggested using "iwpriv" instead of "iwconfig". [For more information on "iwpriv", type "man iwpriv" in your terminal.]

So for people who have encountered this problem, try:


Code:
sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=SHARED
sudo iwpriv ra0 set EncrypType=WEP
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set Key1=<my wep key>
sudo iwpriv ra0 set SSID=<my essid>then try to connect to your AP with


Code:
sudo dhclient ra0 
If this works for you, you might want to include the above lines in the "/etc/init.d/rt61up" script so that it will run at startup

This worked for me but I don't have an /etc/init.d/rt61up file to add these coomands too. When I reboot I have to manually run these commands to get internet access

*Edited* **I didn't see the instructions for this in the original post. I only read the Dapper directions **:lolflag:

---

### Post by Schlomy on 2007-08-31
This worked like a champ, thanks! I did wrestle for awhile because I entered the SSID with ?´s where spaces should go ('cuz usually Linux doesn't like spaces) but after I figured that out it worked great. Thanks for all your work!

Paul

---

### Post by DaFunks on 2007-09-01
Hi guys,

I have just got myself a CWP-854 today thinking it would work but it has this chipset now so I am having big problems.

I am using xubuntu but am having so many problems.

I am a n00b to linux (Well not used it in about 8 years) and setting this up isa big pain in the ***.

I go into Network Manager and my new card does not show up but my Olld wired one does. It is all plugged in fine and should work...

Is there a easy way to get this working?

I tried to follow this guide but ran into problems... and by the looks of the files used it is 2 years out of date so maybe there is a new fix for this.

thanks

---

### Post by Pegasus_from_UA on 2007-09-06
I  installed rt61 driver and got 2 errors

```
buzdack@buzdack-desktop:~/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module$ cp Makefile.6 Makefile
buzdack@buzdack-desktop:~/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module$ sudo make all
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/buzdack/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/buzdack/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/home/buzdack/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: &#1042; &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1080; &#8216;RT61_probe&#8217;
/home/buzdack/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:197: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;struct net_device&#8217; has no member named &#8216;get_wireless_stats&#8217;
/home/buzdack/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: &#1042; &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1080; &#8216;RT61_open&#8217;
/home/buzdack/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
make[2]: *** [/home/buzdack/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[1]: *** [_module_/home/buzdack/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
```


but when i done i have next by command #iwconfig
          ```
ra1       RT61 Wireless  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
is my wireless conection are working ???
I can't connect my laptop =(
Ubuntu 7.04 on desktop , Windows XP on laptop.
P.S. sorry for poor English

---

### Post by broom_hatter on 2007-09-10
The "NO DHCPOFFERS RECEIVED" solution doesn't work for me.  dhclient is still unable to connect.  (I've changed the iwpriv commands to reflect my network settings--TKIP instead of WEP, et cetera.)

---

### Post by shakti_saran on 2007-09-12
I resolved NO DHCPOFFERS received issue by running "dhclient ra1", restarting the router and running dhclient ra1 again. It's working now!!!

---

### Post by regomodo on 2007-09-12
to save yourself farting about with /etc/network/interfaces use rutilt. Unless your comp is fixed there is no need for it unless you like setting your wifi by cli (which i've been doing for months until i found this tool)

[http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/)

---

### Post by eliot_waldo on 2007-09-18
I'm stuck at the "edit /etc/Wireless/RT61STA/rt61sta.dat " point!

After typing  sudo vi -b rt61sta.dat  I get the page with all the wireless config setting but I'm not sure how to modify them.  (My access point is using WPAPSK.)

What should I do now?  Where is the readme/Docs file?  I can't find it in the tar.gz dowload.

Thank you so much  Eliot in Australia

---

### Post by eliot_waldo on 2007-09-20
I have Dapper, Ra Link RT61 chipset in DLink 510 rev C2 card and can't get wireless working.

I've looked through most of this thread for a solution but I'm still stuck.

I'm a newbie to linux and I may be doing something wrong I suspect.  

I get to the instruction "gksudo gedit   /etc/Wireless/RT61STA/rt61sta.dat"  , then I edit that file by replacing the "wrong" text by deleting it and typing in my wireless access point setttings (WPAPSK, TKIP, MY_essid etc) then exiting ( Is that the correct approach?).....Then

When I type iwconfig i get :       lo           no wireless extensions 
                                                   eth0       no wireless extensions 
                                                   ra0         no wireless extensions
                                                   sit0        no wireless extensions

when I type "sudo iwconfig raO" i get "Interface doesn't support scanning" 

when I type "lspci" I get  "0000:00:0a.0 Network Contoller: Ralink: Unknown device 0302 (so i presume linux recognises the card)

Can anyone help me out here. Thanks  ELIOT

---

### Post by eliot_waldo on 2007-09-23
So, I found the answer to my problem and for those who are having the same problem here's what I did:

Firstly, I learned how to edit scripts with vi by reading the excellent tutorial by typing "vimtutor" into a terminal line.  THIS IS ESSENTIAL!

I deleted  rt61sta.dat file: "cd /etc/Wireless/RT61STA/" then "sudo rm rt61sta.dat" 

I reloaded the rt61sta.dat file as per the instructions at the begining of this thread by judgekaster(Some Additional Notes part (b) rt61 Dapper part 2.)

Then I edited the rt61.dat file as per part (d) of the instructions using the correct vi keystrokes and saved the edited file by typing ":wq" (without the quotes) (SSID=My_Network_Name, Type= Infra, AuthMode=WPAPSK, EncrypType=TKIP, WPAPSK= My _Secret_Passphrase, All other lines I left alone).

Then I followed steps f, g and h, rebooted and BINGO IT WORKS.

THank you. It's taken me a week and lots of reading but the effort paid off

---

### Post by Ronin69 on 2007-11-08
4 hours of trying to get this to work.  Ubuntu has nothing on Windows.

Good thing I still have a working copy of XP.

---

### Post by RebounD11 on 2007-12-03
Followed tutorial ==> no more wireless... NOWHERE! it's like I don't even have a wireless card in my computer. 

It failed miserably. took 5 minutes to do it, and another 55 minutes to undo... I'd rather stick to the serialmonkey drivers, so far the only one that work, even the default ones at least showed me I have  a wireless card (useless but something).

PS: Sorry for the angry tone, that wasn't the point, I appreciate the tutorial, and the fact that someone took out of his time to write it, I just hate it that it doesn't work for me :D

---

### Post by k3lt01 on 2007-12-28
This, like the Ubuntu Wiki solution which this looks to be based on, does not work for me at all. I cannot get past the "sudo make all" command at the begining.

Stupid thing is that the driver setup that comes with Gutsy shows that I have a wireless setup, its only problem is it is eractic.

Oh well I will keep searching and see what i can find.

---

### Post by sunseeker888 on 2008-02-12
Guys


i am an absolute newbie, i am having problem setting up w_lan. the file below does not exist anymore can anybody help??







[http://www.ralinktech.com/drivers/Li...1.0.3.0.tar.gz](http://www.ralinktech.com/drivers/Li...1.0.3.0.tar.gz)

---

### Post by k3lt01 on 2008-02-27
I finally got mine working and I did not use this solution at all. I just went the ndiswrapper way and I am now typing here on the very same machine I couldn't get working with the above solutions. Go figure hey.

---

### Post by zpon on 2008-04-30
> **sunseeker888 said:**
> Guys


i am an absolute newbie, i am having problem setting up w_lan. the file below does not exist anymore can anybody help??







[http://www.ralinktech.com/drivers/Li...1.0.3.0.tar.gz](http://www.ralinktech.com/drivers/Li...1.0.3.0.tar.gz)

I believe this is the one [http://www.ralinktech.com.tw/data/drivers/2007_1210_RT61_Linux_STA_v1.1.2.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2007_1210_RT61_Linux_STA_v1.1.2.0.tar.bz2)
The tutorial needs updating

---

### Post by Cuppa-Chino on 2008-04-30
Hi, what version of ubuntu are you using?

If you go to System --> Network do you see a wlan adapter ?

---

### Post by AdrianPtchv on 2008-05-06
There were also problems with my ralink rt2561 pci card after the update to 8.04 version of Ubuntu.
The kernel module which came with it was not working properly (not receiving iwpriv commands). I had to download the latest CVS from serialmonkey, disable the modules, compile and install it and blacklist the previous (already unloaded modules).
After I had to mess a bit with /etc/network/interfaces file.
The following is my successful configuration:

auto lo
iface lo inet loopback

  # The wireless network interface
auto wlan0
iface wlan0 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1
ifconfig wlan0 down
iwconfig wlan0 essid ThenameoftheWIFIrouter
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="74ccaf28761b32a8b45b44b7c25e5f7c9ea45b253aa51bf72f4ff9d26486e3b"
pre-up ifconfig wlan0 up

After the PC went online I received another update and the kernel module had to be reinstalled.
Now it is working and I am planning to try WPA2 AES.
Hope this will be useful for someone.
Generally after each major update there are problems with the wireless card on ubuntu...

---

### Post by cuz on 2008-05-09
I just wanted to throw up a quick bit of info for Hardy users. Here is the simple solution that worked for me (on Toshiba Portege 4005), since I spent ages today and the solution was simple:

1. Install Hardy with the PCMIA wireless card (Orinoco Gold, rt61). I'm using a static IP, so it couldn't configure correctly. I told it to skip config for now.

2. Log in. Change network settings. The KEY: enter WEP key as hex. [Thanks to whoever mentioned that above!] Et voila! Easy peasy.

Note: appending 's:' to the ascii did not work (e.g., 's:your_pwd')

cuz Ubuntu just makes it easy-ish

---

### Post by k3lt01 on 2008-05-09
I installed Hardy as a clean install, not an update, and have never had a moments trouble. No changing settings, no checking anything, it just works out of the box.

You guys using Hardy now who have troubles, even minor ones, is your Hardy a clean install or was it an update from Gutsy or another version? If it was an update some old setting may be hanging and stopping it from working properly.

---

### Post by Payteer on 2008-05-10
Mine was a clean install.  The card is D-Link DWA-610 with a RT61 chip set.  It can detect networks, but I can't put my WPA password in as it keeps on asking for it.

---

### Post by k3lt01 on 2008-05-11
I don't understand what might be the problem for you then sorry. I know when I had Gutsy on mine I had to try a few times, clean installs, to get it to work with ndiswrapper. The only thing I can think of in your case is something may not have installed properly when you installed Hardy.

---

### Post by 4nt1 on 2008-05-22
Hi everybody,

i loaded the rt61 drivers from the ratlink-page, compiled them without problems and installed the rt61,ko module. so far, the module gets loaded (tested via modprobe rt61), but its never used, so no wlan iface like ra0 or wlan0 is present! here the output of "lsmod | grep rt61":

> 
rt61                  241156  0 


"modinfo rt61":

> 
filename:       /lib/modules/2.6.24-16-generic/kernel/drivers/net/rt61.ko
description:    RT61 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     57EF7C13DC2F540964E6100
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.24.3 SMP mod_unload 586 


and "modinfo rt61pci":
> filename:       /lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.0.10
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     D71C36F67F7A0F8B005A78F
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,mac80211,eeprom_93cx6
vermagic:       2.6.24-16-generic SMP mod_unload 586 


any suggestions?

---

### Post by LouReed on 2008-07-24
Hi,
First of all sorry for my shitty english..

Anyway I couldn't find enough help in the french version of the forum so I came down here ..
(yeah I really need some help apparently)

I'm on Xubuntu 8.04 (clean install) fighting with my brand new ralink DWA-510 (rt61 chipset)

My card works (it seems) I mean it can detect lans and I even succeeded in connecting once to my router.

But the connection isn't stable even if wicd says it's like allmighty ! 

So my questions are :

1) Is the preloaded hardy heron driver for rt61 the same that you can find on the ralink website ? if not should I try to install the ralink instead ?

2) Is it a good idea to try the seriamonkey stuff on hardy ?

3) why the f*** do they say they have a driver if it doesn't (really)work ? :p

PS: I tried to use wicd because Network manager kept bullying me lol.
I also tried the manual way..

---

