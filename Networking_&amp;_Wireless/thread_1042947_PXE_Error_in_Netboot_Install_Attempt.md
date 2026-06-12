---
title: "PXE Error in Netboot Install Attempt"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by dunomous on 2009-01-18
******************************************
**Edit:** My issue is that I'm using Intel(R) Boot Agent Version 4.0.19, which basically doesn't allow PXE boot to work. As it stands, it is not as easily possible for me to flash the BIOS (**Note:** It is possible, but requires purchasing special drives that may not necessarily work). Please refer to [this thread]("http://ubuntuforums.org/showpost.php?p=6662604&postcount=20") for further information and error messages. 

>>>>>>>--------[My Solution]("http://ubuntuforums.org/showpost.php?p=6716237&postcount=26")--------<<<<<<<  **Please read the note post below/following it!!!**

I will keep this post updated as I can to save readers time from reading through the pages :D
******************************************

I am trying to install ubuntu (ibex) on a laptop from my laptop (running ibex). Thus, My laptop (host) to Router (DHCP disabled) to target laptop. I keep receiving an error during the PXE boot. It gets an IP address fine, but then throws the error:

pxe-t04 "missing mode"
pxe-e36 "error received from tftp server"
pxe-m0f "exiting intel pxe rom"


I don't know what "missing mode" means, and I can't find it anywhere online. Help is appreciated in advance, thank you!

---

### Post by nixscripter on 2009-01-18
This is a problem with the client or the server. From an [unrelated site]("https://services.netscreen.com/restricted/sigupdates/nsm-updates/HTML/TFTP:MISSING-MODE.html"):

> 
The Trivial File Transfer Protocol (TFTP) is a simplified version of File Transfer Protocol (FTP) used to upload or download files between machines on a network.
...
Three standard **modes** of data transfer are defined for TFTP: netascii, octet, and mail. 
...
A TFTP data packet must contain a string that identifies what mode of data transfer is being used. TFTP data packets that do not contain a mode string are protocol anomalies.
...
[A]nomalous packets may also be a result of incorrectly configured or badly implemented TFTP daemons and clients.


So, either your client or server isn't providing one, in violation of the protocol. My only suggestion: try a different TFTP server, and hope it's not the client (which is probably in the BIOS somewhere). Which one are you using?

---

### Post by dunomous on 2009-01-18
> **nixscripter said:**
> This is a problem with the client or the server. From an [unrelated site]("https://services.netscreen.com/restricted/sigupdates/nsm-updates/HTML/TFTP:MISSING-MODE.html"):



So, either your client or server isn't providing one, in violation of the protocol. My only suggestion: try a different TFTP server, and hope it's not the client (which is probably in the BIOS somewhere). Which one are you using?
I actually finally found this the last night. So, thank you for pointing it out. I set the mode to 1 or 0, I can't remember, which supposedly stands for one of the modes. I'm currently using tftp-hda. After I set the mode, it said again that the file could not be found, which I'm guessing is a bad dnsmasq configuration.

---

### Post by dunomous on 2009-01-18
Oh, and the client machine is a Sony Vaio PCG-R505GCP

---

### Post by nixscripter on 2009-01-19
So this means your mode problem has been fixed, and you need to find the file now, right?

Please post your tftp server and DNS configuration, and I'll take a look at it.

---

### Post by dunomous on 2009-01-19
> **nixscripter said:**
> So this means your mode problem has been fixed, and you need to find the file now, right?

Please post your tftp server and DNS configuration, and I'll take a look at it.

Not exactly, I have set a mode for it, but am unsure if the syntax is correct. 

```
#Defaults for tftpd-hpa
RUN_DAEMON="yes"
OPTIONS="-l -s /var/lib/tftpboot/"
mode="netascii"
```

dnsmasq.conf:

```
dhcp-range=192.168.0.2,192.168.0.99,48h
dhcp-host=(my wireless MAC address),192.168.0.100
dhcp-boot=/var/lib/tftpboot/pxelinux.0,(my hostname),192.168.0.100
```

The correct files should be in place (of the /var/lib/tftpboot folder), as they were copied straight from the alternate 8.10 iso netboot folder. The router, of course, is 192.168.0.1.

---

