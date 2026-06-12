---
title: "Can't upgrade firmware on my Samsung YP-K5"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by ShiftSix on 2007-09-13
the manual says, to locate the samsung device in windows explorer
in the Data folder

screenshot:
[IMG]http://i52.photobucket.com/albums/g13/Shift_Six/problemme.jpg[/IMG]


But i dont have the folder, i dont see the icon
i only see the icon of my sony ericsson phone

what should i do?

i've already tried to put the firmware files under the normal folders

---

### Post by david_2001 on 2007-09-13
What I read tells me that the Samsung YP-K5 is not a USB mass storage device out of the box, so it will not be recognised by a GNU/Linux system.  Looks as though you will need Windows to do the firmware update.  Take a look at [http://ubuntuforums.org/showthread.php?t=317863](http://ubuntuforums.org/showthread.php?t=317863).

---

### Post by ShiftSix on 2007-09-14
> **david_2001 said:**
> What I read tells me that the Samsung YP-K5 is not a USB mass storage device out of the box, so it will not be recognised by a GNU/Linux system.  Looks as though you will need Windows to do the firmware update.  Take a look at [http://ubuntuforums.org/showthread.php?t=317863](http://ubuntuforums.org/showthread.php?t=317863).

 thx

---

### Post by trippinnik on 2007-09-14
it's an MTP device.  You'll still be able to connect using libmtp.  Some of the devices are not supported but yours is [http://libmtp.sourceforge.net/index.php?page=compatibility](http://libmtp.sourceforge.net/index.php?page=compatibility)
you'll need to install libmtp (it's in the repos) or build it to get a more recent version.  Then you can add your device in Amarok it should detect the MTP device.  You might need to use the command line tools to copy over your new firmware though.

---

### Post by ShiftSix on 2007-09-15
> **trippinnik said:**
> it's an MTP device.  You'll still be able to connect using libmtp.  Some of the devices are not supported but yours is [http://libmtp.sourceforge.net/index.php?page=compatibility](http://libmtp.sourceforge.net/index.php?page=compatibility)
you'll need to install libmtp (it's in the repos) or build it to get a more recent version.  Then you can add your device in Amarok it should detect the MTP device.  You might need to use the command line tools to copy over your new firmware though.

i downloaded libmtp, but how do i use it? 
i have a folder with all crazy files i never heard of

but thanx for your post, definitely a step closer to the solution

---

### Post by trippinnik on 2007-09-16
cool, now that you've got the files and their untarred open up a terminal and cd to the directory with the files.
you'll type: 
./configure
then
make
then 
sudo make install
when it's all done try typing mtp-detect, it'll give you some output about your device and if the connection is a success.  Once it's connected you should be able to do some copying, but you may need to use the command line interface mtp-(and one of the utility names)

---

### Post by ShiftSix on 2007-09-16
> **trippinnik said:**
> cool, now that you've got the files and their untarred open up a terminal and cd to the directory with the files.
you'll type: 
./configure
then
make
then 
sudo make install
when it's all done try typing mtp-detect, it'll give you some output about your device and if the connection is a success.  Once it's connected you should be able to do some copying, but you may need to use the command line interface mtp-(and one of the utility names)

thankyou for your help
but im realy not smart in these things
how do i open up a terminal and cd to the directory??

---

### Post by ShiftSix on 2007-09-17
this was on page 7, so.. bump
plz help

---

### Post by ShiftSix on 2007-09-19
bring up my post

---

