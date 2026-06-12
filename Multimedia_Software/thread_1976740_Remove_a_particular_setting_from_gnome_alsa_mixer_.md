---
title: "Remove a particular setting from gnome alsa mixer and restore it at boot"
date: 2012-05-09
forum: Multimedia Software
---

### Post by dzchimp on 2012-05-09
I'm facing a particular issue with my Creative Sound Blaster CA0106. I find that if a particular setting titled IEC958 as displayed in gnome alsa mixer is toggled on, the sound card is muted. Unfortunately every time the PC is rebooted, the setting is toggled on automatically. Hence I have to manually toggle it off on every boot.

The following is the setting:
[IMG]http://droidzone.in/images/screenshots/Selection_001.jpeg[/IMG]

I've stored alsa mixer settings with:
```
alsactl store 0
```

If I do a:
```
sudo alsactl store 0
```

I get an error that home directory "/home/myhome" is 'not ours'

I've added the following to /etc/rc.local:

```
alsactl restore
```

But it doesnt seem to save my alsa settings/restore it at boot. Does gnome alsa-mixer have a seperate settings file? How do I proceed?

---

