---
title: "Trying to convert to wireless.  Need help!"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by Franknj229 on 2009-07-08
I only recently started using Linux (Ubuntu).  I guess I just don't know what I'm doing yet.  Been using Windows for 15 years.

I bought an Edimax 802.11 b/g Turbo Mode PCI Adapter and a Linksys Wireless-G router that has the "powered by Linux" logo on it.

On the box for the adapter, it says it supports Linux OS, but the user manual on the CD says "System Requirements: Windows 2000, 2003, XP or Vista".

When I insert the CD, it shows up on my desktop.  When I double click it, I see a bunch of files and folders.  No matter what I try to run (.exe files) I get an error message.  I just don't understand how to run things on Linux.  Windows would run ANYTHING you clicked on.  Linux doesn't seem to ever run anything for me.

Any advice?

---

### Post by Anxious Nut on 2009-07-08
I think this is the driver your searching for [URL="http://www.opendrivers.com/driver/272513/edimax-ew-7128g-wireless-pci-adapter-driver-linux-source-code-free-download.html"]
http://www.opendrivers.com/driver/272513/edimax-ew-7128g-wireless-pci-adapter-driver-linux-source-code-free-download.html[/URL]

**Yo ubuntu users try to help this dude out by telling him how to install the driver (do him a favor). thanks**

---

