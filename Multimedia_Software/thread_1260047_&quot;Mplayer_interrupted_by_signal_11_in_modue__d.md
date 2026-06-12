---
title: "&quot;Mplayer interrupted by signal 11 in modue : decode_video&quot; ???"
date: 2009-09-07
forum: Multimedia Software
---

### Post by Little Ghost on 2009-09-07
Hello !

I've got this message when I try to open some videos with Mplayer. Does anyone know how to fix it ?

---

### Post by wojox on 2009-09-07
Have you installed the w32codecs?

---

### Post by Little Ghost on 2009-09-07
I've got them, yes

---

### Post by andrew.46 on 2009-09-07
Hi Little Ghost,

> **Little Ghost said:**
> I've got this message when I try to open some videos with Mplayer. Does anyone know how to fix it ?

Can you run one of these problem files from the commandline with the following syntax:
```

mplayer -v ***[COLOR="Red"]my_problem_file.avi[/COLOR]***
```

Hosever I have a deep suspicion that the answer may very well be that you need to upgrade your copy of MPlayer, particularly if you are running the Ubuntu repository version...

Andrew

---

### Post by Little Ghost on 2009-09-07
I can't open them with these command lines, but I think I git mixed up (terminale says it can't find the file...)

As to the upgrade, I've tried different ways without success...

---

### Post by andrew.46 on 2009-09-07
Hi Little Ghost,

> **Little Ghost said:**
> I can't open them with these command lines, but I think I git mixed up (terminale says it can't find the file...)

An easy way to do this is to drag your problem file onto the Desktop. Then open a Terminal and type:

```
mplayer -v $HOME/Desktop/**[COLOR="Red"]myfile[/COLOR]**
```

substituting *myfile* for the name of your own file. You will find that you only need to type in the first few letters and then press the TAB key to complete the correct filename.

All the best,

Andrew

---

### Post by Little Ghost on 2009-09-08
OK, I've opened the file thanks to your explanations, but when mplayer reads it, the video speeds up and slows down any time...

---

### Post by andrew.46 on 2009-09-08
Hi Little Ghost,

> **Little Ghost said:**
> OK, I've opened the file thanks to your explanations, but when mplayer reads it, the video speeds up and slows down any time...

Could you then copy the entire terminal output and paste it into a message here? This will usually give a few hints as to what is going on. I might suggest as well that you give a thought to upgrading your copy any way from RVM's PPA:

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

All the instructions are on this page and this will give you a vastly improved MPlayer that might very well solve the MPlayer crash you are experiencing.

All the best,

Andrew

---

### Post by Little Ghost on 2009-09-08
I've downloaded it, but it still refuses to read the video. The message isn't the same, though : "Cannot find codec for audio format 0x81".
I've just done a quick searh on the net, but there seems to be no thread at all concerning that message...

---

### Post by andrew.46 on 2009-09-08
Hi Little Ghost,

> **Little Ghost said:**
> I've downloaded it, but it still refuses to read the video. The message isn't the same, though : "Cannot find codec for audio format 0x81".

Does the new version of MPlayer run other media files ok though, in particular I hope the message:

```
Mplayer interrupted by signal 11 in modue : decode_video
```

is no longer seen? Concerning this particular problem file, the one that throws the message:

```
Cannot find codec for audio format 0x81
```

is there somehow I can see this file? Perhaps a download link or can you post it somewhere?

Andrew

---

### Post by Little Ghost on 2009-09-09
The former message is no longer seen, that's right ! But now I've got "unsupported pixe format -1"... The file (HD) shows strange squares quite often...

---

