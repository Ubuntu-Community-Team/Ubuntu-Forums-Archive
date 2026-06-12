---
title: "[SOLVED] TV Tuner Help"
date: 2008-04-09
forum: Multimedia &amp; Video
---

### Post by spikedupback529 on 2008-04-09
Hi,

I just installed a TV Tuner, to be exact a Hauppauge WinTV PVR 150. It shows up in Device Manager, but when I go to access it through Movie Player, when I went to Prefrences, it says no tuner, and there is no option to select my TV Tuner. 

I then proceeded to install TV Time Television Viewer. When that installed, a blue screen came up saying no signal, cannot open capture device /dev/video0. I right clicked on the blue screen, went to Input Configuration, and I tried to select Change Video Source, but nothing happened. I also downloaded the ivtv package through Synoptic with no luck.

Any suggestions?
Thanks in advance,
Dale

---

### Post by Pieboy337 on 2008-04-09
This might be a dumb question, but did you try to search for channels under channel management in tvtime?

---

### Post by Jiffyman on 2008-04-09
Do this first

```
sudo rmmod bttv
sudo rmmod bt878
sudo rmmod tuner
```Then

```
sudo modprobe bt878
sudo modprobe bttv card=? tuner=?
```Substitue ? marks with the # for your card and tuner provided below
[http://mandrivausers.org/index.php?showtopic=43596](http://mandrivausers.org/index.php?showtopic=43596)
[COLOR=Red]Also a a small note:[/COLOR] I'm not quite sure if bt878 works for this card and I'm pretty sure card=80 as for the tuner it might = 1 or 2

Afterwards 

Edit modprobe.conf for bttv```
sudo gedit /etc/modprobe.d/bttv
```and insert

```

options bttv card=? tuner=?
```[COLOR=Red]Note:[/COLOR] if you don't have gedit use nano or install gedit. When finished with the install of the card reboot.(You may not have to, but I did.)


Hope this post is of some use to you or possibly points you in the right direction.

---

### Post by spikedupback529 on 2008-04-10
Hi Jiffyman, 

Thanks for the fast response. When I went into the terminal, after I entered the first line, I got back this message:
> ERROR: Module bttv does not exist in /proc/modules

Any suggestions?

Thanks
Dale

---

### Post by Jiffyman on 2008-04-10
Ok no worry the first step is just a precaution in case the modules got added incorrectly. Even though the first line in the first step failed just do the rest. Then do the second step.
Also do you know if your card is PAL or NTSC? It will help to determine what tuner you have. By the way if you find this post useful we have a thanks feature located next to the quote button  that looks like a  star. I like your thanks in words too though.

---

### Post by spikedupback529 on 2008-04-10
Hi,

Still nothing whatsoever. 

Thanks,
Dale

---

### Post by spikedupback529 on 2008-04-10
Also,

Where do I find the channels in TV Time? All I see is a blue screen saying no imput.

Thanks
Dale

---

### Post by wolfen69 on 2008-04-10
I have a Hauppauge pvr150 card running on my gutsy box, and I get  tv by: 

```
sudo apt-get install ivtv-utils
``` 

open VLC player (install with: sudo apt-get install vlc)

File -> Open Capture Device -> PVR -> OK

then you can do (in terminal)

ivtv-tune -c25 (25 is channel number)

which changes the channel.

```
ivtv-tune -h
```

to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

to record tv:

```
cat /dev/video0 > /tmp/name_of_file.mpg
```

it will record whatever channel you are on. then ctrl-c to stop.

btw, im a neighbor in Stratford CT!

---

### Post by Jiffyman on 2008-04-10
> **spikedupback529 said:**
> Also,

Where do I find the channels in TV Time? All I see is a blue screen saying no imput.

Thanks
Dale

This might help you to configure TVtime:
[http://tvtime.sourceforge.net/usage.html](http://tvtime.sourceforge.net/usage.html)

Oh and since you live in the US the tuner should =1

> **wolfen69 said:**
> I have a Hauppauge pvr150 card running on my gutsy box, and I get  tv by: 

```
sudo apt-get install ivtv-utils
```open VLC player (install with: sudo apt-get install vlc)

File -> Open Capture Device -> PVR -> OK

then you can do (in terminal)

ivtv-tune -c25 (25 is channel number)

which changes the channel.

```
ivtv-tune -h
```to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

to record tv:

```
cat /dev/video0 > /tmp/name_of_file.mpg
```it will record whatever channel you are on. then ctrl-c to stop.

btw, im a neighbor in Stratford CT!

Is it even possible to use the card with TVtime?

---

### Post by wolfen69 on 2008-04-10
> **Jiffyman said:**
> Is it even possible to use the card with TVtime?

not that i know of. that's why i use vlc. believe me, it (vlc) will work.

once you get the "tv remote", you wont even have to open vlc. it has a button- "start tv".

if you follow my instructions, i guarantee results.

---

### Post by Jiffyman on 2008-04-10
> **wolfen69 said:**
> not that i know of. that's why i use vlc. believe me, it (vlc) will work.

once you get the "tv remote", you wont even have to open vlc. it has a button- "start tv".

if you follow my instructions, i guarantee results.


Nice, I'm just hoping that my previous instructions don't interfere with yours.

Also since you seem to be a dedicated user with a lot of experience under your belt 
I was wondering if you could take a look at my post. It might be a problem with MythTV I don't know.
[http://ubuntuforums.org/showthread.php?t=749893](http://ubuntuforums.org/showthread.php?t=749893)

---

### Post by spikedupback529 on 2008-04-10
Thanks so much everyone for the help!!!

I can finally abandon windows forever :).


Thanks for everything,
Dale

---

### Post by Jiffyman on 2008-04-11
Just out of curiosity did you use VLC or TVtime? 
Since the problem is fixed  can you mark the thread as solved to let people know. 
You can do this by clicking Thread Tools > Mark this thread a solved.

---

### Post by spikedupback529 on 2008-04-11
I used VLC. Actually, compared to Windows Media Center for XP, this runs so much faster. I´m running Opera, VLC, and Open Office all at the same time with no lag in VLC or any of the effects. Also, with WMC, the audio and video wouldn´t be synced up. I am so amazed with Ubuntu and the Linux platform. I couldn´t ask for a better OS or a better forum. Thank you everyone!!

Dale

---

