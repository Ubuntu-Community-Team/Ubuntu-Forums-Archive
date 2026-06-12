---
title: "Bitrate question in Rhythmbox/Banshee"
date: 2009-03-13
forum: Multimedia Software
---

### Post by casmok on 2009-03-13
Is there a way of adjusting the bitrate when you rip CD's in either Rhythmbox or Banshee. I seem to only end up with 128. When I've used Windows Media Player in the past I chose the highest, i.e. CD quality, and got 320 bps. I've tried MP3 here and some others too and only manage to get 128 bps. I really dont want to go back to WMP

Thanks
Mike

---

### Post by logos34 on 2009-03-14
Applications>Sound&Video>Audio CD Extractor (a.k.a Sound-Juicer)

Edit>Prefs>Output Format>MP3>Edit Profiles>CD Quality (mp3)>Edit

Here's mine:

> audio/x-raw-int,rate=44100,channels=2  !  **[COLOR="Blue"]lame name=enc mode=1 vbr=4 vbr-quality=2 ![/COLOR]** id3v2mux

explanation:

  > **mode**                : Encoding mode
                        flags: readable, writable
                        Enum "GstLameMode" Default: 0, "stereo" Current: 1, "joint"
                           (0): stereo           - Stereo
                           (1): joint            - Joint Stereo
                           (2): dual             - Dual Channel
                           (3): mono             - Mono
                           (4): auto             - Auto
> 
 ** vbr**                 : Specify bitrate mode
                        flags: readable, writable
                        Enum "GstLameVbrmode" Default: 0, "none" Current: 0, "none"
                           (0): none             - No VBR (Constant Bitrate)
                           (2): old              - Lame's old VBR algorithm
                           (3): abr              - VBR Average Bitrate
                           (4): new              - Lame's new VBR algorithm

>  **vbr-quality**         : VBR Quality
                        flags: readable, writable
                        Enum "GstLameQuality" Default: 5, "5" Current: 5, "5"
                           (0): 0                - 0 - Best
                           (1): 1                - 1
                           (2): 2                - 2
                           (3): 3                - 3
                           (4): 4                - 4
                           (5): 5                - 5 - Default
                           (6): 6                - 6
                           (7): 7                - 7
                           (8): 8                - 8
                           (9): 9                - 9 - Worst


See, default is "5" -- which is why you're getting only ~128kbps.

VBR is far and away the best (EDIT: and results in much smaller, excellent sounding files), but if for some reason you want CBR 320, then use "vbr=0 bitrate=320"


For more options, see: 
[B][COLOR="Red"]
gst-inspect lame[/COLOR][/B]

good luck

---

### Post by casmok on 2009-03-14
> **logos34 said:**
> Applications>Sound&Video>Audio CD Extractor (a.k.a See, default is "5" -- which is why you're getting only ~128kbps.

VBR is far and away the best (and results in much smaller, better sounding files), but if for some reason you want CBR 320, then use "vbr=0 bitrate=320"


For more options, see: 
[B][COLOR="Red"]
gst-inspect lame[/COLOR][/B]

good luck

OK thanks for that! 

So you are saying that VBR is actually BETTER quality than 320? I chose 320 because when I ripped music to my MP3 player I previously had done it with Windows Media Player.There was the option for quality and I chose the highest because I wanted CD quality. then when I looked at the files they were list as 320 bitrate. I did notice that the drive was filling up a bit faster than I expected so maybe I've been going about this all wrong. For me the CD quality is important but if I can get that with VBR and smaller files that would be great. Are there any drawbacks to using VBR?

Mike

---

### Post by logos34 on 2009-03-14
> **casmok said:**
> OK thanks for that! 

So you are saying that VBR is actually BETTER quality than 320? I chose 320 because when I ripped music to my MP3 player I previously had done it with Windows Media Player.There was the option for quality and I chose the highest because I wanted CD quality. then when I looked at the files they were list as 320 bitrate. I did notice that the drive was filling up a bit faster than I expected so maybe I've been going about this all wrong. For me the CD quality is important but if I can get that with VBR and smaller files that would be great. Are there any drawbacks to using VBR?

well, strictly in terms of quality, not *better*, but the highest VBR setting (-V 0, or ~256k nominal rate) comes awfully close to 320 Constant bitrate...if you look at lame histogram as it's compressing you'll notice it peaks at 320, concentrating the most bits on the most complex/dense musical passages...And when you consider a) the much smaller size of the resulting file and b) the fact that you can't tell the difference anyway, well then it's a no-brainer to go with vbr.  Check out the lame page over at Hydrogenaudio.  

