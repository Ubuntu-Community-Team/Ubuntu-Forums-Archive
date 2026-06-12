---
title: "vlc ha ha ha"
date: 2015-10-18
forum: Multimedia Software
---

### Post by briar rabbit on 2015-10-18
Well, may be the joke is on me.

I went to trusty*(sic) 14.04 for the SOLE purpose of having vlc to convert files.

It appears as though whatever OS version you have has a vlc on it and that vlc version on that OS version is what you are stuck with until ... the end of time.

So I have 14.04 and I have the vlc that comes with it.

IT DON'T WORK.

I get the "VLC is unable to open the MRL" error.

I found this >Apparently i installed the wrong packages. I installed vlc-nox instead of vlc. It worked after i did apt-get install vlc.< @ [http://ubuntuforums.org/showthread.php?t=2249293](http://ubuntuforums.org/showthread.php?t=2249293)

So, I removed vlc, then reinstalled vlc, and none of the things inside 14.04 ask me if I wanted or not wanted options on "vlc-nox".

vlc STILL DOES NOT WORK. -SAME PROBLEM. 

I reckon I would much rather see the LTS's come out every 6 months.

Is there a tutorial for the 2.1.6 vlc and how in the heck it is supposed to work for converting files - this week?

Are there any vlc MASTERS out there that can perform vlc algorithms or what-ever so this thing can do what it says it can do?

Video will play in the vlc but I need more than that.

---

### Post by deadflowr on 2015-10-18
Moved to Multimedia Software


It's unclear what type of file, or where the file is located, you are trying to convert that gives you the mrl error.

But converting files with vlc is simple easy.
Simply open the menu and go to convert/save. 
Then in the next window add your file and when all files are added, press the convert/save button at the bottom.
Then select and confirm the profile settings by either selecting one of the many pre-configured or create a new one all your own.
Then last but not least, give the new file a name and location.
Then press start to begin the conversion.
And wait for it to convert.

---

### Post by briar rabbit on 2015-10-18
Hi thanks,

I don't have a "Menu" button.

I have a left click on the "play" button which gives me "Open Media".

In my videos I find "Lizards Song", I click open with vlc. 
Then  left click the play button (after stopping the play) and then >  "Open Capture Device" > which gives me "Open Media" at the top is  "File" "Disc" "Network" "Capture Device".  In "Capture Device" at the  bottom is "Play" and a drop down which gives me "Enqueue" "Play"  "Stream" "Convert" clicking "Convert" gives me the "Convert" page which  has "Source" and "Setting". 

On "Setting" I click "Audio - MP3".
"Source" has v4l2://" and will NOT let me enter anything else!
For "Destination" I click "Browse" and name a file in my "Music" Folder/.
Next  is "Start" which yields > "Your input can't be opened: VLC is unable  to open the MRL 'v4l2://'. Check the log for details."

???

---

### Post by mc4man on 2015-10-18
Likely this thread is more a rabbit hole than about a rabbit's misadventures. It would suffice to say that everything you did in post 3 is wrong, start to finish.

1. By default in Ubuntu vlc's menus are in the top panel, when you open vlc you'll see them for about 3 sec.'s, then they disappear. Just move your cursor to that area to reacquire. 
2. To convert a file in vlc (why anyone would use vlc is questionable), you don't open the file first in vlc. Rather  - 

Open vlc, click on Media menu > Convert/Save > Add > browse to & pick the file.
After adding a file then click on the Convert/Save button > pick the Profile desired. If need be after picking a profile you can edit it's parameters by clicking the little tools icon to immediate right of the Profile drop down.
Then either just name the converted file in the Destination box, will be saved to home folder. Make sure to add the proper extension or surprise, surprise.
 Or give it a path/to/name.extension  to save somewhere specific. After entering something in the Destination box the Start button will become active, click on, & ....

---

### Post by Bucky Ball on 2015-10-18
Why not use something that is specifically designed for converting files? 

```
sudo apt-get install soundconverter
```

... rather than using an ill-fitting tool then complaining it doesn't work and LTS releases should come out every six months (simply change to the interim releases which come out every nine months and you need to upgrade every six to achieve that). 

Good luck. :)

---

