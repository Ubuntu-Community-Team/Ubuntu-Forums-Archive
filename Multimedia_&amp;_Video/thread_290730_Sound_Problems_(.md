---
title: "Sound Problems :("
date: 2006-11-01
forum: Multimedia &amp; Video
---

### Post by yellow beard on 2006-11-01
I dont know how this happend but now when I boot into dapper i have a red x on my volume control in the panel. When i click it it says"

```
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.:( 
```

And 

```
No volume control GStreamer plugins and/or devices found.
```

When I try "aplay -l" i get no sound cards found. If i switch to root and try: "modprobe snd-intel8x0" that works and aplay -l gives me

```
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I tried adding snd-intel8x0 to /etc/modules but when I reboot aplay -l gives me no sound cards found again. Strange thing is I get the ubuntu drum sound when the log in screen appears but as soon as i log in I have no sound. Ive tried following this guide: [Comprehensive_Sound_Problems_Solutions_Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")
and removing the alsa packages but it doesn't make a difference.

I think it might be somthing to do with permissions. aplay -l says aplay: device_list:221: no soundcards found.. when i try it as a regular user but as root it works and gives me a read out of my sound card.

---

### Post by yellow beard on 2006-11-01
Fixed it. Just needed to add my self to the group audio! ```
sudo gpasswd -a username audio"
```

---

