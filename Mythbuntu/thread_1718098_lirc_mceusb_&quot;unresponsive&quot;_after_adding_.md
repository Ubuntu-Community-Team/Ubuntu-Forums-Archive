---
title: "lirc mceusb &quot;unresponsive&quot; after adding transmitter"
date: 2011-03-30
forum: Mythbuntu
---

### Post by dhjohnson on 2011-03-30
Hello.

I recently had to start using an IR transmitter after Comcast rolled out DTAs in my area.  I plugged the transmitter cable it into the back of the USB IR receiver I've been using for a few years and it worked fine.  My issue is that my remote is now somewhat buggy and unresponsive:  Many of the buttons on the remote will stop working (as far as the MythTV frontend is concerned -- irw shows that a button is being pressed) after 30 to 90 seconds from the time the last button on the remote was pressed.  The up, down, and pause buttons are exceptions to this -- pressing one of those buttons first "revives" the rest of the buttons on the remote.  When I press one of those three buttons, it is recognized immediately, but multiple presses of one of the other buttons before pressing one of the "reviving" buttons doesn't create a response from the application.

I've had a little bit of luck changing the repeat values in my ~/.lirc/mythtv, but that seems like a really kludgey solution and one that doesn't really address whatever the underlying problem is.  I also tried using a different IR receiver/transmitter without success.

Thanks in advance.

---

### Post by dhjohnson on 2011-04-02
Bump.  :)

---

