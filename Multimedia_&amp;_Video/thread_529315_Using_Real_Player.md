---
title: "Using Real Player"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by PmDematagoda on 2007-08-19
There seems to be a problem with real player such that it can't play almost anything, especially mp4s, does anyone have a solution to this? I installed real player using Automatix2.

---

### Post by wolfen69 on 2007-08-19
this wont solve your problem directly, but have you tried vlc player? it plays anything.

---

### Post by PmDematagoda on 2007-08-19
VLC player can be used for those, thanks:), but i still want to use Real Player, do you think it may be a problem with the codecs cause when i play even an mpeg file it asks me to update the player because it can't find mpeg. The same problem occurred when i used Helix.:(

---

### Post by RomeReactor on 2007-08-19
Hi. As far as I know, RealPlayer for Linux only plays real media formats (.rm, .rmvb). When trying to view other formats, it asks you to download additional codecs which aren't available for Linux. Try adding gstreamer or xine codecs for Totem, or use VLC or Mplayer.

---

### Post by PmDematagoda on 2007-08-19
Okay thanks RomeReactor though what you told me wasn't what i wanted to hear but thanks anyway.

---

### Post by RomeReactor on 2007-08-19
Can you please elaborate?

---

### Post by PmDematagoda on 2007-08-19
Well the thing is VLC doesn't play everything in high quality, so i thought of having Real player or Helix so that i can switch to it if i wanted to. Not exactly a sensible reason but thats the reason.

---

### Post by RomeReactor on 2007-08-19
Both Totem with the necessary codecs or Mplayer can play mp4 files very well; I don't notice any loss in quality, especially from Mplayer. Give them a try. Unfortunately, Real Player can only play .rm or .rmvb files.

---

### Post by PmDematagoda on 2007-08-19
How do i get the mp4 codecs for totem and Mplayer? I looked around the internet but couldn't find them.

---

### Post by RomeReactor on 2007-08-19
Get the w32codecs from [here]("http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20061022-0medibuntu1_i386.deb"). Once it finishes downloading, double-click on it to install. Then install the following packages:

 if you're using **totem-xine**
```
sudo apt-get install libxine1 libxine1-ffmpeg libxine-extracodecs
```


for **totem-gstreamer**
```
sudo apt-get install gstreamer0.10-fluendo-mp3 gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mpegdemux gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

The instructions are entered in the terminal (Applications->Accessories->Terminal). You could also search for the packages in Synaptic (System->Administration->Synaptic Package Manager).

---

### Post by PmDematagoda on 2007-08-19
Would the codecs of totem xine interfere with those of gstream? Beacause both of them were installed(The codecs).

---

### Post by RomeReactor on 2007-08-19
There's no problem having both sets installed; totem will use the ones associated with its backend (gstreamer or xine). In my opinion it's best to have them all installed.

---

### Post by Bablefish on 2007-08-19
First of all there is no subsitute for Real Player I used VLC and the Linux version just doesn't work that well, neither for Real player files nor quicktime. To get it is rather simple just enter this

 sudo apt-get install realplayer 

So far it is the only Linux program to do this but you won't be able to use it on such real player sites like the BBC straight off. You actually have to give it a day or 2 before you try any of those sites...after that it will work.

---

### Post by PmDematagoda on 2007-08-19
Can't Real Player even play mpeg's let alone mp4's?:(

---

