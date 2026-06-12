---
title: "Smplayer Alsa &amp; Pulse Audio Problem - Help"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by mat_london on 2008-01-05
Hi,

I've downloaded the Ubuntu deb of the latest version of Smplayer from their site and also built it from source. 
If I select Alsa as my sound in the preferences section I get no sound, I can only get sound using OSS.

When I check the logs in mplayer I get this:

Smplayer is issuing this command 

mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo x11 -ao alsa -zoom -nokeepaspect -framedrop -dr -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 62914574 -colorkey 131586 -monitoraspect 1.33333 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -aid 1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -ss 888 -osdlevel 0 -vf-add pp -autoq 6 -vf-add expand=osd=1 -noslices -vf-add screenshot -channels 2 /home/mat/some-video.avi

Sound fails on this:

ID_VIDEO_CODEC=ffodivx
[PP] Using external postprocessing filter, max q = 6.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
***** PULSEAUDIO:** Unable to connect: Connection refused
[AO_ALSA] Playback open error: Connection refused
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
VDec: vo config request - 480 x 368 (preferred colorspace: Planar YV12)

I'm getting this with all my video files and they all play fine with if I type "mplayer /home/mat/some-video.avi" in the CLI.

I haven't got Pulse Audio installed although I did at one point.

Any ideas ??

Mat

---

### Post by cor2y on 2008-01-05
Check to see if alsa is installed.
alsa-base, alsa-utils, libasound2,libasound2-plugins,pulseaudio.
Then try playback again.
In theory you shouldn't need all these addons but one can never tell.

---

### Post by Lostincyberspace on 2008-01-06
check out this site and see if it will fix your problem it did mine.[URL="http://translate.google.com/translate?hl=en&sl=fr&u=http://forum.ubuntu-fr.org/viewtopic.php%3Fpid%3D1277848&sa=X&oi=translate&resnum=6&ct=result&prev=/search%3Fq%3Dpulseaudio%2Bsmplayer%26hl%3Den%26safe%3Doff%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3DosO%26pwst%3D1"]
http://translate.google.com/translate?hl=en&sl=fr&u=http://forum.ubuntu-fr.org/viewtopic.php%3Fpid%3D1277848&sa=X&oi=translate&resnum=6&ct=result&prev=/search%3Fq%3Dpulseaudio%2Bsmplayer%26hl%3Den%26safe%3Doff%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3DosO%26pwst%3D1[/URL]
Sorry it is in french it is the only place I could find it it should be on the last post. it should be translated.

---

