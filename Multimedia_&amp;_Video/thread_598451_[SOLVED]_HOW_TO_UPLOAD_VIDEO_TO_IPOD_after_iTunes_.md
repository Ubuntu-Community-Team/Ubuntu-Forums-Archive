---
title: "[SOLVED] HOW TO UPLOAD VIDEO TO IPOD after iTunes update"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by philidox on 2007-10-31
I had no issues uploading music or video with my ipod when i first purchased it.  I wanted to compare it to windows so I did.  iTunes got a hold of it and now i'm all missed up.  I have not be able to upload video to my iTunes updated ipod since.  I've tried it all gtkpod, amarok, thinliquildfilm, etc.  Every since gutsy came I still have the same problem.  When i tried to use gtkpod after gutsy upgrade i get this error every time i try to add new videos to my libraby.  

Import of '/media/sda5/ipod/music.video/Akon - Dont Matter.mp4' failed: m4a/m4p/m4b not supported without the mp4v2 library. You must compile the gtkpod source together with the mp4v2 library.
The following track could not be processed (filetype is known but analysis failed): '/media/sda5/ipod/music.video/Akon - Dont Matter.mp4'

I think gtkpod can do it but I gotta get pass adding mp4 media to my library.  Someone help me resolve this issue

thinliquidfilm works now.  After I renable my old repositories.  The upgrade from fiesty to gutsy autodisable my extra repositories

---

### Post by jacobo.merced on 2007-11-01
Am having the same problem after upgrading to Gusty. Now i get that same error when i try to copy video to my fifth gen Ipod.

---

### Post by philidox on 2007-11-01
Use thinliquildfilm its the bomb!  However it is ONLY a converter and video uploader.  So you'll have to use some other type of ipod manager to remove the video from your ipod.  Rhythmbox will remove any video that was use to upload by thinliquidfilm.

Here are all the urls short and simple in order to get thinliquidfilm working perfectly.  I spent hours trying to get it to work but here ya go any questions post here or call me on skype. skype name: philidox skype number: 5806094614

