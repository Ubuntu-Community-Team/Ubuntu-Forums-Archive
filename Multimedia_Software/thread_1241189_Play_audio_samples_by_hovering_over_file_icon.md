---
title: "Play audio samples by hovering over file icon"
date: 2009-08-15
forum: Multimedia Software
---

### Post by Crunchy the Headcrab on 2009-08-15
I just discovered that I can play audio files simply by holding my mouse of the icon.  This is awesome as it allows me to sample music files without opening my audio player!

The question that I have is if this is a Gnome function of if it is my audio player (exaile) that is doing this.  I don't have to open exaile for this to work.

---

### Post by mc4man on 2009-08-15
It's handled by totem-audio-preview which uses whichever totem is set as default, totem-gstreamer is the install default, can be changed to totem-xine thru installing totem-xine and using update alternatives

(( I don't believe the preview can be seperated from the totem default

Totem-xine can preview more audio formats than the gstreamer one

To change  ((assuming totem-xine is installed
```
sudo update-alternatives --config totem

```

---

### Post by Crunchy the Headcrab on 2009-08-15
Oh I didn't know I had any totem stuff installed.  I guess it's just included in gnome by default?  I'm using Fedora btw and it's not in my programs list.  This isn't a real pressing issue obviously, I was just curious because I definitely like this behaviour and if it was due to something I installed I wanted to make sure I did it in the future.  Apparently it's a default thing, that's even better.

Thanks

---

### Post by mc4man on 2009-08-15
> Apparently it's a default thing, that's even better.
I wouldn't have a clue about fedora, you could take a look around for a file or 2 with -audio-preview in the name to track down

In unbuntu there's a link in /etc/alternatives and the exec in /usr/bin (here both named  totem-audio-preview

---

