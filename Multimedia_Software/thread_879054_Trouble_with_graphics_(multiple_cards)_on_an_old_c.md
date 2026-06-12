---
title: "Trouble with graphics (multiple cards) on an old computer"
date: 2008-08-03
forum: Multimedia Software
---

### Post by Dishonorable on 2008-08-03
So I have an intel integrated video card which as far as I can tell I've disabled in the Bios (ie the feature labeled "integrated graphics" is set to "disabled").  Despite this, Ubuntu has recognized the device.  I also have an old PCI Radeon 9100 installed, which is what my monitor is hooked up to.  The computer is a 2.5 Ghz celeron with 512 Mb of RAM.  I realize that this is a pretty dated machine, but I figured it should run ok with Ubuntu considering it managed XP quickly and without problems.
It runs slow as hell, particularly within firefox, but also just in general.

I figure that the video card situation is probably to blame.  How does Ubuntu recognize the integrated card despite the fact that it's disabled in the bios?

Right now in the screen& Graphics preferences it shows no driver installed for the integrated card and for the radeon card it shows ATI Radeon (fglrx).

If I press "Test" it outputs:

on_button_test_config_clicked()
xauth:  creating new authority file /tmp/dcg-jEOtgV5914/xauthority
Got pid 6187
(0, 0)
checkpoint 1
None
False
Sorry, this configuration video card driver
and monitor doesn't appear to work:

Messages from the X server:
(EE) I810(0): Cannot read V_BIOS (3)
(EE) I810(0): VBE initialization failed.
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error:


Can anybody walk me through what fixing this might require?  Or is my computer just too ancient for the full Ubuntu?

---

### Post by overdrank on 2008-08-03
HI and if you are using Hardy then I would suggest you use the ati driver that comes with hardy on the install. I do not use a ati graphics now but when I was testing it was the ati driver on install that was the best. This link may help some also.
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by Dishonorable on 2008-08-03
I'm using the drivers that installed automatically...   everything is going really slow.  The most apparent effect of this outside of firefox is just clicking and dragging on the desktop.  The rectangle for selecting that appears just jumps across the screen.

---

