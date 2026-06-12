---
title: "I need a 56k modem config"
date: 2005-12-14
forum: Networking &amp; Wireless
---

### Post by MrChips on 2005-12-14
I have a US robotics 5610 56k faxmodem w/ 3com chipset.  This modem is listed under compatible Linux modems and shows up in device manager as it's model and not a winmodem.  So...

Where do I go from here?  I still cannot get connected to the internet.  In device manager under linux.device_file it is listed dev/ttyS14.  In networking to configure the modem it only goes to dev/tty4.  

Is there someway to change this or is there something I'm missing?:confused:

---

### Post by az on 2005-12-14
You can type in the modem device by hand, without using the drop-down menu.


This is a bug, I guess.  I will check to see if it is filed and file it as neccessary.  If alsa sets up these kinds of modems as ttyS14, then Gnome should know to look there when you ask it to autodetect.

---

### Post by MrChips on 2005-12-14
[QUOTE=azz]You can type in the modem device by hand, without using the drop-down menu.[/QUOTE]

Actually I did install the modem AFTER I installed Ubuntu.  There was a winmodem there before which I found out did not work.  So being very new to this OS, I would like to know how to type the correction in by hand.  Much appreciated :)

---

### Post by az on 2005-12-14
System - Administration - Networking

See attached images:

---

### Post by MrChips on 2005-12-14
Ok that's great!
I typed in dev/ttyS14 and the modem is now working but still the browser is not loading pages.  The connection is there.  I can hear the # dialed, and the analog exchange just like normal.

But the browser doesn't seem to be using the connection.  I know must have another step to go through.  I just have no idea. :confused:

---

### Post by ubunlilluz on 2006-01-01
i have a similar problem: i can' connect, but if i call the automatic detection it sees a modem connected in the ttyS0 (that's ok).
When i try to active the connect i can hear that it tries to use the modem, but after a couple of beeps it drops without dialing the number.

---

