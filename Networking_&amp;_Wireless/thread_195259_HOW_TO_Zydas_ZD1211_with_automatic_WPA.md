---
title: "HOW TO: Zydas ZD1211 with automatic WPA"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by shof2k on 2006-06-12
_HOW TO: Zydas ZD1211 wireless with automatic WPA_


**Aim**
This is the dapper version of my previous guide.  As before, I hope this helps you set up a WPA encrypted wireless network when using a ZD1211 based wireless card, such as the Safecom SWLU-5400 dongle.  Thanks to ubuntu user dom for pointing me in the right direction.  It comes in 3 parts:
	Part 1 – Installing the module
	Part 2 – Installing wpa supplicant
	Part 3 – Troubleshooting

**User level**
Intermedidate. This isn't meant to be a simple list of commands to type in to a terminal because networking has too many options for any one script to cover.  You may need to tweak some of the commands or files to your own system settings.

I have got this working on the default 2.6.15-23-386 kernel.  Some of the files may need changing for other kernels.

**Prerequisites**
You can navigate around the file system using the terminal
You can copy and move files using the terminal
You can edit files from the terminal.
You can untar packages
You can follow bad how to's ;)
All downloaded files are assumed to be in /usr/src.  

**Part 1 – Installing the module**
1) You will need the ZD1211 kernel module and wpa_supplicant.  Unfortunately, the versions supplied by ubuntu don't work, so we have to remove them first.  Unplug your dongle/ card, then open a terminal and type:
```

sudo modprobe -r zd1211
sudo apt-get remove wpasupplicant 

``` 

2) The following may not be essential, but it's worth installing to ensure better success with this and any future projects you might do. In a terminal type:
```

sudo apt-get install build-essential kernel-package gcc libncurses5 libncurses5-dev libqt3-mt-dev wireless-tools libssl-dev 

```

3) Work out which version of the kernel you have by typing:
```

uname -r

``` 

4) Obtain the correct headers and source for the kernel.  In my case I'm running 2.6.15-23-386, so I need to get:
```

sudo apt-get install linux-headers-2.6.15-23 linux-headers-2.6.15-23-386 linux-source-2.6.15

``` 

5) Unpack the source and create a standard symbolic link.
```

cd /usr/src
sudo tar -xvjf /usr/src/linux-source-2.6.15.tar.bz2 
sudo ln -s /usr/src/linux-headers-2.6.15-23 /usr/src/linux-headers
sudo ln -s /usr/src/linux-source-2.6.15 /usr/src/linux 

```

6) Also make sure you have a link in /usr/lib/2.6.15-23-386/ build pointing to /usr/src/linux-headers-2.6.15-23-386.  This should be already present, but if not type:
```

sudo ln -s /usr/src/linux-headers-2.6.15-23-386 /usr/lib/2.6.15-23-386/build

```

7) Download a working version of the ZD1211 driver.  There are 2 sites for try there:
a)The Zydas website at: [http://www.zydas.com.tw](http://www.zydas.com.tw).  Click on downloads, then either ZD1211 or ZD1211B.
b) [http://zd1211.ath.cx/download/](http://zd1211.ath.cx/download/).

Both sites gave me a working driver but I found [http://zd1211.ath.cx/download/zd1211-driver-r38.tgz](http://zd1211.ath.cx/download/zd1211-driver-r38.tgz) gave me a driver that worked with wpasupplicant.  You may need to experiment with different drivers to get one that works for your particular dongle/card and kernel.

8.) Untar the source package you selected and edit the Makefile to have the following options:
KERNEL_SOURCE=/usr/src/linux
ZD1211REV_B=0 (set this to 1 if you have a ZD1211B)

9) Compile the module by typing:
```

sudo make
sudo make install 

```

10) Copy the resulting zd1211.ko to /lib/modules/2.6.15-23-386/kernel/drivers/usb/net/zd1211.

11) Install the module using
```

sudo depmod -a
sudo modprobe -v zd1211  

```

12) Now connect the dongle and type 
```

dmesg

```

You should see something like:
```

298456.774000] |__  /   _|  _ \  / \  / ___|
[4298456.774000]   / / | | | | | |/ _ \ \___ \
[4298456.774000]  / /| |_| | |_| / ___ \ ___) |
[4298456.774000] /____\__, |____/_/   \_\____/
[4298456.774000]      |___/
[4298456.774000] zd1211 - version 2.12.0.0
[4298456.774000] usbcore: registered new driver zd1211
[4298466.332000] usb 4-3: new high speed USB device using ehci_hcd and address 5[4298466.585000] Release Ver = 4330
[4298466.585000] zd1211:bulk out: wMaxPacketSize = 200
[4298466.585000] zd1211:bulk in: wMaxPacketSize = 200
[4298466.585000] zd1211:interrupt in: wMaxPacketSize = 40
[4298466.585000] zd1211:interrupt in: int_interval = 1
[4298466.585000] zd1211:interrupt out: wMaxPacketSize = 40
[4298466.585000] EEPORM Ver = 4330
[4298466.585000] zd1211:USB Download Boot code success
[4298466.709000] zd1211:MAC address = 00:e0:98:bf:12:32
[4298466.772000] zd1211:AddrEntryTable = f7d4
[4298466.834000] zd1211:RF_Mode = 0000010d
[4298466.834000] PA type: 0
[4298466.834000] RFMD RF
[4298466.834000] zd1211:Mixed Mode
[4298466.834000] zd1211:File opening did not success
[4298467.020000] zd1211:AllowedChannel = 000007ff
[4298467.082000] zd1211:LinkLEDn = 200
[4298467.144000] AllowedChannel = 000107ff
[4298467.144000] Region:48

```

If you get any error codes here, you will need to go back to 7) and use another driver package.

13) If you have an unsecured network, you should be able to start browsing. To check type:
```
sudo ifconfig 
```to list all the active network connections 
```
sudo iwconfig 
```to list the status of your wireless connection.
	
If you go to SYSTEM-ADMINISTRATION-NETWORKING you can bring up the networking tool to manually disable your ethernet connection and set up wep encryption.  I found keeping only the wireless or wired interface active made my system more stable.

Note if you use a different kernel or recompile your kernel differently, you may well need to do this again.  It's worth posting the driver package that worked for you and the kernel/system used.


**Part 2 – Setting up WPA encryption**

Unless you're comfortable with the world and their dog also using your wireless network, you should really put some encryption on it.  WEP is trivial to do, but is now trivial to break.  Currently WPA/PSK is much more secure.  

This part of the HOW-TO will install a zd1211 friendly version of the linux WPA client wpa_supplicant and have this set up automatically.

1) Download the openssl source file by typing into a terminal:
```

cd /usr/src
sudo apt-get source openssl
sudo tar -xvzf openssl-0.9.8a

```	

2) Download and untar the zydas wpa supplcant from [http://www.zydas.com.tw](http://www.zydas.com.tw).  Click on "Downloads", then click either "ZD1211" or "ZD1211B".

3) Delete the file .config
```

sudo cd /usr/src/wpa_supplicant-0.4.7_zydas
sudo rm .config

```

4) Create a new config file.
```

sudo gedit .config

```

Paste the following configuration options into the file:
[B]CONFIG_DRIVER_HOSTAP=y
CONFIG_DRIVER_WEXT=y
CONFIG_MSCHAPV2=y
CONFIG_WIRELESS_EXTENSION=y
CONFIG_IEEE8021X_EAPOL=y
CONFIG_EAP_MD5=y
CONFIG_EAP_PEAP=y
CONFIG_EAP_TLS=y
CONFIG_DRIVER_ZYDAS=y[/B]

5) Create a link to the openssl source libraries.  
```

sudo ln -s /usr/src/openssl-0.9.8a/include/openssl /usr/src/wpa_supplicant-0.4.7_zydas/openssl

```

6) Compile the program. 
```
	
sudo make clean
sudo make
sudo make install

```


7) Once compiled, create some system links:
```

sudo ln -s /usr/src/wpa_supplicant-0.4.7_zydas/wpa_supplicant /usr/sbin/wpa_supplicant

```

8.) Set up /etc/wpa_supplicant.conf, changing the values in italics:
network={
		ssid = “*network id*”
		scan_ssid = 1
		pairwise=TKIP
		psk=”*encryption key*”
		key_mgmt=WPA-PSK
		proto=WPA
	}

9) Set up your access point to be encrypted, then test the supplicant by typing:
```
	
sudo wpa_supplicant  -i wlan0 -c /etc/wpa_supplicant.conf -D zydas -ddddd

```

and reading the output on the terminal for any error messages.  This took a few attempts with my keyboard becoming very slow as the connection was made.  If your connection is dropped repeatedly, you may need a different driver.

10) If you can connect OK, you can terminate the supplican and set it in the background with
```

sudo wpa_supplicant  -Bw -i wlan0 -c /etc/wpa_supplicant.conf -D zydas 

```

11) To have your wireless network come up automatically with wpasupplicant, edit  /etc/network/interfaces to have the following 2 lines after the iface wlan0 entry:
[B]
pre-up wpa_supplicant -Bw -i wlan0 -c /etc/wpa_supplicant.conf -D zydas
post-down killall -q wpa_supplicant.[/B]

12) To restart your network, type
```

sudo /etc/init.d/networking restart

```
and hopefully wpa should now be working.........

Hope this helps :)

**Part 3 Troubleshooting**
i)I keep getting module error messages.
Keep trying alternate driver versions from both sites above. 

ii)wpasupplicant doesn't compile.
	Check the .config file.  Make sure openssl is linked correctly.

---

### Post by sguart on 2006-06-19
.

---

### Post by dougfir on 2006-06-30
Great HOWTO!  

But I upgraded to 2.6.15-25-386 and now it doesn't work for me.

Has anyone upgraded to 2.6.15-25-386 and have it still work?

---

### Post by shof2k on 2006-06-30
Am on 2.6.15-25-386 myself.  Did you download the new linux-header files and copy the zd1211.ko module to /lib/modules/2.6.15-25-368 as well?

Hope that helps

Will let you know how I get on witht he 686 kernel

---

### Post by dougfir on 2006-07-01
[QUOTE=shof2k]Am on 2.6.15-25-386 myself.  Did you download the new linux-header files and copy the zd1211.ko module to /lib/modules/2.6.15-25-368 as well?

Hope that helps

Will let you know how I get on witht he 686 kernel[/QUOTE]


Well, I chickened out and went back to 2.6.15-23-386.  Maybe I'll try to upgrade later, but now it's time to actually use Linux!  Good to know that it works in ...25-386

---

### Post by shof2k on 2006-07-01
2.6.15-25-686 is fine with the r38 driver.

Anyone know how to get this sorted in Edgy?

---

