---
title: "Running Special University Plugin for Firefox"
date: 2010-08-27
forum: Multimedia Software
---

### Post by libertythor on 2010-08-27
I am using Lucid Lynx and need help installing this plugin.  These are the instructions that were on the University of Phoenix website, but it doesn't seem to work no matter what.

 	
> Manual Installation of the ALEKS plug-in for Java VM on Linux

		
	
These instructions for installing the ALEKS plug-in on Linux are provided for your convenience only. We do not currently provide any support for ALEKS on the Linux operating system.
	
		
To download manually the plug-in on Linux for Netscape 7.1+, or Firefox 1.0+, or Mozilla 1.6+, you will have to download the ALEKS package file and save it on your computer in the "Java VM lib/ext" directory.

For instance, with the Sun Java VM version 1.4.1, this directory is usually:

/usr/java/j2re1.4.1/lib/ext/

or

/usr/local/j2re1.4.1_02/lib/ext/

If you are unsure, please check with your system administrator.

Installation instructions:

   1. Point your mouse at the link below and press down your mouse left button.
          * aleksPack10.jar (6.4M) 

   2. A pop-up window should appear asking you "What should Netscape do with this file?".
   3. In the menu choose the option "Save this file to disk" and click on "OK".

   4. A new window should appear to ask you where you want to save the file.

   5. Save the file in your home directory by clicking on the button "Save" to start the transfer.

   6. Open a terminal and type: (adapt the directory to your own Java VM lib/ext directory)

      > su root
      Password: (Type in the root password)
      > cp aleksPack10.jar /usr/java/j2re1.4.1/lib/ext/
      > exit

   7. Restart Netscape 


It says that it will work on Firefox, but the instructions mention Netscape.

---

### Post by mc4man on 2010-08-28
Maybe have a read thru this thread as to method and which java to use ect.
[http://ubuntuforums.org/showthread.php?t=1522501](http://ubuntuforums.org/showthread.php?t=1522501)

---

