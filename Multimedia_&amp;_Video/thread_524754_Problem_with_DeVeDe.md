---
title: "Problem with DeVeDe"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by Fiki on 2007-08-13
I am trying to convert a .avi file to a burnable DVD. I tried using DeVeDe but whenever i use it the end product is a picture with horizontal lines across it and scratchy chaotic noise. I made sure I was using the North American format and I made sure the video file worked prior to trying to convert it. If DeVeDe dosn't work can anyone reccomend a better solution?

---

### Post by Steveway on 2007-08-13
The mplayer and mencoder packages in the repos are broken!
That is causing that noise.
You can download a patch at the DeVeDe site wich fixes it by changing the binaries with slightly older but functionable ones.
The patch is on the bottom of this page: [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

---

### Post by Fiki on 2007-08-13
I tried installing the patch by using the sh command on the sh file but the problem still presists. am i doing it wrong?

---

### Post by Steveway on 2007-08-13
Did it say that the patch has been applied correctly?

---

### Post by Fiki on 2007-08-13
when i run the command again it says this:

cp: cannot stat `mplayer': No such file or directory
cp: cannot stat `mencoder': No such file or directory

Done. MPlayer and Mencoder downgraded.

---

### Post by Steveway on 2007-08-13
You have to use sudo infront of the command.
If you're in the directory a simple:
$sudo sh install.sh
should do it correctly.

---

### Post by Fiki on 2007-08-13
when i did it i just did sudo su first than the sh command. I tried it again just putting sudo in front and it does the exact same thing. still dosn't fix the problem.

---

### Post by Fiki on 2007-08-13
I figured out what was wrong and i feel like an idiot, but I'm excited I got it to work nonetheless. The problem was merely that I had not stored and run the patch in the same directory as mplayer and mencoder had been installed in - hence the error message that no such files could be located. If anyone else is as empty-headed as me I hope they see this and this helps. Thanks for trying to help anyway :)

---

### Post by Oddvar on 2007-08-15
I have the same problems with devede,mencoder and whatever.. When I installed the "fix" from rastersoft, not even Ubuntu can read my CD's. I have tried to remove the fix, but the errors still there. What is more, when I first installed Feisty (about 2 or 3 mnths ago) everything for the CD's (burning and playing) function perfect. So what has happened? Can anyone tell what to do to get this right again?

---

### Post by Amazona aestiva on 2007-08-15
DeVeDe have been working on my computer since 2 hours!
I use Feisty, DeVeDe 3.01 and this:
[http://www.rastersoft.com/descargas/mplayer_fixed.tar.bz2]("http://www.rastersoft.com/descargas/mplayer_fixed.tar.bz2")
Install steps:
1.Unpack it
2.Open terminal
3.type cd (directory where you extracted) Example: cd '/home/nandor/Desktop/mplayer_fixed'
4.```
sudo ./install.sh
```
5.Enter your password

---

### Post by Artemis3 on 2007-08-18
That mplayer/meconder must be a different compile from the package in edgy. I tried installing the package from edgy and it produced the same (noisy) result, but with the binaries provided in that page the problem is gone...

BTW: with a stereo source you can't go above 384kbps for the audio. Devede won't tell you why but it refuses to encode if you try any higher bitrate.

480x480(576) is valid resolution for SVCD, not DVD.

---

### Post by Southeast First on 2007-08-22
I've downgraded my mplayer and mencoder and that fixed the sound, but when I burn the DVD and pop it into my DVD player the video is messed up. It's almost as if the frames of the video are moving from bottom to top of my screen. However when I pop it into my computer and watch with mplayer it's fine. Can anyone help me?

---

### Post by kelvin spratt on 2007-08-22
Are you using the Latest DeVeDe 3.03 is the latest some of the earlier versions did not work in Ubuntu but are fine in other distros i have burned over 100 DVDs Authored by DeVeDe all done as ISOs then burnt using Nero. All have worked flawlessly using Verbatim at x16, make sure you don't use things like Compiz or beryl while you are useing progs like DeVeDe, if you are not then you need to reinstall the software and patch and try again or use the mencoder Deb From Dapper that works ok.

---

### Post by Southeast First on 2007-08-22
Yup, I'm on Gnome right now, using K3B to burn. And yup, it's the lastest version of DeVeDe. Right now I'm burning a DVD whose video_ts files were created on a Windows machine, so I can determine whether it's a problem with DeVeDe or K3B.

---

### Post by kelvin spratt on 2007-08-22
its not Devede its Ubuntu thats the problem there is a problem with mencoder i also use Debian and that runs ok with the much outdated Devede, but saying that i use Feisty all the time with devede as i also use cinelerra in feisty then Devede to Author. i personally don't like K3B i always had problems with it in edgy and have not bothered since.

---

### Post by Southeast First on 2007-08-22
> **kelvin spratt said:**
> its not Devede its Ubuntu thats the problem there is a problem with mencoder i also use Debian and that runs ok with the much outdated Devede, but saying that i use Feisty all the time with devede as i also use cinelerra in feisty then Devede to Author. i personally don't like K3B i always had problems with it in edgy and have not bothered since.

> **Southeast First said:**
> **I've downgraded my mplayer and mencoder **and that fixed the sound, but when I burn the DVD and pop it into my DVD player the video is messed up. It's almost as if the frames of the video are moving from bottom to top of my screen. However when I pop it into my computer and watch with mplayer it's fine. Can anyone help me?

Turns out it probably is K3b, I'll make a new thread.

---

