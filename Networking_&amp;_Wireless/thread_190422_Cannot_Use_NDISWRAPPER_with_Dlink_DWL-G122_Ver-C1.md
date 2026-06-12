---
title: "Cannot Use NDISWRAPPER with Dlink DWL-G122 Ver-C1"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by mtbuller on 2006-06-06
Hi all, I am totally new to Linux and had just installed Kubuntu.

Read about ndiswrapper and understand that it can make use of the windows drivers that comes with the USB wireless adapter.

Bought a Dlink DWL-G122 and to my surprise, the only driver provided for windows is a setup.exe

So, seems like cannot use ndiswrapper. 

1. Any idea how to proceed?

2. Not related to above but how can I add and try GNOME after I get DWL-G122 working.

Thanks.

---

### Post by mtbuller on 2006-06-06
anyone, please ?

---

### Post by dralaroc on 2006-06-07
Hey mtbuller,

I went to this page: [http://support.dlink.com/products/revision.asp?productId=DWL-G122](http://support.dlink.com/products/revision.asp?productId=DWL-G122) and I did not see a version C1.  I did download the A2 vers. and it did have a Netprism.inf and prismusb.sys files available. You might want to try it or any of the other vers. available for your adapter.  I have an old DWL 120 vers. D that works well with ndiswrapper,  hope this helps.


Edit: I remove my inf & sys file and installed that A2 vers. for the Dwl G122 and it worked.  Heck, give it a shot.

Another edit: Doh!  I googled your adapter, its for a mac and it uses the rt2500 chipset.  I was looking for pc drivers on the DLink site, sorry man!  Anyway, I would still give the A2 or subsequent vers. a shot with ndis and see if it works, also you might want to search the forum for folks using the rt 2500.  Sorry I could not be of more help, I am sure one of the forum vets will chime in and help ya out.

---

### Post by mtbuller on 2006-06-07
[QUOTE=dralaroc]Hey mtbuller,

I went to this page: [http://support.dlink.com/products/revision.asp?productId=DWL-G122](http://support.dlink.com/products/revision.asp?productId=DWL-G122) and I did not see a version C1.  I did download the A2 vers. and it did have a Netprism.inf and prismusb.sys files available. You might want to try it or any of the other vers. available for your adapter.  I have an old DWL 120 vers. D that works well with ndiswrapper,  hope this helps.
[/QUOTE]

Thanks **dralaroc**,

good to know that I've come to the right forum, I almost gave up waiting for help  ;) 

unfortunately, I've tried and doesn't seems to work.

I am trying out the Ralink's driver but when I comes to doing a "make config", konsole tells me that command not found. Any idea how I can get the 'make" command available when I cannot do any apt-get.

Looks like I may have a chicken and egg problem. ](*,) ](*,)

---

### Post by dralaroc on 2006-06-07
My brother in law has that same chipset.  I introduced him to breezy a few weeks ago and I could not get his card to work.  He's currently using a veery long ethernet cable :( .  I gotta get to work on finding a solution for him before he trips over that stupid cable.   As far as the "make config" stuff...I am clueless at the moment.  Hang in there man someone will come to your (my brother in law's) rescue ;) .  Have a good one!

---

### Post by dralaroc on 2006-06-07
Hey mtbuller,

I came across this thread: 

[http://www.ubuntuforums.org/showthread.php?t=188192&page=2&highlight=rt2500](http://www.ubuntuforums.org/showthread.php?t=188192&page=2&highlight=rt2500) 

and the link below provided by ariel seemed interesting.  It also explains how to    extract the needed files from the .exe.  According to forum member ariel "you don't need to download sources and recompile, just install the ndiswrapper package from synaptics"    

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver)

alright man hope that helps ya out or get ya going in the right direction.  Its bed time for this hombre.

---

### Post by mtbuller on 2006-06-07
[QUOTE=dralaroc]Hey mtbuller,

I came across this thread: 

[http://www.ubuntuforums.org/showthread.php?t=188192&page=2&highlight=rt2500](http://www.ubuntuforums.org/showthread.php?t=188192&page=2&highlight=rt2500) 

and the link below provided by ariel seemed interesting.  It also explains how to    extract the needed files from the .exe.  According to forum member ariel "you don't need to download sources and recompile, just install the ndiswrapper package from synaptics"    

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver)

