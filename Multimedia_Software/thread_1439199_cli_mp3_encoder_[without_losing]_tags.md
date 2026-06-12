---
title: "cli mp3 encoder [without losing] tags?"
date: 2010-03-25
forum: Multimedia Software
---

### Post by LintonHanes on 2010-03-25
Hi
I'm downsampling some mp3s for my portable player and soundconverter has not been doing as it's told (96kbps,44100sample) so I checked out lame >this is the command that I've just used, which is great, but lame strips all the id3 tags from the mp3, which I hate

for f in *.mp3;do lame "$f" /output/folder/"$f" -b 96 --scale-r 1.5 --resample 44.1
(--scale-r is raising the volume)

Is there a command (like a different tool) I can use to get these results "with the" tags kept?

---

### Post by LintonHanes on 2010-03-26
I couldn't stop looking, and found that ffmpeg does a great job, in fact it does a 'better' job with the volume adjustment than lame does imho, I've got this command now which works a charm. (-vol 256 is the 'current' volume (it's in bytes) and 512 is double volume, you multiply by 8 for these right)

for f in *.mp3;do ffmpeg -i "$f" -f mp3 -acodec libmp3lame -ab 96k -ar 44100 -vol 512 done/"$f" -map_meta_data outputfile.mp3:inputfile.mp3;done


[edit] 512 is far too much! I'll scale it to 384 or so 'right now'

---

### Post by andrew.46 on 2010-03-26
Hi Linton,

> **LintonHanes said:**
> 

```
for f in *.mp3;do ffmpeg -i "$f" -f mp3 -acodec libmp3lame -ab 96k -ar 44100 -vol 512 done/"$f" -map_meta_data outputfile.mp3:inputfile.mp3;done
```



a very slight variation:

```

for f in *.mp3 
    do 
    ffmpeg -i "$f" -acodec libmp3lame -ab 96k -ar 44100 -vol 384 \
    -map_meta_data 0:0 "${f%.mp3}_adjusted.mp3"
done

```

Not really much different...

Andrew

---

