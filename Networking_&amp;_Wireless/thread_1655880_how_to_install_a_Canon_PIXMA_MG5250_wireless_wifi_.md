---
title: "how to install a Canon PIXMA MG5250 wireless wifi printer ?"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by eljopc on 2010-12-30
I have a Canon PIXMA MG5250 stand alone wifi printer thats connected to all my windows computers and laptops. Now I want to install a computer with Ubuntu 10.10 and connect this printer also wireless by wifi.

is this possible, and how do i do this,do I need to download or configure this somewhere?

---

### Post by eljopc on 2011-01-02
Bump, Nobody?

---

### Post by thewarlord on 2011-01-03
hi,

i decide to buy this printer too.

have you checked the driver on the asia canon website?

[http://support-asia.canon-asia.com/P/search?model=PIXMA+MG5270&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MG5270&menu=download&filter=0&tagname=g_os&g_os=Linux)

please post if they work :)

---

### Post by eljopc on 2011-01-04
> **thewarlord said:**
> hi,

i decide to buy this printer too.

have you checked the driver on the asia canon website?

[http://support-asia.canon-asia.com/P/search?model=PIXMA+MG5270&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MG5270&menu=download&filter=0&tagname=g_os&g_os=Linux)

please post if they work :)

I also found on the normal website if you choose Linux drivers.  My problem is that I have no idea how to install tar.gz files.

If someone can tell me hw to install I will test them. I found some guides on tar balls but to complicated for me.

---

### Post by thewarlord on 2011-01-04
have you see the Debian Package: [http://support-asia.canon-asia.com/contents/ASIA/EN/0100301702.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100301702.html)

i think you don't need to compile the driver source files from the  normal canon homepage.

---

### Post by eljopc on 2011-01-04
I downloaded the DEb pack and unpacked it in the home folder. Than I opened in the unpacked folder the(deb) software thru the software center and installed the printer. Choose the network printer and it finds your wifi printer.

I also installed the scan software but this will not function It does not find my wifi scanner.

---

### Post by owg582pdu on 2011-01-27
Any one got the scanning working?

---

### Post by eljopc on 2011-01-29
> **owg582pdu said:**
> Any one got the scanning working?

Yes only the explenation is Dutch: 
[http://forum.ubuntu-nl.org/hardware-en-drivers/na-herinstall-door-te-veel-ellende-en-errors-hulp-nodig/msg691642/#msg691642](http://forum.ubuntu-nl.org/hardware-en-drivers/na-herinstall-door-te-veel-ellende-en-errors-hulp-nodig/msg691642/#msg691642)

---

### Post by sjosul on 2011-02-05
Scanner is easy: download the "MG5200series-scanner_driver.tar" software from the canon website [here]("http://software.canon-europe.com/software/0040260.asp?model="). Extract, and in the extracted folder, extract the "scangearmp-mg5200series-1.60-1-deb.tar.gz" file.

Install the software in the terminal by navigating to the folder you last extracted, and type:
```
sudo ./install.sh
```

Once installed, to run the software, in a terminal type:
```
scangearmp
```

Or, setup a new menu item called "Scanner" or "ScanGear" etc, and use the same command.

I found that when I first ran scangearmp, there was no identified scanner. there is a single button that will search for a scanner. Found it within seconds.

---

### Post by mytimps on 2011-03-24
> **eljopc said:**
> I downloaded the DEb pack and unpacked it in the home folder. Than I opened in the unpacked folder the(deb) software thru the software center and installed the printer. Choose the network printer and it finds your wifi printer.

I also installed the scan software but this will not function It does not find my wifi scanner.


THANK  YOU THANK YOU THANK YOU!!!!:popcorn:

---

### Post by Harpz on 2011-08-08
Hi
OK I'm new to Ubuntu and a total Ubuntu nub that said I'm enjoying the experience so far, 

I have a MP640 and have managed to get the printer side of the unit working but am stumped on the scanner side.

I've done the below but when i run scangearmg i get the following:

******_****@Anubis:~$ scangearmp
scangearmp: error while loading shared libraries: libcncpmsui.so: cannot open shared object file: No such file or directory

looking for any help please.

> **sjosul said:**
> Scanner is easy: download the "MG5200series-scanner_driver.tar" software from the canon website [here]("http://software.canon-europe.com/software/0040260.asp?model="). Extract, and in the extracted folder, extract the "scangearmp-mg5200series-1.60-1-deb.tar.gz" file.

Install the software in the terminal by navigating to the folder you last extracted, and type:
```
sudo ./install.sh
```

Once installed, to run the software, in a terminal type:
```
scangearmp
```

Or, setup a new menu item called "Scanner" or "ScanGear" etc, and use the same command.

I found that when I first ran scangearmp, there was no identified scanner. there is a single button that will search for a scanner. Found it within seconds.

---

