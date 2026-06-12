---
title: "Subtitles are black independent of options passed"
date: 2011-05-15
forum: Multimedia Software
---

### Post by prconnor@gmail.com on 2011-05-15
Hello,

I have ripped a movie with this command:
```
mencoder "$name".vob -ofps 24000/1001 -aid 128 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000  -vf crop="$cropfactor",hqdn3d=2:1:2 -xvidencopts chroma_opt:vhq=4:bvhq=1:fixed_quant=3 -vobsubout "$name" -vobsuboutindex 0 -sid "$sidnum"  -o ~/"$name".avi
```

This results in three files with the same root name appended .avi .idx and .sub.

When I play the video I see the subtitles that I want, but they are black, and not at all visible.  I see the same font and color when I pass any of the following -sub-bg-color or -*** -***-color ffffff00, either on the command line, or in the config file.

This seems to be true for pretty much all of the files that I have encoded.

Thank you for your help.

---

### Post by handy on 2011-05-15
Try HandBrakeCLI, it works a treat.

I've never used the GUI version, so I can't comment on it.

I put the following in my ~/.bashrc so I can easily call up the command line from the Terminal (which doesn't work), I then copy the failed command & paste it to the command prompt, then make any edits required & go on from there:

```

alias .tmp="cd /mnt/store/pkg/vid/.tmp"

alias hb="echo HandBrakeCLI -t --main-feature -i /media/dvd -o NAME.HERE.mp4 -e x264 -b 1000 -B 192 -s 1 --subtitle-burn"

alias hbt="echo HandBrakeCLI -t <title number here> -i /media/dvd -o NAME-HERE.mp4 -e x264 -b 
1000 -B 192 -s 1 --subtitle-burn"

alias hbhelp="HandBrakeCLI --help"
```

The above sets the output to .mp4 with a file size of approx' 1GB & includes what are usually (-s 1) the English subtitles, though there are occasionally differences.

It is good to use "-t 0" instead of "-t --mainfeature" as you get a chance to check out just what you've got on the DVD which allows you to confirm the subtitles number, If there are multiple features that you want to choose from in one way or another & such.

Anyway it works for me, I've backed up hundreds of DVD's from my collection using this method.

---

### Post by prconnor@gmail.com on 2011-05-15
Using this method do you have the option to enable or disable subtitles?  I suppose the proper thing for me to do is to research the handbrake myself.  Any way thank you for the tip, I'll try it.

It seems that when I rip the subtitles from a vob, acquired using mplayer $title -dumpstream as in the post above that the subtitles are black, however if I rip the subtitles directly from the disc then they are white as in:

```
# Rip the subtitle directly from the dvd
mencoder "$title" -vobsubout "$name" -vobsuboutindex 0 -sid "$sidnum" -ovc frameno -nosound -o ~/"$name".avi
```

I haven't tested this exhaustively, but that seems to be the pattern.  I like that I can turn the subtitles off and on, I would just also like to change the color from black to white.  If I can't find how to do it I can always just re-rip directly from the disc.  Still I am curious to know what is going on, why it behaves as it does.

---

