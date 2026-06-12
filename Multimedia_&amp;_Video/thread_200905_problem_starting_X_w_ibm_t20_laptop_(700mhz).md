---
title: "problem starting X w/ ibm t20 laptop (700mhz)"
date: 2006-06-20
forum: Multimedia &amp; Video
---

### Post by mstine on 2006-06-20
Hello!

I was able to install Xubuntu 6.06 just fine using the 'alternative' disc on my IBM T20, but when attempting to do my first system startup without the CD am experiencing problems getting the graphical interface to load.

Computer Specs:
IBM T20 laptop
700 MHz Pentium M
128MB ram
Savage S3 IX graphics card (8MB)
14" Laptop monitor supporting 1024x768 resolution native

I found another poster here with the same issue, but the thread does not contain a solution to the problem...
[http://www.ubuntuforums.org/showthread.php?t=168036](http://www.ubuntuforums.org/showthread.php?t=168036)

As stated in that thread, with the default settings I simply get a solid white underscore in the top left corner of the screen and nothing appears to happen when the graphical login attempts to load.

If I boot into safe mode and reconfigure the xorg.conf file using 
   dpkg-reconfigure xserver-xorg   , I have tried all of the possible resolution/refresh rate combinations for my monitor (1024, 800, 640... attempting each with all available standard refresh rates of 60, 70, and 75 Hz).  With some of these resolutions, I get brief flashes of oversized icons/toolbars for an instant before the screen goes black again and displays some white text.  This repeats three or four times before dumping me back to the command line prompt.

I have even tried enabling/disabling DRI and enabling/disabling the software framebuffer, but this doesn't seem to make a difference at all - I always get those instantaneous flashes of oversized icons.  This really seems like some kind of refresh rate problem, but I have no idea what else to do!

I remember having a version of Ubuntu Breezy or Hoary (don't remember now - it was last fall sometime) installed flawlessly, and it booted directly to the graphical interface without issue, but the Dapper version of Xubuntu really doesn't seem to like my display/graphics adapter.

Also, when attempting to load up Xubuntu from the Live 'desktop' CD, I get the same problem when selecting the "Start and Install" option from the boot menu, but I get a fully-functional graphical interface if I select the "Start Safe Graphics Mode" option.

Can anyone give me any assistance on this issue?  ](*,) 

Thanks in advance,
Matt

---

### Post by mstine on 2006-06-21
bump

---

### Post by mstine on 2006-06-21
Reinstalled Breezy just fine today, no errors whatsoever.  Graphical login screen is up and ready!

I plan on copying my xorg.conf file from this working Breezy isntall, reinstalling Dapper Xubuntu, and then copying over the xorg.conf to the new Dapper install... maybe this will work.  I'll keep my fingers crossed, and I'll post the results later today.

In the meantime, if anyone has any help, I'm still waiting for other suggestions...

---

### Post by mstine on 2006-06-21
CRAAAP, copying the xorg.conf file didn't work at all...


buuuuuut~~~


YESSS!~!!!!  :grin:   I FINALLY got dapper xubuntu to boot into graphical mode...

The ONE thing I had to change to get this working on my IBM T20 laptop is manually set the amount of video memory on my system...

To do this:
[LIST=1]
[*]When the computer is booting up, enter the GRUB bootloader and select the "recovery" option.
[*]After the system is fully loaded and you are presented with a command prompt as root, type "dpkg-reconfigure xserver-xorg" to enter the configuration utility.
[*]Have the utility attempt to autodetect the card (for the T20, it should autodetect to the Savage driver).
[*]Continue through the screens selecting the default values until you reach the screen telling you to "Enter the amount of memory (in kB) to be used by your video card."  on the line, type "8192", because the T20 savage video card is an 8MB card...  8 x 1024kB.  This is the critical step in getting the graphics to load correctly!  :D
[*]Continue selecting default values until you reach the screen where you must select "Easy" "Medium" "Advanced" or something regarding the way you will set the refresh rate.  Select "Medium", and then on the next screen select "1024 x 768 @ 75 Hz"
[*]For color depth, select "24".
[*]Continue hitting "OK" through the wizard until you are dumped back to the command line.  Type "telinit 6" to restart the computer.  Let the computer boot completely, and you should see graphics!!!
[/LIST]

That's it!  Hopefully this helped somebody whose video memory wasn't detected correctly.

Matt

---

### Post by mitya89 on 2006-06-28
thanks matt! that solved my problem on my ibm t22.

---

### Post by dlai on 2006-06-28
look at this post as well... that is my solution [http://ubuntuforums.org/showthread.php?t=205411&highlight=ibm+t20]("http://ubuntuforums.org/showthread.php?t=205411&highlight=ibm+t20")

---

### Post by noobbutnotboob on 2007-06-22
solved my problem too! thanks for posting Matt! this should go into the ThinkWiki for Feisty!

---

