---
title: "avi to flv converter"
date: 2007-09-28
forum: Multimedia &amp; Video
---

### Post by msadiqrajani on 2007-09-28
does any one know a converter which converts avi files to flv.
or
any avi player for **ubuntu 6.06 lts.**

thanks

---

### Post by ghostborg on 2007-09-28
Hi ,

Windows:
Replay Converter 2.80  Demo fully functional up to 90sec. Look for crack or buy(yuck).

[http://applian.com/replay-converter/demo.php]("http://applian.com/replay-converter/demo.php")

As for an AVI player Most players should work VLC, Movie player.


I use Ubuntu 7.1 beta and am still a noob myself.
I'm not in front of Ubuntu right now, this is from memory:
Maybe you need the codecs to play . Use the Add/Remove programs from the main menu  and type "codec" in the search. Check box  the ones like g?streamer. Also make sure that the drop down box says all programs. Another thing to check is that your repositories, in Synaptic, include the restricted stuff.

Good Luck

---

### Post by eggdeng on 2007-09-28
Easiest is to use ffmpeg ```
 ffmpeg -i video.avi video.flv
```
If you have Mplayer installed, you can use Mencoder from the command line, something like
```
mencoder video.flv -oac copy -ovc lavc -o video.avi
```
Generally Mplayer can play a lot of formats that other apps won't, especially .wmv stuff. As for .avi, it's a container, not a file format so whether or not you can play a given .avi file with a particular player will depend on the file type.

---

### Post by msadiqrajani on 2007-09-28
thanks for reply
ffmpeg not work for me.i think i am too noob to ubuntu.

---

### Post by eggdeng on 2007-09-29
What error do you get? Check ffmpeg is installed ```
which ffmpeg
``` You should get ```
/usr/bin/ffmpeg
``` When you type the command ```
 ffmpeg -i video.avi video.flv 
``` make sure you replace video.avi with the path to your file and video.flv with the path where you want to create the new file. For example, if I have a video called hot_chicks.avi in a folder called research on my Desktop, the command would read ```
 ffmpeg -i /home/eggdeng/Desktop/research/hot_chicks.avi  /home/eggdeng/Desktop/research/hot_chicks.flv 
```

---

### Post by msadiqrajani on 2007-09-29
**error:bash: ffmpeg: command not found**

no ffmpeg binary on that location 

i think i dont have ffmpeg installed

---

### Post by eggdeng on 2007-09-29
```
sudo apt-get install ffmpeg
```

---

### Post by msadiqrajani on 2007-09-29
thanks for reply but.....
another error:
[B]Reading package lists... Done
Building dependency tree... Done
Package ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ffmpeg has no installation candidat[/B]e

---

### Post by eggdeng on 2007-09-29
You need to update your repositories. Use this command ```
lsb_release -a
``` to check which version of Ubuntu you are using. Then follow the instructions at[ https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") to update your repos. You will also be told how to install lots of codecs & media players which will enable support for different file types.

---

### Post by msadiqrajani on 2007-09-29
thanks **eggdeng**
now i can play my blender tutorial videos.
thanks ones again.

---

### Post by nawcom on 2007-11-23
> **ghostborg said:**
> Hi ,

Windows:
Replay Converter 2.80  Demo fully functional up to 90sec. Look for crack or buy(yuck).

[http://applian.com/replay-converter/demo.php]("http://applian.com/replay-converter/demo.php")



fyi applian violates the GPL by directly using mplayer and mencoder for the video conversion. they don't even try to hide it either for some reason check task manager while converting - you'll see mencoder.exe doing the work). Anyways, please support the MPlayer developers and don't do business with Applian; there are many frontends for mencoder, mplayer, and ffmpeg which can make converting easier.

---

### Post by rare HERO on 2008-05-16
> **eggdeng said:**
> Easiest is to use ffmpeg ```
 ffmpeg -i video.avi video.flv
```
If you have Mplayer installed, you can use Mencoder from the command line, something like
```
mencoder video.flv -oac copy -ovc lavc -o video.avi
```
Generally Mplayer can play a lot of formats that other apps won't, especially .wmv stuff. As for .avi, it's a container, not a file format so whether or not you can play a given .avi file with a particular player will depend on the file type.

Thanks eggdeng
worked perfectly.

---

