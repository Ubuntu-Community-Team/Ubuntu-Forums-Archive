---
title: "Brasero – Error message when trying to burn audio CD"
date: 2010-08-20
forum: Multimedia Software
---

### Post by guraknugen on 2010-08-20
This happens every time I try to burn an audio CD – burning data CD seems to work fine.

I open Brasero, click Audio project, drag a couple of FLAC files into it and try to burn, or in this particular case, create an image.

A dialogue pops up where I am supposed to tell it where to put the image. I click Desktop but I don't change the file name (something like ”brasero.cue” or whatever).

Then it starts doing things but after a short while I get an error message and I am asked to save the log file, which I did and here it is:

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
BraseroNormalize called brasero_job_get_action
BraseroNormalize called brasero_job_get_action
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_action
BraseroNormalize called brasero_job_get_session_output_size
BraseroNormalize Output set (AUDIO) image = /tmp/brasero_tmp_MP6MHV.cdr
BraseroNormalize called brasero_job_get_session_output_size
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_tag_lookup
BraseroNormalize Analysing track file:///home/guraknugen/Eget/Projekt/Musik/Johnny%20Rosenberg/2.%20Johnny%20Guitar/Ljudfiler/P%C3%A5g%C3%A5ende/Nagasaki%20Memories%20(%E9%95%B7%E5%B4%8E%E6%85%95%E6%83%85)/Nagasaki%20Memories%20(%E9%95%B7%E5%B4%8E%E6%85%95%E6%83%85)%20-%20Variant%201.flac
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_set_current_action
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1,000000) and gain (-3,530000)
BraseroNormalize called brasero_job_tag_lookup
BraseroNormalize Analysing track file:///home/guraknugen/Eget/Projekt/Musik/Johnny%20Rosenberg/2.%20Johnny%20Guitar/Ljudfiler/P%C3%A5g%C3%A5ende/Love%20Theme%20from%20The%20Godfather/Love%20Theme%20from%20The%20Godfather.flac
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1,000000) and gain (-5,250000)
BraseroNormalize called brasero_job_tag_lookup
BraseroNormalize Analysing track file:///home/guraknugen/Eget/Projekt/Musik/Johnny%20Rosenberg/2.%20Johnny%20Guitar/Ljudfiler/Mastrat%20med%20MTK/16-bits%20f%C3%B6rlustfri/Diamond%20Head.flac
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (0,984772) and gain (-3,570000)
BraseroNormalize called brasero_job_tag_lookup
BraseroNormalize Analysing track file:///home/guraknugen/Eget/Projekt/Musik/Johnny%20Rosenberg/2.%20Johnny%20Guitar/Ljudfiler/P%C3%A5g%C3%A5ende/JR%20CR1/JR%20CR1%2020100307.flac
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize gstflacdec.c(1082): gst_flac_dec_loop (): /GstPipeline:pipeline12/GstDecodeBin:decodebin12/GstFlacDec:flacdec10:
stream stopped, reason not-negotiated
BraseroNormalize called brasero_job_error
BraseroNormalize finished with an error
BraseroNormalize asked to stop because of an error
	error		= 1
	message	= "Internt fel i dataström."
BraseroNormalize stopping
Session error : Internt fel i dataström. (brasero_burn_record brasero-burn.c:2839)
```

I use Ubuntu 10.04 and the Brasero version from the usual repositories, seems to be 2.30.2.

Oh… and I see there is at least one error message in that log file is Swedish, so I guess I have to translate it for you:
”Internt fel i dataström” means something like ”Internal error in data stream”.

And I know my FLAC files are OK; I play them all the time with Totem without any problems. Some of them are 24 bits at 44.1 kHz and some of them are 16 bits at 44.1 kHz. They were converted with Sound Converter 1.4.4 from a 24 bit WAV original.

---

### Post by lykeion on 2010-08-20
Not really a fix, but have you tried disabling the Normalize plugin?
In older versions of brasero (jaunty) there were problems with it:

[https://bugs.launchpad.net/brasero/+bug/374101](https://bugs.launchpad.net/brasero/+bug/374101)

---

### Post by guraknugen on 2010-08-20
> **lykeion said:**
> Not really a fix, but have you tried disabling the Normalize plugin?
In older versions of brasero (jaunty) there were problems with it:

[https://bugs.launchpad.net/brasero/+bug/374101](https://bugs.launchpad.net/brasero/+bug/374101)

No, I didn't try that, so I did now. The problem persists and here is the new log:

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode deactivating
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_HAXDHV.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 182062222222 / bytes = 0 32115776
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_tag_lookup
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode New pad
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set volume level 0,000000 0,000000
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/guraknugen/Eget/Projekt/Musik/Johnny Rosenberg/2. Johnny Guitar/Ljudfiler/Pågående/JR RS1/JR RS1 20100819.flac to /tmp/brasero_tmp_HAXDHV.cdr
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode gstflacdec.c(1082): gst_flac_dec_loop (): /GstPipeline:pipeline5/GstDecodeBin:decodebin5/GstFlacDec:flacdec5:
stream stopped, reason not-negotiated
BraseroTranscode called brasero_job_error
BraseroTranscode finished with an error
BraseroTranscode asked to stop because of an error
	error		= 1
	message	= "Internt fel i dataström."
BraseroTranscode stopping
Session error : Internt fel i dataström. (brasero_burn_record brasero-burn.c:2839)
```

