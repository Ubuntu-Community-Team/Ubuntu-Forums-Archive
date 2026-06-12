---
title: "CommandIR II fails after first remote button push"
date: 2008-08-09
forum: Mythbuntu
---

### Post by Belial6_6 on 2008-08-09
I am trying to get a CommandIR II to work.  I have selected 'CommandIR : Dish Reciever' as the transmitter in Mythbuntu Control Center.  When I boot my system, the CommandIR will turn the status light green.  The first button press I do on a remote will turn the status light red.

I have tried following what directions there are on the CommandIR web site.

**apt-cache policy mythtv-common** gives me:
mythtv-common:
  Installed: 0.21.0+fixes16838-0ubuntu3.1
  Candidate: 0.21.0+fixes16838-0ubuntu3.1
  Version table:
 *** 0.21.0+fixes16838-0ubuntu3.1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages

**apt-cache policy lirc** gives me:
lirc:
  Installed: 0.8.3~pre1-0ubuntu7.1
  Candidate: 0.8.3~pre1-0ubuntu7.1
  Version table:
 *** 0.8.3~pre1-0ubuntu7.1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
        100 /var/lib/dpkg/status
     0.8.3~pre1-0ubuntu7 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages

lsmod has:
Module                  Size  Used by
lirc_cmdir             10468  0 
lirc_dev               18248  1 lirc_cmdir
commandir              34368  1 lirc_cmdir
usbcore               169904  6 commandir,usb_storage,libusual,ehci_hcd,ohci_hcd

I have the suspicion it has something to do with usb because before the the CommandIR II fails, I get a bunch of dmesg 'lirc_cmdir: usb error on read = 10' and after the remote button push, and the status light goes red, I get a bunch of 'lirc_cmdir: usb error on read = -32' messages.

I have tried installing on two different system, and get the exact same results.  I bought the CommandIR II because it was touted as a plug and go solution, so any help in getting this figured out would be really appreciated.

---

### Post by commandir on 2008-08-09
Hi Belial6_6, 

There were a couple remotes that sent the CommandIR II's awry in the last release.  

Keep an eye out here for an updated LIRC package, coming soon:

[https://launchpad.net/~superm1/+archive](https://launchpad.net/~superm1/+archive)
[https://launchpad.net/~mythbuntu/+archive](https://launchpad.net/~mythbuntu/+archive)

Otherwise using LIRC CVS (or probably another remote) would get it working right away.

Matthew

---

### Post by commandir on 2008-08-09
Actually re-reading your post, it sounds like you're using the CommandIR Mini driver with the CommandIR II. 

See the post over here on how to get the CommandIR II driver going before the next MythBuntu release:

[http://www.commandir.com/content/view/37/54/#commandir2](http://www.commandir.com/content/view/37/54/#commandir2)

---

### Post by Belial6_6 on 2008-08-09
I followed the direction on the commandir.com site to get to where I am now.  So, I should have the commandir2 driver.  The web site makes it sound like the commandir2 driver is the same as the commandir mini driver.  It implies that support for commandir2 was added in:

Installed: 0.8.3~pre1-0ubuntu7.1

So, as far as I know I should have the right driver.  I have tried 3 or 4 remote controls, so it seems unlikely that I got the one remote that crashes the driver.  Having any remote crash lirc also makes the device completely worthless, as it makes no sense to install a DVR that stops working every time you use your XBox(one of the remotes I tried) remote.

With CVS, are you suggesting I download the source and compile LIRC myself?  That is not something, I look forward to, but since the system cannot be installed live now, anyway, I could give it a go and if that solves the problem, I could then wait for the official package, and stop looking for a solution.

Do the USB errors sound like a problem with USB, or is it more likely that the errors are simply a symptom of the bad lirc driver?

---

### Post by Belial6_6 on 2008-08-09
I just noticed that the creator of CommandIR is Matthew Bodkin.  Is that you?  If so, that makes the comment about new drivers carry MUCH more weight.  Also if so, would any info from my system be of help to you in ironing out the driver?  I am not running MythTV in 'production' yet, so making tweaks as tests would not be a huge problem.  I'm still in the stage that formatting and reinstalling is easier than trying to fix anything I've broken.

Remote transceiving is the only piece that I am having trouble with in MythTV, so a little bit of extra effort today to make a system 'install and go' tomorrow (figuratively speaking) would be worth it.

---

### Post by commandir on 2008-08-11
Hi, 

Perhaps you just need to remove the lirc_cmdir and commandir kernel modules then - the CommandIR II Userspace driver can't claim the CommandIR's if the Mini's kernel modules are loaded:

** lirc_cmdir 10468 0  (can't be loaded)
lirc_dev 18248 1 lirc_cmdir
** commandir 34368 1 lirc_cmdir  (can't be loaded)
usbcore 169904 6 commandir,usb_storage,libusual,ehci_hcd,ohci_hcd

I see Mario's just published the latest LIRC in his PPA.  Since there's a few lirc-0.8.3~pre1-Ubuntu's, I'd also recommend upgrading to this latest one (published 57 minutes ago from 10:40pm Aug 11/08):

[https://launchpad.net/~superm1/+archive](https://launchpad.net/~superm1/+archive)

I'll add a note up in the commandir.com installation guide for others.

---

### Post by bongfrog on 2008-11-06
Any news on the updated lirc drivers for 8.10 ?   I have looked in Mario's intrepid ppa and they are empty.   I am frankly surprised that 8.10 does not include the updated lirc.

thanks

---

### Post by commandir on 2008-11-13
For the thread archive, this has been resolved in the LIRC 0.8.4a release from superm1 now in the commandir-team PPA for 8.10:

[http://www.commandir.com/content/view/53/75/](http://www.commandir.com/content/view/53/75/)

Matthew

---

