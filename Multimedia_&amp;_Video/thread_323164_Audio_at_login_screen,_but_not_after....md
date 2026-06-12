---
title: "Audio at login screen, but not after..."
date: 2006-12-21
forum: Multimedia &amp; Video
---

### Post by pjburgess on 2006-12-21
This is strange. I get what I can only describe as the "bongos" sound when the login screen appears ( on Ubuntu 6.10 after the latest update ), but then after I login the system refuses to acknowledge that a sound card is installed!

I get this error: "*The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.*"

Or this when i test the sound: "*audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.*"

Typing "lspci -v" yields the following:

**[snip]**
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Biostar Microtech Int'l Corp Unknown device f614
        Flags: bus master, medium devsel, latency 0, IRQ 201
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=64]
        Memory at fa081000 (32-bit, non-prefetchable) [size=512]
        Memory at fa082000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
**[/snip]**

when logged in as my normal user.

However, when I'm logged in as root i get the following instead of the <access denied> above:

**[snip]**
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Biostar Microtech Int'l Corp Unknown device f614
        Flags: bus master, medium devsel, latency 0, IRQ 201
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=64]
        Memory at fa081000 (32-bit, non-prefetchable) [size=512]
        Memory at fa082000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
**[/snip]**

which clearly shows that as root it can access the capabilities information.

This leads me to believe this is a permissions problem, but this is as far as my Linux skills will take me. I've read the super-duper guide to sound on Ubuntu but that yields no solutions.

Anyone got any ideas ??
Thanks.

---

### Post by pjburgess on 2006-12-21
Never mind. Solved it. It was a permissions issue.... i'd somehow removed myself from all groups except the one for my own name. Doh !!

Didn't realize that you needed to be a member of the Audio group to use the device(s).
Powerful and potentially useful security feature, but damn annoying when you accidentally fudge things up !! ](*,) 

How'd I know it was this ? Easy: I tried to access System -> Administration -> Users & Groups, when it told me i didn't have the permission ( that I had two days ago ) to access it. A quick look inside /etc/groups and hey-presto.

Paul.

---

