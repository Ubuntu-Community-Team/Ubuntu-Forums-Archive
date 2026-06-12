---
title: "Convert video"
date: 2012-02-27
forum: Multimedia Software
---

### Post by Miykel on 2012-02-27
G'Day, Is there anyway I can convert various video formats into mpeg using ffmpeg ???
Regards Miykel

---

### Post by andrew.46 on 2012-02-28
> **Miykel said:**
> G'Day, Is there anyway I can convert various video formats into mpeg using ffmpeg ?

Certainly there is a way :). Your best bet is to make sure your copy of FFmpeg is un-crippled:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and then run the following command against one of the files you wish to convert:

```
ffmpeg -i my_file
```

substituting 'my_file' for the actual name of your file. Post the command + full terminal output here and a suitable commandline can be suggested.

Do you have a particular need for mpeg or will another container such as mkv or mp4 be suitable?

---

### Post by Miykel on 2012-02-28
Thanks for the reply Andrew.46,
   The links you gave me I have already visited, thats where I got FFmpeg from, I live in a mtr home, traveling round Australia, and I have to convert all movies to mpeg, copy to an external HDD to watch on my TV when I'm running on batteries, my PC used to much power so I only run it when I'm either plugged into mains or running my Generator, the command you gave me , ffmpeg -i my_file, how much of the file path do I have to write in the terminal, the file is in  Home/Downloads/warehouse13......., but when I write that kind of file path, with the full name of the file,the terminal says  no such file.  blast !! lol.
     I'm still shooting in the dark a bit with Ubuntu, specially with the terminal, so any help will be greatly appreciated.
Regards  Miykel

---

### Post by andrew.46 on 2012-02-28
I am in Australia myself, always good to meet another Aussie on the Forums :). You can change to the location of the file:

```

cd $HOME/Downloads/warehouse13

```

and if this path is correct you can then run the command I suggested. The command *ls* will show the files available in this location.

---

### Post by Miykel on 2012-02-28
Thanks again mate; still  "no such file or directory", blast !!, the trouble is I think I need more educating re; Ubuntu basic principles, lol. I tried a few different ways of writing the file name, even exactly as it is in the folder but no good, I'm sure I'm doing something wrong but I don't know what, due to ignorance lol, could you write the whole command for me so i can see if I'm on the right track or not please ???
  The folder containing the episodes is;
Home/Downloads/Warehouse.13.Season.3
 Thats exactly as it is written
Many Thanks  Miykel
P.S.  Where are you, I'm sitting out the rain in Narrabri !!!

---

### Post by andrew.46 on 2012-02-28
Perhaps the easiest way to get the exact location of the file/directory is to run the following in a terminal window:

```
find $HOME -iname 'Warehouse.13.Season.3*'
```

And I am inside hearing the rain pound down in the Blue Mountains :).

---

### Post by inobe on 2012-02-28
right click the file and hit properties.

copy and paste what the entire name is.

sorry to jump in, this is just what i do when i cd to a file.

---

### Post by techfreakd on 2012-02-29
There are many online web site and software available in internet to convert any type of video. you can choose any format.

---

### Post by Miykel on 2012-03-01
Thanks for the replies guys, I can't get any of it to work though, just get message "no such file etc", I'll just have to play around till I get it to work I guess, I installed  Avidemux  and used that to convert the video's but I still want to learn to use ffmpeg just for the sake of it.
Kind regards Miykel

---

