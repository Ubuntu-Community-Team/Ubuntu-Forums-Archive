---
title: "EVDO: Sierra Wireless AirCard 580"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by carpy on 2006-07-11
Many EVDO cards work under Linux.  Sometimes modifying what works on one card works for another (like the vendor and product IDs).  

This card is specifically a Qualcomm 3G CDMA card, labeled as a Sierra Wireless AirCard 580.  These directions will be for connecting to SprintPCS, although the directions should be very similar.

My system is a Kubuntu  6.06 (Dapper) install.


Here are some great howto's for other cards.  Perhaps you can take this Dapper setup for AirCard 580 and modify it for your system/card.

[http://www.ka9q.net/5220.html](http://www.ka9q.net/5220.html)
[http://www.cs.drexel.edu/~kfu22/evdo/](http://www.cs.drexel.edu/~kfu22/evdo/)
[http://debiana.net/aircard580.html](http://debiana.net/aircard580.html)  (this card, different provider, some stuff done differently)



Upon plugging in the card, it should register as a USB Controller with two USB devices.
These devices are usbserial devices, however unfortunately don't show up as such in Dapper.  Even loading the usbserial module doesn't get the desired results.  You can make it work by manually specifying "modprobe usbserial vendor=0x1199 product=0x0112"  (some similar cards will have different vendor/product numbers but will still work the same...  "lspci -vv" is your friend, as is /proc/bus/usb/devices)
Note:  This is unlike the 620 which loads the "airprime" module automagically.


*DON'T PANIC IF YOU LOG ERRORS WHEN FIRST PLUGGING IN THE CARD!*

The best results I've had have come from using HotPlug (yes, I realize there is likely a better way using hal/udev/dbus but I've not had time to learn them).  This was not my idea, I copied it verbatim from the aforementioned "debiana.net" article.

To get the card working under Dapper, the following items are completed:
* usb/hotplug setup  (/etc/hotplug/usb/sierra.usermap and /etc/hotplug/usb/AirCard580)
* ppp peer setup     (/etc/ppp/peers/1xevdo)
* ppp chat script    (/etc/ppp/peers/1xevdo_chat
* pap password       (/etc/ppp/pap-secrets   - perhaps unnecessary for some services)

So let's begin.  First we setup the USB Hotplug config.  This will automagically load usbserial with the appropriate "forcing" parameters after the card is inserted.  If your card uses different vendor or product IDs, you will want to change them here:

/etc/hotplug/usb/sierra.usermap  :
 # Sierra Aircard 580
 AirCard580  0x0003  0x1199  0x0112  0x0000  0x0000  0xff  0x00  0x00  0x00  0x00  0x00  0x00000000


/etc/hotplug/usb/AirCard580  :
 #!/bin/sh
 
 # Run everything in a subshell, so we can redirect the output
 # more easily.
 (
   # Load the module the right way
   /sbin/modprobe usbserial vendor=0x1199 product=0x0112  
 
   # Make the device node for the modem
   mknod /dev/ttyUSB0 c 188 0
 
 ) 2>&1 | logger -t aircard


/etc/ppp/peers/1xevdo  :
 -detach
 ttyUSB0
 115200
 debug
 noauth
 defaultroute
 usepeerdns
 user ##########@sprintpcs.com
 show-password
 lcp-echo-failure 0
 crtscts
 lock
 connect '/usr/sbin/chat -v -t3 -f /etc/ppp/peers/1xevdo_chat'

"lcp-echo-failure 0" may or may not be necessary.  I have found it to be necessary for my service provider.  ########## should be replaced by the 10-digit phone number associated with the card.  Do not include any hyphens ("-").

/etc/ppp/peers/1xevdo_chat  :
 '' 'AT'
 'OK' 'ATE0V1&F&D2&C1&C2S0=0'
 'OK' 'ATE0V1'
 'OK' 'ATS7=60'
 'OK' 'ATDT#777'

add to /etc/ppp/pap-secrets:
 ##########@sprintpcs.com   *  vzw

Note: ########## is the phone number associated with the 3G card.  The password, "vzw" should be correct for Verizon Wireless.... I don't believe SprintPCS requires a password... or at least it doesn't seem to care that I'm handing it the Verizon password :)



I am using the "lcp-echo-failure 0" option for *pppd 
(in /etc/ppp/peers/1xevdo)

Here is how my 580 card looks on success (notice the "hub 5-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?" error messages!  It still works!  Don't worry!):

syslog:
-------
Jul 11 16:41:31 localhost kernel: [17297024.892000] pccard: CardBus card inserted into slot 0
Jul 11 16:41:31 localhost kernel: [17297025.100000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
Jul 11 16:41:31 localhost kernel: [17297025.104000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
Jul 11 16:41:31 localhost kernel: [17297025.104000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul 11 16:41:31 localhost kernel: [17297025.104000] PCI: Setting latency timer of device 0000:03:00.0 to 64
Jul 11 16:41:31 localhost kernel: [17297025.104000] ohci_hcd 0000:03:00.0: OHCI Host Controller
Jul 11 16:41:31 localhost kernel: [17297025.104000] ohci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 5
Jul 11 16:41:31 localhost kernel: [17297025.104000] ohci_hcd 0000:03:00.0: irq 11, io mem 0xf8000000
Jul 11 16:41:31 localhost kernel: [17297025.204000] hub 5-0:1.0: USB hub found
Jul 11 16:41:31 localhost kernel: [17297025.204000] hub 5-0:1.0: 2 ports detected
Jul 11 16:41:33 localhost kernel: [17297027.124000] usb 5-1: new full speed USB device using ohci_hcd and address 2
Jul 11 16:41:35 localhost kernel: [17297028.968000] hub 5-0:1.0: Cannot enable port 1. *Maybe the USB cable is bad?
Jul 11 16:41:36 localhost kernel: [17297030.160000] hub 5-0:1.0: Cannot enable port 1. *Maybe the USB cable is bad?
Jul 11 16:41:37 localhost kernel: [17297031.352000] hub 5-0:1.0: Cannot enable port 1. *Maybe the USB cable is bad?
Jul 11 16:41:39 localhost kernel: [17297032.544000] hub 5-0:1.0: Cannot enable port 1. *Maybe the USB cable is bad?
Jul 11 16:41:39 localhost kernel: [17297032.848000] usb 5-1: new full speed USB device using ohci_hcd and address 6
Jul 11 16:41:39 localhost kernel: [17297033.104000] usbserial_generic 5-1:1.0: generic converter detected
Jul 11 16:41:39 localhost kernel: [17297033.104000] usb 5-1: generic converter now attached to ttyUSB0
Jul 11 16:41:39 localhost kernel: [17297033.108000] usbserial_generic 5-1:1.1: generic converter detected
Jul 11 16:41:39 localhost kernel: [17297033.108000] usb 5-1: generic converter now attached to ttyUSB1

matt@arwen:~$ sudo pppd call 1xevdo
Password:
Serial connection established.
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x31e05305> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x31e05305> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x31e05305> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x31e05305> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <asyncmap 0x0> <magic 0x97e27743> <pcomp> <accomp>]
sent [LCP ConfAck id=0x0 <asyncmap 0x0> <magic 0x97e27743> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x31e05305> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x31e05305> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x31e05305]
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> 
<ms-dns3 0.0.0.0>]
rcvd [LCP DiscReq id=0x1 magic=0x97e27743]
rcvd [LCP EchoRep id=0x0 magic=0x97e27743 31 e0 53 05]
rcvd [IPCP ConfReq id=0x2 <addr 68.28.153.69>]
sent [IPCP ConfAck id=0x2 <addr 68.28.153.69>]
rcvd [LCP ProtRej id=0x3 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <addr 70.9.2.125> <ms-dns1 68.28.154.11> <ms-dns3 
68.28.146.11>]
sent [IPCP ConfReq id=0x3 <addr 70.9.2.125> <ms-dns1 68.28.154.11> <ms-dns3 
68.28.146.11>]
rcvd [IPCP ConfAck id=0x3 <addr 70.9.2.125> <ms-dns1 68.28.154.11> <ms-dns3 
68.28.146.11>]
Cannot determine ethernet address for proxy ARP
local *IP address 70.9.2.125
remote IP address 68.28.153.69
primary * DNS address 68.28.154.11
secondary DNS address 68.28.146.11
Script /etc/ppp/ip-up started (pid 11709)
Script /etc/ppp/ip-up finished (pid 11709), status = 0x0


Here's what it looks like when I have no signal (or bad signal... sometimes even with the green flashy light):

$ sudo pppd call 1xevdo
Serial connection established.
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7a2bcb3f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7a2bcb3f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7a2bcb3f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7a2bcb3f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7a2bcb3f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7a2bcb3f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7a2bcb3f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7a2bcb3f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7a2bcb3f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7a2bcb3f> <pcomp> <accomp>]
LCP: timeout sending Config-Requests
Connection terminated.
Receive serial link is not 8-bit clean:
Problem: all had bit 7 set to 0
Modem hangup

 (WHAT?  What's that about bit 7?  Oh well... this is what it looks like :)


Hope this helps.
I also hope that the Ubuntu team incorporates the usbserial magic into the distro proper.
Matt

---

### Post by hesperant on 2006-08-11
I gave this method a shot and think perhaps there is something I am missing.

Did you do any configuration or installation prior to the script setups?
I notice that not even the directory structures or base files were created.

Hesperant

---

### Post by ujeezy on 2006-09-02
This tutorial worked great, thanks!!

---

