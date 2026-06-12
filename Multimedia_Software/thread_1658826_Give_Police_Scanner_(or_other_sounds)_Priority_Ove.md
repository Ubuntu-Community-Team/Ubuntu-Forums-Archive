---
title: "Give Police Scanner (or other sounds) Priority Over Music??"
date: 2011-01-03
forum: Multimedia Software
---

### Post by dli8ilb on 2011-01-03
Hi!  I am wondering if there is some way to automatically mute (or significantly lower the volume of) the music when, say for example, 
the skype/gizmo/ekiga recives a call, or there is some occasional chatter on the police scanner - then raise the music volume again once the other sound has finished playing/call ended.

[LIST]
[*] Ubuntu 9.10 (Karmic 32-bit)
[*] Music is playing through Banshee
[*] Police Scanner is just a live internet audio feed playing through VLC
[/LIST]
I'm absolutely willing to change/upgrade OS & software if this is at all possible.

thanks :guitar:

---

### Post by kostkon on 2011-01-06
Check *earcandy*. It's [in the repos]("http://packages.ubuntu.com/karmic/earcandy").

---

### Post by dli8ilb on 2011-01-24
kostkon, you are truly amazing. 
thank you - this is exactly what i was looking for!

---

### Post by Yellow Pasque on 2011-01-24
One of the perks of pulseaudio is that you can adjust the volume of apps relative to each other (using pavucontrol). I don't think you need another app/daemon to accomplish it (though if Earcandy works for you, enjoy).

---

