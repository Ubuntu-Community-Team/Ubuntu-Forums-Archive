---
title: "Hardy 8.04, ATI/AMD 3870 keeps crashing (fglrx)"
date: 2008-05-10
forum: Multimedia Software
---

### Post by whocarez on 2008-05-10
I am experiencing some issues vith radeon 3870 in Ubuntu 8.04 Hardy. This is the 32-bit version of ubuntu. I have enabled the fglrx driver from the repositories, currently it's version 8.3. This driver works very well.. when it works.

Relevant hardware:
ASUS M2N-SLI Deluxe motherboard, bios 1203
AMD 4400+ cpu
2GB memory

From time to time I experience that X crashes. A very common example (although not always reproducable) is if I have Firefox running on one desktop, then I am on another desktop and click on the switcher icon to change to Firefox. I quickly see a mosaic pattern on screen, and the screen goes black. And that is totally black, not possible to switch to a console either, black screen there too. I can still ssh into the computer, it is just impossible to get X working without a reboot. There is not much to get from the logs, at the end of /var/log/Xorg.0.log it just says:

```

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7fa6420]
2: /usr/lib/xorg/modules//libxaa.so [0xb76605b9]
3: /usr/bin/X [0x8172fa3]
4: /usr/bin/X(CompositePicture+0x150) [0x815a1c0]
5: /usr/bin/X [0x816019f]
6: /usr/bin/X [0x815d055]
7: /usr/bin/X [0x81506de]
8: /usr/bin/X(Dispatch+0x2cf) [0x808d8df]
9: /usr/bin/X(main+0x48b) [0x807471b]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d3e450]
11: /usr/bin/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting

(II) AIGLX: Suspending AIGLX clients for VT switch

```

Same thing happens if I try to restart GDM, I just get a black screen on all consoles and have to ssh in and reboot. I have also tried the plain radeon driver, this one just gives me black VT consoles but does not crash. The vesa driver kind of works, but the colors seem messed up and is quite blurry. Switching to console works though. The crashes with fglrx also occur if I disable all desktop effects.

I suspect the black VT consoles might be related to the frame buffer? I am considering making a new initrd without frame buffer.

I might try the 8.4 driver, but right now I am not sure if it will solve anything. The last way out would probably be to try the open source radeonhd driver, although I will not get any 3D support.

I am open for any suggestions how to solve this :(

---

### Post by whocarez on 2008-05-12
Just to be more precise, the error message above is logged when a crash occurs. I see a mosaic pattern, and get thrown out to a console. I have looked a bit more into the issue, and the system runs a lot more stable if I turn off "Visual Effects". I am considering to disable the Compiz extension permanently in xorg.conf.

I have no idea why restarting GDM just gives me a black screen on all consoles though, but I guess it is driver related too. I am going to try the latest driver (8.4) today.

---

### Post by whocarez on 2008-05-12
I just installed the latest ATI-driver (8.4), and at least for now on the system seems a lot more stable, even with "Visual Effects" enabled. Right now I have not experienced a single crash for a couple of hours. I can switch back and forth to a VT console without problems. Killing the X-server with ctrl+alt+backspace also works, at least for now.

I noticed a couple of articles in the AMD/ATI knowledge base:
[http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=30687](http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=30687)
[http://support.ati.com/ics/support/KBAnswer.asp?questionID=26945](http://support.ati.com/ics/support/KBAnswer.asp?questionID=26945)

Although both articles do not mention my card, it is very similar to what I experienced.

One issue remains, it is still impossible to restart GDM, it still results in black consoles (gdm/X hangs). I can probly live with that for now.

---

### Post by JacobSingh on 2008-06-29
I get a similar problem, but seems to happen more often with compiz (not sure if metacity does it at all).

The difference is, when mine goes down, it doesn't go blank, X just dies and I can see system messages.  Music will keep playing and all my apps are still there, just can't see / use them :)

I can switch to a different term, but if I restart gdm, I experience the same lockup.  My log message is the same as yours.

Here is the gfx card:
lspci | VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5200]

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY FireGL V5200
OpenGL version string: 2.1.7412 FireGL Release


Best,
Jacob Singh

---

### Post by danf_1979 on 2008-08-21
> **JacobSingh said:**
> I get a similar problem, but seems to happen more often with compiz (not sure if metacity does it at all).

The difference is, when mine goes down, it doesn't go blank, X just dies and I can see system messages.  Music will keep playing and all my apps are still there, just can't see / use them :)

I can switch to a different term, but if I restart gdm, I experience the same lockup.  My log message is the same as yours.

Here is the gfx card:
lspci | VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5200]

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY FireGL V5200
OpenGL version string: 2.1.7412 FireGL Release


Best,
Jacob Singh

Hi!

I have the exact same problem as Jacob with 8.04 + compiz + ATI x1400 + fglrx drivers from repos. X crashes, but when checking ps -A, all my apps are still there.

Is there any fix?

Log:

```

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7f88420]
2: /usr/lib/xorg/modules//libxaa.so [0xb76375b9]
3: /usr/bin/X [0x8173013]
4: /usr/bin/X(CompositePicture+0x150) [0x815a1f0]
5: /usr/bin/X [0x81601df]
6: /usr/bin/X [0x815d085]
7: /usr/bin/X [0x81506ee]
8: /usr/bin/X(Dispatch+0x2cf) [0x808d8df]
9: /usr/bin/X(main+0x48b) [0x807471b]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d1d450]
11: /usr/bin/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting

(II) AIGLX: Suspending AIGLX clients for VT switch

```

---

