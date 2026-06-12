---
title: "24/96 Files Play Sllooowwllly"
date: 2012-05-15
forum: Multimedia Software
---

### Post by TheYetiWakes on 2012-05-15
Hi

Before moving over to Ubuntu one of the other things I done a while back was sell off my vinyl collection but not before converting a lot of hard to find stuff to FLAC.

Now being an overkill sort of chap and wanting to lose as little quality as possible and not knowing what I may need them for in the future these were done as 24/96 Flac files.  On windows they play fine but in Ubuntu (12.04) they play at about quarter speed, if that.  Quite amusing to listen to for about 10 seconds but that's it.  I have some others that have been converted (in windows) from the original 24/96 Flac to apple .mp4.  (I know but the other half moaning and wanting to play them in itunes it was just easier).  These also play slowly in Ubuntu so I'm thinking that perhaps its not so much the filetype but the original encoding and even if I some how convert these to some other type the problem will remain?

Is this a known problem?  I done some searching but couldn't find anything relating to this.  All other FLAC and Mp3 / Mp4 files play fine.  Its just the 24/96 ones.

Many thanks in advance.

---

### Post by TheYetiWakes on 2012-05-21
Bump.

---

### Post by shantiq on 2012-05-21
which player are you using Yeti?


also   run one of your files in mediainfo  if you do not mind   see what is in there


in synaptic on 12.04 or [**elsewhere**]("http://mediainfo.sourceforge.net/en/Download/Ubuntu")


or upload a file somewhere and link it here so it can be tested    :]

---

### Post by TheYetiWakes on 2012-05-21
> **shantiq said:**
> which player are you using Yeti?

I use Banshee as standard but have tried in Rhythmbox and Amorak with the same results.

> **shantiq said:**
> also   run one of your files in mediainfo  if you do not mind   see what is in there

Ok, im away from computer until later today but will try and report back.  Thanks.

---

### Post by TheYetiWakes on 2012-05-21
I've put a few of the files through mediainfo as suggested.  

Certainly something odd coming back.  There seems to be quite a range of sample rate khz reported for each file in Ubuntu.  Below are the first random 3 I tried.

English 5199kps, 60.9khz, 24bits, 2 channels FLAC
English 2564kps, 30.5khz, 24bits, 2 channels FLAC
English 2787kps, 30.5khz, 24bits, 2 channels ALAC


These are reporting (and playing correctly) as 96khz under Windows?  Could this be a codec installation problem?

---

### Post by flemur13013 on 2012-05-21
Post a link to one of the files (a short one) and I'll see if it plays in foobar.

---

### Post by shantiq on 2012-05-21
yes please if you can a sample would be great



av a look at this here too [**How do I know if my system is capable of playing 24bit/96kHz sound?**]("http://askubuntu.com/questions/19212/how-do-i-know-if-my-system-is-capable-of-playing-24bit-96khz-sound")


but if it does in windows it should too in Ubuntu you'd think


this is to see what u have

> cat /proc/asound/card0/codec#2



now checking it for myself i find this

> cat /proc/asound/card0/codec#2
Codec: Nvidia GPU 0b HDMI/DP
Address: 2
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de000b
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
   ** rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000**
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0


---

### Post by TheYetiWakes on 2012-05-21
Well I don't have a codec#2 file present in that directory but running it on codec#0 returns a lot of information including several instances of supported rates for the various outputs. ( SPDIF, analog etc).  But they all mention the correct rates and bits.


```

PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM

```

I shall try and upload a file but I have very slow internet out here in the sticks (about 0.4Mbps) and the smallest I can see is around 60mb.  If I can get one up before its time to leave for the pub i'll post the link! ;)

In the meantime I shall have a look at Sound Exchange too and see whats what.  I've tried converting some of them with DBPowerAmp convertor in windows but I get the same result as it won't let me alter the actual sample rate, just the filetype.

Many thanks for your help so far, much appreciated.

---

### Post by flemur13013 on 2012-05-21
Here's some 24bit / 96Khz samples: 

