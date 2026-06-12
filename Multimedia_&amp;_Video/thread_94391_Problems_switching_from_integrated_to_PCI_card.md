---
title: "Problems switching from integrated to PCI card"
date: 2005-11-23
forum: Multimedia &amp; Video
---

### Post by B92MOR on 2005-11-23
Hello, I'm new to Ubuntu and Linux.  I 'inherited' a spare PC from a friend (HP Pavilion 8756c) that uses integrated Intel i810 graphics.  Ubuntu has no problem recognising and operating with the integrated graphics, but when I place a PCI graphics card in the box (Geforce MX4000 64MB PCI), I get a black screen freeze after the system initially loads.

I've tried several things so far:
1) The BIOS does not support any option for deactivating the integrated graphics.
2) There are no jumpers on the mobo to deactivate it either.
3) The card works perfectly fine with Windows.  All I need to do in that OS is to go into the Hardware menu and disable the integrated graphics.  I really don't want Windows running on this PC though.
4) I tried some extremely ignorant editing in the "Device" section of the xorg.conf file.  I blundered so hard that I had to reinstall Ubuntu.
5) The nVidia drivers are installed through Synaptic.  That didn't seem to help.

I tried everything I can think of to get it to work, but every time I turn the computer on with the PCI card in it, Ubuntu never gets so far as the login screen without a BlackSOD.  I made one attempt with Knoppix to see if any Linux system would recognize the card, and though Knoppix loaded, there was no hardware acceleration whatsoever.

Any ideas?  I know that the word "integrated" should not be in a Linux user's hardware vocabulary, but I'd rather like to get this to work.

---

### Post by narcolept on 2005-11-23
It's most likely because you're running i810 drivers on a nvidia card. You'll need to either edit /etc/X11/xorg.conf or run dpkg-reconfigure xserver-xorg and replace with the correct driver after you boot with the geforce.  Easiest way would be to put the card in, boot to single user mode (select your kernel in grub,  hit e instead of enter, select the kernel loading line, hit e again, and add a 1 to the end of the line, then do it there and reboot.)  Since you're probably hesitant to edit the config again, reconfiguring X would be your best bet.  I don't use nvidia cards, so I don't know how pesky/finnicky nvidia drivers are these days.

---

### Post by B92MOR on 2005-11-24
Narcolept, you are a saint.  I started the computer with the recovery mode kernel and ran dpkg-reconfigure xserver-xorg and the system got to the login screen for the first time.

I think I can handle any problems from here on out.  Thanks a ton for the help, and most of all for a fast response!

---

### Post by hasty toweling on 2007-11-20
I had this exact same thing and struggled with it for 3 or 4 days before finally figureing out what the problem was.  None of the posts in the forums were of much help and this issue almost forced me back to Windows.  The problem seems to be that Ubuntu was recognizing the wrong pci slot.  My BIOS does not have an option to disable the integrated video, only to set the pci video as having a higher priority.  Ubuntu must not have understood what the BIOS was talking about and persisted in looking at the onboard video slot for the graphics card.  And because I had installed the drivers for the pci card, everything went haywire and I wound up with black screens, stalled boot scripts, and the like.

The exact steps that need to be taken to fix this problem are this:

0: make sure the system works with your old card.

1: physically install your video card.

2: reboot the computer

3: Go to a terminal and type "lspci".  This lists all of the devices attached to your machine.  Locate the one for your new card.  Write down the slot information.  It should look something like "00:0a.00".  Note that this is in HEX.  It needs to be converted to DECIMAL first.  The case above would translate to "00:10:00".  

4: run "sudo dpkg-reconfigure xserver-xorg".  Fill out the fields.  Pay special attetion to the driver part (use 'nv' if you're using an nvidia card) and the pci slot part.  Leave everthing else as default.

5: reboot

That should do it.  It's simple once you figure it out, but to a newbe like myself you don't know where to begin--you just know that it doesn't work and windows does.  Someone not as persistent and technically interested as me would have given up and gone back to Billy G.

If we're going to make this work, we need to be more detailed in these posts and for the love of Pete, *follow up once you've found a solution and describe exactly how you resolved it*.

---

