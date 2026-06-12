---
title: "Windows Media Player 11 plug-in for Firefox?!?"
date: 2009-06-06
forum: Multimedia Software
---

### Post by extigyro on 2009-06-06
Neither mplayer-plugin, nor gecko media player plugin, nor totem plug-in (even the latest 2.27), nor VLC (0.9.9) plug-in... neither of these plug-ins and stand-alone players can handle windows media player 11 video streaming.

Is there any workaround? I digged a lot of threads in ubuntu forum and linuxquestions.org but there still is no actual fix.

Try this (it's the HP original clip about disassembling nx9420 laptop and installing new ram memory module):

[http://vsslfpro.zcce.compaq.com/plmcontent/NACSC/SML/results.htm?SID=1839153&MEID=959CCC73-B4BF-4DD8-A38B-BEAAE32C3088](http://vsslfpro.zcce.compaq.com/plmcontent/NACSC/SML/results.htm?SID=1839153&MEID=959CCC73-B4BF-4DD8-A38B-BEAAE32C3088) and then click on "Expansion memory board" or any other of these video guides.

---

### Post by extigyro on 2009-06-07
Today I also tried the latest helix plug-in but with no success so far.

Any suggestions? :)

---

### Post by extigyro on 2009-06-09
It appears that there is no means of playing windows media player 11 video streaming in Firefox or any other Internet browser in Linux...

---

### Post by extigyro on 2009-06-22
I just want to share some new stuff about the Media Player 11 Video Streaming incapability under Linux.

> 
Quote:
Originally Posted by Knurpht View Post
@oldcpu: I can't watch it. Nor in Opera nor in Firefox. Running Factory, so I only blame myself.
What did you mean by "it was not straight forward"? Did you do something to watch it? If so, wanna tell us what you did?
As noted, its not straight forward. Its not point and click. Blame HP for that. Not Linux.


> 
I had to determine the URL of the video, change the extension from asx to wmv, and then download it to my openSUSE hard drive, and watch it off my hard drive once downloaded. The standard stuff that I do when such sites mess around with their streaming methodology. This is typically quick and easy for me most of the time (but not always). They have also done something bizarre with the audio that I have not sorted yet.


The last quotation was originally posted by **oldcpu in openSUSE Forums (he is one of the Global Moderators of openSUSE Forums)**.

---

### Post by starcraft.man on 2009-06-22
I was about to recommend mediaplayerconnectivity for firefox addon but it only redirects streams to specified apps and as you indicated, you noted VLC can't play asx streams. So I have two solutions for you.

1. Adding restricted windows codecs 
or
2. The download method you described, I just tried it and works.

1. 
a. Add Medibuntu repos to your software sources. To do this, I assume your using jaunty. Go Applications Accessories > Terminal. Then copy and paste following code to enter.

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

b. In the same terminal:
```
sudo apt-get update 
```
followed by
```
sudo apt-get install w32codecs
```
or
```
sudo apt-get install w64codecs
```

NOTE! There are two different packages, one for 64 bit linux and one for 32, pick the one you installed. At download, it would have been i386 for 32, if you didn't download that package your 64.

c. Pipe video to totem however you like, should work. The aforementioned firefox addon can do this easy.

2. As you noted, videos can be downloaded and watched. To get the link, navigate through the left links to the video, then right click on the video (recommend installing mediaplayerconnect first, good add on) then choose send link. This will start your email program, in the body you'll see the link, scroll right until you see http: etc,,,, select the entire link and copy it.

Now open a terminal as described above. We're gonna use wget (a downloading command) to get these videos. Basically the code to download the video is the following:

```
wget link.**wmv**
```

NOTE! As described, you need to change the terminal extension of the link to wmv.

Example code:

```
wget http://vsslfpro.zcce.compaq.com/plmcontent/NACSC/SML/Media/959CCC73-B4BF-4DD8-A38B-BEAAE32C3088/af3_battery.**wmv**
```

There is probably a more efficient means of getting links and download, but this should be good enough.

---

### Post by extigyro on 2009-06-24
I've tried your first method (with a Linux Mint Gloria LiveCD) because i'm using openSUSE 11.1 with KDE3 right now and the results are (of course, i already tried this method in the past):

No success; look at the snapshots.

---

### Post by kilgore9 on 2009-06-24
I'm also trying to view media on a site which doesn't work.  It says I need the Flashplayer plugin, which I have, and its the current version.  A friend told me that the site is using encrypted wmv files.  There is no ".wmv" link to use, its a player that pops up on the site.  

I have all the plugins and stuff for firefox, running on Jaunty.

Any other way to get these videos working??

---

### Post by extigyro on 2009-06-26
Tested also:
Xine browser plug-in.

Results:
No success again.

---

### Post by mc4man on 2009-06-26
You can download and then play in player of your choice.

I'm not sure how starcraft.man got the address (the send link doesn't work as described), but no matter, there is only 1 address, just the filename changes.

You can find the file name in ~/.mozilla/firefox/xxxxxxxx.default/Cache or just infer it, all seem to be done the same, just use the posted wget command and change the ending
/af3_battery.wmv
/af3_ledswitchcover.wmv
/af3_opticaldrive.wmv

ect,ect.


In other words /af3_<the video name without spaces or caps>.wmv

Ex.

 [PHP]wget http://vsslfpro.zcce.compaq.com/plmcontent/NACSC/SML/Media/959CCC73-B4BF-4DD8-A38B-BEAAE32C3088/af3_ledswitchcover.wmv
[/PHP]

 [PHP]wget http://vsslfpro.zcce.compaq.com/plmcontent/NACSC/SML/Media/959CCC73-B4BF-4DD8-A38B-BEAAE32C3088/af3_opticaldrive.wmv
[/PHP]

 [PHP]wget http://vsslfpro.zcce.compaq.com/plmcontent/NACSC/SML/Media/959CCC73-B4BF-4DD8-A38B-BEAAE32C3088/af3_harddiskdrive.wmv[/PHP]

---

### Post by extigyro on 2009-07-04
> **mc4man said:**
> 

In other words /af3_<the video name without spaces or caps>.wmv

Ex.

 [PHP]wget http://vsslfpro.zcce.compaq.com/plmcontent/NACSC/SML/**_Media_**/959CCC73-B4BF-4DD8-A38B-BEAAE32C3088/af3_ledswitchcover.wmv
[/PHP]


10x, but how did you know that it's not 
"http://vsslfpro.zcce.compaq.com/plmcontent/NACSC/SML/results.htm?SID=1839153&MEID=959CCC73-B4BF-4DD8-A38B-BEAAE32C3088/af3_expansionmemoryboard.wmv"
 
but 

"http://vsslfpro.zcce.compaq.com/plmcontent/NACSC/SML/**_Media_**/959CCC73-B4BF-4DD8-A38B-BEAAE32C3088/af3_expansionmemoryboard.wmv", for example?

---

