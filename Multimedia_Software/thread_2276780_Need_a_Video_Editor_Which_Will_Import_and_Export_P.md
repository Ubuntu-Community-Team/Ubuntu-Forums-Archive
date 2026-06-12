---
title: "Need a Video Editor Which Will Import and Export ProRes422 (HQ)"
date: 2015-05-04
forum: Multimedia Software
---

### Post by mark bower on 2015-05-04
Is there an Ubuntu movie editor application that can import ProRes422(SD) or ProRes422(HQ) and then render in the same codecs after editing?  

Openshot works nicely in importing and editing ProRes422 (HQ) & (SD) clips, seems very easy to use.  However, the input is 18 fps but the output becomes 25 fps and appears to be limited to the (SD) codec.  PiTiVi does not work well on any of my different computer systems - generally "stutters" very badly. 

The movie viewers SMPlayer and Videos(aliases Totem,Movie Player) handle ProRes (HQ) & (SD) very nicely on my higher end computer using 15.04.

---

### Post by FakeOutdoorsman on 2015-05-05
Kdenlive can use ffmpeg to export and you can make your own export settings. If you want to export ProRes422 (HQ), then make a setting using a command like this:

```
ffmpeg -i input -c:v prores -profile:v 3 -c:a pcm_s16le output.mov
```
or
```
ffmpeg -i input -c:v prores_ks -profile:v hq -c:a pcm_s16le output.mov
```

---

### Post by mark bower on 2015-05-06
Hope.  I loaded Kdenlive from the Software Ctr onto my Ubuntu 12.04 computer (else I am using 15.04).  Kdenlive did not see my prores (HQ) clips.  It is too late tonite to play with, I will have at it tomorrow.

But a couple of questions:  1) When ffmpeg is run on the cmd line, does it alter or make available additional libraries that Kdenlive looks for?  and 2), I have previously loaded the ffmpeg library via synaptic pkg mgr(SPMgr) - is that a problem or should I removed it via (SPMgr) and then run you suggestions on the cmd line?

---

### Post by FakeOutdoorsman on 2015-05-06
> **mark bower said:**
> Hope.  I loaded Kdenlive from the Software Ctr onto my Ubuntu 12.04 computer (else I am using 15.04).  Kdenlive did not see my prores (HQ) clips.  It is too late tonite to play with, I will have at it tomorrow.
I wasn't sure how it would handle importing the ProRes inputs.

> 1) When ffmpeg is run on the cmd line, does it alter or make available additional libraries that Kdenlive looks for?
Sorry, but I don't really understand this question.

> **mark bower said:**
> and 2), I have previously loaded the ffmpeg library via synaptic pkg mgr(SPMgr) - is that a problem or should I removed it via (SPMgr) and then run you suggestions on the cmd line?

12.04 may still offer the fake "ffmpeg" which is old, buggy, and shouldn't be used. You could possibly get a [static build](http://johnvansickle.com/ffmpeg/) and point Kdenlive to use it for export, but maybe it won't give you that option.

I provided the command line examples for you to make your own Kdenlive export profile if one did not already exist.

---

### Post by mark bower on 2015-05-06
I have never digitally edited movies so everything is new to me.  I played with Kdenlive:  pulled in the ProRes422 (HQ) files, combined a few of them, then rendered to MPEG4.  (A very sophisticated application, not at all simple like Openshot). A good beginning.

What I do not understand is how adding the suggested profiles - pulls in the ProRes codec for export?  Does the ProRes codec reside in some version of ffmpeg?  I am a bit baffled by the fact that the editor can see and manipulate the imported ProRes files, but cannot export(render) them?  But I believe I now understand your "ffmpeg code lines"; one or both are to be added in Kdenlive>Settings>Configure Kdenlive>Transcode>Add Profile.  Is this correct?

So could I trouble you to sequence the steps(and how for the static library if the only way) I should take based on the situation presented?  Employing a static library I believe requires compiling, which I would like to avoid if possible. 

Also, might it be better to use a newer version of Ubuntu to be doing this, say 14.04, or 15.04.  I loaded Kdenlive on my computer with 15.04, it works as experienced with 12.04, and then I loaded a later version of ffmpeg library via synaptic.

---

### Post by FakeOutdoorsman on 2015-05-07
> **mark bower said:**
> Does the ProRes codec reside in some version of ffmpeg?
Yes.

> **mark bower said:**
> One or both are to be added in Kdenlive>Settings>Configure Kdenlive>Transcode>Add Profile.  Is this correct?
Yes. FFmpeg has two ProRes encoders from two different authors. I don't really know the difference. I gave a command for each so you can try them both if you like.

> **mark bower said:**
> Employing a static library I believe requires compiling, which I would like to avoid if possible.
No compiling needed. Either download a static build of ffmpeg, put it wherever you like and then go into Kdenlive and edit "Settings>Configure Kdenlive>Environment>FFmpeg" and change the location to your new build.

