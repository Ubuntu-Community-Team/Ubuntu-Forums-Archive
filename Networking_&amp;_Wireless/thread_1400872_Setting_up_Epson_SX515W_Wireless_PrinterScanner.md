---
title: "Setting up Epson SX515W Wireless Printer/Scanner"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by ryanreed on 2010-02-07
Hi there,
I've used windows all of my life, and never really looked at Linux, so thought it would be a good time to see outside of the box! I installed Ubuntu 9.10 a couple of weeks ago after reading a few Linux Newbie books and deciding it would be the best distro for me. Being completely new with Linux it's proving difficult doing certain things which I would have done with a couple of clicks in Windows, however I've managed to get past some of the problems after hours of searching and messing about. I managed to set my wireless network up, and with a great struggle my wireless printer using cups- which now seems to be printing fine over the network, its IP is 192.168.0.105. However even after reading lots of info and tutorials on Forums & Blogs nothing seems to work regards to my scanner (which is an all-in-one printer [SX515W]("http://www.epson.co.uk/Store/Printers-and-All-in-Ones/Epson-Stylus-SX515W")).

The information is completely overwhelming. I've been told to use iscan with the network plugin which I downloaded from [www.avasys.jp]("http://www.avasys.jp") after installing and running image scan or xscan the printer would scan for a couple of seconds and then it would stop, and I'd have to reset my printer. I read the documents supplied, blogs, and forums telling me to do certain things such as:

