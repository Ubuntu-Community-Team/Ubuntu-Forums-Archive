---
title: "Fastest mp3 encoder?"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by NoSmokingBandit on 2008-01-12
Im trying to convert a bunch of mp3 files to lower bitrate mp3 files using SoundConverter but it takes forever. I just did a 3:36 second song and it too an even two minutes to do it. My computer isnt fast but i can convert a whole cd in windows in about 5 minutes so i should be able to do it the same or faster in linux right? Well, what do you reccomend i use?

---

### Post by vambo on 2008-01-12
Could give lame a try. Note, command line only.

---

### Post by disturbedite on 2008-01-12
its generally considered very bad to convert from a lossy format to another lossy format.  (i.e. mp3 --> mp3).
the reason is, lossy formats throw away quality to get lower file size, etc.  so when you go from lossy to lossy you lose that much more quality.

if you want to use a lossy format, i'd recommend ogg vorbis.

i personally use flac tho, its a lossless format.  (meaning it does not throw away quality & you get the quality of your source file, whether its cd or whatever).

---

### Post by Ex-windows on 2008-01-13
Perhaps audacity would be faster. I am using to change our music over from ogg to mp3 so the wife can use her MP3 player. You will have to install the lame files for this to work.
Good luck

---

### Post by NoSmokingBandit on 2008-01-13
> **disturbedite said:**
> its generally considered very bad to convert from a lossy format to another lossy format.  (i.e. mp3 --> mp3).
the reason is, lossy formats throw away quality to get lower file size, etc.  so when you go from lossy to lossy you lose that much more quality.

if you want to use a lossy format, i'd recommend ogg vorbis.

i personally use flac tho, its a lossless format.  (meaning it does not throw away quality & you get the quality of your source file, whether its cd or whatever).

no offense, but does this really help me at all?

@Ex-windows:
I've only used audacity a few times, is there a batch-converting option in there somewhere? Thanks

---

