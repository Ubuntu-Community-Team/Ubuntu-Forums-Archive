---
title: "Help with patching DSDT/fixing ACPI"
date: 2009-04-26
forum: Multimedia Software
---

### Post by Scooter7 on 2009-04-26
Hi,

I have a Toshiba Satellite Pro P100 laptop, Intel High Definition Audio (Conexant Waikiki).   Without using acpi=off in my kernel line in my /boot/grub/menu.lst, I have no sound.   After doing some research, I've found that I need to patch my DSDT, but I can't find an already-patched file to download, and when trying to compile my own (as per this guide: [http://web.archive.org/web/20080125015702/http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://web.archive.org/web/20080125015702/http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)), I get this error:

```
(output of iasl -tc dsdt.dsl)

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  6138:             Method (BTST, 0, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (BTST)

dsdt.dsl  6165:             Name (_HID, "*PNP0C14")
Error    4001 -                                  ^ String must be entirely alphanumeric (*PNP0C14)

ASL Input:  dsdt.dsl - 6341 lines, 219079 bytes, 2298 keywords
Compilation complete. 1 Errors, 1 Warnings, 0 Remarks, 821 Optimizations
```

I've done some searching, but I can't find a solution to the error.   I'm not /too/ worried about the warning, though (not sure if I need to eliminate all warnings and errors or not).

Any suggestions?   If anyone has a fixed DSDT for my laptop model, or got sound working some other way, I'd appreciate it.

---

### Post by 67GTA on 2009-05-02
Send me a copy of your dsdt.dsl file, and I will see if I can fix the errors.

EDIT: Send me an email through the forums and I will reply to it so you can get my home email. The forums won't let you send them directly to me.

---

### Post by Scooter7 on 2010-02-07
Wow, sorry, I completely forgot about this thread.   I stumbled across it while searching for a solution to my DSDT problem (almost a year later :P).

I did manage to fix the error - I removed the '*' before 'PNP0C14' - but the warning has me stumped.   Any chance you could still help?

---

### Post by 67GTA on 2010-02-07
Remove the quotations also. It should only be 

```
Name (_HID, PNP0C14)
```

---

### Post by Scooter7 on 2010-02-07
Okay, I've done that, now I have a new error, and warning.

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/vertimyst/dsdt.dsl  6138:             Method (BTST, 0, NotSerialized)
Warning  1087 -   Not all control paths return a value ^  (BTST)

/home/vertimyst/dsdt.dsl  6165:             Name (_HID, PNP0C14)
Error    4095 -   syntax error, unexpected PARSEOP_NAMESEG ^

ASL Input:  /home/vertimyst/dsdt.dsl - 6341 lines, 219076 bytes, 2298 keywords
Compilation complete. 1 Errors, 1 Warnings, 0 Remarks, 821 Optimizations
```

---

### Post by 67GTA on 2010-02-07
It's hard to say from here. If you want to send me a fresh copy, I can fix it again.

---

### Post by Scooter7 on 2010-02-07
Okay.   I've sent you an email via the forum.

---

### Post by Scooter7 on 2010-02-07
Edit: I read this in your howto thread ([http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)):

'UPDATE: The kernel dev's will no longer use the patch to enable custom DSDT files for Karmic 9.10 and beyond. Jaunty 9.04 is the last version this will work on. You are urged to file a bug report for DSDT errors.'

Does this mean doing this won't possibly fix my ACPI-related issues?   I'm currently running Kubuntu 9.10.

-----------

I've been playing with it to see if I can fix it myself, and after making some changes, it compiled without errors, but I'm not sure if that means it's 100% working.

These are my original errors/warnings:

```
dsdt.dsl  6138:             Method (BTST, 0, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (BTST)

dsdt.dsl  6165:             Name (_HID, "*PNP0C14")
Error    4001 -                                  ^ String must be entirely alphanumeric (*PNP0C14)

```

For the warning, I added 'Return (Zero)' at the end of the method (sorry if my terminology is wrong - I'm still new to programming), like so:

Original:
```
Method (BTST, 0, NotSerialized)
            {
                If (\_SB.ECOK)
                {
                    Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
                    Store (\_SB.PCI0.LPCB.EC0.KSWH, Local0)
                    XOr (Local0, 0x01, Local0)
                    Store (\_SB.PCI0.LPCB.EC0.BTHE, Local7)
                    Release (\_SB.PCI0.LPCB.EC0.MUT1)
                    If (Local0)
                    {
                        ShiftLeft (Local7, 0x06, Local6)
                        ShiftLeft (Local7, 0x07, Local7)
                        Or (Local7, Local6, Local1)
                        Or (Local0, Local1, Local2)
                        Return (Local2)
                    }
                    Else
                    {
                        Return (Zero)
                    }
                }
            }

```

New code: (addition highlighted in bold)
```

Method (BTST, 0, NotSerialized)
            {
                If (\_SB.ECOK)
                {
                    Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
                    Store (\_SB.PCI0.LPCB.EC0.KSWH, Local0)
                    XOr (Local0, 0x01, Local0)
                    Store (\_SB.PCI0.LPCB.EC0.BTHE, Local7)
                    Release (\_SB.PCI0.LPCB.EC0.MUT1)
                    If (Local0)
                    {
                        ShiftLeft (Local7, 0x06, Local6)
                        ShiftLeft (Local7, 0x07, Local7)
                        Or (Local7, Local6, Local1)
                        Or (Local0, Local1, Local2)
                        Return (Local2)
                    }
                    Else
                    {
                        Return (Zero)
                    }
                }
		
		**Return (Zero)**
            }

```

For the error, I added a '*' to 'Name (_HID, "PNP0C14")'.   I know you said to remove the quotations, but doing so produces more errors.   The way it is now, I get no errors or warnings.   Should I proceed to compile it into my kernel?

---

### Post by 67GTA on 2010-02-08
The how to I wrote no longer works. You have to enable dsdt override in the kernel options, and include this patch [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml) and then recompile the kernel. This is the only way to use custom dsdt in 9.10 and beyond. Opensuse is the only distro that still supports custom dsdt with recompiling your own kernel, which is where I'm at now. Having said that, I am an idiot. I fixed your dsdt and sent it to the wrong person. I was working on two at once, and got them mixed up. I had yours with zero errors, but deleted it after mailing. Please send it again:oops:

---

### Post by Scooter7 on 2010-02-08
[quote="67GTA"]Having said that, I am an idiot. I fixed your dsdt and sent it to the wrong person. I was working on two at once, and got them mixed up. I had yours with zero errors, but deleted it after mailing. Please send it again:oops:[/quote]

Sure, no problem.   Sounds like something I would do. :P

Also, I know I said I was running Kubuntu 9.10, but now I'm running Mandriva 2010. :P   I'm trying out various KDE distros to see which I like the best.   I've previously used OpenSUSE, but not since 11.0.   Are you using KDE?   If so, how is it?   I may install that and try it.

Edit: Decided to install OpenSUSE.   I know it's not really relavant to this thread, but figured I should update anyway.

---

### Post by 67GTA on 2010-02-08
Kubuntu was always too buggy for me, and I don't like Gnome. I was always grudgingly using Ubuntu between the KDE3 to KDE4 transition. I bounced back and forth between Ubuntu and Opensuse for a while. I loved Opensuse once I got used to the package management differences. 11.2 was the first version to make me start using KDE again. It is awesome in my opinion. I recommend the DVD install over the CD. You can actually choose individual packages from the DVD to remove/install during installation, plus set up all of your hardware yourself if you uncheck the automatic config option at the start. You can also add repos from the web during install to pick packages from. Yast is really nice once you get used to it. It has every tool you can imagine. The biggest pet peeve for me is the package manager is set to refresh the repos every time you open it. This is very annoying, but can be turned off easily. I would suggest playing with a live CD, and lurking around on their forums. I will never look back. I will try to get your dsdt back tomorrow.

---