### Post by TheFu on 2015-10-19
I've never gotten VLC to transcode a file. Don't know why, just never worked for me either. There are 20+ other tools that do it already and do it well. avconv, ffmpeg, mencoder, handbrake, ... 

```
avconv -i "path-to-input-file.flv" "path-to-output-file.some-other-extension"
```

An exact example:
```
avconv -i "/tmp/funny-video.mp4" "/tmp/funny-video.mp3"
```

It will figure out how you want it converted based solely on the target.extension. If that isn't sufficient, there are options - many, multiple, complex, do-anything, options.  So ... if you need more help, kindly explain the source file and the desired target file format and codecs for video and audio, we maybe could help. Perhaps. Please.

BTW, almost all transcoding tools out there are actually based on the ffmpeg code for transcoding. Handbrake was. Avconv was and I think VLC was too. There is a PPA for the current ffmpeg to be installed, if that is your desire. I only use it for transcodes that are NOT h.264 - for those, handbrake is really good and easy AND faster than ffmpeg for similar quality and resolutions.  IMHO.

As to LTS ... I don't want them more than every 2 years. Actually, every 3 years would be better for me and my business. Changing an OS every 6 months? That's just crazy talk inside a business and highly risky.  We need to be making money, not swapping an OS all the time.

BTW, vlc does run on pretty much every desktop platform. You have choices. Windows, Mac, Linux ...  I'm positive that the VLC team would be happy to look over your code changes to include any missing features or bug fixes in future releases. Don't forget, these people are all volunteers.  So are most of us here - volunteers. 

The VLC source code is here: [https://github.com/videolan/vlc](https://github.com/videolan/vlc)  Instructions to providing patches are here: [https://wiki.videolan.org/Sending_Patches_VLC/](https://wiki.videolan.org/Sending_Patches_VLC/) - lots of folks are providing patches. It is a vibrant project.

---

### Post by briar rabbit on 2015-10-19
IT WORKS - It Works - it works 
 
mc4man OK well this is ah that was ah well ... 
OK my life is jumping from one rabbit hole right into another 
You know what they say; careful what you wish for 
Ever wish for answers to the greatest mysteries - 
   me neither.  I'm too busy jumping hole to hole, or some - thing like that..... 
 
My vlc came to life for the very first time and every subsequent time in ME-demize size, not mini-mized and not maxi-mized size but the third one - yeah. 
 
When vlc comes to life in this ME-demized size the info in the top panel never shows - though I am glad to drink myself into admitting computer dunceness - as many times as I opened and closed vlc I would have seen the top panel peek and hide, had it been doing so.  As odd as this may sound to some I really must insist - I HAD NO REASON TO PUT MY POINTY POINTER IN THE TOP PANEL :-). That said, I offer the aforementioned as a partial defense, as for anything remaining ... I plead ignorance of any code I am unaware of. 
 
Your time, in pointing out this ever so important and overlooked part of my operations in obtaining the necessary steps to acquire a working file converter in the vlc application which I had been desperately attempting to achieve on my own to absolutely no known working avail, is appreciated.  And I would just like to add in no uncertain terms, thank you. 
 
Mr. "Bucky Ball" 
 
Your astute observation that I should use a better suited program, known as "soundconverter" for the desired results are accepted - thank you. 
 
"TheFu" 
 
Yet another fine contributor of my publicized dilemma. 
It is comforting to learn I am not alone in my trials with "vlc" (and or computers in general). 
I have tried 'some' of those "20+ other tools" before and found "results may vary depending on operator, Operating System, version and I suppose vision too". 
I will attempt to endeavor upon this path after I have given "soundconverter" a chance to satiate my wants, desires and what ever task I may undertake at the time I am undertaking them. 
 
Cheers to all, thank you each and every one. 
Have a very scary Halloween and all that stuff. 
 
In closing this SOLVED issue of peek and go hide AND never seen panel "Menus", I would like to pose a question. 
 
If it takes 4 years to redo and create an OS: how long SHOULD it take a non-techie (or rabbit in this case) to figure the whole (or hole) new OS thing out? 
 
All over the internet there are forums of people who enjoy one particular thing or another and like to share their knowledge of the thing with other  people ... some ... just like me.  :-)  you turn my parenthesis around  :)~

---

