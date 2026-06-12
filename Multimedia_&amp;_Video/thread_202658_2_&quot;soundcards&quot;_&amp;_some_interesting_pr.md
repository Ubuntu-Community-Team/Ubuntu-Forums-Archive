---
title: "2 &quot;soundcards&quot; &amp; some interesting problems"
date: 2006-06-23
forum: Multimedia &amp; Video
---

### Post by play0r on 2006-06-23
ok, at first i thought it was a problem with the flash plugin when i made this post; [http://ubuntuforums.org/showthread.php?t=202436](http://ubuntuforums.org/showthread.php?t=202436)
turns out its actually a problem with which soundcard is chosen on boot.
the soundcards that come up are a soundblaster pci card, which is detected as an Ensoniq AudioPCI, & a VIA 82C686A/B rev50, which is a pci controller chip on my south bridge i believe. 
i've editted /etc/esound/esd.conf & made /etc/asound.conf & now i have audio output in flash videos in firefox & i no longer have to change preferences in xmms with which device to use & the Ensoniq AudioPCI is now default, but by doing so i've affected sound in vlc & totem-xine, also my system sounds. 
when i revert back to the old esd.conf vlc, totem-xine & the system sounds have audio output again & VIA 82C686A/B rev50 is default again, but then flash doesn't again & i have to change xmms's preferences.
any ideas here? i'm kind of annoyed & very desperate lol.

ez,
play0r

p.s.
i can post my editted esd.conf & the asound.conf if needed.

---

### Post by play0r on 2006-06-23
looks like im completely wrong about esd.conf & asound.conf
i just reverted to the uneditted config & it selected my esoniq audipci. any idea on how to specify which card gets used on boot?

ez,
play0r

---

### Post by play0r on 2006-06-23
& now that i used "mixer" instead of "default" in my editted esd.conf
the VIA doesn't come up any more & now i have sound in both totem-xine & firefox flash animations, but i still have no system sounds?!
WEIRD!

ez,
play0r

---

### Post by irv on 2006-06-24
Take a look at this how to link on sound in Linux:
[[COLOR="Red"]http://tldp.org/HOWTO/Sound-HOWTO/index.html[/COLOR]]("http://tldp.org/HOWTO/Sound-HOWTO/index.html")

---

