---
title: "Not interpreting ATI 9200 correctly"
date: 2006-02-01
forum: Multimedia &amp; Video
---

### Post by rtgh4 on 2006-02-01
How do I get ubuntu to recognize my video card properly?  :mad: 
It thinks thecard is pci, but is really agp. In the device manager window, it says it is an unknown device type and unknown capabilities:-k  

Please instruct me and link me to A driver, if necessary.

ATI
Radeon 9200
AGP
256mb ddr

---

### Post by DoorGunner on 2006-02-01
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)
This is by far the best set of instructions for ati drivers....have a go through it.:)

---

### Post by rtgh4 on 2006-02-03
thanks, I've got it:)

---

### Post by Razorback on 2006-02-06
I recently installed an ATI 9250 256 MB card (PCI) in an older compaq ep model pc to replace the existing onbaord graphics.  I have been having problems gettting the fglrx driver to work.  I have used the instructions for loading the driver that comes with Breezy but have had no success.  After everything is installed and I reboot the system, it hangs before the login screen.  To fix, I have used the nano editor to restore the xorg.conf file.  My card is recognized but I can't figure what could be causing this.
On another note, is it bad to have two versions of the restricted files on your pc.  After I removed the 386 restricted files, I decided to move up to the 686 version since I have a Celeron.  Both versions now show up in Synaptic.
Also, should I consider this howto instead of the older one?
Sorry for all the questions.
Thanks for any help!

---

