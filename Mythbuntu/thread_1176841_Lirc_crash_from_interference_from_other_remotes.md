---
title: "Lirc crash from interference from other remotes?"
date: 2009-06-02
forum: Mythbuntu
---

### Post by Chunder on 2009-06-02
Hi all - I'm at a bit of a loss with this one, I'm afraid.
I'm still a bit of a newbie, but I have learned a lot about Linux (and Ubuntu in particular) during my setup of a Mythbuntu system - and almost every solution that worked came from here... so I'm really hopeful that some kind soul can help point me in the right direction. Apologies in advance for all the writing!

I have an Antec Fusion HTPC case (15c2:ffdc - version 2 with the IR and VFD, not LCD) on which 8.10 amd_64 is running happily; I have got lirc (0.8.3-0ubuntu2) installed and running using the built in IR-receiver, controlled by a Logitech Harmony One universal remote - a great gadget, but a pain to get set up initially!

The VFD works OK when booted from (complete, disconnect from wall) cold, but periodically crashes out and displays garbage. I was more interested in getting the remote working, so I disabled the LCDd from running thinking that I would be OK.

Unfortunately, I'm experiencing problems with lirc crashing out, and I wonder whether it is related to the VFD issue.

I've done a bunch of research, and have found people with similar symptoms as I'm experiencing, but have yet to find a solution. One reference on the Codeka forums suggest recompiling lirc_imon with a different refresh_frequency option, but then other responses have stated that this doesn't fix the problem.

I now think that I've tracked down the cause of the problem, but I'm having trouble proving it one way or another, and this is where I could do with some help.

The crash happens consistently when using the volume up/down on my AV receiver remote (Cambridge Audio Azur 640R) - something that the Antec IR shouldn't even be picking up.

If I've booted from cold, the VFD is blank and LCDd is not running. When I change volume (by _holding_ the button, not individual presses), garbage soon appears on the VFD, and lirc stops running with the following messages (the "callback" line is repeated many, many times!)

> [19689.206384] lirc_imon: usb_rx_callback: status(-32): ignored
[19689.214383] lirc_imon: usb_rx_callback: status(-32): ignored
[19689.222384] lirc_imon: usb_rx_callback: status(-32): ignored
[19689.230384] lirc_imon: usb_rx_callback: status(-32): ignored
[19689.238383] lirc_imon: usb_rx_callback: status(-32): ignored
[19689.246386] lirc_imon: usb_rx_callback: status(-32): ignored
[19689.254382] lirc_imon: usb_rx_callback: status(-32): ignored
[19689.262383] lirc_imon: usb_rx_callback: status(-32): ignored
[19689.270382] lirc_imon: usb_rx_callback: status(-32): ignored
[19689.276388] lirc_imon: IR port closed


Pretty much the same message - save the reference stamp and the formatting - is shown in dmesg, kern.log, and syslog.

/dev/lirc0 is still present (although trying to cat the output to the screen doesn't do anything when a button is pressed), and according to ps, lircd is still running. There is also no sign of life using irw, irrecord or mode2, and restarting lircd doesn't do anything.

Previously I thought that there was no alternative but reboot, in which case everything (bar the VFD display) comes back as normal. I have since discovered that I can rmmod lirc_imon, and then immediately modprobe it back in again, and mode2 (and everything else) recognises the remote.

I have tried to see if I can capture the mystery signal that's causing the problem, but neither mode2 nor irrecord show up any response, even if the latter is forced into raw mode. If the crash happens whilst irrecord is doing its stuff, then the process becomes completely unresponsive - and nothing beyond a reboot seems to be able to kill off irrecord.


Can anyone suggest any other logfiles that may help with a more useful message? Are there other programs that can just record the raw data stream from the IR receiver so that I can see what's triggering the problem?
In my naive world, it looks like a buffer overflow that's overwriting part of the VFD display memory area, and trashing the IR receiver - but then again, it could probably be almost anything.

It was starting to seem like I was getting quite proficient at finding problems, and then solving them (with help from the net, naturally) - but this one has used up every last drop of my ability... so I really hope that there is someone out there with the stamina to have read all this, the willpower to get involved, and the ability to help me track down a solution (or enough information to submit a bug report :D ).

Cheers,

Mark P.

---

### Post by Sef on 2009-06-04
Moved to Mythbuntu per op request.

---

### Post by ian dobson on 2009-06-04
Hi,

I've got a strange feeling the the problem is with the IR receiver/on board controller. If the VFD starts displaying crap without loading the driver then there's a good chance that it's the controller.

When you reload the lirc_imon driver the IR controller is then reinitalised and the disply works again.

I know this doesn't help much but keep on looking/trying.

Regards
Ian Dobson

---

### Post by Chunder on 2009-06-04
Ahhh - that's a good point; I'm not disabling the VFD by stopping the daemon, I'm just stopping any software writing to it. The driver for the VFD is integrated into lirc_imon with the IR driver. Doh.

Maybe my best bet would be to research finding (or compiling) a version of the IR driver that doesn't include the VFD stuff, and then see if I still have the same problem.

Hmm... sounds like a challenge *cracks fingers*

---

### Post by ian dobson on 2009-06-04
Hi,

If your motherboard has a serial port, why not pickup a cheap IR receiver (ebay 5-10Euro).

Regards
Ian Dobson

---

### Post by SiHa on 2009-06-05
Or if you're up to a bit of soldering, you could make a homebrew serial receiver yourself. I use them on both my machines, and have never had any problems.

---

