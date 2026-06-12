---
title: "Simultaneous sound via hdmi and spdif?"
date: 2011-03-02
forum: Mythbuntu
---

### Post by Saubazi on 2011-03-02
I am just speculating on my way to work.
I just realised that apparently sound via hdmi is already reality even in Linux?
I have club3d gt220 nvidia card and I haven't checked it yet (don't know if all of them have sound via hdmi)
Anyway until now I only use my old amplifier with 5.1 and spdif from my mobo - only I have to switch it on always when I use mythtv. Hypothetically speaking if my GPU supports sound via hdmi, am I able to enable both?

---

### Post by alien878 on 2011-03-02
If you mean one at a time, then that depends on the hardware.  For example, HDMI and PCI sound worked out of the box for me, but I know others have problems.

If you mean both at once, that can be a bit tricky.  It can be done with alsa plugins, but as far as I know, passthrough won't work in this config (If you ever figure that out, let me know).

See [http://knoppmyth.net/phpBB2/viewtopic.php?p=57567&highlight=alsa#57567](http://knoppmyth.net/phpBB2/viewtopic.php?p=57567&highlight=alsa#57567) for an example.

(Why both at once?  Well, if I have a 5.1 sound source, I would like to simply turn the TV volume down and turn on the receiver without messing around in the setup each time)

---

### Post by Saubazi on 2011-03-02
No, not really simultaneously, you are right. BUT I had a problem with previous hardware and myth that I used passthrough for live tv and DVD but actually analogue for music and mythstream. In that case I had a irexec script that modified mysql definitions for mythtv setup and for alsamixer but it always required short restart of frontend. 

If I now have to do the same (mostly switching mythtv settings via mysql and restarting frontend) it is not worth the trouble - if I can do it solemnly by changing alsamixer settings then by all means - I do not need simultaneous sound via amplifier and tv, but sometimes it would be cool to have sound only from telly if I do not feel like switching on the amplifier.

I also tried plugging in RCA-cable to telly parallel to hdmi but somehow I could not the tv to get picture from one and the sound from the other.

It is not a biggie with new upscaling of sound to 5.1 and software soundmixer - I am very comfortable with myth. Only I always need my amplifier

---

### Post by alien878 on 2011-03-03
You can have mythmusic use a different device than everything else as it has it's own device in the settings.  However, everything else uses the default device.

You can have multiple output devices at once using alsa, but as far as I am aware, passthrough won't work (at least, it didn't when I tried it).

I have thought of using the sql changing script, but that seems too much of a bother.  I stick with spdif for mythmusic and HDMI for everything else.  I just have to keep the good ol' DVD player when I want good sound on a movie.

---

### Post by BicyclerBoy on 2011-03-04
I think you can get S/PDIF pass-thru working in parallel with multi-channel LPCM over HDMI..

Player outputs 5.1 to normal surround5.1 plug which is routed to HDMI.
Dsnoop this into the a52 plugin..
The alsa a52 plugin to outputs AC3 (a52) over S/PDIF.

The sound quality of a52 plugin is not perfect & I find that every hour it gets a bit screwed up.

---

### Post by alien878 on 2011-03-04
> **BicyclerBoy said:**
> I think you can get S/PDIF pass-thru working in parallel with multi-channel LPCM over HDMI..

Player outputs 5.1 to normal surround5.1 plug which is routed to HDMI.
Dsnoop this into the a52 plugin..
The alsa a52 plugin to outputs AC3 (a52) over S/PDIF.

The sound quality of a52 plugin is not perfect & I find that every hour it gets a bit screwed up.If the sound quality dropped, it probably isn't pass-through.  I suspect what happened is the AC3 was de-encoded and re-encoded.  That is what happened when I used the alsa multi-plugs above.

---

### Post by BicyclerBoy on 2011-03-04
Correct, it is not real pass-thru' but a real-time a52 encoder.
It could be a good way to get multi-channel digital audio using an older AVR HT amp.

Some people may find the audio quality okay.
The a52 plug-in does not stop you using the digital pass-thru S/PDIF directly.

Sadly it's the only way to get 5.1 digital audio without using HDMI.
(excluding external DACs etc)

Some brands of TV were going into standby when the HDMI audio stream stops.

MythTV 0.24 has an separate digital output device setting. You can leave the desktop audio set to analogue etc & MythTV will use S/PDIF or HDMI.

---

### Post by alien878 on 2011-03-05
> **BicyclerBoy said:**
> Player outputs 5.1 to normal surround5.1 plug which is routed to HDMI.
Dsnoop this into the a52 plugin..
The alsa a52 plugin to outputs AC3 (a52) over S/PDIF.I just read this closer.... You can dsnoop an output?  I thought it only worked with inputs.  Care to share your config?

---

### Post by BicyclerBoy on 2011-03-07
I thought you could..I'm not using dsnoop or HDMI..
Maybe it should be the copy plug-in.
Finding any docs/info about using alsa is hard work.

My alsa skills has only got a52 plug-in & channel re-ordering.

---

