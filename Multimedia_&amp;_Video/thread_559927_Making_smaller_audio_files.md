---
title: "Making smaller audio files??"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by Ganda_Melga on 2007-09-25
So, here's the thing. Wanted do pass one cd track to the HD in wav format. In gxine I couldn't do it. Nor in VLC.  Nor in real media player. They open the cd and play it, but i found no ripping option.

Add/remove programs and installed the The SoindJuicer Cd ripper. Ah... It ripped the file to HD and with very good quality. But 25 megas??? I need this file to be small even if the sound quality is low.

Also downloaded Audacity, but didn't managed to convert the file to a smaller size.


How on earth can I do this? Any help will be wellcomed. Thanks a lot.

---

### Post by rsambuca on 2007-09-25
I am not positive what you are talking about, but I assume you want to take an audio CD and create mp3's?  Sound Juicer can do this directly, or if you already have ripped it to .wav format, audacity can convert it into an mp3.

---

### Post by Carl H on 2007-09-26
wav files are always going to be reasonably big files, and I'm not sure that the compression can be varied to make them smaller. 

Are you sure you don't want mp3 files? Bit confused about what you're actually trying to do, tbh.

---

### Post by Lord Illidan on 2007-09-26
I think you want an mp3, not a wave file...

---

### Post by ryno519 on 2007-09-26
Sound juicer could rip them directly to the ogg format (shame on you mp3 pushers :P). They are comparable in quality and size to mp3's and use an open format. Alternatively, if you want cd quality copies you could use flac (also available in soundjuicers config) which will be fairly large in size, but not as large as the wav.

---

### Post by wrathkeg on 2007-09-26
> **Ganda_Melga said:**
> 

Add/remove programs and installed the The SoindJuicer Cd ripper. Ah... It ripped the file to HD and with very good quality. But 25 megas??? I need this file to be small even if the sound quality is low.

Also downloaded Audacity, but didn't managed to convert the file to a smaller size.



If you open the file in Audacity, you can change the sample rate, and then save the file:  this will reduce the file size, but also the quality.  Here's how: open the file in Audacity, click on "project rate" in the lower left corner, and pick another number.  You probably have 44100 in there now.  I would select lower numbers one by one, and have a listen.  Like I say, there will be a pretty obvious decrease in quality when you listen to the playback.

Another thing which would lower the file size would be converting from stereo to mono (assuming that it is currently stereo, and that you don't care about it being mono...).  That would halve the file size right there.

[http://www.julianyap.com/wiki/Convert_Stereo_to_Mono_with_Audacity](http://www.julianyap.com/wiki/Convert_Stereo_to_Mono_with_Audacity)

---

### Post by Ganda_Melga on 2007-09-26
Right. What I am trying to do is the following.

A lady friend of mine has a blog with poetry and musics and nice images, etc...

She would like to place "Adagio from Albinoni" as the background music for one of the poetries. Problem is the blog only allows wave files (I suppose these are the same as WAV), and of a low dimension. I Have the original cd. So I need to rip that track from cd, save it in the form of a wave file, and as small as possible. In Windows it's possible to do this with Wimamp. But I would like to do it in linux and not have to go back to windows.

I'll try to follow wrathkeg advice, it seems sensible.

Anyone else has any other ideias?

Thanks a lot for all your support. :popcorn:

---

### Post by rsambuca on 2007-09-26
What blog site is hosting it?  I haven't seen any that limit audio files to .wav files!

---

### Post by Lord Illidan on 2007-09-26
Indeed, limiting to wav files would be a very stupid option, when mp3 is a fraction of the size, at the same bitrate!

---

### Post by mjitkop on 2007-09-26
As others suggested, you can use Soundjuicer to rip the track from your CD into a WAV file. Most likely you will get a stereo WAV file with a sample frequency of 44100 Hz (or 44.1 kHz). 

My suggestion is to open this WAV file in Audacity and do 2 things:
1/ Change the sample frequency down to 22050 Hz
2/ Save it as a mono file, not stereo.

This should give you a WAV file that is one quarter of the original one.

Unfortunately I cannot describe to you what you should do in Audacity to do all this.

Depending on the quality and the size of the file that you can tolerate, it may be good enough (and better quality) to just make a mono file from the original (half the size). What is the maximum size you can use?
There is quite an easy rule to figure out the size of a WAV file: about 10 MB for 1 minute of stereo sound, therefore 5 MB for 1 minute of mono sound. This assumes that the sample frequency is 44100 Hz. Somebody will correct me if I'm wrong. ;-)

---

### Post by HermanAB on 2007-09-26
Hmm, most machines have MP3 capability installed, so you could compress the audio with lame and pretty much everybody on the planet should be able to play it in a browser.

---

### Post by wrathkeg on 2007-09-26
> **Ganda_Melga said:**
> 
Anyone else has any other ideias?

I don't think you need any: what I suggested uses the tools you have available to do the job you asked about! But post back if what I suggested doesn't work for some reason.

---

### Post by Ganda_Melga on 2007-09-30
I tried, and tried, and tried, but in the end the smaller file I could get was 9,7 mega with a lousy sound quality.

Had to go back to windows. Ripped the cd track with windows media player, and then compressed it with Winamp. The resulting file was 1,9 mega with a decente sound quality. It's a shame I was unable to do it under linux. My fault, I suppose.

Anyway, many thanks to those who came foward to help! :popcorn:

---

### Post by rsambuca on 2007-09-30
Sounds like an EBKAC.

---

