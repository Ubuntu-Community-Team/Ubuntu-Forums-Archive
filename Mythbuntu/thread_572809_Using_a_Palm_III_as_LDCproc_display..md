---
title: "Using a Palm III as LDCproc display."
date: 2007-10-10
forum: Mythbuntu
---

### Post by mungewell on 2007-10-10
Brain dump of bits for others to play with.

Basical concept:
Palm III hardware to serial port running LCDproc client, powered from PC supply, hacked to ensure that the palm always turns on when PC powered (think shorting power switch will work).

Applications:
[http://palmorb.sourceforge.net/](http://palmorb.sourceforge.net/)
[http://www.palmbytes.coolfreepages.com/autoexec.html](http://www.palmbytes.coolfreepages.com/autoexec.html)
and/or 
[http://docwhat.gerf.org/code/powerbutton/](http://docwhat.gerf.org/code/powerbutton/)

Have fun,
Mungewell.

---

### Post by laga on 2007-10-10
Thx.

---

### Post by laga on 2007-10-14
I tried this the other day - it worked, but not very well. I could see the output of lcdproc and mythlcdserver, but I'd get some quare blocks in the output on my Palm M100. Have you ever seen this on yours?

---

### Post by mungewell on 2007-10-15
> **laga said:**
> but I'd get some quare blocks in the output on my Palm M100. Have you ever seen this on yours?

Yes, I also see the blocks. :-(

I think that the mythlcdserver is not as advanced as it could be, lots of problems with the screens not being updated when exiting a menus, etc. I believe that these issues are applicable to all LCDproc screens (saw the same thing with the ncurses 'display' as well).

Basically it is not really a suitable method of navigating through menus and selecting content.

My next plan is to use the VNC server, and use a palm vnc client to connect to that. Started experimenting and had some success with:
[http://palmvnc2.free.fr/](http://palmvnc2.free.fr/)

Needed to patch and rebuild VNC server to support server side scalling (to get mythtv menus to fit on such a small screen), but blew up my installation (filled the disk... and corrupted database on the test machine).

Intend to grab RC tonight and have a further play.
Munge.

---

### Post by mungewell on 2007-10-25
> **mungewell said:**
> 
Needed to patch and rebuild VNC server to support server side scalling 

Just a follow up to says it's never as easy as it seems. The patch was for an older version of VNC (3. something), whilst the VNC built into X (vnc4server) has moved on quite a bit wrt to the code. I'll take a better man than me to merge this in.....

There is an older version of VNC in the ubuntu repo's but this isn't as 'clean' as vnc4.


On the up side, the palm end does work (albeit without server side scaling). Just a note to other that might try I have had most luck running the serial link at 38400, any higher than that and the vnc client gets stuck when transfering data.

You need to config PPP settings...
/etc/ppp/peers/palm
---
/dev/ttyACM0 38400 cdtrcts
connect '/usr/sbin/chat -v -f /etc/ppp/palm.chat'
noauth
nodetach
debug
local
192.168.55.101:192.168.55.100
---

and
/etc/ppp/palm.chat
---
TIMEOUT 3600
---

Under the palm's settings configure the network to use a 'direct connection' @38400 and set (any) username/password with automatic IP.

Start the Linux machine listening with the command 'sudo pppd call palm' and do a 'connect' on the palm. Then start palmvnc and connect to '192.168.55.101' (the linux machine).

I am experimenting with changing the vnc4server parameters using 'vncconfig -set <param>'.

Have fun,
Simon.

---

### Post by mungewell on 2009-09-10
For some strange reason (perhaps the alignment of the planents) I found myself playing with this again last night.

Here is a proceedure for downloading code to a fresh/clean Palm m100, using the reset and hotsync buttons and pilot-xfer app.

1) Power device (asks for calibration...) and hit reset switch (is then happy in 'app' screen).
2) Hit sync button and upload PalmOrb prc
3) Hit sync button and upload AutoExec prc
4) Hit sync button and upload AlwaysOn prc
5) Hit sync button and upload XhackMaster prc
6) Hit sync button and upload xhackMaster pdb
7) Hit sync button and upload Saved Preferences' prc
8) Hit sync button and upload psysLaunchDB.PDB (at which point the Palm requests a reset)
9) Hit reset button (or onscreen request)

The palm will soft reboot, and using the settings in the last two files start running the PalmOrb application. You will need to configure the Palm to do so, and then backup these files first.

At this point you can start the LCDproc server and start sending data.

I am looking into ways to automate the triggering of sync and reset so that no human intervention is required.

Mungewell.

---

### Post by mungewell on 2009-09-11
I have worked out why the display is 'blocky'.

There are two commands which LCDd sends that PalmOrb does not like:
0xFE, 0x99, 0xFF - Set Brightness (for LKD)
0xFE, 0x59, 0x03 - Set Brighthess (for VFD)

It'll work great if the following section of MtxOrb.c is commented out.
--
#if 0 //SDW
        if (IS_VKD_DISPLAY) {
                unsigned char out[5] = { '\xFE', '\x89', 0 };

                /* map range [0, 1000] -> [0, 3] that the hardware understands */
                out[2] = (unsigned char) ((long) promille * 3 / 1000);

                write(p->fd, out, 3);
        }
        else {
                unsigned char out[5] = { '\xFE', '\x99', 0 };

                /* map range [0, 1000] -> [0, 255] that the hardware understands */
                out[2] = (unsigned char) ((long) promille * 255 / 1000);

                write(p->fd, out, 3);
        }
#endif
--

Mungewell.

---

