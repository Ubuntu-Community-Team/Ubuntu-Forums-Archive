---
title: "irblaster or commandir"
date: 2008-09-24
forum: Mythbuntu
---

### Post by kameleon25 on 2008-09-24
I am looking to swap over to Dish Network from Comcrap. With this change I will be getting 3 or 4 extra dish boxes that will hook up via the composite cables to the inputs of my 2 PVR-500's. I need a way to control these boxes though. I have looked at the irblaster and commandir. I do not have a serial port on my Gigabyte motherboard though. But I could use a USB to serial adapter if needed. I like the features of the commandir but of course the price of the irblaster. Any input on this subject?

Thanks in advance.

---

### Post by kameleon25 on 2008-09-26
Anyone?

---

### Post by rubrboots on 2008-09-26
I dont know anything about commandir. However, I have setup several systems with the serial homebrew style irblaster, which works very well. You will need a lircd.conf file for your stb, they are several available for dish network boxes. 

If you are trying to control more than one "identical stb's" via a serial irblaster you may have problems. In this case you would need a separate irblaster for each box and lirc is setup by default to operate a single serial port. It is possible to have 2o instances of lirc to achieve this, but I have not been able to get it work myself. I you are able to do it please let me know how you did it.

---

### Post by anonymousdog on 2008-09-26
First, a high-level overview of lircd and MythTV: [http://www.mythtv.org/wiki/index.php/LIRC](http://www.mythtv.org/wiki/index.php/LIRC)

There's two overall ways you can go:
[LIST=1]
[*]Use one blaster to control multiple receivers set to use unique code sets
[*]Use a unique emitter or blaster for each receiver (using the standard code set)
[/LIST]

**First option**:
In the first instance, you use one blaster and one or more emitter(s) sending IR signals visible to all receivers (i.e., the emitter[s] positioned where all receivers can "see" them).  This requires setting all receivers to use unique codesets (step 8 on [this page]("http://www.eggshellskull.com/lirc/multi/index.php")), configuring lircd to include configuration for each of the [codesets]("http://www.mythtv.org/wiki/index.php/DISHNetworkLIRCConfiguration") as discrete remotes, and a discrete (for each tuner) channel change script that defines the remote (codeset) for irsend to use (by referencing the discrete remote names in the lircd configuration).

Using a PVR-500 MCE edition (MCE-compatible) usb remote/receiver/blaster, you can have both emitters sending the same signal (so you only have to position each emitter to be visible to two receivers instead of four).  Unless you set irsend to use only one of the emitters, the dual-emitter blaster sends the same signals to both.

Most any supported usb blaster will work; I'd prefer that over a serial-to-usb converter and a serial blaster.

I believe the standard Mythbuntu lirc configuration for dish set top box and the mce_usb remote includes the 16 codeset /usr/share/lirc/transmitters/dish/general.conf file for Dish network.  So, the fiddly work is positioning your emitter(s) so all receivers can see their signals, modifying pretty standard channel change scripts to designate separate remotes for each receiver, and setting up three of the receivers to use non-standard code sets.

**Second option**:
If you go the unique blaster per each tuner option, you get easier/cleaner emitter placement but more complication and/or expense in setting up the blaster equipment.  The CommandIR is the perfect device for this task: four emitters in once device mitigates most of the setup complication (at a price).

If you've got the IR remote/receiver/blasters that come with MCE editions of the PVR-500, those work out of the box.  Well, at least one of them will.  There's a wiki entry on the mce_usb remote which covers most of the setup.  The dual blasters on each unit can be referenced with an argument to irsend in your channel change scripts.  Getting the second blaster/remote working could be a challenge with some lirc configuration and init script hacking and maybe a udev rule (something like [this](http://www.mythtv.org/wiki/index.php/Volume_Knob_on_Antec_Fusion#Edit_udev_rules) or see [here](http://ubuntuforums.org/showthread.php?p=5660316)) to ensure that there is a static device node for each blaster that survives reboot (otherwise, blasters might switch device numbers randomly).  Then, your channel change scripts will have to designate an irsend --device option (and, optionally, set transmitters for multi-emitter devices [see [here](http://www.mythtv.org/wiki/index.php/MCE_Remote#IR_Blasting)]).

You can get all that working, but it may not survive updates/upgrades well and may increase maintenance in other ways.  Similar complication will be had for all multi-blaster setups, and only slightly less so if each blaster is a unique hardware type/model.

Bottom line: [LIST]
[*]If you can live with positioning of receivers and emitter(s) so you can use one blaster, I'd do that.  That'd work nicely if the backend and receivers were tucked away in an unused room, basement or closet.
[*]If you really need an emitter per each receiver so that emitters can be stuck directly on each receiver, I'd go with the CommandIR (though I have no experience with getting those working with lircd or MythTV).[/LIST]

---

### Post by rubrboots on 2008-09-26
Thanks for the info anonymousdog, method 2 is my only option as all of my stb's respond to the same remote control. I am not interested in buying a commandir so its irblaster or nothing. I am crossing my fingers that support for multiple serial ports will be built into lirc sometime soon.:)

---

### Post by anonymousdog on 2008-09-26
Read more carefully: Most Dish receivers can be set to use any of 16 available code sets.  It's essentially programming the receivers to use a different remote control.  So tuner2 wouldn't respond to IR commands sent to tuner1 because those commands wouldn't correspond to any in tuner2's code set...therefore, it doesn't respond.

---

### Post by rubrboots on 2008-09-26
Actually, I am using motorola boxes, same as comcast boxes. The original poster is the one switching to Dish boxes. I wonder if the motorola boxes have the same function available. I will have to look into that.

---

### Post by kameleon25 on 2008-09-30
Thanks for the input. I don't knwo why I didn't get the notification there were replies. Looks like I will have to go with the commandir due to the USB functionality. Unless a usb to serial adapter would work well enough. I will do a little homework on that also to try to save some dough.

---

### Post by anonymousdog on 2008-10-01
Why not go with one blaster and 4 (of 16 available) code sets on your receivers?  That strategy has very little downside, and the usb blasters are cheap.

---

### Post by Eric Boring on 2008-10-01
> **kameleon25 said:**
> I am looking to swap over to Dish Network from Comcrap. With this change I will be getting 3 or 4 extra dish boxes that will hook up via the composite cables to the inputs of my 2 PVR-500's. I need a way to control these boxes though. I have looked at the irblaster and commandir. I do not have a serial port on my Gigabyte motherboard though. But I could use a USB to serial adapter if needed. I like the features of the commandir but of course the price of the irblaster. Any input on this subject?

Thanks in advance.
 I struggled for quite a while with LIRC on a serial IR blaster. I never could get it working. The CommandIR on the other hand, worked out of the box (with a clean install--I had pretty well messed up LIRC by the time I switched gears.) For me it was well worth the $100 (I got the mini), since it's a transiever, and since without it, I don't know if I ever would have gotten my set-top box working.

-Josh

---

### Post by kameleon25 on 2008-10-07
So I am wondering should i get the regular CommandIR mini or the CommandIR II? At this point I will only have 2 dish boxes on the mythtv box. I see that the mini does not do the 56k option. Is this needed on dish receivers?

---

