---
title: "How to make mplayer the default music player"
date: 2009-06-12
forum: Multimedia Software
---

### Post by snakeman21 on 2009-06-12
Hi, I'm running Ubuntu 9.04, and I'm trying to set mplayer as the default player for video and music files.  In preferred applications, under the multimedia tab, the drop-down menu only has two options: Rhythmbox and custom.  I've selected custom and set the command to "mplayer".  Now all of my videos open in mplayer (probably only because I deleted Totem) but my music still opens in rhythmbox.  After looking at the usage information for mplayer in the Terminal, I think I know why it won't work.  To run mplayer from a command, you have to use:

```
mplayer /path/to/file.mp3
```

Obviously, "mp3" was just my example, and you would replace it with the appropriate extension.  But the point is, Preferred applications will only run the command "mplayer", so nothing happens and it falls back on Rhythmbox.

I have a ton of music, so I'm not going to go to the properties of each one and tell it to open in mplayer, so what can I do?

I am pretty "linux-literate" so I don't mind having to edit a script or something if that's what it takes.  Thanks in advance!

---

### Post by jerrrys on 2009-06-12
am i missing something?  can't you simply right click on your music folder and choose the 'open with' option?

---

### Post by snakeman21 on 2009-06-12
Yes, but I would rather not have to do that.  I would rather be able to double-click and have the file open in mplayer by default.

---

### Post by blackxored on 2009-06-12
Try:
> System->Preferences->Multimedia->Default Player

If not, go into the manual association of file types to use your player.

---

### Post by snakeman21 on 2009-06-12
First, there is no "default player" setting in System->Preferences->Multimedia.  Second, mplayer doesn't have an option in any of its setting to associate files with it.  

I'm going to try uninstalling Rhythmbox, and see if that makes any difference.

Edit:  I also tried System->Preferences->File Management, but there's nothing there either.

---

### Post by snakeman21 on 2009-06-12
Aha! That did it.  Victory is mine!!!  I removed Rhythmbox (I never used it anyways, I use GTKpod for my iPod) and now when I open an audio file, it defaults to mplayer.

Thanks for the suggestions.  Even though I figured it out, I do appreciate the effort.

---

### Post by andrew.46 on 2009-06-12
Hi snakeman21,

You seem to have solved your problem so it only remains for me to add a small comment. I suspect you are using the default gmplayer? If you are really keen on MPlayer you might want to take rvm's SMPlayer for a spin. To my mind it is a vastly superior gui to gmplayer. I attach a screenshot to this post as a quick demo :-).

All the best,

Andrew

---

### Post by jyaan on 2009-06-12
You didn't have to remove anything, just right click the file and choose properties, then in the open with section select the program you want opened by default. However, you would need to do this for each different file format (eg. mp3, ogg, flac).

---

### Post by snakeman21 on 2009-06-13
> **jyaan said:**
> You didn't have to remove anything, just right click the file and choose properties, then in the open with section select the program you want opened by default. However, you would need to do this for each different file format (eg. mp3, ogg, flac).

Yeah, I know.  But I have a LOT of music, and it would taken forever... thanks, though.

Andrew:  I will certainly try it out, thanks!

---

### Post by konqueror7 on 2009-06-13
you don't have to associate each one, you just select the default application for that filetype...:D

---

### Post by Cammy on 2009-06-13
> **andrew.46 said:**
> If you are really keen on MPlayer you might want to take rvm's SMPlayer for a spin. To my mind it is a vastly superior gui to gmplayer. I attach a screenshot to this post as a quick demo :-).

Thanks for that post.  I just installed SMPlayer and it's really nice.  It's my default player now.

---

### Post by snakeman21 on 2009-06-13
> **konqueror7 said:**
> you don't have to associate each one, you just select the default application for that filetype...:D

I tried that, but they still opened in Rhythmbox. :confused: It's really no problem though, I never used Rhythmbox to begin with.

---

### Post by mc4man on 2009-06-13
> tried that, but they still opened in Rhythmbox

In case it comes up in future, to set a default for double left click (file association) you need to go right click -> **'properties'** -> 'open with' on any 1 example of a file type

---

### Post by Tamara Perera on 2009-06-13
Why do you need to make Mplayer your default player. It is not a great player for linux. I think there are better player than Mplayer. You can use VLC in linux. It would be great for you.

---

### Post by snakeman21 on 2009-06-13
> **Tamara Perera said:**
> Why do you need to make Mplayer your default player. It is not a great player for linux. I think there are better player than Mplayer. You can use VLC in linux. It would be great for you.

I have nothing against VLC, I think it's a good player.  I just don't care much for the interface.  I used Totem for the longest time, and then when I wanted to switch, I downloaded almost every one from the repos and tried them... I just like mplayer the best.  Nothing more than personal preference.

---

### Post by andrew.46 on 2009-06-13
Hi Cammy,

> **Cammy said:**
> Thanks for that post.  I just installed SMPlayer and it's really nice.  It's my default player now.

Good to hear :-). Not only is SMPlayer under quite active development but the developer maintains a presence on these forums as well. And of course it is a very nice gui!

Andrew

---

