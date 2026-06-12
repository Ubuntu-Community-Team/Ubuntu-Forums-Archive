---
title: "Mic works(skype) but won`t record on any other app"
date: 2009-08-18
forum: Multimedia Software
---

### Post by Milossh on 2009-08-18
Hello,

I have a microphone, which works on skype, and everything is ok. When I talk into it, I can hear myself on a headphones. Now, when I open gnome-sound-recorder, press record, nothing happens; when I press it once more, it hangs.
Similiar thing with gtk-recordmydesktop. When I disable sound recording, everything is ok, but when I unmute sound in gtk-recormydesktop and press record, i get Error: 768. Could not open/configure sound card.

I have followed[ http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/")
to try to disable pulseaudio, and it looks like I did:

```
abnormal@Eniac:~$ pgrep pulseaudio
abnormal@Eniac:~$ cat /proc/asound/cards
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with ALC655 at 0xf000, irq 22
```

Anyone have an idea?

---

