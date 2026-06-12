---
title: "Problems with remote control after upgrade to 14.04"
date: 2014-09-23
forum: Mythbuntu
---

### Post by Adam_Jacobs on 2014-09-23
I have just installed a new Ubuntu 14.04 plus MythTV 0.27 system.

I have a Soundgraph iMON PAD remote control. It used to work just fine on my old 10.04 system, but now it only partially works.

It clearly can communicate with the PC somehow, as some of the buttons have the expected behaviours. Specifically, the trackpad in the middle moves things up, down, left, or right as expected, the enter button selects things, and the escape button escapes from things. As far as I can tell, they are the only buttons that work. Nothing else does anything.

I saw that in the Mythbuntu control centre I had not enabled LIRC support. So presumably these buttons were somehow recognised natively, without using LIRC. Does that sound right?

So I enabled LIRC in the Mythbuntu control centre. This made absolutely no difference to the behaviour of my remote control.

I have noticed that if I try to start LIRC manually with 

```
 sudo service lirc start
```

I get the following error message:

```
 * Loading LIRC modules                                                  [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```
So presumably this means that LIRC is not even starting in the first place, right?

This is what my /etc/lirc/hardware.conf file looks like:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Soundgraph iMON PAD IR/VFD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="imon/lircd.conf.imon-pad"
REMOTE_LIRCD_ARGS=""


#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""


#Disable kernel support.
#Typically, lirc will disable in-kernel support for ir devices in order to
#handle them internally.  Set to false to prevent lirc from disabling this
#in-kernel support. 
#DISABLE_KERNEL_SUPPORT="true"


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
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""
```

I suppose in theory there are 2 ways to fix this. If MythTV can recognise my remote control natively without the need for LIRC, is it possible to somehow get it to recognise the other keys on my remote without using LIRC? Or alternatively, can anyone suggest what's wrong with my /etc/lirc/hardware.conf file and how I might get LIRC working?

Would be perfectly happy with either of those if it gets the remote fully working.

Many thanks
Adam

---

### Post by Adam_Jacobs on 2014-09-27
OK, I'm making some progress here, but not much.

A little bit of Googling suggested that maybe the line in my [COLOR=#000000]/etc/lirc/hardware.conf file that said:

```
LOAD_MODULES="true"
```

was the problem. So I changed it to false, and now LIRC will at least start.

However, the behaviour of my remote control is still exactly the same as it was before. Only a few keys are recognised.

I have tried to find out what signals are being sent to the PC when I press keys on the remote, using irw and mode2. I thought that mode2 was supposed to give lower-level responses, but I got identical output from both of them. In each case, only the keys that I know to be working gave any output at all. What came up on the screen was stuff like ^[[C (when I move the trackpad left, for example).

Is there any way I can get the PC to tell me what it's receiving when I press a button on the remote? If I know that, then I can figure out if the key mapping is all wrong and that's what's causing my problems.

Or am I going about this in completely the wrong way?

Any help gratefully appreciated![/COLOR]

---

### Post by khPWXxF on 2014-09-29
[FONT=Courier New][SIZE=3][COLOR=#000000]Isn't the next step in the chain to look in /etc/lirc/lircd.conf and the 'include' file(s) in there?
The include files tell LIRC how to interpret the IR pulses.
In my case, the files were generated automatically with mythbuntu control centre. They gave good functionality but have subsequently been tuned.
hth
[/COLOR][/SIZE]Phil

[/FONT]

---

### Post by Adam_Jacobs on 2014-10-04
Thanks Phil. If I go to that lircd.conf file, there is a single include file which is /usr/share/lirc/remotes/imon/lircd.conf.imon-pad

That seems entirely reasonable to me. My device is indeed an Imon Pad, so it certainly sounds like the right file. It maps the names of various keys to various codes. So, for example, a few lines from the file look like this:

```
          KEY_PAUSE                0x2A9115B7
          KEY_FASTFORWARD          0x2B8115B7
          KEY_PREVIOUS             0x2B9115B7
          KEY_STOP                 0x2B9715B7
          KEY_NEXT                 0x298195B7
          KEY_ESC                  0x2BB715B7
          Eject                    0x299395B7




