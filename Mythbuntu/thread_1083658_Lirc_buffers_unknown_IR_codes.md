---
title: "Lirc buffers unknown IR codes"
date: 2009-03-01
forum: Mythbuntu
---

### Post by Freddan101 on 2009-03-01
I got my iMON PAD IR/VFD 15c2:0036 working a couple of weeks ago. I been fiddling around a bit to make the remote work as I want it to (and also teach my Pronto Neo the tricks). Though, I have recognized something weird.

Lirc works just fine as long as I'm just sending iMON codes but as soon I'm sending an IR code to the amp or TV for example lirc freezes up and it takes a couple of iMON codes to make it work again. It's just like lirc is buffering the codes but can't understand them, then it takes a couple of "real" codes to flush out the "bad" ones out.

For example, I'm pressing pause to stop playback, I press pause again and playback starts, no problem. Then I press pause, playback stops, I raise the volume on the amp but when pause is pressed again nothing happens. I have to press pause two more times to make it work. Then everything is back to normal until next time I need to control a different device.

When I control other devices nothing shows up when running mode2 or irw. The iMON codes needed to flush out the "bad" ones don't show up either.

I start lirc with these commands:

```
/usr/sbin/lircd --device=/dev/lirc0 --listen=8765 --listen
/usr/sbin/lircd --device=/dev/lirc1 --connect=localhost 8765 --output=/dev/lircd --connect=localhost 8765 --pidfile=/var/run/lircd1.pid
```

I would need something to make lirc ignore the codes it doesn't understand, but I have found nothing on this when searching the forums. Any ideas how to solve this would be much appreciated!

---

### Post by Freddan101 on 2009-03-06
I'm starting to suspect that the IR devices on my two Technotrend 1500 DVB cards are interfering with the iMON device. 

Is there a way I could blacklist the TT IR devices? I just don't know where to start looking...

---

### Post by Freddan101 on 2009-03-25
*bump*

---

