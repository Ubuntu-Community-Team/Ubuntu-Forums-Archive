---
title: "Xmms2d uses ~30% CPU on some songs."
date: 2008-06-20
forum: Multimedia Software
---

### Post by LinuX-M@n1@k on 2008-06-20
This only happens on some songs.

Why? And how do I prevent this from happening?

From `top`:
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND  
 6853 boris     20   0  105m 9.9m 6872 S 32.0  1.0  21:32.82 xmms2d
```

---

### Post by LinuX-M@n1@k on 2008-06-20
.

---

### Post by LinuX-M@n1@k on 2008-06-21
.

---

### Post by xc3RnbFO8P on 2008-06-21
Did check the songs if they are CBR or VBR?

---

### Post by LinuX-M@n1@k on 2008-06-21
What is CBR and VBR and what is the difference between them?

How do I check if they are CBR or VBR?

---

### Post by xc3RnbFO8P on 2008-06-21
You can use **mp3check** to find errors (Synaptic Package Manager).

in Terminal:
mp3check -e /home/and what ever your mp3 file is/

---

### Post by LinuX-M@n1@k on 2008-07-10
xmms2d uses 38% cpu on radio stream and 34% cpu on some of the songs.

mp3check on one of the songs using high cpu:
```
$ mp3check -e dcpp/Akon\ Feat.\ Kardinal\ Offishall\ -\ Dangerous.mp3 
dcpp/Akon Feat. Kardinal Offishall - Dangerous.mp3:
1503 bytes of junk before first frame header
valid id3 tag trailer v1.0 found
$ 
```

mp3check on one of the songs using about 3-5% cpu:
```
$ mp3check -e dcpp/Missy\ Elliott\ ft.\ Fatman\ Scoop\ -\ Lose\ \ Control.mp3 
dcpp/Missy Elliott ft. Fatman Scoop - Lose  Control.mp3:
545 bytes of junk before first frame header
valid id3 tag trailer v1.0 found
$ 
```

If someone wants to test the radio stream:
[http://193.108.24.21:8000/fresh.m3u](http://193.108.24.21:8000/fresh.m3u)

Sorry for the laaaaaaate reply (don't ask). I hope I'm not too late.

---

### Post by xc3RnbFO8P on 2008-07-10
Try vbrfix in Synaptic Package Manager.
> $ vbrfix --help
VbrFix Command Line Version
===========================
By William Pye, visit [www.willwap.co.uk](www.willwap.co.uk) for latest version
No Arguments Given
Use:
vbrfixc -flag1 -flag2 -flagn in.mp3 out.mp3
FLAGS::
-ri1          removeId3v1 Tag
-ri2          removeId3v2 Tag
-skiplame     if tag made by lame don't fix it
-allways      always write even if not vbr
-makevbr      make it vbr(you need -allways also)
-log          write a log file
-lameinfo     keep the lame info


---

### Post by LinuX-M@n1@k on 2008-07-10
For the stream ?

edit: Now xmms2d uses 3% cpu with the radio stream? What's happening?

---

### Post by xc3RnbFO8P on 2008-07-10
> edit: Now xmms2d uses 3% cpu with the radio stream? What's happening?
Did you install some codec?

---

### Post by LinuX-M@n1@k on 2008-07-10
> **Ringi said:**
> Did you install some codec?

Yes, every codec named GStreamer in Applications > Add/Remove.

No change: 3% cpu usage with the stream and 35-38% with some songs. Don't tell me I have to check all and fix them one by one... Sorry, but, xmms2 is what should be fixed, not the songs!

Correct me if I'm wrong.

---

### Post by LinuX-M@n1@k on 2008-07-11
bump

---

### Post by xc3RnbFO8P on 2008-07-11
> xmms2 is what should be fixed
Yes.
Solved?

---

### Post by LinuX-M@n1@k on 2008-07-11
> **Ringi said:**
> Solved?

No, unfortunately...

---

### Post by LinuX-M@n1@k on 2008-07-14
WtF ?!?!?!!!!!!!!!

```
  PID USER      PR  NI  VIRT  RES  SHR S **%CPU** %MEM    TIME+  **COMMAND**          
 6618 boris     20   0 2772m  13m 6696 R **94.5**  1.4   2:43.76 **xmms2d**          
```

94.5% !!! It's not 100% because I'm using firefox........

After the song ended xmms2 crashed!
And the last time I started xmms2 it used 100% RAM (1GB) and 100% SWAP (506MB)!

---

