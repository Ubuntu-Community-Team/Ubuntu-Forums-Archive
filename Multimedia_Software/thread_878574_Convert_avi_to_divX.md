---
title: "Convert avi to divX"
date: 2008-08-03
forum: Multimedia Software
---

### Post by rootk1t on 2008-08-03
Is there a utility?

Thank you.

---

### Post by kostkon on 2008-08-03
Could you be more specific about the formats?

I mean *avi* is just a container format and thus your *avi* file may be already encoded in the *divx* format.

---

### Post by kahlil88 on 2008-08-03
I think if you install mencoder and xvid, you should be able to encode things as XviD (which is essentially an open-source DivX).

---

### Post by rootk1t on 2008-08-03
Ok, here's the thing.

I've got this home cinema: [http://www.pioneer.eu/eur/products/42/100/42/DCS-370/index.html](http://www.pioneer.eu/eur/products/42/100/42/DCS-370/index.html)

And it sais it can play DivX. If I insert a avi file, it does not recognize that file, and I cannot understand **why???**:confused::confused::confused:

---

### Post by eye208 on 2008-08-03
To find out the format of your AVI file, open it in Ubuntu's default video player, then display the file properties in the sidebar. This will tell you which codecs have been used for the file. A typical Xvid file may look like this:

**Video**

Dimensions: 640 x 480
Codec: XVID MPEG-4
Framerate: 24 frames per second
Bitrate: N/A

**Audio**

Codec: MPEG 1 Audio, Layer 3 (MP3)
Channels: Stereo
Sample rate: 48000 Hz
Bitrate: 128 kbps

Some AVI files contain audio in AC-3 format instead of MP3. This may or may not be supported by your home cinema system. Or the video stream may be H.264 instead of Xvid. If the AVI uses a codec that is not supported by the home cinema system, you can use Avidemux or MEncoder to change the format to something compatible.

It really depends on the capabilities of the home cinema system. Linux video players can play pretty much everything, which may be a blessing or a curse, depending on your point of view. ;)

---

