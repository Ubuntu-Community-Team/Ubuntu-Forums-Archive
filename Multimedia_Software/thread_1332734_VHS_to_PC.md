---
title: "VHS to PC"
date: 2009-11-20
forum: Multimedia Software
---

### Post by spegru on 2009-11-20
I've been trying to get rid of piles of old tapes, but some of the stuff is actually quite good so it seemed obvious to rip them before putting them in the garage so they don't occupy space in the house any more and providing proof against the likely lack of any VHS machine on which to play them on in the future. (I don't want to infringing any copyright!!)

My first attempts not too bad. I used a  VHS/DVD machine to rip several tapes to DVD and then ripped the DVD in the PC using Acidrip. Works pretty well although a bit slow as both steps only run at normal speed (so that's 4 hours in total for a 2 hour tape!) but never mind.
(I was also able to save wasting loads of DVDs by using the same DVD over and over, reformatting it each time.)

However then I ran into problems with some tapes which are copy protected (I still have the original so that's allowed). Funny, I have been using VHS for years and never knew about this till the other day. Anyway unfortunately the makers of the (unknown brand from Maplin) VHS machine had nevertheless incorporated this system and so it refused to copy to DVD. So I needed an alternative.

After a bit of research I came up with this almost 100% system going direct from VHS to PC.
Clearly no PC I ever saw has a scart connector, but many do have s-video and or composite video. However as far as I can tell normal graphics cards that have these use them as outputs only which is no use.
On the other hand many old analogue TV cards also have them and those ones are inputs!
Mine is a no-name analgue card from several years ago, but if you type 'lspci' into a terminal you get  
Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
Thus it is revealed to use a philips chipset which is likely to be widely used

The next problem was that one of my VHS machines did not have s-video connector (a little round 4 pin din thing) or Composite (yellow coaxial plug) and the other would not use them as outputs for VHS (DVD only for some reason). Composite is lower quality anyway.
Both machines had scart but my scart to composite adaptor seemed not to work either. Why? well it turns out that these are made as either inputs or outputs and of course you have to use the right sort. Mine was wrong.

So in the end I got a scart to composite/s-video adaptor that could be set to output or input with a switch.

So I connected the s-video cable between the VHS machine and the PC Analogue TV card input. Then, using XawTV I was able to select s-video as an input instead of the TV tuner and when I set the TV format to be PAL I got a picture on the PC. I also connected the red/white coax audio connectors to the line-in, but that was much too loud so I used mic input. I also had to select the record tab in sound preferences and make sure the correct input was being used.
Fantastic, XawTV can not only show the video but also record it (as long as you choose AVI instead of multiple images).
So now I got a pretty good result

The only remaining problem is I got some faint diagonal stripes on the picture. Perfectly watchable but not quite as good as the VHS-DVD-PC method. 
Ideas on that appreciated.

I hope that helps people rescue those old family/wedding/irreplaceable videos etc and preserve them for the probable VHS-free future!

---

### Post by gslug79 on 2009-11-20
I am also in the process of converting a number of VHS tapes. I brought a S-Video/Composite to USB dongle (Kworld DVD Maker 2) as Google suggested it could be made to work with Linux, but never managed to get the sound to work and found the video quality to be terrible.

Like you, I thought about burning to DVD and then ripping, but eventually came up with a really "hacky" solution: Transfer the tapes to a hard disk PVR, remove the hard disk and put it in a USB enclosure. Copy the content to the computer. This worked perfectly.

I am not sure the above solution will work with all PVRs - I guess some may use proprietary formats and/or some form of DRM, but mine just recorded MPEG2 files onto a FAT32 disk.

As for the VHS copy protection - I guess this is Marcovision. I believe there are ways to remove it, but haven't tried them as all of my tapes were home recorded.

---

### Post by lukeiamyourfather on 2009-11-20
Any video card or capture card that can capture composite or S-Video should do the trick. There are tons of capture cards and video cards that can capture for as little as $20 from places like Newegg. Record the live stream from the capture card using whatever software you want in Linux which will store the video on your hard disk as it goes. No need for these Rube Goldberg solutions of transferring here and converting there. Also since its not going from one lossy source to another (like transcoding from a DVD) you get better picture and audio quality too. Cheers!

---

### Post by stinger30au on 2009-11-20
for original movies like home made movies i converted them ages ago to dvd

i connected my dvd player to my lg dvd recorder in the lounge and let it do all the hard work for me


to cut to dvd i used single layer dvd discs

once cut to dvd i can then copy/burn with linux/win or what ever till the cows come home


for movies from disney etc you have on tape, dont even bother to convert them to dvd

i would go hunting online and see if you can find a rip of them

---

### Post by spegru on 2009-11-21
I agree that sometimes it's hardly worth the effort of ripping VHS, due to the lower quality and yes presumably if you have the tape that should allow you to own a rip in any format, wherever  it came from. However not all content is available and besides, having so many tapes it probably is just about worth the effort - for some stuff anyway.
Besides, I like the challenge!

Just one thing I'/d like to know is how to get rid of those faint diagonal stripes. Any ideas?

---

### Post by spegru on 2009-12-02
I am wondering if there is a better application to look a the tv input with. VLC woiuld seem to be an option but I don't know how to find out what the video device name is (required for the VLC config)
Anyon know how to find out?
It can't be that difficult as XawTV already works

---

### Post by richard32 on 2009-12-05
In VLC Media/Open Capture Device/Advanced options, select input as 1 for composite usually.

The application TvTime also may work for you.

You may need to specify your TV format in these applications.

/dev/video0 may be the device you are looking for if you do need to specifiy it. Drop into a terminal and run dmesg to see which is registered.

---

### Post by spegru on 2010-02-04
I've been using xawtv. Seems to be the only app that can pick up the s-video input. It's pretty crude though - video display locks while recording and since 9.10/mint8 I cant get audio to play through speakers either - presumably due to pulseaudio issues.
Another thing I noticed was it was unable to see the tv card as a source until I unplgged my webcam
TV seems to be more of a problem on linux than it ought to be.......

---

### Post by spegru on 2011-01-31
I've just started  having another go at this.
I'm still using xawtv because that's the only system that I can find that can access the s-video input port of the TV card.

It works, even with protected pre-recorded tapes, but I have two problems

No sound during the recording process, although the recorded file has it ok. I guess this is because xawtv is old and doesn't play nicely with pulse audio.

Pretty poor video quality. It's ok for watching in a smallish window but fairly dire if in full screen due an odd stripey pattern. I think that may be because of poor resolution in the recording process - which is stuck on 384x288, and I cant find a way to increase it. I am guessing this may be a limitations of xawtv and/or the TV card.

In noticed Richard32 suggested using VLC instead but I can't find a way to select the s-video port, so it sticks on analogue TV. The video address is /dev/video0 and the only alternative is /dev/video1 which doesnt work at all. Also I can't find the equivalent for sound, and I guess it may be different with pulse anyway.

Does anyone out there know how to configure the system to use s-video input port, and has anyone had any good results using another method or another method?

---

### Post by spegru on 2011-01-31
answering my own question.....
From here [http://superuser.com/questions/75406/vlc-streaming-with-v4l2-how-can-i-choose-the-input-channel-svideo](http://superuser.com/questions/75406/vlc-streaming-with-v4l2-how-can-i-choose-the-input-channel-svideo)
I found that VLC has an advanced options button on the capture device tab.
The capture device on my setup is /dev/video0
However under 'advanced options' there is an 'input' to set. Since, in xawtv the s-video input was the 4th on the list I chose 4 - but that didn't work of course because the numbers start from zero, so I chose 3 instead and it works!
You can also choose the bitrate, file format and many other things which is way better than xawtv!
If recording from a tape onto the pc then under media, you need to choose save/convert rather than open, and then set the options. When it's fianlly running, it's streaming to the file you made 
All I need to do now is to find out how to get the sound synchronised
To be able to watch and stream at the same time would also be nice!

---

### Post by spegru on 2011-02-02
Answering myself a bit more (I can always use this as a reference in future!), I discovered that using the normal analogue tuner and the RF out from the VHS machine offers better quality because the faint diagonal stripes are gone.
BTW to tune the analogue tv in xawtv you have to type ctrl - (up arrow).
Although the resolution appeared to be higher the final file size was almost identical (~2Gb for a 1.5hr movie)

---

### Post by spegru on 2011-02-02
The odd thing about the quality is that I had always assumed that s-video would be better quality so I am surprised that it is not.
Although it's a long time ago now I remember that going through Scart instead of RF was a better quality connection between VHS and TV.
So I suspect I've still not found the best way.
I have not yet tried the composite video (yellow RCA plug)......

---

### Post by spegru on 2011-02-02
Ok I reckon I'm done now.
I found a composite video cable and can report that it is verry slightly better than going through RF. I suppose I had forgotten just how bad VHS tapes were!

I also tried VLC player instead of xawtv and that made no difference to the quality although I did experience a massive 20 odd second delay on audio that way. I didnt bother solving that as I just used xawtv instead which was fine.

If you want to persevere with VLC then the way to get the right port is under open capture device > advanced > input, and select the number of the input from 0-3 for RF, Composite 1, Composite 2, and S-Video.
 
S-video always seems to have these faint diagonal stripes and Composite is slightly better than RF and you dont even need to tune in the RF. So for best results choose input 1 or 2 on VLC, or just from the menu on xawtv

Other than that I guess you might get better results than me by a better VHS machine (although this one is pretty good I think) or a better TV tuner card for the PC

BTW when you do lsusb my tuner comes up as 
Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
but in fact I think it's just a basic old hauppauge analogue tuner.

I'm quite pleased with this as a way for backing up old VHS tapes you already own - and you don't even need to bother with copying to DVD or something first

Oh yes and you can also edit the resulting avi files using avidemux

bye!

---

