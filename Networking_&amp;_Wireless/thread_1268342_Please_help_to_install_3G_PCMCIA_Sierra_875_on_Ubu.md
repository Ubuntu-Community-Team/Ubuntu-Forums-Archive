---
title: "Please help to install 3G PCMCIA Sierra 875 on Ubuntu Jaunty"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by hendraeffendi on 2009-09-16
I wisth to install 3G modem PCMCIA Sierra 875 on Ubuntu 9.04. Do anybody work with this before? I've tried a little using umtsmon but it doesn't work. I read several time in Internet forum and I found everybody come with same problem with me. Also I tried using pppd but error came like following. 

-----------------------------------------
Setting the abort string

Initializing modem

Setting APN

Dialing...
Script /usr/sbin/chat -v -t6 -f /etc/ppp/peers/gsm_chat finished (pid 6720), status = 0x0
Serial connection established.
using channel 4
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7c53eea4> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0xd7f700> <pcomp> <accomp>]
sent [LCP ConfNak id=0x0 <auth pap>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x7c53eea4> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <auth pap> <magic 0xd7f700> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <asyncmap 0x0> <auth pap> <magic 0xd7f700> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x7c53eea4]
sent [PAP AuthReq id=0x1 user="ccie-lab" password=<hidden>]
rcvd [LCP DiscReq id=0x2 magic=0xd7f700]
rcvd [LCP EchoRep id=0x0 magic=0xd7f700 7c 53 ee a4]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [LCP ProtRej id=0x3 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Modem hangup
Connection terminated.
------------------------------------------


actually, I think my PCMCIA modem is already detected. It can be seen on following
---------------------------------------------------
ce using ohci_hcd and address 2
Sep 17 07:19:17 ccie-lab kernel: [ 1862.041246] usb 8-1: configuration #1 chosen from 1 choice
Sep 17 07:19:17 ccie-lab kernel: [ 1862.048329] sierra 8-1:1.0: Sierra USB modem converter detected
Sep 17 07:19:17 ccie-lab kernel: [ 1862.053239] usb 8-1: Sierra USB modem converter now attached to ttyUSB0
Sep 17 07:19:17 ccie-lab kernel: [ 1862.053336] usb 8-1: Sierra USB modem converter now attached to ttyUSB1
Sep 17 07:19:17 ccie-lab kernel: [ 1862.053430] usb 8-1: Sierra USB modem converter now attached to ttyUSB2
----------------------------------------------------
But, I don't know why LED in the PCMCIA doesn't on.

Please advice.
Thanks

---

### Post by s03r on 2009-10-13
I've been using the same modem on Jaunty, but I rarely use NetworkManager because it has problem detecting the "device mobile broadband capability". I couldn't use umtsmon either, I don't know why, and I haven't got the time to dig into the problem yet. 

For sure, I can still use wvdial to connect to the internet with this modem, but I have to install it manually (by downloading the packages needed and install with dpkg) since I didn't have any alternative network to install it with apt-get.

After that you can edit /etc/wvdial.conf to fill in your provider settings. Google around, there a lot of examples for this.

I agree that it seemed that your modem was already detected, but I'm not really sure why the LED wasn't on. Have you try to eject and insert the device by "pccardctl" command in terminal?

$ sudo pccardctl eject
$ sudo pccardctl insert

Or just try to dial anyway with wvdial.
Let's see what happens. :)

---