### Post by nixscripter on 2009-01-21
Try the "octet" mode instead. "netascii" is for like text, i.e. 7-bit characters. The loader, on the other hand, is unaltered binary.

---

### Post by dunomous on 2009-01-21
> **nixscripter said:**
> Try the "octet" mode instead. "netascii" is for like text, i.e. 7-bit characters. The loader, on the other hand, is unaltered binary.

I tried it, and still the same error. This is just so bizarre. I don't understand.

---

### Post by nixscripter on 2009-01-22
The only config file examples I can find on Google doesn't have the mode line. If you remove it, what happens?

EDIT: also, try making the word mode uppercase. Variables are probably case sensitive.

---

### Post by dunomous on 2009-01-22
> **nixscripter said:**
> The only config file examples I can find on Google doesn't have the mode line. If you remove it, what happens?

EDIT: also, try making the word mode uppercase. Variables are probably case sensitive.

With it removed, it returns the same error. Good idea about making "mode" uppercase. I will need to try that! I will let you know.

---

### Post by dunomous on 2009-01-22
Yeah, it still didn't work with it in uppercase. :(

---

### Post by nixscripter on 2009-01-23
I'm starting to wonder if, as I said earlier, it's the client's fault.

Silly question: do you have another computer you could try netbooting to see if it works?

