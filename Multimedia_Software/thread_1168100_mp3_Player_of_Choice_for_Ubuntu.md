---
title: "mp3 Player of Choice for Ubuntu"
date: 2009-05-23
forum: Multimedia Software
---

### Post by Soapy.Illusions on 2009-05-23
I just switched to Ubuntu last week, and have really liked everything except for how the iPod touch works with the OS.

It is not my iPod and I am planning on purchasing a mp3 player for myself and was wondering which one would work best with Ubuntu.

I am looking for a cheap, with large storage (preferably over 30gigs) that works well and preferably right out of the box with Ubuntu

Any suggestions would be appreciated.

---

### Post by noelvh on 2009-05-23
Well I am not an apple fan, so I have never owned any thing from them. But I will put my 2 bits in here. I have a Sandisk Fuze and love it. This is my second mp3 player and second Sandisk. It is a drag and drop player, meaning you do not need soft ware to move the files on to it. I have the 4gb one with a 2gb micro sd card for a total of 6gb and the hole lot cost me $80.00 USD.

Well I hope this helps.

Noel

---

### Post by Soapy.Illusions on 2009-05-23
Well because of my large music collection I was thinking the SanDisk 32gig Sansa, does it also not require any type of software and easily compatible with ubuntu??

---

### Post by noelvh on 2009-05-23
I think all Sandisk are drag and drop. Linux sees the drvice as a USB flash drive. Also Ubuntu charges my battery.

Noel

---

### Post by Mr_Bumpy on 2009-05-30
The Sansa Fuze can work in two USB modes: MTP and MSC.  In MSC mode, it behaves as any other USB storage device--you can drag and drop files onto the device through your file manager.  In MTP mode, you can't manipulate the device at the file level, but it works instead through music-management programs like Amarok and Banshee.  However, be aware that the Fuze version 2 isn't properly supported in libmtp until version 0.3.7, and the version in Ubuntu 9.04 is 0.3.0.  Ubuntu 9.10 will have Fuze v2 support out-of-the-box.  Your options for MTP mode are to wait it out until Ubuntu 9.10, or compile libmtp yourself (or find a package/repository somewhere with libmtp already compiled).  If you're happy running in MSC mode, that's probably the easiest way for now.

If you decide to compile libmtp yourself, here's what you need to do (instructions are for Ubuntu Jaunty).
[LIST=1]
[*]Download the libmtp source from [[COLOR="Blue"]here[/COLOR]]("http://sourceforge.net/project/downloading.php?group_id=158745&filename=libmtp-0.3.7.tar.gz&a=3278902"), and extract it somewhere.
[*]Install some tools we'll need to compile this sucker:
```
sudo apt-get install build-essential checkinstall libusb-dev
```
[*]Make sure that mtp-tools is not installed (the tools will be included in your compiled version):
```
sudo apt-get remove mtp-tools
```
[*]Using a terminal, go into the folder that you extracted in step 1, and run:
```
./configure --prefix=/usr
```
[*]Assuming you get no errors, next run:
```
make
```
And then after that process completes:
```
sudo checkinstall
```
Note: By running **checkinstall** instead of the usual **make install**, you will create a package that will be maintained by the system, which will help to avoid dependency problems.
[*]The checkinstall program will ask you some questions about the package you will be creating.  Answer 'no' to the question about documentation.  For the description, put whatever you want, or "A library for communicating with MTP aware devices."  Then, you will be asked to specify which elements of the package details you would like to modify.  Change the package name from **libmtp** to **libmtp8** to make sure your package will satisfy the dependencies of other programs that make use of the library.  The other package details aren't important right now.
[*]Once the package has been created and successfully installed, run one final command (from within the same folder):
```
sudo ./hotplug.sh
```
Hit 'yes' to all the options (you might get an error on the last one, but don't worry about it).
[*]Finally, make sure your Fuze is set to MTP mode, *not* autodetect.  For some reason, it seems to bug out in autodetect mode (at least it did for me...).
[*]Connect your Fuze to your system with the USB cable, and if all went right, you should be able to access your device through Amarok.  I haven't tried other players, but they should work too, as long as they support MTP devices.[/LIST]

---

### Post by Mr_Bumpy on 2009-05-31
Crap.  After more testing, it doesn't seem that the MTP transfers from Amarok are very reliable (is it libmtp's fault?)... I'm getting some MP3s that crash the player, and occasional connection glitches with the Fuze.  Looks like I'll have to use MSC mode until the situation is improved.

---

