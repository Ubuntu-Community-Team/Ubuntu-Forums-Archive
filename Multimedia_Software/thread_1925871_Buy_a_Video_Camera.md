---
title: "Buy a Video Camera?"
date: 2012-02-15
forum: Multimedia Software
---

### Post by PDA1 on 2012-02-15
My video camera is a Sony miniDV (tape) which I'm getting supremely sick-and-tired-of.

I'd like to buy a fancy new video camera that either uses a chip or internal hard drive in the $500 range.

I use the following programs;

Kino for capturing the video from the video camera. (kdenlive, cinelerra, etc are much too confusing to use and I don't have the rest of my life to figure them out either)

DVDStyler to create the dvd appearance

K3b to burn the ISO image

Getting an HD video output from the camera would be nice but I'm not sure of the following;

- can the above mentioned programs handle the HD format?
- what is the output of an HD video camera?  Hopefully mp4 or something not proprietary.
- if the HD video is really HD then must the created DVD be burned onto a blue-ray DVD?

I want to move up in quality and not stay where I am.  Going to Best Buy and asking the robots there isn't very helpful.

---

### Post by pixiq on 2012-02-15
> **PDA1 said:**
> ...
Getting an HD video output from the camera would be nice but I'm not sure of the following;

- can the above mentioned programs handle the HD format?

You don't need Kino for a camera with a HDD or flash drive. kdenlive  and cinelerra probably work (I have no own experience of them). I use ***OpenShot*** to edit and/or convert, and ***ffmpeg ***for batch conversion. I can play the videos in the original format (providing the computer's cpu and graphics card are powerful enough).
> 
- what is the output of an HD video camera?  Hopefully mp4 or something not proprietary.

MTS (mpeg2 transport stream, coded with h.264) which I think is proprietary, but readable by several standard programs.
> 
- if the HD video is really HD then must the created DVD be burned onto a blue-ray DVD?

I have a Panasonic SD700. I think there is a new camera with similar (slightly improved) specs today. It produces only 1920x1080 frame size and you can choose between progressive or interlaced. In order to make a standard DVD movie, you convert the HD frame size to DVD format for example with ffmpeg or directly from the editing program (in my case with OpenShot).
> 
I want to move up in quality and not stay where I am.  Going to Best Buy and asking the robots there isn't very helpful.

