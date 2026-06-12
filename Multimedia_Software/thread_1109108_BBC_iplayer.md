---
title: "BBC iplayer"
date: 2009-03-28
forum: Multimedia Software
---

### Post by Majorflam on 2009-03-28
Hi,

I'm using the latest version of Ubuntu and Firefox. I have installed the BBC iplayer for Linux, but when I go to the iplayer website I can't get an option for downloading the programmes... it just wants to let me view in the browser window.

Can anyone help out?

TIA

---

### Post by Fenris_rising on 2009-03-28
Hi there

I think you'll find that that is normal behaviour for iplayer. Unless there is a piece of software such as is used to download youtube videos you will just have to watch the programs as is.

regards

Fenris

---

### Post by ajgreeny on 2009-03-28
You need to install Adobe Air before the BBC iPlayer will work on linux, so if you have not already done so, go to the [http://www.adobe.com/products/air/](http://www.adobe.com/products/air/) site and get it.  I hasten to add that I have not bothered yet so don't know how well it works and have to leave that to you.

---

### Post by Majorflam on 2009-03-28
Hi,

I already have adobe air installed. I know that I should be able to download bbc iplayer files, but I just don't know why the browser isn't recognising that I have the iplayer application installed.

---

### Post by kaivalagi on 2009-03-28
> **Majorflam said:**
> Hi,

I already have adobe air installed. I know that I should be able to download bbc iplayer files, but I just don't know why the browser isn't recognising that I have the iplayer application installed.

I think you might need to go to the bbc iplayer labs section and pick some alternative options, try here: [http://www.bbc.co.uk/iplayer/labs](http://www.bbc.co.uk/iplayer/labs)

I haven't tried using the download function yet, but in applying some settings in the labs section I have a bunch more options available including a download button (which wont work for me cause I haven't installed AIR yet)

Let us know how you get on!

Mind you, DRM on Linux gives me the shivers...you could just use "iplayer-dl" available [here]("http://po-ru.com/projects/iplayer-downloader/"), it mimics an iphone and downloads most content as a .mov file :) but maybe the quality will be better from the "appropriate" options

---

### Post by Majorflam on 2009-03-28
OK, good progress here. I've managed to get the files using the iplayer-dl but is there any way to get the files in mp4 format? It's downloading in mov format by default. Could I convert from mov to mp4?

TIA

---

### Post by kaivalagi on 2009-03-28
> **Majorflam said:**
> OK, good progress here. I've managed to get the files using the iplayer-dl but is there any way to get the files in mp4 format? It's downloading in mov format by default. Could I convert from mov to mp4?

TIA

Avidemux is a good gui based tool, you should be able to figure it out easily enough

It's in the repo's, so to install it's just:

```
sudo apt-get install avidemux
```

Did you try to download from the iplayer site with AIR installed? Just curious...

---

### Post by Majorflam on 2009-03-28
AIR didn't make a difference, it still wouldn't download.

I've tried converting using avidemux but 2 things happen when I convert to mp4.

1. When I open the file using Movie Player it doesn't play, it just jams on the first frame.

2. When I send to my mp4 player it doesn't recognise the file when I try to play back.

---

### Post by kaivalagi on 2009-03-29
> **Majorflam said:**
> AIR didn't make a difference, it still wouldn't download.

I've tried converting using avidemux but 2 things happen when I convert to mp4.

1. When I open the file using Movie Player it doesn't play, it just jams on the first frame.

2. When I send to my mp4 player it doesn't recognise the file when I try to play back.

Works for me...

I set the video to "MPEG-4 ASP (XVid4)" and audio to "MP3 (LAME)", and format as "AVI" i.e. put in a AVI container

I am assuming this will work for you too...

I am now trying the smae but with an MP4 container...this worked (not great) in VLC but not at all in totem.

---

### Post by Majorflam on 2009-03-29
Thanks for your help, I really do appreciate it. Unfortunately I can't get it working yet.

---

### Post by kaivalagi on 2009-03-29
> **Majorflam said:**
> Thanks for your help, I really do appreciate it. Unfortunately I can't get it working yet.

It might be worth searching through the forum for help on "mencoder" as no doubt someone else here has had to get around the same issues you are having at some point in the past

Avidemux should handle the conversions for you though, as all the options you'll ever need are there.

Can you not recode to an AVI container for your mp4 player, with xvid4 mpeg4 and lame mp3 options set? See the attached screenshot for what I mean

I'm sure you'll figure it out

---

### Post by andrew.46 on 2009-03-29
Hi Majorflam,

> **Majorflam said:**
> OK, good progress here. I've managed to get the files using the iplayer-dl but is there any way to get the files in mp4 format? It's downloading in mov format by default. Could I convert from mov to mp4?

FFmpeg can do this for you. If you are interested in trying this method for Intrepid (I assume you are using Intrepid?) you will need:

```
sudo apt-get install ffmpeg libavcodec-unstripped-51
```

And then identify the file with the following:

```
ffmpeg -i myfile.mov
```

If you post the output I am sure a suitable skilled person could also suggest the syntax for conversion. I notice that you mentioned an mp4 player. These devices usually have limitations in what they can play, are you aware of the specific formats this device will accept?


Andrew

---

### Post by Majorflam on 2009-03-30
Thanks for the info Guys. I'm away on business for a couple of weeks so I won't get to try any of this until I get home.

I'll let you know how it goes.

Thanks.

---

### Post by mike-g2 on 2009-06-07
Just to make sure, according to the BBC site you can only download programs if you are in the UK.

Mike

---

### Post by jadrevenge on 2009-11-11
To get the iPlayer working in the browser (Assuming you're in the UK) go to 'Preferences -> Appearance -> Visual Effects' and change the setting to "None" ...

Theres something not quite right in the Firefox/Flash/Javascript combo in Normal mode ...

I have a bug open with the Ubuntu team.

---

### Post by kaivalagi on 2009-11-11
> **jadrevenge said:**
> To get the iPlayer working in the browser (Assuming you're in the UK) go to 'Preferences -> Appearance -> Visual Effects' and change the setting to "None" ...

Theres something not quite right in the Firefox/Flash/Javascript combo in Normal mode ...

I have a bug open with the Ubuntu team.

It works in firefox 3.5 within gnome with compiz turned on for me...I'm am not using Ubuntu now though, Arch instead

---

### Post by jaycee23 on 2009-11-11
It was working in firefox fine until I just did my daily update. I noted there were multiple Firefox related updates. Now iplayer no longer works. 

Having said that it works fine in Opera. 

I had the same fault in Firefox previously but it was corrected at the last but one update!

Looks like they have reversed the fix for some reason!

It's no biggy but I don't really like Opera

#-o

---

