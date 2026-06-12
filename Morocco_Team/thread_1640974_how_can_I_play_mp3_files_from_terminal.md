---
title: "how can I play mp3 files from terminal ??"
date: 2010-12-08
forum: Morocco Team
---

### Post by zazlox on 2010-12-08
is there any command line or a tip to play mp3 file from terminal.
?????
please

---

### Post by I'mGeorge on 2010-12-08
by installing the following terminal apps xmms2, sox or moc and I believe there are even more out there.

---

### Post by zazlox on 2010-12-08
xmms2, sox, moc

how can i use them .

when i type for example xmms on quick search on synaptic

i see a too many result that look similar

how can i know which one to install. and how to use it on terminal

i mean which command shall i type.

---

### Post by I'mGeorge on 2010-12-08
In your terminal just type 

```

sudo apt-get install xmms2

```

here's a tutorial for xmms2 [http://www.dannybuntu.com/2009/02/howto-play-mp3-on-terminal.html](http://www.dannybuntu.com/2009/02/howto-play-mp3-on-terminal.html) 

If you wanna try moc too, install it in the same manner, and just launch it by simply typing moc into your terminal after that, and an interface similar to midnight commander will pop out. For moc your terminal window has to be fullscreen or enough wide.

Sox it's primarely destined for audio files conversion  so you shouldn't install it if you just want something to play your audio files. But if you choose to install it in your terminal just do

```

man sox

``` 
and it will tell you everything that's to be known about it.

---

### Post by zazlox on 2010-12-08
I'MGeorge

.............

thanks for helping , i really appreciate that

i'll use just xmms. very useful :)

---

### Post by Sub101 on 2010-12-08
MPlayer also has a terminal option.

I have the following alias in my .bashrc

```
alias progmusic='mplayer -shuffle /$HOME/Music/Programming/*'
```

---

### Post by zazlox on 2010-12-08
sub101
..........

for the command line to play file

is it the same way as xmms2

mplayer play <the song's name>

or

just : mplayer < the song's name >

---

### Post by rx007 on 2010-12-08
hello try to install mpg321

i've been using that for years. :)

```

sudo apt-get install mpg321

``````

mpg321 mmusic.mp3

```

---

### Post by zazlox on 2010-12-08
> **rx007 said:**
> hello try to install mpg321

i've been using that for years. :)

```

sudo apt-get install mpg321

``````

mpg321 mmusic.mp3

```


thanks for that.  well , we got too many options for playing audio files from terminal

Great.  :)  I like using or doing most things from terminal that's why I asked this question.

now I'm happy , i can play audio files also from terminal  ;)

---

### Post by andrew.46 on 2010-12-09
Just to add some confusion there is also my personal favourite mpg123:

```

andrew@skamandros~/music/ftgws$ **[COLOR="Red"]mpg123 --long-tag --control Revelation_21.mp3 [/COLOR]**
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layers 1, 2 and 3
	version 1.12.4; written and copyright by Michael Hipp and others
	free software (LGPL/GPL) without any warranty but with best wishes


Terminal control enabled, press 'h' for listing of keys and functions.

Playing MPEG stream 1 of 1: Revelation_21.mp3 ...

	Title:   A New Heaven
	Artist:  Lesley Garrett
	Album:   Lesley Garrett - The Singer
	Year:    2005
	Genre:   Classical
	Comment: ABC Classic FM broadcast

MPEG 1.0 layer III, 192 kbit/s, 44100 Hz joint-stereo
        
[6:05] Decoding of Revelation_21.mp3 finished.

```

Andrew

---

### Post by bazita on 2011-11-11
&#1591;&#1576;&#1593;&#1575; &#1610;&#1605;&#1603;&#1606; &#1578;&#1588;&#1594;&#1610;&#1604; &#1605;&#1604;&#1601;&#1575;&#1578; &#1575;&#1604;&#1589;&#1608;&#1578;&#1610;&#1577; 
mp3 
&#1608;&#1581;&#1578;&#1610; &#1571;&#1610; &#1605;&#1604;&#1601; &#1589;&#1608;&#1578;&#1610; &#1571;&#1608; &#1601;&#1610;&#1583;&#1610;&#1608;
&#1571;&#1608;&#1604;&#1575; &#1610;&#1580;&#1576; &#1578;&#1578;&#1576;&#1610;&#1578; &#1576;&#1585;&#1606;&#1575;&#1605;&#1581;
VLC
&#1578;&#1605; &#1605;&#1606; 
terminal
&#1571;&#1603;&#1578;&#1576; 
vlc &#1571;&#1605;&#1585;
&#1605;&#1578;&#1576;&#1608;&#1593;&#1575; &#1576; &#1573;&#1587;&#1605; &#1575;&#1604;&#1605;&#1604;&#1601;

---

### Post by eazyigz on 2013-01-16
> **rx007 said:**
> hello try to install mpg321

i've been using that for years. :)

```

sudo apt-get install mpg321

``````

mpg321 mmusic.mp3

```

That is great advice, works perfectly!

---

