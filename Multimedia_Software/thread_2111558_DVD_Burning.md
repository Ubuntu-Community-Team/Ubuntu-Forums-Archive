---
title: "DVD Burning"
date: 2013-02-02
forum: Multimedia Software
---

### Post by Shadius on 2013-02-02
Hello,

I have a video file (.mkv) and its subtitle file (.srt) that I would like to burn to a DVD. How do I go about doing so? Which program do I use? I would prefer something with a GUI since I'm not so good with the command line. Thank you.

---

### Post by prodigy_ on 2013-02-02
**Brasero** is a CD/DVD burner included with Ubuntu. It's a GUI application. For converting from MKV to video DVD you can install **Devede**. And for DVD authoring there's **Bombono DVD**.

---

### Post by howefield on 2013-02-02
I would use Devede if you mean to play the DVD in DVD player.

---

### Post by Shadius on 2013-02-02
Thank you for the replies. When I try to install DeVeDe, it gives me a list of things I need to uninstall, so how do I uninstall them? How come I have to uninstall things to get DeVeDe anyway? Kind of confused about that. Here's a screenshot of what Ubuntu Software Center says:

---

### Post by gifford on 2013-02-02
I use K3b, it's in the software center and synaptic. Easy to use with nice GUI. There are a number of add-ons for almost anything you would need.

---

### Post by Shadius on 2013-02-03
So I tried DeVeDe and it created an ISO file that would take up about 6.2 GB on a DVD. I only have 4.7 GB DVDs, so my question is, how can I split it into 2 discs? I'll take a look at K3b also.

---

### Post by Bucky Ball on 2013-02-03
*Thread moved to **Multimedia & Video**.*

@ Shadius: Not sure why you are posting in Abosolute Beginners with 979 beans ... ;)

---

### Post by Shadius on 2013-02-03
> **Bucky Ball said:**
> *Thread moved to **Multimedia & Video**.*

@ Shadius: Not sure why you are posting in Abosolute Beginners with 979 beans ... ;)

Sorry, I was going to post in there, but figured since I know nothing about burning a video DVD on Ubuntu, I'd post it in the beginner's section. Thanks for moving it to the appropriate section.

---

### Post by sudodus on 2013-02-03
> **Shadius said:**
> So I tried DeVeDe and it created an ISO file that would take up about 6.2 GB on a DVD. I only have 4.7 GB DVDs, so my question is, how can I split it into 2 discs? I'll take a look at K3b also.
If you find no other way to split the video, it should work with either of these, to change the video (before making an iso file of it).

1. Try with ffmpeg to make one copy of the first part of the video, and one copy of the second part using the -t and -ss options.

2. Try with ffmpeg to decrease the file size via quality of the video, so that the whole video will fit in one DVD disk. I mean that you can decrease the frame size or use some filter or simply decrease the video bitrate using the -b option.

See ```
man ffmpeg
``` or some tutorial on the internet.

---

### Post by Bucky Ball on 2013-02-03
All good. Probably have better luck here, beginner burner or not. ;)

---

### Post by speartip on 2013-02-03
How long (time wise) is the file that you want to convert to a DVD iso?
When you load it in Devede, you can click the "adjust disc usage" button & it will reduce the iso to a size that will fit on one dvd.
 I also enable "dual pass encoding" in properties/quality, it takes longer but quality is better imo.

---

### Post by petersonlevi88 on 2013-02-05
I am lost on the DVD burning my friends. Either the files are wrong, or I am missing something important. I have tried k3b and DeVeDe. The original is a DVD rip Xvid.avi download. On DeVeDe I have dropped the framerate down and have tried the MPEG and iso options. On the iso it says burning to disc and successfully created DVD, but it will not play in a DVD player. It takes over 2 hours for DeVeDe to convert file before burning. And no, I'm not selling them. LOL I just wanna watch on my bigger tv instead of my 15" DELL monitor. Can someone please help? Thank you.

P.S. I have several different formats including rar. I have to use vlc for a few to play. My goal is to get my collection of 30 movies all to DVD format that will play in my home DVD player. Thank you and any help is greatly appreciated as this kinda stuff is new to me

---

### Post by speartip on 2013-02-05
It could be your codecs or settings.
Make sure you have the medibuntu repo enabled.
I also use the latest ffmpeg ppa from here:
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)
& the latest devede from here:
[http://www.rastersoft.com/programas/devede.html#download_section](http://www.rastersoft.com/programas/devede.html#download_section)
In devede settings make sure in preferences the video & menu encoder is set to ffmpeg. And in advanced options create an iso image is ticked.
I also followed the instructions here as well:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
under installing libdvdcss.

Also when using Brasero to burn the dvd, make sure you select "burn image" & not "video project"

Other than that i'm out of ideas.

---

### Post by petersonlevi88 on 2013-02-05
> **speartip said:**
> It could be your codecs or settings.
Make sure you have the medibuntu repo enabled.
I also use the latest ffmpeg ppa from here:
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)
& the latest devede from here:
[http://www.rastersoft.com/programas/devede.html#download_section](http://www.rastersoft.com/programas/devede.html#download_section)
In devede settings make sure in preferences the video & menu encoder is set to ffmpeg. And in advanced options create an iso image is ticked.
I also followed the instructions here as well:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
under installing libdvdcss.

Also when using Brasero to burn the dvd, make sure you select "burn image" & not "video project"

Other than that i'm out of ideas.
Thank you speartip. I was able to get it to play in an Apex dvd player, however, it showed a scrolling screen like an old tv does when you have the horizontal knob turned too far. I will try all your suggestions to see if I can fix.

Also, how do enable medibuntu? I have no clue what that is?

---

### Post by petersonlevi88 on 2013-02-06
Thank you speartip

---

### Post by speartip on 2013-02-06
Hi,
To enable medibuntu.
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

### Post by Shadius on 2013-02-06
> **speartip said:**
> How long (time wise) is the file that you want to convert to a DVD iso?
When you load it in Devede, you can click the "adjust disc usage" button & it will reduce the iso to a size that will fit on one dvd.
 I also enable "dual pass encoding" in properties/quality, it takes longer but quality is better imo.

Thank you very much. That solved it for me.

---

### Post by speartip on 2013-02-06
No problem.
Glad I could help.

---

