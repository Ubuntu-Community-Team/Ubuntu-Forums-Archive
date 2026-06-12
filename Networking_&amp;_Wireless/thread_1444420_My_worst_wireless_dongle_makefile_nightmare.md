---
title: "My worst wireless dongle makefile nightmare"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by cyberhood on 2010-04-01
So I'm trying to get my new Wireless USB dongle to work with Xubuntu 9.10 Karmic Koala.

I've extracted the .rar file that was on the drivers CD that came with the dongle.  According to the ReadMe....
The Model Name is: RT2870 Wireless Lan Linux Driver
Driver Name: rt2870.o/rt2870.ko
Hardware: Ralink 802.1n Wireless LAN Card
Description: This is a linux device driver for Ralink RT2870 USB ABGN WLAN Card.

My issues:
1. I do not see the driver file anywhere in the folder contents... I suppose that I have to "build" it.
2. In the makefile the chipset is default set to "CHIPSET = 3070" & the folder that holds all the extracted files is named 2008_1128_RT3070_Linux_STA_v2.0.1.0 so I'm confused as to whether this dongle has a 2870 or 3070 chipset inside.  Does it matter?
3. Sorry, I'm a bit of a n00bster when it comes to all this, but I'm having some problems with the build instructions.  It reads:
```
Build Instructions:  
====================
1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	** Build for being controlled by WpaSupplicant with Ralink Custom Event
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   command: #./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make									# compile driver source code

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2870sta
```

In step #1 I really have no idea what it wants me to do, nor if I should enter anything in the 'x' places.  
The MODE & TARGET parts of step #2 are finished.  For the linux kernel source file path it reads: ```
LINUX_SRC = /opt/fvt_11N_SDK_0807/fvt131x_SDK_11n/linux-2.6.17
``` in the first LINUX_SRC entry.  I guess that's correct..?
Step #3: I have no idea what the first 2 instructions want me to do but I found the config.mk file it's talking about.  I sacrificed NetworkManager for WICD... will this make a difference in the later instructions in this step?
The steps after those are *really* just Greek to me.  I have no idea what's going on.

My current situation:
As I do not have internet access on the computer in question, nor can I establish a wired connection to the router, I have no idea how I would install header & library files if I need to.
The light on the dongle *does* come on when I plug it into a USB port.
I've blacklisted "rt2800usb" already because that's what the cool kids were doing in the other help threads I've researched on this topic to get it to work. Don't know if I should've... 

Please help... and thanks in advance.

---

### Post by chili555 on 2010-04-01
Well, rt2870sta and rt3070sta are both in the kernel, unless you have a very old version of Ubuntu. It's a beautiful warm day here, so let's not waste time compiling, as fun as that might be. First, let's see what driver your card needs. Please post:```
lsusb
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by cyberhood on 2010-04-01
Thanks for the quick reply chili555.  We've been blessed with a beautiful day on my side of the fence as well.  Unfortunately, I have a book that goes to the press next month that I gotta finish so I'm trapped inside even though today's a sunny spring holiday!!

lsusb comes up with:
```
Bus 001 Device 005: ID 1b75:3072
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage [sic] Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04fc:0801 Sunplus Technology Co., Ltd
Bus 001 Device 002: ID 0603:00f2 Novatek Microelectronics Corp.
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
```
lsmod | grep -e rt2 -e rt3 comes up with:
```

rt2870sta                  488820   0 
```

---

### Post by chili555 on 2010-04-01
I am wondering how rt2870sta gets loaded; it is not correct, as presently written, for your device. However, I think the cool kids were wrong:```
Bus 001 Device 005: ID [COLOR="Red"]1b75[/COLOR]:[COLOR="Red"]3072[/COLOR]

``````
$ modinfo [COLOR="Blue"]rt2800usb[/COLOR] | grep 3072
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]1B75[/COLOR]p[COLOR="Red"]3072[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
```What happens if you unload rt2870sta and load rt2800usb?```
sudo rmmod -f rt2870sta
sudo modprobe rt2800usb
iwconfig
```Is an interface created? If not, let's see:```
dmesg | grep -e rt2
```

---

### Post by chili555 on 2010-04-01
Please check PMs.

---

### Post by cyberhood on 2010-04-01
::cringe::
Input/output errors all around
no wireless extensions.

What's that mean?

good luck bro, looking forward to hearin' from ya when you get back
thanks

---

### Post by chili555 on 2010-04-01
> Input/output errors all aroundWhen you removed rt2870sta or when you modprobed rt2800usb? What did they say, more or less?

---

### Post by cyberhood on 2010-04-02
Note: I've plugged in an older dongle and moved to another room so I can reach the router.

---

### Post by chili555 on 2010-04-02
> I've unplugged the new one that I'm trying to get drivers for now. Should I plug it in?Please. Then run:```
iwconfig
```Do you have a wireless interface other than wlan7? If not, post:```
lsmod | grep rt2
```Thanks.

---

### Post by cyberhood on 2010-04-02
Alright, both USB dongles plugged in.  Connected to the 'net wirelessly with the old one.

---

### Post by chili555 on 2010-04-02
Please take the old one, wlan7, out and lock it in the trunk of your car...unless, of course, you need it to connect to reply to this forum. It is too confusing to the system and me! Insert the new device, and run:```
iwconfig
dmesg | grep -e rt2 -e rt3
```Thanks

---

### Post by cyberhood on 2010-04-02
lol, sorry
```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

