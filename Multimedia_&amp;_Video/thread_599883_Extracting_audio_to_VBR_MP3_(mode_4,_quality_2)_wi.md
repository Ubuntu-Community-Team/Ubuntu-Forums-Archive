---
title: "Extracting audio to VBR MP3 (mode 4, quality 2) with Sound Juicer"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by Zunino on 2007-11-01
Hello.

I have been trying to use Sound Juicer to rip and encode tracks through the gstreamer-lame plugin with the following custom gstreamer pipeline:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=4 vbr-quality=2 ! id3v2mux

My goal is to use lame's new VBR encoding algorithm with quality setting 2. What happens is that the ripping and encoding do take place, but when I check out the properties of the generated mp3 files on Rhythmbox, the 'details' tab says 128Kbps.

I assumed at first that it could be simply a problem with the way Rhythmbox reads the mp3 info, but then I noticed that the file size of the mp3s wouldn't change when I used the built-in 'CD-Quality, MP3' pipeline.

Has anybody been able to successfully produce VBR mp3 files with a pipeline like the one I presented here? Is there something missing or mispelled on that line?

FWIW, here are the software versions:

    * gstreamer-0.10
    * LAME plugin: 0.10.6
    * Sound Juicer 2.20.0

Thank you.

-- 
Ney André de Mello Zunino

---

### Post by GrouchoMarx on 2007-11-09
I'm having the same problem. As best I can tell it seems that either gstreamer or lame is failing to encode VBR. When I specify VBR, all I've been able to get are CONSTANT bitrates up to 160kbps. (When I SPECIFY a constant bitrate, I can get whatever constant bitrate I want).

The ACTUAL bitrate measurements where done using VLC's stream statistics.

Have you had any luck finding a solution?

---

### Post by GrouchoMarx on 2007-11-09
By the way, I can confirm that this doesn't happen in Feisty with the EXACT same gstreamer pipelines.

---

### Post by Zunino on 2007-11-13
> **GrouchoMarx said:**
> Have you had any luck finding a solution?
I ended up putting Sound Juicer aside and decided to try something else. After some searching around, I chose to install [Grip]("http://www.nostatic.org/grip/"). I am very happy with the tool, having configured it to use the lame encoder. The lame command line options I have been using are: 
```
-h --preset standard %w %m
```
It's not too hard to feel overwhelmed by the amount of configuration options that Grip offers, but I can assure you that it is worth spending some time with them. Be sure to check the documentation that comes with the software.

Good luck!

-- 
Ney André de Mello Zunino

---

### Post by rykel on 2007-11-24
> **Zunino said:**
> 

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=4 vbr-quality=2 ! id3v2mux



Hi,

Mine says

[INDENT]audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=**0** vbr-quality=**6** ! id3v2mux[/INDENT]

When I check the Properties of the ripped mp3, Rhythmbox says, "Unknown".

What exactly is the bitrate for mode 0 quality 6? If I want to rip speech CDs with the smallest filesize (eg. lowest bitrate) using a lame preset, what should I change in the line above?

Thanks for helping.

---

### Post by GrouchoMarx on 2007-11-24
To see what the lame options are and what they mean, in the CLI type:
```
gst-inspect-0.10 lame
```
You will see that mode=0 indicates stereo, and that there are 9 vbr-quality settings, with 0 being the best and 9 being the worst. You will also see a set of actual LAME presets (as opposed to just vbr-quality settings) and you can set these using the pipeline option "preset=XXXX" (where for example XXXX could be 1002, the extreme preset).

I don't recommend the lowest vbr-quality because the sound is actually quite bad, but something like 5 or 6, although still noticeably distorted on good sound systems, will sound fine on earbuds. However the actual LAME presets ([medium, standard, extreme and insane]("http://lame.cvs.sourceforge.net/*checkout*/lame/lame/doc/html/presets.html")) are apparently more efficient than simply setting vbr-quality, and for low files-size, "preset=1006" (medium) would be the way to go.

If you want to see the exact bitrate in real-time, you can open the file using vlc, then go to view > Stream and Media Info... and under the statistics tab you should see the bitrate in real-time (from which you can confirm that it is a variable bitrate, and also get a sense of the average bitrate).

