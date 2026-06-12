---
title: "Sound and video drivers..."
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by vexerr on 2008-04-06
Ok first off, I'm not totally in the dark with linux. Ive had experience using it, just never having to set everything up. So far linux automatically assigned some open source drivers for my radeon x800, will this retain full functionality?  So far the graphics seem pretty solid but havent fully explored it yet.  Second, I have onboard soundcard and the drivers it assigned must not be up to par.  The sound itself works fine, but I have 5.1 speakers and the sound is limited to the front two.  That and the system volume wont change, the only way it changes it through the actual speaker system.

I believe I had the drivers for Realtek AC 69 on my windows system, but I cant quite figure out how to make that happen for linux.  I found the drivers and what not, but cant figure out how to get them into use.  Thanks.:confused::confused:

---

### Post by Metaljaz on 2008-04-07
For sound issues give this a try.

Double click the volume control, go to Edit > Preferences, and enable the following components:
Master Surround
Surround
Center
PCM
Make sure you have these sounds unmuted, or you will get no sound out of your subwoofer, center and rear channels.

Also, from the terminal type: alsamixer
make sure that channels you need are not muted. You use the arrow keys to move and the "m" key on the keyboard to mute unmuted selections.

---

### Post by vexerr on 2008-04-08
i tried that with no luck. went into the terminal with alsamixer and although the channels for surround and center were shown... they did not have the multicolored colume meter that pcm and pc speaker have... they still do have the box where it either reads 00 or MM, they both read 00 as do PCM and pc speaker.

---

### Post by Metaljaz on 2008-04-08
From the terminal window (under Applications>Accessories>Terminal) type:

sudo lshw
Enter your password when prompted

scroll to multimedia and tell us what it says under product. This should be your sound card. Should look something like this:

 *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0

---