Alternatively you could use [mc4man's PPA](https://launchpad.net/~mc3man/+archive/trusty-media) and install ffmpeg from there. I believe the binaries are symlinked to /usr/bin so you won't have to tell Kdenlive where it is, but if you do have to just point Kdenlive to the binaries. Somewhere in "/opt/" (you could also point Kdenlive to ffplay as well since it will be included with the ffmpeg package from this PPA).

> **mark bower said:**
> Also, might it be better to use a newer version of Ubuntu to be doing this, say 14.04, or 15.04.
15.04 contains a relatively recent version of the real ffmpeg from FFmpeg.

---

### Post by mark bower on 2015-05-07
I downloaded the static library ffmpeg-2.6.2 from ffmpeg.org, and extracted it on the Desktop.  I peeked inside and there is folder called libavcodec; inside that folder I see 9 prores files. (With synaptic I also note that the libavcodec-dev folder is present on the computer, but not installed).

I go to Settings>Config Kdenlive>Environment and see "MLT environment tab" > FFmpeg with entry box.  The entry is "/usr/bin/avconv", where avconv is an executable file.  What should my entry be in lieu of "/usr/bin/avconv"?  The other entry boxes include: FFplay,MLT profiles folder,Melt path,Processing threads.

I entered the two code lines at Settings>Config Kdenlive>Transcode>[entered in Parameters box] and Named them Prores1 and Prores2.  I do not see where they show up elsewhere?  For instance, I thot they should show up in Settings>Manage Project Profiles, but they are not there.  Sorry, but I am not familiar with the mechanics of Kdenlive.

Based on digital from super8 film, I believe the output format will become 1440 x 1080p (HQ), but I do not know enuf to specific frame rate, bitrate etc.

---

### Post by FakeOutdoorsman on 2015-05-08
> **mark bower said:**
> I downloaded the static library ffmpeg-2.6.2 from ffmpeg.org, and extracted it on the Desktop.  I peeked inside and there is folder called libavcodec; inside that folder I see 9 prores files. (With synaptic I also note that the libavcodec-dev folder is present on the computer, but not installed).

Sounds like you downloaded the source code instead of a compiled binary from here:
[http://johnvansickle.com/ffmpeg/](http://johnvansickle.com/ffmpeg/)

Once you download and extract it you'll get a "ffmpeg" file that you can point Kdenlive to. So if it is located at "/home/mark/ffmpeg" that's what you replace "/usr/bin/avconv" with.

> **mark bower said:**
> I entered the two code lines at Settings>Config Kdenlive>Transcode>[entered in Parameters box] and Named them Prores1 and Prores2.  I do not see where they show up elsewhere?  For instance, I thot they should show up in Settings>Manage Project Profiles, but they are not there.  Sorry, but I am not familiar with the mechanics of Kdenlive.
I'm not sure. I'll take a look tomorrow if I get a chance.

> **mark bower said:**
> Based on digital from super8 film, I believe the output format will become 1440 x 1080p (HQ), but I do not know enuf to specific frame rate, bitrate etc.
I'm not familiar enough with Kdenlive to know what it will do, but ffmpeg attempts to preserve the size, frame rate, metadata and other stuff unless you tell it otherwise or if the output format requires changes.

I usually don't bother changing parameters unless I need to, but it really depends on how the output is going to be used/viewed.

---

### Post by mark bower on 2015-05-08
Status:  I now have the library "ffmpeg-2.6.2-32bit-static" downloaded, extracted on the Desktop, and pointed to in the MLT Environment tab.  And the code lines you supplied are entered and shown in the Transcode page, again with names of Prores1 and Prores2.

For discussion purposes:  I have two clips on the Video1 line, and have not set up a project(maybe this is the problem, but I was able to render a MPEG-4 file without having opened a project).

Now I go to the Rendering page (pop-up):  Destination is set to "File Rendering".  If I open Destination options I can select "Lossless/HQ" which seems like what I want for prores.  The Lossless/HQ selection sets the Output file to .../kdenlive/untitled.mkv.  And a profiles column shows eg "FFV1 lossless (video) + PCM (sound)".  I do not see Preres1 or Prores2 as options.  I do see them if I go to Project>Transcode, but could not get anywhere messing around with Rendering options?

[B]What can I do next to get Kdenlive to render in Prores?
[/B]

---

### Post by mark bower on 2015-05-11
Bumped for more help please.

---

### Post by FakeOutdoorsman on 2015-05-13
Looks like Kdenlive render profiles have changed since I looked at it years ago. Here's what I did to make it work:

[list=1]
[*]Click *Render* button.
[*]Choose *Destination: Lossless / HQ*.
[*]Click the *S* button to create a new profile.
[*]You can refer to the screenshot for what parameters to enter. (There is a typo, use mov instead of mp4 under *Extension*).
[*]Save and render.
[/list]

I don't know why it will place the new profile under it's own group [s]or why it attempts to give it mp4 extension when you "render"[/s].

The Transcode profiles are for something else entirely. It allows you to right click on a file you imported and re-encode it.

[ATTACH=CONFIG]261964[/ATTACH]

---

### Post by mark bower on 2015-05-13
It did not work.  I am going to do the below so that only the detailed changes are made; it may be easier to determine the problem if there is one.  Please correct my steps if I missed something.

1) Uninstall and reinstall Kdenlive(from Ubu Software Ctr) so I have a fresh new copy with no unintended alterations.
2) Add your 2 code lines given in post #7 at Kdenlive>Settings>Configure Kdenlive>Transcode>[Parameters block] and call them Prores1 and Prores2 respectively
3) Point to the ffmpeg static library on my desktop(renamed from download to ("ffmpeg") in Settings>Configure>Environment>MLT tab>[in the FFmpeg block].  The downloaded library from [http://johnvansickle.com/ffmpeg/](http://johnvansickle.com/ffmpeg/) is "ffmpeg-2.6.2-32bit-static", my computer is 32 bit.
4) Follow the 5 steps you gave in the previous post
5) Report back results

---

### Post by FakeOutdoorsman on 2015-05-14
You don't need to do step 2. The transcode stuff is so you can convert imported clips, not for encoding your final, edited movie.

It seems like a video would be the best way to show how to do this, but I won't be able to make one for a few days at least.

---

### Post by mark bower on 2015-05-14
It did not work.  I omitted entering the code lines, but completed the other steps.

