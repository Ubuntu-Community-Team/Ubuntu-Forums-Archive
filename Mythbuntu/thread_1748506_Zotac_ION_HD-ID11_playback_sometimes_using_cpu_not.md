---
title: "Zotac ION HD-ID11 playback sometimes using cpu not vdpau"
date: 2011-05-03
forum: Mythbuntu
---

### Post by rbroberg on 2011-05-03
I upgraded to mythbuntu/11.04 last week, with an out of the box installation on a zotac zbox HD-ID11 front end (backend is mythbuntu/11.04 as well).  Connection from zbox to home theatre is via hdmi cable.  The zbox is a dual-core 1.6Ghz atom with the next-generation ion (512M onboard) nvidia.  Audio configuration is set to the nvidia hw option (equivalent to the hwplug1,7 in mythtv/0.24), with 5.1 specified as output.

I'm having an issue where, regardless of the playback profile which I choose, many (most!) of the content I play seems to be using the cpu for decoding rather than the hw.  This can been seen by watching the cpu used by the box - when watching videos with lower resolution than 720p, the cpu goes up to 48-52% (mythfrontend using the cycles).  When watching videos which are 720p, the hw decoding is definitely happening, as the cpu is around 4-6%.

All of my recorded content (hd homerun), SD and HD, are playing back pegging the cpu as well.

I've changed my playback profiles (and tried many of them, including all of the vdpau ones) but the behavior is unchanged.  I've examined the output from 'mythfrontend -v playback' and the messages make it look like it's using vdpau.

What's more is that the audio quickly becomes 160ms-200ms out of sync with the video as well.

Does anybody know how to make this box play video content consistently using the hw decoding instead of pegging the cpu?  It's clear that the box is struggling to do the software decoding, not to mention it gets much hotter (and the fan runs more loudly to compensate).

---

### Post by nickrout on 2011-05-03
> **rbroberg said:**
> I upgraded to mythbuntu/11.04 last week, with an out of the box installation on a zotac zbox HD-ID11 front end (backend is mythbuntu/11.04 as well).  Connection from zbox to home theatre is via hdmi cable.  The zbox is a dual-core 1.6Ghz atom with the next-generation ion (512M onboard) nvidia.  Audio configuration is set to the nvidia hw option (equivalent to the hwplug1,7 in mythtv/0.24), with 5.1 specified as output.

I'm having an issue where, regardless of the playback profile which I choose, many (most!) of the content I play seems to be using the cpu for decoding rather than the hw.  This can been seen by watching the cpu used by the box - when watching videos with lower resolution than 720p, the cpu goes up to 48-52% (mythfrontend using the cycles).  When watching videos which are 720p, the hw decoding is definitely happening, as the cpu is around 4-6%.

All of my recorded content (hd homerun), SD and HD, are playing back pegging the cpu as well.

I've changed my playback profiles (and tried many of them, including all of the vdpau ones) but the behavior is unchanged.  I've examined the output from 'mythfrontend -v playback' and the messages make it look like it's using vdpau.

What's more is that the audio quickly becomes 160ms-200ms out of sync with the video as well.

Does anybody know how to make this box play video content consistently using the hw decoding instead of pegging the cpu?  It's clear that the box is struggling to do the software decoding, not to mention it gets much hotter (and the fan runs more loudly to compensate).

what codec is the sd material encoded in. you can use ffmpeg -i filename or mediainfo filename to determine that. (ffmpeg should be installed already, mediainfo requires adding a repo and installing, but gives much more informative output)

vdpau will only assist with mpeg2 and h264 material, unless your GPU supports 'Feature Set 3' (what is the output of lspci?)

---

### Post by LowSky on 2011-05-03
check the version of playback profile you are using... vdpau might not be enabled if you are not using the correct VDPAU profile.

---

### Post by nickrout on 2011-05-03
> **LowSky said:**
> check the version of playback profile you are using... vdpau might not be enabled if you are not using the correct VDPAU profile.

I think if 720p material is playing back with 4-6% cpu, vdpau must be working.

Also original poster, are these 'recordings' or 'videos' you are watching?

---

### Post by rbroberg on 2011-05-03
> **nickrout said:**
> what codec is the sd material encoded in. you can use ffmpeg -i filename or mediainfo filename to determine that. (ffmpeg should be installed already, mediainfo requires adding a repo and installing, but gives much more informative output)

vdpau will only assist with mpeg2 and h264 material, unless your GPU supports 'Feature Set 3' (what is the output of lspci?)


Output of lspci is:
03:00.0 VGA compatible controller: nVidia Corporation GT218 [ION] (rev a2)

According to the wikipedia page on nvidia, the GT218 supports 'Feature Set C'.

The video which plays using vdpau is encoded with h264; the one which uses the cpu is encoded with mpeg4; the wikipedia page says 'Feature Set C' supports 'mpeg4-4 part 2'
(output from 'ffmpeg -i')
    Stream #0.0: Video: mpeg4, yuv420p, 624x352 [PAR 1:1 DAR 39:22], 23.98 tbr, 23.98 tbn, 23.98 tbc

---

### Post by rbroberg on 2011-05-03
> **LowSky said:**
> check the version of playback profile you are using... vdpau might not be enabled if you are not using the correct VDPAU profile.

I've tried all of the profiles which have VDPAU in them - vdpau is definitely enabled, as it is clearly happening for some of the content I'm watching - just not for all of it.  That's what's strange

---

### Post by rbroberg on 2011-05-03
> **nickrout said:**
> I think if 720p material is playing back with 4-6% cpu, vdpau must be working.

Also original poster, are these 'recordings' or 'videos' you are watching?

Correct - the issue is that with 720p source content, vdpau is definitely working - but it's not working for all other content, be it videos or recordings.  As mentioned, all of my recordings (SD and HD) are pegging the cpu; only my 720p videos do *not* peg my cpu.

---

### Post by nickrout on 2011-05-03
Sorry I said Feature set '3', but I meant 'C'.

I can olny suggest looking hard at your frontend logs, with playback logging enabled.

---

