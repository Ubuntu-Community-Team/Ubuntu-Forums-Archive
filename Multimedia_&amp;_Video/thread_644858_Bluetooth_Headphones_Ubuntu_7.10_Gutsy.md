---
title: "Bluetooth Headphones Ubuntu 7.10 Gutsy"
date: 2007-12-19
forum: Multimedia &amp; Video
---

### Post by basjava on 2007-12-19
I have a bluetooth headset (Dell BH200) that works perfectly in XP - I can actually connect it two different ways in XP, as an audio sink and as a headset - for skype, etc. I am wanting to use them as headphones in Ubuntu, this was easy in XP - just tell it to use the audio sink service restart whatever application I wanted to use if it was already open and away I went. 

After living on the forums for the past two days I have come across some very useful information on connecting them in Ubuntu Gutsy. After following the directions on several threads listing commands and config files to edit I came across the Blueman applicaton. I ran it, connected my headset to it, setup the services to use audio sink for the headset. I finally even got the headset to show up in sound preferences. However the only place BT Headset shows up is the Default Mixer Tracks in the Sound Preferences window. But after changing that to BT Headset I still get no sound out of the headset. 

Contents of my ~/.asoundrc file

```
 pcm.headset {
  @args [BDADDR TIMEOUT]
  @args.BDADDR {
    type string
    default "00:16:44:10:81:9E"
  }
  @args.TIMEOUT {
    type integer
    default 6000
}

  type sco
  bdaddr $BDADDR
  timeout $TIMEOUT
}

ctl.headset {
  type sco
}

pcm.a2dpd {
  type a2dpd
}
```

Its probably something small I'm missing, but any help would be appreciated.

---

### Post by basjava on 2007-12-19
[Not that I was pitching Windows but rather proving the headset was functional]

---

### Post by basjava on 2007-12-22
After learning the ~/.asoundrc file's purpose, I decided to delete my ~/.asoundrc file and restore it to default, I then added only:
```
pcm.bluetooth {
  type bluetooth
  device "XX:XX:XX:XX:XX:XX"
}
```
doing this made it work in Audacious when I manually typed in "bluetooth"
[http://blueman.tuxfamily.org/forum/viewtopic.php?f=5&t=5](http://blueman.tuxfamily.org/forum/viewtopic.php?f=5&t=5) 

And I wanted bluetooth to be the default device, so I used this: 
```
pcm.!default {
  type bluetooth
  device "XX:XX:XX:XX:XX:XX"
}
```
However, later I realized it wasn't defaulting to my sound card if the headphones weren't on, the application would fail and issue an error message.

Does anyone know how to make the sound card the default device if the headphones aren't on or able to be connected? :?:

---

### Post by Ceadda on 2007-12-22
I am experiencing the exact same problemo. any help would be greatly appreciated.

---

### Post by Mait on 2008-01-14
> **basjava said:**
> However, later I realized it wasn't defaulting to my sound card if the headphones weren't on, the application would fail and issue an error message.

Does anyone know how to make the sound card the default device if the headphones aren't on or able to be connected? :?:

I have exactly same problem. Help plz

---

### Post by MrBordello on 2008-01-15
same thing here. This .asoundrc fixed it temporarily:
```

pcm.bluetooth {
type bluetooth
}

pcm.!default {
 type plug
 slave.pcm "bluetooth"
}

```
(the MAC is _not_ needed with Blueman !)
But after every restart the headset disconnects randomly. :(

---