1st - I open two clips with the Add Clip button, then move them to the Video 1 line.  [The clips I used (streetcar.mov and fiddle.mov) come from [http://www.mymovietransfer.com/2012_1080p_Pricing.html](http://www.mymovietransfer.com/2012_1080p_Pricing.html).  The clips are had by rt clicking on the images, then selecting "Save Link As", click Save to download.  These clips are the codec flavor Prores422(SD) and are of the form I will receive from MyMovieTransfer.com when my movies are digitized.]

2nd - I open the Rendering pop-up by clicking on the Render button.  
Destination reads:  File rendering
Output file reads:  home/rocky/kdenlive/untitled.m2t

3rd - I change 
Destination to read:  Lossless/HQ
Output file now reads:  home/rocky/kdenlive/untitled.mkv

4th - I click the "Create new profile" button (which looks like a sheet of paper with a "+" sign on it and
Destination reads:  Lossless/HQ
Group reads:  Lossless HQ
Profile name:  entered "Hope1"
Extension:  entered mov in lieu of mkv
click the OK button
click Render to File button

5th - resulting message in pop-up after clicking the Render to File button:
"/home/rocky/kdenlive/untitled.mov
Rendering finished in 00:00:00
Video without audio track"
I go to ~/kdenlive and see "untitled.mov", 565 bytes, obviously no digital clip?

I should probably state again, the Prores clips play just fine in Kdenlive (as well as Openshot); I just cannot render(save) HQ to HQ, and both HQ and SD appear to render as SD and only at 25 fps, not the 16 fps input.

---

### Post by mark bower on 2015-05-22
Well, still hoping for some help.  Simply put, I want to import prores422(HQ) and prores422(SD) files, edit them, then render (export) in the exact same format as received.  This means HQ to HQ, SD to SD, and holding to 16 fps.

How is this done in Openshot, Kdenlive, or some other movie editor.

---

### Post by FakeOutdoorsman on 2015-05-26
[Here's a video](http://avmule.com/kdenlive_prores.mp4).

First you have to make a Project Profile with a suitable frame rate for your videos: *Settings > Manage Project Profiles*. My Kdenlive wouldn't let me save it due to a [bug](https://bugs.kde.org/show_bug.cgi?id=347822) (it has been fixed upstream). You can click "Use as default" when you're done. Then somehow you'll have to apply the new Project Profile to your current project if the "Use as default" button doesn't do it.

Then make your Render Profile. You can ignore the part where I'm floundering around after clicking "copy profile to favorites" (duh...where did it go?).

---

### Post by mark bower on 2015-05-28
I have learned a lot this past week.  I now realize that the 18fps from super8 mm will not remain at 18fps when going to digital video.  The frames and rate will likely encode to either MPEG-2/H.262 or MPEG-4/H.264, and 23.98 vs 29.98fps.  I have googled this topic a lot and do not get clarity.  I will be showing the resultant video: 1) at HD 1080 from a computer, 2) probably make DVDs of the video, and 3) and may generate a Blu-ray disc. [Actually this involves videos, approx 4,000' of home super 8mm.

Openshot appears to fill the need with respect to prores422 (SD); I might not work with the (HQ) flavor.  I am at the first stages of trying formats on the TV that appear to run at the correct rate, but some difficulties with "stuttering".  

I should have the time to look at your effort wrt Kdenlive over the next few days.  I will attempt to understand what you have done and report back within a few days.  There are just so many variables to deal with, and I am only a novice.

---

### Post by mark bower on 2015-06-01
O.K.  Your video was a big help - followed exactly(except included two files) - trying to talk thru step by step would have been impossible.  I obtained a rendered file of "fiddle" and "streetcar" combined which has the characteristics (as seen by SMPlayer) of a prores HQ file:  182MB,apch,116170kbps,16fps,ffprores(file size,format,bitrate,fps,selected codec respectively) - WOW.  

Now some questions:
1) So Kdenlive has ProRes imbedded in it somewhere?
2) If receive my files as prores422 (SD) instead of HD, can I substitute in your video example SD for HQ and leave all else the same?
3) And for 18fps, what might the entries be for frame rate (you used 16043/1001 for 16fps)?
4) For "properties=lossless/ProRes vprofile=3 movflags=+write_colr", what is the origin for the content of this line, what do the entries mean?
5) Why did you select the line "Lossless HuffYUV + FLAC"?  What does it mean or stand for? 

I'll look for your response; I may not be back for about 3 - 4 weeks, the time to get my first film processed to digital.  I will return.

mark

---

### Post by FakeOutdoorsman on 2015-06-01
> 1) So Kdenlive has ProRes imbedded in it somewhere?
I don't know about the decoding/playback. I think it uses the ffmpeg binary for encoding the output, and ffmpeg has ProRes de/encoding support.

> 2) If receive my files as prores422 (SD) instead of HD, can I substitute in your video example SD for HQ and leave all else the same?
If the size is different than 1920x1080, then you'll have to change that.

> 3) And for 18fps, what might the entries be for frame rate (you used 16043/1001 for 16fps)?
With ffmpeg, if you wanted to preserve the same frame rate you don't need to do anything, but I believe Kdenlive will explicitly set a frame rate as defined in the encoding profile. You said you wanted to preserve the frame rate, so I first looked at the input file with ffmpeg. It said the frame rate is an oddball 16.03, but that is a rounded figure. The actual frame rate is 16.026973027, or 16043/1001 as shown with this long ffprobe command:

```
$ ffprobe -v error -select_streams v:0 -show_entries stream=avg_frame_rate -of default=noprint_wrappers=1:nokey=1 1080p_fiddle.mov
16043/1001
```

However, after all of that, it probably won't matter if you want to use a standard frame rate, such as 24 (or 24/1 in Kdenlive-ese). ffmpeg will simply duplicate frames, and being an old film transfer, it probably won't look much different, and it will be a standard frame rate for blu-ray (I think you mentioned that somewhere). Additionally, you won't have to probe each input and change to a weird frame rate. I'm guessing the transfers result in such an odd frame rate because maybe the film is being played/scanned at that rate to make the timing look normal and perhaps each one is different and is subjectively adjusted. That's my guess at least.