This time I tried to burn one file only, still as an audio CD image. Here's the data of the file:
FLAC
Stereo
44.1 kHz
24 bits
Playing time: 3:02

Anyone who happen to know of any limits when burning audio projects? Am I not supposed to use FLAC files? Do I first have to convert to 16 bits? Other things that comes to mind?

Another thing I noticed was that when I right click a file in Brasero's play list area and click &#8221;Edit information&#8230;&#8221;, the composer field is empty, which is not the case when opening the file with EasyTag &#8211; a tag editor for audio files which can easily be found and installed from Ubuntu software center, by the way.

---

### Post by lykeion on 2010-08-20
I will try burn flac files (16 and 24 bit depth) with brasero and see what I come up with, and post my results here tomorrow.

---

### Post by guraknugen on 2010-08-20
> **lykeion said:**
> I will try burn flac files (16 and 24 bit depth) with brasero and see what I come up with, and post my results here tomorrow.

Okay, thanks. I will be away for vacation so I won't be able to follow this for a couple of days, but I will do some tests too when I get back.

---

### Post by tommcd on 2010-08-20
Before you go away for vacation, try installing **gnomebaker** and see if you can burn an audio CD with that. 
Gnomebaker has worked much better than Brasero in my experience. You could also try **xfburn**. But try gnomebaker first.

---

### Post by guraknugen on 2010-08-21
> **tommcd said:**
> Before you go away for vacation, try installing **gnomebaker** and see if you can burn an audio CD with that. 
Gnomebaker has worked much better than Brasero in my experience. You could also try **xfburn**. But try gnomebaker first.

Tried Gnomebaker now and it works, but I don't like it… But yes, it works.
Burned to a CD-RW (only one track) since I found no option for burning to an image file (there is an option for that somewhere, right?). The funny thing is that when I played the CD with Rhythmbox, the title of the song was ”On the road again” with ”Fuel” which I found a bit strange since I recorded it myself (I am some kind of a multi instrumentalist or whatever to call it)…

Well, got to go now, see you in a couple of days.

And thanks for helping.

---

### Post by lykeion on 2010-08-21
Ok, now I have tested burning an Audio CD image of FLAC files with Brasero. 
16-bit FLAC files burned ok, but I got the same error as you did when trying with 24-bit FLAC files.
I don't know if that has anything to do with the 16-bit limitation of Audio CD, 
but in my mind Brasero should convert to 16-bit automatically and not halt with an error.
Anyway, simple solution would be to convert your audio files to 16-bit FLAC with sox/audacity/other before adding them to Brasero.

---

### Post by guraknugen on 2010-08-24
> **lykeion said:**
> Ok, now I have tested burning an Audio CD image of FLAC files with Brasero. 
16-bit FLAC files burned ok, but I got the same error as you did when trying with 24-bit FLAC files.
I don't know if that has anything to do with the 16-bit limitation of Audio CD, 
but in my mind Brasero should convert to 16-bit automatically and not halt with an error.
Anyway, simple solution would be to convert your audio files to 16-bit FLAC with sox/audacity/other before adding them to Brasero.

Thanks for testing this!

Even though I didn't like Gnomebaker, it did the job, so I think that's an even easier solution, at least the few times I need to burn an audio CD (I never use anything else.

One thing that impressed me a little when I skipped Windows for Ubuntu 7.04 in summer 2007 was that I didn't need to convert my 24-bit files (WAV back then, FLAC these days) before burning them. Back then I used the burning software that was included in the distro, but I can not right now remember which one it was. Maybe it was Gnomebaker after all… So it's a bit disappointing that Brasero doesn't seem to be able to do this at all.

I guess a good thing to do is to report this as a bug to the Brasero project, which is what I intend to do, if no one already did. Meanwhile I will use Brasero and Gnomebaker, depending on what I want to do.

[Here's my bug report]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/623558")

---

### Post by tommcd on 2010-08-25
> **guraknugen said:**
> Back then I used the burning software that was included in the distro, but I can not right now remember which one it was. Maybe it was Gnomebaker after all… 
Gnomebaker was indeed at one time the default CD burning tool that was included with a standard Ubuntu install. At some point they switched to Brasero. I think Ubuntu 7.04 may have still used Gnomebaker; but I am not sure to be honest.

---

### Post by guraknugen on 2010-08-26
> **tommcd said:**
> Gnomebaker was indeed at one time the default CD burning tool that was included with a standard Ubuntu install. At some point they switched to Brasero. I think Ubuntu 7.04 may have still used Gnomebaker; but I am not sure to be honest.

I just searched a bit and I found that Brasero was included in Ubuntu by default since 8.04. I guess that means that 7.10 and earlier had Gnomebaker by default. I actually have an Ubuntu 7.10 live CD so if I really want to know I can always start up my computer with it…

---

### Post by eric71 on 2010-09-02
Wish I had seen this thread earlier. I was very frustrated when I couldn't burn an audio cd this morning. After having some coffee after going to work I realized that the only difference between the current project and recent successful burns was that one song was a 24 bit flac. I had always burned combinations of ogg, mp3 and 16 bit flac with no problems. This thread seems to confirm my suspicion that Brasero chokes on 24 bit flac files. I'm not sure why this would be - Totem plays them just fine, and as far as I know Brasero is using the same gstreamer backend. I'll know better next time, and if I can confirm this I'll file a bug.

edit: just noticed that guraknugen already filed the bug. I need more coffee.

---

