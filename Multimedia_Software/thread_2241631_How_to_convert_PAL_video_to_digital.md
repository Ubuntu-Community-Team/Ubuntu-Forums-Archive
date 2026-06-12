---
title: "How to convert PAL video to digital"
date: 2014-08-27
forum: Multimedia Software
---

### Post by satimis on 2014-08-27
Hi all,

I have old video taken with Song Video 8 Handycam CCD-F380E
photo - sony_video8.JPG
(I hope the handycam still working)

Is there any any way converting the PAL video to digital?  If YES, please advise HOW.  Pointers would be appreciated.


Sony PlayMemories Home is FREE but for Windows.
Freeware which enables photos and videos to be easily managed and edited on PC.
[http://support.d-imaging.sony.co.jp/www/disoft/int/download/playmemories-home/win/en/index.html?](http://support.d-imaging.sony.co.jp/www/disoft/int/download/playmemories-home/win/en/index.html?)

Are there similar application on Open Source for Linux?

Thanks

Regards
satimis

---

### Post by TheFu on 2014-08-27
So the files are analog and can only be played back from the SONY device?

What have you tried so far? Where did it fail?

---

### Post by satimis on 2014-08-27
> **TheFu said:**
> So the files are analog and can only be played back from the SONY device?

What have you tried so far? Where did it fail?
Hi,

The video are resting on shelves for long time.  Now I have no player which has been broken.  I still have the Song Video 8 Handycam in store room.  I'll dig it out to see whether it still works  If it still working where can I connect it?

Regards
satimis

---

### Post by TheFu on 2014-08-27
I can't tell if the output from the handycam is digital already or analog on a tape.  What is the format of the files?  If htey are .dv or some other well-know video and you can get them onto a computer, there is hope.

It may be possible to transfer the file through a firewire connection too. Does the handycam have firewire?

Otherwise, going the playback-way and recording the video with an analog-to-digital recorder is necessary.  Hardware is required to "record" the video playback.  If you cannot play the video with current equipment, then it may be less hassle/cost to take it to a professional and have them do it.

I use Windows for all my video processing ... except the very last step - transcoding to h.264/mkv. For DVD resolution or less, using xvid/mpeg4 and AVI containers is more efficient on storage.  I cannot recommend any specific hardware to handle the transfer from analog to digital. All that I've used were Windows-only.

---

### Post by satimis on 2014-08-27
Hi 
TheFu,

I haven't touched the Song Video 8 Handycam for long time.  According to my recollection in the past I can connect it to an old TV with cable playing the video tape.  I hope I can find the cable.  But I couldn't connect it to computer?  I'll check the Song Video 8 Handycam tomorrow.

I just looked at the tape.  It is marked "Sony Metal MP90, PAL 8, Video 8".

I have no problem coming back to Windows.  I have Windows 7 running on VM of Oracle VirtualBox.  If I can't make it connect the Handycam I can install a hard drive on a PC to run Windows

Regards
satimis

---

### Post by TheFu on 2014-08-27
Something like this: [http://www.amazon.com/USB-Video-Capture-Device-Computer/dp/B00MLZCK96/](http://www.amazon.com/USB-Video-Capture-Device-Computer/dp/B00MLZCK96/)

Again - I don't know of any with strong Linux support. Also, if the resolution is DVD or less, these cheap devices are fine.  For 720p, the capture devices are more expensive, but can usually accept lower resolution inputs too.  The Hauppauge 1212 is expensive, but does work for Linux.  I have a 1512 which does NOT support Linux.

Many TV-Tuners will have inputs for recording too and if MythTV claims support, then I'd try it under Linux. [http://www.mythtv.org/wiki/Digital_Tuner_Cards](http://www.mythtv.org/wiki/Digital_Tuner_Cards) - definitely look for inputs OTHER THAN ATSC or QAM - those do not help with what you need. The Hauppauge 950Q does, for example.

Of course, it would be much more preferred to get the files directly from the tape in whatever format it uses to avoid re-re-recording.

---

### Post by satimis on 2014-08-27
Hi TheFu,

Thanks for your advice.

Ok.  If my Handycam is still running I'll buy a USB video capture device and the TV-Turner card for recording.  I hope my DVD burner is still working.  I haven't burned DVD for long time.

> 
... definitely look for inputs OTHER THAN ATSC or QAM
Could you please explain in more detail?

In another thought how to check the Handycam is working?  Turning is not sufficiently equal to working.

Regards
satimis

---

### Post by TheFu on 2014-08-27
> **satimis said:**
> Hi TheFu,

Thanks for your advice.

Ok.  If my Handycam is still running I'll buy a USB video capture device and the TV-Turner card for recording.  I hope my DVD burner is still working.  I haven't burned DVD for long time.


Could you please explain in more detail?

In another thought how to check the Handycam is working?  Turning is not sufficiently equal to working.

Regards
satimis

You only need 1 of those tuner/capture devices, not both.
Physical DVD?  Why would you want that?  I haven't burned a DVD is years and years.

What is the resolution of the recordings and what type of device do you want to playback the video on? This will help to decide what videocodec and container works best.

---

### Post by satimis on 2014-08-28
> **TheFu said:**
> You only need 1 of those tuner/capture devices, not both.
Physical DVD?  Why would you want that?  I haven't burned a DVD is years and years.

What is the resolution of the recordings and what type of device do you want to playback the video on? This will help to decide what videocodec and container works best.
Hi,

Oh Sorry, I misunderstood your advice.  You referred to DVD resolution.

I found the old Sony Handycam but without battery.  I don't know why.  All accessories are in the carrying bag including lens except battery and mic cover, a sponge.

I connected the Handycamer direct to the battery charger as shonw on camera1.jpeg attached.  The viewfinder displayed distant objects.  But after a while it turned off.

Beside I could not eject the cassette cover(camera2.jpeg).  The lithium battery is gone(camera3.jpeg).  I'll replace it to see what will happen

I think the handycam can't work.   

Regards
satimis

---

### Post by lisati on 2014-08-28
I can totally appreciate the desire to capture the old tapes into a digital format. I have both a Video-8 and a Digital-8 camera, which I recently decided to check to see if they still had some life left. The tapes are the same size, but the recordings are in different formats.

I have a [DVD recorder with HDD]("http://www.sony.co.uk/support/en/product/rdr-hx750"), purchased about 5 years ago, that I can use for capturing from both cameras when I find a tape that has been hiding in a corner somewhere. I've no idea if such devices are still available.

For the Video-8 camera, I use a "standard" analogue connection. 

For the Digital-8 camera, I use a firewire connection, referred to as i.Link in the camera's manual. It has the advantage of being a digital connection and allowing some degree of control of the camera from the recorder.


edit: My Google-fu for getting hold of a suitable manual that I didn't have to pay for is a bit off at the moment, but from what I could find, it looks like you have an analogue camera, making my comments about firewire/i.Link irrelevant.....

---

### Post by satimis on 2014-08-28
> **lisati said:**
>  - snip -

I have a [DVD recorder with HDD]("http://www.sony.co.uk/support/en/product/rdr-hx750"), purchased about 5 years ago, that I can use for capturing from both cameras when I find a tape that has been hiding in a corner somewhere. I've no idea if such devices are still available.

For the Video-8 camera, I use a "standard" analogue connection. - snip

Hi,

Thanks for your advice.

Just contacted Sony Service Center here.  They don't carry such model, DVD Recorder with Hard Drive, any more but provide service duplicating V8 tape to DVD which can be played in DVD writer.  Cost is charged per hour rate.  In response to my question in re the quality of DVD duplicated they said it will be equal to that of the V8 tape provided.  They also provide service duplicating VHF tapes.  I also have some old stocks.

I think this will be a better solution for my headache.  Advice on request in re of DVD quailty would be appreciated before I visit Sony Service Center in person.  Any attention I need to care.

Thanks

A further question:
Will DVD be in .mp4 or .flv format?  Because I need files in these format to post on website.

Regards
satimis

---

### Post by lisati on 2014-08-28
DVDs have their own format, which usually needs a bit of work before they can be uploaded to a website.

The Windows-based video editing software I use can import from a DVD and output in a variety of formats. I haven't looked too hard for Ubuntu-based equivalents, partly because old habits die hard, partly because the newer camcorders I have came with Windows software, and partly because it has cost me a lot of money over the years purchasing other video software that does what I want.

---

### Post by satimis on 2014-08-28
> **lisati said:**
> DVDs have their own format, which usually needs a bit of work before they can be uploaded to a website.

The Windows-based video editing software I use can import from a DVD and output in a variety of formats. I haven't looked too hard for Ubuntu-based equivalents, partly because old habits die hard, partly because the newer camcorders I have came with Windows software, and partly because it has cost me a lot of money over the years purchasing other video software that does what I want.
Hi,

You're right.

There are many solution on Open Source ripping DVD to mpg/mp4/avi etc. such as;

How to rip a DVD to MPEG-4 using MEncoder & Linux
[http://www.axllent.org/docs/view/mencoder-dvd-to-mpeg4/](http://www.axllent.org/docs/view/mencoder-dvd-to-mpeg4/)

Top 5 Linux DVD RIP Software
[http://www.cyberciti.biz/tips/linux-dvd-ripper-software.html](http://www.cyberciti.biz/tips/linux-dvd-ripper-software.html)

Before bringing my old V8 tape to Sony I'll contact some other shops here for comparison.  However I have better confidence on Sony Service Center although they charge 20% more for such a service.

Regards
satimis

---

### Post by TheFu on 2014-08-29
None of those services will be cheap.  Think hundreds of $$$, not $20.
So - if you can playback the tapes into either a capture device or tuner that costs $40 and you have more than 2hrs of video to be retained, I think it will be cheaper to do it yourself.

DVDs can be either data or video.  The video format is what SONY will return to you. You want this in DVD-PAL, since it will be higher resolution than US standard DVD resolution (480p). Get the highest resolution possible, but not higher than the source.  Then you can convert it to mp4 using a DVD ripper + handbrake - fairly easily and set the resolution down (or not) as desired.

---

### Post by satimis on 2014-08-29
> **TheFu said:**
> None of those services will be cheap.  Think hundreds of $$$, not $20.

Yes.  The cost will not be economical.  But it'll save me lot of headache.

> 
So - if you can playback the tapes into either a capture device or tuner that costs $40 and you have more than 2hrs of video to be retained, I think it will be cheaper to do it yourself.
I have no available hardware to play V8 tape.  I'll try the shops selling second hand electronic devices whether I can find something for my use.  There is no urgency for me.

> 
DVDs can be either data or video.  The video format is what SONY will return to you. You want this in DVD-PAL, since it will be higher resolution than US standard DVD resolution (480p). Get the highest resolution possible, but not higher than the source.  Then you can convert it to mp4 using a DVD ripper + handbrake - fairly easily and set the resolution down (or not) as desired.
If I understand your advice correct, request Sony converting V8 to DVD-PAL system?  Thanks

Regards
satimis

---

### Post by satimis on 2014-08-31
Hi all,

Several hours before I visited an electronic shop here selling 2nd hand hardwares.  I found VHS players, not expensive costing about $80.  But there is no gurantee.  The player can connect to TV set. To connect computer I need a capture card or an old TV tuner card.

If I found a second hand V8 player I may get it as a toy to see whether I can do something treating the V8 tape. Otherwise I will bring all tapes to Sony for duplication. They will duplicate the tapes on DVD which I and play back on TV

satimis

---

### Post by FakeOutdoorsman on 2014-08-31
I often capture ancient analong sources. I use a Canopus ADVC110 which has analog inputs and a firewire output. It will output DV. It was somewhat an expensive device for the time that I bought it for what it does, but now there are many cheaper alternatives but I haven't tried any. Check the device in case it has NTSC and PAL specific switches on the back before capturing so you can choose the correct setting on the device.

I hook up the analog out from the camera or playback deck to the capture device via composite cables (yellow, red, and white). Then from the capture device I connect the firewire to the computer.

I hit play on the camera/deck then use the command line tool "dvgrab". (Alternatively you could also use a properly configured ffmpeg, but I like the "-rewind" option for dvgrab).

```
dvgrab -rewind -size 0 -showstatus oldcrappyvideo
```

It will create a DV file named *oldcrappyvideo001.dv* or something like that I then process with ffmpeg:

```
ffmpeg -i oldcrappyvideo001.dv -c:v libx264 -preset slow -crf 24 -filter:v "yadif=1:1,hqdn3d=4,format=yuv420p" \
-movflags +faststart -c:a libfdk_aac -vbr 4 -metadata title="Title" output.mp4
```

I prefer ffmpeg from FFmpeg instead of what Ubuntu users are fed in the repository, and filtering support is much better. To get it:
[list]
[*]You can download a [Linux build of ffmpeg](http://ffmpeg.org/download.html) or...
[*]follow a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)
[/list]

For video and audio encoding recommendations see:
[list]
[*][FFmpeg H.264 Video Encoding Guide](https://trac.ffmpeg.org/wiki/Encode/H.264)
[*][FFmpeg AAC Audio Encoding Guide](https://trac.ffmpeg.org/wiki/Encode/AAC)
[/list]

Alternatively you can pipe directly from dvgrab to ffmpeg to avoid the intermediate file, but I often mess around with the ffmpeg encoding settings for particular sources then delete (or keep) the DV files when I'm done.

---

