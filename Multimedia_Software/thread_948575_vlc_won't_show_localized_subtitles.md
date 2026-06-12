---
title: "vlc won't show localized subtitles"
date: 2008-10-15
forum: Multimedia Software
---

### Post by se_landy on 2008-10-15
Hi, I have a problem with vlc. When i play a movie and put a croatian subtitles, those lines with croatian letters in them, never show up... can I do anything to make those lines visible?

P.S. Is there any movie player for ubuntu that allows to adjust subtitles (speed, size) ?? If the answer is yes, could you PLEASE give me a link to install it?? I'm desperate ](*,)

---

### Post by cariboo on 2008-10-15
Have you install croation language support? Go to System-->Administration-->Language Support, and add it there.

Jim

---

### Post by lovinglinux on 2008-10-15
VLC can play almost everything, but I prefer the simplicity of gnome-mplayer. It is in the repositories, but the deb version provided in the link below works better, specially in regard to subtitle languages with special characters like ours (mine is Portuguese).

Download version 0.8 from [http://www.getdeb.net/app/GNOME+MPlayer](http://www.getdeb.net/app/GNOME+MPlayer)

After installation open it and hit CTRL+P to bring the properties configuration. In the subtitle tab enable Substation Alpha support, choose the Font, Color, Scaling and Encoding. I guess the encoding for Croatian is iso-8859-2.

Subtitle sync can be changed on the fly using "Y" and "G" keys. For subtitle position use "R" and "T". Audio sync can be controlled using "+" and "-" keys.

Additionally, you could edit ~/.mplayer/config to add extra configurations. Check "man mplayer" for options.

This is my config 
```

[default]

alang=English,eng,en
slang=Portuguese,por,pt
ao=pulse
vo=x11
zoom=1
vf=eq2
double="yes" #double buffering(recommended for subtitles)


#SSA subtitle rendering
# *** = a s s   without spaces (the forum thinks I'm using bad word)

***="yes"
embeddedfonts="yes"
***-color="FFFF0000"

#Freetype subtitle rendering

font=/usr/share/fonts/truetype/msttcorefonts/arial.ttf 
subfont-text-scale="5"
subfont-outline="3"

[gnome-mplayer]
alang=English,eng,en
slang=Portuguese,por,pt
ao=pulse
vo=x11
zoom=1
vf=eq2
double="yes" #double buffering(recommended for subtitles)


#SSA subtitle rendering
# *** = a s s   without spaces (the forum thinks I'm using bad word)

***="yes"
embeddedfonts="yes"
***-color="FFFF0000"

#Freetype subtitle rendering

font=/usr/share/fonts/truetype/msttcorefonts/arial.ttf 
subfont-autoscale=1
subfont-text-scale="7"
subfont-encoding="ISO-8859-1"
subfont-outline="3"
msglevel=all=5
```

---

### Post by se_landy on 2008-10-15
I installed language support - didn't help!
Also, installed mplayer, and did the adjustments. when i start a video, i only hear sound, there is no picture... :S

My basic problem is that I'm looking for a video player that can play video normally, and have ability to adjust subtitles (speed, size...). And to be able to show croatian (localized) letters in subtitles... 
I spent two weeks trying to find something like that for ubuntu, and still didn't find it. Something like bsplayer, or gom player for windows...

Is there any hope that I will find something??? :confused:

---

### Post by lovinglinux on 2008-10-15
> **se_landy said:**
> I installed language support - didn't help!
Also, installed mplayer, and did the adjustments. when i start a video, i only hear sound, there is no picture... :S

The video problem with mplayer is just a codec issue. Install Gstreamer plugins. You can use Add/Remove manager. I'm not sure, but you might need to add medibuntu repository to software sources before installing the codecs.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

After installing the plugins, the video should work with gnome-mplayer. You will probably like it, but if you want a more advanced frontend you could also use smplayer. It is in the repos too.

> **se_landy said:**
> My basic problem is that I'm looking for a video player that can play video normally, and have ability to adjust subtitles (speed, size...). And to be able to show croatian (localized) letters in subtitles... 
I spent two weeks trying to find something like that for ubuntu, and still didn't find it. Something like bsplayer, or gom player for windows...

Is there any hope that I will find something??? :confused:

Gnome-mplayer can play almost anything with the proper codecs, it has an excellent subtitles support, including for your language, it has a simple but nice interface and has simple commands to adjust subtitles as mentioned before. So, you don't have to look anywhere else. Just install the codecs.

I was a Gom player user before Ubuntu and I'm very satisfied with gnome-mplayer.

You can also install the Firefox plugin with this command:

```
sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
```

```
sudo apt-get install gecko-mediaplayer
```

---

### Post by lovinglinux on 2008-10-15
I forgot to mention in my previous post that gnome-mplayer is a frontent to mplayer. So after install, make sure you launch the correct frontend using the following command:

```
gnome-mplayer
```

---

### Post by rvm4000 on 2008-10-16
I think mplayer/smplayer can display croatian characters without problems:

[[IMG]http://img366.imageshack.us/img366/1606/croata1pl7.th.jpg[/IMG]](http://img366.imageshack.us/my.php?image=croata1pl7.jpg)[[IMG]http://img366.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by juky on 2009-06-06
Hi,

under VLC player select Tools--Preferences--Subtitles&OSD. 

Under "Default encoding", select CP1250.


Cheers,
juky

---

### Post by Grove on 2009-10-31
> **juky said:**
> Hi,

under VLC player select Tools--Preferences--Subtitles&OSD. 

Under "Default encoding", select CP1250.


Cheers,
juky

thanks mate, i've been looking for some time after the encoding settings.

godspeed,
G

---

### Post by moon2js on 2010-02-10
I'm having the same problem with Karmic. Totem and VLC won't display Korean subtitles. I can type and view websites in Korean, but no matter what encoding I set Totem or VLC to use for subtitles, it still shows gibberish (although usually different kinds of gibberish with different encoding settings). There are two Korean character encodings in addition to the various UTF/Unicode encodings.

The subtitle files are SMIL and they work fine in GOM player in XP. But I have the same gibberish problem with VLC in XP.

In XP, Firefox can open the SMIL files and I can plainly see the subtitles fine. But for some reason, I can't open the SMIL file in FF in Ubuntu. (Whenever I try to open, it just asks me where I want to save it as if I were downloading it -- from my own /home/Downloads folder).

Any suggestions?

---

### Post by AlexisCC on 2010-02-14
moon2js and I share the same problem.  vlc, totem, gnome, and smplayers all display either gibberish or empty boxes instead of Korean subtitles.  I've been surfing for days looking for a resolution and the closest I could find was someone with an identical problem...  :(   

I will add that IBUS works great in all applications and when I open the .smi or .srt files in OpenOffice I see perfect Korean fonts, however when I open the files in Gedit, the same gibberish is displayed. (IBUS does allow me to input Korean characters in Gedit, but I can't see them displayed.)

Any help would be much welcomed.

---

### Post by taekr on 2010-06-02
I do have the same problem. 

I have tried everything I can think of but my players won't display Korean subtitles. It works very well with Windows though. 

I have Gomne-palyer, Smplayer, VLC player.. . installed every video players.. 

Any help?

---

### Post by kudzu on 2010-10-03
I hate to revive an old thread, but I have the exact same unresolved problem as taekr, AlexisCC and moon2js; no matter how I tinker with the fonts and codecs, Korean subtitles only show up as boxes.  The English subtitle files I use are .srt files and work fine, but all the Korean subtitle files I find are .smi files.  I wonder if that has something to do with it?

---

### Post by milan karmelic on 2012-12-23
it worked for me. 

ubuntu 12.04 lts

smplayer

i did ctrl+p in smplayer and under subtitles menu, subtitles tab i choose coding option for my language, which is croatian btw. 

there is also an option for automatic search and find of desired language which you choose from drop down menu.

hope i helped ,)

---

