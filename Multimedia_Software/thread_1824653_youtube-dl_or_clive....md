---
title: "youtube-dl or clive..."
date: 2011-08-14
forum: Multimedia Software
---

### Post by o15977 on 2011-08-14
we all know youtube-dl and clive aren't working anymore..... but that's what i live on!!! anyone knows how to fix it? where are all the engineers? D:

---

### Post by andrew.46 on 2011-08-14
> **o15977 said:**
> we all know youtube-dl and clive aren't working anymore.....

The newest version of youtube-dl is working for me:

```

andrew@skamandros~$ **[COLOR="Red"]youtube-dl --version[/COLOR]**
2011.08.04

```

If your version is older try running:

```
youtube-dl --update
```

---

### Post by zadehas on 2011-08-14
Also clive version 2.2.26 is working for me.

Because these programs are not really 100% approved by video streaming sites like yahoo, you can always expect they break almost every time they change something, so you need to update.

---

### Post by kerry_s on 2011-08-14
Minitube download works to.

---

### Post by beew on 2011-08-14
Get the DownLoadHelper addon for Firefox.

---

### Post by dniMretsaM on 2011-08-14
You could always use a FF add-on or a Greasemonkey script. Also, how is this thread not closed yet?

---

### Post by Dr.Paneas on 2011-08-17
I&#8217;ve written some scripts that allow your to download music from Youtube.com in a simple and easy way. All you need is GNU/Linux distro and two dependencies installed:

[LIST]
[*]ffmpeg
[*]    youtube-dl
[/LIST]

Please select what method fits best to your needs:

1. I Know the Band and the Song: 
Script: [http://drpaneas.com/scripts/musicdown.sh](http://drpaneas.com/scripts/musicdown.sh)
```
#!/bin/bash
echo What is the artist of the song?
read ARTIST
echo What is the name of the song?
read NAME
echo "##################################"
echo "#### P L E A S E      W A I T  ###"
echo "##################################"
mkdir temp && cd temp
youtube-dl "ytsearch:$ARTIST $NAME album version"
ffmpeg -i *.flv -aq 2 "${ARTIST} - ${NAME}.mp3"
rm -rf *.flv
cd .. && mv temp/*.mp3 $PWD && rm -rf temp
echo Your song has been downloaded successfully
```

2. I have a txt file with all my favourite Youtube videos. Please download and make them mp3
Script: [http://drpaneas.com/scripts/musictext.sh](http://drpaneas.com/scripts/musictext.sh)
```

#!/bin/bash
echo "Type the filename:"
read FILENAME
mkdir temp && cp $FILENAME temp/ && cd temp
youtube-dl -i --max-quality=FMT -o "%(stitle)s" -a $FILENAME
rm $FILENAME && cd ..
for file in temp/*; do ffmpeg -i $file -aq 2 $PWD/$file.mp3 ; done
mv temp/*.mp3 $PWD && rm -rf temp
echo "Your videos are finally converted into mp3!"

```

3. I have a Youtube Playlist and I want all of them! ASAP!
[http://drpaneas.com/scripts/playst.sh](http://drpaneas.com/scripts/playst.sh)
```
#!/bin/bash
echo Enter the youtube PLAYLIST url to begin download
read PLAYLIST
mkdir temp && cd temp
youtube-dl -cit $PLAYLIST
for file in *; do ffmpeg -i $file -aq 2 $file.mp3 ; done
rm -rf *.flv *.mp4
cd .. && mv temp/*.mp3 $PWD && rm -rf temp
echo Done! Enjoy!

```

More information and proof working videos at my blog: [http://drpaneas.com/?p=143](http://drpaneas.com/?p=143)

---

