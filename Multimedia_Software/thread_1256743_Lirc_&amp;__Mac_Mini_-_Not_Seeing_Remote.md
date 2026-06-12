---
title: "Lirc &amp;  Mac Mini - Not Seeing Remote???"
date: 2009-09-03
forum: Multimedia Software
---

### Post by BDPNA on 2009-09-03
I've been spending over a week now attempting to get ANY remote (Apple remote, Harmony, etc) to send commands to ubuntu (and then XBMC, but first just seeing it work in Ubuntu would be fine).

I've done a lot more trial and error and still no luck here...One day I have no idea what I did and suddenly the Apple remote was sending commands to Linux for volume up/down, then I rebooted and it was gone.  So I know this is possible.

Anyway I looked into some system logs and I hope maybe someone can look at this and help me make sense of what's happening with lirc on my mini and what I'm doing wrong.  I've changed some system config files not relating to lirc in my search for a fix, so maybe I messed something up.

First of all, can someone tell me where this is coming from?  I do not have a mce remote, just an apple remote and a Harmony set up as a Plex device, but I may have accidentally grabbed the wrong code and put it somewhere:

```
Aug 25 15:15:21 MacPlex kernel: [ 2507.167236] lirc_dev: IR Remote Control driver registered, major 61 
Aug 25 15:15:21 MacPlex kernel: [ 2507.168899] 
Aug 25 15:15:21 MacPlex kernel: [ 2507.168901] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.51 $
Aug 25 15:15:21 MacPlex kernel: [ 2507.168905] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
Aug 25 15:15:21 MacPlex kernel: [ 2507.171550] usbcore: registered new interface driver lirc_mceusb2

```Also from the system log at bootup, it seems it starts a client then around 30 seconds later it stops, however when I try and run lircd from command line it always says it's running:

```
Aug 25 21:14:18 MacPlex lircd-0.8.4a[4267]: accepted new client on /dev/lircd
Aug 25 21:14:18 MacPlex lircd-0.8.4a[4267]: initializing '/dev/usb/hiddev0'
Aug 25 21:14:19 MacPlex avahi-daemon[3001]: Invalid query packet.
Aug 25 21:14:19 MacPlex last message repeated 2 times
Aug 25 21:14:32 MacPlex lircd-0.8.4a[4267]: removed client
Aug 25 21:14:32 MacPlex lircd-0.8.4a[4267]: closing '/dev/usb/hiddev0'

```Anyway I'd sure appreciate a little help if anyone could offer up any.  I have read 20 pages about lirc and the mac mini and still for whatever reason I can't get this thing to work, can't even get irw to see a remote.  Once I get the receiver working the rest seems easy.

I also just tried an app called gnome-lirc-properties which is a nice GUI but it's locking up when I attempt to auto detect, and when I manually select the mini's IR receiver under manufacturer and model, it claims it can't see the device.  

Is there something else I can do to see if my Mac Mini's IR receiver is getting initialized properly?

Thanks for any help, I am going out of my dang mind!

---

### Post by BDPNA on 2009-09-04
Just a little more info here, it looks like lirc only tries to start when I run IRW:

```

Sep  4 00:04:32 MacPlex lircd-0.8.4a[2470]: accepted new client on /dev/lircd
Sep  4 00:04:32 MacPlex lircd-0.8.4a[2470]: initializing '/dev/usb/hiddev0'

```

When I exit IRW, I get this:

```

Sep  4 00:04:48 MacPlex lircd-0.8.4a[2470]: removed client
Sep  4 00:04:48 MacPlex lircd-0.8.4a[2470]: closing '/dev/usb/hiddev0'

```

When I restart the server, I see this:

```

Sep  4 00:05:39 MacPlex lircd-0.8.4a[2470]: caught signal
Sep  4 00:05:39 MacPlex lircd-0.8.4a[4542]: lircd(macmini) ready

```

Any idea what might be wrong?  A permissions thing with the files or my user?  Is the fact I have a wireless mouse and keyboard hooked up to the mini throwing things off, or perhaps on a different hiddev?

Help??

---