---

### Post by rykel on 2007-11-26
Thanks, very helpful reply!

If I would like to rip each track (approximately 10min, speech) under 10MB (so that I can upload to mp3tunes.com) which preset should I apply?

---

### Post by GrouchoMarx on 2007-11-26
10 MB * (1024 KB/MB) * (1024 B/KB) * (8 b/B) / (10*60 sec) = 140 000 b/s  = 140 kb/s (target bitrate)

So the lowest LAME preset (medium), which should give you a bitrate "in the 150-180kbps range", might not be enough.

Instead you can try setting vbr-quality to 6 or 5, which should give you a bitrate of 128 or the next level higher.

Unfortunately I can't tell you what bitrate the next level higher is. Using gstreamer to encode LAME in Gutsy does not work as it does in Feisty. This is what I was complaining about earlier in the thread: when I set "vbr-quality" I can't get a bitrate larger than 128, and when I set "preset" I can't get a bitrate larger than 160. I have tried this on two fresh Gutsy installs on two seperate computers, and both gave the same result. Under feisty, the EXACT same gstreamer pipelines work as they should.

If you manage to rip LAME above a 160 bitrate in Gutsy I would love to know how.

---

### Post by GrouchoMarx on 2007-11-26
In fact, because of this error, I can't even be sure that vbr-quality 6 gives you an average bitrate of 128. You will have to experiment on your own. (But at least you know that you need less than or equal to 140 kbps).

---

### Post by superkikim on 2007-11-27
I've been trying gstreamer lame in sound juicer with the following params:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=2 ! id3v2mux

and 

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-mean-bitrate=256 vbr-min-bitrate=128 vbr-max-bitrate=512 vbr=4 vbr-quality=2 ! id3v2mux

The result is the same.

The problem I face is that the bitrate shown in the file audio properties is 32kbps

Obviously, this is not the case. My mp3 file is much better than a 128Kbps mp3 file. But as the track lenght is based on this record, my file (5.6MB) is shown to last for 25min... Confusing to calculate playlist, and also confusing for the @#%&ing iPod...

I WANT TO HAVE A (almost) PERFECT CONVERSION TO BE CORRECTLY PLAYED ON IPOD !!!!!!!! HEEEEEEEELP !!!!! sigh... :frown: 

My thought was finally: 

I should make a script that extract CDs in MP3 static rate (at 256Kbps) for the iPod and a second file in Ogg Vorbis for local use.... As I don't really have a problem or room (500GB available locally, and 80GB available in the iPod)...

Question is: how to make that damn script...

Anyway, computing is not for exigent people... It is so average... pffff.

---

### Post by GrouchoMarx on 2007-11-27
I think your problem might be solved by adding xingmux headers to your pipeline:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=2 ! xingmux ! id3v2mux
```

Besides that, how long (in minutes:seconds) is the file? 5.6 megs seems pretty small for a high quality (vbr-quality=2) mp3. Are you sure that it's actually ripping at the bitrate that you want? My problem is that I can't get a bitrate above 160 kbps.

---

### Post by superkikim on 2007-11-29
> **GrouchoMarx said:**
> I think your problem might be solved by adding xingmux headers to your pipeline:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=2 ! xingmux ! id3v2mux
```

Besides that, how long (in minutes:seconds) is the file? 5.6 megs seems pretty small for a high quality (vbr-quality=2) mp3. Are you sure that it's actually ripping at the bitrate that you want? My problem is that I can't get a bitrate above 160 kbps.

Thank you so much. It works... Can you explain what xingmux does ?

Regarding the max bitrate, you can add vbr-min-bitrate and vbr-max-bitrate. Without these: FIle size 5.6MB

```

10. Snap! - It's Not Over.mp3
-----------------------------

Bitrates:
------------------------------------------------------------
 32                                                     0.1%
112                                                     0.1%
128                                                     0.2%
160     ||||||||||||||||||||||||||||||||||||||||       99.6%
------------------------------------------------------------

Type                : mpeg 1 layer III
Bitrate             : 159
Mode                : stereo
Frequency           : 44100 Hz
Frames              : 11335
Length              : 00:04:56
Av. Reservoir       : 30
Emphasis            : none
Scalefac            : 2.8%
Bad Last Frame      : no
Sync Errors         : 0
Encoder             : Lame 3.97
Lame Header         : No

```

