---
title: "How I solved the background noise problem when recording audio/videos"
date: 2013-06-13
forum: Multimedia Software
---

### Post by davidongo on 2013-06-13
Hi, folks. 



So, getting into audio recording in Ubuntu, many people say that "I thought that my background noise when recording audio was due to the microphone, but I booted to Windows, and it records well"... I also fell in that trap, and it is due to the fact that WINDOWS HAS A BACGROUND NOISE REMOVAL OPTION in the audio settins for microphone. If you go to you Windows 7, for example, and go to menu->run, and write the command "control mmsys.cpl", you will load the audio settings. If you go to Record tab-> Microphone->and click on properties button, there must be a tab which says something like "enhancements" or something like that (in my Spanish Windows version the tab says "mejoras"). You will see that the option of "noise removal" (or something like that, in Spanish it is "supresión de ruidos"), it is checked. If you UNCHECK and then use Audacity, you will probably **THE SAME BACKGROUND NOISE THAT YOU HAD IN UBUNTU.**
So yeah, this was a trap for my diagnosis, and I understood what someone already said in another forum, several years ago: more frequently than one thinks, the background  problem is due to a bad microphone. You can try out the background recorded by an well-working internal microphone, and compare it with the background of your faulty external microphone, which sounds like statics. And learn to distinguish those two DIFFERENT NATURE OF BACKGROUNDS, and react upon this.

So, the problem is that, by default, Ubuntu has no noise removal. Somebody will say, "use the Audacity Noise Removal Tool". Yeah, man, if my hour costs half a dolar, maybe, but this is not an option for busy people, and besides the noise removal of Audacity is NOT half as good as the noise removal by default that Windows has, and that Ubuntu should have or maybe has but is not checked by default. It is better to have GREAT sound, don't accept a background noise in your recordings.

If you want to save a screencast, here's a bonus of this forum thread for a tip: 

**avconv -f alsa -ar 22050 -i default -f x11grab -s 1280X800 -r 10   -i :0 -acodec adpcm_swf  output.flv**

The codec parameter is because after I installed libavcodec and libmp3lame, the alsa recording defaulted to libmp3lame, but the avconv CAN'T RECORD FOR LONG AN FLV VIDEO WITH AUDIO ENCODED TO MP3, BECAUSE IT SAYS "SEGMENTATION FAULT". The other codec, adpcm_swf, does work better for this purpose. You can latter play with the screensize or the framerate, if you want a lighter file.

Ok, 
Best regards, I hope someone will find this useful in the future, and save him/her lots of days trying to figure this out, as it occurred to me.
David L.



------------------------------------
** *Remark for moderators only****: Unfortunately, the threads that helped me out to solve my problem were  already closed and were more than 4 or 5 years old, so I couldn't post  there for other people this solution. It's a shame that Ubuntuforums, based on VBulletin, closes threads only for being "older" or "inactive". If you, reader, are a moderator,  simply read on and save for yourself your comments of "forum rules". This thread is for  helping people, so either contribute or shut up.*

---

