---
title: "Recursive conversion of all files in a directory"
date: 2011-10-16
forum: Multimedia Software
---

### Post by uzd4ce on 2011-10-16
I like to make audio-only versions of movies that I listen to at work.  I've been using ffmpeg to convert avis or mkvs individually, and that works fine, but I've got a bunch of files left and I'd like to see if I can convert all the files in one step.

The command I'm using to pull out the audio is 

```
ffmpeg -i input_file.avi -vn -ab 48k output_file.mp3
```

Say I have a directory of 50 avi files. How can I run that command on all of them in sequence?

I've looked around a bit and came up with this code, but I'm not sure if the syntax is exactly right.

```
for f in *.avi
ffmpeg -i "$f" -vn -ab 48k "$f.mp3" 
done
```

Any suggestions would be appreciated.

---

### Post by shantiq on 2011-10-16
hi uzd the word do was missing :)



```

for f in *.avi
do 
    ffmpeg -i "$f" -vn -ab 48k "${f%.avi}.mp3" 
done 

```


Also i think you can knock off -vn   it knows if the extension is mp3 there is no video to be converted


```

for f in *.avi
do 
    ffmpeg -i "$f" -ab 48k "${f%.avi}.mp3" 
done 

```



Can be used for all formats in FFMPEG

---