With vbr-min-bitrate=64 vbr-max-bitrate=320: File size: 7.8MB

```

10. Snap! - It's Not Over.mp3
-----------------------------

Bitrates:
------------------------------------------------------------
 32                                                     0.1%
 64                                                     0.0%
 80                                                     0.0%
112                                                     0.0%
128                                                     0.3%
160     |||||||                                         6.4%
192     ||||||||||||||||||||||||||||||||||||||||       34.9%
224     |||||||||||||||||||||||||||||||||||||          32.9%
256     ||||||||||||||||||||                           17.7%
320     ||||||||                                        7.6%
------------------------------------------------------------

Type                : mpeg 1 layer III
Bitrate             : 221
Mode                : stereo
Frequency           : 44100 Hz
Frames              : 11335
Length              : 00:04:56
Av. Reservoir       : 59
Emphasis            : none
Scalefac            : 3.2%
Bad Last Frame      : no
Sync Errors         : 0
Encoder             : Lame 3.97
Lame Header         : No

```

And it is done in seconds :-D 

You will find all settings about the options for MP3 encoding with sound juicer at [https://lists.ubuntu.com/archives/ubuntu-users/2005-July/043363.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-July/043363.html)

If you understand some of these that might drasticly change the quality :-) Let me know ;-)

Cheers

------------------------------------------------------------------------------------

Beside that, I've made some tests. In the link above, they say there is no maximum for vbr-max-bitrate. Therefore I tried at 512 and 1024... It doesn't work. If you go over 320, that setting is just ignored.

Also I've tried to change the vbr-quality parameter... This is what determines the average bitrate.. For exemple, with vbr-quality removed (default is therefore 6), the result for the same file is for 5.8MB:

```
GStreamer Pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-min-bitrate=128 vbr-max-bitrate=320 ! xingmux ! id3v2mux
```

```
10. Snap! - It's Not Over.mp3
-----------------------------

Bitrates:
------------------------------------------------------------
 32                                                     0.1%
128     |||||||                                        12.1%
160     ||||||||||||||||||||||||||||||||||||||||       65.8%
192     ||||||||||                                     16.6%
224     ||                                              4.2%
256                                                     0.9%
320                                                     0.2%
------------------------------------------------------------

Type                : mpeg 1 layer III
Bitrate             : 165
Mode                : stereo
Frequency           : 44100 Hz
Frames              : 11335
Length              : 00:04:56
Av. Reservoir       : 53
Emphasis            : none
Scalefac            : not used
Bad Last Frame      : no
Sync Errors         : 0
Encoder             : Lame 3.97
Lame Header         : No

```

However with vbr-quality set to 0 (the highest), the resut is for 8.4MB:

```

10. Snap! - It's Not Over.mp3
-----------------------------

Bitrates:
------------------------------------------------------------
 32                                                     0.1%
128                                                     0.1%
160     |                                               1.2%
192     |||||||||||                                    13.7%
224     ||||||||||||||||||||||||||||||||||||||||       46.0%
256     ||||||||||||||||||||||                         26.0%
320     |||||||||||                                    12.8%
------------------------------------------------------------

Type                : mpeg 1 layer III
Bitrate             : 239
Mode                : stereo
Frequency           : 44100 Hz
Frames              : 11335
Length              : 00:04:56
Av. Reservoir       : 64
Emphasis            : none
Scalefac            : 3.9%
Bad Last Frame      : no
Sync Errors         : 0
Encoder             : Lame 3.97
Lame Header         : No

```

While above the result was for vbr-quality=2 a bit different.

