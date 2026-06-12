---
title: "Version 2 of the Sansa Fuze MP3 player and MTP mode"
date: 2009-01-16
forum: Multimedia Software
---

### Post by hazza96 on 2009-01-16
I have my Fuze working perfectly in MSC mode and I do not intend using it in MTP mode but I wanted to share what I found when trying to.

In MSC mode the version 2 Fuze has a ID of 0x74c3 when I do run the lsusb command. To get the purdy music player icon on my Desktop and Rhythmbox to recognise it as a player device I had to add that ID to the Fuze line in the file:

**/usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi**

When I connect the version 2 Fuze in MTP mode it has an ID of 0x74c2. When I run the command mtp-detect it shows "no raw devices found.

If I look at the file **/etc/udev/rules.d/45-libmtp8.rules** at lines 147/148 and 472/473 has the ID of the Fuze as 0x74c0.

After I change those lines to 0x74c2 and run the mtp-detect command it gives me screens and screens of info but locks up towards the end.

A user with a version 1 Fuze shows [this]("http://docs.google.com/View?docid=df7snrjc_0dvkndsfd") as their output of mtp-detect. I do not get the last 3 lines.

After changing the rules files I run the mtp-connect command and it shows a line with the Fuze and it's ID still being 0x74c0.

So at the moment it appears that the MTP support for the Version 2 of the Fuze does not work.

---

### Post by nanotube on 2009-03-22
i'm seeing exactly the same behavior from the version2 sansa fuze that i just got - i wanted to try to get the "default" tracks from the player, but couldn't get it to be seen in mtp mode at all.

will try the latest libmtp and see if that helps... :)

---

### Post by nanotube on 2009-03-22
just compiled and installed the latest libmtp as of this writing (0.3.7), and it did detect the device, but still failed, and locked up the fuze so i had to reset it.

this was the output:
```

libmtp version: 0.3.7

Listing raw device(s)
   Found 1 device(s):
   SanDisk: Sansa Fuze v2 (0781:74c2) @ bus 0, dev 34
Attempting to connect device(s)
PTP_ERROR_IO: Trying again after re-initializing USB interface
usb_claim_interface(): Bad file descriptor
LIBMTP PANIC: Could not open session on device
Unable to open raw device 0
OK.

```

I filed a bug with libmtp on this. for your reference, here's the link:
[https://sourceforge.net/tracker2/?func=detail&aid=2702272&group_id=158745&atid=809061](https://sourceforge.net/tracker2/?func=detail&aid=2702272&group_id=158745&atid=809061)

hope they get this fixed. not that i particularly care - it works just fine in msc mode... :)

---

### Post by Mr_Bumpy on 2009-05-30
I have the Sansa Fuze version 2 player working flawlessly with Amarok 2 right now.  I ran into the lock-up problem, mentioned in this thread, but one of two steps seems to have solved it (not sure which one):
[LIST=1]
[*]running ./hotplug.sh from the libmtp 0.3.7 source directory
[*]setting the Fuze to MTP mode rather than Autodetect
[/LIST]

Anyway, if you'd like to know what steps I've done so far, here are my instructions from another thread:
--------------------------
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

### Post by clconway on 2009-06-11
It's possible to install libmtp v0.3.7 on Jaunty using [Prevu]("https://wiki.ubuntu.com/Prevu"). (I had to download the source package and invoke Prevu on the .dsc file.)

---

