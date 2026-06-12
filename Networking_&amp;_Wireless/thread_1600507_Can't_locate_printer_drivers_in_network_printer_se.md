---
title: "Can't locate printer drivers in network printer setup"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by darkmire on 2010-10-19
I am trying to set up a Samsung clx2160N as a standalone network printer on my home network. It is a printer with standalone network capability and is connected directly to my router and has a static IP number.  We have a few Windows computers at home and they had no problem detecting the printer, installing the drivers and working.  Unfortunately my Ubuntu computer recognises the printer and I can even access it's setup and diagnositcs through its IP number.   However when I try to add it as a printer, drivers for it cannot be located.  

I#ve tried setting it up three ways:

1.  Using Samsung's own setup package - finds printer and all the details it needs to work but offers no drivers
2.  Using Ubuntu's printer setup - recognises printer but stalls at Searching for Drivers dialog
3.  Trying to *** printer using CUPS - no problem finding and recognising printer, but when I come to search for the driver I get Internal Server Error.

I have of course been trying to do all of these as root.  That's the limit of my knowledge reached and searches on the net aren't helping me either.  The printer works fine directly connected via USB, so the drivers are on the computer somewhere.  How do I get them set up to use the printer on the network?

Using Ubuntu 10.04

---

### Post by chili555 on 2010-10-19
Perhaps these links will assist you:

[http://www.openprinting.org/printer/Samsung/Samsung-CLX-2160](http://www.openprinting.org/printer/Samsung/Samsung-CLX-2160)

[http://foo2qpdl.rkkda.com/](http://foo2qpdl.rkkda.com/)

Especially see:> *** DON'T USE the foo2zjs package from:
         ***Ubuntu***, SUSE, Mandrake/Manrivia, Debian, RedHat, Fedora, Gentoo, Xandros, EEE PC, Linpus, MacOSX, or BSD!
*** Download it here and follow the directions below. I don't have this device, so I am not sure I can help very much if you get stuck.

---

### Post by darkmire on 2010-10-19
Thanks for that info.  As far as I can see from the CUPS error log, CUPS is trying to look for the drivers in a directory that isn't there.  I haven't yet worked out how to get CUPS to look in the directory that has the drivers.

In the end, I made a copy of the entry for the Samsung CLX-2160N, went into Properties on the copy that I made and changed the URI from USB to the address of the network printer and it works fine - now why didn't I think of that in the first place?  :)

---

### Post by chili555 on 2010-10-19
Glad it's working! Have fun and enjoy Ubuntu.

---

