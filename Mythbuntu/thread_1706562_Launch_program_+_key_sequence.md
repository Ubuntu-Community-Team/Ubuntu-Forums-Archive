---
title: "Launch program + key sequence"
date: 2011-03-14
forum: Mythbuntu
---

### Post by IceCap on 2011-03-14
I'm working on installing b-em (a BBC Micro emulator, b-em.bbcmicro.com) on my Mythbuntu box through MythGame (I'm planning on writing up a detailed how-to and posting here if there is interest) and I just got it to work.
  However, there is no (right now with version 2.1a) way to launch the program into fullscreen, but instead Alt-Enter toggles between windowed and full-screen.
  So my question is, how can I automatically launch the program and right there after send the emulator an "Alt-Enter" signal to go into full-screen?

  Also, I'm planning on having my remote quit the emulator (even though playing games really requires a keyboard or a joystick) and it involves the key sequence "F11", "Alt-F", "E".  I'm assuming this will be a breeze with lirc (I checked quickly and it looks like Iirc can handle a sequence of key-strokes)?

  Thanks

  IC

---

### Post by newlinux on 2011-03-14
If the emulator doesn't support LIRC directly you might want to consider using irxevent.  I haven't used it, but from what I remember it should be able to do what you want.

---