### Post by StylusPilot on 2006-07-02
Great guide, I'm just having one issue with number 7,

in my /usr/src/wpa_supplicant-0.4.7_zydas folder there is no file called wpa_supplicant, only

wpa_supplicant.conf
wpa_supplicant.c
etc....

Am I meant to be linking to one of those?

---

### Post by dom on 2006-07-13
> **shof2k said:**
> _HOW TO: Zydas ZD1211 wireless with automatic WPA_
<snip>

Nice howto !

I tried to update to Dapper recently but it died halfway through, and then I had lots of half installed stuff. So I got the Dapper ISOs for Ubuntu and Xubuntu.  I installed the latter and am very happy with it, apart of course from the wireless issue, didin't relish the thought of going through this again !

Anyway, some comments on going through this as I lost my own notes from the fun I had last year :)

Part 1 point 1, "apt-get remove wpasupplicant" also want to remove ubuntu base and something else, has anybody let it ?? is it safe ?

Part 1 point 7, is the link wrong ?

Part 2 point 1, this doesn't get the openssl source for me ! I have a comment on another thread, others have seen this also, so just in case somebody here get its, it appears apt doesn't always get the source for this one...

I just got through it all and it doesn't like my configuration file, I'll be back later.


Anybody know if this is every going to make it into the standard distro ?

---

### Post by shof2k on 2006-07-13
> **StylusPilot said:**
> Great guide, I'm just having one issue with number 7,

in my /usr/src/wpa_supplicant-0.4.7_zydas folder there is no file called wpa_supplicant, only

wpa_supplicant.conf
wpa_supplicant.c
etc....

Am I meant to be linking to one of those?
You need to compile wpa suplicant first (step 6).  You will then see the file wpa_supplicant.

Hope that helps

---

### Post by shof2k on 2006-07-13
> 
Part 1 point 1, "apt-get remove wpasupplicant" also want to remove ubuntu base and something else, has anybody let it ?? is it safe ?

Ubuntu base is a meta-package (a collection of packages not the packages themselves).  Removing it shouldn't cause problems.

> 
Part 1 point 7, is the link wrong ?

The link is ok, but the site doesn't support a direct link (something  about virutal directories). I'll put the domain there instead with instructions on how to get to the source.

> 
Part 2 point 1, this doesn't get the openssl source for me ! I have a comment on another thread, others have seen this also, so just in case somebody here get its, it appears apt doesn't always get the source for this one...

My bad.  The command should be "apt-get source". I'll correct the HOWTO.

I hope Edgy takes care of this.  I don't know how I can push this further other than cornering Mark Shuttleworth at lugradio live.

---

### Post by dom on 2006-07-13
> **shof2k said:**
> Ubuntu base is a meta-package (a collection of packages not the packages themselves).  Removing it shouldn't cause problems.


coola, thanks

> **shof2k said:**
> 
The link is ok, but the site doesn't support a direct link (something  about virutal directories). I'll put the domain there instead with instructions on how to get to the source.

i mean one of the "ln -s" commands given there ....? ?

> **shof2k said:**
> 
My bad.  The command should be "apt-get source". I'll correct the HOWTO.


Ah, just showing up what I don't know now :)

> **shof2k said:**
> 
I hope Edgy takes care of this.  I don't know how I can push this further other than cornering Mark Shuttleworth at lugradio live.

I hope so too.

Anyway, just got it working, it moved from the latest zydas driver back to 38 but it turned out that the wpa-supplicant didn't like some lines in the config, these to be specific :
  #ctrl_interface=/var/run/wpa_supplicant
  #ctrl_interface_group=0

I just commented those as shown and it was fine then. I'm on xubuntu wireless with wpa-psk (tkip) again as i type :)

Btw, by dev is still the Usb adaptor, 3com 3crusb10075.

Will try the latest zydas driver again and report here.

Again, thanks for compiling these notes !

Fingers crossed that the ubuntu devs get better wireless support both in terms of drivers that are already out there, and the wpa code. As you say, people are fast ditching wep, i don't know anybody who bothers with it now really.

---

### Post by dom on 2006-07-13
> **dom said:**
> 
Will try the latest zydas driver again and report here.


latest zydas driver didn't work out of the box with wpasupplicant for me(ioctl errors), so i went back to version 38, which was what i had used before with ubuntu 5.10.

---

### Post by shof2k on 2006-07-14
I've fixed the duplicate link in pt2 step7.

Glad this helped.  The sooner WPA and wireless work "out the box", the closer linux is to making the mass desktop.

---

### Post by Robroy11976 on 2006-07-16
Does is guide also work with WEP or 802.11b only? Do i have to run this all even with WEP only???

---

### Post by shof2k on 2006-07-16
> **Robroy11976 said:**
> Does is guide also work with WEP or 802.11b only? Do i have to run this all even with WEP only???

802.11b or g depends on your hardware, this guide will work on both. 

You only need part 1 to get the network running.  WEP is available via System-Administration-Networking.  However WEP is trivial to crack and gives almost no protection.

Unless you mind anyone using and snooping your Wireless LAN, I'd give WPA a try.

---

### Post by Robroy11976 on 2006-07-16
Ah ok ... so even if i can all of these and still use 802.11b and WEP Key ... it will still work ...

---

### Post by DX 00 on 2006-07-17
Great How To. Thanks a lot. I just installed Dapper Drake with linux-kernel-2.6.15-26 and so far, the how to works perfectly with nonsecure and wep networks. I'll try wpa soon though.

Thx alot.:D

---

### Post by Robroy11976 on 2006-07-17
Is the Linux kernel file like the ver 2.6.xx is pre-installed in Dapper?  coz i can't seem to find it in the usr/src folder ... or is it the one in the apt-get install linux-source???

---

### Post by shof2k on 2006-07-17
> **Robroy11976 said:**
> Is the Linux kernel file like the ver 2.6.xx is pre-installed in Dapper?  coz i can't seem to find it in the usr/src folder ... or is it the one in the apt-get install linux-source???

Yep thats the source.  As per the guide, you need to copy the archive to /usr/src, unpack it to get the linux-source-2.6.* folder, then create a link to it called /usr/src/linux.  

Try to follow the guide and let me know where things are confusing.

---

### Post by Robroy11976 on 2006-07-17
I can't seem to install the linux-source ... should i change the repositories first as suggested in the ubuntuguide.org???  And do i have to be online to install this this packages??

---

### Post by Marc Higgins on 2006-08-19
I am having trouble getting networking on my old laptop.

It is a 150mhz mmx with 64mg ram (Samsung S600) running stock standard xubuntu 6.06, kernel 2.6.15-26-386

There are 2 ways we should be able to connect to the internet on this machine but neither are working for me at the moment

Unicorn USB WL54G wireless adapter (Chipset is ZyDAS Zd1211b) this is the preferred method but as a back up plan I have some Xircom PS-CEM-28 combo 10BaseT Ethernet 28.8kbs/33.6kbs fax modem PCMCIA cards that i have had working in the past on this machine.

Unicorn USB WL54G wireless adapter
(Chipset is ZyDAS Zd1211b)

lsusb shows

Bus 001 Device 005: ID 0ace:1215 ZyDas
Bus 001 Devide 001: IS 0000:0000

so it sees it OK

I have done modprobe zd1211 & I can see it in then in lsmod (but this disappears with a reboot)

lsmod |grep zd
zd1211 206624 0
usbcore 130692 3 zd1211,usbhid,uhci_hcd

iwconfig shows

lo 	no wireless extensions

there is nothing obvious in dmsg

At this point i found this thread & though woo hoo!

[http://www.ubuntuforums.org/showthread.php?t=195259&highlight=Zd1211](http://www.ubuntuforums.org/showthread.php?t=195259&highlight=Zd1211)

sudo modprobe -r zd1211
sudo apt-get remove wpasupplicant 

sudo apt-get install build-essential kernel-package gcc libncurses5 libncurses5-dev libqt3-mt-dev wireless-tools libssl-dev 

& things start to come unstuck form me on this howto here; 

we don't have a web connection yet so I cant find get the other repositories so there is no  kernel-package libncurses5-dev libqt3-mt-dev libssl-dev 

unname -r
2.6.15-26-386

sudo apt-get install linux-headers-2.6.15-26 linux-headers-2.6.15-26-386 linux-source-2.6.15

again no network connection means no linux-source

so thats about as far as i can go unless i can get some kind of a web connection & access to the repositories

so I turned to the xirom (the backup plan)

Xircom PS-CEM-28 combo 10BaseT Ethernet 28.8kbs/33.6kbs fax modem PCMCIA card. 

This was working beautifully on this laptop under sarge around 1 year ago guessing kernel 2.2, I remember i had to do a modprobe but cant be 100% sure I have the right module

modprobe xirc2ps_cs seems to do nothing 

cardctl status shows

Socket0:
5V 16-bit PC Card
funtion 0: [ready]
Socket 1:
no card

So the pcmcia slot sees something.

for good measure I also installed tried modprobe xircom_tulip_cb but this made no difference.

Have a PCMCIA compact flash adapter & when I put that in as well i get 

Socket0:
5V 16-bit PC Card
funtion 0: [ready]
Socket 1:
3.3V 16-bit PC Card
funtion 0:[read]

So I am guessing the PCMCIA slot is working fine 

Help me please, I am going out of my brain here ](*,)

---

### Post by 4ndr3wk on 2006-08-20
9) Compile the module by typing:
Code:

sudo make sudo 
make install

sorry to be a n00b but where abouts do i need to throw this data into to compile it? is it into the terminal or into the code for the driver? :-k 

thanks 4ndr3wk

---

### Post by shemyak on 2006-08-22
> **4ndr3wk said:**
> sorry to be a n00b but where abouts do i need to throw this data into to compile it? is it into the terminal or into the code for the driver? :-k 

You should type these 2 commands (first is 'sudo make', second 'sudo make install') in the terminal. Your working directory must be the directory where you have unpacked driver's source.

---

### Post by cybersnoop on 2006-08-23
I've been able to compile the zd1211 (r83) and set-up wpasupplicant. It all works, but is **extremely slow** (transferring with Samba is at most 10 kBps)

iwconfig wlan0 reports:
```
Link Quality=100/100  Signal level=95/100  Noise level=0/100
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:8127
Tx excessive retries:74459  Invalid misc:1   Missed beacon:0

```

and pinging my router results in:
```
min/avg/max/mdev = 4.007/71.018/107.782/28.613 ms
```

which is rather extreme compared to my windows box pinging the router in <=1ms (over WLAN ofcourse).

How can I debug this problem? Is it the *Rx invalid frag* or the *Tx excessive retries*?

---

### Post by joerenes on 2006-08-27
Thanks for the well-written howto. Unfortunately, I had no luck.

