---
title: "Encoding to alac [Apple lossless Audio Codec] with ffmpeg"
date: 2011-09-22
forum: Multimedia Software
---

### Post by shantiq on 2011-09-22
Just found out [**alac**]("http://en.wikipedia.org/wiki/Alac") is now available in ffmpeg for decoding which it was before but **also** for encoding


```
 D A    adpcm_sbpro_4   ADPCM Sound Blaster Pro 4-bit
 DEA    adpcm_swf       ADPCM Shockwave Flash
 D A    adpcm_thp       ADPCM Nintendo Gamecube THP
 D A    adpcm_xa        ADPCM CDROM XA
 DEA    adpcm_yamaha    ADPCM Yamaha
[COLOR="DarkRed"][B] DEA    alac            ALAC (Apple Lossless Audio Codec)
[/B][/COLOR] D A    als             MPEG-4 Audio Lossless Coding (ALS)
 D A    amrnb           Adaptive Multi-Rate NarrowBand
 D V D  amv             AMV Video
 D V D  anm             Deluxe Paint Animation
 D A    ape             Monkey's Audio
 DEV D  asv1            ASUS V1

```

If you want to convert one file use

```
ffmpeg -i filename.wav   -acodec alac filename.m4a
```

[replace wav with name of your starting codec]


or for **batch convert**  ( cd to a FOLDER of lossless or uncompressed music files )

```
for f in *; do ffmpeg -i "$f" -acodec alac "${f%.*}.m4a"; done

```
or  codec specific  (replace wav with name of your starting codec)

```
for f in wav; do ffmpeg -i "$f" -acodec alac "${f%.wav}.m4a"; done
```

---

