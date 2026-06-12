---
title: "MCEUSB receiver not working on 14.04"
date: 2015-05-02
forum: Mythbuntu
---

### Post by Marc_Aronson on 2015-05-02
Clean install of 14.04 with new hardware. MCEUSB receiver that worked on a different machine running 12.04 / LIRC isn't working on the new machine with LIRC.

I read [this article]("http://pdxpastimes.blogspot.com/2014/11/howto-get-mce-usb-remote-working-in.html") about using ir-keyboard. I can get some responses from ir-keyboard, but nothing consistent. 

Here is the result of running "***sudo ir-keyboard***" 
```
Found /sys/class/rc/rc0/ (/dev/input/event6) with:        Driver mceusb, table rc-rc6-mce
        Supported protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC other
        Enabled protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC other
        Name: Media Center Ed. eHome Infrared
        bus: 3, vendor/product: 1784:0008, version: 0x0101
        Repeat delay = 500 ms, repeat period = 125 ms
aronson@myth-zbox:~$

```

Here is the result of hitting the "5" key on the remote over and mover while running [I][B]sudo ir-keyboard -t
[/B][/I]```
1430606767.521279: event type EV_MSC(0x04): scancode = 0x800f8401430606767.521279: event type EV_SYN(0x00).
1430606767.905231: event type EV_MSC(0x04): scancode = 0x800f040
1430606767.905231: event type EV_SYN(0x00).
1430606769.217121: event type EV_MSC(0x04): scancode = 0x400
1430606769.217121: event type EV_SYN(0x00).
1430606769.313111: event type EV_MSC(0x04): scancode = 0x100
1430606769.313111: event type EV_SYN(0x00).
1430606769.633082: event type EV_MSC(0x04): scancode = 0x400
1430606769.633082: event type EV_SYN(0x00).
1430606769.857023: event type EV_MSC(0x04): scancode = 0x2003c1
1430606769.857023: event type EV_SYN(0x00).
1430606770.145004: event type EV_MSC(0x04): scancode = 0x4007
1430606770.145004: event type EV_SYN(0x00).
1430606770.528947: event type EV_MSC(0x04): scancode = 0x4007
1430606770.528947: event type EV_SYN(0x00).
1430606770.912912: event type EV_MSC(0x04): scancode = 0x400
1430606770.912912: event type EV_SYN(0x00).
1430606771.008930: event type EV_MSC(0x04): scancode = 0x1f3f
1430606771.008930: event type EV_SYN(0x00).
1430606771.136867: event type EV_MSC(0x04): scancode = 0x1001f08
1430606771.136867: event type EV_SYN(0x00).
1430606771.328871: event type EV_MSC(0x04): scancode = 0x400
1430606771.328871: event type EV_SYN(0x00).
1430606771.552831: event type EV_MSC(0x04): scancode = 0x2003c
1430606771.552831: event type EV_SYN(0x00).
1430606777.376196: event type EV_MSC(0x04): scancode = 0x4007
1430606777.376196: event type EV_SYN(0x00).
1430606777.984143: event type EV_MSC(0x04): scancode = 0x400
1430606777.984143: event type EV_SYN(0x00).
1430606778.208083: event type EV_MSC(0x04): scancode = 0x2003c1
1430606778.208083: event type EV_SYN(0x00).
1430606780.287867: event type EV_MSC(0x04): scancode = 0x400
1430606780.287867: event type EV_SYN(0x00).
1430606781.183760: event type EV_MSC(0x04): scancode = 0x2003c10
1430606781.183760: event type EV_SYN(0x00).
1430606782.463647: event type EV_MSC(0x04): scancode = 0x4007
1430606782.463647: event type EV_SYN(0x00).

```

Notice how the scancode's are not consistent. Notice also how the "*[FONT=Arial]event type EV_KEY[/FONT]*" lines are totally missing.

I have been digging and googeing for hours -- no success.

Any ideas?

My machine is a "[[COLOR=#111111][FONT=Arial]Zotac Mini PC Barebones System ZBOX-BI320-U[/FONT][/COLOR]]("http://www.amazon.com/Zotac-Mini-Barebones-System-ZBOX-BI320-U/dp/B00LJEFR68/ref=sr_1_4?s=pc&ie=UTF8&qid=1430606957&sr=1-4&keywords=mini+pc")" 

Finally, as you can see below, I did stop the LIRC service before running this test
```
aronson@myth-zbox:~$ ps auxw | grep lirc
aronson  21875  0.0  0.0  10468  2232 pts/2    S+   15:51   0:00 grep --color=auto lirc

```

Any help would be greatly appreciated!

Marc

---

### Post by Marc_Aronson on 2015-05-23
I swapped to a different MCEUSB IR receiver and things are working now. 

The one that didn't work would show the following in kern.log when plugged into the USB port:
> Registered Topseed Technology Corp. eHome Infrared Transceiver with mce emulator interface version 1

My new MCEUSB IR reciver that works shows the following in kern.log when plugged into the USB port:
> Registered Formosa21 eHome Infrared Transceiver with mce emulator interface version 2


So the conclusion is -- some of the MCEUSB receivers work on this new setup; some don't.

It's worth noting that both of these receivers work on Mythbuntu 12.04 with my old hardware.

Based on everything I've read the issue is probably not the mythbuntu version (12.04 vs. 1404), but instead, the chipset in the new device. Having said this, I have not run the experiments to prove this conclusively.

Posting this in case it helps someone else.

Marc

---

### Post by jerrymr on 2015-06-28
Just to add a little more info in case it helps anyone, I recently ran into this exact problem/symptoms.  I am using a Topseed receiver with a v1 interface which I migrated to new frontend hardware (Liva ECS), and I ended up with the choppy scancodes.  The receiver worked fine on my old 12.04 box, but did not work on the new box with 14.04.  It also did not work with 15.04.

I tried installing a beta Windows 10 on the Liva and that was able to talk to the receiver ok.  So it's a software problem, or at least solvable with software.  This post, [http://ubuntuforums.org/showthread.php?t=2203116](http://ubuntuforums.org/showthread.php?t=2203116), talks about driver issues and/or xHCI/USB 3.0 issues, and has a patch for the mceusb driver.  But the 3.16 kernel that comes with 14.04 already has the patch integrated.

I was ultimately not able to find a fix for this.  If you have a bios that allows you to disable xHCI (mine doesn't) that would be something to try.

-Jerry

---

### Post by Marc_Aronson on 2015-07-17
> **jerrymr said:**
>  If you have a bios that allows you to disable xHCI (mine doesn't) that would be something to try.

My BIOS has that option and I tried it before replacing it with a different version IR receiver.It did not solve the problem...

Based on everything I've read and tried, I suspect there are multiple root-causes for the same symptoms. The fix that works for any individual will vary based on which root-cause(s) are causing the problem for that person's setup...

Marc

---

### Post by Mythological on 2015-08-12
Check to make sure that Ubuntu isn't seeing TWO IR receivers, even if you only have one.  That bit me with a newer Acer Revo, and I found the solution here:

[If your MCE compatible remote stopped working in Ubuntu 14.04 or another newer release of Linux, check for this weird problem!]("http://tech.iprock.com/?p=13210")

---