```

Now, if I could somehow tell what code was being sent when I press the pause button on my remote, I could see if it is indeed 0x2A9115B7 as my config file seems to think it should be, and if it's not, then I guess that's the problem and I can tweak the file accordingly.

However, I'm not sure how to do that. I thought that's what mode2 was supposed to do, but I guess I must have misunderstood. Does anyone know how I can tell what codes are being sent when I press a button on the remote?

Thanks
Adam

---

### Post by khPWXxF on 2014-10-05
Hi Adam
Try this.
Exit frontend.  Start terminal session.   irw  and press buttons.

Hth.  Phil

---

### Post by Adam_Jacobs on 2014-10-05
I've already tried irw. I get the same results as if I try mode2. In other words, I get nothing for some buttons, but for the buttons that already work, I get things like [COLOR=#000000]^[[C appearing on the screen. I don't get anything looking like [/COLOR][COLOR=#000000]0x2A9115B7.

I'm guessing that something fairly basic is really not set up correctly, but unfortunately I have no idea what it could be.[/COLOR]

---

### Post by Adam_Jacobs on 2014-10-12
OK, I've been doing a little more investigation here. Still totally stumped, but I have a bit of extra information now which I hope might give someone smarter than me a clue about what is going on.

As stated previously, only a limited number of buttons on my remote control seem to have any effect, either on the frontend or when I'm using irw or mode2.

I have also noticed that the same buttons generate entries in the syslog when I press them. Other buttons don't generate any entries in the syslog.

A somewhat weird thing is that the entries are not generated constently: they vary each time. There is not just one entry per press, but several. The number of entries seems to vary from 3 to 8, but is usually 4. Here are a selection of entries from the syslog (separated by blank lines) from when I press the down button on the remote control's trackpad:

```
Oct 12 10:20:08 htpc kernel: [160939.821099] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
Oct 12 10:20:08 htpc kernel: [160939.869096] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x1000105
Oct 12 10:20:08 htpc kernel: [160939.925091] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x100040f
Oct 12 10:20:08 htpc kernel: [160940.005098] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x100020f
Oct 12 10:20:08 htpc kernel: [160940.045089] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x100010f
Oct 12 10:20:08 htpc kernel: [160940.085092] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x100020f
Oct 12 10:20:08 htpc kernel: [160940.125085] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x100050f
Oct 12 10:20:08 htpc kernel: [160940.165088] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x1000002



Oct 12 10:20:23 htpc kernel: [160955.405098] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x1000002
Oct 12 10:20:23 htpc kernel: [160955.445083] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x100060f
Oct 12 10:20:24 htpc kernel: [160955.525090] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x100060f
Oct 12 10:20:24 htpc kernel: [160955.605086] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x100060f
Oct 12 10:20:24 htpc kernel: [160955.645088] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x1000002



Oct 12 10:20:31 htpc kernel: [160963.133103] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x1000002
Oct 12 10:20:31 htpc kernel: [160963.173091] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x100060f
Oct 12 10:20:31 htpc kernel: [160963.253090] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x100050f


Oct 12 10:22:34 htpc kernel: [161086.317100] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
Oct 12 10:22:34 htpc kernel: [161086.429095] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x100050f
Oct 12 10:22:35 htpc kernel: [161086.509095] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x100060f
Oct 12 10:22:35 htpc kernel: [161086.549091] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x1000002



Oct 12 10:22:40 htpc kernel: [161091.965098] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x1000002
Oct 12 10:22:40 htpc kernel: [161092.005083] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x100050f
Oct 12 10:22:41 htpc kernel: [161092.085090] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x100060f
Oct 12 10:22:41 htpc kernel: [161092.165095] imon 4-4:1.0: imon_incoming_packet: unknown keypress, code 0x100050f
```

So far, so baffling.

But here is another really weird thing. If I press the volume up or down controls on my remote, it creates no entry in the syslog, has no effect on irw or mode2, and has no effect on MythTV frontend. However, if I am out of MythTV and on the Unity desktop, then pressing the volume controls does seem to control the normal Ubuntu volume.

I am completely stumped by all this. If anyone can give me any clue about how I might go about getting my remote control to work, I would be very grateful.

Thanks
Adam

---

### Post by Ulrich_Eckhardt on 2014-10-21
What is the exact USB id of the iMon remote? For the iMon 15c2:0034 used in my Thermaltake DH102 I have submitted several patches to the [linux media mailing]("http://www.spinics.net/lists/linux-media/msg74604.html") list to get the remote and especially the front panel buttons correctly working. This patch set is incorporated into the latest 3.18-rc1 kernel (but requires an other[ patch]("https://www.mail-archive.com/linux-media@vger.kernel.org/msg80499.html"), since the iMon is broken in 3.17.0) .

---

### Post by Adam_Jacobs on 2014-10-26
If I type lsusb at a terminal (is that what you meant by the USB id?) I get the following entry for the remote control:

Bus 004 Device 002: ID 15c2:0035 SoundGraph Inc.

---

### Post by Adam_Jacobs on 2014-11-02
Bump?

---

### Post by AlecJ on 2014-11-02
Are you on the latest fixes build?
[http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

---

### Post by alien878 on 2014-11-06
Some time ago, lirc was merged into the kernel.  An IR remote now works more like a keyboard, which is a good thing (IMHO).  Unfortunately, the change is not well documented.

It appears that the kernel driver config files are incomplete for your remote.

You have two options:

1.  Use ir-keymap to fix the keymappings.  Good places to start are [http://forum.xbmc.org/showthread.php?t=104541](http://forum.xbmc.org/showthread.php?t=104541)  and [http://forum.xbmc.org/showthread.php?t=101151](http://forum.xbmc.org/showthread.php?t=101151) 

2. Install the old lirc and modify the kernel lirc to pass events to it.  The old config files can then be used.  I didn't do this, but you can probably find instructions via google.

Cheers,

Allen

---

