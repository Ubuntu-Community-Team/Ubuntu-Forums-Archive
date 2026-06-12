---
title: "Jaunty / Netgear WPN111 ....trouble installing drivers"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by TuNeCedeMalis on 2009-05-06
Hello!

I'm using the following tutorial

">            This is a complete how to on installing and setting up the Netgear WPN111 wireless device in Ubuntu Gutsy Gibbon.

1. Download the two attachments (WIndows drivers and ndiswrapper)

2. Install build-essential (Needed for compiling ndiswrapper)
  Code:
 sudo apt-get install build-essential 3. Extract ndiswrapper
  Code:
 tar -zxvf ndiswrapper-1.51.tar.tar 4. Go to the ndiswrapper directory
  Code:
 cd ndiswrapper-1.51 5. Run
  Code:
 make distclean
make
sudo make install 6. Check that ndiswrapper is installed properly  
  Code:
 ndiswrapper -v If it outputs something like this:
  Code:
 utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586 It has installed correctly. 
If it show something different (Please upgrade ndiswrapper to the latest version by going to the ndiswrapper website [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)), run  
  Code:
 sudo make uninstall Three times and repeat steps 5-8 again and check ndiswrapper -v again. 

If it does display the correct output, then you can move to the next step 

7. Go back to your home directory
  Code:
 cd .. and then extract the windows drivers
  Code:
 tar -zxvf win-drivers.tar.gz 8. Change directory to the windows drivers
  Code:
 cd win-drivers 9. Run
  Code:
 sudo ndiswrapper -i netwpn11.inf 10. Check if the windows driver is installed
  Code:
 ndiswrapper -l If it shows: then you can move onto the next step.
  Code:
 netwpn11 : driver installed
        device (1385:5F01) present If not, remove driver
  Code:
 sudo ndiswrapper -r netwpn11 And reinstall the driver
  Code:
 sudo ndiswrapper -i netwpn11.inf 11. Run
  Code:
 sudo depmod -a
sudo ndiswrapper -m
sudo modprobe ndiswrapper If it all goes to plan, Ubuntu should still be running OK and the Netgear device should be winking at you:KS

12. Finally make sure that the device initializes at boot, run
  Code:
 nano /etc/modules And add ndiswrapper at the end of the page.



Hopefully, if you have done everything correctly, you should have a working WPN111 Wireless device!
 Now right off the bat I see this tutorial was made for gutsy, so that may be a problem. 

Anyways, my problem is that when I get to the ndiswrapper -l command I get this message

"     WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.   netwpn11 : driver installed  
     device (1385:5F01) present"


Thanks for the help in advance!!!!

---

### Post by TuNeCedeMalis on 2009-05-07
Please, anyone?! It would really be nice to be able to run Ubuntu.

---

### Post by TuNeCedeMalis on 2009-05-07
:confused:

---