But still, CD quality is not really achieved :-(

In the below picture, you can see on the left the mp3 file above, and on the right the CD. There still a loss :-( Result is sound is a bit less "crystal clear" with the MP3. But still far much better then CBR or lower quality VBR

[IMG]http://www.sissaoui.com/pics/mp3vsCD.png[/IMG]

Still I'm not sure what this is measuring. I've tried to make a MP3 at 48000 Hz and the gap is bigger. So I guess the left pic show 44100 Hz, and the right pic (the CD) show less... I don't know how to find out what is the frequency on the original CD :-) I've made a "WAV lossless" extract, and it says 22050 Hz ?!?! If true, that would be quite poor for a CD :-(

If anyone knows a tool similar to encspot and that works for Ogg Vorbis, AAC WAV and MP3, I'd like to make some more tests.


Cheers

Akim

---

### Post by eye208 on 2007-11-29
> **Zunino said:**
> but when I check out the properties of the generated mp3 files on Rhythmbox, the 'details' tab says 128Kbps.
Keep in mind that there is no bit rate field in the ID3 header of an MP3 file, and even if there was one, it wouldn't be authoritative in any way.

An MP3 file consists of frames, and each of these frames has its own header with a bit rate field in it. This is what makes VBR possible in the first place. In order to accurately identify the average bit rate of a VBR MP3 file, the player application would have to scan the whole file. Since this is quite time time-consuming (and impossible in the case of streaming content), most players either
[LIST]
[*]display the bit rate of the first frame or
[*]guess the average bit rate from the file size and the ID3 TLEN (recording length) field.
[/LIST]
Both methods are inaccurate in their own ways.

The bottom line is: Sound Juicer, GStreamer and LAME are not at fault here. Inaccurate bit rate readings are something you just have to live with if you use VBR. In fact it's pure luck if some player manages to show an accurate value.

---

### Post by eye208 on 2007-11-29
> **superkikim said:**
> [IMG]http://www.sissaoui.com/pics/mp3vsCD.png[/IMG]
What you can see in the picture is LAME's low-pass filter at work. You can turn it off at the encoding stage by adding -k to the LAME command line. This is not advisable for low bit rates, but since you prefer quality over size reduction, it might work well for you.

---

### Post by GrouchoMarx on 2007-11-29
I believe xingmux adds extra header information specifying various properties for VBR mp3s.

My problem however is that I can't get VBR to work properly.

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 bitrate=256 ! xingmux ! id3v2mux
```

works fine and gives me 256 kbps constant bitrate mp3s. But if i want to create variable bitrate mp3s then:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=0 ! xingmux ! id3v2mux
```

or any other pipeline that specifies vbr, fails. I end up with an mp3 of much lower quality (<160kbps) and filesize. These same pipelines worked perfectly in feisty, but fail under gutsy. I've tried it on two computers with fresh installs and got the same result. I wish I knew why. I'm pretty sure that I'm using the pipelines correctly if only because they worked in feisty. I also can't imagine that I'm the only one experiencing these "out-of-the-box" issues, but maybe people just aren't noticing that their mp3s are lower quality than they specified.

---

### Post by 12barz on 2007-11-29
GrouchoMarx is not alone.  I'm having the same problem.  I've never gotten Sound Juicer to work, but got decent results in Feisty with Grip.  Since "upgrading" to Gutsy, Grip is giving me mp3's that Amarok says are 32 bitrate.  I've tried changing the command line from specific VBR settings to preset settings.  Nothing works.  Should probably be reported as a bug, but I'm not sure where to report it.

---

### Post by GrouchoMarx on 2007-11-30
> **12barz said:**
> GrouchoMarx is not alone.  I'm having the same problem.  I've never gotten Sound Juicer to work, but got decent results in Feisty with Grip.  Since "upgrading" to Gutsy, Grip is giving me mp3's that Amarok says are 32 bitrate.  I've tried changing the command line from specific VBR settings to preset settings.  Nothing works.  Should probably be reported as a bug, but I'm not sure where to report it.

Have you tried adding xingmux headers to your mp3s? I'm not sure how you would specify that in Grip, but adding xingmux headers seems to solve the problem of the bitrate not being "reported" correctly. Getting the right bitrate in the first place is another story.

---

### Post by eye208 on 2007-11-30
If xingmux is not available outside the GStreamer realm, any other ID3 tagging tool might do the trick as well.

---

### Post by superkikim on 2007-11-30
> **GrouchoMarx said:**
> I believe xingmux adds extra header information specifying various properties for VBR mp3s.

My problem however is that I can't get VBR to work properly.


Gotcha... You didn't read my entire reply [-X

Ok, I admit it was a bit long and messy :lolflag:

As I say above, you need to use vbr-min-bitrate and vbr-max-bitrate.

Have a look to [that page for details]("https://lists.ubuntu.com/archives/ubuntu-users/2005-July/043363.html"). And if you understand some settings that might change drasticly the quality fo mp3s, tell me ;-)

My current gstreamer pipeline:
```
GStreamer Pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-min-bitrate=128 vbr-max-bitrate=320 ! xingmux ! id3v2mux
```

Do not try vbr-max-bitrate over 320... You will end again with a constant at 160 :-) 320 is the maximum, even if the above post says there is no maximum.

---

### Post by GrouchoMarx on 2007-11-30
> Gotcha... You didn't read my entire reply

Ok, I admit it was a bit long and messy

As I say above, you need to use vbr-min-bitrate and vbr-max-bitrate.

I did in fact try vbr-min-bitrate and vbr-max-bitrate. I've tried almost every combination of vbr settings. In fact, all the information on that page you mentioned is available via the command:

```
gst-inspect-0.10 lame
```

As far as which settings will improve the quality, besides the obvious fact that higher bitrates are better than lower, that variable bitrates are better than constant bitrates, and that the "new" vbr algorithm is better than the "old" algorithm, the only other thing I've read (from lame's documentation) is that the lame "presets" (medium, standard, extreme and insane) are apparently better (more efficient?) than just setting the vbr quality/bitrate.

