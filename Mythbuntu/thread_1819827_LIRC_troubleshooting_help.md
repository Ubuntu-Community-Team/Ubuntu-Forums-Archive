---
title: "LIRC troubleshooting help"
date: 2011-08-06
forum: Mythbuntu
---

### Post by beartard on 2011-08-06
My mythbuntu setup is working fine with the mceusb remote I configured at the original installation.  I recently purchased a DirecTV remote to try.  The reason for this is it's a universal remote designed for a DVR, so it controls my TV, cable box, and mythtv.

Of course, I can program the remote itself to control a Microsoft device that's compatible with mceusb, but it's lacking functionality for crucial buttons (like "guide".)

I found a config file for the remote on the LIRC site.  I installed LIRC on my desktop to test and tweak it.  Everything works fine.  It shows up in irw perfectly.

I copied the file to a new directory as /usr/share/lirc/remotes/directv/lircd.conf.directv.  I edited my /etc/lirc/hardware.conf to include this file.  Then I added the button functions for the remote in ~/.lirc/mythtv.  I have restarted LIRC and even rebooted, but I can't get the remote to show codes as a DirecTV remote in irw on the mythbuntu box.

I'm not even sure where to begin troubleshooting this.  Is there anything different about LIRC on mythbuntu that I should be aware of?  After all, it did work perfectly on my desktop (which is Ubuntu without MythTV.)

Attached are my lircd.conf.directv and lircrc files for mythtv.  Any help would be appreciated.

---

### Post by worldwidejoe on 2011-08-07
Check that the name of the remote in your lircd.conf.directv file is exactly the same as it is in your hardware.conf file.  So for you that would be directv.  If they're different it seems to break things.

---

### Post by beartard on 2011-08-08
Thanks for the response.  My hardware.conf contains an include line that points to the lircd.conf.directv.  The remote name inside that file is "directv" which matches the button settings in my mythtv (lircrc) file.

---

### Post by rileyp on 2011-08-09
Are you trying to use irsend?
Are you using natty?
Can you send anything at all?
If you can could I please see your hardware.conf
Im using mythbuntu and have the receiver working but cant get it to send.
Maybe we could help each other...
cheers rileyp

---

### Post by beartard on 2011-08-09
I have attached both my hardware.conf and my lircd.conf files.

As far as setup, I'm using mythbuntu natty.  Everything is set up pretty much just as it came out the box.  The only changes I've made as far as lirc goes is the files I've attached here and above.  I'm not sure what irsend is, honestly, as I haven't added anything or taken anything away from the initial setup.

The receiver "sees" the remote sending codes, but doesn't recognize them.  I have several mceusb remotes that work perfectly with the setup.  In fact, I can program one of the DirecTV remote's devices as a Microsoft DVR.  It sends most, but not all buttons.  This is a limitation of the remote's internal programming, however.

I'm trying to add my DirecTV remote so that lirc/myth recognizes both mceusb and directv.  irw on my desktop can recognize the codes from the above files, but my myth box will not.

---

### Post by AlecJ on 2011-08-10
Your hardware file points to this file 
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
on line 9

Either copy and paste the contents of lircd.conf.directv at the bottom of mceusb/lircd.conf.mceusb file or point to the location of your lircd.conf file you posed, on line 9.
It would appear that its not reading the .conf file for your Direct tv remote.

---

### Post by beartard on 2011-08-10
I appreciate the response.  I tried your advice.  Without knowing how to specify two separate lircd.conf files in hardware.conf, I commented out the line for the mceusb remote and just left the directv remote.  I have the same results I had before.

I've had some strange behavior lately with remotes and was playing around earlier today.  The strangeness I noticed was that, when I'd do anything tv-related (volume, mute, tv-power) both the tv and mythfrontend would change volume or mute at the same time.  I fired up irw again and noticed that lirc is indeed seeing my directv remote, even without a change to hardware.conf.  Unfortunately, it's only seeing these tv-related buttons.

When I got my directv remote, I programmed it for my tv using codes provided by directv.  This remote is one that sends volume signals directly to the tv by default.  When I did irrecord originally, it assumed I wanted to use tv volume codes for mythfrontend volume as well.  Makes sense.  Since I had also set actions in lircrc (mythtv) for the remote's volume buttons, I got a response from both devices.

Now, back to my desktop box.  My hardware.conf still points to the mceusb file, but irw sees my directv codes correctly as they should.

Still scratching my head.

Edit:  I've compared the files in /etc/lirc as well as /usr/share/lirc and they're identical.  I even checked ownership and permissions, just to be sure.  That would lead me to believe that whatever is standing in my way would be in my home directory on the MythTV box.

---

