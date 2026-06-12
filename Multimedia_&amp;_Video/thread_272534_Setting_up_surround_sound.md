---
title: "Setting up surround sound"
date: 2006-10-06
forum: Multimedia &amp; Video
---

### Post by Over1ord on 2006-10-06
I have the Sound Blaster Live! 5.1 sound card and it works fine from installation but I dont have my back channels, sub, or center.  What can I do to make the whole setup work?  I went to the SoundBlaster website but they didnt have linux drivers.

---

### Post by dw5437 on 2006-10-06
Google 
Alsa Multi-channel Audio mini-HOWTO

Worked for me.

---

### Post by frolle on 2006-10-09
I tried to follow this guide: [http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml)

But without any luck, i still only have sound in my front speakers.

Anyone?

---

### Post by _simon_ on 2006-10-09
My other half has the same card.

from terminal:

```

alsamixer

```

She has the following enabled: (I don't think all of the below need to be enabled but she hasn't bothered to go through them and see which are unused)

Bass
Treble
3D Contol Sigmatel Depth
3D Contol Sigmatel Rear Depth
Surround
Center
LFE
Wave Center
Wave LFE
Wave Surround
IEC958 Coaxial
IEC958 LiveDrive
IEC958 TTL

---

### Post by frolle on 2006-10-09
> **_simon_ said:**
> My other half has the same card.

from terminal:

```

alsamixer

```

She has the following enabled: (I don't think all of the below need to be enabled but she hasn't bothered to go through them and see which are unused)

Bass
Treble
3D Contol Sigmatel Depth
3D Contol Sigmatel Rear Depth
Surround
Center
LFE
Wave Center
Wave LFE
Wave Surround
IEC958 Coaxial
IEC958 LiveDrive
IEC958 TTL

And it is working?

I have all that enabled.

Edit: I got it working :)

---

