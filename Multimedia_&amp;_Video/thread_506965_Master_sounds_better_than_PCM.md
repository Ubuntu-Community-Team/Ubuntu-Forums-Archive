---
title: "Master sounds better than PCM"
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by Aphoxema on 2007-07-22
I'm having an interesting issue, I can't even begin to guess what the source is. 

My sound card is is a '00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)' and when I have my master volume at a more comfortable level but I turn my PCM volume up (Ubuntu), any application that puts out audio (the worst are VLC and Totem, but XMMS and RhythmeBox aren't as bad) sounds a little distorted, like my speakers are going out but it's the same no matter how low I turn the physical volume knob down.

But... if I turn the PCM/application's volume down and I control things by the Master volume, things sound much better. As long as the PCM or the individual applications volume is really low and the Master is higher, everything sounds okay. I wouldn't really care about this but it puts me in a frustrating position of volume control in all my applications, like Pidgin even with the soft, short sounds I set on it or Firefox when I come across someone's page with their own music or something and I nearly fall out of my seat getting a face full of death metal or heavy rap.

---

### Post by megabyte405 on 2007-07-22
A good rule of thumb is, if your speakers/amp/receiver has its own volume control, set all other volumes (in the computer) to 75% of max and then only use the hardware control.  This will prevent "clipping" which is the distortion that you're hearing.  If you don't have a hardware volume knob, then use Master to control your volume: PCM "comes before" master, and so should be set at 75%.  Some applications (like VLC) may have their own additional volume control: generally either 75% or 100% works best with those.

---

