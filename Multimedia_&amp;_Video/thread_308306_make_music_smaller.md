---
title: "make music smaller"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by Fittersman on 2006-11-27
how can i do one of the following:

convert my songs to 128kbps
or
convert my songs to wma
or
or something that makes my songs smaller but they MUST be in either mp3 or wma format

i have a truly pic 'n roll mp310 plus

---

### Post by mssever on 2006-11-27
You can use lame to do this, I believe. I don't know if it's installed by default or if you'll have to install it from one of the repos (universe?).

Read "man lame" for specifics, but to downsample MP3s to 128kbps, do something like ```
lame --mp3input -b 128 input.mp3 output.mp3
```

---

### Post by Fittersman on 2006-11-27
i have a whole folder, lets say i want to do the whole thing in one shot, can this be done?

---

### Post by mssever on 2006-11-27
You could try a loop: ```
mkdir new
for i in *.mp3; do lame --mp3input -b 128 "$i" "new/$i"; done
```The newly encoded files will be in the "new" directory.

---

### Post by Kingfield on 2006-11-28
haha this is what i need as well.

---

### Post by Fittersman on 2006-11-28
is there a way to check first if its already 128kbps? because i know some of mine are already in 128

---

### Post by Zaen on 2006-11-28
I'm not positive, but I think if you were to play the songs through xmms it tells you the bitrate of the songs. good luck.

---

### Post by Kingfield on 2006-11-29
still need prog...](*,)

---

### Post by mssever on 2006-11-29
> **Fittersman said:**
> is there a way to check first if its already 128kbps? because i know some of mine are already in 128
Here's one to do this. Note, however, that it involves decoding every file, so it will be slow (although faster than doing it manually). There's probably a better way to accomplish this... (BTW: I also modified the for loop to work on files ending in .MP3 as well.)
```

mkdir new
for i in *.mp3 *.MP3 ; do 
    if [ $(mpg321 --test --verbose "$i" 2>&1 | grep 'Bitrate'| awk '{print $2}') -ne 128 ]; then
        lame --mp3input -b 128 "$i" "new/$i"
    fi
done
```> **Kingfield said:**
> still need prog...](*,) ?? What kind of program?

---

### Post by Dekunuts on 2006-11-29
why don't you just install soundconverter through synaptec. It has a graphical interface and is super easy to use. It allows batch convert into mp3/wma.

---

### Post by Kingfield on 2006-11-30
> **Dekunuts said:**
> why don't you just install soundconverter through synaptec. It has a graphical interface and is super easy to use. It allows batch convert into mp3/wma.
does it allow bitrate changing for mp3tomp3? ill try it out now.

---

### Post by Fittersman on 2006-11-30
soundconverter isnt working for me for some reason.

---

### Post by Dekunuts on 2006-12-01
soundconverter works great on my install and i didn't do anything special. Do make sure that you installed all the gstreamer plugins so MP3 support is there.

I do not know what the tomp3 means, so maybe you actually know more than I do, which would mean i can't help you. Who knows

---

### Post by Fittersman on 2006-12-02
it seems to stop at 16% everytime, just after it creates the .wav file of the song...

---

### Post by pietro_spina on 2006-12-10
> **mssever said:**
> Here's one to do this. Note, however, that it involves decoding every file, so it will be slow (although faster than doing it manually). There's probably a better way to accomplish this... (BTW: I also modified the for loop to work on files ending in .MP3 as well.)
```

mkdir new
for i in *.mp3 *.MP3 ; do 
    if [ $(mpg321 --test --verbose "$i" 2>&1 | grep 'Bitrate'| awk '{print $2}') -ne 128 ]; then
        lame --mp3input -b 128 "$i" "new/$i"
    fi
done
```

Thanks for the lesson in loops. However ID3v2 tags are lost with this technique...is there some way to preserve them?

-pietro

---

### Post by Fittersman on 2006-12-10
install "Audio Tag Tool" in add or remove programs and use it to rename all your files with all the information in your id3 tags or whatever they are called then when they are done converting use it to create the tags again. play around with it and you will figure it out.

---

### Post by pietro_spina on 2006-12-10
> **Fittersman said:**
> install "Audio Tag Tool" in add or remove programs and use it to rename all your files with all the information in your id3 tags or whatever they are called then when they are done converting use it to create the tags again. play around with it and you will figure it out.

that's not very automagical now, is it?   <shrug>

---

### Post by Fittersman on 2006-12-10
if by automagical you mean it does the whole folder with one click then yes it is automagical

---

