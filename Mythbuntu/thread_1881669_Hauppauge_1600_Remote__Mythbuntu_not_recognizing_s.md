---
title: "Hauppauge 1600 Remote:  Mythbuntu not recognizing some buttons"
date: 2011-11-15
forum: Mythbuntu
---

### Post by alotau on 2011-11-15
Using a fresh 11.10 Mythbuntu installation on newly bought hardware.  Have Hauppauge 1600 installed and am able to watch live TV, which, after many painful hours of configuring and searching Internet, I am WAY more impressed with than my wife is.

After further research I did manage to get the remote to be recognized.  Many buttons seem to work.  Here is the configuration I ultimately ended up using in my /etc/lirc/hardware.conf as suggested in a few places:

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="ir_kbd_i2c lirc_dev lirc_i2c"
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/event5"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

```The arrow keys work fine.  I could configure in the frontend GUI the buttons for +/- channels, play, ffwd, etc.

The big problem is that the "OK" button seems completely unrecognized in Mythbuntu.  For example, when mapping/configuring keys using the frontend GUI, most keys on the remote are accepted as options, but when I press "OK" as the button of choice nothing happens.  When moving around the menus in the frontend, OK does nothing.

I can see that "OK" is sending a signal by doing:

$ sudo cat /dev/input/event5

and pressing some buttons.  When I press "OK" (or any other remote button) gibberish hits the screen while doing that cat.

I've already read other suggestions in other posts about just buying a different remote that is better supported, but I've come this far, I'd love to get this thing working properly.

I feel overmatched by the irrecord, irw and associated commands, but am willing to try things.  I'm hoping the fix is something like a couple edits in a key-mapping file and a re-boot, but I'm used to having my Linux hopes dashed.

Any help appreciated and I'm happy to provide further details as needed.

Thanks.

---

### Post by alotau on 2011-11-22
Couldn't wait anymore.  Bought an MCE remote and it worked out of the box.

I guess the mystery of the non-functioning buttons will go unsolved for me.

---

### Post by SirKingChase on 2011-12-23
Still unsolved - 

I am having the exact same problem, running Ubuntu 11.10 as well.  Only buttons that work our volume and arrow keys.  I spent so much time getting all this stuff set up, it is really disappointing.  I am giving up as well.

Are you still using the 1600 IR? Or a USB one?
What remote did you get? Will any MCE remote work?

---

### Post by alotau on 2011-12-24
I agree that it is really disappointing.

I honestly don't think the MCE remote I got had a brand name.  It was the only MCE Remote at the computer shop I went to, so I just bought it and hoped for the best.  It worked for me.  It says "Certified for Windows Vista" on the user manual, if that helps at all.

It has a USB receiver that works quite well.  I haven't tried to use it to control any other devices yet, so I can't speak to that.

I can tell you that the one I bought is NOT pictured here:

[http://www.mythtv.org/wiki/MCE_Remote]("http://www.mythtv.org/wiki/MCE_Remote")

but it obviously looks quite similar.

Good luck.

I'm still struggling with getting the TV out to work when I don't have a computer monitor also connected.  Ugh.

---

### Post by flatspin on 2012-07-08
I finally got this fixed for my HVR-1600 card.  Seems lirc sees it as a HVR-1100 and the irw codes do seem to match the HVR-1100, except for one.  And this is why the OK button didn't work.

In:
/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge

It is listed as:
       Ok              0x001C

Which is wrong.  The code should be:
       Ok              0x0160

Edit and save it.  Bounce your lirc (/etc/init.d/lirc restart) and you should have your OK button back.

---

### Post by anonymousdog on 2012-07-08
> **flatspin said:**
> I finally got this fixed for my HVR-1600 card.  Seems lirc sees it as a HVR-1100 and the irw codes do seem to match the HVR-1100, except for one.  And this is why the OK button didn't work.

In:
/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge

It is listed as:
       Ok              0x001C

Which is wrong.  The code should be:
       Ok              0x0160

Edit and save it.  Bounce your lirc (/etc/init.d/lirc restart) and you should have your OK button back.
Please, please, please make a note of this in the [Wiki for this card]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600#IR_Remote")!

---

### Post by samcoinc on 2012-11-11
I am hoping someone can help.  New install of mythbuntu from the livecd.  Without changing anything - some keys work on the remote.  (1600 black) but if I try to select any usb remote from the configureation setup - the remote stops working.  (like selecting the above hvr-1100.  I am at a loss.  Like I say - the remote sort of works without selecting a remote in the mythbuntu setup.  

I have tried a buch of things (starting from a fresh install each time) and the only way it seems to sort of work is if I don't select any remote.  I tried also jaus site here - no go 

[http://jaysdesktop.blogspot.com/2012/06/configuring-lirc-for-hvr-1600-in-ubuntu.html](http://jaysdesktop.blogspot.com/2012/06/configuring-lirc-for-hvr-1600-in-ubuntu.html)

thanks!
sam

---

### Post by samcoinc on 2012-11-11
This is what I get when I plug it in

```

[  383.429024] Registered IR keymap rc-rc6-mce
[  383.429262] input: Media Center Ed. eHome Infrared Remote Transceiver (0609:0334) as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/rc/rc1/input16
[  383.429558] rc1: Media Center Ed. eHome Infrared Remote Transceiver (0609:0334) as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/rc/rc1
[  383.429843] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input17
[  383.431856] rc rc1: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[  383.624074] mceusb 4-2:1.0: Registered SMK CORPORATION MCE TRANCEIVR Emulator Device 2006 with mce emulator interface version 1
[  383.624087] mceusb 4-2:1.0: 2 tx ports (0x0 cabled) and 2 rx sensors (0x0 active)

```

---

### Post by samcoinc on 2012-11-13
ok - so I followed thise directions  (2nd post.)

[http://forum.xbmc.org/showthread.php?tid=141868&pid=1237617#pid1237617](http://forum.xbmc.org/showthread.php?tid=141868&pid=1237617#pid1237617)

(I am skunkworks)

Using the /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb for the lircd.conf file.  I get sane output from irw

Now I just need to figure out how to get mythbuntu to see it..  I am searching and it doesn't seem anyone has a corisponding lircrc based on the above lircd.conf...

sam

---

### Post by samcoinc on 2012-11-13
Ok I found mce remote lirc.conf and ~/.lirc/mythtv files. (top 2)

[http://petersmith.homeip.net/wiki/index.php/MythTV_Remote](http://petersmith.homeip.net/wiki/index.php/MythTV_Remote)

This seems to work well (light testing)

Also - I was getting double key presses..  After even more searching..

[http://ubuntuforums.org/showthread.php?p=10709651#post10709651](http://ubuntuforums.org/showthread.php?p=10709651#post10709651)

I edited  /etc/rc.local and added

echo lirc > /sys/class/rc/rc0/protocols

That seemed to fix it.  Now on to setting up channels..  :)

sam

---

### Post by samcoinc on 2012-11-14
oh - and the important parts of my hardware.conf file

#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

---

