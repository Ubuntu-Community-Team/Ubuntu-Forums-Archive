---
title: "Lirc- pvr150 IR Blaster will not transmit"
date: 2008-04-25
forum: Multimedia Software
---

### Post by ssycorax on 2008-04-25
Ok,

I've been on this for while now. I have a vanilla Hauppauge pvr150 in a Dell PIII and I'm trying to change channels on my cable box using the IR blaster.

The remote works fine, irw recieves and displays the codes as expected, and I can navigate mythtv. I've followed the instuctions in section 10.2.4 of the Muthbuntu 7.10 Installation manual several times (I also note that this section is virtually identical in the 8.04 manual).

Things go swimmingly until I enter:
 
         irsend SEND_ONCE blaster POWEROFF

to which my computer responds:

         irsend: command failed: SEND_ONCE blaster POWEROFF
         irsend: hardware does not support sending
 
I've investigated this on a number of forums and some people have had success using an install routine from the Feisty manual to recompile the kernel to incluide the lirc_pvr150 module. I've tried this and have failed twice only to reinstall. It always seems to me that I MUST be doing something wrong during the install.

Curiously, both the 7.10 and 8.04 installation manuals say that the Hauppauge PVR 150 is "supported by the lirc pvr150 module" (this is found in section 10.2 IR Transmitting). I say curiously because during the install, the system apparently doesn't allow for the use of the lirc_pvr150 module. If I choose "Hauppauge TV Card" during install, the system uses the lirc_dev and the lirc_i2c modules. I tried choosing "Other Remote" when configuring lirc during install in an effort to manually choose the lirc_pvr150 module, but it was not an option.

I've come across several posts that seem to imply that the lirc_pvr150 module is the key. I tried to manually reference it in my hardware.conf file . . . to no avail.

Am I missing something simple?

The PVR 150 is pretty common, as is the Dell. The Manual is straightforward enough-- except the bit about the IR blaster being supported by a module that is apparently no longer being installed for that purpose. At least it's not showing up in my hardware.conf file where I'd expect it to be.

Any help woud be greatly appreciated.

---

### Post by Trimble Epic on 2008-04-28
Devs, Is the 150's FIRMWARE included in 8.04 now, or do we still have to GO GET IT and put it in place before the blaster will work?

---

### Post by rkocher on 2009-01-05
I know this is an old post but I just spent the weekend trying to get my pvr150 blasting on my mythbuntu system. Solution actually turned out to be fairly easy but I've found it no where else - Remove lirc by running: 

"sudo apt-get --purge remove lirc" 

To ensure the driver is not still loaded run:

"modprobe -r lirc_i2c" 

Then follow the instructions at [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24)

---

