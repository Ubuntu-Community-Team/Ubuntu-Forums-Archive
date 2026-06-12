---
title: "Graphics Problems with Mythbuntu 9.10 beta"
date: 2009-10-19
forum: Mythbuntu
---

### Post by dualboot on 2009-10-19
Hi All,
Hope its OK to ask questions on the beta.  Not sure its to do with MythTV anyway.

I have an ASUS P2-M2A690G with an Athlon Dual Core 4800+ and a built in ATI RadeonTM 1250.  It was bought with a NovaT 500 and Mythbuntu 8.04 pre-installed, and worked well.  I use the HDMI output and run at 720p.

I want to upgrade, and move to 64 bit, but rather than risk any mis-haps I bought a second hard drive and did a clean install of the current 9.04 64 bit yesterday.  It seemed to install OK, and the desktop looked OK, but Mythtv (setup or normal fronted) were just big blocks of colour with no text.  I guessed it was working because in the frontend if I hit escape then down arrow then enter it came back out to the desktop.

Anway - being flighty, rather than persevere I downloaded the daily build of the 9.10 beta 64 bit ISO a few days ago, and this has come up fine.  Both desktop and MythTV fronted work properly, though to start with the NOVA-T could find no channels.  

In the desktop menu's applications - settings - display there is only one resolution (1280*720).  After a few minutes it popped up a 'there is a restricted driver available' which I leapt on, but it was for the Nova-T.

The Nova-T is working OK now, but the video is a bit jerky, an I suspect I need to find a way to get it to use the correct driver.

The 'manage restricted drivers' screen only shows the Hauppage one.

---

### Post by bsntech on 2009-10-19
try the following:

Hit Ctrl + F1 on your keyboard

It will take you to a black screen with a login prompt.  Put in your username/password in here that you used to setup Ubuntu.

After logging in, type "sudo /etc/init.d/gdm stop"

After it stops, type in "sudo X -configure"

This will then create a new xorg.conf file and it will tell you where the file is placed and the name of the file - usually it will put it in ~/xorg.conf.new

Now, copy this file and overwrite the other xorg.conf file:

"sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup"  (This will backup your currenty config)
"sudo cp ~/xorg.conf.new /etc/X11/xorg.conf" (This will put in the new xorg.conf file in the appropriate spot.  ENSURE that the ~/xorg.conf.new file is the one that the X -configure made for you.

Then reboot and see if that helps.  This will setup X to use the proper ATI driver for your video card.  With the blocks of colors and such that you mention, it very well may be that the incorrect driver is being used currently for your X Windows System.

---

### Post by dualboot on 2009-10-19
Thanks bsntec - I will give that a try as soon as I can - I had to re-install the old hard disk in time to record flashforward !

---

### Post by dualboot on 2009-10-21
I generated the new xorg.conf file.  It seems to pick up the right information - monitor is a Panasonic, BoardName is "RS690 [Radeon X1200 Series]

but on re-booting its the same.  I went back in to the Cntr-alt-F1 and shut down gdm again and re-ran 'sudo X -configure' and tried the test it suggests 'X -config xorg.conf.new' but that just gives me a blank screen.

cntrl alt F1 gets me back to a list of messages that don't mean much, but don't look bad -  all say success except on which says

"(EE) GLX error: Can not get required symbols."

Any ideas ?  

Just for thoroughness I worked my way through the setting in the TV playback menu - CPU-/+/++/Normal etc etc everyone - none were smooth though.

---

### Post by GoMad on 2009-10-22
Hi,
 
I had this when I upgraded from 9.0.4 to 9.10 and I search everywhere for the answer. It sppears to me 'upgrading' rather than a fresh install blats your gnome config. The only way I could get this to work (and it did !) was.
 
Ctrl+F1 -> command prompt
 
sudo apt-get install gnome-console
 
this reinstalled all the console stuff, fixed the block colours and te repeat login screen issue I had. You could do the dpkg-reconfigure kdm and if that gui works the above will almost certainly resolve the gnome issues.
 
Let me know as this fixed it for me !

---

### Post by dualboot on 2009-10-22
"sudo apt-get install gnome-console" gave not found.
Come to think of it, isn't mythbuntu xfce not gnome (though service gdm stop works ? )

Also re-reading your reply, mine was a clean install.

---

