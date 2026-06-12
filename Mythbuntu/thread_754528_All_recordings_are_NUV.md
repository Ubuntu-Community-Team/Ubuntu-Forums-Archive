---
title: "All recordings are NUV"
date: 2008-04-13
forum: Mythbuntu
---

### Post by dallas8101 on 2008-04-13
I have an older mythbuntu 7.1 box setup with a hauppauge 150 card.  It records to .MPG files, just as I need for my further processing.

I have just setup a new 8.04 beta mythbuntu box using a pcHDTV 5500 card, using in analog NTSC mode.  I had originally set it up to do transcoding.  All my recordings are going to a .NUV file, even before transcoding starting.  From some other forum messages,  I then turned off all transcoding switches again to try to see if I would get to mpg files.  

I am still getting NUV files.  They are really useless to me for use afterward (although I have not tried to simply copy to another system and rename to MPG).  Does any one know if it is simply the difference between the PVR-150 and the HD5500 cards, or the 7.1 vs 8.04?  Or have I gotten stuck because I started with the transcoding settings on?

---

### Post by laga on 2008-04-14
The analog card of the pcHDTV 5500 is just a framegrabber. MythTV puts recordings from these cards into a Nupplevideo container, hence the .nuv extension.

The PVR 150 spits out MPEG-2.

---

### Post by tgm4883 on 2008-04-14
Laga is correct.  The pcHDTV 5500 does not contain a hardware encoder.  So mythtv is actually encoding the file using your CPU.  That is where it creates the NUV file

---

### Post by dallas8101 on 2008-04-14
Many thank for confirming.  I had already ordered another PVR-150 card in expectation.  I need it all working by Tues night.  

Another question is if there is a way to setup transcoding processes to convert from NUV to MPEG2, rather than MPEG4?  I have seen threads for NUV->MPEG4, but all with some issues on the reliability of NUVCONVERT (not sure of the name).  That way I could at least continue to use my pcHDTV 5500 investment to some productive use.  Otherwise I have to pull it entirely.

I am a newbie, so my knowledge of the linux/myth program set is rather limited.

---

### Post by tgm4883 on 2008-04-14
> **dallas8101 said:**
> Many thank for confirming.  I had already ordered another PVR-150 card in expectation.  I need it all working by Tues night.  

Another question is if there is a way to setup transcoding processes to convert from NUV to MPEG2, rather than MPEG4?  I have seen threads for NUV->MPEG4, but all with some issues on the reliability of NUVCONVERT (not sure of the name).  That way I could at least continue to use my pcHDTV 5500 investment to some productive use.  Otherwise I have to pull it entirely.

I am a newbie, so my knowledge of the linux/myth program set is rather limited.

I'm not sure about transcoding it, but IMHO software encoders are not worth it.  Either pull it or start getting HD.

---

### Post by tgm4883 on 2008-04-14
Keep in mind, that when you do switch and start using the digital part of the pcHDTV 5500, you can record more than 1 show at a time per tuner.

---

### Post by laga on 2008-04-14
Transcoding to MPEG-2 in MythTV isn't possible yet. It's being worked on, but I don't know when it'll be complete.
You can use an "user job" to transcode to MPEG-2.. but a PVR 150 is easier :)

---

