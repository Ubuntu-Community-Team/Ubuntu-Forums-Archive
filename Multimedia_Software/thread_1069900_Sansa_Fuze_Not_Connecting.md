---
title: "Sansa Fuze Not Connecting"
date: 2009-02-14
forum: Multimedia Software
---

### Post by Sean_b84 on 2009-02-14
last night i bought a sansa fuze i spent a couple hours of searching google and forums and i still cant find anything that works. on the mtp mode it will say Connect=>Writing=>Disconnected and on msc it says Connecting=>Writing and then back to the main screen. on lsusb it dosn't show the device and on mtp-detect it says "no raw devices" i dont know if anybody else has had this problem but any help would be much appreciated.

---

### Post by Mr_Bumpy on 2009-05-30
I'm not sure why MSC mode isn't working for you.  Have you tried updating your firmware (you may need a Windows box for that step...)?

For your reference, here are some notes and instructions I posted in another thread:
----------------------------------
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

### Post by e.m.fields on 2009-11-22
Hi Sean
Did you get yours to connect yet?

Having same problem.  Ubuntu 9.04, Sansa Fuze, not mounting, and no results from LSUSB.


Please someone respond if you've figure this out and I'll add it to a "solved" thread.

---

