---
title: "Tuner Problem: Kworld, no audio on analog channels."
date: 2007-10-21
forum: Mythbuntu
---

### Post by am_pcguy on 2007-10-21
I just built a MythTV box for the first time.  I chose Mythbuntu as I've been using Ubuntu on daily for over a year now.  

I have a Kworld 115 tuner card.  I followed the instructions at the [MythWiki]("http://mythtv.org/wiki/index.php/Kworld_ATSC_110") to set up the card. 

After I configure the MythTV backend I have a V4L card on /dev/video0, and a DVB card.  The DVB card plays, and captures HD perfectly.  The Analog side however has no audio.

I've seen lots of posts about adding saa7134-alsa to /etc/modules, /etc/modprobe, or /etc/modules.conf.  I've tried each way.  I also noticed that in /etc/modprobe.d/alsa-base there are 2 entries that refer to saa7134-alsa 

> install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
and 
> options saa7134-alsa index=-2

So it should be loaded, and it appears to assign a -2 to the device, so it won't take /dev/dsp0 and be the main sound card for the system.  

My Dmesg however puts the saa7134[0]/alsa device on IRQ11 and sets it to -1. 
I'm not sure if all of that is tied together.  When the machine boots I have no sound on the analog side.  If I use the commands to un-mute from the wiki entry above, or do alsamixer -c 1 and un-mute the audio there I get a high pitched noise from the analog tuner.  

Perhaps I don't have a full understanding of the way the modules are loaded and how the system defines the PCI sound on the card.

Has anyone had luck getting sound on the analog side of this card?  Am I just getting overly confused and missing something?  I just did a full reinstall so I'm back to ground zero.  I'd really like to add another tuner to the system but I've only got one more PCI slot and I'd hate to waste it on a SD only tuner.

Thanks,

---

### Post by am_pcguy on 2007-10-22
I reinstalled Mythbuntu.

This time I learned that /etc/modprobe.d/ holds all of the modules that need to be loaded for Debian based Linux 2.6.  When you want to add modules to load create a new file in that directory.  Enter your settings then "sudo modules-update".  

Also to make sure you are not already loading, or loading and setting options you don't want you can search each file for listings.

For example I found that "cat /etc/modprobe.d/alsa-base | grep saa7134" told me that the saa7134, and saa7134-alsa were loaded in that file.  Other options that I was told to set in the Mythtv Wiki entry for my Kworld 115 were partially set in /etc/modprobe.d/aliases.  I edited the entries adding the needed settings, ran "sudo modules-update" and rebooted.  Everything loaded as it should.

Now I still don't have "working" audio from the analog side of the tuner card.  I have audio but it is high pitched and to fast.  I think this may have something to do with the mpeg2 encoding but I don't really know how to check.  

The other problem I have (that I didn't have before the reload) is X isn't picking up my projector settings.  I manually edited xorg.conf with the correct info for my projector, and have the binary nvidia drivers installed.  When I reboot the screen defaults to 640x480 becuase of the "failsafe".  If I plug in a different monitor I can open "sudo nvidia-settings" and set the resolution to 1280x720 60, then switch the cable back to my projector and the output is perfect.  However if I reboot or restart x it goes back to the 640x480.

---

### Post by Bally on 2007-10-28
Hi

 I am also having issues with sound from analouge card...

however in response to the projector issue can you post your xorg.conf listing?

Cheers Bally

---

### Post by SM0k3 on 2007-11-06
BUMP, I need help with this also I using a KWorld ASTC 115 card. I'm getting a TV signal through TVTime but not getting any sound. 

Thanks

---

### Post by buntu92104 on 2007-12-02
> **am_pcguy said:**
> I reinstalled Mythbuntu.

This time I learned that /etc/modprobe.d/ holds all of the modules that need to be loaded for Debian based Linux 2.6.  When you want to add modules to load create a new file in that directory.  Enter your settings then "sudo modules-update".  

Also to make sure you are not already loading, or loading and setting options you don't want you can search each file for listings.

For example I found that "cat /etc/modprobe.d/alsa-base | grep saa7134" told me that the saa7134, and saa7134-alsa were loaded in that file.  Other options that I was told to set in the Mythtv Wiki entry for my Kworld 115 were partially set in /etc/modprobe.d/aliases.  I edited the entries adding the needed settings, ran "sudo modules-update" and rebooted.  Everything loaded as it should.

Now I still don't have "working" audio from the analog side of the tuner card.  I have audio but it is high pitched and to fast.  I think this may have something to do with the mpeg2 encoding but I don't really know how to check.  

The other problem I have (that I didn't have before the reload) is X isn't picking up my projector settings.  I manually edited xorg.conf with the correct info for my projector, and have the binary nvidia drivers installed.  When I reboot the screen defaults to 640x480 becuase of the "failsafe".  If I plug in a different monitor I can open "sudo nvidia-settings" and set the resolution to 1280x720 60, then switch the cable back to my projector and the output is perfect.  However if I reboot or restart x it goes back to the 640x480.

Can you post the changes you made to load the modules and set the Kworld 115 options?

Thanks!

---