If not, then you might try another TFTP server, such as **tftpd** from the package repository. You can find install instructions here: [http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

However, I would emphasize: if you have another client, try that first (go into the BIOS and make the network interface the first boot device).

---

### Post by dunomous on 2009-01-23
> **nixscripter said:**
> I'm starting to wonder if, as I said earlier, it's the client's fault.

Silly question: do you have another computer you could try netbooting to see if it works?

If not, then you might try another TFTP server, such as **tftpd** from the package repository. You can find install instructions here: [http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

However, I would emphasize: if you have another client, try that first (go into the BIOS and make the network interface the first boot device).

The only other machine I have is a windows box, so it's possible. I'm starting to think it is the client myself, as well. I may just go ahead and acquire the resources to find a ROM drive and use the Live CD. I hate giving up, though :( 

Why would having the network interface as first boot device be important? I ask because it always says to press F12 to boot from the network, which I do. I guess, I could give it a try. After that, I suppose, tftp is next.

---

### Post by nixscripter on 2009-01-24
I simply meant that the way to make that client (the one just to test it) netboot is to make the NIC the first boot device. That way you can test it without messing up the hard disk or other settings.

---

### Post by adante on 2009-01-26
Hi guys, I am also having the same problem. Exact same error as dunomous' first post. The laptop is a Toshiba TE2100. It runs Intel(R) Boot Agent Version 4.0.18 (see below as to why this may be important)

I don't quite understand what dunomous was talking about when he changed the mode of the server in the /etc/defaults/tftpd-hpa - anyway I tried those settings but nothing worked.

Next I tried enabling the inbuilt dnsmasq tftpd server:

dnsmasq.conf:
```
dhcp-boot=/var/lib/tftpboot/pxelinux.0
enable-tftp
tftp-root=/var/lib/tftpboot
```

just for the record:

> $ ls /var/lib/tftpboot
netboot.tar.gz  pxelinux.0  pxelinux.cfg  ubuntu-installer


Then I stop tftpd-hpa and restart dnsmasq, and when I start the laptop it says a new shiny error:

> CLIENT MAC ADDR: blahblah
CLIENT IP: 192.168.1.245 MASK: 255.255.255.0 DHCP IP: 192.1681.18
GATEWAY IP: 192.168.1.18
TFTP.
PXE-T04: unsupported request from 192.168.1.245
PXE-E36: Error received from TFTP server
PXE-M0F: Exiting Intel PXE ROM.


I get in my syslog:

> Jan 26 19:37:17 pveer dnsmasq[11403]: DHCPDISCOVER(eth0) 00:a0:d1:d5:1a:46
Jan 26 19:37:17 pveer dnsmasq[11403]: DHCPOFFER(eth0) 192.168.1.245 00:a0:d1:d5:1a:46
Jan 26 19:37:18 pveer dnsmasq[11403]: DHCPREQUEST(eth0) 192.168.1.245 00:a0:d1:d5:1a:46
Jan 26 19:37:18 pveer dnsmasq[11403]: DHCPACK(eth0) 192.168.1.245 00:a0:d1:d5:1a:46
Jan 26 19:37:18 pveer dnsmasq[11403]: TFTP sent /var/lib/tftpboot/pxelinux.0 to 192.168.1.245
Jan 26 19:37:18 pveer dnsmasq[11403]: TFTP error 0 TFTP Aborted received from 192.168.1.245
Jan 26 19:37:18 pveer dnsmasq[11403]: TFTP failed sending /var/lib/tftpboot/pxelinux.0 to 192.168.1.245
Jan 26 19:37:18 pveer dnsmasq[11403]: TFTP unsupported request from 192.168.1.245

I don't know. Maybe now it is this error here: [http://syslinux.zytor.com/wiki/index.php/Hardware_Compatibility#Intel_Boot_Agent_4.0.19](http://syslinux.zytor.com/wiki/index.php/Hardware_Compatibility#Intel_Boot_Agent_4.0.19). I hope not, because this laptop has no cd/floppy so I can't upgrade bios without an o/s which needs a bios upgrade so catch 22 :)

dunomous: have you tried the inbuilt server? If you do, let me know. I'm going to see if I can get any luck netbooting with another comp maybe later.

---

### Post by nixscripter on 2009-01-26
I'm afraid I don't know much about the built-in TFTP server with dnsmasq, but just a quick question: your dhcp-boot line is **cp**xelinux.0, but your file is **p**xelinux.0. Shouldn't those be the same?

---

### Post by adante on 2009-01-27
> **nixscripter said:**
> I'm afraid I don't know much about the built-in TFTP server with dnsmasq, but just a quick question: your dhcp-boot line is **cp**xelinux.0, but your file is **p**xelinux.0. Shouldn't those be the same?

oh yes sorry that was a typo that was inserted when I was copying the lines from my dnsmasq.conf

---

### Post by dunomous on 2009-01-28
> **adante said:**
> dunomous: have you tried the inbuilt server? If you do, let me know. I'm going to see if I can get any luck netbooting with another comp maybe later.

Sorry about the delay! I have been busy and have not had a chance to work on it. I have not exclusively tried the built in tftp server, but will try it soon and let you know!

---

### Post by dunomous on 2009-02-02
Just letting you know, I have no forgotten, but still have been busy. Have you gotten any improvements?

---

### Post by nixscripter on 2009-02-02
I'm afraid it's pretty conclusive, with more research.

> A lot of people have reported problems with Intel Boot Agent 4.0.19 not performing the initial bootstrap correctly. On the other hand, versions 4.0.17, 4.0.21, and 4.1.01 have all been reported to work correctly. This problem also seems to occur on version 4.0.18 as well. You will likely see symptoms similar to the following bolded output from a Sony VAIO PCG-GRX520 Version R0216B0:

Intel(R) Boot Agent Version 4.0.18
Copyright (C) 1997-2001, Intel Corporation

CLIENT MAC ADDR: 08 00 42 42 42 42  GUID: D4E54B40-4B65-11C6-8C44-080042424242
CLIENT IP: 10.0.0.98  MASK: 255.0.0.0  DHCP IP: 10.0.0.17
GATEWAY IP: 10.0.0.17
TFTP.
PXE-T04: unsupported request from 10.0.0.98
PXE-E36: Error received from TFTP server
PXE-M0F: Exiting Intel PXE ROM.

If you have a card or system with Intel Boot Agent 4.0.19, please contact the manufacturer for an upgrade. 

...

If your network adapter is on the motherboard, you will probably need to request a BIOS upgrade from your system or motherboard vendor.

Alternatively, with a little bit of googling, one can locate BIOS image editors capable of replacing "Expansion ROM" images following the main BIOS. Using this technique, it's possible to extract and modify the UNDI network driver and/or the Intel Boot Agent Expansion ROM. 


([Source]("http://syslinux.zytor.com/wiki/index.php/Hardware_Compatibility"))

This is the third place I've found this advice. I'm afraid you're stuck unless you want to risk bricking it. :neutral:

---

### Post by dunomous on 2009-02-03
> **nixscripter said:**
> I'm afraid it's pretty conclusive, with more research.



([Source]("http://syslinux.zytor.com/wiki/index.php/Hardware_Compatibility"))

This is the third place I've found this advice. I'm afraid you're stuck unless you want to risk bricking it. :neutral:

Drats! I have version 4.0.19 :( The laptop was free, so, I don't mind taking the risk of bricking it. I'm just not sure how I could go about trying to flash the BIOS. The only ports seem to just be USB, and those aren't detected by the BIOS. There might be another port, though ... I'll have to look. In the meantime, any suggestions?

---

### Post by nixscripter on 2009-02-03
Google says upgrading the expansion ROM is quite messy, involving x86 assmebler which is beyond me.

The question is, why are you trying to netboot? If it's a Linux install, I know of several alternative ways to try and install it (floppy tricks, hard disk tricks) over a network.

---

### Post by dunomous on 2009-02-03
> **nixscripter said:**
> Google says upgrading the expansion ROM is quite messy, involving x86 assmebler which is beyond me.

The question is, why are you trying to netboot? If it's a Linux install, I know of several alternative ways to try and install it (floppy tricks, hard disk tricks) over a network.

The problem is, unless I missed a port, that it only has USB ports. No optical drive, no floppy drives. The BIOS does not recognize USB ports on boot. I tried hooking up an external optical drive, but it did not work. So, netboot seems to be the only option (outside of disassembling the laptop and hooking up the hard drive to a desktop and formatting it there.).

---

### Post by nixscripter on 2009-02-03
I'm afraid that disassembling it should be on the table (so to speak).

[http://www.shock-e.com/archives/2004/04/installing_windows_on_a_sony_v.html](http://www.shock-e.com/archives/2004/04/installing_windows_on_a_sony_v.html)

Supposed schematics: [http://www.eserviceinfo.com/download.php?fileid=25839](http://www.eserviceinfo.com/download.php?fileid=25839)

I'm afraid I'm out of options at this point. :neutral:

---

### Post by dunomous on 2009-02-05
> **nixscripter said:**
> I'm afraid that disassembling it should be on the table (so to speak).

[http://www.shock-e.com/archives/2004/04/installing_windows_on_a_sony_v.html](http://www.shock-e.com/archives/2004/04/installing_windows_on_a_sony_v.html)

Supposed schematics: [http://www.eserviceinfo.com/download.php?fileid=25839](http://www.eserviceinfo.com/download.php?fileid=25839)

I'm afraid I'm out of options at this point. :neutral:

Ah, thank you for the schematics. I will give it a try!

---

### Post by dunomous on 2009-02-11
> **nixscripter said:**
> I'm afraid that disassembling it should be on the table (so to speak).

[http://www.shock-e.com/archives/2004/04/installing_windows_on_a_sony_v.html](http://www.shock-e.com/archives/2004/04/installing_windows_on_a_sony_v.html)

Supposed schematics: [http://www.eserviceinfo.com/download.php?fileid=25839](http://www.eserviceinfo.com/download.php?fileid=25839)

I'm afraid I'm out of options at this point. :neutral:

So, I disassembled the laptop and put the drive into another laptop to test it. After trying to format it with a LiveCD, it is very apparent that the drive is damaged. Running badblocks leaves me stuck at 13.5% completion after a whole night's worth. During the check, and any other I/O test, it gives scores of I/O errors, mainly pertaining to buffer errors and bad blocks. If that is not enough, when it checks a certain sector, it gives the most atrocious platter scratching sound I can imagine (think nails to chalk board). 

So, I:
     1) Installed Xubuntu on a working drive (with an optical drive and LiveCD) in another laptop (that does not belong to me, but the drive does).
     2) Put the drive in my laptop. 

It now all works. A bit of a ridiculous solution for such a small and simple machine. If anyone needs any help on how I fixed all this, let me know.

**I must accredit those who helped me, and appreciate their help very much! That's mainly you, nixscripter.**

---

### Post by dunomous on 2009-02-13
Just to note, I did a reinstall on the drive that didn't work with an install. Apparently, all these errors were caused by using the original LiveCD. The machine I'm using is old/has little RAM. So, fix = using alternate (*the* alternate install iso, not just a different burn) install disk.

---

### Post by nixscripter on 2009-02-14
I'm glad you could at least get it installed.

Happy linuxing! :)

---