### Post by ron999 on 2008-01-13
Hi
I have used a program called 'ConvertIT'.
It's a front-end for ffmpeg and mencoder.
It converts almost anything to anything and in the 'Sound' section there is 'ANY-MP3 Wizard', so you can set your required bitrate and batch-convert the files.
This is the link:-[http://ubuntuforums.org/showthread.php?t=567016]("http://ubuntuforums.org/showthread.php?t=567016")
:guitar:

---

### Post by ron999 on 2008-01-13
Sorry, I double-posted.

---

### Post by NoSmokingBandit on 2008-01-13
I had no luck with ConvertIt. It wouldnt output any files.

---

### Post by koleoptero on 2008-01-14
You can lower the quality of conversion in sound converter. Using normal should give you good speed and (if you want the converted files for a portable mp3 player) a relatively good quality.

Plus I don't think there are any other mp3 encoders than LAME available for linux (I could be wrong though).

---

### Post by NoSmokingBandit on 2008-01-14
> **koleoptero said:**
> You can lower the quality of conversion in sound converter. Using normal should give you good speed and (if you want the converted files for a portable mp3 player) a relatively good quality.

Plus I don't think there are any other mp3 encoders than LAME available for linux (I could be wrong though).

I said i had used sondconverter but is was agonizingly slow. I was going to 128kbps cbr mp3 and it took 2 minutes to do a 3:36 song which is really really slow.

---

### Post by ron999 on 2008-01-14
> **NoSmokingBandit said:**
> I had no luck with ConvertIt. It wouldnt output any files.

Pity that you couldn't get ConvertIT running. It works OK for me.
But I did a road test.
I took a 5min 45sec mp3 track encoded at 320Kbps, file size 13.2MB and converted it to 128Kbps, file size 5.3MB.
Using ConvertIT the job took 3 minutes. So it's probably not much quicker than the app that you're using.

---

### Post by Ex-windows on 2008-01-14
> **NoSmokingBandit said:**
> no offense, but does this really help me at all?

@Ex-windows:
I've only used audacity a few times, is there a batch-converting option in there somewhere? Thanks
 I am very sorry to take so long  I have been re installing all kinds of "stuff" lol. To answer your question (if you still r searching) So far as I have tried Audacity will batch convert a whole cd (folder) Maybe could do more but u would need to make your folder names and artist/album title. I have not tried to burn more than this  at 1 time.
Hope this helps and again I do apologise 4 the delay.
PS  Start with the Project button>import audio>The BATCH EXPORT= Export Multiple near the bottm after you import your files. Then you should get a box to title album and artist etc

---

### Post by disturbed1 on 2008-01-15
You'll get a speed hit, no matter which encoder, front end, tool, whatever, because the mp3 has to be decoded to wav first, then re-encoded back to mp3. So the time taken is not just mp3 encoding.

The fastest encoder is gogo-nocodda
> 
fast mp3 encoder based on lame
gogo-no-coda ("gogo") is a mp3 lossy audio codec forked from lame (or based on lame, whichever you prefer) with a target of simply being a fast implementation while keeping reasonable quality. But considering you would have to first decode the mp3 files to wav, there may not be any speed increase.

This is from a terminal -
```
lame --mp3input -b 128 input.mp3 output.mp3
```Just a basic lame command to re-encode an mp3 to 128kb mp3 using quality level of 2 (0=highest, 9=worse). You can add the -q option, putting in a higher number = faster encodes with worse sound quality.

A simple loop for the whole dir -
```
for i in *.mp3; do lame --mp3input -b 128 "$i" recode-"$1"; done
```same as above, but for every file that ends in .mp3 its re-encoded and renamed to recode-

To use lame decoding piped into gogo-no-codda
```
lame --decode input.mp3 - | gogo stdin -b 128 output.mp3
```lame will decode input.mp3 to stdin (-) and pipe (|) it to gogo. Gogo will from stdin (which is the decoded mp3 file) and encode it to 128kb output.mp3.

Simple loop to do the whole dir
```
for i in *.mp3; do lame --decode "$i" - | gogo stdin -b 128 recode-"$i"; done
```
gogo-no-codda package from rarewares attached below.

---

### Post by ron999 on 2008-01-15
Thanks for that disturbed1.

I installed gogo and repeated my road test using your command:-
```
lame --decode input.mp3 - | gogo stdin -b 128 output.mp3
```
It did the job in 1minute 10 seconds.
So I think you have a good solution.
:guitar:

---

### Post by Ex-windows on 2008-01-17
Would this program work to convert the.ogg into mp3??
Also I installed the program isthere a gui to it or only terminal?
Thanks

---

### Post by NoSmokingBandit on 2008-01-17
> **ron999 said:**
> Thanks for that disturbed1.

I installed gogo and repeated my road test using your command:-
```
lame --decode input.mp3 - | gogo stdin -b 128 output.mp3
```
It did the job in 1minute 10 seconds.
So I think you have a good solution.
:guitar:
Yeah, this works much better. Thanks a ton.

---

### Post by disturbed1 on 2008-01-17
Not sure about the gui. 

```
for i in *.ogg; do oggdec -Q "$i" -o -|gogo -b 128 -q 4 stdin "$i".mp3; done
```

^^ That should get you started. Change -b 128 to what ever bitrate you want, -q 4 to which ever quality level you want. 0 is highest quality and slowest, 9 is much, much faster, but lower quality.

Sound Converter is a GStreamer GUI that works with lame. Available in Synaptic.


YW - glad it worked out :D

---

### Post by stchman on 2008-01-17
> **NoSmokingBandit said:**
> Im trying to convert a bunch of mp3 files to lower bitrate mp3 files using SoundConverter but it takes forever. I just did a 3:36 second song and it too an even two minutes to do it. My computer isnt fast but i can convert a whole cd in windows in about 5 minutes so i should be able to do it the same or faster in linux right? Well, what do you reccomend i use?

Yes, it is much faster to rip a CD than convert MP3s to a lower bitrate.

Most MP3 to MP3 converters are going to be very slow.  My recommendation is to just re-rip the CDs that you got the music from.

You do know that sound quality will suffer from this.

---

### Post by Ex-windows on 2008-01-17
> **disturbed1 said:**
> Not sure about the gui. 

```
for i in *.ogg; do oggdec -Q "$i" -o -|gogo -b 128 -q 4 stdin "$i".mp3; done
```

^^ That should get you started. Change -b 128 to what ever bitrate you want, -q 4 to which ever quality level you want. 0 is highest quality and slowest, 9 is much, much faster, but lower quality.

Sound Converter is a GStreamer GUI that works with lame. Available in Synaptic.


YW - glad it worked out :D

Thanks for the input, cant wait to toy around with this tonite. When I started using ubuntu I did all our cd's in the .ogg not realising that we would be getting a "mp3" player lol. So now I am /was slowly redoing each cd from the music library on the HD. Hopefully I'll be able to figure this out.:)
Thanks again

