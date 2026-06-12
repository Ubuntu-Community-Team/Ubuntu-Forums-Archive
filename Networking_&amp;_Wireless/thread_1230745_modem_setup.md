---
title: "modem setup"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by jimn1547 on 2009-08-03
Trying to get modem going. found drivers and installed,       sudo wvdialconf/etc/wvdial conf  on command line......   found out needed to download wvdial -1 60tar and wvstreams-4.  Can't get local group to answer about modem code.           I think I just about got this going,could some body look this over to see if everything is right?       Ubuntu 9.04       Kernel 2.6.28-11-generic:D

---

### Post by wojox on 2009-08-03
Here's the modem help page:
[https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=modem&sa=Search](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=modem&sa=Search)

---

### Post by jimn1547 on 2009-08-03
Will someone help me get this going?:(

---

### Post by GeorgeVita on 2009-08-04
Hi **jimn1547**,

> **jimn1547 said:**
> Trying to get modem going. found drivers and installed,       sudo wvdialconf/etc/wvdial conf  on command line......   found out needed to download wvdial -1 60tar and wvstreams-4.  Can't get local group to answer about modem code.           I think I just about got this going,could some body look this over to see if everything is right?       Ubuntu 9.04       Kernel 2.6.28-11-generic:D

I am not sure if I can help you but if your problem is to get **wvdial** program and associated dependencies read:
[http://ubuntuforums.org/showthread.php?p=7245790#post7245790](http://ubuntuforums.org/showthread.php?p=7245790#post7245790)

Once you get the program (or if you already have it) we will try to fix the /etc/wvdial.conf file.

Regards,
George

---

### Post by jimn1547 on 2009-08-05
wvstreams-4.6.tar.gz     -----                wvdial-1.60.tar.gz       ------    in home folder............        tryied to unzip says can't find?:(

---

### Post by GeorgeVita on 2009-08-05
Hi **jimn1547**, you can do it if you follow instructions below:

> **GeorgeVita said:**
> ...At first I downloaded the following packages (from a pc connected to the internet, any O.S.):

1. [http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download](http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download)
2. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download)
3. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download)
4. [http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download](http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download)
5. [http://packages.ubuntu.com/jaunty/i386/wvdial/download](http://packages.ubuntu.com/jaunty/i386/wvdial/download)

**Note that above are all for an i386 pc.**

I copied all to a USB memory stick, and then paste them to the ubuntu 9.04 running pc into **/var/cache/apt/archives/** directory using **sudo nautilus** from terminal. Then I installed all packages by double clicking the icon of each .deb package **in above order** (1,2,3,4 and finally 5) ignoring any message. Finally (after installation) I run wvdialconf, edit the /etc/wvdial.conf file and connected with **sudo wvdial**!

You can find a .zip file to [http://acomelectronics.com/GeorgeVita/restore_wvdial.html](http://acomelectronics.com/GeorgeVita/restore_wvdial.html)
Regards,
George

---

### Post by jimn1547 on 2009-08-06
Scan Modem ran....Got drivers installed......Now wvdial has me stopped:  downloaded on floppy, where is the easyest place to put it so I can run the commands?     Tried to put in Home folder, says copy error in-out.                    :confused:

---

### Post by GeorgeVita on 2009-08-06
> **jimn1547 said:**
> Scan Modem ran....Got drivers installed......**Now wvdial has me stopped**:  downloaded on floppy, where is the easyest **place to put it** so I can run the commands?     Tried to put in Home folder, says copy error in-out.                    :confused:

To install **wvdial** you need also some other packages. The total is 5 .deb packages listed in my previous post. For Ubuntu Jaunty on a 386 CPU you can get [my .zip file]("http://acomelectronics.com/GeorgeVita/wvdial_904_i386.zip") unzip it and then use:```
sudo nautilus
```click on File System > var > cache > apt > archives to copy all (5) .deb files into **/var/cache/apt/archives/** directory (or use **sudo cp ...** command to copy them).

Double click the icon of the 1st .deb to install it. Continue with the next (install it) and then 3rd, 4th, 5th (last one). Reboot and will be there.

Regards,
George

---

### Post by jimn1547 on 2009-08-07
:)I don't understand your instructions.   I have the zip file.      Opened  >        "   file system>VAR>CACHE>ARCHIVES  "      I am there:             sudo cp file on command line: said not found...................How do you copy to Directory?

---

### Post by GeorgeVita on 2009-08-07
Hi **jimn1547**, I test the following and works (Ubuntu 9.04, i386):

1. **Get [wvdial_904_i386.zip]("http://acomelectronics.com/GeorgeVita/wvdial_904_i386.zip")** file
2. **Copy it to Desktop** of your Ubuntu 9.04 PC
3. Right click **wvdial_904_i386.zi**p and choose **Extract Here**
4. Double click on the directory **wvdial_904_i386** (created on Desktop)
5a. Double click on icon **libxplc0.3.13_0.3.13-1build1_i386.deb**
>>> a message will appear saying "Same version available in a sofware channel", click **Close**
>>> Click **Install Package** into 'Package Installer - libx...' window
>>> Give your password and press <Enter>
>>> Wait for the installation of this package, click **Close** when finished
>>> Close 'Package Installer - libx...' window
5b. Do the same as **5a** with icon **libwvstreams4.4-base_4.4.1-0.2ubuntu2_i386.deb**
5c. Do the same as **5a** with icon **libwvstreams4.4-extras_4.4.1-0.2ubuntu2_i386.deb**
5d. Do the same as **5a** with icon **libuniconf4.4_4.4.1-0.2ubuntu2_i386.deb**
5e. Do the same as **5a** with icon **wvdial_1.60.1+nmu2_i386.deb**

Hope now you can make it!

Regards,
George

P.S. please note that: 'As I am always a computing newbie, I do not know the best way to do the above. A more experienced person may can provide a simpler method.'

---

### Post by jimn1547 on 2009-08-08
:DThanks,all went well.    Installed evervthing.          Your download fixed the problem!    Discussion group told me what Drivers to download.......I wonder if there is a problem there too.   installed drivers,says: Modem should be found with  $sudo wvdialconf  /etc/wvdialconf   -      ran command says" No Modem"  -   No ports set up   -  durning scan ..    Scan Modem:   Serial controller:Rockwell International HFC 56K Data/fax Modem Primary deviceID 127a:1003         chipset:hcfpcimodem          Download:hcfpcimodem-7.80.02.02full_ k2.6.28_11_generic _ubuntu_i386.dep.zip   I contacted them because no driver listed on that page had 7.8 in front.  The one I downloaded  started _k2.6.28_11 they said ok.   ..........:confused:                     "The Modem is not configured"

---

### Post by demosthene1 on 2009-08-08
Here is what worked for me in Juanty.
I installed Gnome PPP. 
Gnome PPP didn't work for me in Juanty like it did in previous Ubuntu versions so here is the solution that worked for me. Very simple.
I went here:
System > Prefrences > Main Menu. Find the Gnome PPP program in the Internet section under Applications. Select Gnome PPP and click Properties. In the command line field change it to:
gksu gnome-ppp

Then run Gnome PPP and setup your modem and account. All should work just fine if you have a compatible modem. I use a USRobotics USB modem.

---

### Post by jimn1547 on 2009-08-10
:confused: I can't understand your directions.....can't find what you are talking about in my system.

---

### Post by jimn1547 on 2009-08-14
I can't get the drivers to install......Have the  Zip package in Home folder......I can open the files,but when I open Terminal to unzip: it tells me- errors,can't find archieve,file not found.....Can someboby walk me through this?:P

---