1.[http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/](http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/)
2.[http://liquidweather.net/howto/index.php?id=59](http://liquidweather.net/howto/index.php?id=59)
3.[http://thinliquidfilm.org/downloads.php](http://thinliquidfilm.org/downloads.php)
4.[http://liquidweather.net/howto/index.php?id=96](http://liquidweather.net/howto/index.php?id=96)

Go to this url's and follow the steps in that order and you should be fine

---

### Post by kostkon on 2007-11-01
> **philidox said:**
> I had no issues uploading music or video with my ipod when i first purchased it.  I wanted to compare it to windows so I did.  iTunes got a hold of it and now i'm all missed up.  I have not be able to upload video to my iTunes updated ipod since.  I've tried it all gtkpod, amarok, thinliquildfilm, etc.  Every since gutsy came I still have the same problem.  When i tried to use gtkpod after gutsy upgrade i get this error every time i try to add new videos to my libraby.  

Import of '/media/sda5/ipod/music.video/Akon - Dont Matter.mp4' failed: m4a/m4p/m4b not supported without the mp4v2 library. You must compile the gtkpod source together with the mp4v2 library.
The following track could not be processed (filetype is known but analysis failed): '/media/sda5/ipod/music.video/Akon - Dont Matter.mp4'

I think gtkpod can do it but I gotta get pass adding mp4 media to my library.  Someone help me resolve this issue

thinliquidfilm works now.  After I renable my old repositories.  The upgrade from fiesty to gutsy autodisable my extra repositories

You have to install *gtkpod-aac* (not *gtkpod*) in order to be able to upload *MPEG4* videos and *aac* music files to *iPod*. But, there is also another program you can try. It's called *Floola* and is a very good *iPod* manager. Its only downside is that it is not open source.

In case you decide you want to try it, you can get a binary from [its site]("http://www.floola.com/"). There is not, at least until now, a package for *Floola* to download from [*getdeb.net*]("http://getdeb.net/") and use in *Gutsy*. There is only a package for *Feisty*. Using the binary will suffice, anyway.

---

### Post by blurryone on 2007-11-28
Hmm... hey guys, have been trying to get this sorted for a couple days now.. i have gtkpod-aac and i still can not upload vids.. this is a clean install of gutsy

any help would be appreciated!!! :confused::confused:

---

### Post by airtonix on 2007-12-05
I too am not having fun uploading vids to the pod.

I can get them encoded. in various ways, they play on the pc..but not on the ipod.

I've tried to use gtkpod, gtkpod-aac, thinliquidfilm, none of which worked

Right now I am trying out floola.

Will return with more info

Edit: Worked nicely for me. 

1. download from here : [http://www.floola.com/modules/wiwimod/index.php?page=download_linux](http://www.floola.com/modules/wiwimod/index.php?page=download_linux)
2. Extract from archive.
3. run binary prog within new folder.

 + I dragged an xvid onto the target for adding a file. 
 + it told me it need converting, which I allowed.
 + Then it copied the converted movie to the ipod.
 + I unmounted the ipod, and play the video.

---

### Post by philidox on 2007-12-07
> **airtonix said:**
> I too am not having fun uploading vids to the pod.

I can get them encoded. in various ways, they play on the pc..but not on the ipod.

I've tried to use gtkpod, gtkpod-aac, thinliquidfilm, none of which worked

Right now I am trying out floola.

Will return with more info

Edit: Worked nicely for me. 

1. download from here : [http://www.floola.com/modules/wiwimod/index.php?page=download_linux](http://www.floola.com/modules/wiwimod/index.php?page=download_linux)
2. Extract from archive.
3. run binary prog within new folder.

 + I dragged an xvid onto the target for adding a file. 
 + it told me it need converting, which I allowed.
 + Then it copied the converted movie to the ipod.
 + I unmounted the ipod, and play the video.

I followed your instruction but I cannot add the xvid video files!  I can add all the mp3's I want but when I drag and drop ANY video it just sits there.  Any help would be  a big help

---

### Post by blurryone on 2007-12-11
philidox.. i think the issue is with the conversion... have you converted your vid to mp4? if not, do you have the same conversion tools as artonix? (he did not specify)

anywho.. still have this prob myself.. Artonix... what were you using to encode the vids?

Cheers
Blurry

:popcorn:

---

### Post by blurryone on 2007-12-12
bump :-S

---

### Post by philidox on 2007-12-12
> **blurryone said:**
> philidox.. i think the issue is with the conversion... have you converted your vid to mp4? if not, do you have the same conversion tools as artonix? (he did not specify)

anywho.. still have this prob myself.. Artonix... what were you using to encode the vids?

Cheers
Blurry

:popcorn:

I got ya man,  I got floola working PERFECTLY! Its all in the setup!  It will not only upload your video but convert and upload simultaneously.  Here is the text instructions to get your fix!

1. Start up floola(like you normally would) and go to "Tools">>>"Advance">>>"Uninstall Floola".
note: this will remove the bad install of floola

2. Start up floola again. This time it ask me to selected the type of ipod. I choose "IPOD VIDEO". Thats its

Now I went to "Add" and drag and dropped a video file and blam! I now have videos on my ipod thru floola.

If that was not good enough here is the youtube video, it should explain everything

[http://www.youtube.com/watch?v=iDMU7eHF4Ew](http://www.youtube.com/watch?v=iDMU7eHF4Ew)

---

### Post by redDEADresolve on 2007-12-13
gusty gtkpod-aac is broken. There is nothing wrong with your setup, settings or ipod; it just Ubuntu let gtkpod-aac ship with a huge bug.

gtkpod-aac from the repos will not let you upload video

---

### Post by OmegaBLK on 2007-12-13
If anyone is interested on the progress of the bug that is preventing gtkpod-aac from uploading aac/mp4/m4a files to your ipod check out this [bug report thread](https://bugs.launchpad.net/ubuntu/+source/gtkpod-aac/+bug/163283).  Patches have been applied and hopefully the fixed packages will be uploaded to the repo soon.

---

### Post by blurryone on 2007-12-13
fantastic work guys! appreciate all the help.. i think we can safely put this one to solved...

:guitar:

---

### Post by philidox on 2007-12-14
> **blurryone said:**
> fantastic work guys! appreciate all the help.. i think we can safely put this one to solved...

:guitar:

how do you do that blurryone?  I've always wondered that

---

### Post by philidox on 2007-12-14
> **OmegaBLK said:**
> If anyone is interested on the progress of the bug that is preventing gtkpod-aac from uploading aac/mp4/m4a files to your ipod check out this [bug report thread](https://bugs.launchpad.net/ubuntu/+source/gtkpod-aac/+bug/163283).  Patches have been applied and hopefully the fixed packages will be uploaded to the repo soon.

I'm using floola now so gtkpod is not an issue but I did do an update on my system and gtkpod aac is working great but like i said floola is fantastic.

---

### Post by philidox on 2007-12-14
> **philidox said:**
> how do you do that blurryone?  I've always wondered that

never mind figured it out

---

### Post by blurryone on 2007-12-14
heh no worries pretty straight forward once you realize how :)

---