### Post by Franknj229 on 2009-07-08
[LEFT]When I insert the installation wizard CD, I get approx 20 folders, all the different languages.  I understand the wizard won't run on Linux.  There is a folder for "Linux Drivers".  There is also a file called "autorun.exe".  If I click the autorun.exe, I get the following error message in terminal:

 [/media/cdrom0/AutoRun.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/AutoRun.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/AutoRun.exe or
          /media/cdrom0/AutoRun.exe.zip, and cannot find /media/cdrom0/AutoRun.exe.ZIP, period.

If I click on the "linux driver" folder, it just opens up to 4 more folders.  The first is "RT61", the second is "RT73", the third is "RT2860_RT2890_RT2760", and the fourth is "RT2870_RT2770".

If I click on one of those folders, it opens up to two .txt files and another file.  For example, if I click on the first folder above, it gives me two .txt files and a file called "2008_0723_RT61_Linux_STA_v1.1.2.2.tar.bz2".

If I click on that file, it seems to want me to extract it somewhere, but I could be wrong about that, because clicking on it opens up two more files...

Sheesh.

[/LEFT]

---

### Post by t0mppa on 2009-07-08
First off, looks like a Ralink card and since I don't have one myself, don't really have experience with them. But long as you just need help with installing the driver itself, it doesn't differ from any other software installation on Linux. And there might be an easier way to setup drivers for your card, but until someone posts one, you're stuck with manually compiling the files on your CD.

And yes, Linux won't run any .exe files or any software made for Windows. You have to install the drivers manually.

The different directory names sound like different chipset numbers, so you'll have to pick the one that corresponds to your device. And the .tar.bz2 file is an archive which likely holds the driver and instructions on how to compile it on Linux.

So, to start with here's a generic guide of what you need to do, if you don't understand or run into trouble with one of the steps, just ask and we'll take it from there. Especially if you're unfamiliar with using command-line tools, things might seem a bit confusing, but it's actually not that hard once you get accustomed to it.

What you should do is first find out what kind of chipset your card has. You can accomplish that by opening up terminal (Applications / Accessories / Terminal) and running **lspci**, which lists all PCI devices recognized by the OS. From the output, you should find a line describing your wireless interface and that will tell you which chipset your card has and thus solve the problem of which of the 4 directories to pick.

After figuring out the correct directory, you'll need to extract the contents of the tarball (the .tar.bz2 file) to your HD. Recommended place to extract it to is your home directory or a subdirectory under it. After that is done, you'll have to manually compile the driver. Go to the directory where you extracted the package and there will likely be a file named INSTALL or README or both, which will have specific instructions on how to compile it.

---

### Post by RD1 on 2009-07-08
I'm sorry but, I have to ask, have you physically installed the card yet?

I believe this card should be supported by Ubuntu "out of the box".

---

### Post by Franknj229 on 2009-07-10
Hi guys.  Thanks for trying to help.  As I said, I am trying to do this on my girlfriend's computer, so I don't have as much time with it as I would need to figure everything out.  I'm not at her house right now and I probably won't be back for a few days thanks to work.
 
I did physically install the card, but I assumed I needed to install the software as well because there is no indication that it is recognized.  Someone on another forum told me to run lspci -I.  I typed that into the terminal and got two pages of mess.  I have no idea what any of it means or if it even tells me anything at all.  It looked like random combinations of letters.  I didn't see anything that indicated a wireless card.
 
The router (not yet installed) has the "powered by Linux" logo on it, but it also came with a CD that is supposed to be run before connecting the router.  I fear I will be just as confused when it comes to running the files on that CD as well.

---

### Post by t0mppa on 2009-07-11
> **Franknj229 said:**
> Hi guys.  Thanks for trying to help.  As I said, I am trying to do this on my girlfriend's computer, so I don't have as much time with it as I would need to figure everything out.  I'm not at her house right now and I probably won't be back for a few days thanks to work.

This forum isn't going anywhere, just drop back when you get to try out the things suggested, in case you still have some problems.

> **Franknj229 said:**
> I did physically install the card, but I assumed I needed to install the software as well because there is no indication that it is recognized.  Someone on another forum told me to run lspci -I.  I typed that into the terminal and got two pages of mess.  I have no idea what any of it means or if it even tells me anything at all.  It looked like random combinations of letters.  I didn't see anything that indicated a wireless card.

Ok, if it does work out of the box, like RD1 said, then things become a lot easier as you don't have to install anything on the laptop. If so, you should be able to see available wireless networks when clicking on the network icon in your notification area at the top right corner of your desktop.

As for the lspci, there's no need to run it if your card can pick up the networks as mentioned above. If it looks like it's not working, you should find your card with a **lspci -nn | grep RaLink** though. If that doesn't give any output, you can just run one without the pipe & grep part and post it here. If you don't have a working Internet connection yet at your GF's, then you can just run **lspci -nn >> lspci.txt** which will send all the output to a text file and then copy that file to a transportable media, such as floppy disk, usb stick, cd or external hard drive and take it to a computer with Internet access.
 
> **Franknj229 said:**
> The router (not yet installed) has the "powered by Linux" logo on it, but it also came with a CD that is supposed to be run before connecting the router.  I fear I will be just as confused when it comes to running the files on that CD as well.

The only thing that I can think of that would be on the CD is a wizard for setting up the router to work with your Internet connection and I doubt they've bothered to make one for Linux. Anyhow, that is not really required, as web interfaces in routers have become a de facto standard. [Here]("http://www.home-network-help.com/wireless-router.html")'s a page showing how to configure it without using the fancy wizard. It might not be exactly the same as the one on your router, but you should be able to find the same things with a little digging and/or consulting the manual.

---

### Post by Franknj229 on 2009-07-26
Thanks t0mppa,
 
I just ran lspci -nn | grep RaLink and the following popped up:
 
01:00.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
 
I then extracted the RT61 folder and it seemed to work fine.
 
Now it's on to the router.  There is a CD in the box with a big sticker on it that says "RUN CD FIRST before connecting cables".
 
This CD is, as expected, giving me just as much trouble as the last one.  The CD contains the following folders: APP, DataBase, Doc, Driver, Enu, Language, licences, Norton, pack.  It also contains the following loose files: Autorun.inf, config.ini, DNet.dll, EhSecure.exe, ez54g.dll, preflib.dll, ses_cl.dll, seshlp.dll, SetupWIZ.ico, SetupWizard.exe.
 
I'm just not sure what I'm supposed to be doing at this point.  In the manual it says to go to [http://192.168.1.1](http://192.168.1.1)  But nothing happens when I type that in.  It just lags there saying "connecting to 192.168.1.1  I haven't connected the router yet though because it says not to until I run the CD.  Should the router be connected before trying to connect to that website?

---

### Post by MartynT on 2009-07-26
Hi Frank,

the CD that came with the router will be for Windows, so the apps (autorun, setup.exe, etc.) will not work on Linux.  The CD probably contains documentation and may (if you are lucky) contains Linux drivers.  If you are really lucky you wont need them.

[http://192.168.1.1](http://192.168.1.1) is the address of your routers admin/setup page, so if your computer isn't connected to the router then you wont get anything.

My advice, connect up/switch on your ADSL / Cable modem.  Connect your router to that.  Connect you pc to the router.  Switch the router on.  Now go to 192.168.1.1.

You'll have to supply an SSID (just a name for the router/connection - how about "Frank".  You'll also have to pick a channel.  I'd avoid 1, 6 and 11 as they tend to be used a lot (by your neighbours).  And you'll probably want to setup some encryption WPA2, WPA or WEP.

Finally, I understand your frustrations.  Windows often just involves clicking things and downloading things until everything works.  Linux often required reading (manuals, forums, etc.) and a bit of figuring out.  Try to think of it as a treasure hunt rather than a chore.  Your favourite search engine is aften a good place to start.  For example, I just put "tar" into google and it led me to [http://en.wikipedia.org/wiki/Tar_(file_format)]("http://en.wikipedia.org/wiki/Tar_(file_format)").  That page explains that files like your 2008_0723_RT61_Linux_STA_v1.1.2.2.tar.bz2 is a compessed archive (compressed with bzip2).  After a bit of reading you'll be untaring like a seasoned pro :D

---

### Post by t0mppa on 2009-07-27
Like Martyn said, you likely just have to setup a few simple things on the router to get it up and running, which can be done from the web page on the IP you posted. You can read through the manual (and check the docs directory on the CD for help files) and you should get a good idea of what has to be set up and why and how to use the web UI. And do remember to change the admin password for the router, the default ones can usually be Googled, so they're not particularly secure.

Just don't use WEP for encryption, it's very easy to break and there are even threads on this forum about how it's done. Since you've brand new hardware, just pick WPA2 with AES and it's virtually unbreakable, long as you use a proper password or passphrase.

---

### Post by Franknj229 on 2009-07-27
Part of the problem is that I'm finding it so difficult to navigate Ubuntu. Once I install something (AVG anti-virus, for example) I can't figure out how to access it again if I want to change settings or anything like that. It's like it's running secretly.
 
I might be having the same problem with the router. Everything seemed to install just fine. The website said I am broadcasting and accepting. I couldn't find anywhere on the website ([http://192.168.1.1](http://192.168.1.1)) where I could change anything though, such as password or adding encryption. Everything seemed to be working fine, except for the fact that I couldn't load any web pages other than the router page. I thought that if I could just "open" the file with the router info in it, I could make the changes. In other words, if this were a windows machine, there would now be an icon on my desktop as soon as I installed the router. I would double click the icon and bring up all the router menus. I can't find that on Ubuntu.
 
Also, according to the router manual, a lot of info needs to be provided by my internet service provider. Do I really need to call them?
 
Finally, and this isn't really an Ubuntu issue, how am I supposed to know all the "addresses" I need to know? 192.168.1.100, 255.255.255.0, etc... It says I have to make sure all the devices used by my wireless network have the same addresses. Is this common knowledge stuff here? How did I get so far behind the curve when it comes to computer technology??? Shouldn't the wireless card just pick up the wireless signal and be able to connect (assuming I know the password)?
 
Thanks again for helping. I feel like such an a..

---

### Post by t0mppa on 2009-07-28
> **Franknj229 said:**
> Part of the problem is that I'm finding it so difficult to navigate Ubuntu. Once I install something (AVG anti-virus, for example) I can't figure out how to access it again if I want to change settings or anything like that. It's like it's running secretly.

It's not running secretly, just that program shortcuts don't get automatically placed on the desktop on Ubuntu. Instead they're put into the Applications menu and then you can create the shortcut yourself, if you want it on desktop. Although a more Gnome'ish way would be to put it on the top panel by right clicking it, choosing add to panel, then application launcher from the menu and then just picking which application shortcut you want to place there.
 
> **Franknj229 said:**
> I might be having the same problem with the router. Everything seemed to install just fine. The website said I am broadcasting and accepting. I couldn't find anywhere on the website ([http://192.168.1.1](http://192.168.1.1)) where I could change anything though, such as password or adding encryption. Everything seemed to be working fine, except for the fact that I couldn't load any web pages other than the router page. I thought that if I could just "open" the file with the router info in it, I could make the changes. In other words, if this were a windows machine, there would now be an icon on my desktop as soon as I installed the router. I would double click the icon and bring up all the router menus. I can't find that on Ubuntu.

The reason for that is that the configuration exists on the router, not your local computer, so that's why a web page is used by default. I've never even had a router which had some other way to configure it, even on Windows. Wasn't there anything at all about it on the manual?
 
> **Franknj229 said:**
> Also, according to the router manual, a lot of info needs to be provided by my internet service provider. Do I really need to call them?

Only if your ISP doesn't use DHCP, in which case it would make sure to provide the info to you along with whatever documents you got when you made the deal. You can just set the router to obtain IP address automatically and that will most likely work.
 
> **Franknj229 said:**
> Finally, and this isn't really an Ubuntu issue, how am I supposed to know all the "addresses" I need to know? 192.168.1.100, 255.255.255.0, etc... It says I have to make sure all the devices used by my wireless network have the same addresses. Is this common knowledge stuff here? How did I get so far behind the curve when it comes to computer technology??? Shouldn't the wireless card just pick up the wireless signal and be able to connect (assuming I know the password)?

You only need to know those, if you want to set the addresses of different interfaces up manually, if you just use DHCP, then the router will handle the address management for you.
 
> **Franknj229 said:**
> Thanks again for helping. I feel like such an a..

I think it'd be safe to say that everyone who switched from Windows initially felt like that. Ubuntu isn't really all that hard to learn though, you just have to relearn to do the same things in a bit different way, if you use the GUI or then you can englighten yourself and learn a bit about computers, networks, etc. technology behind our daily chores by doing stuff manually and actually learning to understand why things work the way they do.

---

### Post by MartynT on 2009-08-01
Hi Frank, I think we should go back a few steps.  The subject of this thread is "Trying to convert to wireless."

It seems you're also trying to convert to Ubuntu.  I'd suggest one step at a time.  Presumably you have a Windows system connected to the internet via wire (Ethernet adsl/cable), presumably without a router.

I'd suggest first trying to convert your windows system to wireless, or more specifically to go via your new router.  This will require you to learn about the router.  You'll have to choose an SSID, a channel, a type type of encryption (you want WPA2 if it's available), an encryption password and for good measure a new password for the router (the default of 1234 is not very secure :D ).  You'll have to do all this via the [http://192.168.1.1](http://192.168.1.1) web interface to the router.  Until you have done all this you wont have wireless access to the net from your Windows machine.  

Once you've done all this go to step 2.  Get your Ubuntu system connected to the net using a wire to your router.  Once you have that you can start to learn a few things about Ubuntu (like using synaptic to install things).

Then move to step 3, getting your Ubuntu system connected via the wireless.  By the time you get to this step you'll have already setup your Windows system so things like 192.168.1.x and DHCP won't seem new to you.

> **Franknj229 said:**
> Part of the problem is that I'm finding it so difficult to navigate Ubuntu. Once I install something (AVG anti-virus, for example) I can't figure out how to access it again if I want to change settings or anything like that. It's like it's running secretly.

....

Thanks again for helping. I feel like such an a..

I have the opposite problem.  On Windows it's often near impossible to stop things from auto starting at startup, especially all the malware that's so popular on Windows.  I recently did some cleanup on my father's old XP machine.  It used to take 8 minutes to become usable from switch on.  I delved into the registry, you know, HK_Local_Machine/software/microsoft/windows/this/that/the_other/current_version/run/....  I removed 35 entries !!  35 !!  All sorts of rubbish that thought that it was the most important thing on the PC.  After this the thing started in 90 seconds.  My own experience I recently added a new optical drive (DVD Writer).  The install of the driver also installed a firmware upgrade checker.  So every time I start the very first thing it did was check that there wasn't new firmware for the DVD Writer.  Never mind me, I'll just wait !!

Anyway, rant over.

With Ubuntu I wont say that Anti Virus isn't necessary, just that it's a lot less necessary than on Windows.  Personally I don't run any.

When you do install new things they usually just appear in one of the menus.  Those that don't can just be run from terminal.  If you want to know where something has been installed try which or whereis.  I recently installed emacs ...

```
martyn@martyn:~$ whereis emacs
emacs: /usr/bin/emacs /etc/emacs /usr/lib/emacs /usr/share/emacs /usr/share/man/man1/emacs.1emacs-snapshot.gz /usr/share/man/man1/emacs.1.gz
martyn@martyn:~$ which emacs
/usr/bin/emacs
```

/usr/bin is a bit like the Unix version of c:/program files, but I have to be careful what I say, many would consider it blasphemy ;)

Finally, don't feel like an a... just for being new to something.  Everyone was new once and most people on these forums like helping others.

The only a... is someone who makes fun or won't help.  They're quite rare on here.

---

