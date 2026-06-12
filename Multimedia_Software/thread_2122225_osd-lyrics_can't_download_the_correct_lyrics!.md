---
title: "osd-lyrics can't download the correct lyrics!?"
date: 2013-03-04
forum: Multimedia Software
---

### Post by GnuKian on 2013-03-04
To improve my English, I use the program [OsdLyrics]("https://github.com/osdlyrics/osdlyrics") (a _dynamic_ lyrics player). Indeed, this is the only Linux software equivalent to [Minilyrics]("http://www.crintsoft.com/") that I could find.
 Osdlyrics often can not download the right lyrics compared the playing song! for example, Now I'm listening to the "Jessie Ware - Devotion - 2012" album, but only two of the lyrics are properly downloaded! the other lyrics have the correct name and the wrong contents or a chinies translation of song!
Osdlyrics use 2 engines: ttplayer & xiami;[B]A
Any idea to replacing the engines or improvement in the way that the program recognize lyrics?[/B]

if you want to test this software, run these commands:
```

sudo add-apt-repository ppa:osd-lyrics/ppa
sudo apt-get update
sudo apt-get install osdlyrics
```
[IMG]http://uploadtak.com/images/l316_lyr.png[/IMG]

---

### Post by GnuKian on 2013-03-05
Is it possible to change the default osd-lyrics engines as same as [lrc-show-x]("http://uploadkon.ir/uploads/lrcshow%20x%20demo%20video.flv")?
(osd-lyrics is more handsome than lrcshow-x)

---

### Post by GnuKian on 2013-03-08
except osd-lyrics and lrcshow-x, Is there any other choice?

---

### Post by GnuKian on 2013-04-21
After days; Sorry: Up

---

### Post by rusta on 2013-07-07
I have my own script for that. I use it with "Custom actions" on Thunar.

[http://pastebin.com/yH3EHmhL](http://pastebin.com/yH3EHmhL)

it use glyrc command to retrieve lyrics.  I set 5 seconds to wait for each server to respond. You can change that time at glyrc line

If lyrics were found it will open a zenity dialog --text-info and you can copy the lyrics to the clipboard with a button or cancel (close the dialog)
If no lyrics were found then a notify will pop-up.

Read inside the script, you can change database folder (cache) location.

dependencies:  glyrc, sqlite3, eyeD3, zenity, libnotify-bin, xclip

The script takes the song info from tag, so , they should be there and with correct information about the song

You can add more code to this script. glyrc is very versatile and you can retrieve the artist photo, bio, and something more.

./letras_com_en "song.mp3"

 don't forget quotes if spaces are in name

Happy Lyric'ng

---

### Post by rusta on 2013-07-07
/.letras_com_en   is my script name, only that.

---

### Post by mynonrealemail on 2013-11-15
> **rusta said:**
> 
./letras_com_en "song.mp3"
don't forget quotes if spaces are in name
/.letras_com_en   is my script name, only that.
I get the below error when I run [COLOR=#ff0000]*lyrics "/home/notrea/MyMusics/Tegan-AND-Sara/Closer.mp3"*[/COLOR]
```
bash: /home/notrea/bin/lyrics: /bin/bash^M: bad interpreter: No such file or directory
```

@rusta
1. I've saved your script into a file (named 'lyrics') and `chmod +x` and put it under '[COLOR=#ff0000]*/home/notrea/bin*[/COLOR]' folder. but it does not work?
2. Can it handle a folder of songs?

---

