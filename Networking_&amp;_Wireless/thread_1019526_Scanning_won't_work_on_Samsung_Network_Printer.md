---
title: "Scanning won't work on Samsung Network Printer"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by costre on 2008-12-23
Hello, this is about a Samsung CLX-2160N, a network printer/scanner.

I didn't have any problems connecting and configuring this printer for printing jobs. It is connected to my router via RJ45 cable, and my computer connects through the wireless ethernet card to the router and prints without a problem.

But the scanning function doesn't seem to work. Using XSane, all I get when starting the program is 

```
 Couldn't open device 'v4l:/dev/video0' 
Invalid argument 
```

All I did when configuring the printer was to connect network printer, type in the IP-address, and that was it. 

How do I make Ubuntu connect to the proper location to make my network scanner work?

---

### Post by transformania on 2009-03-29
I have a CLX-3175FN; same problem.

I decided to check to see how it was set up to work in Vista, and there are three different executables excepted in the firewall for scanning.  When doing an actual scan, it seems to be connecting on port 9400.

That's about as far as I've gotten; no solution yet.  USB scanning under Ubuntu works fine.

---

### Post by Dngrsone on 2009-11-02
I have a Samsung CLX-3175FN, as well, and looking to get the scanner working over the network.

So far, I have found this information for xsane:

```
# Samsung CLX-3170 Series

SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="342a", MODE="0664", RUN+="libusbscanner", ENV{libsane_matched}="yes"
```

I also have [this site](http://www.sane-project.org/lists/sane-backends-cvs.html#SCANNERS), which lists [xerox_mfp (1.0-11)](http://www.sane-project.org/man/sane-xerox_mfp.5.html) as the backend driver.

I just have to figure out how to put it all together.

---

### Post by Dngrsone on 2012-04-19
Kind of old thread, I know, but I did get my scanner working and this is how I did it:


I am currently using Ubuntu 12.04-beta2-desktop-amd64 with the scanner connected to the local network.

This is what I did, based on information from the [this thread](http://ubuntuforums.org/showthread.php?t=1920543) and the [Samsung Unified Linux Driver Repository](http://www.bchemnet.com/suldr/).

I uninstallaed the drivers I downloaded and installed from the Samsung website.

Then I added the repository by editing /etc/apt/sources.list and adding the following line:

```
deb http://www.bchemnet.com/suldr/ debian extra
```

I then installed the GPG key:

```
sudo wget -O - http://www.bchemnet.com/suldr/suldr.gpg | sudo apt-key add -
```

Follw that up with:

```
sudo apt-get update
```

I downloaded the current repository (currently v 3.00.90 ), unzipped it, drilled down to the directory where I unzipped it and invoked the following:

```
sudo find . -type d -exec chmod 755 {}\;
```

Which will make everything that needs to be executable, well, *executable*.

I then ran the install.sh file to install my drivers.

Additionally, I had to do this:

```
sudo apt-get install samsungmfp-scanner
```

to install the scanner package.

Then this:

```
sudo /opt/Samsung/mfp/bin/netdiscovery --all --scanner >.samsung.netdiscovery 
```

to get the scanner seen over the network.

Now, the driver installed for the printer was for the CLX-3170, and it did not work correctly.  I opened up the Printing dialog, manually selected the CLX-3175splc driver, and then changed the printer URI to the printer (at its IP address) and "LPD network printer via DNS-SD"

Hopefully I got all the steps included there.

---

### Post by dvenema on 2012-11-27
Have been successfully using the CLX-3175fn with Ubuntu since Karmic with the following drivers:
[http://www.bchemnet.com/suldr/index.html](http://www.bchemnet.com/suldr/index.html)

I am now on 12.04 LTS and this also worked flawlessly until some weeks ago, it stopped scanning via LAN. I don't know exactly which update caused it.

Anyway, I solved it by following instructions on:
[http://wiki.ubuntuusers.de/Samsung-Laserdrucker](http://wiki.ubuntuusers.de/Samsung-Laserdrucker)

I only changed the settings in /etc/sane.d/xerox_mfp.conf and this worked immediately.

---

