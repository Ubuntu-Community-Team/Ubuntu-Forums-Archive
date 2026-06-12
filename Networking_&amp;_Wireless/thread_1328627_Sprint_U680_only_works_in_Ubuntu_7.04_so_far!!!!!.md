---
title: "Sprint U680 only works in Ubuntu 7.04 so far!!!!!"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by brow5679 on 2009-11-16
Need help getting Sprint U680 to work in more Linux than Ubuntu 7.04.

---

### Post by pdc on 2009-11-16
you tell us what you have done:

to what extent does the 

"install on linux" section of this post help you?

[http://www.evdoinfo.com/content/view/2106/63/](http://www.evdoinfo.com/content/view/2106/63/)

what does 

> lsusb

and 

> sudo tail -f /var/log/messagessay with the modem plugged in?

copy and paste the results

---

### Post by brow5679 on 2009-11-16
Doing as you said it comes up:

Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 16d8:6803 CMOTECH Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and:

Nov 16 18:13:22 brow5679-desktop kernel: [  141.345841] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 16 18:13:22 brow5679-desktop kernel: [  141.347035] type=1503 audit(1258416802.351:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5927 profile="/usr/sbin/cupsd"
Nov 16 18:13:22 brow5679-desktop kernel: [  141.347055] type=1503 audit(1258416802.351:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5927 profile="/usr/sbin/cupsd"
Nov 16 18:13:22 brow5679-desktop kernel: [  141.347069] type=1503 audit(1258416802.351:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5927 profile="/usr/sbin/cupsd"
Nov 16 18:13:22 brow5679-desktop kernel: [  141.347083] type=1503 audit(1258416802.351:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5927 profile="/usr/sbin/cupsd"
Nov 16 18:13:22 brow5679-desktop kernel: [  141.347096] type=1503 audit(1258416802.351:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5927 profile="/usr/sbin/cupsd"
Nov 16 18:13:22 brow5679-desktop kernel: [  141.347110] type=1503 audit(1258416802.351:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5927 profile="/usr/sbin/cupsd"
Nov 16 18:13:22 brow5679-desktop kernel: [  141.347124] type=1503 audit(1258416802.351:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5927 profile="/usr/sbin/cupsd"
Nov 16 18:13:22 brow5679-desktop kernel: [  141.347137] type=1503 audit(1258416802.351:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5927 profile="/usr/sbin/cupsd"
Nov 16 18:13:22 brow5679-desktop kernel: [  141.347258] type=1503 audit(1258416802.351:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5927/net/dev" pid=5927 profile="/usr/sbin/cupsd"

---

### Post by brow5679 on 2009-11-16
That was in Ubuntu 8.10.  I have Ubuntu 7.04 working.

---

### Post by brow5679 on 2009-11-16
The "Install on Linux" is the same as what comes with the modem except what comes with the modem also tells me how to do Ubuntu 7.10 which does not work.  Again I have only gotten Ubuntu 7.04 to work.  I thank you for your trying to help so far.

---

### Post by pdc on 2009-11-16
try 

> sudo modprobe usbserial vendor=0x16d8 product=0x6803

and then 

> sudo ls ttyUSB*

and tell us what you get

and please make clear which operating system you have installed, and are using

---

### Post by pdc on 2009-11-16
so this device is basically a zeroCD device; that is, you need zero CDs to get it to work, as it has preloaded software, so is seen as a CD_ROM storage device; but it may have 3? types of linux software preloaded; an rpm version, and one assumes a .deb version;

the vendor ID product ID is likely the device in its usb storage mode state;

which country are you in? which provider are you with? If you have a working OS; and the modem works:

what about going with that ?

---

### Post by brow5679 on 2009-11-16
I am now trying to get it to work in Ubuntu 8.10.  As I said it works fine in Ubuntu 7.04.  The shell information was and now is  from Ubuntu 8.10.  The first sudo was accepted and nothing else come up but the second sudo tht is "sudo ls ttyUSB*"  it said this:


ls: cannot access ttyUSB*: No such file or directory

I am in USA and my OS are installed for the USA.  There are not the standard .deb drivers or otherwise just sh commands and what makes 7.04 work ./connect.

---

### Post by pdc on 2009-11-16
you need a programme called usb_modeswitch

google for it; latest version is 1.0.5 and they tell you how to get it from the debian site;

the latest version is said to be automated; so should do all for you; 



it should "flip" your device from storage device to modem

Google on 

> 16d8:6803 CMOTECH 

and you will find some background reading on your device: 

it is not a very common device; 

read this thread: a CDMA modem like yours

[http://ubuntuforums.org/showthread.php?t=1320700](http://ubuntuforums.org/showthread.php?t=1320700)

---

### Post by brow5679 on 2009-11-17
Well the older modeswitch installed easily but I could not figure out how to use it.  I tried to install the newest one but said I needed tcl|tclsh which I could not find in .deb form.  I read the string you suggested but do not yet understand it.  I will work more tomorrow.  Thanks for all your help.  I will keep working on it..

---

### Post by pdc on 2009-11-17
okay; here is a bit of homework for you;

this posting

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=69](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=69)

is a guy talking about getting your modem running; using modeswitch

________________

Next thing:

if you use the find function on a browser, and go through the conf file for modeswitch, your modem is listed

[http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf](http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf)

(eg search under DefaultVendor=  0x16d8 and it is called C-motech D-50 (aka "CDU-680")

the instructions at the top of the file (inside commented # signs) say

> # Just set or remove the comment signs (# and ;) in order to activate # your device. (Actual entries are further down, after the reference.)

so you can clean the file up to just the reference to your device

so the command

> usb_modeswitch -v 0x16d8 -p 0x6803 -m 0x07 -M 5553424308e0408524000000800008ff524445564348470000000000000000

(all one line) your device should switch from storage to modem;

and the various other files should automate that, so you don't have to do it each time;

but as I understand it, if you install usb_modeswitch, and use the above command, your modem should appear for a once off config;

(and the conf file issues the above command each time, I understand .........)

anyway, a bit more homework for you above:

linux is the thinking (wo)man's operating system; you end up understanding some of how it works ............. !!

---

### Post by brow5679 on 2009-11-17
I have found the C-motech D-50 in /etc/usb_modeswitch.conf.  And have installed it for the automatic finding but it still complains that it cannot find if as default device and does not work.

---

### Post by 2TallSwede on 2009-11-18
I've used the Franklin branded version, cdu-680, for over a year now without problems...up until a couple of weeks ago ([http://ubuntuforums.org/showthread.php?t=1290634&highlight=cdu-680](http://ubuntuforums.org/showthread.php?t=1290634&highlight=cdu-680)). Now, using 9.10, it doesn't work anymore or at least I can't get the mode switched. I haven't been able to get usb_modeswitch to work either.

The method I used in the link above worked with the 9.10RC but something changed with the final release. I'm not sure what but something screwed it up and it command to switch the interface to modem doesn't work anymore.

---

### Post by 2TallSwede on 2009-11-18
Found this solution over in another thread ([http://ubuntuforums.org/showthread.php?t=1304745&highlight=wireless+broadband+karmic](http://ubuntuforums.org/showthread.php?t=1304745&highlight=wireless+broadband+karmic))

Type this into terminal:

sudo rmmod usb-storage
sudo modprobe -r option
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x16d8 product=0x6803

This works in 9.10 and at this point, you can connect using the connection manager. One quick note though: speed is limited to about 500k with this solution but at least it works.

---

### Post by brow5679 on 2009-11-19
I installed 9.10 and tried sudo rmmod usb-storage and it said the modem was already mounted.  I did the rest and it excepted it but it did not start up the modem.  I tried it by unmounting the modem and tried again and it excepted all commands but still not modem.  What connection manager are you using.  I tried on just for Sprint but still no hookup.  Have you any ideas?

---

### Post by 2TallSwede on 2009-11-24
> **brow5679 said:**
> I installed 9.10 and tried sudo rmmod usb-storage and it said the modem was already mounted.  I did the rest and it excepted it but it did not start up the modem.  I tried it by unmounting the modem and tried again and it excepted all commands but still not modem.  What connection manager are you using.  I tried on just for Sprint but still no hookup.  Have you any ideas?

For me, once I plug the modem in, after a few seconds a folder window pops up what shows the content of the USB drive. At this point it, if I run the rmmod command I get an error saying the USB drive is in use. If I run the command immediately after I plug it in, it works.

I'm using the default NetworkManagerApplet with Karmic.

---

### Post by brow5679 on 2009-11-24
I do not know what I am doing wrong.  I get the pop up window with U680 and run the commands but the modem is not in the network manager.  It has the CDMA to set up but I cannot set it up.  I have not had so much trouble with other devices in Linux as this one.  I still can only get U680 to work in 7.04.

---

### Post by brow5679 on 2009-12-02
Has anybody gotten Sprint U680 to go in Ubuntu 7.10?  It says it should in my drivers. I still have it working only in ubuntu 7.04.

---

### Post by zero-n on 2009-12-19
I think this **[COLOR="Red"][program]("http://www.4shared.com/file/133986371/74edf4f0/cmotech-qtmodem_19_all.html")[/COLOR]** will help you.

---

### Post by brow5679 on 2009-12-22
How will the editor vim help me.  I cannot use apt-get because I do not have the Sprint u680 going in anything but ubuntu 7.04.  Ubuntu 7.04 is not supported anymore so I can not use spt-get there either.  I would like to get Sprint u680 going in Ubuntu 9.10 the most. I appreciate your help.

---

### Post by zero-n on 2009-12-22
It seems that you got me wrong.

sudo apt-get install vim is my **[COLOR="Red"]Signature[/COLOR]** not a part of my response.

Your U680 modem is produced by **[Cmotech]("http://www.cmotech.com/")** a Korean company. i am using another product from the same company and i have there linux program as .deb package you can download it from **[here]("http://www.4shared.com/file/133986371/74edf4f0/cmotech-qtmodem_19_all.html")**.

try it i hope it will work with you.

---

### Post by brow5679 on 2009-12-23
I have the CMO program installed in 9.10.  A form comes up and says to plug in the modem and I have it plugged in and the program shows me no modem.  How do you use this program?  Thanks for your help.

---

### Post by pdc on 2009-12-23
Hi brow5679; you are still working away on this modem problem; 

kind of curious: if it worked on 7.04, why change?

tell us what provider you want to log into: 

the programme wvdial may help you if we can work out what company you need to connect to ...........

---

### Post by brow5679 on 2009-12-23
I use Sprint for the provider.  The files on my modem tell me how to use Ubuntu 7.04 and 7.10.  I have not gotten 7.10 to work even though it says I should.  I hove not gotten any other Linux to work except ubuntu 7.04 and I have tried to get many other Linux such as SuSE etc.  I do not want to use 7.04 only because I cannot get the graphics to work in my Laptops.  That is why I cannot use only 7.04.  Thank you again.

---

