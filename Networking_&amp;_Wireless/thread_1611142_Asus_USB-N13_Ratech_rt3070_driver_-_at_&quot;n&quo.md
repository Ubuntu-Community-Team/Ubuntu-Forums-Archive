---
title: "Asus USB-N13 Ratech rt3070 driver - at &quot;n&quot; speeds"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by jlh97214 on 2010-11-01
Recently the connection issues with my ASUS USB-13 wireless device were solved (see: [http://ubuntuforums.org/showthread.php?t=1499153);](http://ubuntuforums.org/showthread.php?t=1499153);) however, the solution only works at "g" speeds, not at the "n" speeds of the device.  After the thread was "solved" some well intended experts (I'm a newbie, and old, so simple works best) added some modifications to the thread, updating the driver, much appreciated, however, I was left in the dust with the nomenclature. 

Is there a "simpler" way, like Chili555's original solution, to use the 1) updated driver and 2)get the device operating at "n" speeds as it was designed?  Thank you

---

### Post by MooPi on 2010-11-01
You could try to set it with iwconfig.
```
sudo iwconfig wlan0 rate 150M
```
With your wireless designation ie wlan1 wlan2 or ra0 as possible. Is your router or access point N speed capable.

---

### Post by chili555 on 2010-11-01
What does this tell us about the ability of the router?```
sudo iwlist wlan0 scan
```Substitute ra0 or your wireless interface.

---

### Post by ibates on 2010-12-03
I think I am in a real fix.

I have an ASUS USB-N13 and am having great difficulties getting it up and running.

In the first instance, I created the files as shown in the reply #2 by chili555 at [http://ubuntuforums.org/showthread.php?t=1499153%29;](http://ubuntuforums.org/showthread.php?t=1499153%29;).  Nothing. Zix. Blank.  Not even a light from the LED on the dongle.

I researched a bit further, and came across the post from redsultan of March 13 2010 entitled "Help needed with ASUS USB-N13 Wireless Network Adapter.

I noticed that perhaps I should have installed some drivers and did so, exactly as described inredsultan's post.  Nothing.  Zix.  Blank.

Reading further in that post, I cam across a reply from Poostickz which said I shouold read the "Readme" file carefully and apply it.  This I did.  Nothing. Zix. Blank.

So I have done a few prints in terminal, and they are as follows:

xxxx-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and

hedy@hedy-laptop:~$ lsusb
Bus 004 Device 003: ID 05dc:a731 Lexar Media, Inc. 
Bus 004 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
hedy@hedy-laptop:~$

and finally, 

dmesg | grep -e rt2 -e rt3

[   36.508780] usbscore:  registered new interface driver rt2870.

But still, nothing, Zix, blank.

Perhaps someone can make head or tail out of all this.  I can't.  And there are so many threads and replies on this subject that it has simply become impossibly confusing for a non-tech head who doesn't really understand too much about it but just wants to get the dongle working.

This problem is made even more difficult for me to fathom because until I get this thing working, it is very difficult to get this machine on line.  All the above quotes are copied via a very circuitous method.

Help would be appreciated.

---

### Post by ibates on 2010-12-04
I have just reread some of the posts here and think that I might be able to work things out based on a solution by chili555 in one of the earlier posts.

I will give it a go, and if no joy, I will return to this thread with a fresh post.

Thanks.

---

### Post by chili555 on 2010-12-04
I am watching. Post back with your report and I'll be glad to help.

---

### Post by kwikksilva on 2010-12-04
Hi Guys,
Not to hi-jack - but getting back to the original post.

I am running 10.04.

I used chilli555's method to get my N13 up and running (adding the 2 lines to the 2 files) - and it did come up in like no time at all. It was a 2 minute job.

However - as per poster no. 1 - it only works at 54g. I tried the following with no joy.

```
sudo iwconfig wlan0 rate 150M
```Also 

```
sudo iwlist wlan0 scan
```Returned my router showing 802.11b/g/n

This stick achieved 270mb/s under Windows 7.

My next step was to compile the RALink driver (latest version 2.4.0.1 [2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO]) which compiled successfully out of the box (i changed the 2 WPA_SUPPLICANT entries to 'Y' first )- and but the card - although recognized - will not connect to any networks.

So right now i am running the RaLink driver - hoping that i can get it connecting - and that this will provide 'N' speeds.

Any other suggestions on how to get this stick working at 'N'?

Thanks

Kwikk

---

### Post by ibates on 2010-12-05
This post appears as a separate thread dated 05 Dec 2010.  But I have repeated the text here to follow on from an earlier communication with Chili555.

I am running Ubuntu Release 10.04 (lucid), Kernel Linux 2.6.32-26-generic-pae, GNOME 2.30.2.

I have installed the ASUS USB-N13 according to your advice in previous posts, specifically, in your advice to 828688 Ben.

The dongle seems to be operating as it should. The LED does its flashing at what appears to be the correct time. Wicd also looks correct. Networks are found with good signals shown. Everything looks correct. But when I attempt to connect, "validating authentication" runs for quite some time, and eventually results in a dialogue window stating the communication failed. The required WEP password is entered in the RT2870STA.dat file, and again in the wicd window.

I have entered as much detail in the RT2870STA.dat file as I dare, and believe it to be correct.

ndiswrapper is not installed. Network Manager is uninstalled. Only wicd remains.

Any thoughts, or queries which might allow you to diagnose this predicament?

---

### Post by chili555 on 2010-12-05
> **ibates said:**
> This post appears as a separate thread dated 05 Dec 2010.  But I have repeated the text here to follow on from an earlier communication with Chili555.

I am running Ubuntu Release 10.04 (lucid), Kernel Linux 2.6.32-26-generic-pae, GNOME 2.30.2.

I have installed the ASUS USB-N13 according to your advice in previous posts, specifically, in your advice to 828688 Ben.

The dongle seems to be operating as it should. The LED does its flashing at what appears to be the correct time. Wicd also looks correct. Networks are found with good signals shown. Everything looks correct. But when I attempt to connect, "validating authentication" runs for quite some time, and eventually results in a dialogue window stating the communication failed. The required WEP password is entered in the RT2870STA.dat file, and again in the wicd window.

I have entered as much detail in the RT2870STA.dat file as I dare, and believe it to be correct.

ndiswrapper is not installed. Network Manager is uninstalled. Only wicd remains.

Any thoughts, or queries which might allow you to diagnose this predicament?Please see your other post. I'm answering there.

---

### Post by FishRCynic on 2011-01-30
> **jlh97214 said:**
> Recently the connection issues with my ASUS USB-13 wireless device were solved (see: [http://ubuntuforums.org/showthread.php?t=1499153);](http://ubuntuforums.org/showthread.php?t=1499153);) however, the solution only works at "g" speeds, not at the "n" speeds of the device.  After the thread was "solved" some well intended experts (I'm a newbie, and old, so simple works best) added some modifications to the thread, updating the driver, much appreciated, however, I was left in the dust with the nomenclature. 

Is there a "simpler" way, like Chili555's original solution, to use the 1) updated driver and 2)get the device operating at "n" speeds as it was designed?  Thank you

Did this ever get an answer? 

***Correction****
Maverick does work with the previous solutions (ie ralink driver installation) listed 
but has drivers already (that work for G ). These drivers do not appear to allow N speeds. 
I am on amd64 if that makes a difference.
I can connect to the router if it is set to allow G, I can see the router if it is set to N only but cannot connect to it.

always remember to sudo make clean when removing a driver lol

***update 10.10****
default rt2870sta driver gives G speed only, will not authenticate with N router
does not appear to read RT2870sta in /etc/Wireless/RT2870sta/ regardless whether
configured or not - 

realtek driver 2.3... with modifications to suit 10.10 installed rt3070sta
added to modules
blacklisted rt2870sta, rt2800usb

and have speeds from 130M to 150M as per network manager

hopefully the ubuntu os driver will be corrected for 10.04 (and 10.10)
(it just makes life that much simpler when you plug it in and it works)

thanks to the various posters of all the people involved 
especially Chili555


(10.04 with the asus drivers from the asus site and the firmware from the Ralink site gets N speeds)
I did not mess around changing the udev rules etc as per other postings 
did a make, make install, also copied the .dat to /etc/wireless...  as per ASUS driver instructions
added rt2870sta to /etc/modules and blacklist rt2800usb to /etc/modprode.d/blacklist.conf
copied the downloaded firmware to /lib/firmware

---

### Post by muskieangler on 2011-02-05
> ***update 10.10****
default rt2870sta driver gives G speed only, will not authenticate with N router
does not appear to read RT2870sta in /etc/Wireless/RT2870sta/ regardless whether
configured or not - 

realtek driver 2.3... with modifications to suit 10.10 installed rt3070sta
added to modules
blacklisted rt2870sta, rt2800usb

and have speeds from 130M to 150M as per network manager

hopefully the ubuntu os driver will be corrected for 10.04 (and 10.10)
(it just makes life that much simpler when you plug it in and it works)

thanks to the various posters of all the people involved 
especially Chili555Can you please explain more about how you got N to work in 10.10?  Specifically, "realtek driver 2.3... with modifications to suit 10.10 installed rt3070sta".
[B]
**Update***[/B]

I ended up figuring it out on my Ubuntu 10.10 64bit installation with the latest updates which gets the adapter working, but only on wireless "G".
> 
**realtek driver 2.3**DPO_RT3070_LinuxSTA_V2.3.0.2_20100422

> **with modifications to suit 10.10 installed rt3070sta**Changed file include/os/rt_linux.h line 1077 to:
 #define RTUSB_URB_ALLOC_BUFFER(pUsb_Dev, BufSize, pDma_addr)                             usb_alloc_coherent(pUsb_Dev, BufSize,  GFP_ATOMIC, pDma_addr)

 And line 1078 to:
 #define RTUSB_URB_FREE_BUFFER(pUsb_Dev, BufSize, pTransferBuf,  Dma_addr)        usb_free_coherent(pUsb_Dev, BufSize, pTransferBuf,  Dma_addr)

After performing the edits, install the driver

make
make install

Blacklist the old rt2870sta and a few other offenders to make room for the new  rt3070 in  /etc/modprobe.d/blacklist.conf

Like so...

blacklist rt2870sta
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib

Add the "rt3070sta" line in /etc/modules (make sure "rt2870sta" line is not in /etc/modules).

If you get permission denied through any of the above, use "sudo" before the commands .  Otherwise, REBOOT ;-)

Worked like a charm for me.  Now I can finally get speeds as fast as my  Internet connection through my LAN!  Didn't have to do anything special  with Network Manager either, it played nice along the way.

> 
thanks to the various posters of all the people involved 
especially Chili555                      God bless you people!

For the record, I'm using the said Asus USB N-13 with a Netgear WNR3500L loaded with DD-WRT (Originally thought the Netgear was the issue)
The connection lit right up once I changed the Wireless to "auto" for both channel and frequency and added WPA2 Personal using AES only.  Other router settings may work OK with the N-13 too.

Thought that extra bit might be useful to someone.  Peace.

---

### Post by polarbear10 on 2011-02-21
Running 10.04, I'd like to get mine to work at n speeds too and have spent a few hours at this already and I think I have to step away...

Perhaps I am missing something but in the file I have the line numbers don't match but I did find this thread and changed the items to match.

[http://ubuntuforums.org/showthread.php?t=1602644](http://ubuntuforums.org/showthread.php?t=1602644)

Unfortunately for me, editing the file resulted in make errors.

I started over with a virgin copy of the installer - this time not changing anything

DPO_RT3070_LinuxSTA_V2.3.0.2_20100422

sudo make works - but make install fails - looking closely at error in the output of the command #sudo make install, I decided to rename RT2870STA.dat to RT3070STA.dat after which the sudo make install worked.

As I had followed post 35 from this thread:
[http://ubuntuforums.org/showthread.php?t=1419504&page=4](http://ubuntuforums.org/showthread.php?t=1419504&page=4)
I decided to remove the two files I previously created before restarting

The new driver does work and at N speeds - an unfortunate error in the ASUS driver linux download has made for a lot of grief.

Thanks muskiangler for getting me close enough to get the answer!

---

### Post by ken0069 on 2011-03-14
Ok so I'm back after a few months looking to see if anyone has had any success with getting N speeds out of this Asus n13 USB wireless adapter and now, just as before there's a bunch of stuff posted that makes absolutely no sense to me at all.

So, is there a thread somewhere that gives specific simple step by step instructions on how to get N speeds out of this adapter in Ubuntu 10.10?:(

---

### Post by polarbear10 on 2011-03-19
Hi Ken,

Here's what I did with the latest driver (in more detail than above).  Note I'm running 10.04 not 10.10 but I am getting wireless N speeds with the latest ASUS driver.

Download latest driver for the usb device from ASUS for the N-13

Extract the contents and then open terminal

cd /Downloads/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422

sudo make

sudo mv RT2870STA.dat RT3070STA.dat

sudo make install

Restart your computer and it should now work.

* I have a small problem, every once in a while after I run all the available Ubuntu updates for 10.04 LTS, I have to re-install the driver or the USB wireless doesn't come on.  The next time it happens I'm going to try adding: [http://ubuntuforums.org/showpost.php?p=8927671&postcount=32](http://ubuntuforums.org/showpost.php?p=8927671&postcount=32)

For now though I'm going to leave it alone because it works ;)

---

### Post by chili555 on 2011-03-19
> * I have a small problem, every once in a while after I run all the available Ubuntu updates for 10.04 LTS, I have to re-install the driver or the USB wireless doesn't come on.That's normal. When you get an updated linux-image you must rebuild the module against the later kernel:```
cd /Downloads/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422
[COLOR="Red"]sudo make clean[/COLOR]
sudo make
sudo make install

```

---

### Post by Elijah on 2011-03-23
> **polarbear10 said:**
> Running 10.04, I'd like to get mine to work at n speeds too and have spent a few hours at this already and I think I have to step away...

Perhaps I am missing something but in the file I have the line numbers don't match but I did find this thread and changed the items to match.

[http://ubuntuforums.org/showthread.php?t=1602644](http://ubuntuforums.org/showthread.php?t=1602644)

Unfortunately for me, editing the file resulted in make errors.

I started over with a virgin copy of the installer - this time not changing anything

DPO_RT3070_LinuxSTA_V2.3.0.2_20100422

sudo make works - but make install fails - looking closely at error in the output of the command #sudo make install, I decided to rename RT2870STA.dat to RT3070STA.dat after which the sudo make install worked.

As I had followed post 35 from this thread:
[http://ubuntuforums.org/showthread.php?t=1419504&page=4](http://ubuntuforums.org/showthread.php?t=1419504&page=4)
I decided to remove the two files I previously created before restarting

The new driver does work and at N speeds - an unfortunate error in the ASUS driver linux download has made for a lot of grief.

Thanks muskiangler for getting me close enough to get the answer!

Hi, 

I followed this same procedure but I never reached 'n' speeds. Interestingly when I apply the udev procedure it doesn't scan my 'n' router, when I remove the udev rules it appears again but stuck at 'g' speeds :confused:

I should've known it was too good to be true to find the 'Linux support' in the box... was I fooled :(

Anything else I can do here? (10.10)

---

### Post by Ripper1028 on 2011-07-19
I just loaded the newest version of ubuntu, and am not real good with the terminal. I followed both links and could not get anything but errors even during the sudo make. So running ubuntu version 11.04 I think, I get this during the sudo make:

I renamed the file wireless to make it easier than typing the whole thing in.

make -C tools
make[1]: Entering directory `/home/john/Desktop/Linux/wireless/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/john/Desktop/Linux/wireless/tools'
/home/john/Desktop/Linux/wireless/tools/bin2h
cp -f os/linux/Makefile.6 /home/john/Desktop/Linux/wireless/os/linux/Makefile
make -C /lib/modules/2.6.38-10-generic/build SUBDIRS=/home/john/Desktop/Linux/wireless/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-10-generic'
  CC [M]  /home/john/Desktop/Linux/wireless/os/linux/../../common/cmm_mac_usb.o
/home/john/Desktop/Linux/wireless/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitRecv’:
/home/john/Desktop/Linux/wireless/os/linux/../../common/cmm_mac_usb.c:83:3: error: implicit declaration of function ‘usb_buffer_alloc’
/home/john/Desktop/Linux/wireless/os/linux/../../common/cmm_mac_usb.c:83:30: warning: assignment makes pointer from integer without a cast
/home/john/Desktop/Linux/wireless/os/linux/../../common/cmm_mac_usb.c:112:4: error: implicit declaration of function ‘usb_buffer_free’
make[2]: *** [/home/john/Desktop/Linux/wireless/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/john/Desktop/Linux/wireless/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-10-generic'
make: *** [LINUX] Error 2
john@john-RF882AA-ABA-SR2034NX-NA680:~/Desktop/Linux/wireless$

---

### Post by chili555 on 2011-07-19
> **Ripper1028 said:**
> I just loaded the newest version of ubuntu, and am not real good with the terminal. I followed both links and could not get anything but errors even during the sudo make. Would you please post:```
lsusb
```Maybe there is an easier way.

---

### Post by Ripper1028 on 2011-07-20
Hi, thanks for the help. I feel like I already know you after following all your posts trying to get this to work.

john@john-RF882AA-ABA-SR2034NX-NA680:~$ lsusb
Bus 002 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2011-07-20
> I feel like I already know you after following all your posts trying to get this to work.Then you know I would have loved for you to *plug in* the Asus USB-N13 before you ran:```
lsusb
```Thanks.

---

### Post by Ripper1028 on 2011-07-20
Sorry, it's my dad's computer and I didn't know that he took it out and put it back in the box.

john@john-RF882AA-ABA-SR2034NX-NA680:~$ lsusb
Bus 002 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2011-07-20
> **Ripper1028 said:**
> Sorry, it's my dad's computer and I didn't know that he took it out and put it back in the box.

john@john-RF882AA-ABA-SR2034NX-NA680:~$ lsusb
Bus 002 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubAre you trying to get it to connect or are you trying to achieve N speeds? This device is driven at G speeds with rt2870sta. It is also claimed by a conflicting driver, rt2800usb. Let's fix that first. In a terminal:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot. Does it connect now? 

Do you need to move on to N speeds?

---

### Post by Ripper1028 on 2011-07-20
I did the blacklist and then unplugged the ethernet and restarted and it works fine. I don't know if it is n speeds or not, but thank you for the help.

---

### Post by knightowl626 on 2011-07-22
This is my first post. The learning curve for Linux has been both  educational and frustrating. I can get the Asus USB-N13 to work on my  emachines netbook, but only connecting to WEP encryption. I can't figure  out why I could not connect to my SSID in WPA encryption. My internal Broadcom wif-card works flawlessly. I am using  Ubuntu 10.10 Netbook edition with the Kernel Linux 2.6.35-30 maverick.  With this kernel version it is simply plug-n-play. I have tried to  compile the driver and still could not get it connect to WPA. Could someone please help me troubleshoot it? Any help is really appreciated.

---

### Post by chili555 on 2011-07-22
> **knightowl626 said:**
> This is my first post. The learning curve for Linux has been both  educational and frustrating. I can get the Asus USB-N13 to work on my  emachines netbook, but only connecting to WEP encryption. I can't figure  out why I could not connect to my SSID in WPA encryption. My internal Broadcom wif-card works flawlessly. I am using  Ubuntu 10.10 Netbook edition with the Kernel Linux 2.6.35-30 maverick.  With this kernel version it is simply plug-n-play. I have tried to  compile the driver and still could not get it connect to WPA. Could someone please help me troubleshoot it? Any help is really appreciated.Welcome to the world of Ubuntu! Let's see where you are so far. Please open a terminal and run and post:```
lsmod | grep rt2
modinfo rt2870sta | grep -e version -e lib
```Thanks.

---

### Post by knightowl626 on 2011-07-22
@chili555, thank you for your prompt response and assistance. Per your request,

**lsmod | grep rt2**

rt2870sta             406690  1 
crc_ccitt              1351  1 rt2870sta

[B]modinfo rt2870sta | grep -e version -e lib
  
[/B]filename:        /lib/modules/2.6.35-30-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:          2.1.0.0
srcversion:     93E93E3E336F412601AF0FA
vermagic:       2.6.35-30-generic SMP mod_unload modversions 686

---

### Post by chili555 on 2011-07-22
> filename: /lib/modules/2.6.35-30-generic/[COLOR="Red"]kernel/drivers/staging[/COLOR]/rt2870/rt2870sta.ko
version: 2.1.0.0This seems to be the built-in version, not the compiled version. Tell me about your efforts to compile. What file did you download?

Is your router set to WPA2 only or to WPA and WPA2 mixed mode? Mixed mode is tricky. Does it try to connect and just time out or what?

---

### Post by knightowl626 on 2011-07-22
Hi chili555. My compiled driver setup:

1) Downloaded the driver for Asus support website and extracted to the  Downloads directory. File version: DPO_RT3070_LinuxSTA_V2.3.0.2_20100422

2) Rename the file "**RT2870STA.dat**" to "**RT3070STA.dat**"

3) sudo gedit os/linux/config.mk
Verified that Support Wpa Supplicant and Support Native Wpa Supplicant for Network Manager is enabled by changing "n" to "y".

4) sudo make

5) sudo make install

6) sudo gedit /etc/udev/rules.d/network_drivers.rules

Pasted this line into the file: ACTION=="add", SUBSYSTEM=="usb",  ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe  -qba rt2870sta"

7) sudo gedit /etc/modprobe.d/network_drivers.conf

Pasted this line into the file: install rt2870sta /sbin/modprobe  --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1784" >  /sys/bus/usb/drivers/rt2870/new_id

Rebooted. Can connect to SSID WEP encrytion, but not WPA.

I followed robbiebravo setup in this post on pg. 14 ([http://tinyurl.com/3zznzho](http://tinyurl.com/3zznzho)).

My Netgear DGN3500 SSID is set to WPA2-PSK encryption only. Everytime I  connect to my SSID-WPA2 it keeps asking for the password after 30  seconds. I know it is the correct password. My internal wifi-card connects  fine without any issue. I could reinstall Ubuntu 10.10 Netbook Edition  from scratch and start all over. Please advise. Your time and effort are  greatly appreciated.

---

### Post by knightowl626 on 2011-07-22
chili555. Man, I don't know what I did, but I can connect to my SSID WPA2 encryption. I feel like running into the wall literally. You must send out some positive vibe or something. Thanks for your help though. Peace!

---