```
sudo gedit /etc/sane.d/epkowa.conf 
add "net 192.168.0.105 1865"

sudo gedit /etc/sane.d/dll.conf
commented epson & epson2, added epkowa, enabled net

sudo gedit /etc/sane.d/net.conf
added 192.168.0.105

sudo gedit /etc/services
checked for sane 6566/tcp entry
```I don't really know what most of these edits do, and I'm getting a bit confused with scanning to a local usb printer, scanning to a server, and scanning directly to the network printer/scanning. But whats worse is I don't really know whats now installed! I've been told to uninstall/install libusb, different versions of iscan, libsane, sane-utils, and so on; it's making it even more overwhelming because I don't know what any of the programs do or if I even need them =[

The scanner no longer try's to scan, and when running image scan it gives me the error: "Could not send command to scanner, check the scanners status."

When I run sane-find-scanner the output is:
```

ryan@ryan-desktop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

**found USB scanner (vendor=0x7392, product=0x7711) at libusb:002:002**
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```which I guess says that it's found a scanner connected by USB? Even though I don't have a usb scanner...

scanimage -L gives me:

```

ryan@ryan-desktop:~$ scanimage -L
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
ryan@ryan-desktop:~$ 

```Like I said, being new to Linux I'm completely lost with what I'm doing or what I should be listing here! This is my last resort really, if I still can't get this thing working I may just give up because it's so stressfull! I don't know if anyone would be able to help me due to not knowing what I've installed/uninstalled, but I'd be so grateful if anyone does!

Regards


Ryan

---

### Post by ryanreed on 2010-02-07
Just restarted printer/scanner and now it gives me the following:


```
ryan@ryan-desktop:~$ scanimage -L
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
device `epson2:192.168.0.105' is a Epson PID flatbed scanner

```

---

### Post by gcolvin on 2010-02-11
Hey Ryan,
I too am new to Linux, and went through the same flail. As I said in my post, what worked for me was installing the avasys driver. My etc/sane.d/dll.conf file has two docs. iscan is the pertinent one. It reads as follows: 

# iscan -- enables the SANE backend(s) required
# Any changes to this file will be lost when upgrading iscan.
epkowa

disregard hplip file. Modifications to the other files did nothing for me.  Finally, the network address for the wifi all-in-one should be what you put in the epkowa.config file. Are you sure you haven't put your computer address there, b/c my computer address is 192.168.0.5. My all-in-one has its own address which is 192.168.0.197 which is what I entered in epkowa.config:  net 192.168.0.197. You should not need a port number; I think that pertains to wired (ethernet) settings. You can find the all-in-one IP address on the 610 by going to the menu>settings>network>confirm setiings option.   All this assumes you are trying to connect wifi. I hope this doesn't just confuse things more. Also, I found it easier to log in as root, and go to "places" menu and navigate to the desired files, then edit them in the file, as opposed to doing all this from the shell, which is cumbersome, being new to this myself.
Good Luck, gcolvin

---

### Post by quercus32 on 2010-07-09
Hi, I'm also having some slightly more basic issues with scanning using this device.

I've installed the avasys driver (epson-inkjet-printer-escpr_1.0.0-1lsb3.2_i386.deb on Ubuntu 9.10 Karmic).  The printing side works absolutely fine.

But I'm getting nowhere with scanning.  It sounds like I should be expecting this package to include the iscan application, but as far as I an see, it doesn't.  I also don't have any entries relating to epkowa in any of my sane configuration, as far as I can see.

When I run sane-find-scanner, or run scanimage -L, it appears to detect the scanner on the network, or that I have it connected via USB:

[INDENT][I]> sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x0856) at libusb:007:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
[/I][/INDENT]

[INDENT][I]> scanimage -L
device `epson2:192.168.1.105' is a Epson PID flatbed scanner
[/I][/INDENT]


Does anybody have this working (either via USB or network), who might be able to point me in the right direction?

When I run xsane, it gives me a scanner dialog, and info that is consistent with the output from scanimage -L.

But then scans fail with a "Failed to start scanner: Error during device I/O", or "Error during read..."

As I say, what concerns me is that the scanner appears to be visible, but I can't see any evidence that my scanning setup thinks it has a driver for it, despite having installed the escpr package.  Printing works flawlessly, so I don't think it's a networking / communications issue between the PC & device.  Sometimes the scanner appears to lurch into action, but fails immediately (and needs to be powered off to restart it).


Grateful for any pointers on this!

---

### Post by quercus32 on 2010-07-09
Update: I now have this working.

I realised that I need to install the iscan data and iscan packages as well as the escpr package from [http://www.avasys.jp]("http://www.avasys.jp").

It was a little hard to find... as far as I could see, the download page for scanners at Avasys didn't list my device (or anything remotely like it).  The download page for my "all-in-one" device only listed printer drivers, and not the image-scan packages.

In the end I just went to the scanner driver download page, selected a recent-looking device pretty much at random, and continued to the package download page.  The drivers available installed fine, and they work.

Note: you need to install iscan data before iscan, in order for iscan's dependencies to be satisfied.

---

### Post by gezzathorpe on 2010-10-09
Hi.. could you give me the details of how you set up the printer please?

---

### Post by mick8985 on 2010-10-11
Install this deb:
[http://ubuntuone.com/p/JiQ/](http://ubuntuone.com/p/JiQ/)

Then,

Install this if you have 32 bit:
[http://ubuntuone.com/p/JiR/](http://ubuntuone.com/p/JiR/)

Or, if you have 64 bit:
[http://ubuntuone.com/p/JiS/](http://ubuntuone.com/p/JiS/)

Edit: sorry Gezza I misread your post.
For me the printer was discovered by cups automatically.
System > Administration > Printing 
Click "Add" if the printer is not there already and just follow the steps

---

### Post by anksush on 2011-05-05
I have written two guides on the topic that address this issue. Links below:

[http://makegadgetswork.blogspot.com/2010/11/configure-epson-s515w-on-linux-mint.html]("http://makegadgetswork.blogspot.com/2010/11/configure-epson-s515w-on-linux-mint.html")

[http://makegadgetswork.blogspot.com/2011/05/part-2-configure-epson-s515w-on-linux.html]("http://makegadgetswork.blogspot.com/2011/05/part-2-configure-epson-s515w-on-linux.html")

Hope you find these useful.

---

