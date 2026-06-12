---
title: "Suggestion for usb-midi adapter?"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by christian.convey on 2006-07-28
I'd like to connect my keyboard, which has only the old-style MIDI adapter, to my notebook.

Can anyone recommend a particular adapter model as being really easy to use under Dapper?  I only need it to support one MIDI device.

Thanks,
Christian

---

### Post by stmiller on 2006-08-03
The Yamaha UX16 (?) or XU16 works fine in Linux. Picked up automagically. It is restricted to 16 channels (that's all the device can do).

---

### Post by damo21 on 2006-08-05
I use Edirol UM-1EX and it works straight away, plug in and dapper automagically modprobes snd-usb-audio and it appears in jack connections instantly.
One minor issue (which I solved) was that if i left it plugged in during bootup, it stole the alsa device number 0 and then my audio configuration was all messed up.  Solution which worked for me was to hard compile the driver for primary audio device, and alsa, into the kernel.

Then it really makes no difference when things are plugged in or not.
It was confusing until I realised what was the problem.

---