---

### Post by disturbed1 on 2008-01-17
If you still have the original CDs, you would be much better off just ripping to mp3 using Lame. That is if sound quality is your number one concern.

---

### Post by NoSmokingBandit on 2008-01-17
> **stchman said:**
> Yes, it is much faster to rip a CD than convert MP3s to a lower bitrate.

Most MP3 to MP3 converters are going to be very slow.  My recommendation is to just re-rip the CDs that you got the music from.

You do know that sound quality will suffer from this.
The thing is, in windows (which is arguably slower than linux) i can convert mp3 to mp3 a whole lot faster than anything ive tried in linux.
And yes, i am aware that a lower bitrate = worse quality. If that were an issue i wouldnt be converting these songs to begin with.

---

### Post by ron999 on 2008-01-17
'whole lot faster' seems a bit vague.

Have you ran some conversions and compared gogo times against M$ times ?

---

### Post by NoSmokingBandit on 2008-01-17
gogo is probably about the same, but in soundconverter is was unbearably slow. Ill run a test here in a minute.

Edit:
Just ran a test, here is exactly what i did.
I shut my computer down. Truned it back on and booted into ubuntu. I copied The Mars Volta's Cicatriz ESP from my music hard drive onto my desktop. I then set it to convert in SoundConverter while talking to my friend on pidgin.
When that was done i shut my computer completely down again and botted into XP. I then copied the same song to my desktop and converted it in Fair Stars Audio Converter.
The song is 12:36 long and was ecoded as mp3 at VBR averaging 224kbps. In both programs i converted it to an mp3at 128kbps CBR.

In Ubuntu 7.10 it took 3:31. The play time divided by the converting time of the track (756 seconds/211 seconds) is 3.58. So it converted at about 3.6x real speed.
In Windows XP it took 1:58. The play time divided by the converting time (756/118) is 6.40. So it converted at 6.4x real time.

XP's time ratio divided by Ubuntu's time ratio (6.4/3.58) is 1.78. So Fairstars running in XP is 1.8 times as fast as Sound Converter running in Ubuntu.

---

### Post by disturbed1 on 2008-01-17
> **NoSmokingBandit said:**
> gogo is probably about the same, but in soundconverter is was unbearably slow. Ill run a test here in a minute.

Edit:
Just ran a test, here is exactly what i did.
I shut my computer down. Truned it back on and booted into ubuntu. I copied The Mars Volta's Cicatriz ESP from my music hard drive onto my desktop. I then set it to convert in SoundConverter while talking to my friend on pidgin.
When that was done i shut my computer completely down again and botted into XP. I then copied the same song to my desktop and converted it in Fair Stars Audio Converter.
The song is 12:36 long and was ecoded as mp3 at VBR averaging 224kbps. In both programs i converted it to an mp3at 128kbps CBR.

In Ubuntu 7.10 it took 3:31. The play time divided by the converting time of the track (756 seconds/211 seconds) is 3.58. So it converted at about 3.6x real speed.
In Windows XP it took 1:58. The play time divided by the converting time (756/118) is 6.40. So it converted at 6.4x real time.