Finally, have a look at the following thread which show some current work of mine (I have a working method, but want to make it more efficient)
[[COLOR="SeaGreen"]_http://ubuntuforums.org/showthread.php?t=1920371_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1920371")

---

### Post by PDA1 on 2012-02-15
I'm not as smart and as experienced as you are, that's for certain sure.

"probably work" and "should work" and "no experience with" are terms that terrify me...especially when using Ubuntu.

When I create/author (or whatever the term is) a DVD using DVDStyler I rely upon "chapters" (individual scenes of a video).  The "chapters" were previousy created when I downloaded the video to my computer (using Kino) and then exported in mpeg format for DVD.

Can OpenShot (which I began fooling with yesterday) create a similar "individual chapter(s)? which are "rendered" as mpeg....or does it render as one huge video file with all chapters not separated?

My videos are always put onto DVD so watching them locally isn't something I typically do.

---

### Post by LuridCinema on 2012-02-15
Dont worry. All you need is a cheapo camcorder that records onto Sd card, pop it in and transfer the files and Openshot will open it. I have stuff I recorded witha Canon T2i, a cheapo Kodak Handi-cam and a Canon SX20IS and Openshot will easily edit them no muss, no fuss. Great thing about SD cars is no transfer hassles like w/ DV tapes, just upload and go..

BTW I use Cinelerra and yes it was a bitch to learn, but now I love it. LOTS of tutorials on YTube for both Cinelerra and Openshot.

You can chop the videos into chapters or have DVD styler do it for you

---

### Post by pixiq on 2012-02-16
Don't worry PDA1,

I find it easier to manage the videos from these new video cameras. Importing the files to linux is much easier, and as *LuridCinema* wrote, there are several tools that you can use to edit the footage, to get what you want. And now you have a definite statement that Cinelerra works for HD video clips :KS

---

### Post by PDA1 on 2012-02-16
I'm not so interested in a "cheapo" camera....unless that'll equal the quality of my current miniDV camera (which I'm really learning to hate).

Question-  Will one of those fancy High Definition video cameras (1000 x 700 or something like that) make a video that will retain the HD quality when put on a 4.5 Gb DVD?  

I don't understand how a HD video can fit onto a regular DVD?  I thought video would be too large?

Cinelerra....UGH.  I'll give it a try....again.

It's really hard to learn how to use those programs and that's why I stick with the Kino, DVDStyler, K3b method.  "Old dog (no kidding) new tricks"

Thanks folks.

---

### Post by pixiq on 2012-02-16
> **PDA1 said:**
> ...
Question-  Will one of those fancy High Definition video cameras (1000 x 700 or something like that) make a video that will retain the HD quality when put on a 4.5 Gb DVD?

One common HD frame size is 1280x720, another is 1920x1080. Obviously this is higher resolution than the standard DVD format, so it will occupy more disk space for the same quality (compression, frame rate ...). So if you want to retain the HD quality, the length of the movie must be shorter (and it may not conform to all the DVD standards). But most new computers and new TV sets can play mp4 files with frame size 1280x720 and frame rate 30 frames/s progressive without problems and the best ones will play 1920x1080/50p.
> 
I don't understand how a HD video can fit onto a regular DVD?  I thought video would be too large?

If you want to make a DVD movie, that can be played by 'every' DVD player, you should make it conform to some basic standard. That can be done using OpenShot. The frame size and frame rate of the exported video will fit, but you lose the HD quality.
> 
Cinelerra....UGH.  I'll give it a try....again.

It's really hard to learn how to use those programs and that's why I stick with the Kino, DVDStyler, K3b method.  "Old dog (no kidding) new tricks"

Thanks folks.
OpenShot is not very powerful, but it is often good enough and it is rather easy to learn :-)

---

### Post by coffee412 on 2012-02-16
Why not try kdenlive? I use it when I have video to edit and do things like add titles and other effects. Not that hard to learn really. 

For basic editing out unwanted video segments or changing to another format I have always enjoyed avidemux.

For burning to cd or dvd I use dvdstyler and k3b though.

---

### Post by PDA1 on 2012-02-16
I'm not sure if I commented here but in trying to install Cinelerra I got some error message...which I posted over on another thread.  The  program did open but I can't hear any audio.  Typical

---

### Post by pixiq on 2012-02-16
I run Ubuntu Studio 11.04 which has a lot of software for audio and video pre-installed, for example OpenShot.

---

### Post by PDA1 on 2012-02-16
'Just bought a Sony "Bloggie" Hd something-or-another for $140

Made a 30 second video and easily uploaded it to the computer.

Watched the video.....formatted the camera....wiped my finger prints off of the camera....put the camera back in the box...and will return it tomorrow.

Nice looking camera and easy to use.

Video output looks like junk...grainy....yellow....yuck.

My "old style" Sony miniDV is far superior in video quality though the resolution isn't HD.

I think if I got one of those "shoulder carried" video camera$ I'd be $ati$fied....and broke.


Anyone have any ideas for a good quality camera?

---

### Post by pixiq on 2012-02-17
I have a Panasonic SD700. I think there is a new camera with similar (slightly improved) specs today. It produces only 1920x1080 frame size and you can choose between progressive or interlaced.

I am satisfied with the quality from my camera, particularly when I use progressive rather than interlaced video.

---

### Post by PDA1 on 2012-02-17
The Panasonic looks like a fine camera and it's pretty nice that they have a 3-d lens for it.

Do you find the standard battery life is intolerable?

I was looking at a used Canon XL-1 (miniDV) but the videos youtube weren't all that impressive only because of the quality of those that were uploaded.

---

### Post by pixiq on 2012-02-17
I bought a second battery with higher capacity (not a panasonic battery, but a cheaper compatible one), and together those two batteries are enough for me. The camera was delivered with a 16GB flash card and I bought an additional 32 GB SDHC card.

---

### Post by cotcot on 2012-02-17
DVD iS 720 X 576 or 720 x 480 pixels. So you will have a reduction in quality unless you go for blue ray.
HD cams have mostly AVCHD format. Unfortunately not all cams use exactly the same AVCHD format.  I convert them using Blender VSE to mp4, avi or dvix before editing. 
Be aware that the Canon 25 p AVCHD format is recorded as 50 i (each frame is split in 2 half frames generated out of the same frame). Some editors have difficulties with it. Sound not synchronized or frame drops. Panasonic had the same AVCHD version as Canon (in the time i bought my HF100).
Kdenlive is fairly easy to learn. It will not take half of your life.
I recommend looking for a cam with a SDHC card slot. You do not need to 'capture' your video, just plug in the card and copy the files or connect the cam as an external usb mass storage.
I stopped burning DVD and I do not switch to blue ray because i play back directly from my simple laptop to the TV (use HDMI connection).

---

### Post by PDA1 on 2012-02-17
Very interesting.  I've got a lot to learn.  I had been wondering about the no-DVD anymore situation and it appeared as though that probably will be the case soon or people will start using Blu-Ray instead.

I'm very interested in the quality of the video (at least right now I am).  'Just bought some fancy TV today and watched regular commercial DVD's on it and was impressed by the overall quality.  My "home DVD's" look a little more "primative" than I'd hoped.

Earlier today I used DVgrab in Terminal which brought tears of joy to me as my old pal Kino was crashing too much.  DVgrab using the -a option even provides a file name blahblah.DV and a time stamp so it's somewhat perfect.

Kdenlive?  Ugh....maybe some day.

Would like to hear more of your thoughts on producing a video with Linux stuff.

Thanks

---

