---
title: "PVR-350, IR Blaster and DirecTV issues"
date: 2010-01-09
forum: Mythbuntu
---

### Post by scsever on 2010-01-09
I have Mythbuntu 8.10 installed and decided to give the an blaster a try, but having problems. My setup is the PVR-350, a Hauppauge silver remote, a homemade serial IR blaster and a DirecTV D11 receiver.
In MCC for remote I selected Hauppauge TV card.  This works fine by itself for doing the basic MythTV navigating.  When I decided to thy out the IR blaster I kept this same remote selected, did not select dynamic mapping and selected serial port DirecTV IR.  After doing this my Hauppauge remote no longer does anything at all, won't even navigate MythTV.  I then opened MCC and selected dynamic mapping but the remote still would not do anyting.  I opened MCC again and removed the IR support and now the Hauppauge remote navigates MythTV again.
One thing I realized after doing this is that I was no longer sure how my remote was supposed to work.  When it is working and I change a channel from the remote it will change a channel on my tuner card but if I get it setup to be the IR blaster remote will it then automatically change channels to the dish receiver and no longer control the tuner card?  Should I still be able to navigate the MythTV menus after it is setup as the IR blaster remote?  Guess I'm a little confused on what to expect when this is working, maybe I'll need two remotes, one for Myth and one for IR blaster?  
Any help on resolving this issue would be greatly appreciated.
As a side note I do have a Gyration 3101 if that could be used for the IR blaster controller.

Thanks,

---

### Post by IceCap on 2010-01-09
Hi,

  I have almost identical setup here (PVR-350, DirectTV D11-800).  I went through this last year.  The problem you are having is a hickup in the setup.  The problem has to do with the remote software loaded before the ir-blaster software and that messes up the remote software (lirc).  There are post here on how to fix this which involves editing a text file somewhere (I can't remember this in detail, it was over a year ago I was working on this).

  However, I strongly recommend controlling the Directv box with a serial cable.  Well, you need a NULL modem cable and specific serial to USB adapters.  Search for "directv.pl" or go [**here**]("http://www.pdp8.net/directv/directv.shtml").
This works really well and much easier to setup than ir blasters.  Note that you might need to update the software on your Directv receiver (I had to in order to get the serial/USB port on the receiver working).  Updating the software is described in the receiver manual but it requires starting it up and pressing some buttons on the remote at the same time.

   Somewhere in the MythTV setup is a field for changing channel commands and all you need to put there is "directv.pl" (or maybe "directv.pl ON" to make sure the receiver is turned on.  You then edit the directv.pl file to match your system (it is all described in the file an on the website).  You have D11 and it uses 9600 baud (well, mine does).  Then you can use the script to automatically turn the received on and off as well.

  I started the IR blaster route (using 8.04) and spent days trying to get it to work.  Finally gave up and once I got the right serial cable that route was so much easier.  Again, not all serial to USB dongles work.  You need to buy one of those that are listed to work.

  Just don't hook the receiver up to the USB port on your computer.  It isn't a proper USB port, but a serial port with a USB plug.

  Hope this helps.

  IC

---