**So forget all of that crap and use 24/1.**

> 4) For "properties=lossless/ProRes vprofile=3 movflags=+write_colr", what is the origin for the content of this line, what do the entries mean?
Back in the day Kdenlive render profiles mostly looked like a ffmpeg command. Now they do this:
[i]Kdenlive now makes use of "property presets" delivered by the melt project (see melt doco). These presets are referenced by the properties=<preset> syntax. In the example illustrated, the render profile is referencing lossless/H.264. This refers to a property preset found in file H.264 found on the system at /usr/share/mlt/presets/consumer/avformat/lossless.

All the <presets> referenced in the render settings in Kdenlive will be referring to presets found at /usr/share/mlt/presets/consumer/avformat/ (on a default install). Note that you reference presets found in subdirectories of this folder using a <dirname>/<profile> syntax as shown in the example above. [/i]
From: [https://userbase.kde.org/Kdenlive/Manual/Project_Menu/Render/Render_Profile_Parameters](https://userbase.kde.org/Kdenlive/Manual/Project_Menu/Render/Render_Profile_Parameters)

I didn't see a ProRes render profile, and the import function didn't seem to work, so I had to make one using this new style that I was ignorant about. The "vprofile=3" sets the ProRes profile to "HQ" as you requested. The "movflags=+write_colr" will add the colr atom which I believe is standard for Apple's ProRes outputs, but for your use it probably won't matter if it is there or not.


> 5) Why did you select the line "Lossless HuffYUV + FLAC"?  What does it mean or stand for?
You can ignore that. That was a result of me flailing around Kdenlive after I clicked "add to favorites" which I never clicked before. I didn't expect it to move my new ProRes profile from the lossless category; I assumed it would copy it to favorites.

---

### Post by mark bower on 2015-06-01
To be clear(I believe I haven't), I will receive my digitized super8 movies back as either ProRes HQ or SD (my choice), and 18fps.  I intend to edit the files, then store as archive at 18fps and SD or HQ(can't make up my mind!).  Then I am planning for 3 outputs from the archive:  display from laptop on TV, generate DVD, generate Blu-ray(maybe).  The ProRes HQ clip I rendered per your video instructions appears to display very nicely on the TV from a laptop at 16fps.  So maybe I'll just make copies of the archive and use for TV viewing(large,large files).  I am lost at this point on options like MPEG-2/h.262, MPEG4/H.264 and fps (which looks like either 24 or 30 will be used) for use with Blu-ray and DVD - which is best to use for my purposes?  But those questions I'll tackle when I start working with my own digitized movies and experience problems with display.

So some follow-up comments/questions per previous 5 questions:
1) I will not try and understand more, if it works, it works.
2) I dug all the way down to /usr .../lossless and looked at the file ProRes.  Great.  I now see if I use "vprofile=2" in "Save Profile - Kdenlive" I will render ProRes(SD).
3) For archiving, I believe I will want to store at 18fps.  The ffprobe CLI cmd works nicely; I have been using SMPlayer to extract the fps.
4) Thanks for explanation
5) Understood

---