I tried several different modules, both 2.6 and 2.15 from zydas (now part of atheros) and three from the other source, 38, 83 and 72. none of them could connect, although wpasupplicant reported that it was connected. the access point saw nothing, however, and trying to bring up the network with dhcp failed. since i've got a pci slot doing nothing, i think i'll try that route. 

-joe

---

### Post by funchords on 2006-08-28
For step 6, I got "No such file or directory" until I did the following:

> sudo mkdir /usr/lib/2.6.15-26-386
sudo mkdir /usr/lib/2.6.15-26-386/build
sudo ln -s /usr/src/linux-headers-2.6.15-26-386 /usr/lib/2.6.15-26-386/build


Hope I did that right...  still slogging through...

---

### Post by funchords on 2006-08-28
> **shof2k said:**
> 

1) Download the openssl source file by typing into a terminal:
```

cd /usr/src
sudo apt-get source openssl
sudo tar -xvzf openssl-0.9.8a

```	

The second command produced an error.  It seems that the first command (or something else along the way) already created a directory.  

```
robb@TOPOL016:/usr/src$ sudo apt-get source openssl
Reading package lists... Done
Building dependency tree... Done
Need to get 3306kB of source archives.
Get:1 http://us.archive.ubuntu.com dapper/main openssl 0.9.8a-7build1 (dsc) [810B]
Get:2 http://us.archive.ubuntu.com dapper/main openssl 0.9.8a-7build1 (tar) [3271kB]
Get:3 http://us.archive.ubuntu.com dapper/main openssl 0.9.8a-7build1 (diff) [33.4kB]
Fetched 3306kB in 8s (381kB/s)
dpkg-source: extracting openssl in openssl-0.9.8a
dpkg-source: unpacking openssl_0.9.8a.orig.tar.gz
dpkg-source: applying ./openssl_0.9.8a-7build1.diff.gz
tar: Read 6656 bytes from -
robb@TOPOL016:/usr/src$ sudo tar -xvzf openssl-0.9.8a
tar: openssl-0.9.8a: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error exit delayed from previous errors
robb@TOPOL016:/usr/src$ ls -l
total 46672
lrwxrwxrwx  1 root src        28 2006-08-28 14:34 linux -> /usr/src/linux-source-2.6.15
lrwxrwxrwx  1 root src        32 2006-08-28 14:34 linux-headers -> /usr/src/linux-headers-2.6.15-26
drwxr-xr-x 19 root root     4096 2006-08-28 14:22 linux-headers-2.6.15-26
drwxr-xr-x  4 root root     4096 2006-08-28 14:22 linux-headers-2.6.15-26-386
drwxr-xr-x 20 root root     4096 2006-08-02 22:01 linux-source-2.6.15
-rw-r--r--  1 root root 44403157 2006-08-02 22:02 linux-source-2.6.15.tar.bz2
drwxr-xr-x 23 root root     4096 2006-08-28 15:45 openssl-0.9.8a
-rw-r--r--  1 root src     33424 2006-03-29 01:07 openssl_0.9.8a-7build1.diff.gz
-rw-r--r--  1 root src       810 2006-03-29 01:07 openssl_0.9.8a-7build1.dsc
-rw-r--r--  1 root src   3271435 2005-11-15 05:35 openssl_0.9.8a.orig.tar.gz
drwxr-xr-x  4 robb robb     4096 2006-08-28 15:41 zd1211-driver-r38
robb@TOPOL016:/usr/src$

```

HTH, so far so good!

---