---

### Post by superkikim on 2007-12-02
> **GrouchoMarx said:**
> I did in fact try vbr-min-bitrate and vbr-max-bitrate.

And still, you get 160 max only ?!?

Did you try to just copy-paste my pipeline above ? I woul'd be surprise if it gives different results in two different computers... At least no so different.

Try that pipeline and tell me...

Thank you for the gst-inspect tip

---

### Post by GrouchoMarx on 2007-12-02
Yes, if I copy and paste that gstreamer pipeline you gave earlier:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-min-bitrate=128 vbr-max-bitrate=320 ! xingmux ! id3v2mux
```

Then I get a fairly constant bitrate around 160 kbps. However, I've just discovered that if you take this exact pipeline and bump the minimum bitrate above 160, then you can get a CONSTANT bitrate mp3 at that minimum bitrate you set. Still very weird.

Re: the results should be the same on different computers. I completely agree since encoding *shouldn't* be architecture dependent. However I wanted to somehow account for the fact that relatively few people seem to be having this problem. (Though there are definitely other people having the problem: [Is gstreamer limiting your LAME bitrate???]("http://ubuntuforums.org/showthread.php?p=3872011#post3872011")). One of my theories is that some people just aren't noticing because it worked in Feisty, and so they don't notice the smaller filesizes and the lower bitrates.

If someone can figure out a way to directly test the lame libraries through the CLI, that would go some way to isolating the problem.

---

### Post by superkikim on 2007-12-04
> **GrouchoMarx said:**
> Yes, if I copy and paste that gstreamer pipeline you gave earlier:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-min-bitrate=128 vbr-max-bitrate=320 ! xingmux ! id3v2mux
```

Then I get a fairly constant bitrate around 160 kbps. However, I've just discovered that if you take this exact pipeline and bump the minimum bitrate above 160, then you can get a CONSTANT bitrate mp3 at that minimum bitrate you set. Still very weird.


you talk about Constant ? Why ? How do you measure your bitrate ?

---

### Post by GrouchoMarx on 2007-12-04
> you talk about Constant ? Why ? How do you measure your bitrate ?

