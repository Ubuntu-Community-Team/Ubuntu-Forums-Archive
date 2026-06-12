---
title: "Display will not wake after being put to sleep"
date: 2008-12-26
forum: Mythbuntu
---

### Post by RaygionsSumta on 2008-12-26
I have recently (Dec 19, 2008 ) switched from Ubuntu (Hardy Heron) with a manual install of MythTV to MythBuntu 8.10.  Prior to that I was working on Fedora.  In MythBuntu 8.10, I am finding that when the machine is left inactive that it suspends signal to the display.  This is good, as when someone just walks away, the television will shut off after 10 minutes without a signal.  What is bad, is that the signal out from the Myth box is not being resumed when the remote buttons are pressed.  Nor when a button on the keyboard is pushed. Nor when the mouse is moved.  

The only fix, I have discovered is to switch consoles -- punch in Ctrl-Alt-F5, then return to the graphic console with Ctrl-Alt-F7.  This restores the DVI signal, but the bother of having to do this is only further exacerbated by the WAF (Wife Irritation Factor) and the loss of useful bluetooth keyboard support in Intrepid Ibex.

I have found two suggestions for a fix to this failue to resume.  Unfortunately, neither has worked.

1) Add ‘Option “UseEvents” “true”’ to the Screen section of xorg.conf
2) Add ‘DOUBLE_CONSOLE_SWITCH=true’ to /etc/default/acpi-support

Any suggestions?

---

### Post by RaygionsSumta on 2008-12-31
bump

---

