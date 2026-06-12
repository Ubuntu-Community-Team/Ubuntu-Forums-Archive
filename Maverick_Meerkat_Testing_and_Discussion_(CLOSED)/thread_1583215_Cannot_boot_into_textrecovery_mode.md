---
title: "Cannot boot into text/recovery mode"
date: 2010-09-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by abeowitz on 2010-09-27
Yesterday's updates seem to have broken my startup on amd64.

The system boots, then seems to set the console to a broken text mode resolution, preventing ctrl-alt-F1, etc.

Booting into single or recovery does exactly the same thing.  I see the login prompt, then it blacks out.

'nomodeset' doesn't work either.

So, what's doing this thing and how can I turn it off?

(Going to try and rescue image into the root and enable sshd...)

---

### Post by VMC on 2010-09-27
Lets start with what video card your using.

---

### Post by abeowitz on 2010-09-27
I've got an Nvidia 9800.  It's using the proprietary drivers through the Ubuntu packaging system...

I managed to boot the alt install CD into recovery mode and chrooted to the root fs.  Updated the packages and rebooted just fine...

Weird.

Still, linux 'single' should avoid fb, gdm, etc...

Not sure how this kernel is configured.

---

### Post by abeowitz on 2010-09-28
OK, problem booting today, no X.org...

I seem to have no console at all.  As soon as grub does its thing, I get a blank screen with an underline cursor, no blinking.

Shortly after, I get the Ubuntu 10.10 dot progress animation...

Then I get the blank console, and eventually GDM,... sometimes.

I got GDM back by SSHing in and apt-get upgrading, then rebooting.

-=-=-

Even after successful GDM login to Gnome, if I hit Ctrl-Alt-F1..9, I get the broken console.

It seems the kernel is going into an invalid console mode, yet 'nomodeset' doesn't seem to have an effect...

---

### Post by VMC on 2010-09-28
What does the ".xsession-errors" say? Anything of value.

---

### Post by abeowitz on 2010-09-28
.xsession-errors has a bunch of stuff, but nothing related, I think.

In order for .xsession-errors to have related errors, I'd have to be able to login, no?  hmmm...

This problem occurs before GDM even starts.

1)  POST
2)  GRUB menu
3)  Screen blanks, blinking underline
4)  Ubuntu 10.10 text screen.  Dot progress 'bar'....
5)  Screen blanks, large, non-blinking underline, position varies, suggesting incorrect resolution set.
6)  Hard disk light blinks on & off, i.e. boot continues
7)  No keyboard input works.  i.e. No ctrl-alt-F1, no console, no GDM.

When it does make it to GDM, Ctrl-alt-F1 will give me a black screen with a non-blinking underline character.

Xorg.0.log might have a hint... Perhaps I have 2 problems...
```

[  2705.461] Failed to switch from vt07 to vt01: Input/output error
[  2706.337] Failed to switch from vt07 to vt01: Input/output error
[  2706.760] Failed to switch from vt07 to vt01: Input/output error
[  2707.041] Failed to switch from vt07 to vt01: Input/output error
[  2707.568] Failed to switch from vt07 to vt08: Input/output error
[  2707.959] Failed to switch from vt07 to vt06: Input/output error
[  2708.135] Failed to switch from vt07 to vt05: Input/output error
[  2708.315] Failed to switch from vt07 to vt04: Input/output error
[  2708.490] Failed to switch from vt07 to vt03: Input/output error
[  2708.880] Failed to switch from vt07 to vt02: Input/output error
[  2709.093] Failed to switch from vt07 to vt01: Input/output error
[  2709.408] Failed to switch from vt07 to vt01: Input/output error

```

---

### Post by abeowitz on 2010-09-28
dmesg...

```

[   21.592633] vga16fb: initializing
[   21.592638] vga16fb: mapped to 0xffff8800000a0000
[   21.815160] Console: switching to colour frame buffer device 80x30
[   21.821090] fb0: VGA16 VGA frame buffer device
[   21.828396] do_general_protection: 12 callbacks suppressed
[   21.828400] bterm[2173] general protection ip:40400e sp:7fff284ff8a8 error:0 in bterm[400000+b000]
[   23.276526] bterm[2187] general protection ip:40400e sp:7fff39fed9c8 error:0 in bterm[400000+b000]

```

What is bterm?

Can I disable fb0?

---

### Post by abeowitz on 2010-09-28
VMC, thanks for helping, BTW... :)

:KS

Removing bogl-bterm seems to have done the trick...

Ctrl-Alt-F1 gives me a normal terminal now...

---