~$ dmesg | grep -e rt2 -e rt3
[   10.916490] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   10.944763] usbcore: registered new interface driver rt2870
```

---

### Post by chili555 on 2010-04-02
Those low timestamps in dmesg, 10.xx, are undoubtedly when the computer booted. Leaving your device plugged in and the other in the trunk, please do:```
sudo ifconfig wlan7 down
sudo rmmod -f rt2870sta
sudo modprobe rt2800usb
iwconfig
```Thanks. Is the other device an rt2870sta device?

---

### Post by cyberhood on 2010-04-02
```
~$ sudo ifconfig wlan7 down
wlan7: ERROR while getting interface flags: No such device
~$ sudo rmmod -f rt2870sta
~$ sudo modprobe rt2800usb
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan8     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
I don't know what chip the old dongle has.  Do I have to take it outta the trunk to find out? ;)

---

### Post by chili555 on 2010-04-02
> wlan8     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
Woo hoo! You have a wireless interface! Now can you click that ole Network Manager icon and connect?

Let's leave the other dongle in jail for now. We can return to it later.

---

### Post by cyberhood on 2010-04-02
...using WICD.  Opened it up, can't see any wireless networks to connect to.  Went to preferences, changed wlan7 to wlan8.  Refreshed. Still nothing.

---

### Post by chili555 on 2010-04-02
Please detach the ethernet cable, open a terminal and do:```
sudo ifconfig wlan8 up
sudo iwlist wlan8 scan
```If you get scan results, does Wicd see networks now? Does it connect?

---

### Post by cyberhood on 2010-04-02
I'm not connected with a cable.  I'm posting wirelessly from a different computer.

```
~$ sudo ifconfig wlan8 up
wlan8: ERROR while getting interface flags: No such device
~$ sudo iwlist wlan8 scan
wlan8     Interface doesn't support scanning.
```

---

### Post by chili555 on 2010-04-02
> wlan8: ERROR while getting interface flags: No such device
What???

I thought we just saw it. Please let me see:```
iwconfig
ifconfig
```Thanks.

---

### Post by cyberhood on 2010-04-02
Hmm... strange, yes.  I repeated the previous steps and got it back up somehow.

```
~$ sudo ifconfig wlan8 up
~$ sudo iwlist wlan8 scan
wlan8     No scan results

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan8     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:97:b6:6a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan8     Link encap:Ethernet  HWaddr 00:4f:77:00:0c:d5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-4F-77-00-0C-D5-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
Note: now the light on the dongle is blinking.

---

### Post by chili555 on 2010-04-02
> now the light on the dongle is blinking.I think it wants you to click the Wicd icon and connect to your network. Can you please do so?

---

### Post by cyberhood on 2010-04-02
According to WICD: "No wireless networks found." 
A refresh gives the same message.  Light still flashing.

---

### Post by chili555 on 2010-04-02
Does it scan?```
sudo iwlist wlan8 scan
```

---

### Post by cyberhood on 2010-04-02
```
sudo iwlist wlan8 scan
wlan8        No scan results
```

Was looking around in the Advanced Settings of Wicd and found that the WPA Supplicant Driver is set to "wext" is that correct?  I see "ralink_legacy" in there too.

And why, when I type "iwconfig", does the wireless network not show up next to ESSID like it does with my other dongle?  Nor is there an Associated Access Point.

---

### Post by chili555 on 2010-04-02
> Was looking around in the Advanced Settings of Wicd and found that the WPA Supplicant Driver is set to "wext" is that correct? I see "ralink_legacy" in there too.Wext is correct in 90% of all cases. > And why, when I type "iwconfig", does the wireless network not show up next to ESSID like it does with my other dongle? Nor is there an Associated Access Point.Because you have not yet associated; that is, connected. 

Back in a few.

---

### Post by chili555 on 2010-04-02
Please do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```You will find dmesg.zip in your user directory. Please attach it to your reply. Thanks.

---

### Post by cyberhood on 2010-04-02
```
zip dmesg.zip dmesg.txt
adding: dmesg.txt (deflated 71%)
```

