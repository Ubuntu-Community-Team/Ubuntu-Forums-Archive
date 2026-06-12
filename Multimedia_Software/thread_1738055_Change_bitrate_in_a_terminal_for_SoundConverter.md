---
title: "Change bitrate in a terminal for SoundConverter"
date: 2011-04-24
forum: Multimedia Software
---

### Post by W29 on 2011-04-24
Hi

I've been testing with the SoundConverter software and I want to write a  script for it.
Most music files on my pc are *.flac. But I want to convert some albums to my mp3 player with a script. Everything works fine. I do this:
```
soundconverter -b -m audio/mpeg -s .mp3 *.flac
```But the quality is 128kbps.
Is there any way to change the bitrate (in the terminal ofcourse)?

And if this is not possible, is there an alternative that copies the tags correct like SoundConverter?

w29

---

### Post by ron999 on 2011-04-24
...

---

### Post by W29 on 2011-05-06
*bump*
Anyone?

---

### Post by W29 on 2011-06-25
*bump²*

---

### Post by cybrsaylr on 2011-06-25
Why do it in terminal?

I have no problems converting ogg or flac files into any mp3 bitrate needed from 192 up to 320 with sound converter by just opening it and using it as is.

---

### Post by W29 on 2011-07-10
> **cybrsaylr said:**
> Why do it in terminal?

I have no problems converting ogg or flac files into any mp3 bitrate needed from 192 up to 320 with sound converter by just opening it and using it as is.

Because I want to write a nautilus script for that purpose.

---

### Post by erind on 2011-07-10
> **W29 said:**
> ...
```
soundconverter -b -m audio/mpeg -s .mp3 *.flac
```But the quality is 128kbps.
Is there any way to change the bitrate (in the terminal ofcourse)?

And if this is not possible, is there an alternative that copies the tags correct like SoundConverter?

From the terminal, usually '*ffmpeg*' is the preferred tool for such conversions. It can take different bitrates (I used 192kb in this case), and its '*-map_meta_data outfile:infile*' option preserves id3 tags of the original song as well, and never had an issue so far. This is script that I use:

```
  for song in *.flac 
   do
    ## to preserve id3 tags, use ffmpeg option:    -map_meta_data outfile:infile
    ffmpeg -i "$song" -map_meta_data safe_"${song%.*}".mp3:"$song" -ac 2 -ab 192kb  safe_"${song%.*}".mp3
    mv safe_"${song%.*}".mp3 "${song%.*}".mp3
   done
```_Attention_: for some reason ffmpeg's  '-map_meta_data'  _fails_ if filename begins with numbers [1-9], resulting from the original filename, so  prepend a '*safe_*' temporary prefix at the start of the output filename, and then when 'ffmpeg' is done, rename it to its original name.

---

