---
title: "rdesktop colour depth"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by thegrimgod on 2009-02-22
Hey guys,
I just installed Windows 7 Beta on a vmware machine - kind of my first time playing with both vmware on linux and rdesktop.
Anywhoo, the problem that I am getting is with the colour depth being reduced to 16 bit, which is ... ugly to say the least.
Here is the command that I run:

grim@noshelter:~$ rdesktop -u grim -a 24 -g 1024x768  grim-PC:3389
WARNING: Remote desktop does not support colour depth 24; falling back to 16

Now I tried to force 24 bit on both rdesktop, as you can see above, and the windows machine.
For windows, I went into the Local group policy editor in control panel, and in Computer Configuration>Windows Components>Termianl Services>Terminal Server>Remote Session Environment>Limit maximum colour depth, and enabled that to be 24 bit.
I would really prefer to test rdesktop with the correct colour depth, as the vmware console is pretty slow, and I plan to use the vmware machines for real work, after I play around with them a bit.
Any suggestions on why the colour depth is reduced?
I am not sure which part is at fault here, rdesktop, or windows. Any previous experience with other windows machines, with which rdesktop worked?
Thanks

---

### Post by thegrimgod on 2009-02-27
:(
Bum...

Well I did a read on the man pages:
       -a <bpp>
              Sets the colour depth for the connection (8, 15, 16 or  24).   More
              than  8 bpp are only supported when connecting to Windows XP (up to
              16 bpp) or newer.  Note that the colour depth may also  be  limited
              by  the server configuration. The default value is the depth of the
              root window.

Now as far as I can understand English, it seems that either only Windows XP allows up to 16 bits, all windows older >=xp allow a max of 16, or the man page is just confusing...

Even if there was a limit on the colour depth, 24 as far as I can see the upper limit being, why couldn't  I use more than 16 if both the server and the client support this.

I am confused :confused:

---

### Post by Cosimix on 2009-07-16
Use **tsclient** instead of rdesktop...
 
Follow these steps:
1. _Enable VRDP_ on Virtualbox
if the machine is already running in the background (VBoxHeadless), run:
**VBoxManage controlvm** *vmname* **vrdp on**
else if the VM is not running, enable VRDP on Virtualbox > Remote Display
to test it on the cli type "**telnet** *hostip* 3389" 
if you get connection Established you are ok else open TCP port 3389 on your firewall 
 
2. run tsclient (gui application)
Use protocol version 5 (RDPv5) and change color-depth to 24bit. 
**Note** When connecting use the server IP and not the VM's 
 
... MS is rubbish!

---