[http://01688cb.netsolhost.com/samplerdownload/](http://01688cb.netsolhost.com/samplerdownload/)

and 

[http://www.highdeftapetransfers.com/downloadinst-template-php-w5.php](http://www.highdeftapetransfers.com/downloadinst-template-php-w5.php)

Foobar & vlc tell me they're 24bit/96KHz; audition tells me they're 32 bit.

They play fine in vlc and foobar+wine; audition+wine gets confused (and thinks it's 32 bit).

alsamixer tells me: HDA nVidia / Realtek ALC888 (regular low-end built-in sound) with ubuntu12.04, no special drivers or software. 

You might try VLC - from what I've seen the standard linux music-players - rhythmbox, etc - are pretty buggy.

Edit: my codec#0 entries look like yours.

---

### Post by TheYetiWakes on 2012-05-21
Right

I've managed to upload one here to Dropbox.  It is actually one of the ones I had converted to ALAC .m4a to use in iTunes but its the smallest file I can find quickly (76mb).  I'll upload a flac if needed.

[http://db.tt/qkrWk5xr](http://db.tt/qkrWk5xr)

(Hope you like prog folk)!

Had a quick look at Sox but it doesn't seem to handle .m4a filetypes, I shall dig deeper on this though as it looks promising. 

Many thanks again

---

### Post by TheYetiWakes on 2012-05-21
> **flemur13013 said:**
> Here's some 24bit / 96Khz samples: 

[http://01688cb.netsolhost.com/samplerdownload/](http://01688cb.netsolhost.com/samplerdownload/)

and 

[http://www.highdeftapetransfers.com/downloadinst-template-php-w5.php](http://www.highdeftapetransfers.com/downloadinst-template-php-w5.php)

Foobar & vlc tell me they're 24bit/96KHz; audition tells me they're 32 bit.

They play fine in vlc and foobar+wine; audition+wine gets confused (and thinks it's 32 bit).

alsamixer tells me: HDA nVidia / Realtek ALC888 (regular low-end built-in sound) with ubuntu12.04, no special drivers or software. 

You might try VLC - from what I've seen the standard linux music-players - rhythmbox, etc - are pretty buggy.

Edit: my codec#0 entries look like yours.

Many thanks Flemur, you must have posted as I was typing.  I'll try the samples you kindly posted but heading out the door now.  

I have tried VLC, I get the same problem. 

Cheers

---

### Post by shantiq on 2012-05-21
ok yeti as you see it plays in Ubuntu here no prob
[ATTACH]218421[/ATTACH]


so i am thnking as you suggested maybe codec







[B]
===============[/B]

[B]

OK[/B]   **got it **    i then tried it in vlc    and movie player just what you described     **slurred and checking**   in aqualung it gives white noise



but it is happy from commandline  thus on 12.04


> mplayer    file.m4a  or   >  mplayer *    [for a bunch of them]

[ATTACH]218429[/ATTACH]



and     > ffplay  file.m4a   also works here




**or ** simply install [[SIZE=1]**DEADBEEF** [/SIZE]]("http://ubuntuforums.org/showpost.php?p=9423841&postcount=1")  and sorted...        for some reason it has the wherewithal to play those files   not like a pachyderm in treacle :KS


**ps   and yes 24/96 **is so worth it  :KS  beautiful clear rich sound on your track

---

### Post by TheYetiWakes on 2012-05-21
Hi Shantiq

Back from the pub full of hope but alas no joy here.  Tried DeadBeef first off as seemed the simplest option but again the same result for me, just plays at half the speed.

I then tried ffplay command and recieved:

> 
avplay version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2003-2011 the Libav developers
  built on Mar 22 2012 05:29:10 with gcc 4.6.3
Silversong.m4a: Invalid data found when processing input


finally trying your first option last I received:

> MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Silversong.m4a.
libavformat version 53.21.0 (external)
Mismatching header version 53.19.0


Something up with my Ubuntu install I presume?  Its a fresh install of only a couple of weeks ago.  I then added various restricted repositories and additional codecs as found in the sticky guides on this forum.

---

### Post by Nutria on 2012-05-22
> **flemur13013 said:**
> Here's some 24bit / 96Khz samples: 

[http://01688cb.netsolhost.com/samplerdownload/](http://01688cb.netsolhost.com/samplerdownload/)


Downloaded DvorakViolinCon.flac and gave it a shot.

aqualung plays it, but with jitters and static.  Maxes out a Athlon II X4 640 core.

VLC 2.0.1, OTOH, only uses 20% of a core, playing the music perfectly.

mocp uses only 3% CPU.

---

### Post by Nutria on 2012-05-22
> **TheYetiWakes said:**
> Hi Shantiq

Back from the pub full of hope but alas no joy here.  Tried DeadBeef first off as seemed the simplest option but again the same result for me, just plays at half the speed.

I then tried ffplay command and recieved:



finally trying your first option last I received:



Something up with my Ubuntu install I presume?  Its a fresh install of only a couple of weeks ago.  I then added various restricted repositories and additional codecs as found in the sticky guides on this forum.

In the avplay from stock 12.04 the song plays perfectly on my machine:
```
$ apt-cache policy libav-tools
libav-tools:
  Installed: 4:0.8.1-0ubuntu1
  Candidate: 4:0.8.1-0ubuntu1
  Version table:
 *** 4:0.8.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status

$ avplay "05 Messenger Birds.m4a"
avplay version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2003-2011 the Libav developers
  built on Mar 22 2012 05:09:06 with gcc 4.6.3
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '05 Messenger Birds.m4a':
  Metadata:
    major_brand     : M4A 
    minor_version   : 0
    compatible_brands: M4A mp42isom
    title           : Messenger Birds
    artist          : Mellow Candle
    album           : Swaddling Songs
    genre           : Folk
    track           : 5/12
    date            : 1972
  Duration: 00:03:39.60, start: 0.000000, bitrate: 2927 kb/s
    Stream #0.0(eng): Audio: alac, 96000 Hz, 2 channels, s32, 2832 kb/s
   7.84 A-V:  0.000 s:0.0 aq=  329KB vq=    0KB sq=    0B f=0/0   
```

No joy with VLC 2.0.1, but mplayer succeeds, even though it spits out lots of scary messages:
```
$ mplayer "05 Messenger Birds.m4a"
MPlayer SVN-r34707-4.6 (C) 2000-2012 MPlayer Team

Playing 05 Messenger Birds.m4a.
libavformat version 54.0.0 (internal)
libavformat file format detected.
[lavf] stream 0: audio (alac), -aid 0, -alang eng
Clip info:
 major_brand: M4A 
 minor_version: 0
 compatible_brands: M4A mp42isom
 title: Messenger Birds
 artist: Mellow Candle
 album: Swaddling Songs
 genre: Folk
 track: 5/12
 date: 1972
Load subtitles in ./
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 54.0.0 (internal)
AUDIO: 96000 Hz, 2 ch, s32le, 2833.0 kbit/46.11% (ratio: 354124->768000)
Selected audio codec: [ffalac] afm: ffmpeg (FFmpeg ALAC audio)
==========================================================================
AO: [pulse] 96000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.0 (00.0) of 219.6 (03:39.6) ??,?% 
Audio device got stuck!
A:   0.2 (00.1) of 219.6 (03:39.6)  3.4% 
Audio device got stuck!
A:   0.3 (00.3) of 219.6 (03:39.6)  3.6% 
Audio device got stuck!
A:   0.7 (00.6) of 219.6 (03:39.6)  3.0% 
Audio device got stuck!
A:   0.9 (00.8) of 219.6 (03:39.6)  2.8% 
<snip>
```

---

### Post by shantiq on 2012-05-22
wow Yeti  i am sorry it has not yet connected     what a bummer can't be far now

you are using 12.04 are you not?


hard to understand why it would be ok for some of us on some of the players and so far not on any for you   [ and we know it is not hardware since you can play it all on Windows]

of course you have    ffmpeg    and

```
sudo apt-get install ubuntu-restricted-extras
```    which has some of the bits and pieces sometimes required



another thing to check would be your libav     

this is what i have here [see if any of these are missing or different on your install]

[ATTACH]218459[/ATTACH]






short of a reinstall my last offer :] has to be the [**version of VLC**]("http://www.andrews-corner.org/vlc.html") from scratch that has all the latest codecs [from Andrew's page]


also  Fakeoutdoorsman  [**ffmpeg**]("http://ubuntuforums.org/showpost.php?p=4907079&postcount=1") with all the latest too

---

### Post by Nutria on 2012-05-22
> **shantiq said:**
> hard to understand why it would be ok for some of us on some of the players and so far not on any for you

Apps are different.  Library versions are different.  Even ones that use libFLAC.so.8 might not implement everything in the same manner.

He'll just have to suck it up and upgrade to 12.04.  (gnome-session-fallback does a good enough job for me of replicating the GNOME v2.32 experience if that's what he's justifiably concerned over.)

---

### Post by shantiq on 2012-05-22
> **Nutria said:**
> Apps are different.  Library versions are different.  Even ones that use libFLAC.so.8 might not implement everything in the same manner.

He'll just have to suck it up and upgrade to 12.04.  (gnome-session-fallback does a good enough job for me of replicating the GNOME v2.32 experience if that's what he's justifiably concerned over.)


hi Nutria   [great name as i live in Norfolk:]]

oh i thought Yeti was on 12.04
where do you see that he is not?   he says  > in Ubuntu (12.04) they play at about quarter speed,

i am not convinced that it would be the reason for it not to work tho
would look at the libav as indicated earlier/ffmpeg libraries etc...


anyway he cannot be far now  ::]]]

---

### Post by TheYetiWakes on 2012-05-22
> Apps are different. Library versions are different. Even ones that use libFLAC.so.8 might not implement everything in the same manner.

He'll just have to suck it up and upgrade to 12.04. (gnome-session-fallback does a good enough job for me of replicating the GNOME v2.32 experience if that's what he's justifiably concerned over.)

Just to confirm i'm on 12.04 LTS and not too concerned with Gnome fallback, i'm getting on with Unity better than I thought I would ;)

Shantiq - I'll try your suggestions later when I get back from work and thanks from a fellow Norfolk bumpkin for all the tips so far.

---

### Post by shantiq on 2012-05-22
> thanks from a fellow Norfolk bumpkin for all the tips so far:KS:KS:KS

hilarious.  what are the odds????    and then Nutria joined us here; which is the name of the famous Norfolk Coypu

Well best of luck...

---

### Post by flemur13013 on 2012-05-22
FWIW, MessengerBirds.m4a would only play properly for me with "ffplay" (too slow and/or clicking and/or crash with others) , although FLAC 24/96 files played fine with lots of software, as mentioned before.  I stay away from itunes-related formats as much as possible.

I understand the desire for oversampling, etc, but people can't actually hear any (positive) difference between 16bit/44.1KHz and higher-res formats: 16bit has greater dynamic range, and 44.1KHz sampling covers more frequencies, than humans can hear.  48KHz is sometimes used for compatibility with DVDs, etc, but it doesn't sound better.

E.g. this article is worth reading:  [http://people.xiph.org/~xiphmont/demo/neil-young.html](http://people.xiph.org/~xiphmont/demo/neil-young.html)
++
"Articles last month revealed that musician Neil           Young and Apple's Steve Jobs discussed offering           digital music downloads of 'uncompromised studio quality'.           Much of the press and user commentary was particularly           enthusiastic about the prospect of uncompressed 24 bit 192kHz           downloads.  24/192 featured prominently in my own           conversations with Mr. Young's group several months ago.

         Unfortunately, there is no point to distributing music in           24-bit/192kHz format. Its playback fidelity is slightly           inferior to 16/44.1 or 16/48, and it takes up 6 times the           space."
++

---

### Post by Nutria on 2012-05-22
> **shantiq said:**
> oh i thought Yeti was on 12.04

Sorry; got my threads confused.

---

### Post by TheYetiWakes on 2012-05-22
> **flemur13013 said:**
> 
I understand the desire for oversampling, etc, but people can't actually hear any (positive) difference between 16bit/44.1KHz and higher-res formats: 16bit has greater dynamic range, and 44.1KHz sampling covers more frequencies, than humans can hear.  48KHz is sometimes used for compatibility with DVDs, etc, but it doesn't sound better.


Well think that debate is for another thread as it could go around and around. I would say agreed on a PC playing sound files through mediocre speakers its not worth it but as I have them in this format would be handy to play them when the mood takes me at the computer rather than have to resample them all or re-find the vinyl to re-rip it.  

As for quality well played back on my decent system my vinyl rips in 24/96 from Pro-Ject Turntable -> Tube Box Pre-Amp SE II -> Tascam US-144 sound far better than standard CD issues of the same albums in 16/44.1?    

As I said at the start it may be overkill but a lot of these albums are very rare (lots of bootlegs too) and I no longer have them.  Hence trying to make digital preservations of the best possible quality.  Overkill now may come into own in the future. 


[QUOTE=shantiq]hilarious. what are the odds???? and then Nutria joined us here; which is the name of the famous Norfolk Coypu[/QUOTE]

Whatd'ya mean?  There's more places outside Norfolk??  My map just says Here Be Monsters!

I've already got the restricted repro's installed.  I shall have a further poke about to see what's what.

---

### Post by shantiq on 2012-05-22
yes there are articles knockin around telling you that 24/96 does not sound better and there are also people who need to remove the pound of wax they have in the ear canal



and maybe tinned food tastes the same as fresh   if one's tastebuds have been removed  :KS




but hey if you listen to your music on a cheese grater   it probably makes no difference :KS:KS   on a PC wired to an average stereo like mine it **makes a lot** of difference

not 192 versus 96 i agree but 24   versus 16 is unmissable

But each to their own..


   I cannot wait for Neil Young to actually release something in 24/192 or whatever; i simply wish he stayed away from the Mac people    ......


audiophiles of the world unite 


and again Yeti hope you find a way through on your system....

---

### Post by TheYetiWakes on 2012-05-22
Well no luck i'm afraid Shantiq.

I've had a look through the Libav files and seem pretty much in line with yours.

Funny you should mention Mr Young.  Some of the flac files I would like to play again are the rips extracted from the 24bit/192khz PCM stream from the Blu Ray version of his Archives boxset.  They sound phenomenal and almost makeup for the shocking amount of duplications from studio material he put on Archives.

---

### Post by Nutria on 2012-05-22
> **shantiq said:**
> yes there are articles knockin around telling you that 24/96 does not sound better and there are also people who need to remove the pound of wax they have in the ear canal

and maybe tinned food tastes the same as fresh   if one's tastebuds have been removed  :KS

but hey if you listen to your music on a cheese grater   it probably makes no difference :KS:KS   on a PC wired to an average stereo like mine it **makes a lot** of difference

not 192 versus 96 i agree but 24   versus 16 is unmissable

Bah.  Do you also use oxygen-free strained copper Monster cables?

Due to the human ear's 20KHz upper range, the Nyquist–Shannon sampling theorem and the physics of attenuation, **anything above 44KHz is wasted**.

(Even though there's a bit of waste, 48KHz is a good frequency because mathematically it works so well with all the common video frame rates.)

Similarly, 65536 (surely you know that's 16 bits) possible frequencies each only lasting 1/44056th of a second is more than the human ear can distinguish except in a well-designed and engineered concert hall.  Even then, 20 bits is the upper limit of human perception.

Lastly, IMNSHO, the very industrial and physical nature of pressing hot vinyl and the abrasion of needle against vinyl means that the analog signal is going to degrade over time.  It's that manifestly obvious reason why people dumped their LPs as quickly as they could.

---

### Post by Nutria on 2012-05-22
> **TheYetiWakes said:**
> I've had a look through the Libav files and seem pretty much in line with yours.

Have you tried mplayer (which plays 24/96 ALAC and FLAC) and mocp (which only plays the 24/96 FLAC).

---

### Post by shantiq on 2012-05-23
at this point one would   say reinstall

but what guarantee id there that it would then work

actually each time u install things get installed in a different order   so i do not know

almost voodoo:KS:KS


Nutria thanx for all the technical info there; and i have seen all this before one way or the other;   but my ears disagree  ..  and i leave it there as it is way off topic  well maybe not since we are talking 24/96  but does not advance Yeti's quest

Puzzling and again puzzling....       tell us when you crack it  .....no doubt will at some point

---

### Post by TheYetiWakes on 2012-05-23
I don't like usually reinstalling just because of an error or so but this and a couple of other hardware changes im doing may mean its on the cards.  

Would be nicer to work out why though for future reference.

Thanks for all the help anyways.

---

### Post by Yellow Pasque on 2012-05-23
It's always a good idea to use a LiveCD/USB to test that kind of thing out. If the errors still exist on LiveCD/USB, then reinstalling isn't the answer.

---

### Post by shantiq on 2012-05-23
you need someone who knows more about all the possible reasons;    surely there must be someone outthere who could crack it for you.....      whoever you may be....

reinstall as you say is a sledgehammer to crack a nut

---

### Post by Yellow Pasque on 2012-05-23
I'm using Debian sid with Debian multimedia repo. My audio setup uses no pulseaudio and no software mixing.
For me, the file plays correctly in Audacious (3.3.x, built from source), ffplay and mplayer

The file does not play correctly in gstreamer apps (rbox,totem, gst123) or vlc.

I'll do more testing later when it stops thundering here.

---

### Post by TheYetiWakes on 2012-05-23
Well due to a couple of other glitches and things I took the plunge and done a complete reinstall.  Still the same problem.  Then installed restricted set and VLC through the link Shantiq kindly posted and...  still not working.   

Guess I will have to look and doing something else with the files on the windows side before taking the Ubuntu leap full time.

Thanks for all the tips guys.  Really not sure what else can be tried?

---

### Post by Yellow Pasque on 2012-05-23
I'm baffled why VLC can't play it while other ffmpeg-based players can. :\
```
$ cvlc -v ~/Downloads/05\ Messenger\ Birds.m4a 
VLC media player 2.0.1 Twoflower (revision 2.0.1-0-gf432547)
[0x1148be8] dummy interface: using the dummy interface module...
[0x1008718] mp4 stream warning: unknown box type covr (incompletely loaded)
[0x1009998] avcodec decoder warning: Physical channel configuration not set : guessing
[0xf49df8] alsa audio output warning: device cannot be paused
[0xf49df8] main audio output warning: PTS is out of range (-9984), dropping buffer
[0xf49df8] main audio output warning: buffer too late  (91145), up-sampling
[0xf49df8] main audio output warning: buffer way too late (182916), dropping buffer
[0xf49df8] main audio output warning: timing screwed, stopping resampling
[0xf49df8] main audio output warning: buffer way too late (232041), dropping buffer
[0xf49df8] main audio output warning: buffer way too late (189374), dropping buffer
[0xf49df8] main audio output warning: buffer too late  (146708), up-sampling
[0xf49df8] main audio output warning: buffer way too late (238478), dropping buffer
```

---

### Post by Nutria on 2012-05-23
> **Temüjin said:**
> I'm baffled why VLC can't play it while other ffmpeg-based players can. :\

Don't be.  You'd think that every media player treats input files the same, but that's just not the case.

So, file a bug against vlc and post the bug # here.  I'll add a verification to the bug, to demonstrate that it's not just you.

---

### Post by ron999 on 2012-05-23
> **Temüjin said:**
> I'm baffled why VLC can't play it while other ffmpeg-based players can.
Hi
VLC won't play "05 Messenger Birds.m4a" for me...
but it will play OK with VLC when decompressed to **wav**
```
ffmpeg -i "05 Messenger Birds.m4a" -c:a pcm_s24le Messenger_Birds.wav
```
Then
```
cvlc Messenger_Birds.wav
```

Maybe VLC is happy with 24/96 wav files, but not if they are flac or alac.
Could be a bug in VLC.

---

### Post by Yellow Pasque on 2012-05-23
Well, gstreamer-ffmpeg exhibits the same behavior as VLC, so I think it goes deeper. I even tried gstreamer 1.0 from debian experimental

---

### Post by shantiq on 2012-05-24
see further on.................

---

### Post by TheYetiWakes on 2012-05-24
> i bet you it will [the problem therefore and it is not a problem if that is right would be something in the Windows encoding; something specific there that does not ALWAYS translate well to Linux]

Hi Shantiq

I shall try again later when I am near the computer with the actual files but I have already tried converting them and it didn't help.  Can't remember exact text but received error about intitializing codec for .m4as. I also played around with them in windows but none would subsequently play in Ubuntu.

---

### Post by shantiq on 2012-05-24
ok failed to see ffmpeg turned them into 16-bit so not an option that way

---

### Post by ron999 on 2012-05-24
> **shantiq said:**
> 
they now play on all the players here

Hi
Are you sure that these flac/alac files are still 24/96 after conversion?

---

### Post by shantiq on 2012-05-24
well spotted Ron    cannot believe i missed that      no they re 16-bit now defeating the exercise   hhhhmmmmmmmmmm   

the kbps was so high i did not think to check:KS


so no route through that way....



tried sox    which retains 24-bit but then   shhhhhhhhhhhhhh noise and no play



so still only   deadbeef   audacious    mplayer and ffplay     ....   on the original 24/96 m4a

---

### Post by andrew.46 on 2012-05-24
I am on my slackware partition at the moment but the latest git vlc plays the file *05 Messenger Birds.m4a* flawlessly here..... This copy is compiled against the git FFmpeg. Picked up some nice cover art too :).

---

### Post by ron999 on 2012-05-24
> **andrew.46 said:**
> I am on my slackware partition
Hmmm
With XUbuntu 12.04 and
VLC media player 2.1.0-git Rincewind (revision 1.3.0-git-2549-ga418fa2)
compiled against
ffmpeg version git-2012-05-16-e556121
"05 Messenger Birds.m4a" won't play for me.

---

### Post by andrew.46 on 2012-05-24
> **ron999 said:**
> Hmmm
With XUbuntu 12.04 and
VLC media player 2.1.0-git Rincewind (revision 1.3.0-git-2549-ga418fa2)
compiled against
ffmpeg version git-2012-05-16-e556121
"05 Messenger Birds.m4a" won't play for me.

Must be that dodgy guide you are following :). Recompile and try adding:

```
--disable-speex
```

to the ./configure string and you should be able to play the file. If this works for you I will adjust the vlc guide appropriately.

---

### Post by ron999 on 2012-05-24
@ andrew.46
The wav/flac/alac 24/96 files play OK with mPlayer/SMPlayer so I'm not going to recompile VLC just now.


@ TheYetiWakes
Show the output from this command:-
```
mplayer "05 Messenger Birds.m4a"
```

```
xubuntu:~$ mplayer "05 Messenger Birds.m4a"
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 05 Messenger Birds.m4a.
libavformat version 53.21.0 (external)
Mismatching header version 53.19.0
libavformat file format detected.
[lavf] stream 0: audio (alac), -aid 0, -alang eng
Clip info:
 major_brand: M4A 
 minor_version: 0
 compatible_brands: M4A mp42isom
 title: Messenger Birds
 artist: Mellow Candle
 album: Swaddling Songs
 genre: Folk
 track: 5/12
 date: 1972
Load subtitles in ./
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
AUDIO: 96000 Hz, 2 ch, s32le, 2833.0 kbit/46.11% (ratio: 354124->768000)
Selected audio codec: [ffalac] afm: ffmpeg (FFmpeg ALAC audio)
==========================================================================
AO: [pulse] 96000Hz 2ch s32le (4 bytes per sample)
Video: no video
Starting playback...
A:   1.8 (01.7) of 219.6 (03:39.6)  3.6% 


MPlayer interrupted by signal 2 in module: play_audio
A:   2.0 (01.9) of 219.6 (03:39.6)  3.7% 

Exiting... (Quit)
```

---

### Post by TheYetiWakes on 2012-05-24
> **ron999 said:**
> 
@ TheYetiWakes
Show the output from this command:-
```
mplayer "05 Messenger Birds.m4a"
```


As back in post #13.  Different track but from the same album.

---

### Post by shantiq on 2012-05-24
audacious and [**deadbeef**]("http://sourceforge.net/projects/deadbeef/files/debian/0.5.4/deadbeef_0.5.4-1_amd64.deb/download") only 2 gui that work on mine


i know they did not work for you in previous install    but on new one ??


both easy and quick to install if your patience is holding out:KS

---

### Post by andrew.46 on 2012-05-24
vlc guide altered, the file now plays successfully on Precise Pangolin, at least with the development version of vlc:

Howto: Build the development version of vlc under Ubuntu
[http://www.andrews-corner.org/vlc.html](http://www.andrews-corner.org/vlc.html)

I have not built the release version though, might be worth a try...

---

### Post by TheYetiWakes on 2012-05-24
> **andrew.46 said:**
> vlc guide altered, the file now plays successfully on Precise Pangolin, at least with the development version of vlc:

Howto: Build the development version of vlc under Ubuntu
[http://www.andrews-corner.org/vlc.html](http://www.andrews-corner.org/vlc.html)

I have not built the release version though, might be worth a try...

Hi Andrew

It was the development release, following those instructions, of VLC that I installed.  Doesn't play for me with it though?

---

### Post by andrew.46 on 2012-05-24
> **TheYetiWakes said:**
> It was the development release, following those instructions, of VLC that I installed.  Doesn't play for me with it though?

I have altered the guide by adding *--disable-speex* to the vlc ./configure string. This is a heavy handed way of avoiding building a speex resampler used when decoding your file, this filter seems to be broken at the moment and I am loathe to add to [this report]("http://trac.videolan.org/vlc/ticket/5781") as the vlc developers can be quite abrasive.....

Try the [recompile section]("http://www.andrews-corner.org/vlc.html#update") and hopefully your file will spring to life :).

---

### Post by TheYetiWakes on 2012-05-25
> **andrew.46 said:**
> I have altered the guide by adding *--disable-speex* to the vlc ./configure string. This is a heavy handed way of avoiding building a speex resampler used when decoding your file, this filter seems to be broken at the moment and I am loathe to add to [this report]("http://trac.videolan.org/vlc/ticket/5781") as the vlc developers can be quite abrasive.....

Try the [recompile section]("http://www.andrews-corner.org/vlc.html#update") and hopefully your file will spring to life :).

Ah I see, OK I will give it a go later.  I've actually had some success in finally getting the file to play though.

I've re-installed ffmpeg last night and for some reason now mplayer actually recognises and plays the file but this is the only player to do so of the ones I have tried (Banshee,VLC, Deadbeef, Rhythmbox).  

I can't see anything that I have done differently from the last time it was installed.  

On a slightly different note does anyone know if it is possible to convert files with ffmpeg to 24bit?  Wondering if its the iTunes .m4a causing some of the problems and was trying to turn into flac or wav to see if I get any different results.  I was using the following code as highlighted earlier in this thread but get an error saying it doesn't recognise what to do with the output "s24le":

```
ffmpeg -i "05 Messenger Birds.m4a" -c:a pcm_s24le Messenger_Birds.wav
```

---

### Post by shantiq on 2012-05-25
hi Yeti    well some success at last



no doubt Andrew's route will be the solution here



ffmpeg does not convert to 24-bit only 16 to my knowledge

that was the mistake i made yesterday and Ron pulled me up on it

Sox converts to 24-bit   but i tried it here and the resulting file went ssshhhhhhh   on all players



if you have   mplayer going now i suggest  this [**trick**]("http://ubuntuforums.org/showpost.php?p=11898266&postcount=7")    with      ```
mplayer */./*.flac *m4a
```   instead of nvlc

and it will give you a decent way to play your files    as well as vlc     return to move to next track   arrows for navigation

---

### Post by TheYetiWakes on 2012-05-25
Right finally a breakthough I think.

I recompiled VLC as instructed and it does then indeed play the file.  What is slightly better news is that since reinstalling ffmpeg and recompiling VLC all players I have previously tried now play the original .flac files that I made where before they wouldn't.  I cannot say exactly what altered it, I only carried out the above two actions.

Apart from mplayer and VLC they all baulk still at the .m4a itunes converted ones but I fear that may be something to do with some dodgy windows side conversion perhaps into a not fully supported codec?

Anyway, I can abandon those files as I have the original .flac ones anyway and i'm not sure its worth investigating further for that filetype which is not common in Ubuntu?

On another note I loaded up windows and created some 24/96 .wav files too and they play in all players in Ubuntu too.

Good news and thanks for all the time and effort everyone put in.  It is very much appreciated.  Just wish I could have pinned it down to exactly what's cured it.

---