320 cbr is really a tremendous waste for no perceptible quality difference.    It's just a standard (used for album downloads, etc.).  For only a little more space you might as well go for lossless.  Personally I'd be perfectly happy with vbr-new -V 0 or -V 1, knowing that I can't tell it from the original.

---

### Post by casmok on 2009-03-16
> **logos34 said:**
> well, strictly in terms of quality, not *better*, but the highest VBR setting (-V 0, or ~256k nominal rate) comes awfully close to 320 Constant bitrate...if you look at lame histogram as it's compressing you'll notice it peaks at 320, concentrating the most bits on the most complex/dense musical passages...And when you consider a) the much smaller size of the resulting file and b) the fact that you can't tell the difference anyway, well then it's a no-brainer to go with vbr.  Check out the lame page over at Hydrogenaudio.  

320 cbr is really a tremendous waste for no perceptible quality difference.    It's just a standard (used for album downloads, etc.).  For only a little more space you might as well go for lossless.  Personally I'd be perfectly happy with vbr-new -V 0 or -V 1, knowing that I can't tell it from the original.

Thanks! Your two explanations cleared up a lot of things for me. I'm slowly figuring out what I'm doing here and enjoying learning too :D

---

### Post by casmok on 2009-03-23
OK I have one further question. I edit the Audio CD extractor profile. Heres mine now:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=0 ! id3v2mux

I then ripped a CD. yes the file size is much smaller but I'm confused about the bitrate I getting. Its set to VBR but if I look at the tracks in File Browser and right click Properties>Audio it shows a bitrate of 32 (well mostly but sometimes the same track shows a different bitrate like 92)

And then the bitrate displayed in the player is different like 160 kbps
What am I gettting, Am I really ripping using VBR?

---

### Post by logos34 on 2009-03-23
> **casmok said:**
>  I'm confused about the bitrate I getting. Its set to VBR but if I look at the tracks in File Browser and right click Properties>Audio it shows a bitrate of 32 (well mostly but sometimes the same track shows a different bitrate like 92)

And then the bitrate displayed in the player is different like 160 kbps
What am I gettting, Am I really ripping using VBR?

You can verify with [MediaInfo]("http://mediainfo.sourceforge.net/en") ([CLI ]("http://mediainfo.sourceforge.net/en/Download")version--mediainfo_0.7.12-1_i386.Debian_5.deb).  It's what I use--tells me all I need to know about mp3 files.

ex:
> 
user@ubuntu:~/music2/U2/No Line On The Horizon$ **mediainfo** [COLOR="Blue"]08\ -\ FEZ-Being\ Born.mp3 [/COLOR]
General #0
Complete name                : 08 - FEZ-Being Born.mp3
Format                       : MPA1L3
File size                    : 8.02 MiB
PlayTime                     : 5mn 17s
Bit rate                     : 212 Kbps
Album                        : No Line On The Horizon
Track name                   : FEZ-Being Born
Track name/Position          : 08
Track name/Position_Total    : 11
Performer                    : U2
Recorded date                : 2009
Writing library              : LAME3.97 

Audio #0
Codec                        : MPEG-1 Audio layer 3
Codec profile                : Joint stereo
[COLOR="Red"]Bit rate mode                : VBR
Bit rate                     : 212 Kbps
Minimum bit rate             : 32 Kbps[/COLOR]
Channel(s)                   : 2 channels
Sampling rate                : 44.1 KHz
Resolution                   : 16 bits
Writing library              : LAME3.97 
Encoding settings            : [COLOR="Red"]VBR[/COLOR] (mtrh)

Could be that the conflicting bitrate info your getting in different places is due to a mixup between the minimum threshold bitrates vs. actual average bitrate (different for each track) vs. the nominal VBR rate/quality setting (128, 160, 192, 224, etc)

hope that helps

---

### Post by rotwang888 on 2009-03-24
> **logos34 said:**
> You can verify with [MediaInfo]("http://mediainfo.sourceforge.net/en") ([CLI ]("http://mediainfo.sourceforge.net/en/Download")version--mediainfo_0.7.12-1_i386.Debian_5.deb).

 Thanks!  I didn't know about mediainfo.  Now I can stop using Mr.Questionman with wine. :p

---

### Post by casmok on 2009-03-25
Logos34:
Thanks for that!

---

