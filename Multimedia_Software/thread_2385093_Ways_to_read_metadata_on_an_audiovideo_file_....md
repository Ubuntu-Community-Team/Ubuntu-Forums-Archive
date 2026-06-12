---
title: "Ways to read metadata on an audio/video file ..."
date: 2018-02-16
forum: Multimedia Software
---

### Post by shantiq on 2018-02-16
I have always used mediainfo which can also be used in any language from the command line but there are others.
My question here is do you any more than the ones mentioned below which do a thorough job?

&#10122; * mediainfo*
```
mediainfo yourfile
```

and if you go and get the .cvs files you can then do any language:

```
mediainfo --Language="file:///home/yourname/MediainfoLanguages/ru.csv"
```


you need to go and fish the language you want [here]("https://github.com/MediaArea/MediaInfo/tree/master/Source/Resource/Plugin/Language")  manually in my experience click on de.dsv then copy save in a txt document in a folder of your making [37 languages so far]

so on a computer with no hungarian i can still do

```
mediainfo --Language="file:///home/shan/MediainfoLanguages/hu.csv" "myfile.mp4"
Általános
Teljes név                               : myfile.mp4
Formátum                                 : MPEG-4
Formátum profil                          : Base Media
Kódek azonosító                          : isom (isom/iso2/avc1/mp41)
Fájlméret                                : 2,22 GiB
Id&#337;tartam                                : 59 perc
Teljes adatsebesség                      : változó
Teljes adatsebesség                      : 5 366 kb/s
Kódolás dátuma                           : UTC 1904-01-01 00:00:00
Jelölés dátuma                           : UTC 1904-01-01 00:00:00
Kódoló szoftver                          : Lavf57.56.101

Kép
Sáv száma                                : 1
Formátum                                 : AVC
Formátum/adatok                          : Advanced Video Codec
Formátum profil                          : High@L3.2
Formátum beállítások, CABAC              : igen
Formátum beállítások, RefFrames          : 4 képkocka
Kódek azonosító                          : avc1
Kódek azonosító/adatok                   : Advanced Video Coding
Id&#337;tartam                                : 59 perc
Adatsebesség                             : 5 041 kb/s
Szélesség                                : 1 280 képpont
Magasság                                 : 720 képpont
Képarány                                 : 16:9
Képkockasebességi mód                    : állandó
Képkockasebesség                         : 50,000 FPS
Szabvány                                 : Component
ColorSpace                               : YUV
ChromaSubsampling                        : 4:2:0
BitDepth/String                          : 8 bit
Sorváltás típusa                         : folytonos
Bit/(képpont*képkocka)                   : 0.109
Adatfolyam mérete                        : 2,09 GiB (94%)
Kódolás dátuma                           : UTC 1904-01-01 00:00:00
Jelölés dátuma                           : UTC 1904-01-01 00:00:00
colour_range                             : Limited
colour_primaries                         : BT.709
transfer_characteristics                 : BT.709
matrix_coefficients                      : BT.709

Hang
Sáv száma                                : 2
Formátum                                 : AAC
Formátum/adatok                          : Advanced Audio Codec
Formátum profil                          : LC
Kódek azonosító                          : 40
Id&#337;tartam                                : 59 perc
Adatsebesség mód                         : változó
Adatsebesség                             : 320 kb/s
Csatornák száma                          : 2 csatorna
Csatorna kiosztás                        : Front: L R
Mintavételezési gyakoriság               : 48,0 kHz
Képkockasebesség                         : 46,875 FPS (1024 spf)
Adatfolyam mérete                        : 135 MiB (6%)
Nyelv                                    : angol
Default                                  : igen
AlternateGroup/String                    : 1
Kódolás dátuma                           : UTC 1904-01-01 00:00:00
Jelölés dátuma                           : UTC 1904-01-01 00:00:00


```

&#10123; *mplayer has got a handy tool too*

```
mplayer -vo null -ao null -frames 0 -identify yourfile
```


&#10124; *exiftool also good*

```
sudo apt-get install libimage-exiftool-perl
```

then

```
exiftool yourfile
```


&#10125; *avprobe* *or ffprobe*

```
avprobe yourfile
```



if you know of any of similar or higher grade please indicate. Thanx

---

