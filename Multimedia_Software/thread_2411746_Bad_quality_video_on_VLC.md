---
title: "Bad quality video on VLC"
date: 2019-02-03
forum: Multimedia Software
---

### Post by scabini9 on 2019-02-03
Hi, I am new in this OS, I have installed Lubuntu on my old laptop and I had a lot of problems that I could fix thanks to the forums of the community. 
Now when I want to play a movie in Full HD resolution, it plays in very bad quality. I think its a drivers issue about my videocard but I dont know how to fix it.
I would apreciate a lot if someone can help me with this problem.
Thanks for reading.

---

### Post by SeijiSensei on 2019-02-03
We need a lot more information to help.  I'm going to ask you to open the Terminal application and type a command or two.

First, run the command "lspci" which lists everything that uses the PCI bus.  You should see an entry like this

```
VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6730M/6770M/7690M XT]

```

Please report back the video device identified on your system.

Also, I'd try a different player than VLC.  The best current choice is "mpv" which you can install with the command

```
sudo apt install mpv smplayer
```

I've included the GUI called SMPlayer which provides a graphical interface to mpv (and the older mplayer).  Any better?

---

### Post by shantiq on 2019-02-04
> **scabini9 said:**
> Hi, I am new in this OS, I have installed Lubuntu on my old laptop and I had a lot of problems that I could fix thanks to the forums of the community. 
Now when I want to play a movie in Full HD resolution, it plays in very bad quality. I think its a drivers issue about my videocard but I dont know how to fix it.
I would apreciate a lot if someone can help me with this problem.
Thanks for reading.


VLC used to be king for video playback   ....    these days not so much    i suggest you install [mpv]("https://mpv.io/installation/")   > sudo apt install mpv   and either play from terminal or gui   it is STABLE and will unlikely give you the headaches that VLC can

---

