---
title: "HOWTO: Wireless Printing on 64bit with Lexmark X7675"
date: 2010-04-07
forum: Networking &amp; Wireless
---

### Post by _simon_ on 2010-04-07
Download the driver from Lexmark. 
[http://support.lexmark.com/index?page=downloadFile&actp=RECOMMEND&productCode=LEXMARK_X7675&id=DR20523&segment=DOWNLOAD&actp=PRODUCT&userlocale=EN_UK&locale=en](http://support.lexmark.com/index?page=downloadFile&actp=RECOMMEND&productCode=LEXMARK_X7675&id=DR20523&segment=DOWNLOAD&actp=PRODUCT&userlocale=EN_UK&locale=en) (link correct at time of posting)

As the drivers are 32bit you'll have to do the following:
Taken and updated from here [http://www.phoronix.com/scan.php?page=article&item=lexmark_linux&num=4](http://www.phoronix.com/scan.php?page=article&item=lexmark_linux&num=4)

> 
Prerequisite packages: ia32-libs, openjdk-6-jre

1. Get the latest driver (link above)
2. Untar driver (should be able to right click and extract)
3. run in terminal "./lexmark-08z-series-driver-1.0-1.i386.deb.sh --noexec --target lexmark"
4. a "lexmark" (from --target) directory was created, "cd lexmark"
5. run in terminal "tar xvf instarchive_all --lzma"
6. run in terminal "sudo dpkg -i --force-all lexmark-08z-series-driver-1.0-1.i386.deb."


Make sure you're in the correct folders else it won't work ;)

Assuming all went well you should get an Installation Complete message. So that's the driver installed.

This next bit I'm a bit fuzzy on as I'd already set the printer up via windows so it already had my wireless nextwork details stored. If you know the IP for your printer then type it into a browser window to access the printer admin page and enter your wireless details (Configuration -> Wireless) 
I'm not sure how you'd find the IP for the printer via Linux - hopefully someone can fill that missing part in? I had mine because it had been setup via Windows already and was showing in the router devices connected section.

If you have already got it working via windows then all you need to do is add the printer in Ubuntu either via CUPS ([http://localhost:631](http://localhost:631)) or System -> Administration -> Printing (see following steps)

Go to New -> Find Network printer and enter the printer IP into the Host box. 

It may take a little while but should find the printer and you'll now be looking at the words "Lexmark 7600 Series" in the URI text box. 
Delete those words from that URI box and enter socket://printeripaddress* and press forward

*this is the IP address!

You've already installed the driver so simply choose Lexmark and then 7600 series and choose the driver press forward and fill out the following 2/3 boxes and you're done.

Print a test page to be sure. It takes a few seconds to go through.

If you have any questions then I'll try my best to help but I'm no Linux expert and have pieced this together from a lot of googling along with trial and error.

I haven't looked into getting the scanner to work yet.

---

### Post by HamaLee on 2010-04-07
Thanks for this.  I (think) I installed the driver and went through the process of adding a new printer from your post.  I can't print anything though.  Anybody got any advice?

UPDATE: It works!  When it came time to choose the driver I had two choices with similar names, one of which was "recommended".  I chose the one that was NOT recommended and it successfully printed the test page.

---

### Post by Rasa1111 on 2010-04-07
wow niice!
props to you. 

 i cant even get my friends wired lexmark working yet. :lol:
dont even want to think about wireless! lol
  nicely done. *

---

### Post by jbr6700 on 2010-05-02
I have tried installing as directed, but no luck here. :( I'll insert the terminal session and hopefully someone can tell me what I am doing wrong.

 [PHP][/PHP]brian@A8V-VM:~$ ./lexmark-08z-series-driver-1.0-1.i386.deb.sh --noexec --target lexmark
Creating directory lexmark
Verifying archive integrity... All good.
Uncompressing nixstaller.......................................................................................................................Extraction failed.
......Terminated
brian@A8V-VM:~$ sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh --noexec --target lexmark
[sudo] password for brian: 
Creating directory lexmark
Verifying archive integrity... All good.
Uncompressing nixstaller..............................................................
brian@A8V-VM:~$ cd Lexmark
bash: cd: Lexmark: Not a directory
brian@A8V-VM:~$ cd lexmark
brian@A8V-VM:~/lexmark$ tar xvf instarchive_all --lzma
printdriver.te
tar: printdriver.te: Cannot open: File exists
lexmark-08z-series-driver-1.0-1.i386.deb
tar: lexmark-08z-series-driver-1.0-1.i386.deb: Cannot open: File exists
launcher.c
tar: launcher.c: Cannot open: File exists
launcher
tar: launcher: Cannot open: File exists
lsbrowser
tar: lsbrowser: Cannot open: File exists
lsusbdevice
tar: lsusbdevice: Cannot open: File exists
tar: Exiting with failure status due to previous errors
brian@A8V-VM:~/lexmark$ sudo tar xvf instarchive_all --lzma
printdriver.te
lexmark-08z-series-driver-1.0-1.i386.deb
launcher.c
launcher
lsbrowser
lsusbdevice
brian@A8V-VM:~/lexmark$ sudo dpkg -i --force-all lexmark-08z-series-driver-1.0-1.i386.deb.
dpkg: error processing lexmark-08z-series-driver-1.0-1.i386.deb. (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 lexmark-08z-series-driver-1.0-1.i386.deb.
brian@A8V-VM:~/lexmark$ 
[PHP][/PHP]

---

### Post by jbr6700 on 2010-05-03
Bump. Anyone have any ideas? TIA

---

### Post by wbar2 on 2010-05-04
> **jbr6700 said:**
> Bump. Anyone have any ideas? TIA

Have you tried this method?
[http://ubuntuforums.org/showthread.php?p=9230411](http://ubuntuforums.org/showthread.php?p=9230411)

It's the same drivers you use for the X7675, so it should work.

---

### Post by jbr6700 on 2010-05-04
Yes, I had previously. I went back and retried it on your suggestion today. The driver did install this time because I missed the "sh" at the beginning of the command prior. My present issue is that Ubuntu has loaded the driver, sees the printer and apparently can communicate with it...........but still will not print. When I try to print, I do receive a message that the color ink is low, but that's as far as it gets. I do receive a message on the printer screen that a job is canceling, but no paper/print job is output. I can open the print jobs window and it shows a print job stopped. Tried installing a new color cartridge,but that did not help.I'd call halfway there better than none ATM,but sure would like to get this "all"the way there. Oh as a BTW, I tried both ways wireless as well as using a USB cable. The end result was the same. :-(

---

### Post by jbr6700 on 2010-05-07
Ok,I don't know what happened but yesterday after updating the system, the printer started to print from 10.04. I dunno if it was one of the updates or something else, but all is good now. Thanks to those that helped. 8-):biggrin:

---