Contents of dmesg.1.gz (can't find dmesg.zip):
```
.\" Copyright 1993 Rickard E. Faith (faith@cs.unc.edu)
.\" May be distributed under the GNU General Public License
.TH DMESG 1
.SH NAME
dmesg \- print or control the kernel ring buffer
.SH SYNOPSIS
.BI "dmesg [ \-c ] [ -r ] [ \-n " level " ] [ \-s " bufsize " ]"
.SH DESCRIPTION
.B dmesg
is used to examine or control the kernel ring buffer.

The program helps users to print out their bootup messages.  Instead of
copying the messages by hand, the user need only:
.RS
dmesg > boot.messages
.RE
and mail the
.I boot.messages
file to whoever can debug their problem.
.SH OPTIONS
.TP
.B \-c
Clear the ring buffer contents after printing.
.TP
.B \-r
Print the raw message buffer, i.e., don't strip the log level prefixes.
.TP
.BI \-s bufsize
Use a buffer of size
.I bufsize
to query the kernel ring buffer.  This is 16392 by default.
(The default kernel syslog buffer size was 4096
at first, 8192 since 1.3.54, 16384 since 2.1.113.)
If you have set the kernel buffer to be larger than the default
then this option can be used to view the entire buffer.
.TP
.BI \-n level
Set the
.I level
at which logging of messages is done to the console.  For example,
.B \-n 1
prevents all messages, expect panic messages, from appearing on the
console.  All levels of messages are still written to
.IR /proc/kmsg ,
so
.BR syslogd (8)
can still be used to control exactly where kernel messages appear.  When
the
.B \-n
option is used,
.B dmesg
will
.I not
print or clear the kernel ring buffer.

When both options are used, only the last option on the command line will
have an effect.
.SH SEE ALSO
.BR syslogd (8)
.\" .SH AUTHOR
.\" Theodore Ts'o (tytso@athena.mit.edu)
.SH AVAILABILITY
The dmesg command is part of the util-linux-ng package and is available from
ftp://ftp.kernel.org/pub/linux/utils/util-linux-ng/.
```

---

### Post by chili555 on 2010-04-02
Were you in your home directory? Did you do both commands in order? Please do:```
ls | grep dmesg
```Don't you see two files, dmesg.txt and dmesg.zip? 

I'm confused.

---

### Post by cyberhood on 2010-04-02
Alright, yeah I was looking in the wrong place.  I found them.  So, what exactly do you want me to post?  The contents of the .txt file?

---

### Post by chili555 on 2010-04-02
Just make a reply and attach the zip file by clicking the paperclip up above the reply box.

---

### Post by cyberhood on 2010-04-02
I can't, I'm posting from another computer.  I'm outta gas, I gotta hit the sack.  Tomorrow I'll connect again from the other comp with the old dongle and send the .zip.

Thanks a ton for your help so far

---

### Post by cyberhood on 2010-04-03
dmesg.zip

---

### Post by chili555 on 2010-04-03
Are you quite certain that when you ran *lsusb* back in post #4 that you had your current device inserted and not the one we locked in the trunk? Please run:```
lsusb
```Post the part related to your wireless or, if in doubt post it all.

So far, your dmesg looks fine, except the wireless doesn't work. Please let me see:[CODE]ls /lib/firmware | grep rt2

Thanks.

---

### Post by cyberhood on 2010-04-03
```
~$ lsusb
Bus 001 Device 007: ID 1b75:3072  
Bus 001 Device 006: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 005: ID 0951:1607 Kingston Technology Data Traveler 2.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 003 Device 002: ID 04fc:0801 Sunplus Technology Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

~$ ls /lib/firmware | grep rt2
rt2561.bin
rt2561s.bin
rt2661.bin
rt2860.bin
rt2870.bin
```

---

### Post by cyberhood on 2010-04-03
> **chili555 said:**
> Are you quite certain that when you ran *lsusb* back in post #4 that you had your current device inserted and not the one we locked in the trunk?

I plugged in the old dongle between posts #7 & #8.

---

### Post by cyberhood on 2010-04-03
> **chili555 said:**
> However, I think the cool kids were wrong

Just reading back from what we posted on the first page since you told me to take a closer look there.  Should I have un-blacklisted "rt2800usb" based on this comment? Or have we already done that?
I apologize again for my n00bness... just a regular dude trying to expunge M$ Windoze from the strangle-hold it has on my life and gain some autonomy.

---

### Post by chili555 on 2010-04-03
I hope we un-blacklisted correctly. Please do:```
sudo cat /etc/modprobe.d/blacklist
```If there is no such file, we can move to the next step. If there is such a file, leave the terminal open and open a second terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```If there are any entries in *blacklist* beyond amd76x_edac, move them over to *blacklist.conf*.

In blacklist.conf, make sure that blacklist rt2870sta is in there. Make sure that these lines are ***not*** in there:> blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00libAmend as necessary, proofread, save and close gedit. Reboot if there were any changes and give me your report.

---

### Post by cyberhood on 2010-04-03
```
sudo cat /etc/modprobe.d/blacklist
```
...came up with no such file

blacklist prior to this post: 
```
blacklist amd76x_edac
blacklist rt2800usb
```

blacklist after this post:
```
blacklist amd76x_edac
blacklist rt2870sta
```

Rebooted and some new major changes: I first logged into my master account only to find "Places" (where I normally access the "File System") **not** in the taskbar along side "Applications" and things looking a bit strange on when I expanded "Applications" - no avatars next to Apps.  Rebooted again with hopes of getting a look at the blacklist file once again and things back in order.  Sign in screen appeared.  I tried to log into the master account (I'm absolutely positive I've entered the correct password) and it thinks for a second and the log in screen pops up again with no errors.  I try to log into master account again, same thing happens.  I *can* log into my second account and everything appears ok and normal, but I don't have sudoer permission. 
What happened?

---

### Post by chili555 on 2010-04-03
I have no idea. Blacklisting should have no effect on the loading of the desktop. Is there any improvement if you boot with the device removed? Please post:```
cat /etc/modules
```

---

### Post by cyberhood on 2010-04-03
```
cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt2870sta
```

Yeah, I figured the blacklisting would have nothing to do with it considering the fact that I've made changes there before and rebooted without any problems whatsoever.  The strange thing is that it's the _only_ change I made to the system before I had this problem.  I wasn't doing anything else on the machine.
I do get some message -that I've never seen or noticed before- when I try to log in to the main account about "Starting lists crypto disk..." something or other, then the screen goes completely white then the log in screen appears again.  Problem is, this machine moves FAST, it's what I designed it for.  It's running Xfce from a solid state drive and I never have time to read any of the boot messages or errors.  Tried rebooting without the device plugged in... same story.
No problems logging into the secondary account.  That is, with the exception of not having sudoer privileges - unless that can be changed...?

---

### Post by chili555 on 2010-04-03
So that is how rt2870sta is getting loaded; see your first several posts. We now have a situation where one file says, 'load rt2870sta' and another says, 'never load rt2870sta.' It seems we have confused the system!```
sudo gedit /etc/modules
```Remove the rt2870sta line, proofread, save and close gedit. Reboot. Do things look a bit better? Can you insert the USB device? And connect?

---

### Post by cyberhood on 2010-04-03
```
sudo mousepad /etc/modules
[sudo] password for SecondaryAcctName: (#here I tried both the sudo account password and the Secondary password to no avail)
SecondaryAcctName is not in the sudoers file. This incident will be reported.
```
How do I use sudo commands from my secondary account?

---

### Post by chili555 on 2010-04-03
> my secondary account?I don't understand. Is this a dual boot or wubi or virtual machine installation?

---

### Post by cyberhood on 2010-04-03
> **chili555 said:**
> I don't understand. Is this a dual boot or wubi or virtual machine installation?
Not dual boot. Have no idea what wubi or virtual machine mean.
*edit* just looked up wubi and virtual machine and my system does not have anything to do with either... as far as I'm aware of.  Xubuntu is the only thing installed and running on it.

I just have two user accounts.  For some reason now I can't sign into my principle [sudo] user account and I'm using the secondary one I had created.  But on the secondary user account it won't let me do sudo commands from the terminal.  I don't think it has sudo privilege.  Is there anyway I can complete sudo privilege commands from the terminal without having to log into the principle user account?

---

### Post by chili555 on 2010-04-03
Yikes! You seem to have a few problems. Please try:```
sudo su
gedit /etc/modules
```After your changes are made, proofread and saved, do:```
exit
```Reboot.

---

### Post by cyberhood on 2010-04-03
same message for 'sudo su' terminal command attempt:
```
sudo mousepad /etc/modules
[sudo] password for SecondaryAcctName:
SecondaryAcctName is not in the sudoers file. This incident will be reported.
```
I can open /etc/modules in mousepad (the text editor I'm using) without using the sudo command, but when I try to remove the 'rt2870sta' line then save it gives me a "Can't open file to write" error.

---

### Post by chili555 on 2010-04-03
Can you run the installation CD as a live CD and find the file that way? There will be an /etc/modules file in the install CD, but you want to find the one in /mnt/media or some such. I am rebooting my system with a live CD and will see what it looks like for you.

---

### Post by cyberhood on 2010-04-03
> **chili555 said:**
> Can you run the installation CD as a live CD and find the file that way?
Trying this... so far I only have a pulsating rat...

---

### Post by chili555 on 2010-04-03
I am booted in the live CD. I opened a terminal and did:```
cd /media && ls
```It was a very long series of numbers and letters. I typed in the first two and pressed Tab nand the rest filled in and I pressed Enter and then typed ```
ls
```I saw my file system and typed:```
cd etc
sudo gedit modules
```After I made a change, I saved and closed. I checked and the change sticks

---

### Post by cyberhood on 2010-04-03
From the live CD: I didn't get very far in the terminal:
```
ubuntu@ubuntu:~$ cd /media && ls
ubuntu@ubuntu:/media$ ls
ubuntu@ubuntu:/media$ cd etc
bash: cd: etc: No such file or directory
ubuntu@ubuntu:/media$ sudo mousepad modules (this brought up a blank text file with the name "(modules)"

```
... but I found *real?* modules from a search of the File System icon on the desktop and changed:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
```
to
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
```
Now what? Should I try and boot sans live cd?

---

### Post by cyberhood on 2010-04-03
Rebooted. Removed live CD. Same problem with principle account access.  Some quick message in a black screen about "Starting init crypto disks..." 
Signed into secondary user account, found the modules folder... unchanged.

```
lp
rt2870sta
```

handful of bloody hair

---

### Post by cyberhood on 2010-04-03
Should I start a new thread about my root user account access problem?

---

### Post by chili555 on 2010-04-03
> **cyberhood said:**
> Should I start a new thread about my root user account access problem?Yes, please. Something deeper than wireless is amiss.

---

### Post by cyberhood on 2010-04-03
> **chili555 said:**
> Yes, please. Something deeper than wireless is amiss.
Shucks... and it seemed like we were getting so close!
Logged out of secondary user account and it went to a blank screen with a command line.  I entered my principle user account name and got a message looking something like this:
```
[ 4552.294717] end_request: I/O error, dev sda, sector 268415 
[ 4552.294889] end_request: I/O error, dev sda, sector 268415 
[ 4570.765769] end_request: I/O error, dev sda, sector 268415 
[ 4739.xxxxxx] end_request: I/O error, dev sda, sector 268415 
[ 4552.xxxxxx] end_request: I/O error, dev sda, sector 268415 
etc. stuff like this... couldn't copy it all
```
Are these bad sectors in my disk?  Could this prevent a log in? Can I do anything about it?
Note: I boot from an SSD on the motherboard.  I have an HDD in there with no OS loaded on it (if you couldn't tell)...

[new thread]("http://ubuntuforums.org/showthread.php?t=1446192")

---

### Post by chili555 on 2010-04-03
It sounds like a bad disk or at least disk corruption. The gurus over on General Help will...help.

You missed a step here:>  	
I am booted in the live CD. I opened a terminal and did:
Code:

[COLOR="Red"]cd /media && ls

It was a very long series of numbers and letters. I typed in the first two and pressed Tab nand the rest filled in[/COLOR] and I pressed Enter and then typed
Code:

ls

I saw my file system and typed:
Code:

cd etc
sudo gedit modules

After I made a change, I saved and closed. I checked and the change sticks 

---

### Post by cyberhood on 2010-04-03
> **chili555 said:**
> It sounds like a bad disk or at least disk corruption. The gurus over on General Help will...help.

You missed a step here:

I did that step, I just didn't get the long series of numbers and letters that you said yours came up with.  I do have an Ubuntu live cd.  You think I should try that instead of the Xubuntu live cd?

---

### Post by chili555 on 2010-04-03
It should be the same either way. You might just google up 'fsck' and see if that helps repair your problems. I am pretty sure you can safely run it from the live CD.

---

### Post by cyberhood on 2010-04-03
> **chili555 said:**
> I am booted in the live CD. I opened a terminal and did:```
cd /media && ls
```It was a very long series of numbers and letters. I typed in the first two and pressed Tab nand the rest filled in and I pressed Enter and then typed ```
ls
```I saw my file system and typed:```
cd etc
sudo gedit modules
```After I made a change, I saved and closed. I checked and the change sticks
After a bit of head scratching I decided to change your command recommendation from /media to /dev and this is what came up:
```
ubuntu@ubuntu:~$ cd /dev && ls
agpgart          loop4               ram7        tty10  tty4   ttyS2
audio            loop5               ram8        tty11  tty40  ttyS3
binder           loop6               ram9        tty12  tty41  urandom
block            loop7               random      tty13  tty42  usb
bus              mapper              rfkill      tty14  tty43  usbmon0
cdrom            mcelog              rtc         tty15  tty44  usbmon1
cdrw             mem                 rtc0        tty16  tty45  usbmon2
char             mixer               scd0        tty17  tty46  usbmon3
console          net                 sda         tty18  tty47  usbmon4
core             network_latency     sda1        tty19  tty48  usbmon5
cpu_dma_latency  network_throughput  sda2        tty2   tty49  vcs
disk             null                sda5        tty20  tty5   vcs1
dri              oldmem              sdb         tty21  tty50  vcs2
dsp              pktcdvd             sdb1        tty22  tty51  vcs3
dvd              port                sdc         tty23  tty52  vcs4
dvdrw            ppp                 sequencer   tty24  tty53  vcs5
ecryptfs         psaux               sequencer2  tty25  tty54  vcs6
fb0              ptmx                sg0         tty26  tty55  vcs7
fd               pts                 sg1         tty27  tty56  vcs8
full             ram0                sg2         tty28  tty57  vcsa
fuse             ram1                sg3         tty29  tty58  vcsa1
hidraw0          ram10               shm         tty3   tty59  vcsa2
hidraw1          ram11               snapshot    tty30  tty6   vcsa3
hidraw2          ram12               snd         tty31  tty60  vcsa4
hpet             ram13               sndstat     tty32  tty61  vcsa5
input            ram14               sr0         tty33  tty62  vcsa6
kmsg             ram15               stderr      tty34  tty63  vcsa7
log              ram2                stdin       tty35  tty7   vcsa8
loop0            ram3                stdout      tty36  tty8   zero
loop1            ram4                tty         tty37  tty9
loop2            ram5                tty0        tty38  ttyS0
loop3            ram6                tty1        tty39  ttyS1

``` 
Is that the long series of numbers and letters you were referring to?
If so which "first two" exactly do I type in?

ps- hard disk check from live cd came up clean.

---

### Post by chili555 on 2010-04-03
> Is that the long series of numbers and letters you were referring to?No. You are in the wrong place. Please do:```
cd /media && ls
```That's LS there, not one-ess. What does the terminal have to say?

---

### Post by cyberhood on 2010-04-03
The terminal doesn't say anything.  It's gives me the same as before: as far as I can tell it just adds "/media" next to the command user's name.
Terminal looks exactly like this:
```
ubuntu@ubuntu:~$ cd /media && ls
ubuntu@ubuntu:/media$
```

---

### Post by chili555 on 2010-04-03
OK, I booted into a live CD and figured it out. It doesn't show up because it's not yet mounted. Go to Places and see a listing (or two) for xx GB Media, where xx is the size of your harddrive. Click it and it will mount and an icon will appear on your desktop. Now when you do ls, you will see the volume. Running Lucid, it appeared as a long string of numbers and letters. I'm running a live CD for Jaunty now and it shows as [COLOR="Blue"]disk[/COLOR]. Then I did *ls* and saw the file system on the harddrive. If I did *cd etc*, I would see modules and I could ```
sudo gedit modules
```

I will stay live in case you have any other issues.

---

### Post by cyberhood on 2010-04-04
Thanks a lot for all your help chili.  But seeing as how I'm not getting anywhere with the live cd and the gurus in General Help seem to be at a loss of words regarding my login problems I've decided to throw in the towel -for this round- and do a fresh install.  Once everything is up and running again I'll give the new wireless device another go and update this thread.
Thanks again for stickin' with me... you're the true embodiment of the word "community" here.

---

### Post by chili555 on 2010-04-04
Thanks for your kind comments. I will try to look for your posts. If I don't chime right in, please PM me. Good luck. See you again soon.

---

### Post by cyberhood on 2010-04-04
Ok, Xubuntu 9.10 reinstalled and ready to rock :guitar:

the /etc/modules folder looks "stock" now... with only the > lp line in the code.

---

### Post by chili555 on 2010-04-04
Let's check which modules are loaded:```
lsmod | grep rt2
```If none are loaded, do:```
sudo modprobe rt2800usb
iwconfig
```Do you have a wireless interface, wlan0, perhaps? If so, please do:```
sudo iwlist wlan0 scan
```Let me hear your progress so far.

---

### Post by cyberhood on 2010-04-04
Note: wireless dongle inserted with blinking light. 
```
~$ lsmod | grep rt2
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
crc_ccitt               1852  1 rt2800usb
mac80211              181236  3 rt2x00usb,rt2x00lib,zd1211rw
cfg80211               93052  3 rt2x00lib,zd1211rw,mac80211
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
sudo iwlist wlan1 scan
wlan1     No scan results

~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.
```

---

### Post by cyberhood on 2010-04-04
Now I understand all the references to coffee beans!  I don't know how much coffee I've gone through messing around with this OS.  It sure is fun learning though.  Who knows, it might force me to move to something stronger!:evil:\\:D/

---

### Post by chili555 on 2010-04-04
> mac80211              181236  3 rt2x00usb,rt2x00lib,[COLOR="Red"]zd1211rw[/COLOR]
cfg80211               93052  3 rt2x00lib,[COLOR="Red"]zd1211rw[/COLOR],mac80211
May I assume that wlan0 and zd1211rw are for your other device? Do conditions improve if you do:```
sudo rmmod -f zd1211rw
sudo ifconfig wlan1 up
sudo iwlist wlan1 scan
```

---

### Post by cyberhood on 2010-04-04
> **chili555 said:**
> May I assume that wlan0 and zd1211rw are for your other device?
I dunno the specs of the other device.  I'll go lock it in the trunk now.

> **chili555 said:**
> Do conditions improve if you do:```
sudo rmmod -f zd1211rw
sudo ifconfig wlan1 up
sudo iwlist wlan1 scan
```
I typed in all 3 commands & got a response for the third command there:
```
wlan1      No scan results
```

---

### Post by chili555 on 2010-04-04
Please, let's take a look at:```
dmesg | grep rt2
```Thanks.

---

### Post by cyberhood on 2010-04-04
this is what appears:
```
~$ dmesg | grep rt2
[  725.225770] Registered led device: rt2800usb-phy1::radio
[  725.225813] Registered led device: rt2800usb-phy1::assoc
[  725.225852] Registered led device: rt2800usb-phy1::quality
[  725.226243] usbcore: registered new interface driver rt2800usb
[  725.367127] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin
```

---

### Post by chili555 on 2010-04-04
Is your router an 802.11N model? Evidently rt2800usb has difficulty scanning or even connecting to N devices. Does it help to change your router to operate in mixed B and G (not N) mode?

---

### Post by cyberhood on 2010-04-04
I don't know.  I think so.  How would I go about finding out?  At the moment I don't have physical access to the router.  I'm a floor above it with a locked door in between me and it.  My landlord should be back from vacation tomorrow and I would be able to have a look at it, physically, if necessary.  Unless there's another way...

*note* the point of purchasing the newer "high-power N" wireless device was to hopefully have more reach and improved connectivity.  The cheaper one I had barely reached the router from where I was (18% connectivity) and my connection would come and go depending on the % number.  I have no idea at the moment if the router supports N devices, or whatever.  I guess if it doesn't I'll have to take the device back...?

---

### Post by chili555 on 2010-04-04
Let's try another approach. Please do:```
sudo rmmod -f rt2800usb
sudo modprobe rt2800usb nohwcrypt=1
sudo iwlist wlan0 scan
```If we can get it to work, we can tweak one file and make that permanent.

Even if the landlord's router is locked on N, I would think you might see a neighbor's signal. If I walk my laptop to the front porch, I see four or five.

---

### Post by cyberhood on 2010-04-04
When I executed the second command I got a bubble reminding me that I wasn't connected to the wireless network... in case that means anything.
```
~$ sudo rmmod -f rt2800usb
~$ sudo modprobe rt2800usb nohwcrypt=1
~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.
```

---

### Post by chili555 on 2010-04-04
> a bubble reminding me that I wasn't connected to the wireless networkThat means the card is working and available to connect if it gets a command through NM to do so!

Sorry, I meant:```
sudo iwlist wlan[COLOR="Red"]1[/COLOR] scan
```If you get scan results, click the Network Manager icon and see if you can connect.

---

### Post by cyberhood on 2010-04-04
wlan1                        No scan results

---

### Post by chili555 on 2010-04-04
That and the notification ballon suggest to me that if it could see a network, it could connect. I noticed here:> wlan1     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
There is no bit rate specified. It may mean that the card has not negotiated one with a router or otherwise. Let's try to force one and see if that helps.```
sudo iwconfig wlan1 rate 54M
sudo iwlist scan
```Or:```
sudo iwconfig wlan1 rate auto
sudo iwlist wlan1 scan
```

---

### Post by cyberhood on 2010-04-04
turned up 
```
wlan1 No scan results
```

for both 54M & auto

---

### Post by chili555 on 2010-04-04
Unless there is another computer nearby to see his router's mode, or another router to see, then I think the only options left are to go to the trunk and get the Zydas device working and to see the landlord.

---

### Post by cyberhood on 2010-04-04
I'm on a different computer right now and wirelessly connected to the router in question through my internal wireless card (if that's what you mean).  Can I see the router's mode from here?

---

### Post by chili555 on 2010-04-04
Sure.```
sudo iwlist wlan0 scan
```Use whatever the wireless interface is, if it's not wlan0. Find out with:```
iwconfig
```It ought to look something like:> Cell 01 - Address: 99:24:56:2A:77:88
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"mylilrouter"
                    Bit Rates:[COLOR="Red"]1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s[/COLOR]
                    Mode:Master
--- snip ---

---

### Post by cyberhood on 2010-04-04
yay!
```
wlan0     Scan completed :
          Cell 01 - Address: 00:01:38:X8:X8:9X
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=60/70  Signal level=-50 dBm
                    Encryption key:on
                    ESSID:"WLAN_8X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008b133c21ea
                    Extra: Last beacon: 168ms ago
                    IE: Unknown: 0007574C414E5F3842
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030102
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD050010910400

```

---

### Post by chili555 on 2010-04-04
You might try to right-click the Network Manager icon and select Edit Connections. Select Wireless and click Add. Put in Auto WLAN_8X. Check the Wireless Security tab and fill in your WEP (it looks like) details. Save and close and see if it connects.

---

### Post by cyberhood on 2010-04-04
Got a "connection established" bubble, heart jump SUCCESS feeling, but when I hover the mouse over the wireless symbol in the top right it says: "Wirelessnetwork connection 'Audo WLAN_8X active: Auto WLAN_8X (0%)"

Tried to open Mozilla... won't go to any webpages...

---

### Post by chili555 on 2010-04-04
Please post:```
iwconfig
ifconfig
```Thanks.

---

### Post by cyberhood on 2010-04-04
iw & if:
```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"Auto WLAN_8X"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: FE:24:3E:5D:F6:E4   
          Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:97:b6:6a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:560 (560.0 B)  TX bytes:560 (560.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:4f:77:00:0c:d5  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::24f:77ff:fe00:cd5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3659 (3.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-4F-77-00-0C-D5-30-30-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by chili555 on 2010-04-04
Please do:```
sudo ifconfig wlan1 down
sudo iwconfig wlan1 mode managed
sudo ifconfig wlan1 up
```I have no idea how this could happen:> wlan1     IEEE 802.11bgn  ESSID:"Auto WLAN_8X"  
          Mode:[COLOR="Red"]Ad-Hoc[/COLOR]  Frequency:2.412 GHz  Cell: FE:24:3E:5D:F6:E4   
          Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
Also, amend your settings to WLAN_8X, not Auto WLAN_8X.

---

### Post by cyberhood on 2010-04-04
ok, Changed to WLAN_8X (without Auto)

did the down - mode managed - up steps. no changes.
I went into Network Manager - Wireless - clickd on WLAN_8X - Edit - Wireless tab and I see my SSID & the mode is set to Ad-hoc.  There's only one more option - Infrastructure...

---

### Post by chili555 on 2010-04-04
Infrastructure. That's what Managed is called sometimes in some places in the world. Go for it!

---

### Post by cyberhood on 2010-04-04
No change.

The BSSID & MAC address spaces are blank.  Should they be filled in too?

curiosity: I don't quite understand how we got "Auto WLAN_8X" to appear in the ESSID when the iwconfig prompt was executed before, but now, after "WLAN_8X" has been created (the one that actually exists) & Mode reads "Managed" ESSID looks like this: " "... empty ::headscratch emoticon::

---

### Post by cyberhood on 2010-04-05
Are you sure this isn't a driver issue?

---

### Post by chili555 on 2010-04-05
It certainly could be. Do you want to try another?

---

### Post by cyberhood on 2010-04-05
OK, but remember (from post #1) I haven't touched the packaged Linux driver yet.  I only unzipped it and got completely confused when I read the "instructions" on how to compile it.  I had no problems following the instructions for the old driver in the trunk - which were written by either a native English speaker, or a techie to layman translator, or both... either way it was legible and followable.  If you want I can send you the driver stuff that I have, if that would be of any help.  To my knowledge the one it came with isn't even compiled yet.  
Check your PM for the rest of the router saga.
Here are the specs on the dongle:
> The drivers for Windows and Linux, Mac are included.
Full Compatibility with Turbo-G and Wireless-G

The AirLive Wireless-N family is fully compatible with Turbo-G and Wireless-G devices. In fact, they
will run at full Turbo speed when linking with Turbo-G products. Therefore, you can get the maximum
performance out of your legacy equipments. The AirLive Wireless-N technology protects your current
investment while making your wireless network ready for the future. complete product description and specs here: [http://www.airlive.com/product/product_3.jsp?pdid=PD1234297283834](http://www.airlive.com/product/product_3.jsp?pdid=PD1234297283834)

driver .rar can be found here: [http://www.airlive.com/support/support_3a.jsp?pdid=PD1234297283834](http://www.airlive.com/support/support_3a.jsp?pdid=PD1234297283834)

thanks

---

### Post by chili555 on 2010-04-05
Before we have some fun, please do:```
uname -r
sudo updatedb
locate rt2870sta.ko
```Just workin' a hunch here...

---

### Post by cyberhood on 2010-04-05
comes up with:
```
~$ uname -r
2.6.31-14-generic
~$ sudo updateb
sudo: updateb: command not found
~$ locate rt2870sta.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
```

does that mean it's there?

---

### Post by chili555 on 2010-04-05
You have the driver on your system now, but it doesn't grab your device. Let's see if we can force it. Please do:```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1b75 3072" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig
```Let me know the outcome. If it works, we still have a step or two to complete.

---

### Post by cyberhood on 2010-04-05
outcome ...
```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1b75 3072" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1b75 3072" > /sys/bus/usb/drivers/rt2870/new_id
~$ sudo modprobe rt2870sta
~$ dmesg | egrep 'rt28|usb|Phy'
[    0.117120] usbcore: registered new interface driver usbfs
[    0.117160] usbcore: registered new interface driver hub
[    0.117220] usbcore: registered new device driver usb
[    0.952195] usb usb1: configuration #1 chosen from 1 choice
[    0.952837] usb usb2: configuration #1 chosen from 1 choice
[    0.953326] usb usb3: configuration #1 chosen from 1 choice
[    0.953793] usb usb4: configuration #1 chosen from 1 choice
[    0.954253] usb usb5: configuration #1 chosen from 1 choice
[    1.268089] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.447426] usb 1-1: configuration #1 chosen from 1 choice
[    1.765369] usb 1-5: new high speed USB device using ehci_hcd and address 5
[    2.045066] usb 1-5: configuration #1 chosen from 1 choice
[    2.074673] usbcore: registered new interface driver usb-storage
[    2.083901] usb-storage: device found at 5
[    2.083907] usb-storage: waiting for device to settle before scanning
[    2.197094] usb 1-6: new high speed USB device using ehci_hcd and address 6
[    2.408199] usb 1-6: configuration #1 chosen from 1 choice
[    2.425279] usb-storage: device found at 6
[    2.425285] usb-storage: waiting for device to settle before scanning
[    2.693208] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    2.884254] usb 3-1: configuration #1 chosen from 1 choice
[    2.902078] usbcore: registered new interface driver hiddev
[    2.906909] input: MLK USB Multi-Smart Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3
[    2.907121] generic-usb 0003:04FC:0801.0001: input,hidraw0: USB HID v1.11 Mouse [MLK USB Multi-Smart Mouse] on usb-0000:00:1d.1-1/input0
[    2.907158] usbcore: registered new interface driver usbhid
[    2.907165] usbhid: v2.6:USB HID core driver
[    3.125475] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    3.313234] usb 3-2: configuration #1 chosen from 1 choice
[    3.331741] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4
[    3.331891] generic-usb 0003:0603:00F2.0002: input,hidraw1: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:1d.1-2/input0
[    3.368201] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input5
[    3.368428] generic-usb 0003:0603:00F2.0003: input,hiddev96,hidraw2: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:1d.1-2/input1
[    5.007073] Registered led device: rt2800usb-phy0::radio
[    5.007113] Registered led device: rt2800usb-phy0::assoc
[    5.007151] Registered led device: rt2800usb-phy0::quality
[    5.007860] usbcore: registered new interface driver rt2800usb
[    6.478431] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin
[    7.089177] usb-storage: device scan complete
[    7.424524] usb-storage: device scan complete
[ 7787.698935] usb 1-5: USB disconnect, address 5
[ 9479.072026] usb 1-5: new high speed USB device using ehci_hcd and address 7
[ 9479.206828] usb 1-5: configuration #1 chosen from 1 choice
[ 9479.210291] usb-storage: device found at 7
[ 9479.210296] usb-storage: waiting for device to settle before scanning
[ 9484.208339] usb-storage: device scan complete
[ 9676.132171] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 9676.143865] rtusb init --->
[ 9676.143963] usbcore: registered new interface driver rt2870
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by chili555 on 2010-04-05
> I've blacklisted "rt2800usb" already because that's what the cool kids were doingAlrighty then! Now we're getting somewhere.

Now, please blacklist rt2800usb, rt2x00lib and rt2x00usb. Next, please do:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Reboot and give me a good report.

PS - Now that we are at 100 posts, I guess I could concede that it's a nightmare.

---

### Post by cyberhood on 2010-04-05
blacklist.conf now looks like this:
```

blacklist amd76x_edac
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00usb
```
in the terminal:

```
sudo mousepad /etc/modprobe.d/blacklist.conf
~$ sudo su
# echo rt2870sta >> /etc/modules
# exit
exit
```
rebooting...

100 posts and almost 1000 views!  That _must_ mean others are on this nightmare ghostship of fools following the whole thing!  Don't worry boys.... land hoooooooo!!!!!!!!!!!!!

---

### Post by cyberhood on 2010-04-05
OK, when the computer rebooted the (default) network manager symbol begins to spin clockwise like it's thinking.  A window opens, without prompting, asking me for my Wireless Network Authentication Key.  I type it in... hit 'connect'.... it thinks for a while... and the window appears again.

note: I don't know the default network program that comes with Xubuntu but I don't think it's the traditional Network Manager that most people are used to.  I looks a little different & it's more minimalistic.  Anyway, even though it should do the same thing I'm gonna grab Wicd once I have establish a cabled connection to the router sometime this week.  I'm just more comfortable with its GUI than whatever Xubuntu comes with.

---

### Post by cyberhood on 2010-04-05
drat! rebooted again... key interrogation window pops up again (which I guess is a step forward since that didn't happen before)... enter the key again... thinks... window appears again.

I'm CERTAIN about the key.  I had it written down before to connect with the computer I'm currently using.  This afternoon when I checked out the router I copied the key down once again.  It's EXACTLY the one I had before and that everyone I know is connecting with.  Why does it keep asking me for the key?

---

### Post by chili555 on 2010-04-05
The router doesn't like the key, either the length or the case or something. Can you right click the icon and edit connections and delete the prior profile WLAN8_X you created and see if Network Manager figures it out by itself?> (which I guess is a step forward since that didn't happen before)Yes, indeed!

---

### Post by cyberhood on 2010-04-05
Right-clicked on networking icon - Edit Connections... - Wireless tab - highlighted previously created wireless connection point - delete button - close - reboot - nothing.

---

### Post by chili555 on 2010-04-05
When you click the NM icon, do you see your network? When you ask it to connect, are you prompted for the key? Does it pop up with WEP 40/128-bit HEX? How many digits are in your key? Did you remove any and all settings in NM?

---

### Post by cyberhood on 2010-04-06
[SOLVED!]...got it working!!

Thanks chili, couldn't have done it without ya!!

I hope we helped some others along the way...

---

### Post by danhilu on 2010-05-03
Hello cyberhood and chili555
this few words to thank you both for this excellent work. You've saved the config of my wife who hopefully won't give up xubuntu now.
I've shared a sumary of my config and changes here
[http://ubuntuforums.org/showthread.php?p=9228644](http://ubuntuforums.org/showthread.php?p=9228644)
because it was more specific to my config (Xubuntu 9.10 karmic, 
Wifi USB key Edimax EW-7711UTn).
Thanks again,
Daniel.

---

### Post by cyberhood on 2010-05-17
> **danhilu said:**
> Hello cyberhood and chili555
this few words to thank you both for this excellent work. You've saved the config of my wife who hopefully won't give up xubuntu now.
I've shared a sumary of my config and changes here
[http://ubuntuforums.org/showthread.php?p=9228644](http://ubuntuforums.org/showthread.php?p=9228644)
because it was more specific to my config (Xubuntu 9.10 karmic, 
Wifi USB key Edimax EW-7711UTn).
Thanks again,
Daniel.
Hey cool. Glad to hear that we were able to help out others along the way & keep a user in the community! :)

---

