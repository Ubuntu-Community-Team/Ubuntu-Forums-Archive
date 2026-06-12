---
title: "need help getting audio output working"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by Runiko on 2008-01-07
Hi all!

I bought a cheap-cheap laptop (everex stepnote nc1510) the other day and have been struggling to put ubuntu on it (because there are no XP drivers and vista is slow enough to be unusable.). I've gotten a lot of good help here so far, and have wireless networking up and running, and am installing the Openchrome graphics drivers as we speak.

But I am puzzled: Why do I get no sound? There seems to be a VIA sound driver running by default, but going into "preferences>sound" and pushing "test" on anything results in a blank silence.

When I run lspci, the sound card is listed as: " Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)"

Can anyone help me get this resolved? I love how fast ubuntu runs on this thing, and want to be able to use it for everything!

Thanks in advance!

---

### Post by linuxwizard on 2008-01-08
Type this into a shell alsamixer

You will now see what appears to be a graphical equalizer. It is more like ten different volume controls in the sample place.
To navigate around:
Left and Right Arrow Keys - Move left and right (if you move long enough in one direction you will get back to where you started - you will not fall off the screen )
Up and Down Arrow Keys - Increase and decrease volume respectively
Letter M Key - Mutes/unmutes. If a channel is unmuted, then there is a green box underneath the volume slider. If the channel is muted, the box is grey.

Make sure everything is unmuted.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

