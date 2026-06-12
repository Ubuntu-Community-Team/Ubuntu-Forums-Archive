---
title: "WMA to MP3 Retaining Meta-data"
date: 2010-05-23
forum: Multimedia Software
---

### Post by jv2112 on 2010-05-23
I have about 50% of my music collection in wma format from my old Windoze days. I don't want to spend the time ( it is about 1800 songs) to re rip the tunes but I want uniform format. I tried using Sound Converter 1.4.4 but I lost all the meta-data.

Any Ideas on Conversion  ](*,)

---

### Post by mc4man on 2010-05-23
> but I lost all the meta-data.
I'm kinda surprised you got none written..

Most of the wma I have is lossless which requires  something altogether different to convert w/ tags using linux apps, but I have a couple of wma3(pro) samples.  

Both soundconverter and soundkonverter did write tags, just the basic ones though. (sc and sk   both  support wma2 and wma3 

Ex.
orig.
> doug@doug-desktop:~$ ffmpeg -i '/home/doug/Desktop/wmat/w3.wma' 

Input #0, asf, from '/home/doug/Desktop/wmat/w3.wma':
  Metadata:
    title           : Flyaway
    author          : Joan Osborne
    copyright       : 
    comment         : 
    WM/Lyrics       : 
    WM/MediaPrimaryClassID: {D1607DBC-E323-4BE2-86A1-48A42A28441E}
    WMFSDKVersion   : 11.0.6001.7001
    WMFSDKNeeded    : 0.0.0.0000
    IsVBR           : 0
    WM/Year         : 1996
    WM/EncodingTime : 1844674
    WM/Composer     : Joan Osborne
    WM/Publisher    : Mercury
    WM/Genre        : Rock
    WM/AlbumTitle   : Early Recordings
    WM/AlbumArtist  : Joan Osborne
    PeakValue       : 326
    AverageLevel    : 985
    WM/TrackNumber  : 1
    WM/UniqueFileIdentifier: AMGa_id=R   241160;AMGp_id=P   143261;AMGt_id=T  1489835
    WM/Provider     : AMG
    WM/ProviderRating: 2
    WM/ProviderStyle: Rock

soundconverter - missed the genre
> input #0, mp3, from '/home/doug/Desktop/wmat/w3.mp3':
  Metadata:
    TIT2            : Flyaway
    TPE1            : Joan Osborne
    TDRC            : 1996
    TALB            : Early Recordings
    TRCK            : 1


sounkonverter - missed or misread the track number 
> Input #0, mp3, from '/media/abedcdc2-ad76-44ec-88ea-0b5c10a2dce1/home/doug/soundKonverter/Desktop/wmat/w3.mp3':
  Metadata:
    TSSE            : LAME 32bits version 3.98 ([http://www.mp3dev.org/](http://www.mp3dev.org/))
    TPE1            : Joan Osborne
    TALB            : Early Recordings
    TCON            : Rock
    TIT2            : Flyaway
    TDRC            : 1996
    TLEN            : 232338
    TPOS            : 0
    TYER            : 1996

I'm not sure sk can be adjusted to write more tags - I'm pretty sure sc can't.

alternately if not other solution arises you could try running the 30 free trial of dbpoweramp in wine and see if it does better - should


Edit: do you have id3v2 installed?

---

### Post by jv2112 on 2010-05-24
I will have to run some more tests. If you got that result I may have done something wrong. 

What will id3v2 do for me ?

---

### Post by mc4man on 2010-05-24
> What will id3v2 do for me 

It's a cli Tag writer - I'm assuming sc and sk use it.. though could be wrong

(For the few mp3's I do for an ipod - lame uses it


Actually I see sc depends on libtag1 - so maybe not the issue - not sure what sk uses

---

### Post by jv2112 on 2010-05-26
Not sure but I think you are dead on. I installed and re ran the job on Sound Converter & it seems to be picking up on the tags.


Only 1600 more tunes to go.... painfully slow ](*,)


:twisted: ---> But I am determined ... Effort = Results.


Thanks Again :guitar:

---

