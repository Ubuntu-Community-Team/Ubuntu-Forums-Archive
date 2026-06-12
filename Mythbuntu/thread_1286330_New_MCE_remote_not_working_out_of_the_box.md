---
title: "New MCE remote not working out of the box"
date: 2009-10-08
forum: Mythbuntu
---

### Post by dfinn on 2009-10-08
Just bought this remote : [http://www.newegg.com/Product/Product.aspx?Item=N82E16880121003](http://www.newegg.com/Product/Product.aspx?Item=N82E16880121003)

irw sees the buttons being pressed but myth does not.

I went through the config in MCC, selected the new version of MCE remote. 

Here's the output from dmesg when I plug in the receiver and from the output from irw:

[   72.072032] usb 2-3: new full speed USB device using ohci_hcd and address 3
[   72.284107] usb 2-3: config 1 interface 0 altsetting 0 endpoint 0x1 has an invalid bInterval 0, changing to 32
[   72.284113] usb 2-3: config 1 interface 0 altsetting 0 endpoint 0x82 has an invalid bInterval 0, changing to 32
[   72.299297] usb 2-3: configuration #1 chosen from 1 choice
[   72.500025] usb 2-3: reset full speed USB device using ohci_hcd and address 3
[   72.716924] lirc_dev: lirc_register_plugin: sample_rate: 0
[   72.723428] lirc_mceusb2[3]: Topseed Technology Corp. eHome Infrared Transceiver on usb2:3
dfinn@freevo:~$ irw 
000000037ff07bdd 00 OK mceusb
000000037ff07be0 00 Down mceusb
000000037ff07be0 01 Down mceusb
000000037ff07bdf 00 Left mceusb
000000037ff07bdf 01 Left mceusb
000000037ff07bde 00 Right mceusb
000000037ff07bde 01 Right mceusb

when starting mythtv in verbose mode I get the following:

dfinn@freevo:~$ mythfrontend -v important,general
2009-10-08 19:58:33.223 Using runtime prefix = /usr
2009-10-08 19:58:33.749 XScreenSaver support enabled
2009-10-08 19:58:33.749 DPMS is active.
2009-10-08 19:58:33.750 Empty LocalHostName.
2009-10-08 19:58:33.750 Using localhost value of freevo
2009-10-08 19:58:33.758 New DB connection, total: 1
2009-10-08 19:58:33.764 Connected to database 'mythconverg' at host: localhost
2009-10-08 19:58:33.766 Closing DB connection named 'DBManager0'
2009-10-08 19:58:33.768 Primary screen 0.
2009-10-08 19:58:33.768 Connected to database 'mythconverg' at host: localhost
2009-10-08 19:58:33.770 Using screen 0, 1280x1024 at 0,0
2009-10-08 19:58:33.779 New DB connection, total: 2
2009-10-08 19:58:33.779 Connected to database 'mythconverg' at host: localhost
2009-10-08 19:58:33.783 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-10-08 19:58:33.783 Enabled verbose msgs: important general
2009-10-08 19:58:34.414 No theme dir: /home/dfinn/.mythtv/themes/Mythbuntu-8.04
2009-10-08 19:58:34.416 Primary screen 0.
2009-10-08 19:58:34.417 Using screen 0, 1280x1024 at 0,0
2009-10-08 19:58:34.417 No theme dir: /home/dfinn/.mythtv/themes/Mythbuntu-8.04
2009-10-08 19:58:34.418 Switching to square mode (Mythbuntu-8.04)
2009-10-08 19:58:34.436 Using the Qt painter
mythtv: could not connect to socket
mythtv: Connection refused
2009-10-08 19:58:34.436 lirc_init failed for mythtv, see preceding messages
2009-10-08 19:58:34.437 JoystickMenuClient Error: Joystick disabled - Failed to read /home/dfinn/.mythtv/joystickmenurc

any help would be extremely appreciated

---

### Post by ohzopants on 2009-10-09
I have that same remote and it worked right out of the box for me.
Note that I use xbmc and not mythtv, but that shouldn't really matter.

---

### Post by dfinn on 2009-10-09
> **ohzopants said:**
> I have that same remote and it worked right out of the box for me.
Note that I use xbmc and not mythtv, but that shouldn't really matter.

Yeah, the reason I bought the remote is because everyone said it would work out of the box.  I'm currently doing a fresh install of 9.04 to see if it makes a difference.

---

### Post by dfinn on 2009-10-09
Well, this is really odd but I may have it figured out.  I'm using an older Shuttle XPC w/NVidia mother board.  It's got USB ports on the front and rear.  I'm using a Netgear MA111 for wireless for the moment.  I had been trying with both the IR receiver and the MA111 plugged into the 2 ports in the back.  I knew I had all my stuff configured right.  When I would get to the point where I had everything working and I started up the mythfrontend (also crashed several times just running irw) it would completely hang the box.  I moved the MA111 to the front ports (moving the IR receiver to the front didn't fix the problem) and it seems to have fixed it.  Remote works.  This was with 8.04.1 so now I'm doing an install of 9.04 to test on that.

---

