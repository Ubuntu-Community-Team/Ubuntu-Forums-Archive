---
title: "live cd or full install: hang on boot, card insert"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by Maciek on 2006-07-04
I've been running Debian on my old Inspiron 7000 for some time, and had no problems running my wireless SMC2835W card in it.  I believe I was using the "prism54" module/driver.

This past week I decided to install Ubuntu 6.06 on this same computer, to bring my installation more up to date, and make it easier to manage.  Alas, having the card inserted into the PCMCIA slot seems to cause Ubuntu to freeze.  Here are the scenarios I've encountered/tested:

1. if I leave the card inserted during Live CD boot, system seems to hang at the line "Loading hardware drivers"  (text from memory, not necessarily exactly that phrase)

2. I removed the card and was able to boot from the Live CD, and install Ubuntu to the hard-drive.  I was able to boot and reboot many times with the card not inserted.

3. When I insert the card back into the laptop and boot, it again hangs on the same line.

4. Even weirder, if I insert the wireless card into the PCMCIA slot while the laptop is already booted off the hard-drive installation and sitting at the desktop screen, the laptop seems to *freeze*!:
- mouse cursor no longer moves when I move the mouse
- no disk activity no matter what I do
- keyboard completely unresponsive, even the caps lock/num locks LEDs, IIRC
- can't switch to virtual console using Ctrl+Alt+Fn? (again, keyboard's out)

Help??? :confused: 

Since the laptop freezes whenever I insert the card I can't do any sort of diagnostics.  Perhaps I need to specify some Linux boot parameters???

---

### Post by tturrisi on 2006-07-04
[check here]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?action=fullsearch&context=180&value=prism54&fullsearch=Text")

---

### Post by Maciek on 2006-07-04
Did you have any particular post in mind in those search results?  None of them mention the case of the whole system hanging with the card; they mostly address (relatively) minor problems of the card just not working...

Anyhow, I suppose that might be a good resource for further config issues once I stop my system from hanging, thanks.

---

