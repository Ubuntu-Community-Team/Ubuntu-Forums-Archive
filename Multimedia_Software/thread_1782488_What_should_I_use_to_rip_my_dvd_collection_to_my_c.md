---
title: "What should I use to rip my dvd collection to my computer to play on my tv?"
date: 2011-06-14
forum: Multimedia Software
---

### Post by Aeonis on 2011-06-14
I'm still trying to figure out how to get my movies to play on my xbox in a different room.  It's giving me some problems.

Until I get that going, I wanted to go ahead and rip my dvd collection and have it to play on my xbox.  That being said, I looked at some different ripping utilities, but I wanted to try to keep everything in mp4 format (or something similar) without needing to use the DVD menu and such.  I'd like to be able to enable or disable closed captioning as well.

Could someone help me find a utility that will do that?

---

### Post by handy on 2011-06-14
I used HandBrakeCLI to rip my collection to HDD in .mp4 format. I included subtitles which if you use .mp4 with HandBrake are incorporated into the video & can't be turned off. Those that didn't have subtitles I downloaded in .srt format from the web & they can be turned on/off.

HandBrake also allows you to make .mkv files. If you go that route you can rip the subtitles separately & therefore turn them on/off.

You don't have to use HandBrakeCLI if you prefer a GUI.

From memory, I think it is due to different attitudes to libraries & such you can't access HandBrake from the Ubuntu repos. So you have to do it another way:

[http://www.jonathanmoeller.com/screed/?p=2991](http://www.jonathanmoeller.com/screed/?p=2991)

---

### Post by Aeonis on 2011-06-15
> **handy said:**
> I used HandBrakeCLI to rip my collection to HDD in .mp4 format. I included subtitles which if you use .mp4 with HandBrake are incorporated into the video & can't be turned off. Those that didn't have subtitles I downloaded in .srt format from the web & they can be turned on/off.

HandBrake also allows you to make .mkv files. If you go that route you can rip the subtitles separately & therefore turn them on/off.

You don't have to use HandBrakeCLI if you prefer a GUI.

From memory, I think it is due to different attitudes to libraries & such you can't access HandBrake from the Ubuntu repos. So you have to do it another way:

[http://www.jonathanmoeller.com/screed/?p=2991](http://www.jonathanmoeller.com/screed/?p=2991)

How do I use the CLI?  Is there a good tutorial I can follow?  I am new to CLI.  I tried the GUI, but it only grabbed part of the video.

EDIT:  Well, on Windows, it doesn't work right.  On Ubuntu, it's awesome.  I do have one problem.  I'm ripping a DVD that has 2 chapters, but in the "Title" area, it has about 10 different areas.  How do I combine them all into one?

What I'd really like to do is this:  This dvd has a menu that access three different videos.  How can I get this one to go ahead and load the menus?  Or...can I separate it out to just choose one of hte sub menus?

---

### Post by Zachzee on 2011-06-15
I haven't used this program much but it may work here 
try: dvd::rip (found mine in my software center)
i don't know if it will help but you can try?

---

### Post by handy on 2011-06-16
> **Aeonis said:**
> 
How do I use the CLI?  Is there a good tutorial I can follow?  I am new to CLI.  I tried the GUI, but it only grabbed part of the video. 

If you go to the handbrake web sit you will find plenty of how-to. Also *"HandBrakeCLI --help"* will probably give you all you need.

What I do to make it easier for my dreadful memory as far as the HandBrakeCLI command line is concerned, is have an alias in ~/.bashrc which when I call it, doesn't do the job first up, but I can then copy & past it in the Terminal & edit the output name to suit.

Here is what I use in my ~/.bashrc :

```
alias .tmp="cd /mnt/store/pkg/vid/.tmp"

alias hbt="echo HandBrakeCLI -t <title number here> -i /media/dvd -o NAME-HERE.mp4 -e x264 -b 1000 -B 192 -s 1 --subtitle-burn"

alias hbhelp="HandBrakeCLI --help"
```

> **Aeonis said:**
> 
EDIT:  Well, on Windows, it doesn't work right.  On Ubuntu, it's awesome.  I do have one problem.  I'm ripping a DVD that has 2 chapters, but in the "Title" area, it has about 10 different areas.  How do I combine them all into one?

What I'd really like to do is this:  This dvd has a menu that access three different videos.  How can I get this one to go ahead and load the menus?  Or...can I separate it out to just choose one of hte sub menus?

You can't do the menu thing with HandBrake. What you learn to do is run the command line as I posted above, with "0" as the title number. What that does is scan the media (DVD or HDD) & give you the results. The results may look a little complicated at first, but with a little experience you learn which bits you want to look at.

You look at the various titles (numbered) & see how long they are. This makes it quite easy to find the main title & also if you have multiple worthwhile chapters/sections on the DVD, you can find identify them & rip/transcode them one after the other.

It works for me, I've probably done a thousand of the things.

You can rip the subtitles & if none exist you can add them by picking them up from various sites on the net.

---

