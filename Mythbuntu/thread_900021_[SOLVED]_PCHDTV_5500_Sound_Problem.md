---
title: "[SOLVED] PCHDTV 5500 Sound Problem"
date: 2008-08-24
forum: Mythbuntu
---

### Post by napsilan on 2008-08-24
I'm having problems with the analog sound on my pchdtv 5500, using the v4l drivers (analog input does not show up with dvb).  Either 1.the sound from /dev/dsp1 has a horrible high pitch tin to it, or 2. /dev/dsp1 (or even /dev/dsp) does not exist.  

I have tried adding cx88-dvb/cx88-alsa to /etc/modules, compiling and installing the newer v4l-dvb drivers, compiling and using kernel 2.6.26.3, and using 8.10 alpha 4 (which had video problems since ATI drivers don't work with xorg 7.4, so I didn't get to test if the sound worked)

edit: attached dmesg of kernel 2.6.26.3, where both /dev/dsp and /dev/dsp1 are missing.  Had to rename it to .doc because it was bigger than the txt file limit for the forums.

---

### Post by klc5555 on 2008-08-25
Leaving aside for the moment that if you configure the PCHD5500 card with the DVB drivers in 8.04, the analog component of the card will then be configured as a completely separate (V4l) tuner from the digital component, and only later linked to its digital half in "Recording Groups", so that Myth doesn't try to schedule the two halves to record simultaneously. This is a big change from the way the PCHD5500 is configured in 7.10, where analog configuration appeared as a submenu of the DVB setup. I don't think the PCHD5500 documentation has caught up to this yet.

Anyway, a shot in the dark, but by the looks of your two posted outputs, if I'm reading them right, your actual sound device that Alsa should be using for default is an Intel chip on the motherboard (or elsewhere), but Alsa has arrogated the Connexant CX088 chip from the PCHD5500 as the default device, which won't work. Run asoundconf -l from a prompt and see all the listed Alsa devices. The first listed one is the one Alsa is trying to use. If it's the cx088 from the PCHD5500 is listed first, use asoundconf set-default-card to set your real device as the default. Then either /dev/dsp or /dev/dsp1 (it's a toss-up which) should work for the analog section of the card.

This would be my first guess.

Good luck!:)

---

### Post by napsilan on 2008-08-25
I think I might have found the problem with the sound in the updated kernel.  I had just copied the existing config and compiled it, but I took a closer look and apparently both ALSA and OSS were unchecked, so I'm compiling it again with ALSA and I'll see how it works.

edit:

Finished the kernel, only /dev/dsp (microphone input) is showing up, not /dev/dsp1 (sound input through the capture card). attached dmesg

in 2.6.26.3, asoundconf list is showing only the Intel sound card (correctly used for output).  No other sound devices are listed.

I added the dmesg of kernel 2.6.24.19, where both /dev/dsp (mic) and /dev/dsp1 (capture card audio) show up, but the capture card sound is high pitched and tinny.

---

### Post by newlinux on 2008-08-25
what are your liveTV audio settings in recording profiles? What have you got hte audio rate set to in mythtv-setup? try 48000 uncompressed for your recording profile.

---

### Post by napsilan on 2008-08-25
> **newlinux said:**
> what are your liveTV audio settings in recording profiles? What have you got hte audio rate set to in mythtv-setup? try 48000 uncompressed for your recording profile.

Winner

I had set the sound rate to 48k in the backend right away like the wiki recommended, however, I completely forgot about the frontend recording profiles.  I changed the frontend recording profile sounds rate from 32k to 48k and that fixed the high pitched tinny sound.  

I still need to use the stock kernel (2.6.24.19) to get the capture sound device (/dev/dsp1) to show up, but that's fine.

Thank you both for the help, I'll go add this to the mythtv wiki

---

### Post by sidboswell on 2008-09-08
Where do you set the sound on the front end?  I've got the tinny sound and can't seem to get rid of it.

V4L
/dev/dsp1

I've tried 32000, 44000, 48000 and checked and unchecked the volume selection.  


OK.  made the change on the front end and back end and still have the tinny sound....

Thanks,
sid.

---

### Post by newlinux on 2008-09-10
Did you change all your recording profiles on the frontend to the right settings or just the default?

---

### Post by enricor77 on 2010-08-23
I am trying to configure the PCHDTV under Mythbuntu 9.10:
I just sent this email to the support, I am going to keep the forum updated with any response. I hope you guys can help me as well:

To the support of PCHDTV,

I have recently purchased the PCHDTV-5500. I have successfully connected the card to the S-Video  exit of my Direct Tv box (Analog);however, no audio is captured.
I am using Mythbuntu 9.10 and mythtv 0.22 as player. 
I tried to compile the drivers from the cd or downloaded from the website but I received errors during the make step. The cx88_audio and other modules are loaded automatically by the system. 
I have connected the PCHDTV-5500 audio jack to the Mic or Line In on my audio card with is not muted and working properly.
 I verified that the S-Video exit is sending both audio and video, using a PVR-150.
I have followed the configuration steps on the wiki page to configure the card in mythtv both as analog and digital setting the open on demand flag and the sample rate at 48K.
I read that the card is sometimes shipped with the audio capture feature disabled and there is a way to enabled changing a registry on the cx88 eprom.

If I connect a jack from the composite exit of the directtv box to the line in I get audio, which is out of synch and not present into the recordings, same if I bridge the audio jacks through the card (directtv to PCHDTV , PCHDTV to line-in)
 
What am I missing?

An additional note:
Selecting /dev/dsp1 as audio device for the V4l Analog I get a static noise which is present also in recordings. 


Thank you so much for your help

---