XP's time ratio divided by Ubuntu's time ratio (6.4/3.58) is 1.78. So Fairstars running in XP is 1.8 times as fast as Sound Converter running in Ubuntu.

What codec are you using in Windows to convert/rip with? As seen, some mp3 encoders are faster than others. Quite a few *rippers* will use l3enc, l3fastenc, or even xing. These are not the same as Lame in SoundConverter. I'd say Fair Stars uses either l3enc or l3fast encode. You can encspot [http://www.guerillasoft.co.uk/encspot/index.html](http://www.guerillasoft.co.uk/encspot/index.html) to guess the encoder used.

---

### Post by kevdog on 2008-01-18
You could try this:
[http://mediacoder.sourceforge.net/screenshots.htm](http://mediacoder.sourceforge.net/screenshots.htm)

It works through wine, which a lot of times isnt optimal.  Ive used it in windows however and it provides for a fairly good GUI!

---

### Post by eye208 on 2008-01-18
> **NoSmokingBandit said:**
> In Ubuntu 7.10 it took 3:31. The play time divided by the converting time of the track (756 seconds/211 seconds) is 3.58. So it converted at about 3.6x real speed.
In Windows XP it took 1:58. The play time divided by the converting time (756/118) is 6.40. So it converted at 6.4x real time.
Encoding speed strongly depends on noise shaping quality. This is independent of bitrates. For example:

lame --cbr -b 128 -q 0 will encode at 1.37x speed.

lame --cbr -b 128 -q 9 will encode at [SIZE="5"]46x[/SIZE] speed. (Fast enough for you?)

As you can see, it's pointless to compare encoding speeds without looking at the quality of the final result. LAME can be just as fast as any other encoder if speed is what you are looking for. But if you are willing to trade speed for quality, LAME will not only outperform any other MP3 encoder but even rival some AAC encoders.

---

### Post by NoSmokingBandit on 2008-01-18
> **disturbed1 said:**
> What codec are you using in Windows to convert/rip with? As seen, some mp3 encoders are faster than others. Quite a few *rippers* will use l3enc, l3fastenc, or even xing. These are not the same as Lame in SoundConverter. I'd say Fair Stars uses either l3enc or l3fast encode. You can encspot [http://www.guerillasoft.co.uk/encspot/index.html](http://www.guerillasoft.co.uk/encspot/index.html) to guess the encoder used.

It uses Lame. I wont convert to mp3 without using lame. :D

@Eye208:
What Q value does soundconverter use?

---

### Post by Ex-windows on 2008-01-18
:)  WOW    I wish I knew all this stuff:confused:
I think I'll just go brew some more coffee:lolflag: and leave the geek stuff to you guys :lolflag:

---

### Post by disturbed1 on 2008-01-18
> **NoSmokingBandit said:**
> It uses Lame. I wont convert to mp3 without using lame. :D

@Eye208:
What Q value does soundconverter use?

Hmm, that is strange. I downloaded the demo, ran it through wine. It was pretty quick. Encspot reports the files as either using Xing or gogo. Eventhough lame_enc.dll is in the directory :confused: Encspot reports all my lame encodes as lame encodes. But that could mean anything ;) older versions of lame had the option of using the xing header to compensate for poor lame vbr header. So who knows.


The default q level in soundconverter is 2. I believe, since it doesn't store all it's settings in gconfig nor a config file. It's hard coded in the sourcecode, line 1070
> cmd = "lame quality=2 "Soundconverter is a python script, so you could open it in any text editor and hack away :D

---

### Post by NoSmokingBandit on 2008-01-18
> **disturbed1 said:**
> 
Soundconverter is a python script, so you could open it in any text editor and hack away :D

lol, i wish i could. im terrible at any kind of coding. I'll try some stuff out on soundconverter though, maybe ill learn something. Thanks!

---

