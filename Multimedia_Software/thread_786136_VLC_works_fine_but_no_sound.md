---
title: "VLC works fine but no sound"
date: 2008-05-07
forum: Multimedia Software
---

### Post by JonahBird on 2008-05-07
[**SOLVED**
This should have been in the absolute beginners section. I feel like such a jerk. sorry for wasting yuor time. 
(I thought that removing and reinstalling VLC would return everything to the default setting, but nope that has to be done in the settings menu) 


if anyone can help it would be much appreciated. 
VLC cannot play sound. it all started a few weeks ago when I had a friend staying with me and messing with my computer, 
when I play anything the default audio track is Disabled. When I switch to track 1 it acts normal but no sound comes out, in the message panel I get the following warning:

main debug: control type=17
main debug: looking for decoder module: 25 candidates
main debug: using decoder module "mpeg_audio"
main debug: thread 2994908048 (decoder) created at priority 0 (input/decoder.c:159)
mpeg_audio debug: MPGA channels:2 samplerate:44100 bitrate:128
main debug: looking for audio output module: 6 candidates
main debug: using audio output module "aout_file"
main debug: output 's16l' 44100 Hz Stereo frame=1 samples/4 bytes
main debug: mixer 'fl32' 44100 Hz Stereo frame=1 samples/8 bytes
main debug: filter(s) 'fl32'->'s16l' 44100 Hz->44100 Hz Stereo->Stereo
main debug: looking for audio filter module: 24 candidates
main debug: using audio filter module "float32tos16"
main debug: found a filter for the whole conversion
main debug: looking for audio mixer module: 3 candidates
main debug: using audio mixer module "float32_mixer"
main debug: input 'mpga' 44100 Hz Stereo frame=1152 samples/1053 bytes
main debug: looking for audio filter module: 1 candidate
[COLOR="RoyalBlue"]normvol warning: bad input or output format
main warning: no audio filter module matching "volnorm" could be loaded[/COLOR]
main debug: looking for audio filter module: 1 candidate
main debug: using audio filter module "normvol"
main debug: filter(s) 'mpga'->'fl32' 44100 Hz->44100 Hz Stereo->Stereo
main debug: looking for audio filter module: 24 candidates
main debug: using audio filter module "mpgatofixed32"
main debug: found a filter for the whole conversion
main debug: filter(s) 'fl32'->'fl32' 48510 Hz->44100 Hz Stereo->Stereo
main debug: looking for audio filter module: 24 candidates
main debug: using audio filter module "bandlimited_resampler"
main debug: found a filter for the whole conversion
[COLOR="RoyalBlue"]mpgatofixed32 debug: libmad error: bad main_data_begin pointer
mpgatofixed32 debug: libmad error: bad main_data_begin pointer
[/COLOR]

Movie player, Gxine, Rythmbox, realplayer, sound juicer all play sound fine. 
 
any Ideas? what does it all mean? will I ever get my beloved VLC media player to work? 

thank you

---

