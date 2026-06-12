---
title: "bulk unpacking from lossless (wavpack;flac;ape)"
date: 2011-02-19
forum: Multimedia Software
---

### Post by shantiq on 2011-02-19
Cobbling info from different sources finding this script useful and maybe hopefully useful to some of you too

1.  cd to folder containing folders containing wv,flac,ape


bulk unpacking from lossless (wavpack;flac;ape)
==============================================


```
for i in */
do
  cd "$i"
  wvunpack *wv     [COLOR="Red"](replace this line  with  flac -d *.flac     for flac)       [/COLOR]
  cd ..
done

&&

for i in */
do
  cd "$i"
  mkdir "unpacked" && mv *.wav "unpacked"  
  cd ..
done
```

FOR APE
=======

```
for i in */
do
  cd "$i"
  for f in *.ape; do mac "$f"  "${f%.ape}.wav" -d ;  done
  cd ..
done

&&

for i in */
do
  cd "$i"
  mkdir "unpacked" && mv *.wav "unpacked"  
  cd ..
done
```

---

### Post by shantiq on 2011-02-19
forgot to add ape a really easy way to your system with a .deb


so [here goes]("http://ubuntuforums.org/attachment.php?attachmentid=162759&d=1278575963")

---

### Post by shantiq on 2011-02-20
line 4 in the script at the top can be changed to any of those  **To move from one format to another**




**[SIZE="2"]To mp3 320kbps[/SIZE]** (lossy) (here from flac but simply replace word flac by name of codec you start from)


Code:
```
for f in *.flac; do ffmpeg -i "$f" -ab 320k "${f%.flac}.mp3"; done

```

[COLOR="DarkRed"]if you want to delete the original file add
Code:
```
&& rm "$f"

```   before the ;[/COLOR]



wav to shorten

Code:
```
for f in *.wav; do shorten "$f" "${f%.wav}.shn"; done

```

so wav to shorten becomes

Code:
```
for f in *.wav; do shorten "$f" "${f%.wav}.shn" && rm "$f"  ; done

```


shorten to wav

Code:
```
for f in *.shn; do ffmpeg -i "$f" "${f%.shn}.wav"; done

```


wav to mp3HD

Code:
```
for f in *.wav; do mp3hdEncoder -br 320000   -if "$f" -of "${f%.wav}.mp3"; done

```
When using mp3hdEncoder or mp3hdEncoder.exe under wine make sure you have accepted the terms and conditions first IT WILL SIMPLY not work otherwiseFor mp3hdEncoder enter mp3hdEncoder in the command line and follow instructions for .exe right click and do same


mp3HD to wav

Code:
```
for f in *.mp3; do mp3hdDecoder   -if "$f" -of "${f%.mp3}.wav"; done
```


wav to alac apple lossless

Code:
```
for f in *.wav; do ffmpeg -i  "$f" -acodec alac "${f%.wav}.m4a"; done
```


alac to wav


Code:
```
for f in *.m4a; do ffmpeg -i "$f" "${f%.m4a}.wav"; done


alac to flac
```

Code:
```
for f in *.m4a; do ffmpeg -i "$f" "${f%.m4a}.flac"; done

```


flac to alac

Code:
```
for f in *.flac; do ffmpeg -i "$f" -acodec alac "${f%.flac}.m4a"; done
```

wav to mp4als

Code:
```
for f in *.wav; do mp4alsRM22rev2  "$f"  "${f%.wav}.mp4"; done
and to decompress 
```

Code:
   ```
for f in *.mp4; do mp4alsRM22rev2 -x -v "$f"  "${f%.mp4}.wav"; done

```

wav to bonk

Code:
```
for f in *.wav; do bonk encode -l "$f"  "${f%.wav}.bonk"; done

```

wav to ofr OptimFROG

Code:
```
for f in *.wav; do ofr --encode  "$f"  "${f%.wav}.ofr"; done

```

ape to flac

Code:
```
for f in *.ape; do ffmpeg -i "$f" "${f%.ape}.flac"; done

ape to alac
```

Code:
```
for f in *.ape; do ffmpeg -i "$f" -acodec alac "${f%.ape}.m4a"; done

```

shorten to alac

Code:
```
for f in *.shn; do ffmpeg -i "$f" -acodec alac "${f%.shorten}.m4a"; done
```



wavpack to flac

Code:
```
for f in *.wv; do ffmpeg -i "$f"  "${f%.wv}.flac"; done

```

---

