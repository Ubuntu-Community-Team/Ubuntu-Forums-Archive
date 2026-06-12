---
title: "Quick FFMPEG Codec Comparison Test: x264 vs xVid"
date: 2008-01-04
forum: Multimedia Production
---

### Post by philc on 2008-01-04
Today I took the time to run a quick comparison test using FFMPEG for producing content with the [x264]("http://www.videolan.org/developers/x264.html") and [xVid]("http://www.xvid.org/") codecs. x264 produces H.264 content, while xVid encodes in MPEG4. Frankly, I was a little surprised with the results.

The input file was sourced from[ BBC Motion Gallery]("http://www.bbcmotiongallery.com/"). It was an MPEG2 Program Stream with I-Frames, encoded at approximately 50Mbps. It also contained a single MP2 audio track at approximately 356kbps. To see the clip on BBC Motion Gallery, [click here]("http://www.bbcmotiongallery.com/Customer/SearchDetails.aspx?searchText=2573-9&type=Simple&itemId=fa1b564c-47d0-4cab-86e0-44cd4363d7ad"). The clip was chosen because it is only 2 seconds long, so I could transcode it quickly, and there is also lots of movement, so I expected artifacts.

The output file container is QuickTime MOV, the video bitrate around 2Mbps, the audio codec aac (through libfaac) at 128kbps. I performed a 1 pass and 2 pass encode with x264 and xVid. The output file was to be 720x404 in size, this is 16:9 aspect ratio. All files were played back on a Windows XP machine using QuickTime Player 7.1.3. Some cropping of the original MPEG2 was required to remove VITC at the top and some black padding left and right. An example FFMPEG command line I used is outlined below. As you can see, there are very few optimisations other than the base settings.

FFMPEG command for the second pass x264 encode:

ffmpeg -i 2573-9.mpg -vcodec libx264 -f mov -b 2000k -acodec libfaac -ab 128k -s 736x442 -croptop 34 -cropbottom 4 -cropleft 8 -cropright 8 -deinterlace -pass 2 2573-9_h264.mov

The final output file sizes are as follows:

    * x264 1 pass: 599.558 kilobytes
    * x264 2 pass: 553.767 kilobytes
    * xVid 1 pass: 577.232 kilobytes
    * xVid 2 pass: 559.947 kilobytes

So, while xVid one pass produced smaller file sizes than x264 one pass, the x264 2 pass file is smaller than the xVid 2 pass file. Due to the short duration of the input file, no comparison of encoder speed could really be made. However, anecdotally from other ad hoc encoding jobs, xVid does seem to be quicker.

Now, to the real proof of the pudding, what was the quality like. Have a look at the following image file:

