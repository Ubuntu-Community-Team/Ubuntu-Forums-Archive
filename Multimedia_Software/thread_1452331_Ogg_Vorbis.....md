---
title: "Ogg Vorbis...."
date: 2010-04-11
forum: Multimedia Software
---

### Post by oxf on 2010-04-11
I'm not really experienced at using Vorbis, up till now have ripped to MP3. However, I recently installed Rubyripper and today set about doing some comparison rips.

The Vorbis website informs me that It's not really valid to evaluate Vorbis with the variable bit rate concept and that instead the concept of "Quality" is used.[COLOR=Blue] [COLOR=Black]It goes on to say that the default Quality is "3", Q "5" is "very near CD quality" and Q "6" is "[/COLOR][/COLOR]lossless stereo coupling"

[COLOR=Blue][COLOR=Black]So... I ripped at quality 5 and 6. For Q6 if I look at the file properties it tells me that I have a bit rate of 192. Can that really be? I mean is that "really" only 192 or just how it interprets the .ogg file. 

And.. given you can take it up to Q "10" what would that achieve other than create a much larger file size? [/COLOR][/COLOR]

---

### Post by oxf on 2010-04-12
bmp

---

### Post by Chronon on 2010-04-12
I believe it just means that it cuts out less and less information, giving a higher fidelity compressed file.  Vorbis is a lossy codec, so fidelity depends on the quality or bitrate (unlike with lossless codecs).

---

### Post by cascade9 on 2010-04-12
> **oxf said:**
> I'm not really experienced at using Vorbis, up till now have ripped to MP3. However, I recently installed Rubyripper and today set about doing some comparison rips.

The Vorbis website informs me that It's not really valid to evaluate Vorbis with the variable bit rate concept and that instead the concept of "Quality" is used.[COLOR=Blue] [COLOR=Black]It goes on to say that the default Quality is "3", Q "5" is "very near CD quality" and Q "6" is "[/COLOR][/COLOR]lossless stereo coupling"

[COLOR=Blue][COLOR=Black]So... I ripped at quality 5 and 6. For Q6 if I look at the file properties it tells me that I have a bit rate of 192. Can that really be? I mean is that "really" only 192 or just how it interprets the .ogg file. 

And.. given you can take it up to Q "10" what would that achieve other than create a much larger file size? [/COLOR][/COLOR]

Q5 is 'very near CD quality'? Yeah, right. For people who believe that 192K CBR MP3s are 'CD quality' maybe. 

Yes, Q6 really is 192k (well, sort of, from what I recall vorbis is made to be a VBR codec, even though it can be done as CBR). 

As you increase the bitrate, less data is discarded, so a higher Qx file is better quality. A Q10 file would have more of the original information than a Q9 file, and so on. Really, anyone who uses Q10 has some strange reason for doing it, or hasnt heard of lossless- Q10 is 500k. I've got lossless files that are smaller than that. 

Persoanlly, if I rip to ogg vorbis I use Q8 (256k) or Q9 (320k) myself.

---

### Post by oxf on 2010-04-17
> **cascade9 said:**
> Q5 is 'very near CD quality'? Yeah, right. For people who believe that 192K CBR MP3s are 'CD quality' maybe. 

Yes, Q6 really is 192k (well, sort of, from what I recall vorbis is made to be a VBR codec, even though it can be done as CBR). 

As you increase the bitrate, less data is discarded, so a higher Qx file is better quality. A Q10 file would have more of the original information than a Q9 file, and so on. Really, anyone who uses Q10 has some strange reason for doing it, or hasnt heard of lossless- Q10 is 500k. I've got lossless files that are smaller than that. 

Persoanlly, if I rip to ogg vorbis I use Q8 (256k) or Q9 (320k) myself.

I was just quoting what was written on the Vorbis web site.

Before I've ripped to MP3 using VBR quality "0" the highest. If I look at properties of the ripped file it usually gives a bitrate anywhere from say 180K to 250K bit since it's VBR not CBR I assumed this is some sort of average that going to vary anyhow.

When I started reading about Vorbis I discovered it claimed to "be better" than MP3, giving a higher quality for the same file size or smaller file size for same quality. Since I'm new to Vorbis I cant say how true that is? 

I also read from the Vorbis site that bitrate is not the best way of comparing a Vorbis audio file but rather the concept of "quality" is more accurate. Thats what it said anyway. So when I looked at the properties of the Vorbis Q6 rip and saw the bitrate of 192K I had to wonder what that actually meant? I'm still confused about that!

The bottom line is I was satisfied with my Q0 MP3 rips but if I can better that either in quality or file size that would be great.

---

### Post by cascade9 on 2010-04-18
> **oxf said:**
> I was just quoting what was written on the Vorbis web site.

Before I've ripped to MP3 using VBR quality "0" the highest. If I look at properties of the ripped file it usually gives a bitrate anywhere from say 180K to 250K bit since it's VBR not CBR I assumed this is some sort of average that going to vary anyhow.

Vorbis is pretty much always VBR (unless you force it to use CBR). 

MP3 V0 should be about 245k/sec max IIRC, but the bitrate will drop at some points (which is why its VBR, the bitrate varies but in theory teh quality satys the same). What bitrate is displayed depends on what you are checking the file with, and how much the codec can drop the bitrate in response to quite/simple parts of the track. 

> **oxf said:**
> 
When I started reading about Vorbis I discovered it claimed to "be better" than MP3, giving a higher quality for the same file size or smaller file size for same quality. Since I'm new to Vorbis I cant say how true that is? 

Vorbis normally does better than MP3 in listening tests, but that isnt really 'hard' data. Its pretty difficult to get ahrd data on what lossy codec is the 'best'. 

> **oxf said:**
> 
I also read from the Vorbis site that bitrate is not the best way of comparing a Vorbis audio file but rather the concept of "quality" is more accurate. Thats what it said anyway. So when I looked at the properties of the Vorbis Q6 rip and saw the bitrate of 192K I had to wonder what that actually meant? I'm still confused about that!

The bottom line is I was satisfied with my Q0 MP3 rips but if I can better that either in quality or file size that would be great.

Basicly, if it says '192k' its probably refereing to the 'quality' setting. 

Q8 (256k) should be better than a V0 MP3, but slightly bigger files. If you really want quality then lossless is the onyl way to go.

---

### Post by oxf on 2010-04-18
> **cascade9 said:**
> Vorbis is pretty much always VBR (unless you force it to use CBR). 

MP3 V0 should be about 245k/sec max IIRC, but the bitrate will drop at some points (which is why its VBR, the bitrate varies but in theory teh quality satys the same). What bitrate is displayed depends on what you are checking the file with, and how much the codec can drop the bitrate in response to quite/simple parts of the track. 



Vorbis normally does better than MP3 in listening tests, but that isnt really 'hard' data. Its pretty difficult to get ahrd data on what lossy codec is the 'best'. 



Basicly, if it says '192k' its probably refereing to the 'quality' setting. 

Q8 (256k) should be better than a V0 MP3, but slightly bigger files. If you really want quality then lossless is the onyl way to go.

Thanks...
Well I'm satisfied with a V0 MP3 anyway. I looking to maybe increase quality a bit if theres not too much of a downside such as larger file size, or keep the same quality and save a bit of file space. Looks like I need to try Q7 or Q8.

---

