---
title: "Newbie Nova-T / resolution issues..."
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by bobble_the_hatt on 2007-05-21
Hi all; first post, after battling with a fresh 7.04 install - all help much appreciated!

Having a couple of issues, one simpler than the other (I hope).  Firstly, I seem to be stuck with 800x600 and can't do a damn thing about it.  I've a stock Advent monitor that's being picked up happily as a TG 1550, and my xorg.conf is full of display modes which include 1024x768 (the monitor's native resolution).  This isn't translating into 1024x768 being an option in the Screen Resolution preferences dialog, and I can't find any references to resolution in gconf-editor either - so any other pointers on where to look would be great!  I'm using an ATI Radeon 8500LE if that's any help - I think using the radeon driver, but not sure.  Can check this eve when I get home if that's a possible source of the issue.

Secondly, I'm having trouble picking up my Hauppauge Nova-T (this is intended to be a mythtv box).  THe card seems to be picked up ok (lspci shows plenty of Conexant related lines), and I understand that 2.6.20 doesn't autodetect and load the cx88_dvb module, so I shouldn't expect to see it in the lsmod output.  However, trying to load cx88_dvb fails, meaning I've nothing registered as frontend0 and I can't make any progress in setting anything up (am trying to follow the howto here: [http://www.parker1.co.uk/mythtv_ubuntu.php](http://www.parker1.co.uk/mythtv_ubuntu.php)).

Does anyone have any thoughts?  All suggestions welcomed...

Thanks.

---

### Post by newlinux on 2007-05-21
When you say loading the cx88_dvb module fails, How are you loading it and what happens when you load it?

Do you get an error message?

---

### Post by bobble_the_hatt on 2007-05-21
Thanks for replying - shall do my best to dig everything out this eve and let you know.

I'll make sure I've got the output from:

lspci
lsmod
dmesg
modprobe cx88_dvb

at least - anything else that'd help identify what's up with it?

Thanks again...

---

### Post by newlinux on 2007-05-21
Yep, that will be good.

You may already know this but try running 

```

sudo dpkg-reconfigure xserver-xorg

```

Which will walk you through reconfiguring your xorg.conf.

In any event, for your resolution problem, post your /etc/X11/xorg.conf. I'm not as familiar with the ATI cards and drivers and their quirks, but I might be able to help, or someone else will. I've had resolution recognition problems before, however.

---

### Post by newlinux on 2007-05-21
Also, you might be better off using the tutorials located here:
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by bobble_the_hatt on 2007-05-21
All attached... hope it sheds some light on things.

I did try the dpkg reconfigure route, but all it did was break my mouse input to the extent I couldn't left- or right-click, so I thought I'd ask rather than bury myself deeper :)

Thanks for taking the time to look; much appreciated.

Cheers,

Ross

---

### Post by newlinux on 2007-05-21
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

Is definitely the problem with your card. You'll need to be able to insert that module to get it working. Is the dmesg output you posted before or after trying to load that module? 

As for your resolution, nothing sticks out with your xorg.conf. You are using the "ati" driver, and I'm not aware of any of the issues with that.

I'll look into this more...

---

### Post by bobble_the_hatt on 2007-05-22
Hmmm.

On a closer look, I think something might have been up last night - for a start, there's nothing resembling a DVB card in my lspci output!  There has been before, and I think in that situation I got a longer and more detailed error message from the modprobe - will try and replicate this evening again.

Looking at the resolution issue again, my xorg differs in a few places from what's suggested here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) - notably in the BusID and Option under Device, and the Extensions and ServerLayout sections.  Would changing those settings help, do you think?

---

### Post by bobble_the_hatt on 2007-05-22
Ok, now I do seem to have a card loaded - not sure what was up last time, but nothing a simple remove-blow-PCI-slot-replace didn't fix!

I'm equally stumped still, though I think it may have loaded the card under a different module - I just can't quite decipher the system logs yet so am not sure.  Any guidance, as always, welcomed.

Resolution issue is still plaguing me, and I seem to have screwed a bunch of settings up in the process, but that at least I stand a fighting chance with by myself - the hardware's proving trickier...

Thanks,

Ross

---

### Post by Sangoma on 2007-05-30
Hi,
I have had mythtv up and working for a couple of months using 2 nova-t pci cards.
I used the parker guide and it is very good. Keep persevering, it's worth it!
Have you tried 'sudo modprobe' each of the following? (i needed these to get mine working):

cx88_dvb 
bttv
bt878 
dvb_core
dst 
dvb-bt8xx

Also, I needed to install the firmware upgrade for one of my cards (pre-2004 model), I followed the instructions on the parker guide:

[http://parker1.co.uk/mythtv_novafw.php](http://parker1.co.uk/mythtv_novafw.php)

I found the following guide quite useful especially when getting the remote working, old versions guide but in-depth and useful non-the-less:

[http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html](http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html)

Hope that helps a little. :D

---

