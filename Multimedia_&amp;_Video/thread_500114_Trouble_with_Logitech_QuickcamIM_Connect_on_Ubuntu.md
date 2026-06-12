---
title: "Trouble with Logitech Quickcam/IM Connect on Ubuntu 7.04"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by Randy Scarberry on 2007-07-13
Hello all.  I'm having some trouble getting my Logitech Quickcam/IM Connect to work on Feisty Fawn in the application Camerama.  I followed the procedure given in [http://ubuntuforums.org/showthread.php?t=303330&highlight=046d%3A08d9]("http://ubuntuforums.org/showthread.php?t=303330&highlight=046d%3A08d9")  , which was for Kubuntu 6.10 and an older version of the driver.  So I'll list the same steps as I did them:

**Step 1.**  Run lsusb to find the vendor ID and product ID:

# **lsusb**
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Bus 002 Device 002: ID **046d:08d9 Logitech, Inc.** 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c30a Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

**Step 2.** Download latest driver source code from [Michael Xhaard's homepage]("http://mxhaard.free.fr").  Here is where I begin to deviate from the old procedure.  The latest driver is:  gspcav1-20070508.tar.gz.  I just downloaded this file onto my desktop using FireFox.

**Step 3:** Open a terminal window and become root.

**sudo -s**
Password:######## 
root@<my computer name>

**Step 4.**  Download linux headers, restricted modules, and build essential.  Since I already did this while configuring my wireless card, it was unnecessary.  By the way, uname -r identified my kernel as **2.6.20-16-generic**.

**Step 5.** Compile the gspca (not spca5xx) source code.

cd /usr/src
mv ~/Desktop/gspcav1-20070508.tar.gz .
tar xfvz gspcav1-20070508.tar.gz
cd gspcav1-20070508

**STEP 6:** Set the environment variable CC for the gspca Makefile.  I assumed my system uses gcc-4.1 and entered the following command.

export CC=gcc-4.1

**STEP 7:** Set a link back to source code(headers).

ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build

**STEP 8:** Compile the gspca source code, remove the old driver(from memory and hard drive), install the new driver and load the new driver.  I entered the following commands, which differ slightly from the old procedure.  In case you're wondering why I use "gspca" instead of "gspcav", when I tried the latter, I got a not found message.  So I looked at the files in the directory and saw that the header and object files began with "gspca".

make
modprobe -r spca5xx
modprobe -r gspca
rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/gspca* 
make install
modprobe gspca

(The two rm lines were probably unnecessary, because "make install" includes the same commands.)

I didn't see any error messages, so I then typed "dmesg" and found the following in the listing:

[  635.684000] usbcore: deregistering interface driver gspca
[  635.700000] ubuntu/media/gspcav1/gspca_core.c: driver gspca deregistered
[  680.784000] Linux video capture interface: v2.00
[  680.796000] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[  681.436000] usbcore: registered new interface driver gspca
[  681.436000] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered

It sees the camera, but it's not labeled as Logitech.  This may be ok, since I think ZC3XX was what was listed on Michael Xhaard's page.  When I run Camerama, it locks up either immediately for very soon after I begin using it.  Sometimes for a few seconds I'll see live video, but image capture hasn't worked yet.  It always freezes up and has to be killed.

Thanks in advance for any help!

---

### Post by Randy Scarberry on 2007-07-15
I think I solved the problem myself.  Before I posted the original message, I had run Camerama, once or twice and clicked the "Take Picture" button.  Both times I got the error message: "Cannot create ~/Webcam_Pictures" and then Camerama froze.  I created the Webcam_Pictures directory from a terminal, tried again, but got the same message and another freeze.

Today I plugged in an old Logitech laptop webcam to see if it would work.  It worked fine without having to change a thing.  When I clicked on "Take Picture", I got the same error message, but at least the program didn't freeze.  I opened Preferences -> Local Capture, then clicked on the "Browse..." button.  I selected my Webcam_Pictures directory in the file chooser and clicked OK.  Even though it was the same directory that was already in the dialog, doing this got rid of the error and I could take pictures.

So, just for grins, I replaced the old cam with the newer Logitech Quickcam IM/Connect.   It works now!  Don't really know why, but it does.

---

