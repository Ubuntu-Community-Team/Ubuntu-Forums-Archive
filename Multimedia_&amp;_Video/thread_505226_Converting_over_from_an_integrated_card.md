---
title: "Converting over from an integrated card"
date: 2007-07-20
forum: Multimedia &amp; Video
---

### Post by docdagger on 2007-07-20
I have an HP that came with the xpress 200 integrated graphics from ATI.  I bought a PCI express ATI that is the X1650 pro to take over.  I used the manual approach to update to the most recent driver from ATI for linux.  Everytime I connect the cable to the card the system brings up a screen about having to shut down Xvideo file.  My integrated card works just fine.  Any ideas how to get this to cooperate better?

Thanks.

---

### Post by scxtt on 2007-07-20
are you plugging your monitor (or a 2nd monitor) into the X1650 *after* you've booted up on the integrated card?

---

### Post by docdagger on 2007-07-20
I've been plugging into the new card before I boot up the computer.  Do you need to switch cards in ubuntu after you're to the desktop then?  Once the new card is in the express slot the integrated plug in no longer gives a signal.  I left the new card in and then booted up with the vga adapter plugged into the integrated card.  The monitor registered no signal.  I finally took the new card out then the integrated card began working again.  I then booted into ubuntu and used envy to download the latest driver from ati for the 64 bit platform.  I am wondering why the ubuntu system is having a hard time redirecting the newest drivers to the new card.  Please let me know what other things could be done.  I'm assuming that ubuntu can utilize the pci express slots.

---

### Post by scxtt on 2007-07-20
if you bought the ATi card to "take over" for the integrated card - it would be best to disable it via your motherboards BIOS (on the same token, you may have to enable PCI-e via your bios as well - it may be a "1 or the other" type deal) ... then plug your monitor into the ATi card and take it from there ... i'm sure you can use both at the same time, but if you don't have any reason to, and it's giving you problems - take it out of the equation ...

it's not a great idea to plug in / move around video cards after X has come up - probably isn't an "end of the world" thing (and you can always Ctrl+Alt+Backspace to restart) - but DO NOT physically remove a card after your box has power (i'm sure you know that ;)) ...

---

### Post by docdagger on 2007-07-23
I'm guessing you mean to disable the integrated card?  I won't be able to do this till tonight so I'll try it then.  I'll reread the error message and post it so I let you know exactly what it's saying.  I'm just recently installed the ubuntu system so I'm still pretty vague on many of it's aspects.  I'll also check the PCI e slot to verify it's enabled.

---

