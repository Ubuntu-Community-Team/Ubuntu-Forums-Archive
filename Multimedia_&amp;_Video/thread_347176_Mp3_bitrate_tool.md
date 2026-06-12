---
title: "Mp3 bitrate tool?"
date: 2007-01-26
forum: Multimedia &amp; Video
---

### Post by Flavian on 2007-01-26
Hi guys :)
I've got the following "problem" I've got 1257 Mp3s (2.3Gb) which I want to put on my cell phone memorycard in order to listen to them.
The problem is that the Card is only 2Gb big.
So I was wondering if there was a tool, with which I can decrease the Bitrate of the Mp3s from 64 to 32 and do that in BATCH mode. Because doing that for every single file would just kill me!

Thanks for any help!
Flo

---

### Post by RomeReactor on 2007-01-26
Maybe [this]("http://https://savannah.nongnu.org/projects/audio-convert") will help:

```
sudo apt-get install nautilus-script-audio-convert
```

Edit: Also you probably should try with Lame:

```
sudo apt-get install lame
```

Post #6 (by metasyntax) in [this]("http://www.ubuntuforums.org/showthread.php?t=88199") thread discusses how to use it for batch conversion.

---

### Post by meng on 2007-01-26
Um, don't think that will help, because it will only convert from one format (like mp3) to another format (like ogg). But you could just use lame:
lame -b 32 original.mp3 new.mp3

Now, to do this as a batch job, I'd recommend a short shell script (unless you're a bash god and want to do it as a single command in console):
```

for filename in `ls *mp3`
do
    lame -b 32 filename new$filename
done

```
which will create new files prepended by 'new'
You could make this recursive and even overwrite the files rather than renaming the new ones.

---

### Post by RomeReactor on 2007-01-26
Well, you can try with meng's idea, but just posted this to say that the script by metasyntax works; just open a terminal and change to the directory where your mp3's are and type

```
for x in [ `ls -1 *.mp3` ]; do lame --preset 32 $x new32-${x}; done
```

Worked for me, though it **did** create new files (with a "new32-" prefix) instead of changing the ones already there.

Edit: Files must **not** have spaces between words; the only way is to place underscores "_" instead of spaces, or to do away with spaces altogether :(

meng's script looks better :D

---

### Post by Flavian on 2007-01-26
Thanks man!
That worked for me too. Awesome.
Now there is the final question: Is there a possibility to get the ID3 Tags in the new files as well? and if not with LAME, is there another possibility?

Thanks for your help guys, I really appreciate it.
Flo

---

### Post by Flavian on 2007-01-26
... and is there maybe a way to put the prefix at the end?
now it looks like that 32_name-of-file.mp3.
Is it possible to make it that way: name-of-file_32.mp3
if i put the _32 after the {x} in the command line it turns out to look that way: name-of-file.mp3_32 which obviously is wrong ;)

---

### Post by mpyusko on 2007-11-22
I'm not so sure about how to do it in a shell script, but I  use an X program called Bulk Rename (available here - [http://thunar.xfce.org/](http://thunar.xfce.org/)).  It works great for me and it allows you to find/replace, insert, overwrite, remove, number....... from right or left of name.  Like I said, it's a great little program.

---

