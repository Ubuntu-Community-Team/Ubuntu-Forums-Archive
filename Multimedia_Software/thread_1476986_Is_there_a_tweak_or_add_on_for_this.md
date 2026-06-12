---
title: "Is there a tweak or add on for this?"
date: 2010-05-08
forum: Multimedia Software
---

### Post by savaan on 2010-05-08
I'm still new to Ubuntu (i'm on 9.10) so i'm not sure which media player i'm hearing. When i hover over my mp3's a player will start automatically giving me a sample of the song. problem is, when i move my cursor away, the song stops. is there a way to just continue that song with a click or some add on, or is the only way just to double click and play it through my various media players? i'd assume that some media player has kicked in if its coming through my speakers...just thought it'd be nice not to have to restart the song, but rather continue playing and allow my cursor to be moved away.

---

### Post by dFlyer on 2010-05-08
If your using 10.04 the default media player is Rhythmbox located in Applications, sound and video. Double clicking will start it for full play.

---

### Post by savaan on 2010-05-08
I have a few different media players here. Any of them will start my song by double clicking..it starts the song from the beginning :( I was hoping to find out how/if its possible to be able to move my cursor away, yet have the song continue playing

---

### Post by User3k on 2010-05-08
> **savaan said:**
> I have a few different media players here. Any of them will start my song by double clicking..it starts the song from the beginning :( I was hoping to find out how/if its possible to be able to move my cursor away, yet have the song continue playing

I am not sure if you can, but that would be a great feature to add in the future releases I think.

---

### Post by savaan on 2010-05-08
i'm no programmer, but apparently its activating some kind of media player in the background...why not have a feature to continue playing, a right click or something. doesn't even have to be a full featured playlist, just a one song at a time thing

---

### Post by mc4man on 2010-05-08
What's being used is totem-audio-preview

I guess if you wanted to add to your r.click you could in numerous ways  - a simple custom definition ( r. click - open with - use custom command), a nautilus action, simple script, ect.

The disadvantages are - no control if run in background, if opened in a terminal still no control other than Ctrl+c to kill.
May cut out early on you , may not. (on a quick test a nautilus action/script played fully -  a r. click created custom definition not completely to end.

Really not suited to such use.

(screen shows all 3 - custom def - highlighted, script - preview1, n-a - Totem Preview

The basic command if you wish to fool with is
totem-audio-preview
(location - /usr/bin

---

