---
title: "Meizu M6 video encoding"
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by -::Bas::- on 2008-03-19
Hi i made a little script that I would like to share with you.
It's to encode your .avi (xvid) files to files a Meizu M6 can play.
Btw, this will substitute the spaces in your filmnames for underscores. (If anyone wants to make the code more efficient so it can handle spaces in the filenames, be my guest.)
The only thing you have to do is to move to the folder where your video files are, and run the script. The script makes a new folder and drops the encoded files in there.

Here's what you should do: 

First install mencoder

```
sudo apt-get install mencoder
```

Now open gedit and paste this into it, use this when your film(s) have an aspectratio of 4:3 (or are widescreen with black lines under and above the video):

```
#!/bin/bash

for i in *\ *
do
mv "$i" $(echo "$i" | tr ' ' '_')
done
mkdir enc
for film in *.avi ; do
    echo Processing $film
    mencoder $film -oac mp3lame -lameopts cbr:mode=2:br=128 -af resample=44100 -srate 44100 -ofps 18 -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:cbp:trell:vbitrate=384 -vf    scale=320:240 -ffourcc XVID -o enc/$film
done
```

Save the file in your home directory and call it 'encode'

When you want to encode something, just move to the folder containing the video files and type
```

~/encode
```

Use this when the film(s) you want to encode are widescreen (aspectratio of 16:9, and no black lines under and above the video):

```
#!/bin/bash

for i in *\ *
do
mv "$i" $(echo "$i" | tr ' ' '_')
done
mkdir enc
for film in *.avi ; do
    echo Processing $film
    mencoder $film -oac mp3lame -lameopts cbr:mode=2:br=128 -af resample=44100 -srate 44100 -ofps 18 -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:cbp:trell:vbitrate=384 -vf scale=320:176 -vf-add expand=:240 -ffourcc XVID -o enc/$film
done
```

Your terminal will be busy for a while, but after that in the video folder you will find a folder called 'enc', where you find your newly encoded videofiles in, ready to be played on your Meizu M6.

Enjoy!

---

