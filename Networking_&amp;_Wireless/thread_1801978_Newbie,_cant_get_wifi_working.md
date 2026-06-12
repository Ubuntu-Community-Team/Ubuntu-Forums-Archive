---
title: "Newbie, cant get wifi working"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by kevineugenius on 2011-07-11
Working with a Dell Inspiron 6000 and installed Ubuntu 10.10 just to get familiar with some form of Linux and see if it can maybe be a solution for me later in life.  The wireless card is Dell's 1470 and the chip on the card is labelled BCM4311 so that's what I went for.  At first it showed an unconnected wired NIC and for wireless it said "no firmware", but now it doesnt say anything about either one of them, it says "no network devices available".  

I followed the instructions here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) for both "STA - No Internet Access" and "b43 - No Internet Access" and when it says to go to the additional drivers menu to enable the new driver, there's nothing on the list.  I then tried [https://help.ubuntu.com/10.10/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.10/internet/C/troubleshooting-wireless.html) that guide and [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) that one.  

Please remember I'm a newbie in your instructions.  Don't say things like "just run a qf13 on the PCL so the ergotron bus will be cleared, it's probably a thermawhatsit in conflict with the meatloaf kernel" as I won't have a clue how to execute said instruction.  More useful would be "open a terminal and type 'ireallyenjoynewcarpetting' then check if the output says 'blargh 010101' "

Thanks!

---

### Post by sanderd17 on 2011-07-11
Are you sure you got no error messages? Try the steps for the ubuntu wiki again and look really close for error messages.

---

### Post by Bucky Ball on 2011-07-11
Get online with a cable if you haven't already, get updates, check System>Administration>Additional drivers. That will possibly give you the STA driver, but your best bet is to open Synaptic Package Manager and install:

firmware-b43-installer
b43-fwcutter

Your card should be up in a jiffy, no need to faff about manually installing drivers. That's making it more complicated than it needs to be. ;)

---

### Post by kevineugenius on 2011-07-11
> **sanderd17 said:**
> Are you sure you got no error messages? Try the steps for the ubuntu wiki again and look really close for error messages.

There were some errors, like the first time I tried to run one of the packages it said a different package was missing, so I browsed around to find that package and installed a tree of dependencies about 4-deep, but it still did nothing in the end.

To Bucky, when I open Synaptic Package Manager, is that showing stuff that is currently loaded?  b43-fwcutter is already on the list and from the notion that it gives me the option to remove it, I'm guessing it's one of the things I installed.  The other, firmware-b43-installer, is not listed.  Do I need to be plugged in to wired to find it?

At this point, I'm considering a fresh install because a left click on the network icon says "No network devices available" so I have a hunch that I broke the wired somehow when installing various other packages...

---

### Post by Bucky Ball on 2011-07-11
You should have both firmware-b43-installer and b43-fwcutter. If there is an STA driver enabled in 'additional drivers', disable it. You have done an update? Does all sound a bit strange. If a reinstall is not a problem then you'll learn a bit more about installing, but you might wind up with the same problem.

When you boot from the LiveCD with 'Try Ubuntu' do you get internet okay (through cable, don't attempt to get the wireless up when running from a CD boot if it doesn't come up 'automagically')?

---

### Post by kevineugenius on 2011-07-11
I don't actually have a wire available at the moment so I have done no updates, it's just a 10.10 CD that I downloaded a few months ago.  Upon fresh install I'm reminded of a list of errors that happened right after the initial restart.

[ 1591.xxxxxx] end_request: I/O error, dev sr0, sector yyyyyy

At least a full page of these with the x and y being different numbers for each line.

---

### Post by Bucky Ball on 2011-07-11
Perhaps try 10.04 LTS and see if you get the same results. Stabler. (and longer support)

---

### Post by smurphy_it on 2011-07-11
The i/o Errors are pointing to your cd/dvd drive.  That could give you grief.  I'd suggest booting off another LiveCD/DVD.  You can always download the 11.04 from [www.ubuntu.com](www.ubuntu.com)

After you download it, run a mdk5 check on it to validate the CRC is good, and then burn it to a cd/dvd - or put it as a live distro on a USB Flash drive.

Instructions for md5 checking I would assume are on the site.  If not, check the forums or google it.  Fairly easy to get going.

---

### Post by Bucky Ball on 2011-07-11
Best and safest is to download via torrent. mdk5 checked in the process. ;)

[http://www.ubuntu.com/download/ubuntu/alternative-download#bt](http://www.ubuntu.com/download/ubuntu/alternative-download#bt)

---

### Post by kevineugenius on 2011-07-11
When retrying the wiki guide and installing bcmwl-kernel-source it says "Dependency is not satisfiable: dkms" so I navigated to /pool/main/d/dkms and installed that as I did last time.  

Continued through step 1, installing the packages listed.  When I go to the Additional Drivers menu, though, there is nothing there.

I guess I'll just scrap the project until wired is available or I get back to school.  My home internet is so slow it'd take me three weeks to get another CD downloaded.

---

### Post by Bucky Ball on 2011-07-11
You really shouldn't need to do all this. If firmware-b43-installer is missing there is something amiss. It should be there along with b43-fwcutter and this card would be working.

---

### Post by kevineugenius on 2011-07-11
I went to Synaptic Package Manager and typed 'b43' into the search and nothing was there.  I don't have my flash drive today either, but tomorrow I would have a USB method of getting those two files onto the computer if that's an option?

---

### Post by nm_geo on 2011-07-11
> **kevineugenius said:**
> I went to Synaptic Package Manager and typed 'b43' into the search and nothing was there.  I don't have my flash drive today either, but tomorrow I would have a USB method of getting those two files onto the computer if that's an option?

Type _bcm_ in the search box and I think you will see firmware-b43-installer.

---

### Post by kevineugenius on 2011-07-11
bcm returns 
b43-fwcutter
bcmwl-kernel-source
bcmwl-modaliases
libklibc

---

### Post by nm_geo on 2011-07-11
> **kevineugenius said:**
> bcm returns 
b43-fwcutter
bcmwl-kernel-source
bcmwl-modaliases
libklibc

Ok I bet this new install has not been updated correct?

Let's do this in terminal.. with ethernet cable connected.

```
sudo apt-get update

```then 

```
sudo apt-get upgrade
```then 
```

sudo apt-get install firmware-b43-installer
```

---

### Post by nm_geo on 2011-07-11
Screenshot of my Synaptic in Maverick 10.10.  Note the orange selected line. please do not install what you see on my screenshot .. (it is a test)

---

### Post by kevineugenius on 2011-07-11
Yeah, that's the hiccup.  No ethernet available so no updates and no downloading stuff.  I didn't think it would be such an ordeal to USB over a driver but I tried multiple times.

---

### Post by nm_geo on 2011-07-11
Sorry on review I saw you had tried that one.

---

### Post by Bucky Ball on 2011-07-12
If you search for B43 they should both come up, but they don't, so that is tricky. With no internet, trickier again. 

One of the drivers is on the CD, think it is the STA. If you haven't tried that, insert the CD and add it to your software sources, update and try again.

---