### Post by FakeOutdoorsman on 2015-06-01
> SD or HQ (can't make up my mind!)
This may help, from [Apple ProRes White Paper June 2014](https://www.apple.com/final-cut-pro/docs/Apple_ProRes_White_Paper.pdf):
> **Apple ProRes 422 HQ**: A higher-data-rate version of Apple ProRes 422 that preserves visual quality at the same high level as Apple ProRes 4444, but for 4:2:2 image sources. With widespread adoption across the video post-production industry, Apple ProRes 422 HQ offers visually lossless preservation of the highest-quality professional HD video that a single-link HD-SDI signal can carry. This codec supports full-width, 4:2:2 video sources at 10-bit pixel depths, while remaining visually lossless through many generations of decoding and reencoding. The target data rate of Apple ProRes 422 HQ is approximately 220 Mbps at 1920 x 1080 and 29.97 fps.

**Apple ProRes 422 SD**: A high-quality compressed codec offering nearly all the benefits of Apple ProRes 422 HQ, but at 66 percent of the data rate for even better multistream, real-time editing performance. The target data rate of Apple ProRes 422 is approximately 147 Mbps at 1920 x 1080 and 29.97 fps.

Too bad the film transfer guys (most likely) don't give you the choice of FFV1 + FLAC in Matroska. That's what I'd prefer for my own archival stuff instead of the lossy ("visually lossless"), proprietary ProRes.

---

### Post by mark bower on 2015-08-03
My 1st ProRes422HD(HQ) super8mm movie has been digitized.  It really looks nice.  
(Note: FakeOutdoorsman video link at comment #16 is the crux of what enabled Kdenlive to output ProRes HQ)

I now would like to be able to change the digitized frame rate from 24fps (vendor can only do frame to frame @ 24fps) back to the original frame rate = 18fps, and return to the corresponding longer runtime.  Granted, in VLC I can view the digitized 24fps movie at .75X and effectively increase the runtime to 24/18 x (original runtime), or the original runtime equivalent to 18fps.  Using a clip of the movie as an example:  .75 times a 1:00min clip = a 1:20min runtime.  But this is inconvenient - not neat.  And I have many more movies to go. 

In Kdenlive I have rendered a 1min clip in both 24fps and 18fps, 1080p-prores HQ.

Results as seen by VLC, runtime timed with a stopwatch:
24fps:  Frame Rate:  24, Content Bit Rate:  170mb/s, Runtime:  1.0min
18fps:  Frame Rate:  18, Content Bit Rate:  127mb/s, Runtime:  1.0min

This shows a reduction in bits/sec, but not the expected increase in runtime to 1:20min.  (It is not clear to me why the bit rate decreased, but the runtime remains the same).  That is, in going from 24 to 18 frames the runtime the runtime should go from 1 min to about 1:20 min - I can't get Kdenlive to do it?  For each of the renderings, I enter the applicable frame rate in both Settings>Configure Kdenlive>Project Defaults>[24fps or 18fps], and the same frame rate in Settings>Manage Project Profiles>[24fps or 18fps]>clicked "Use as a Default">click O.K.

The transfer vendor used telecine to produce an equivalent 18fps by inserting additional frames for play at 24fps, again not neat for archiving and exceeds the process rate of my computer which causes severe stutter.  

So, is there a way in Kdenlive to render the 24 rate to a true 18fps in Kdenlive??

---

### Post by FakeOutdoorsman on 2015-08-04
I recommend asking the [ffmpeg-user mailing list](http://ffmpeg.org/contact.html). Make sure to show the complete console output of "ffmpeg -i input.mov", and use a [recent build](http://johnvansickle.com/ffmpeg/). Perhaps you can adapt it for Kdenlive, or re-encode it first into a suitable lossless intermediate format (ffv1 for example) then import into Kdenlive.

---

### Post by mark bower on 2015-08-08
Well, I have grown a bit weary on this because of so many complications.  I believe your suggestion is beyond my sanity capability, but thanks for trying to give help.

I tried the vendor's telecined 24fps to 18fps digital file with added blended frames.  With mild motion the appearance becomes blurred as the camera sweeps over small objects - at least small objects are where the blurring seems most noticeable.

So, I believe I am going to have to compromise and play both files and burned discs(DVD,Blu-ray) at .75x via laptop, using apps like VLC and SMPlayer.  While this works for me, it may not work for my children depending on their equipment and software.  Thus it would be neat to be able to burn to an effective 18fps rate.  The Blu-ray player I have does not have a variable speed playback adjustment.  At first search it appears most Blu-ray players do not come with a variable playback speed option.

---

### Post by FakeOutdoorsman on 2015-08-10
> **mark bower said:**
> I believe your suggestion is beyond my sanity capability, but thanks for trying to give help.
You only need to send a message to ffmpeg-user at ffmpeg.org. No need to subscribe to the mailing list: your message will be approved by a moderator usually within 24 hours. Then you can check the [archives](https://lists.ffmpeg.org/pipermail/ffmpeg-user/) for replies (or in the message ask for your email address to be CC'd for replies). To reply to a message in the archives click the email link of the person you are replying to. The link will provide the necessary headers, etc.

> **mark bower said:**
> I tried the vendor's telecined 24fps to 18fps digital file with added blended frames.  With mild motion the appearance becomes blurred as the camera sweeps over small objects - at least small objects are where the blurring seems most noticeable.
Can you provide a short sample that shows the issue? This example will skip the first 30 seconds, and make a 5 second long, [stream copied](https://ffmpeg.org/ffmpeg.html#Stream-copy) output:
```
ffmpeg -ss 30 -i input -t 5 -c copy output.mov
```

---

### Post by mark bower on 2015-08-11
@FakeOutdoorsman
I do not want to cause frustration in guiding me.  But allow me to "rescope ", then state specifically what would be of great help - this has been an "evolving challenge".  And again, my original files to be transcoded are ProResHD(HQ)/24fps.

Rescope: I edit in Kdenlive per your previous help. (Note:  Althoh I can enter 1080p/18fps per an earlier suggestion, and VLC says its 18fps, the rate is not changed and the runtime remains the same).  I then transcode to MPEG-4 to reduce the playing bit rate(introduce compression), and use highest quality setting.  I am abandoning DVD and Blu-ray discs; video files will be played from laptop HD or USB flash drive.

Needed:  A CLI(I assume ffmpeg) that will: 1) transcode the MPEG-4/.mp4 files from 24fps to play at 18fps and retain the quality characteristics at HD(1920x1080), and 2) not introduce an audio track.

I have selected MPEG-4 as my understanding it should give me better quality files versus MPEG-2.  I use the highest quality setting for transcoding in Kdenlive.

Is a CLI to do this achievable/reasonably possible.

mark

---

### Post by mc4man on 2015-08-11
Just for curiosity of this interesting thread - 
I'm assuming the orig were super8 film @ 18fps. 
The website states that all files returned will be @ same fps as the film, but that's not actually the case. If so, why not?
(- I'll guess that at 1080p only 24fps is available?, if so why not have the film done @ 1080i/18fps?

---

### Post by mark bower on 2015-08-11
@mc4man

Good questions - since I have been thru the ringer I can mostly answer them.

Yes, super8mm film was shot at 18fps(if I hadn't been so cheap and used 24fps, this would never have been a problem).  I first went to MyMovieTransfer.com and they transferred frame for frame with playback at 1080p/18fps(so it can be done).  However, their quality was very poor for a number of factors.  So I went to another vendor who works with Hollywood a lot.  They normally process film which is shot at 24fps; their equipment is only designed to output at 24fps, the movie industry standard.  Their quality is tops and they improved many scenes as well as mitigating some scratches in scratched film scenes.  The only way the vendor can provide me with 18fps playback is by adding extra blended frames, and this adds a noticeable blur when there is mild motion in the scene.

So I need to play the video files at .75x (18/24) to see the correct speed.  I can do this on a laptop with VLC.  I have investigated bluray players for versatile speed control, I do not believe they are available.  I returned one to Best Buy today that would only due 1/8,1/4,1/2X.  And as stated, I need .75X.  I can play the videos to my TV via VLC, my laptop, .75X - but really, a bit of a nuisance.  How much easier it would be to have the video display at 18fps and simply plug a USB flash drive with the 18fps video files into a bluray player and view(I did this with a flash drive, but at 24fps). 

I must confess, I do not fully understand how the digital video is stored.  However, it seems that some how the "director" for the fps speed to play should be adjustable within the stored files?  Clearly it is "externally" done when utilizing VLC.  I am not sure about the 1080i vs 1080p stuff, but I believe all video media is or has moved to progressive (1080p) based on digital vs the older TV lines; my one bluray disc is 1080p/24fps.

Hope this answers more than you wanted to know.

---

### Post by mc4man on 2015-08-12
Maybe FO can tell you if ffmpeg with the setpts video filter can slow down the vid without causing you much issue (maybe,  -vf "setpts=(4/3)*PTS"  or something...
Otherwise framerate conversions seem a bit complicated.

---

### Post by mark bower on 2015-08-12
breaker-breaker
I went to ffmpeg.org/forums and found exactly the line I needed, and yes, it utilizes "setpts".  I want to verify all the way thru from digitized 24fps files to playing on my bluray player at 18fps off a USB flash drive. Assuming all goes as predicted, I will return with a final wrap-up/summary post and set this thread to solved!  Could only get to this point because of forum help.

---

### Post by FakeOutdoorsman on 2015-08-12
Although setpts is useful it probably isn't the best solution for this case, but it's not possible to provide any suggestions without a short sample file.

---

### Post by mark bower on 2015-08-13
Well I thot I had it made.  I used setpts per the following:  

ffmpeg -i input.mp4 -vf "setpts=1.3*PTS" output.mp4

The desired video rate is achieved and with extra frames added, stuttering is not apparent.  Very easy to tweak the rate if desired.  However, the quality of the output files using the "setpts" function is not good.  A rough estimate in file size reduction after applying setpts is 70%.  IE, a 2.0GB file is reduced to .61GB.  Correspondingly, the bit/s rate for the same file during play is reduced from about 67Mb/s to 15Mb/s(I used peak rates since average is hard to judge).

I scoured the ffmpeg.org/forum for a quality parameter that could be included during encoding process, but I could not see that as being available.  Note:  I believe that setpts adds frames rather than just recoding to tell the frames to play slower.  However, looks like this is acceptable.

If atch icon>Add Files>Browse & atch works, you should get a MPEG-4(.mp4), VLC= 1 min duration, 97MB clip.  If not, please tell me how to get it to you - I can mail if that works.

I did see the following at FFmpeg.org, but cannot figure out what N and TB mean, nor what to do with FRAME_RATE, althoh maybe that is what should be used?
FFmpeg Filters Documentation
12.9 setpts,asetpts
Set fixed rate of 25 frames per second: 
setpts=N/(25*TB)
N 	The count of the input frame for video or the number of consumed samples, not including the 	current frame for audio, starting from 0. 
TB	The timebase of the input timestamps. 
FRAME_RATE frame rate, only defined for constant frame-rate video 

Well, I looked at return and I do not see that the clip made it?

---

### Post by mc4man on 2015-08-13
> **mark bower said:**
> 

If atch icon>Add Files>Browse & atch works, you should get a MPEG-4(.mp4), VLC= 1 min duration, 97MB clip.  If not, please tell me how to get it to you - I can mail if that works.

Well, I looked at return and I do not see that the clip made it?
you can't attach video files per se & any file is limited to 976KB or less in  this forum.  (vid files at or less can be put in a folder & archived to attach,  of no value to you in this case anyway due to size. 
This is a fairly innocuous upload site - (you can leave up or delete at some point if  desired via the supplied delete link.

[http://www.datafilehost.com/](http://www.datafilehost.com/)

---

### Post by FakeOutdoorsman on 2015-08-13
I'm looking for a short sample derived from the original ProRes file, using stream copy as shown in [post #25](http://ubuntuforums.org/showthread.php?t=2276780&page=3&p=13335947&viewfull=1#post13335947). Specifically a segment that exhibits the previously described behavior.

---

### Post by mark bower on 2015-08-13
Aah, i get it.  i will extract the file(short clip) a little later this eve and post.  Also, I tried the following with similar results to previous attempts.  It will extend the clip time from 1min to 1:20min(good), but it inserts extra frames to do so and the quality(file size and bit rate) drops by about 66% in the output file.

ffmpeg -i input.mp4 -r 18 -vf "setpts=(1.3333)*PTS" output.mp4

---

### Post by mark bower on 2015-08-13
o.k. atch should be the 5sec clip of ProResHD(HQ) @ 24fps.  Returned and looks like no upload; file is 106MB.  Just looked at mc4man's comments which sounds like 106MB will not be supported, even with a folder? - Make some other arrangement via private message?

---

### Post by mc4man on 2015-08-14
> **mark bower said:**
> o.k. atch should be the 5sec clip of ProResHD(HQ) @ 24fps.  Returned and looks like no upload; file is 106MB.  Just looked at mc4man's comments which sounds like 106MB will not be supported, even with a folder? - Make some other arrangement via private message?
The limit here would be 976KB or less than 1MB, so you would fit much prores here (1/25 of a sec.. or so. You'd be ok with that upload site @ 106

---

### Post by mark bower on 2015-08-14
@mc4man

> so you would fit much prores here (1/25 of a sec.. or so. You'd be ok with that upload site @ 106 

Sorry, but I do not understand how to send the 106MB file - eg, what upload site.

I googled with keywords "ffmpeg quality" and tapped into a number of suggested CLIs to maintain quality with ffmpeg.  I will try/experiment with some today.  Of course one can try and figure stuff out from the FFmpeg.org Documentation itself, but it is so extensive that it blurs!

To be clear, I can slow the play rate back to 18fps from 24fps via the added frames.  This is o.k., but not desirable.  In so doing, the parameters are not set correctly to maintain quality.  This is** not o.k**. and I hope we can figure out how to overcome it.  The problem occurs in either of two paths: ProRes_24fps.mov>ffmpeg>18fps.mp4 or ProRes_24fps.mov>Kdenlive>24fps.mp4>ffmpeg>18fps.mp4

---

### Post by mc4man on 2015-08-14
click on link in this post
[http://ubuntuforums.org/showthread.php?t=2276780&p=13337980&viewfull=1#post13337980](http://ubuntuforums.org/showthread.php?t=2276780&p=13337980&viewfull=1#post13337980)
After uploading you'll be given a download link & a delete link. Copy both links to a file, post the dl link here. 
If desired you can use the delete link to remove the file at some point. Otherwise it will stay on the site unless it has I think 90 days of inactivity, then the site will delete.

---

### Post by mark bower on 2015-08-14
I synthesized from some posts and made progress with the following code line which plays at 18fps(equivalent) and maintains the desired quality level:

```
ffmpeg -i input.mov -r 18 -vf "setpts=1.333*PTS" -c:v libx264 -crf 19 output.mp4
```
So this takes my ProResHD(HQ) 1min clip,1.3GB file size, and converts it to 1.20 min duration as .mp4, 137MB file size, 15Mb/s bit rate - all very good.  I suspect that even tho the code works, it is not fully correct or optimal.  If "-r 18" is removed, the file duration is 1:19 min, file size is 157MB and 25Mb/s bit rate(quality a bit higher than desired).

@mc4man - I will now attempt the upload per your instructions.

---

### Post by mark bower on 2015-08-14
The upload would not work at datafilehost.  It appeared like it was uploading, but then after 7min returned to  opening upload page with no download or  remove link provided.  I tried to email the problem to them per the following from their FAQ both with and without the "[]", but only got an error msg.

 contact[@]datafilehost.com.

---

### Post by blm-ubunet on 2015-08-14
@mark

Having had a film digitized a while ago..
Would expect the vendor to supply digital video file at original frame rate & another post-processed video to DVD or other standardized video format.
I would expect your quicktime .mov file to be at the original frame rate with no added frames.

Like you, I found the conversion (FinalCut) from 17fps to 50i DVD to be pretty bad.
The deshaking was no good & frame interpolation was rubbish.
Old film cameras may have run at 24fps but the temporal sampling (motion blur) is not 24fps because of the shutter duty cycle. The motion temporal sampling is not too different to 50Hz.

ffmpeg does not do frame interpolation (yet) so used mjpegtools yuvfps.
ffmpeg has to have 50or 60fps to make interlaced DVD video. 

```
fmpeg -i your-input-video.mov -vf "crop=720-40:576-30:0:0, scale=720:576, deshake=-1:-1:-1:-1:16:16:2" -f yuv4mpegpipe -y stream.y4m

cat stream.y4m | yuvfps -w -r 50:1 -s 17:1 | ffmpeg -f yuv4mpegpipe -i - -vcodec mpeg2video -flags +ilme+ildct -target pal-dvd  -b 8000k -y new2.mpg
```
You can probably pipe the whole lot in one command once you find the settings you require.

HTH.

---

### Post by mark bower on 2015-08-14
The upload would not work at datafilehost.  It appeared like it was uploading, but then after 7min returned to  opening upload page with no download or  remove link provided.  I tried to email the problem to them per the following from their FAQ both with and without the "[]", but only got an error msg.

 contact[@]datafilehost.com.

BUT STOP.  I am going to consider the compromise of working with the 18fps equivalent, that is, the file is increased in size by 3:1 frames to display at the correct original rate.  That is, for every 3 orig frames an additional frame is inserted added.  And not battle trying to get 24fps to display at 18fps - unless of course, someone stumbles on the knowhow.

---

### Post by mark bower on 2015-08-14
@blm-ubunet

This thread obscures some of my info.  Please see post #23 per link; the particular vendor I am working with does a great job with the transfer at 24fps.  The vendor is getting a new machine which will do 18fps or any fps for that matter, except that the excellent color correction capability will not be available on the new machine.  So opted to go fwd with the 24fps.  Actually, if it looks o.k., I am leaning towards transcoding to 18 + 6 frames for an effective 18fps per sec.  Not sure what you mean by "frame interpolation", possibly frame blending?  If so, I previously commented that the blended frames to achieve effective 18fps are detected by the eye if there is mild motion, eg, unsteady camera movement as I experience in underwater scenes near the ocean surface.

[http://ubuntuforums.org/showthread.php?t=2276780&page=3](http://ubuntuforums.org/showthread.php?t=2276780&page=3)

---

### Post by blm-ubunet on 2015-08-14
I did read that post..
I just have hard time believing a professional vendor could be so crazy to not provide unprocessed video (as well).
Would have expected them to have just tagged it as 24fps because (your 18fps) it is close enough to std format.

The film frames are digitized one by one.. and AFIAU the pro-res format is just sequence of i-frames. The real frame rate can be 18fps when the container reports any fps.
The vendor would have had to go to some trouble to create actual 24p video from this video.

Interpolation is not crude frame blending it is motion vector (temporal-spatial) tracking (a lot like de-interlacing).

To display 24p at 18fps your video player just repeats frames as required. I doubt there is any blending.
Sadly I do not know of any linux video renderer that can do interpolation; you have to go to windows & madVR.
The only linux tool (AFAIK) to interpolate video frames is "yuvfps".

If you slow down the 24fps (container rate) to display at 18fps you will get motion jitter unless your display refreshrate is 18,36,54 or 72Hz refresh.

If your video has actually been (damaged) telecined to 24p then could try to undo with videofilters detelecine or pullup:
ffmpeg -i input -vf pullup -r 18 ... but you need a container that allows that framerate or use yuvfps..
Both of these filters might only work on "normal" telecine framerates. Detelecine can be "taught" a pulldown pattern to use/undo.

---

### Post by FakeOutdoorsman on 2015-08-15
> **blm-ubunet said:**
> 
Sadly I do not know of any linux video renderer that can do interpolation; you have to go to windows & madVR.
The only linux tool (AFAIK) to interpolate video frames is "yuvfps".

[slowmoVideo](https://github.com/slowmoVideo/slowmoVideo/wiki)

---

### Post by mark bower on 2015-08-15
No, the 18fps was not telecined to 24fps.  The vendor does frame to frame, but packaged in a fashion I do not understand to 24fps.  Again, almost all of Hollywood and movie industry I am told does 24fps, and that is the major customer for the vendor. However, I looked at 4 of our DVDs, and they run at 29.97 re VLC.  I am not sure of refresh rates, but on a laptop 24fps slowed to about .72X seems smooth.  And going to an effective 18fps from 24fps(one frame added for every 3 original frames), well that also appears smooth and what I am currently scrutinizing.  

o.k., interpolation is not blending.  

Now I am working with a file size of 5.5GB, that to be stored on a USB flash drive requires that the drive be formatted NTFS(not FAT32).  So having done that, it appears that my bluray player will not accept the NTFS format.  So I am currently looking into possibilities - I am guessing the bluray manual will not specifiy the USB format(s) required.

---

### Post by blm-ubunet on 2015-08-15
Just as I said in post #42 & #45..
The vendor has (correctly) provided digitized video where one file frame = one film frame without frame creation/interpolation.
The container has been tagged/timestamped/rendered at 24p because that is close to 18fps & the container might not support weird framerates (AFAIK).

You have to override the bogus file frame-rate but you can not play that on anything but computer & you will have pulldown (in video rendering) cadence jitter unless your display refreshrate is an nice multiple of 18Hz.

Good luck with the BD/consumer video device, I would think they support mpegts, m2ts & mkv using h264 codec profile high@L4.x 4:2:0.

DVD video does not support 24p (thankfully).

---

### Post by mark bower on 2015-08-17
@blm-ubunet

The more I think about, the better interpolation sounds.  I would guess that means that an "inserted unblurred" frame would be added for every 3 frames in my 24fps case, to display at equivalent 18fps?  An interpolated frame would make it virtually impossible for the eye to detect.  

I did finally identify the problem with my ffmpeg transcoding from .mov to .mp4.  I can now play the .mp4 files on my bluray player.  At this point I suspect that I may some superfluous CLI entries, -maxrate and -bufsize which do not seem to be effective for the settings I use in ffmpeg.  I would like to debug before I post a final summary on my transcoding from ProResHD(HQ) to .mp4.

---

### Post by blm-ubunet on 2015-08-22
I believe one of the avisynth interpolation filters allows you to define which frames are modified & or added, so could limit the extent of frame creation.
That filter may not exist outside of windows/wine.

Ffmpeg can be built with some type of support for avisynth (avxsynth in linux).
[http://forum.doom9.org/showthread.php?p=1706676#post1706676](http://forum.doom9.org/showthread.php?p=1706676#post1706676)
That could mean that interpolation etc could be done at playback using avs script & ffplay or mpv.

But regardless, avxsynth has been surpassed by vapoursynth.
[http://www.vapoursynth.com/](http://www.vapoursynth.com/)

The "mvtools" avisynth plugin has been recently ported to vapoursynth which allows motion vector interpolation amongst loads of other things..

---

### Post by mark bower on 2015-08-24
The summary I promised.  Special thank to those that supported this quest.  

I dropped the plan to use DVD and bluray discs and went to the following sequence where orig = prores422HD(HQ):

Transfer (scan) super8mm film --> orig.mov                            (done by professional transfer house)
Edit & render orig.mov with Kdenlive --> edited-orig.mov      (optional)
Transcode with ffmpeg --> MPEG-4(1080p) 
Copy MPEG-4 files to USB flash for TV viewing.

The super8mm film is transferred to prores422(HQ) at 24fps (vendor process).  Each file is then edited and stored in prores422(HQ).   The edited file (primarily inclusion of a title) is then transcoded to the .mp4 format to include:  1) 1:3 ratio of extra frames added, 2) quality set to a high level, but not cause file size to exceed about 4GB (USB FAT 32 limitation).

The following command line is what I used in ffmpeg to produce the .mp4 video files, where input.mov is either the orig.mov or the edited-orig.mov file:

```
ffmpeg -i input.mov -vf  "setpts=(1.333)*PTS" -c:v libx264 -preset slow -pix_fmt yuv420p -crf # output.mp4
```

-vf "setpts=(1.333)*PTS"  - returns apparent f/s to 18fps (original film rate) by inserting (duplicating) an extra frame for every 3 original frames; 1.333 = 24/18.  So while the digital video still runs at 24fps, it appears to be running at 18fps, the original rate.
-preset - my understanding is this should produce improved quality (by compressing slowly) in addition to a low "crf" setting
-crf #  - quality setting, # is 0 to 53, lower number = higher quality and runtime Mb/s 
-pix_fmt yuv420p  - sets the color space  to 8bit per pixel; makes mp4 file largely compatible for most players.  yuv422p is 10 bits per pixel but I could not get it to work.

 I can not explain the difference in the settings to get to approximate same quality(runtime b/s), but the following is what I used for crf:

                      ffmpeg
ProRes HQ--------------->MPEG-4   crf 20

                     Kdenlive                                      ffmpeg
ProRes HQ --------------->edited ProRes HQ ------------->MPEG-4    crf  17,18,19 or 20

When the MPEG-4 video is run, it is smooth with no noticeable judder.  The quality of the video produced by the transfer vendor  is spectacular:  1) no apparent loss in resolution from the projected films, 2) scenes exposure adjusted if necessary, and 3) scratches seen via the projector are either gone or minimized in the digitized files.  And it so easy to pop the USB stick with the MPEG-4 files into the bluray player and play on the TV.

---

### Post by mark bower on 2015-09-21
I am saying goodbye to this thread and will not be returning.  I remain very thankful for the support that did work for me and enable me to get thru my large project.

---