alright man hope that helps ya out or get ya going in the right direction.  Its bed time for this hombre.[/QUOTE]

Thanks for the info.

I keep on trying and if anything good turns up. I'll keep you posted.

---

### Post by mtbuller on 2006-06-09
[QUOTE=dralaroc]My brother in law has that same chipset.  I introduced him to breezy a few weeks ago and I could not get his card to work.  He's currently using a veery long ethernet cable :( .  I gotta get to work on finding a solution for him before he trips over that stupid cable.   As far as the "make config" stuff...I am clueless at the moment.  Hang in there man someone will come to your (my brother in law's) rescue ;) .  Have a good one![/QUOTE]


Hi dralaroc,

good news, you can keep the "stupid cable". I've found [this]("http://www.linuxquestions.org/questions/showthread.php?p=2265682").

Enjoy

---

### Post by kris_kelvin on 2006-06-09
I've got the same dongle and got it working after plenty of research and hard work using the drivers provided by Ralink:
[http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

Download "RT73" drivers and follow the build instructions in README really carefully. Just do this one extra thing before you start: 
go to directory Module and find line starting with #define RTVID1. Change this line and the next one into this:[INDENT]
#define RTVID1              0x07d1      //ralink
#define RTPID1              0x3c03
[/INDENT]
(you can check if these are the correct values for you by command "lsusb", it should say something like this: "Bus 004 Device 002: ID 07d1:3c03 D-Link System")

Also after following the build instructions in README, remember to copy the driver to modules directory:
sudo cp rt73.ko /lib/modules/2.6.15-23-386/kernel/net/

Now try to "modprobe rt73" or just reboot. The driver should now recognize your usb dongle. The driver and the dongle work fine for me, however I'm having some problems with the usb in general - probably nothing to do with the driver or the dongle.

---

### Post by mtbuller on 2006-06-09
[QUOTE=kris_kelvin]I've got the same dongle and got it working after plenty of research and hard work using the drivers provided by Ralink:
[http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

Download "RT73" drivers and follow the build instructions in README really carefully. Just do this one extra thing before you start: 
go to directory Module and find line starting with #define RTVID1. Change this line and the next one into this:[INDENT]
#define RTVID1              0x07d1      //ralink
#define RTPID1              0x3c03
[/INDENT]
(you can check if these are the correct values for you by command "lsusb", it should say something like this: "Bus 004 Device 002: ID 07d1:3c03 D-Link System")

Also after following the build instructions in README, remember to copy the driver to modules directory:
sudo cp rt73.ko /lib/modules/2.6.15-23-386/kernel/net/

Now try to "modprobe rt73" or just reboot. The driver should now recognize your usb dongle. The driver and the dongle work fine for me, however I'm having some problems with the usb in general - probably nothing to do with the driver or the dongle.[/QUOTE]


Hi kris_kelvin,

thanks, I got it done too.

:D :D

---

### Post by b0rsten on 2006-07-14
i have the same usb-dongle, installing the driver worked correct for me but i can't connect to my wlan-network...

the network-applet in gnome shows me all reachable networks and if i try to connect to my network the "animation" starts but it won't connect...

my router "says" that my client is "connecting" but i can't connect :(

---

### Post by Grugs on 2006-08-08
> **kris_kelvin said:**
> I've got the same dongle and got it working after plenty of research and hard work using the drivers provided by Ralink:
[http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

Download "RT73" drivers 

Am I right is saying the "RT73" drivers are the ones that come from clicking on the "USB" below the "RT2571W/RT2671" heading (under the "Linux" heading) at [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)?

> **kris_kelvin said:**
> and follow the build instructions in README really carefully. Just do this one extra thing before you start: 
go to directory Module and find line starting with #define RTVID1. Change this line and the next one into this:[INDENT]
#define RTVID1              0x07d1       //ralink
#define RTPID1              0x3c03
[/INDENT]


Assuming yes, then after untarring the " RT73_Linux_STA_Drv1.0.3.6.tar.gz" file which comes from that link, which file in the Module directory has the must-be-changed line?  Not finding that line in any file, I instead added 
[INDENT]{USB_DEVICE(0x07d1, 0x3c03)}, /* D-Link */ \ [/INDENT]
directly below 
[INDENT]#define RT73_USB_DEVICES { \ [/INDENT]
in the Module/rtmp_def.h file (as per suggestions found at 
[http://aggrssive.olt.ubc.ca/viewItems.php?fID=1854](http://aggrssive.olt.ubc.ca/viewItems.php?fID=1854)  and also at [http://www.abclinuxu.cz/hardware/show/141296](http://www.abclinuxu.cz/hardware/show/141296)

> **kris_kelvin said:**
> 

Also after following the build instructions in README

The make all command produced a lot of "warning" messages in the console, do you know if that's irrelevant?

> **kris_kelvin said:**
> , remember to copy the driver to modules directory:

sudo cp rt73.ko /lib/modules/2.6.15-23-386/kernel/net/

Doing so makes rt73.ko the only .ko file my (equivalent?) /lib/modules/2.6.15-26/kernel/net directory, which otherwise contains only other directories (such as 8021q, appletalk, atm, ax25, bluetooth, bridge, to name a few - each of which seems to contain nothing but one or more .ko files.  So is this really the right directory for the rt73.ko file?  I suspect not, given that 

> **kris_kelvin said:**
> Now try to "modprobe rt73"

produces 

[INDENT]FATAL: Module rt73 not found.[/INDENT]

If, instead, I follow the instructions in the Module/README file and do

[INDENT]sudo insmod rt73.ko[/INDENT]

then I get

[INDENT]rtusb init ====>
usbcore: registered new driver rt73[/INDENT]

in /var/log/syslog, but when I then do 

[INDENT]ifconfig[/INDENT]

There's still no sign anything that looks like usb wireless dongle/adapter/stick/thingy - just the usual eth0 and lo, which is how I'm feeling.

What have I missed / done wrong?

---

### Post by Grugs on 2006-08-08
A further note:

[INDENT]ifconfig -a[/INDENT]

produces

[INDENT]rausb0    Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/INDENT]

and when I run

[INDENT]sudo ifconfig rausb0[/INDENT]

I get 


[INDENT]RT25usb Drvier version 1.0.0[/INDENT]

in /var/log/syslog and everything then freezes up leaving me with nothing do but press and hold down the (notebook) computer's power button until the computer turns off, and I cry.

(With the USB thing unplugged, I am able then to reboot, and smash my head against the wall some more.)

---

### Post by Grugs on 2006-08-10
I think I've got it.

After reboot, I ran lsmod just to see if the rt73 module I inserted (before the system crashed and I then shut down the computer) was still there.

[INDENT]lsmod | grep rt[/INDENT]

No mention of any rt73 modules, but there did seem to be another rt module:

[INDENT]parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
rt2570                184768  0
rtc                    13492  0
agpgart                34888  2 intel_agp
usbcore               130692  3 rt2570,uhci_hcd
[/INDENT]

Note the "rt2570".  I can't say for sure where this came from; perhaps its from my earlier efforts to get my USB stick working with a driver from rt2x00.serialmonkey.com.

Whatever.  If at this point I insert the rt73 module (from Ralink) with

[INDENT]sudo insmod Module/rt73.ko[/INDENT]

, when I then run

[INDENT]sudo ifconfig rausb0 up[/INDENT]

the system crashes and I have to power it down and restart it.

After restarting the computer, the rt2570 module was back and there was again no sign of the rt73 module.  The trick I've now got to work three times in a row is simply this: 

First remove the rt2570 module with

[INDENT]sudo rmmod rt2570[/INDENT]

and only then insert the rt73 module

[INDENT]sudo insmod Module/rt73.ko[/INDENT]

The /var/log/syslog file seems to raise an alarm:

[INDENT] rausb0 (WE) : Driver using old /proc/net/wireless support, please fix driver ![/INDENT]

But I ignored that and ran

[INDENT]sudo ifconfig rausb0 up[/INDENT]

to which /var/log/syslog responded:

[INDENT]rt73 driver version - 1.0.3.6[/INDENT]

and 

[INDENT]rausb0: no IPv6 routers present[/INDENT]

Curious.

When I now run 

[INDENT]iwlist scan[/INDENT]

where I immediately used to get

[INDENT]rausb0 No scan results[/INDENT]

I now, after a second or so, get

[INDENT]Cell 01 - Address: 00:12:17:71:33:01
                    ESSID:"Ninas linksys"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s
[/INDENT]

So I consider that success.  Now I just have to find Nina and ask her for her encryption key!

---