### Post by funchords on 2006-08-28
> **shof2k said:**
> 
2) Download and untar the zydas wpa supplcant from [http://www.zydas.com.tw](http://www.zydas.com.tw).  Click on "Downloads", then click either "ZD1211" or "ZD1211B".

Looks like the site has been redesigned.  I found a copy here (ZD1211).

[http://www.atheros.com/RD/ZyDAS/web_driver/ZD1211_USB/Linux/wpa_supplicant-0.4.7_zydas.tar.gz]("http://www.atheros.com/RD/ZyDAS/web_driver/ZD1211_USB/Linux/wpa_supplicant-0.4.7_zydas.tar.gz")

and here (ZD1211B)

[http://www.atheros.com/RD/ZyDAS/web_driver/ZD1211B/Linux/wpa_supplicant-0.4.7_zydas.tar.gz]("http://www.atheros.com/RD/ZyDAS/web_driver/ZD1211B/Linux/wpa_supplicant-0.4.7_zydas.tar.gz")

---

### Post by funchords on 2006-08-28
> **shof2k said:**
> 
7) Once compiled, create some system links:
```

sudo ln -s /usr/src/wpa_supplicant-0.4.7_zydas/wpa_supplicant /usr/sbin/wpa_supplicant

```

The **sudo make install** copies the binaries to /usr/local/sbin, which is in the path.  I think these links aren't necessary (and are, perhaps, confusing). Your thoughts?

---

### Post by funchords on 2006-08-28
> **shof2k said:**
> 
11) To have your wireless network come up automatically with wpasupplicant, edit  /etc/network/interfaces to have the following 2 lines after the iface wlan0 entry:
[B]
pre-up wpa_supplicant -Bw -i wlan0 -c /etc/wpa_supplicant.conf -D zydas
post-down killall -q wpa_supplicant.[/B]


The period at the end of the second line causes it to fail (wpa_supplicant.: no process killed).  Removing the period causes it to behave as it should.

 ... AND ... after all is said and done ... :KS  :KS  IT WORKS  :KS  :KS 

I seem to be stuck at 11 MB/s rate, but I haven't even started to troubleshoot that.  

I am using a Hawking HWU54G USB Wireless-G adapter.  It uses the ZD1211 (not Rev B) version of the driver.  

Something to add to the HowTo?...

I didn't know how to tell whether I had a Rev B or not.  This was helpful:
[http://zd1211.ath.cx/wiki#ZyDASZD1211802.11b/gUSBWLANchipsetLinuxdrivers]("http://zd1211.ath.cx/wiki#ZyDASZD1211802.11b/gUSBWLANchipsetLinuxdrivers")

[B][I]Oh my...

As I'm completing this message, I just ran across this page.  Turns out we probably can forget all this wpa_supplicant rebuilding as long as we use a more recent driver ...

[http://zd1211.ath.cx/wiki/WPAConfiguration]("http://zd1211.ath.cx/wiki/WPAConfiguration")[/I][/B]

Sigh...

---

### Post by Stealth on 2006-08-29
Yea, I have some questions about this!

Although the instructions here didn't quite get it working for me (I just used the basic instructions from: [http://zd1211.ath.cx/](http://zd1211.ath.cx/)) I was wondering whether or not these Zydas chips will work with network manager? And if they do, how do I go about setting up the wpa for them, seeing as how my NM doesn't seem to pickup the wlan0...

Also, if you can't use NM, how can I use my current install of wpasupplicant to do what is necessary? Like someone said above, it looks like:
> Driver rev 58 and newer work with stock wpasupplicant, with -D wext driver profile.

But how do I use that wext driver?

---

### Post by funchords on 2006-08-29
wext is not a driver, it just means that you use a driver that supports Wireless Extensions.  

Warning: I haven't tried this myself... I just noticed that quote yesterday.

If you have compiled and installed zd1211 driver Rev. >58, then theoretically you should not have to do anything except install network-manager and network-manager-gnome via apt-get and reboot your system.  (The Network Manager enumerates the cards at boot time.)

If it doesn't work, then the other option (also theoretically) is to uninstall network-manager and to use the existing wpa_supplicant.  Create a wpa_supplicant.conf file as described here, use the same command line except replace the -D zydas with -D wext.

Please let me know what happens.  I'd do this myself except I have a full agenda for today.

---

### Post by Stealth on 2006-08-29
Ok, awesome! Thanks. Looks like I just need to keep the key in the usb for network-manager to detect it.

Although it is pretty buggy. No range detection, and although it claims to not support WPA, it will eventually connect to the network once I type the password to the keyring...

---

### Post by shof2k on 2006-08-30
It's well worth putting the extra repositories in and yes you need to be online.

---

### Post by shof2k on 2006-08-30
I'll make a note of funchops comments and update the guide soon. 

Thanks to everyone who put a comment up :)

---

### Post by funchords on 2006-08-30
LOL @ "funchops!"  :-)

---

### Post by normal on 2006-08-31
How do I get linux-source-2.6.15 with no internet connection whatsoever?

---

### Post by joerenes on 2006-09-01
scratch my previous post --- now it works!!! Can I change my vote somehow?

I followed the install guide at [http://zd1211.ath.cx/]("http://zd1211.ath.cx/") with the stock wpasupplicant ubuntu package (0.4.8-3ubuntu1.1) and the latest driver (r83). I'm using a zxyel g-220 and -D wext did the trick!

Additionally, I changed my /etc/network/interfaces to look like:

auto wlan0
iface wlan0 inet dhcp
     [INDENT]wpa-ssid <name>
     wpa-scan-ssid 1
     wpa-proto WPA2
     wpa-key-mgmt WPA-PSK
     wpa-psk <precomputed key>
     wpa-ap-scan 1[/INDENT]

and the network comes up automatically. Thanks!

-joe

---

### Post by funchords on 2006-09-03
Joe, with that in your /etc/network/interfaces -- are you using Network Manager at all, then?

This is great!

---

### Post by Bilko on 2006-09-03
Thanks, works great :p  got my 3com dongle  (3CRUSB10075) going following the steps in the first post !

---

### Post by regmind on 2006-09-03
> **Bilko said:**
> Thanks, works great :p  got my 3com dongle  (3CRUSB10075) going following the steps in the first post !
Bilko, I have exactly the same dongle as you - I know this is a little off-topic - but I would really appreciate your response to some questions I have..

-Which version of the zydas driver are you using?
-Have you ever been able to get Dapper to work flawlessly with dchp and the 3crusb10075 ?
- Am I right to assume that your router is the 3com 3crwdr10072a?

Thanks in advance

---

### Post by Nystagmus on 2006-09-04
Just chiming in to say a big thank you for an excellent tutorial. This worked flawlessly for me using the 2.6.15-26-686 kernel with the zd1211-driver-r83.tgz. I have a Zydas dongle using the zd1211b. My previous mistake was looking up the wrong adapter (thought I had the 1201 chip), but thankfully my dongle case is translucent enough to see the chip label. Definitely helped boost my understanding of the linux kernel, drivers and modules.=D>

---

### Post by Bilko on 2006-09-04
> **regmind said:**
> Bilko, I have exactly the same dongle as you - I know this is a little off-topic - but I would really appreciate your response to some questions I have..

-Which version of the zydas driver are you using?
-Have you ever been able to get Dapper to work flawlessly with dchp and the 3crusb10075 ?
- Am I right to assume that your router is the 3com 3crwdr10072a?

Thanks in advance

I followed the steps in the howto pretty much to the letter, that's including the recommended driver (r38 ?).  Everything is working fine here, that's with dchp (well I did get a freeze after a large rsync session, but that hasn't been repeated).

And yep my router is the 10072a, with the dongle thrown in free :)

---

### Post by joerenes on 2006-09-09
> **funchords said:**
> Joe, with that in your /etc/network/interfaces -- are you using Network Manager at all, then?

This is great!

No, no network manager (that's system|admin|networking, right?). The network worked great right up to the moment I plugged in a usb tuner device.... Anyone have any thoughts on what that causes the device to stop responding?

---

### Post by yetanothername on 2006-09-09
I think I need some help. I have followed the steps in this howto, but when I issue the command: 'sudo iwconfig' I get

> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.


the output from ifconfig is

> eth0      Link encap:Ethernet  HWaddr 00:17:31:1C:3B:86
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:66 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:17:31:1C:39:92
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe1c:3992/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1547 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1456710 (1.3 MiB)  TX bytes:233520 (228.0 KiB)
          Interrupt:82

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)



I am working with a xterasys xn-3134g mini wireless lan usb adapter and have tried both the 38 and 83 drivers, with the same results.

I will post the ouput from dmesg next as it is too long for this post. Unfortunately it has a ton of stuff that means little to me - I was wondering about the bluetooth stuff. Also when I ran this command before I did see a line about zd1211 driver being registered (or something to the affect)

any help would be appreciated

cheers

---

### Post by yetanothername on 2006-09-09
This is the output from the dmesg command (sorry for the huge size)
> [QUOTE][17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009b000 (usable)
[17179569.184000]  BIOS-e820: 000000000009b000 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e9b60 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[17179569.184000]  BIOS-e820: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000007ffbe000 - 000000007ffe0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[17179569.184000] 1151MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 524208
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 294832 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fb650
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x06000606 MSFT 0x00000097) @ 0x7ffb0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x06000606 MSFT 0x00000097) @ 0x7ffb0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x06000606 MSFT 0x00000097) @ 0x7ffb0390
[17179569.184000] ACPI: MCFG (v001 A M I  OEMMCFG  0x06000606 MSFT 0x00000097) @ 0x7ffb0410
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x06000606 MSFT 0x00000097) @ 0x7ffbe040
[17179569.184000] ACPI: DSDT (v001  A0350 A0350001 0x00000001 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x508
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:6 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:6 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] ACPI: IRQ14 used by override.
[17179569.184000] ACPI: IRQ15 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 3400.462 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.756000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.756000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.832000] Memory: 2068256k/2096832k available (1976k kernel code, 27364k reserved, 606k data, 288k init, 1179328k highmem)
[17179570.832000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.912000] Calibrating delay using timer specific routine.. 6809.22 BogoMIPS (lpj=13618444)
[17179570.912000] Security Framework v1.0.0 initialized
[17179570.912000] SELinux:  Disabled at boot.
[17179570.912000] Mount-cache hash table entries: 512
[17179570.912000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e4bd 00000000 00000001
[17179570.912000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000e4bd 00000000 00000001
[17179570.912000] monitor/mwait feature present.
[17179570.912000] using mwait in idle threads.
[17179570.912000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179570.912000] CPU: L2 cache: 2048K
[17179570.912000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000080 0000e4bd 00000000 00000001
[17179570.912000] mtrr: v2.0 (20020519)
[17179570.912000] CPU: Intel(R) Pentium(R) D CPU 3.40GHz stepping 04
[17179570.912000] Enabling fast FPU save and restore... done.
[17179570.912000] Enabling unmasked SIMD FPU exception support... done.
[17179570.912000] Checking 'hlt' instruction... OK.
[17179570.928000] checking if image is initramfs... it is
[17179571.384000] Freeing initrd memory: 6841k freed
[17179571.388000] ACPI: Looking for DSDT ... not found!
[17179571.392000] ENABLING IO-APIC IRQs
[17179571.392000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179571.536000] NET: Registered protocol family 16
[17179571.536000] EISA bus registered
[17179571.536000] ACPI: bus type pci registered
[17179571.536000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=8
[17179571.536000] PCI: Using MMCONFIG
[17179571.536000] ACPI: Subsystem revision 20051216
[17179571.544000] ACPI: Interpreter enabled
[17179571.544000] ACPI: Using IOAPIC for interrupt routing
[17179571.544000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.544000] PCI: Probing PCI hardware (bus 00)
[17179571.548000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LSTA] (Node dffe4880), AE_TYPE
[17179571.548000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LATA._STA] (Node dffe4980), AE_TYPE
[17179571.548000]     ACPI-0158: *** Error: Method execution failed [\_SB_.LATA._STA] (Node dffe4980), AE_TYPE
[17179571.548000] Boot video device is 0000:01:00.0
[17179571.552000] PCI: Transparent bridge - 0000:00:12.0
[17179571.552000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.568000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[17179571.568000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
[17179571.568000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[17179571.568000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PD._PRT]
[17179571.576000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179571.576000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PE._PRT]
[17179571.576000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PF._PRT]
[17179571.580000] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *11
[17179571.580000] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *11
[17179571.580000] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *11
[17179571.580000] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *11
[17179571.580000] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *0, disabled.
[17179571.580000] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *0, disabled.
[17179571.580000] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[17179571.584000] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[17179571.584000] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[17179571.584000] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
[17179571.584000] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *3
[17179571.584000] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *11
[17179571.584000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LSTA] (Node dffe4880), AE_TYPE
[17179571.584000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LATA._STA] (Node dffe4980), AE_TYPE
[17179571.584000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.584000] pnp: PnP ACPI init
[17179571.592000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LSTA] (Node dffe4880), AE_TYPE
[17179571.592000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LATA._STA] (Node dffe4980), AE_TYPE
[17179571.592000]     ACPI-0158: *** Error: Method execution failed [\_SB_.LATA._STA] (Node dffe4980), AE_TYPE
[17179571.592000] pnp: PnP ACPI: found 17 devices
[17179571.592000] PnPBIOS: Disabled by ACPI PNP
[17179571.592000] PCI: Using ACPI for IRQ routing
[17179571.592000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.616000] pnp: 00:0e: ioport range 0xc00-0xc0f has been reserved
[17179571.616000] pnp: 00:0e: ioport range 0xd00-0xd0f has been reserved
[17179571.616000] pnp: 00:0e: ioport range 0xa20-0xa2f has been reserved
[17179571.616000] pnp: 00:0e: ioport range 0xa30-0xa3f has been reserved
[17179571.616000] PCI: Bridge: 0000:00:02.0
[17179571.616000]   IO window: b000-bfff
[17179571.616000]   MEM window: f7000000-f9cfffff
[17179571.616000]   PREFETCH window: a0000000-bfffffff
[17179571.616000] PCI: Bridge: 0000:00:04.0
[17179571.616000]   IO window: disabled.
[17179571.616000]   MEM window: disabled.
[17179571.616000]   PREFETCH window: disabled.
[17179571.616000] PCI: Bridge: 0000:00:06.0
[17179571.616000]   IO window: disabled.
[17179571.616000]   MEM window: disabled.
[17179571.616000]   PREFETCH window: disabled.
[17179571.616000] PCI: Bridge: 0000:00:07.0
[17179571.616000]   IO window: c000-cfff
[17179571.616000]   MEM window: f9d00000-f9dfffff
[17179571.616000]   PREFETCH window: disabled.
[17179571.616000] PCI: Bridge: 0000:00:12.0
[17179571.616000]   IO window: d000-dfff
[17179571.616000]   MEM window: f9e00000-f9efffff
[17179571.616000]   PREFETCH window: disabled.
[17179571.616000] PCI: Bridge: 0000:00:14.0
[17179571.616000]   IO window: disabled.
[17179571.616000]   MEM window: disabled.
[17179571.616000]   PREFETCH window: disabled.
[17179571.616000] PCI: Bridge: 0000:00:16.0
[17179571.616000]   IO window: disabled.
[17179571.616000]   MEM window: disabled.
[17179571.616000]   PREFETCH window: disabled.
[17179571.616000] PCI: Bridge: 0000:00:17.0
[17179571.616000]   IO window: e000-efff
[17179571.616000]   MEM window: f9f00000-fbffffff
[17179571.616000]   PREFETCH window: c0000000-dfffffff
[17179571.616000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179571.616000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179571.616000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179571.616000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[17179571.616000] PCI: Setting latency timer of device 0000:00:12.0 to 64
[17179571.616000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[17179571.616000] PCI: Setting latency timer of device 0000:00:16.0 to 64
[17179571.616000] PCI: Setting latency timer of device 0000:00:17.0 to 64
[17179571.620000] audit: initializing netlink socket (disabled)
[17179571.620000] audit(1157814178.620:1): initialized
[17179571.620000] highmem bounce pool size: 64 pages
[17179571.620000] VFS: Disk quotas dquot_6.5.1
[17179571.620000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.620000] Initializing Cryptographic API
[17179571.620000] io scheduler noop registered
[17179571.620000] io scheduler anticipatory registered
[17179571.620000] io scheduler deadline registered
[17179571.620000] io scheduler cfq registered
[17179571.620000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179571.620000] pcie_portdrv_probe->Dev[007e:10de] has invalid IRQ. Check vendor BIOS
[17179571.620000] assign_interrupt_mode Found MSI capability
[17179571.620000] Allocate Port Service[pcie00]
[17179571.620000] Allocate Port Service[pcie03]
[17179571.620000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179571.620000] pcie_portdrv_probe->Dev[007e:10de] has invalid IRQ. Check vendor BIOS
[17179571.620000] assign_interrupt_mode Found MSI capability
[17179571.620000] Allocate Port Service[pcie00]
[17179571.620000] Allocate Port Service[pcie03]
[17179571.620000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179571.620000] pcie_portdrv_probe->Dev[007e:10de] has invalid IRQ. Check vendor BIOS
[17179571.620000] assign_interrupt_mode Found MSI capability
[17179571.620000] Allocate Port Service[pcie00]
[17179571.620000] Allocate Port Service[pcie03]
[17179571.620000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[17179571.620000] pcie_portdrv_probe->Dev[007e:10de] has invalid IRQ. Check vendor BIOS
[17179571.620000] assign_interrupt_mode Found MSI capability
[17179571.620000] Allocate Port Service[pcie00]
[17179571.620000] Allocate Port Service[pcie03]
[17179571.620000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[17179571.620000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[17179571.620000] assign_interrupt_mode Found MSI capability
[17179571.620000] Allocate Port Service[pcie00]
[17179571.620000] Allocate Port Service[pcie03]
[17179571.620000] PCI: Setting latency timer of device 0000:00:16.0 to 64
[17179571.620000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[17179571.620000] assign_interrupt_mode Found MSI capability
[17179571.620000] Allocate Port Service[pcie00]
[17179571.620000] Allocate Port Service[pcie03]
[17179571.620000] PCI: Setting latency timer of device 0000:00:17.0 to 64
[17179571.620000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[17179571.620000] assign_interrupt_mode Found MSI capability
[17179571.620000] Allocate Port Service[pcie00]
[17179571.620000] Allocate Port Service[pcie03]
[17179571.620000] isapnp: Scanning for PnP cards...
[17179571.972000] isapnp: No Plug & Play device found
[17179571.988000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179571.988000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.988000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.988000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.988000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.992000] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.992000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.992000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.992000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.992000] mice: PS/2 mouse device common for all mice
[17179571.992000] EISA: Probing bus 0 at eisa.0
[17179571.992000] EISA: Detected 0 cards.
[17179571.992000] NET: Registered protocol family 2
[17179572.012000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.036000] IP route cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.036000] TCP established hash table entries: 524288 (order: 9, 2097152 bytes)
[17179572.036000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.036000] TCP: Hash tables configured (established 524288 bind 65536)
[17179572.036000] TCP reno registered
[17179572.036000] TCP bic registered
[17179572.036000] NET: Registered protocol family 1
[17179572.036000] NET: Registered protocol family 8
[17179572.036000] NET: Registered protocol family 20
[17179572.036000] Using IPI Shortcut mode
[17179572.036000] ACPI wakeup devices:
[17179572.036000] P0P8 P0PA P0PB P0PC P0PD PS2K PS2M UAR1 NSMB USB0 USB2 NMAC P0P1 MC97 P0PE P0PF BR10 BR11 PWRB
[17179572.036000] ACPI: (supports S0 S1 S3 S4 S5)
[17179572.036000] Freeing unused kernel memory: 288k freed
[17179572.072000] vga16fb: initializing
[17179572.072000] vga16fb: mapped to 0xc00a0000
[17179572.204000] Console: switching to colour frame buffer device 80x25
[17179572.204000] fb0: VGA16 VGA frame buffer device
[17179573.224000] Capability LSM initialized
[17179573.252000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179573.784000] SCSI subsystem initialized
[17179573.784000] ACPI: bus type scsi registered
[17179573.784000] libata version 1.20 loaded.
[17179573.784000] sata_nv 0000:00:10.0: version 0.8
[17179573.784000] **** SET: Misaligned resource pointer: dfef8502 Type 07 Len 0
[17179573.788000] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[17179573.788000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LSA0] -> GSI 23 (level, low) -> IRQ 50
[17179573.788000] PCI: Setting latency timer of device 0000:00:10.0 to 64
[17179573.788000] ata1: SATA max UDMA/133 cmd 0xA480 ctl 0xA402 bmdma 0x9C00 irq 50
[17179573.788000] ata2: SATA max UDMA/133 cmd 0xA080 ctl 0xA002 bmdma 0x9C08 irq 50
[17179574.156000] ata1: dev 0 cfg 00:045a 49:2f00 82:346b 83:7fe9 84:4773 85:3469 86:3c01 87:4763 88:407f 93:0000
[17179574.156000] ata1: dev 0 ATA-7, max UDMA/133, 488397168 sectors: LBA48
[17179574.156000] sata_get_dev_handle: SATA dev addr=0x100000, handle=0xdffe65c0
[17179574.164000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LSTA] (Node dffe4880), AE_TYPE
[17179574.164000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LATA._STA] (Node dffe4980), AE_TYPE
[17179574.164000]     ACPI-0158: *** Error: Method execution failed [\_SB_.LATA._STA] (Node dffe4980), AE_TYPE
[17179574.164000] nv_sata: Primary device added
[17179574.164000] nv_sata: Primary device removed
[17179574.164000] nv_sata: Secondary device added
[17179574.164000] nv_sata: Secondary device removed
[17179574.164000] ata1: dev 0 configured for UDMA/133
[17179574.164000] sata_get_dev_handle: SATA dev addr=0x100000, handle=0xdffe65c0
[17179574.172000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LSTA] (Node dffe4880), AE_TYPE
[17179574.172000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LATA._STA] (Node dffe4980), AE_TYPE
[17179574.172000]     ACPI-0158: *** Error: Method execution failed [\_SB_.LATA._STA] (Node dffe4980), AE_TYPE
[17179574.172000] scsi0 : sata_nv
[17179574.376000] ata2: no device found (phy stat 00000000)
[17179574.376000] scsi1 : sata_nv
[17179574.376000]   Vendor: ATA       Model: HDT722525DLA380   Rev: V44O
[17179574.376000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179574.376000] **** SET: Misaligned resource pointer: dfef8302 Type 07 Len 0
[17179574.376000] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
[17179574.376000] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LSA1] -> GSI 22 (level, low) -> IRQ 58
[17179574.376000] PCI: Setting latency timer of device 0000:00:11.0 to 64
[17179574.376000] ata3: SATA max UDMA/133 cmd 0x9880 ctl 0x9802 bmdma 0x9080 irq 58
[17179574.376000] ata4: SATA max UDMA/133 cmd 0x9480 ctl 0x9402 bmdma 0x9088 irq 58
[17179574.380000] Driver 'sd' needs updating - please use bus_type methods
[17179574.380000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179574.380000] SCSI device sda: drive cache: write back
[17179574.380000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179574.380000] SCSI device sda: drive cache: write back
[17179574.380000]  sda: sda1 sda2 sda3
[17179574.412000] sd 0:0:0:0: Attached scsi disk sda
[17179574.760000] ata3: dev 0 cfg 00:045a 49:2f00 82:346b 83:7fe9 84:4773 85:3469 86:3c01 87:4763 88:407f 93:0000
[17179574.760000] ata3: dev 0 ATA-7, max UDMA/133, 488397168 sectors: LBA48
[17179574.760000] sata_get_dev_handle: SATA dev addr=0x110000, handle=0xdffe6360
[17179574.768000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LSTA] (Node dffe4880), AE_TYPE
[17179574.768000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LATA._STA] (Node dffe4980), AE_TYPE
[17179574.768000]     ACPI-0158: *** Error: Method execution failed [\_SB_.LATA._STA] (Node dffe4980), AE_TYPE
[17179574.768000] nv_sata: Primary device added
[17179574.768000] nv_sata: Primary device removed
[17179574.768000] nv_sata: Secondary device added
[17179574.768000] nv_sata: Secondary device removed
[17179574.768000] ata3: dev 0 configured for UDMA/133
[17179574.768000] sata_get_dev_handle: SATA dev addr=0x110000, handle=0xdffe6360
[17179574.776000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LSTA] (Node dffe4880), AE_TYPE
[17179574.776000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LATA._STA] (Node dffe4980), AE_TYPE
[17179574.776000]     ACPI-0158: *** Error: Method execution failed [\_SB_.LATA._STA] (Node dffe4980), AE_TYPE
[17179574.776000] scsi2 : sata_nv
[17179574.980000] ata4: no device found (phy stat 00000000)
[17179574.980000] scsi3 : sata_nv
[17179574.980000]   Vendor: ATA       Model: HDT722525DLA380   Rev: V44O
[17179574.980000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179574.980000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[17179574.980000] SCSI device sdb: drive cache: write back
[17179574.980000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[17179574.980000] SCSI device sdb: drive cache: write back
[17179574.980000]  sdb:<4>nv_sata: Primary device added
[17179574.992000] nv_sata: Primary device removed
[17179574.992000] nv_sata: Secondary device added
[17179574.992000] nv_sata: Secondary device removed
[17179574.992000]  sdb1 sdb2
[17179574.992000] sd 2:0:0:0: Attached scsi disk sdb
[17179574.996000] NFORCE-CK804: IDE controller at PCI slot 0000:00:0f.0
[17179574.996000] NFORCE-CK804: chipset revision 243
[17179574.996000] NFORCE-CK804: not 100% native mode: will probe irqs later
[17179574.996000] NFORCE-CK804: BIOS didn't set cable bits correctly. Enabling workaround.
[17179574.996000] NFORCE-CK804: 0000:00:0f.0 (rev f3) UDMA133 controller
[17179574.996000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:pio, hdb:pio
[17179574.996000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[17179574.996000] Probing IDE interface ide0...
[17179575.564000] Probing IDE interface ide1...
[17179576.300000] hdc: SONY DVD RW DW-Q120A, ATAPI CD/DVD-ROM drive
[17179576.972000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.992000] hdc: ATAPI 126X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[17179576.992000] Uniform CD-ROM driver Revision: 3.20
[17179577.100000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179577.100000] **** SET: Misaligned resource pointer: dfbc7ac2 Type 07 Len 0
[17179577.100000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[17179577.100000] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LMAC] -> GSI 21 (level, low) -> IRQ 66
[17179577.100000] PCI: Setting latency timer of device 0000:00:13.0 to 64
[17179577.100000] forcedeth: using HIGHDMA
[17179577.128000] ieee1394: Initialized config rom entry `ip1394'
[17179577.620000] eth0: forcedeth.c: subsystem: 01043:81d3 bound to 0000:00:13.0
[17179577.620000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179577.620000] **** SET: Misaligned resource pointer: dfbc78c2 Type 07 Len 0
[17179577.620000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 19
[17179577.620000] ACPI: PCI Interrupt 0000:05:0b.0[A] -> Link [LNKC] -> GSI 19 (level, low) -> IRQ 74
[17179577.668000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[74]  MMIO=[f9eff800-f9efffff]  Max Packet=[2048]
[17179577.684000] Probing IDE interface ide0...
[17179578.280000] Attempting manual resume
[17179578.304000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.316000] kjournald starting.  Commit interval 5 seconds
[17179578.940000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000a24dd9]
[17179587.028000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179587.028000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[17179587.056000] eth0: no link during initialization.
[17179587.680000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179587.680000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179587.948000] **** SET: Misaligned resource pointer: f7d59a02 Type 07 Len 0
[17179587.948000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 18
[17179587.948000] ACPI: PCI Interrupt 0000:04:00.0[A] -> Link [LNKD] -> GSI 18 (level, low) -> IRQ 82
[17179587.948000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[17179587.948000] sky2 v1.4 addr 0xf9dfc000 irq 82 Yukon-EC (0xb6) rev 2
[17179587.948000] sky2 eth1: addr 00:17:31:1c:39:92
[17179588.092000] NET: Registered protocol family 17
[17179588.156000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.164000] nvidia: module license 'NVIDIA' taints kernel.
[17179588.168000] **** SET: Misaligned resource pointer: f7d59a02 Type 07 Len 0
[17179588.168000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 17
[17179588.168000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 17 (level, low) -> IRQ 98
[17179588.168000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[17179588.168000] PCI: Enabling device 0000:08:00.0 (0000 -> 0003)
[17179588.168000] **** SET: Misaligned resource pointer: f7d59a02 Type 07 Len 0
[17179588.168000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 16
[17179588.168000] ACPI: PCI Interrupt 0000:08:00.0[A] -> Link [LNKB] -> GSI 16 (level, low) -> IRQ 106
[17179588.168000] PCI: Setting latency timer of device 0000:08:00.0 to 64
[17179588.168000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179588.248000] Real Time Clock Driver v1.12
[17179588.428000] input: PC Speaker as /class/input/input1
[17179588.704000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x600
[17179588.704000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x700
[17179588.756000] Floppy drive(s): fd0 is 1.44M
[17179588.772000] FDC 0 is a post-1991 82077
[17179588.832000] sky2 eth1: enabling interface
[17179588.896000] logips2pp: Detected unknown logitech mouse model 85
[17179588.924000] ACPI: PCI Interrupt 0000:05:07.0[A] -> Link [LNKB] -> GSI 16 (level, low) -> IRQ 106
[17179588.928000] Audigy2 value: Special config.
[17179589.376000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[17179589.472000] parport: PnPBIOS parport detected.
[17179589.472000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179589.480000] parport0: Legacy device
[17179589.812000] ts: Compaq touchscreen protocol output
[17179590.184000] lp0: using parport0 (interrupt-driven).
[17179590.208000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179590.208000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179590.208000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179590.260000] fuse init (API version 7.3)
[17179590.292000] Adding 2305316k swap on /dev/sda3.  Priority:-1 extents:1 across:2305316k
[17179590.424000] EXT3 FS on sda2, internal journal
[17179590.536000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179590.536000] md: bitmap version 4.39
[17179590.636000] sky2 eth1: Link is up at 100 Mbps, full duplex, flow control both
[17179590.936000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179593.652000] NET: Registered protocol family 10
[17179593.652000] lo: Disabled Privacy Extensions
[17179593.652000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179593.652000] IPv6 over IPv4 tunneling driver
[17179593.736000] kjournald starting.  Commit interval 5 seconds
[17179593.736000] EXT3 FS on sdb1, internal journal
[17179593.736000] EXT3-fs: mounted filesystem with ordered data mode.
[17179597.952000] ACPI: Power Button (FF) [PWRF]
[17179597.952000] ACPI: Power Button (CM) [PWRB]
[17179597.968000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LSTA] (Node dffe4880), AE_TYPE
[17179597.968000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LATA._STA] (Node dffe4980), AE_TYPE
[17179597.968000]     ACPI-0158: *** Error: Method execution failed [\_SB_.LATA._STA] (Node dffe4980), AE_TYPE
[17179598.020000] ibm_acpi: ec object not found
[17179598.048000] pcc_acpi: loading...
[17179602.828000] ppdev: user-space parallel port driver
[17179603.104000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179603.108000] apm: overridden by ACPI.
[17179603.924000] eth1: no IPv6 routers present
[17179606.784000] Bluetooth: Core ver 2.8
[17179606.784000] NET: Registered protocol family 31
[17179606.784000] Bluetooth: HCI device and connection manager initialized
[17179606.784000] Bluetooth: HCI socket layer initialized
[17179606.820000] Bluetooth: L2CAP ver 2.8
[17179606.820000] Bluetooth: L2CAP socket layer initialized
[17179606.824000] Bluetooth: RFCOMM socket layer initialized
[17179606.824000] Bluetooth: RFCOMM TTY layer initialized
[17179606.824000] Bluetooth: RFCOMM ver 1.7
[17179716.376000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17179716.472000] ISOFS: changing to secondary root
[/QUOTE]

---

### Post by funchords on 2006-09-09
yetanothername: 

It's what I'm not seeing that might be the problem.  I don't know how to fix it, but hopefully, it's a lead...

I don't see your USB ports being initialized.  Here is the output of my dmesg, showing the type of messages that you might see when the USB ports are waking up...

```

[17179579.316000] usbcore: registered new driver usbfs
[17179579.316000] usbcore: registered new driver hub
[17179579.320000] USB Universal Host Controller Interface driver v2.3
[17179579.320000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179579.320000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179579.320000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179579.320000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179579.320000] uhci_hcd 0000:00:1d.0: irq 169, io base 0x0000d800
[17179579.320000] hub 1-0:1.0: USB hub found
[17179579.320000] hub 1-0:1.0: 2 ports detected
[17179579.424000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 185
[17179579.424000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179579.424000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179579.424000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179579.424000] uhci_hcd 0000:00:1d.1: irq 185, io base 0x0000d000
[17179579.424000] hub 2-0:1.0: USB hub found
[17179579.424000] hub 2-0:1.0: 2 ports detected
[17179579.528000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 177
[17179579.528000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179579.528000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179579.528000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179579.528000] uhci_hcd 0000:00:1d.2: irq 177, io base 0x0000d400
[17179579.528000] hub 3-0:1.0: USB hub found
[17179579.528000] hub 3-0:1.0: 2 ports detected
[17179579.636000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 193
[17179579.636000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179579.636000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179579.636000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179579.636000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179579.636000] ehci_hcd 0000:00:1d.7: irq 193, io mem 0xea880000
[17179579.640000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.640000] hub 4-0:1.0: USB hub found
[17179579.640000] hub 4-0:1.0: 6 ports detected
[17179579.664000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179579.840000] Attempting manual resume
[17179579.860000] kjournald starting.  Commit interval 5 seconds
[17179579.860000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.776000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[17179581.152000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[17179581.540000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[17179585.428000] NET: Registered protocol family 10
[17179585.428000] lo: Disabled Privacy Extensions
[17179585.428000] IPv6 over IPv4 tunneling driver
[17179649.384000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0113
[17179649.384000] usbcore: registered new driver usblp
[17179649.384000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver

```

---

### Post by yetanothername on 2006-09-10
Thanks for the input.

Hmmmm, I wonder if it was because I disabled legacy USB support in the BIOS to install Ubuntu, though I would have thought that that would only be older USB 1.x stuff.

I will do a search for USB initialisation information tomorrow (it's 1:30am at the moment)

cheers

---

### Post by deldredge on 2006-09-22
Holy crap I've been trying for a week to get this to work. I've even reinstalled so that I have a completely default dapper installation to work with. My kernel is 2.5.15-26-386. My wireless dongle is Zonet zew2501 which uses the 1211b driver. I installed the 38 driver but i've tried just about every one on the site. This is my dmesg output, which is missing something I think - it doesn't look like it's seeing the dongle at all?

```
dan@dan-desktop:~/Desktop/zd1211-driver-r38$ dmesg
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e6c00 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 00000000040fd800 (usable)
[17179569.184000]  BIOS-e820: 00000000040fd800 - 00000000040ff800 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000040ff800 - 00000000040ffc00 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000040ffc00 - 0000000020000000 (usable)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 512MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 131072
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126976 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.1 present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6bc0
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x00000001 PTL  0x01000000) @ 0x040fdbcb
[17179569.184000] ACPI: FADT (v001 DELL   KUBLAI   0x20000208 PTL  0x000f4240) @ 0x040ff78c
[17179569.184000] ACPI: DSDT (v001  Intel  S2440BX 0x00000001 MSFT 0x01000004) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01402000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 598.723 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.464000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.468000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179570.536000] Memory: 508596k/524288k available (1976k kernel code, 15064k reserved, 606k data, 288k init, 0k highmem)
[17179570.536000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.616000] Calibrating delay using timer specific routine.. 1198.37 BogoMIPS (lpj=2396749)
[17179570.616000] Security Framework v1.0.0 initialized
[17179570.616000] SELinux:  Disabled at boot.
[17179570.616000] Mount-cache hash table entries: 512
[17179570.616000] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.616000] CPU: After vendor identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.616000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179570.616000] CPU: L2 cache: 256K
[17179570.616000] CPU serial number disabled.
[17179570.616000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179570.616000] mtrr: v2.0 (20020519)
[17179570.616000] CPU: Intel Pentium III (Coppermine) stepping 01
[17179570.616000] Enabling fast FPU save and restore... done.
[17179570.616000] Enabling unmasked SIMD FPU exception support... done.
[17179570.616000] Checking 'hlt' instruction... OK.
[17179570.632000] checking if image is initramfs... it is
[17179573.236000] Freeing initrd memory: 6841k freed
[17179573.276000] ACPI: Looking for DSDT ... not found!
[17179573.280000] ACPI: setting ELCR to 0200 (from 0e00)
[17179573.280000] NET: Registered protocol family 16
[17179573.280000] EISA bus registered
[17179573.280000] ACPI: bus type pci registered
[17179573.280000] PCI: PCI BIOS revision 2.10 entry at 0xfd993, last bus=1
[17179573.280000] PCI: Using configuration type 1
[17179573.284000] ACPI: Subsystem revision 20051216
[17179573.284000] ACPI: Interpreter enabled
[17179573.284000] ACPI: Using PIC for interrupt routing
[17179573.288000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.288000] PCI: Probing PCI hardware (bus 00)
[17179573.288000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179573.292000] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[17179573.292000] PCI quirk: region 7000-700f claimed by PIIX4 SMB
[17179573.292000] Boot video device is 0000:01:00.0
[17179573.292000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.296000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[17179573.296000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[17179573.296000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[17179573.300000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
[17179573.300000] ACPI: Power Resource [PFAN] (on)
[17179573.304000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.304000] pnp: PnP ACPI init
[17179573.312000] pnp: PnP ACPI: found 11 devices
[17179573.312000] PnPBIOS: Disabled by ACPI PNP
[17179573.312000] PCI: Using ACPI for IRQ routing
[17179573.312000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.312000] pnp: 00:00: ioport range 0x7000-0x700f has been reserved
[17179573.312000] pnp: 00:00: ioport range 0x8000-0x803f could not be reserved
[17179573.312000] PCI: Failed to allocate mem resource #6:10000@fe000000 for 0000:01:00.0
[17179573.312000] PCI: Bridge: 0000:00:01.0
[17179573.312000]   IO window: disabled.
[17179573.312000]   MEM window: f5000000-f5ffffff
[17179573.312000]   PREFETCH window: fc000000-fdffffff
[17179573.316000] audit: initializing netlink socket (disabled)
[17179573.316000] audit(1158950543.316:1): initialized
[17179573.316000] VFS: Disk quotas dquot_6.5.1
[17179573.316000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.316000] Initializing Cryptographic API
[17179573.316000] io scheduler noop registered
[17179573.316000] io scheduler anticipatory registered
[17179573.316000] io scheduler deadline registered
[17179573.316000] io scheduler cfq registered
[17179573.316000] Limiting direct PCI/PCI transfers.
[17179573.316000] isapnp: Scanning for PnP cards...
[17179573.672000] isapnp: No Plug & Play device found
[17179573.720000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MICE] at 0x60,0x64 irq 1,12
[17179573.732000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.732000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.732000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.736000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.740000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.744000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.744000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.744000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.744000] mice: PS/2 mouse device common for all mice
[17179573.744000] EISA: Probing bus 0 at eisa.0
[17179573.744000] Cannot allocate resource for EISA slot 1
[17179573.744000] Cannot allocate resource for EISA slot 7
[17179573.744000] Cannot allocate resource for EISA slot 8
[17179573.744000] EISA: Detected 0 cards.
[17179573.744000] NET: Registered protocol family 2
[17179573.784000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.784000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.788000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.788000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.788000] TCP: Hash tables configured (established 131072 bind 65536)
[17179573.788000] TCP reno registered
[17179573.788000] TCP bic registered
[17179573.788000] NET: Registered protocol family 1
[17179573.788000] NET: Registered protocol family 8
[17179573.788000] NET: Registered protocol family 20
[17179573.788000] Using IPI Shortcut mode
[17179573.792000] ACPI wakeup devices:
[17179573.792000] PCI0 USB0 UAR1  KBC MICE
[17179573.792000] ACPI: (supports S0 S1 S5)
[17179573.792000] Freeing unused kernel memory: 288k freed
[17179573.948000] vga16fb: initializing
[17179573.948000] vga16fb: mapped to 0xc00a0000
[17179574.084000] Console: switching to colour frame buffer device 80x25
[17179574.084000] fb0: VGA16 VGA frame buffer device
[17179575.272000] Capability LSM initialized
[17179575.360000] ACPI: Fan [FAN1] (on)
[17179575.372000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179576.720000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[17179576.720000] PIIX4: chipset revision 1
[17179576.720000] PIIX4: not 100% native mode: will probe irqs later
[17179576.720000]     ide0: BM-DMA at 0x10e0-0x10e7, BIOS settings: hda:DMA, hdb:pio
[17179576.720000]     ide1: BM-DMA at 0x10e8-0x10ef, BIOS settings: hdc:DMA, hdd:pio
[17179576.720000] Probing IDE interface ide0...
[17179577.008000] hda: Maxtor 52049U4, ATA DISK drive
[17179577.680000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.680000] Probing IDE interface ide1...
[17179578.080000] hdc: SAMSUNG CD-ROM SC-148F, ATAPI CD/DVD-ROM drive
[17179578.864000] hdd: IOMEGA ZIP 100 ATAPI, ATAPI FLOPPY drive
[17179578.920000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.940000] hda: max request size: 128KiB
[17179578.980000] hda: 39882528 sectors (20419 MB) w/2048KiB Cache, CHS=39566/16/63, UDMA(33)
[17179578.980000] hda: cache flushes not supported
[17179578.980000]  hda: hda1 hda2 < hda5 >
[17179579.012000] hdc: ATAPI 48X CD-ROM drive, 128kB Cache, UDMA(33)
[17179579.012000] Uniform CD-ROM driver Revision: 3.20
[17179579.360000] usbcore: registered new driver usbfs
[17179579.360000] usbcore: registered new driver hub
[17179579.368000] USB Universal Host Controller Interface driver v2.3
[17179579.368000] **** SET: Misaligned resource pointer: c3c385e2 Type 07 Len 0
[17179579.368000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[17179579.368000] PCI: setting IRQ 9 as level-triggered
[17179579.368000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[17179579.368000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[17179579.372000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[17179579.372000] uhci_hcd 0000:00:07.2: irq 9, io base 0x000010c0
[17179579.372000] hub 1-0:1.0: USB hub found
[17179579.372000] hub 1-0:1.0: 2 ports detected
[17179579.584000] Attempting manual resume
[17179579.636000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.664000] kjournald starting.  Commit interval 5 seconds
[17179579.716000] usb 1-2: new low speed USB device using uhci_hcd and address 2[17179595.892000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179595.916000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179595.944000] Linux agpgart interface v0.101 (c) Dave Jones
[17179595.948000] agpgart: Detected an Intel 440BX Chipset.
[17179595.952000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179595.988000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[17179597.216000] logips2pp: Detected unknown logitech mouse model 0
[17179597.244000] **** SET: Misaligned resource pointer: c3cc0502 Type 07 Len 0
[17179597.244000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179597.244000] PCI: setting IRQ 11 as level-triggered
[17179597.244000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179597.244000] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[17179597.244000] 0000:00:0d.0: 3Com PCI 3c905C Tornado at e08c2000. Vers LK1.1.19
[17179597.536000] nvidia: module license 'NVIDIA' taints kernel.
[17179597.552000] NVRM: The NVIDIA RIVA TNT2 Model 64/Model 64 Pro GPU installed in this system is
[17179597.552000] NVRM:  supported through the NVIDIA Legacy drivers. Please
[17179597.552000] NVRM:  visit http://www.nvidia.com/object/unix.html for more
[17179597.552000] NVRM:  information.  The 1.0-8762 NVIDIA driver will ignore
[17179597.552000] NVRM:  this GPU.  Continuing probe...
[17179597.552000] NVRM: No NVIDIA graphics adapter found!
[17179597.640000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input1
[17179597.732000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179597.732000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
[17179597.948000] ide-floppy driver 0.99.newide
[17179598.148000] hdd: No disk in drive
[17179598.192000] input: PC Speaker as /class/input/input2
[17179598.196000] Real Time Clock Driver v1.12
[17179598.196000] hdd: 98304kB, 96/64/32 CHS, 4096 kBps, 512 sector size, 2941 rpm
[17179598.268000] parport: PnPBIOS parport detected.
[17179598.268000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[17179598.300000] usbcore: registered new driver hiddev
[17179598.328000] input: Dell Dell USB Keyboard as /class/input/input3
[17179598.328000] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:07.2-2
[17179598.328000] usbcore: registered new driver usbhid
[17179598.328000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179598.388000] **** SET: Misaligned resource pointer: dce8f6c2 Type 07 Len 0
[17179598.392000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[17179598.392000] PCI: setting IRQ 10 as level-triggered
[17179598.392000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179598.876000] Floppy drive(s): fd0 is 1.44M
[17179598.892000] FDC 0 is a post-1991 82077
[17179599.260000] hdd: No disk in drive
[17179599.636000] ts: Compaq touchscreen protocol output
[17179600.024000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179600.196000] hdd: No disk in drive
[17179601.104000] NET: Registered protocol family 17
[17179601.212000] lp0: using parport0 (interrupt-driven).
[17179601.376000] Adding 843372k swap on /dev/hda5.  Priority:-1 extents:1 across:843372k
[17179601.544000] EXT3 FS on hda1, internal journal
[17179601.924000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179601.924000] md: bitmap version 4.39
[17179602.736000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179603.536000] hdd: No disk in drive
[17179604.044000] cdrom: open failed.
[17179604.512000] NET: Registered protocol family 10
[17179604.512000] lo: Disabled Privacy Extensions
[17179604.512000] IPv6 over IPv4 tunneling driver
[17179612.472000] ACPI: Power Button (FF) [PWRF]
[17179612.772000] ibm_acpi: ec object not found
[17179612.840000] pcc_acpi: loading...
[17179615.220000] eth0: no IPv6 routers present
[17179621.472000] ppdev: user-space parallel port driver
[17179621.852000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179621.856000] apm: overridden by ACPI.
[17179627.608000] Bluetooth: Core ver 2.8
[17179627.608000] NET: Registered protocol family 31
[17179627.608000] Bluetooth: HCI device and connection manager initialized
[17179627.608000] Bluetooth: HCI socket layer initialized
[17179627.652000] Bluetooth: L2CAP ver 2.8
[17179627.652000] Bluetooth: L2CAP socket layer initialized
[17179627.692000] Bluetooth: RFCOMM socket layer initialized
[17179627.692000] Bluetooth: RFCOMM TTY layer initialized
[17179627.692000] Bluetooth: RFCOMM ver 1.7
[17182080.432000]
[17182080.432000]  _____     ____    _    ____
[17182080.432000] |__  /   _|  _ \  / \  / ___|
[17182080.432000]   / / | | | | | |/ _ \ \___ \
[17182080.432000]  / /| |_| | |_| / ___ \ ___) |
[17182080.432000] /____\__, |____/_/   \_\____/
[17182080.436000]      |___/
[17182080.436000] ZD1211B - version 2.0.0.0
[17182080.436000] usbcore: registered new driver zd1211b
dan@dan-desktop:~/Desktop/zd1211-driver-r38$
```

please help, I'm ready to throw my computer out the window.

---

### Post by marra on 2006-09-28
Hi all!

this tutorial is really clear and well written. thankyou all!

But..
After a lot of work there is still something wrong.

My card (3comusb10075) should work properly since I can see my accesspoint.

briefly now my problem is this:
```

ioctl[SIOCSIWAP]: Operation not supported
wpa_driver_zydas_init: failed to set wpa_supplicant-based roaming

```

I suppose the error is in the driver.
I've expeimented different (r38 r83) driver releases getting different errors.
This one seem to achieve the best result (deb package zd1211-source)

what's wrong? :-k

thanks,
stefano


here the complete dump follows:
```

root@athlon:/usr/src/wpa_supplicant-0.4.7_zydas# ./wpa_supplicant  -i wlan1 -c /etc/wpa_supplicant.conf -D zydas -ddd
Initializing interface 'wlan1' conf '/etc/wpa_supplicant.conf' driver 'zydas' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=4):
     66 72 65 64                                       fred
scan_ssid=1 (0x1)
pairwise: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=9): [REMOVED]
key_mgmt: 0x2
proto: 0x1
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 8: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='fred'
Initializing interface (2) 'wlan1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=13 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
Own MAC address: 00:14:7c:67:28:76
wpa_driver_zydas_set_key: alg=NONE key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_zydas_set_key: alg=NONE key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_zydas_set_key: alg=NONE key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_zydas_set_key: alg=NONE key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_zydas_set_countermeasures: enabled=0
wpa_driver_zydas_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Added interface wlan1
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=4):
     66 72 65 64                                       fred
Scan timeout - try to get results
Received 284 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:14:7c:b7:75:44 ssid='fred' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:14:7c:b7:75:44 (SSID='fred' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_zydas_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
wpa_driver_zydas_associate
wpa_supplicant initiates scan and AP selection

ioctl[SIOCSIWAP]: Operation not supported
Association request to the driver failed
Setting authentication timeout: 10 sec 0 usec

...
...


```

---

### Post by guyjohnston on 2006-10-19
Hi, I've finally managed to get my card with the zd1211b chipset working with WPA, by using KNetworkManager (I usually use KDE/Kubuntu). I'm using the 2.6.15-26-amd64-generic kernel, and the r83 version of the driver from [http://zd1211.ath.cx/](http://zd1211.ath.cx/). It usually takes a while to get it to connect, but it seems pretty stable once that's worked. Before I installed KNetworkManager, I could sometimes get onto an unencrypted network, but the connection kept stopping. I assume the GNOME frontend for network-manager would do exactly the same thing. Incidentally, network-manager uses the standard wpasupplicant package supplied with Ubuntu and it seems to work without going through the steps for WPA explained in this guide.

---

### Post by G_Dem on 2006-10-20
Brilliant tutorial and finally after much headache I got my wireless to work. Previously I tried using my linksys card which wouldnt work with ndiswrapper but after Buying a Zyxel USB and with help from your tutorial I've got it to work. However, when WEP is enabled and after configuring the WEP key in the network tools the system sort of hangs. I can still move the mouse and click on things but after clicking on something it attempts to run the program and then stops. Also I cant shutdown the pc.

I get none of these probs when WEP is disabled though.

Any Ideas?

---

### Post by Chomsty on 2006-11-10
Thanks for this helpful tutorial. It seems like all of you got your WLAN to work. But not so for me. I tried the driver from [http://www.zydas.com.tw](http://www.zydas.com.tw) as well as the latest driver from [http://zd1211.ath.cx](http://zd1211.ath.cx). With both of them I manage the steps 1-11. But after plugging in my ZyXEL ZyAIR G-220, the dmesg shows
(with driver from [http://www.zydas.com.tw](http://www.zydas.com.tw))
[17182676.396000]  _____     ____    _    ____
[17182676.396000] |__  /   _|  _ \  / \  / ___|
[17182676.396000]   / / | | | | | |/ _ \ \___ \
[17182676.396000]  / /| |_| | |_| / ___ \ ___) |
[17182676.396000] /____\__, |____/_/   \_\____/
[17182676.396000]      |___/
[17182676.396000] zd1211 - version 2.5.0.0
[17182676.424000] usbcore: registered new driver zd1211
.....
[17182703.324000] Region:48
[17182703.728000] zd1205: (exit) zd1205_config, /usr/src/ZD1211LnxDrv_2_6_0_0/src/zd1205.c line 2493
[17182703.728000] zd1205: (exit) zd1205_init, /usr/src/ZD1211LnxDrv_2_6_0_0/src/zd1205.c line 7977

(with driver from [http://zd1211.ath.cx](http://zd1211.ath.cx))
[17184382.544000] zd1211 - [http://zd1211.ath.cx/](http://zd1211.ath.cx/) - r83
[17184382.544000] Based on [www.zydas.com.tw](www.zydas.com.tw) driver version 2.5.0.0
[17184382.544000] usbcore: registered new driver zd1211
...
[17184403.048000] Region:48
[17184403.452000] zd1205: (exit) zd1205_config, /usr/src/zd1211-driver-r83/src/zd1205.c line 2601
[17184403.452000] zd1205: (exit) zd1205_init, /usr/src/zd1211-driver-r83/src/zd1205.c line 8570

I checked the corresponding code in zd1205.c, but didn't understand what's going on there :confused:. Does anybody have any ideas or suggestions?
Thanks for all comments.
PS: I'm using Edgy with the Kernel 2.6.17-10-386.

---

### Post by firemaker on 2006-11-21
I am realy desperate trying to get wireless working on my Ibook.
I am using ubuntu and followed the instructions here step by step the model of USB Dongle i am using is the WL-430U (zd1211b).
I installed Zydas but still no connection to the router and iwconfig shows no wireless extentions please help me out here.
Here is what I get when I exec dsmeg:
[  205.668537] 
[  205.668561]  _____     ____    _    ____
[  205.668569] |__  /   _|  _ \  / \  / ___|
[  205.668577]   / / | | | | | |/ _ \ \___ \
[  205.668585]  / /| |_| | |_| / ___ \ ___) |
[  205.668593] /____\__, |____/_/   \_\____/
[  205.668601]      |___/
[  205.668609] ZD1211B - version 2.5.0.0
[  205.674047] Release Ver = 1048
[  205.674072] zd1211:bulk out: wMaxPacketSize = 4000
[  205.674083] zd1211:bulk in: wMaxPacketSize = 4000
[  205.674093] zd1211:interrupt in: wMaxPacketSize = 4000
[  205.674103] zd1211:interrupt in: int_interval = 1
[  205.674113] zd1211:bulk out: wMaxPacketSize = 4000
[  205.677248] EEPORM Ver = 4810
[  205.677259] zd1211:macp->release != EEPVer
[  205.696364] zd1211:USB Download Boot code success
[  236.326410] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  313.699404] eth1: Link is up at 100 Mbps, full-duplex.
[  313.699429] eth1: Pause is disabled
[  313.700059] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  324.623157] eth1: no IPv6 routers present
[  455.946056] zd1211: usb_control_msg 2 fail: FFFFFF92
[  455.946088] zd1211_Download_IncludeFile failed
[  455.946112] zd1211b: probe of 2-1:1.0 failed with error -5
[  455.946156] usbcore: registered new driver zd1211b
[  489.829694] usb 2-1: USB disconnect, address 6
[  511.751526] ohci_hcd 0001:10:18.0: wakeup
[  512.133332] usb 1-1: new full speed USB device using ohci_hcd and address 2
[  512.340562] usb 1-1: configuration #1 chosen from 1 choice
[  512.342704] Release Ver = 1048
[  512.342721] zd1211:bulk out: wMaxPacketSize = 4000
[  512.342732] zd1211:bulk in: wMaxPacketSize = 4000
[  512.342742] zd1211:interrupt in: wMaxPacketSize = 4000
[  512.342752] zd1211:interrupt in: int_interval = 1
[  512.342762] zd1211:bulk out: wMaxPacketSize = 4000
[  512.342778] EEPORM Ver = 4810
[  512.342785] zd1211:macp->release != EEPVer
[  512.358347] zd1211:USB Download Boot code success
[  531.001191] zd1211: usb_control_msg 2 fail: FFFFFF92
[  531.001222] zd1211_Download_IncludeFile failed
[  531.001246] zd1211b: probe of 1-1:1.0 failed with error -5
[  531.001637] usb 1-1: USB disconnect, address 2
[  542.858878] eth1: Link is up at 100 Mbps, full-duplex.
[  542.858912] eth1: Pause is disabled
[  553.596906] eth1: no IPv6 routers present
[  944.353393] zd1211 - [http://zd1211.ath.cx/](http://zd1211.ath.cx/) - r83
[  944.353419] Based on [www.zydas.com.tw](www.zydas.com.tw) driver version 2.5.0.0
[  944.356399] usbcore: registered new driver zd1211
[  968.002674] ohci_hcd 0001:10:18.0: wakeup
[  968.384830] usb 1-1: new full speed USB device using ohci_hcd and address 3
[  968.592099] usb 1-1: configuration #1 chosen from 1 choice
[  968.594162] Release Ver = 1048
[  968.594177] zd1211:bulk out: wMaxPacketSize = 4000
[  968.594189] zd1211:bulk in: wMaxPacketSize = 4000
[  968.594199] zd1211:interrupt in: wMaxPacketSize = 4000
[  968.594209] zd1211:interrupt in: int_interval = 1
[  968.594218] zd1211:bulk out: wMaxPacketSize = 4000
[  968.594235] EEPORM Ver = 4810
[  968.594243] zd1211:macp->release != EEPVer
[  968.609852] zd1211:USB Download Boot code success
[ 1186.909962] usbcore: deregistering driver zd1211b
[ 1194.029775] zd1211: usb_control_msg 2 fail: FFFFFF92
[ 1194.029807] zd1211_Download_IncludeFile failed
[ 1194.029833] zd1211b: probe of 1-1:1.0 failed with error -5
[ 1194.122737] usb 1-1: USB disconnect, address 3
[ 1220.053980] ohci_hcd 0001:10:18.0: wakeup
[ 1220.434342] usb 1-1: new full speed USB device using ohci_hcd and address 4
[ 1220.641588] usb 1-1: configuration #1 chosen from 1 choice
[ 1221.233623] 
[ 1221.233648]  _____     ____    _    ____
[ 1221.233656] |__  /   _|  _ \  / \  / ___|
[ 1221.233664]   / / | | | | | |/ _ \ \___ \
[ 1221.233673]  / /| |_| | |_| / ___ \ ___) |
[ 1221.233681] /____\__, |____/_/   \_\____/
[ 1221.233688]      |___/
[ 1221.233697] ZD1211B - version 2.5.0.0
[ 1221.239738] Release Ver = 1048
[ 1221.239760] zd1211:bulk out: wMaxPacketSize = 4000
[ 1221.239771] zd1211:bulk in: wMaxPacketSize = 4000
[ 1221.239781] zd1211:interrupt in: wMaxPacketSize = 4000
[ 1221.239792] zd1211:interrupt in: int_interval = 1
[ 1221.239801] zd1211:bulk out: wMaxPacketSize = 4000
[ 1221.243046] EEPORM Ver = 4810
[ 1221.243059] zd1211:macp->release != EEPVer
[ 1221.261337] zd1211:USB Download Boot code success



Thanks for any advice

---

### Post by firemaker on 2006-11-24
Ok, managed to get the driver going but I don´t get higher bitrate than 11mb/s can´t I get more?
:confused:

---

### Post by lite on 2006-12-26
The patched wpa_supplicant was pretty tricky to find from the website because the site is broken.
Here is the exact url:

[http://www.atheros.com/RD/ZyDAS/web_driver/ZD1211B/Linux/wpa_supplicant-0.4.7_zydas.tar.gz](http://www.atheros.com/RD/ZyDAS/web_driver/ZD1211B/Linux/wpa_supplicant-0.4.7_zydas.tar.gz)

---

### Post by frenzy05 on 2007-02-16
I can't get my one  it work at all. It the wifimax pack (zd1211). I'm running Ubuntu 6.10 the Edgy Eft,  2.6.17-11-generic. Can someone please help me.

---

### Post by shof2k on 2007-02-19
> **frenzy05 said:**
> I can't get my one  it work at all. It the wifimax pack (zd1211). I'm running Ubuntu 6.10 the Edgy Eft,  2.6.17-11-generic. Can someone please help me.

There is an Edgy version of this guide.  That uses a driver compatiable with 2.6.17-11.  It is at 
[http://ubuntuforums.org/showthread.php?p=2093008](http://ubuntuforums.org/showthread.php?p=2093008)

---

