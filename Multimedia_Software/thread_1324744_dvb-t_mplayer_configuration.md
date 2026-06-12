---
title: "dvb-t mplayer configuration"
date: 2009-11-12
forum: Multimedia Software
---

### Post by pedja_portugalac on 2009-11-12
[img]http://www.olcso-alkatresz.hu/kepek/pinnacle/pinnacle_pctv_nano_stick_dvb_minus_t_73e_4.jpg[/img]

Hi everybody 

I just solved my problem watching TV over dvb-t usb stick and mplayer and I would like to share this how-to with you.

My USB DVB receiver is an Pinnacle PCTV 73e nano and is detected out of the box in Karmic. To watch TV over it I use svn-mplayer compiled while the stick was hooked in my laptop. To compile svn-mplayer I used andrew.46 how-to from here: [http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)
It is no GUI version of mplayer. It run exclusively from terminal (command line).

If you have finished compiling and installing svn-mplayer and all other things from haw-to above it's time to start configuring mplayer. Remember, USB DVB receiver must be connected to the computer while compiling!!!

You should install program w_scan witch is inside synaptic repository and you can find it searching for "dvb" there, it'll be at the and of the list. I don't know why I couldn't find it using apt-get?

Ones installed you'll use it to scan and create channels.conf file witch mplayer use to play TV. I was trying various types of .conf file but the one xine use is the one mplayer is able to read. I have also disabled radio stations in my .conf file, please read man w_scan for more information about scan options.

Now, open terminal and start scanning and creating .conf file like this, change "BE" with prefix for your country, DE = Germany, FR = France etc.
```
w_scan -ft -c BE -X -R N -O N >> channels.conf
```

Wait till it ends creating .conf file and than type
```
$ sudo mkdir /etc/mplayer
$ sudo cp channels.conf /etc/mplayer/
```
You are ready to watch your TV now and for that just type
```
$ mplayer dvb://
```
You can switch between channels using "k" and "h" on your keyboard. For more information about mplayer commands please read man mplayer and enjoy this wonder of media player.

Discussions about more complex commands etc are welcome

---

### Post by andrew.46 on 2009-11-12
Hi pedja,

> **pedja_portugalac said:**
> 

Now, open terminal and start scanning and creating .conf file like this, change "BE" with prefix for your country, DE = Germany, FR = France etc.
```
w_scan -ft -c BE -X -R N -O N >> channels.conf
```

Wait till it ends creating .conf file and than type
```
$ sudo mkdir /etc/mplayer
$ sudo cp channels.conf /etc/mplayer/
```

Great guide :). Perhaps you could create the channels.conf file as ~/.mplayer/channels.conf rather than placing it in the equally correct /etc/mplayer/channels.conf? This would perhaps simply make editing a little easier but would also cluster all of the user-defined configuration files in one place. Mind you if you were confident in the process you could always run:

```
w_scan -ft -c BE -X -R N -O N >> **[COLOR="Red"]~/.mplayer/[/COLOR]**channels.conf
```

and thus eliminate a few steps.

Andrew

---

### Post by pedja_portugalac on 2009-11-13
Hi Andrew

The idea is OK but when I tried first set up mplayer point me to that directory. Also, I like to save channels.conf in my home directory as a backup. When I want to capture (dump) stream from one channel I edit /etc/mplayer/channels.conf leaving just desired channel, that way mplayer have no choice but saving that channel. I say this because I don't know haw to tell mplayer to save desired channel from the full list. It'll always save the first channel on the list in channels.conf. And if I say mplayer dvb://channel_name it will return unknown channel.

After I have captured stream.dump file I convert it using svn version of ffmpeg with, for example, this command:
```
ffmpeg -i stream.dump -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -threads 0 output_hq.mp4
``` 
Then I can save it for my collection and of course share it on the net :D

Thanks for the suggestion and please come back if you find anything about this subject. ;)

---

### Post by andrew.46 on 2009-11-13
Hi pedja,

> **pedja_portugalac said:**
> Thanks for the suggestion and please come back if you find anything about this subject. ;)

Well it sounds as if you are a long way ahead of me on this one :). The only thing that I can offer is the html documentation which perhaps you have already read:

[http://www.mplayerhq.hu/DOCS/HTML/en/mpeg_decoders.html](http://www.mplayerhq.hu/DOCS/HTML/en/mpeg_decoders.html)

which has a section called 'Digital TV (DVB input module). You can use your DVB card for watching Digital TV.' that might be of use to you in particular the small section that speaks of selecting individual channels. My apologies if you have already read this :). You have certainly made me a little interested in this technology, it looks absolutely fascinating!

Andrew

---

### Post by pedja_portugalac on 2009-11-13
> **andrew.46 said:**
> Hi pedja,
Well it sounds as if you are a long way ahead of me on this one :). 
It sounds very nice coming from you. :) I am sure if you had one of this devices you already have made better and more complete how-to. :) It's strange that on MPlayer-DVB mailing list there's not much about this subject. Doesn't matter, we have now one tuto that works 100%. :)   
> You have certainly made me a little interested in this technology, it looks absolutely fascinating!
It's very nice little device I bring with me everywhere. I have 18.4 HD and 5.1 surround capable laptop and it's lot of time better then some small analog european hotels TV, specially when we can catch some HD channels. Here in Europe HD channels or shows are not available everywhere nor all the time.

Cheers

---