[http://farm3.static.flickr.com/2331/2166176406_44357465ed_o.png]("http://farm3.static.flickr.com/2331/2166176406_44357465ed_o.png")

This is where I was surprised. The x264 files are on the left. 1 pass is bottom left. 2 pass is top left. The xVid files are on the right. 1 pass bottom right. 2 pass top right. Clearly, the 1 pass xVid file is superior to the 1 pass x264 file. I also believe that the 2 pass xVid file is slightly better quality then the 2 pass x264 file. Areas for close inspection (we're looking at the two top files here):

    * Bottom right corner. There is more blocking and artifacts on the x264 file.
    * Top right wing tip. The xVid file has better definition here.
    * The underside of the wings and tail. Again the xVid file has better definition.
    * The background fire. I think the xVid file has less artifacts and better definition in general.
    * As there aren't a lot of colours in the example video, it's hard to say which codec handles colour better, but there is obviously more depth in each of the 2 pass samples, compared to the 1 pass output.

That's pretty much it. I was surprised that to my eye the xVid content appeared to be superior to the x264 output. Perhaps with a more complext FFMPEG command and options this would have changed.

I'd be interested to hear other's thoughts and opinions on these two codecs.

---

### Post by philc on 2008-01-04
After a couple of tips on the FFMPEG user mailing list, I re-ran this test with some command optimisations. Specifically:

    * De-blocking loop filter enabled with -flags +loop
    * CABAC enabled with -coder ac

New FFMPEG command example for x264, second pass is:

ffmpeg -i 2573-9.mpg -vcodec libx264 -flags +loop -coder ac -f mov -b 2000k -acodec libfaac -ab 128k -s 736x442 -croptop 34 -cropbottom 4 -cropleft 8 -cropright 8 -deinterlace -pass 2 2537-9_x2642passnew.mov

New screen grab is here:

[http://farm3.static.flickr.com/2281/2166352750_138697cfaa_o.png]("http://farm3.static.flickr.com/2281/2166352750_138697cfaa_o.png") 

x264 still on the left, xVid on the right. Old 2 pass files bottom. New 2 pass files, with - coder ac and - flags +loop added to the FFMPEG command, on top.

The new x264 file is slightly larger than the old one (50 bytes). The xVid file is the same size.

From the new screen grab, it can be seen that the x264 output is now clearly superior. In this case it can be really proved that optimising the FFMPEG command can truly make a difference.

---

### Post by theacoustician on 2008-01-04
> **philc said:**
> 
New FFMPEG command example for x264, second pass is:

ffmpeg -i 2573-9.mpg -vcodec libxvid -flags +loop -coder ac -f mov -b 2000k -acodec libfaac -ab 128k -s 736x442 -croptop 34 -cropbottom 4 -cropleft 8 -cropright 8 -deinterlace -pass 2 2537-9_xvid2passnew.mov
That looks like your xvid command line.  Also, why such a high bitrate for 264?  There's really no reason to encode SD material higher than about 1000-1250k if you have all your switches correctly set.

---

### Post by philc on 2008-01-04
> **theacoustician said:**
> That looks like your xvid command line.  Also, why such a high bitrate for 264?  There's really no reason to encode SD material higher than about 1000-1250k if you have all your switches correctly set.

Sorry, you're right. Typo on my behalf and I have edited my post.

The main reason for using 2Mbps for the x264 encoding, is that the QuickTime files on BBC Motion Gallery, where I obtained the Master MPEG2 file, are at 2Mbps ([http://download.bbcmotiongallery.com/quicktime/00/25/73/2573-9_70.mov](http://download.bbcmotiongallery.com/quicktime/00/25/73/2573-9_70.mov)).  These files have been created using an expensive commercial H.264 encoder. I want to create a file using x264, to see how it compares.

For playback, perhaps 2Mbps is more than you need. However, given that the BBC Motion Gallery files are often used for rough cut editing, prior to licensing master material, 2Mbps is barely enough!

---

### Post by theacoustician on 2008-01-04
> **philc said:**
>  I want to create a file using x264, to see how it compares.

For playback, perhaps 2Mbps is more than you need. However, given that the BBC Motion Gallery files are often used for rough cut editing, prior to licensing master material, 2Mbps is barely enough!

To the first part, you should check out the MSU 264 codec shootout.

As for the second part, anyone editing B-framed video for contribution grade masters should be shot.  That's just a mess waiting to happen.  Hopefully once they've settled on a rough edit, they go back and apply the changes to a MJPEG or some other all I-frame format.  I guess it does answer why you were using .mov instead of .mkv or .mp4 though.

Just a note too : Nero has released their reference AAC encoder for Linux now.  You should give it a go for the audio.

Edit : do you happen to know which encoder the BBC uses?  Tandberg, SA, Motorola, other?  I've got a stack of EGT Alto's sitting on my desk now waiting to be configured :)

---

### Post by philc on 2008-01-04
> **theacoustician said:**
> To the first part, you should check out the MSU 264 codec shootout.

Thank you I will. I've been reading the doom9 codec comparisons, but it seems the last time they did one of note was back at the end of 2005!

> **theacoustician said:**
> As for the second part, anyone editing B-framed video for contribution grade masters should be shot.  That's just a mess waiting to happen.  Hopefully once they've settled on a rough edit, they go back and apply the changes to a MJPEG or some other all I-frame format.  I guess it does answer why you were using .mov instead of .mkv or .mp4 though.

I concur regarding the B-Frames. However, given that Motion Gallery has over 50,000 clips online and the QuickTimes are provided free of charge, albeit watermarked, for preview purposes, I guess it was a tradeoff on size vs quality.

As for me personally, my interest here stems from my own website which plays back H.264 content - currently either in embedded QuickTime player, or now via the latest Flash update that supports H.264 content. From a legacy point of view all the QuickTime content is in a MOV container. I presume Flash will support H.264 in an mp4 container, but I haven't tested, and I doubt it'll support Matroska, but I'll try that too just for fun.

> **theacoustician said:**
> Just a note too : Nero has released their reference AAC encoder for Linux now.  You should give it a go for the audio.

Thank you I will. I've been using libfaac with FFMPEG for Linux work to date.

> **theacoustician said:**
> Edit : do you happen to know which encoder the BBC uses?  Tandberg, SA, Motorola, other?  I've got a stack of EGT Alto's sitting on my desk now waiting to be configured :)

"The BBC" is a big place and they use lots of different technologies. And of course Dirac is a BBC originated initiative. However, the part I know about doesn't use any of the ones you mention. :) 

BBC Motion Gallery uses Telestream's FlipFactory for transcoding and ClipMail for encoding at this time:
[http://66.102.9.104/search?q=cache:XAgCDfPRmuIJ:www.telestream.net/news/05_09_09_d.htm](http://66.102.9.104/search?q=cache:XAgCDfPRmuIJ:www.telestream.net/news/05_09_09_d.htm)

---

### Post by theacoustician on 2008-01-04
> **philc said:**
> BBC Motion Gallery uses Telestream's FlipFactory for transcoding and ClipMail for encoding at this time:
[http://66.102.9.104/search?q=cache:XAgCDfPRmuIJ:www.telestream.net/news/05_09_09_d.htm](http://66.102.9.104/search?q=cache:XAgCDfPRmuIJ:www.telestream.net/news/05_09_09_d.htm)Gah, the website seems to be toast.  Too bad :(

Please keep posting updates with your 264 experiments.

---

### Post by eye208 on 2008-01-04
I did a similar comparison a few weeks ago, but at much lower bitrates. The source material was some HD stock footage taken from Apple's website. I used MEncoder to downscale (704x396) and encode it in 2-pass mode at 622kbps average bitrate (29.97fps). Look at the results here:

[img]http://img295.imageshack.us/img295/8960/xvid0297gj1.png[/img]
Xvid

[img]http://img524.imageshack.us/img524/222/x2640297ii3.png[/img]
x264

[img]http://img205.imageshack.us/img205/7452/xvid5802fw9.png[/img]
Xvid

[img]http://img521.imageshack.us/img521/193/x2645802zi9.png[/img]
x264

[img]http://img183.imageshack.us/img183/8549/xvid7478od4.png[/img]
Xvid

[img]http://img526.imageshack.us/img526/206/x2647478rd1.png[/img]
x264

As you can see, H.264 does a very good job eliminating block noise artifacts.

While x264 is a great codec, unfortunately the same thing cannot be said about FAAC, the open-source AAC codec. I still prefer LAME in VBR mode for audio encoding. Vorbis is not an option here because it is not officially supported in MP4 containers.

By the way, if you want to produce Quicktime-compatible H.264 video you must keep in mind that some advanced H.264 features are not supported in Apple's implementation. If these features are used in a video, Quicktime will show nothing but a white screen on playback. So you have to choose your encode settings carefully to work around Quicktime's limitations.

---

### Post by philc on 2008-01-05
Thanks eye208.

It looks like x264 certainly beats xVid in pretty much all areas!

I've not used Mencoder myself, but was reading up on it yesterday. Is there a reason you prefer this over FFMPEG? Although I know Mencoder has the ability to utilise the libavcodec library and libx264, the same as FFMPEG.

Would you be able to elaborate regarding the limitations of FAAC?

Also, could you share your Mencoder command options for producing the x264 content? 

I started working my way through some other options for x264 yesterday (actually mostly based on the Mencoder documentation here - [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html#menc-feat-x264-encoding-options](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html#menc-feat-x264-encoding-options)

I have tried adding subq set at 5,6 and 7 to my command posted above, but couldn't visually see any difference on the clip I was using.

---

### Post by theacoustician on 2008-01-05
> **philc said:**
> Thanks eye208.

It looks like x264 certainly beats xVid in pretty much all areas!

I've not used Mencoder myself, but was reading up on it yesterday. Is there a reason you prefer this over FFMPEG? Although I know Mencoder has the ability to utilise the libavcodec library and libx264, the same as FFMPEG.

Would you be able to elaborate regarding the limitations of FAAC?

Also, could you share your Mencoder command options for producing the x264 content? 

I started working my way through some other options for x264 yesterday (actually mostly based on the Mencoder documentation here - [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html#menc-feat-x264-encoding-options](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html#menc-feat-x264-encoding-options)

I have tried adding subq set at 5,6 and 7 to my command posted above, but couldn't visually see any difference on the clip I was using.The quality of FAAC is somewhat less than that of other closed source encoders out there.  Also, to my knowledge, you can't make 5.1 AAC files with FAAC.  That's why I mentioned Nero's reference encoder is available for Linux now.  The quality is excellent and it will do 5.1 AAC.

---

### Post by eye208 on 2008-01-07
> **philc said:**
> I've not used Mencoder myself, but was reading up on it yesterday. Is there a reason you prefer this over FFMPEG?
Convenience. Ubuntu's MEncoder comes with all the codecs included, some of which are missing in Ubuntu's FFMPEG. But I also appreciate that I can preview video and audio filters in MPlayer before using them in a transcoding session with MEncoder.

> Would you be able to elaborate regarding the limitations of FAAC?
FAAC is not too bad, but it suffers from the fact that LAME is such an excellent codec. I can encode to MP3 at 96kbps (average) using the -q 0 and -k switches (aq=0:lowpassfreq=-1:highpassfreq=-1 in MEncoder), and the result will be clearly superior to FAAC's output at the same target bitrate. And MP3 is compatible with every mobile playback device available.

> Also, could you share your Mencoder command options for producing the x264 content?
I think I used the default settings, except for bitrate and pass of course, but I don't remember exactly. I try to keep my own videos compatible with Quicktime, so I often use "no8x8dct", but I think I did not use it for this test.

> I have tried adding subq set at 5,6 and 7 to my command posted above, but couldn't visually see any difference on the clip I was using.
Maybe it's because you were using high target bitrates. Quality differences become more visible/audible at low bitrates.

---