I am measuring the bitrate realtime with VLC (view > stream and media info > statistics). You will see a variable bitrate fluctuate between whatever minimum and maximum bounds have been encoded. A constant bitrate will remain, well, constant. However in my case:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-min-bitrate=128 vbr-max-bitrate=320 ! xingmux ! id3v2mux
```

The VLC statistics show a bitrate of 160 kbps that DOES NOT fluctuate. Moreover, the file size and the length of song indicate an average bitrate of 160 kbps. However, the bitrate should be fluctuating between 128 and 320 kbps, and have an average bitrate of around 224 kbps. Unfortunately, this problem seems to happen with any other gstreamer pipeline that specifies a variable bitrate.

---

### Post by 12barz on 2007-12-10
Well, I've tried xingmuxing my pipeline and wound up with 128 CBR files.  Take a look at launchpad Bug #35112.  Is our problem connected to that gstreamer bug?  If so, may be bad news since it's been around for a while and still not fixed.  I'm worried that the importance level of the bug was only listed as medium.  Could this reflect a kind of ogg-supremacist, anti-mp3 bigotry in the upper geekmosphere of Ubuntu?  I hope not.  Even if ogg has superior attributes and the proprietary stance of mp3 patent holder's ticks us off, mp3 is still the lingua franca of the music world.  Ubuntu can't have credibility with musicians or others in the music community without vbr mp3 capability.  I'm getting it from Ripper-x now, but I wish I could have finer control over the properties than the Ripper-x interface gives me.  Sure wish we could have gstreamer and Sound Juicer fixed to act right.  Check out bug #35112 and see what you think.

---

### Post by jocheem67 on 2007-12-10
If it's about control then just use grip or even lame from the commandline:

lame --vbr-new -V 1  song.wav song.mp3 

Should do the trick....

However I'm too interested in getting gstreamer to work, just for the fun of it....

Still lame directly used is the strongest method in encoding to mp3...

---

### Post by GrouchoMarx on 2007-12-10
> Take a look at launchpad Bug #35112. Is our problem connected to that gstreamer bug?

If the problem you're referring is that the song lengths are being mis-reported, then bug #35112 seems to be connected. However, if you're referring to the fact that the ACTUAL lame bitrate is being capped by gstreamer, then I don't think so.

> lame --vbr-new -V 1 song.wav song.mp3 

Thanks for that! I was looking for some way to rule out lame as the source of the problem. Now using lame from the command line I can get high-quality variable bitrates. Obviously it's not being piped through any external tagging software (xingmux, id3v2mux) and so the bitrate won't reported properly by most media players, but using VLC's real-time stream statistics you can see that it is in fact a high-quality (~224 kbps) variable bitrate.

Although this will be useful in the interim, there's the added complication that lame only handles certain bitwidth wav files (8, 16, 24, and 32), which I don't know how to make using Sound Juicer.

@jocheem67: Just to confirm, you see the bitrate being capped at ~160 kbps with gstreamer?

> Even if ogg has superior attributes and the proprietary stance of mp3 patent holder's ticks us off, mp3 is still the lingua franca of the music world. Ubuntu can't have credibility with musicians or others in the music community without vbr mp3 capability.

Also, mp3s are necessary if you want to play your music on portable music players. (Unfortunately, and through no fault of the developers, ogg is not compatible with the majority of music players :().

---

### Post by GrouchoMarx on 2008-01-06
I have posted a simple (if not ideal) workaround in the following thread: [Is gstreamer limiting your LAME bitrate???]("http://ubuntuforums.org/showthread.php?t=608034")

---

### Post by thebrade on 2008-02-19
This thread has been a major help. I was starting to wonder if anyone even knew what the various vbr settings did. My only question is for superkikim: what command did you run to get those bit-rate outputs for your various test cases?

---

### Post by thebrade on 2008-02-22
Another question. The resulting mp3's from using this gstreamer line in sound juicer:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=0 vbr-min-bitrate=128 vbr-max-bitrate=320 ! xingmux ! id3v2mux

sound great, but the track times are totally wrong. I've seen this happen when encoding VBR mp3's before. is there a fix for this issue? usually the times adjust correctly when you start playing them, but it's just retarded looking, and it seems to happen on every player (including the PS3).

---

### Post by GrouchoMarx on 2008-02-22
Hmm, the "! xingmux" should have taken care of the track length problem. Double check that you have the "gstreamer0.10-plugins-bad" package installed. It contains the xingmux libraries.

---

