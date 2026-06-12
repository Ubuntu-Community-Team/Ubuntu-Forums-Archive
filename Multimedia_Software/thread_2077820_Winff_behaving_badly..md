---
title: "Winff behaving badly."
date: 2012-10-29
forum: Multimedia Software
---

### Post by Langstracht on 2012-10-29
I have a bunch of m4v files that I want to convert to .avi.

The only programme that I have found that seems to do that "successfully" is Winff.

BUT ... I end up with a badly pixellated file which, admittedly, is much smaller - perhaps 1/3rd of the size.

I'd be happy with a same size file with NO pixellation.

Anyone any ideas on how to improve this.  I'm thinking in terms of, given the specs of the m4v file, what options to choose in Winff.  The manual I have found is disappointingly lacking in such details.

Appreciate any help.

TIA

---

### Post by ron999 on 2012-10-29
> **Langstracht said:**
> 
The only programme that I have found that seems to do that "successfully" is Winff.

BUT ... I end up with a badly pixellated file which, admittedly, is much smaller - perhaps 1/3rd of the size.

Hi
WinFF is a gui for **FFmpeg**.
If you can decide a suitable FFmpeg command then it can be used to make your own preset for WinFF.

Try an FFmpeg command like this for starters:-
```
ffmpeg -i foo.m4v -vcodec mpeg4 -b 1500k -acodec libmp3lame -ab 128k -ar 44100 -ac 2 foo.avi
```


Tutorial is here:- [http://code.google.com/p/winff/wiki/HowToMakePresets]("http://code.google.com/p/winff/wiki/HowToMakePresets")
If the result is still pixelated, increase the video bitrate (-b) to 1800k or 2000k or whatever.

---

### Post by Langstracht on 2012-10-29
Ta very much.

I'll have a boo at the tutorial and then, presumably, monkey around with the command you so kindly provided to (try to) match the specs of my particular m4v files.

Thanks again.

---

### Post by FakeOutdoorsman on 2012-10-29
Why do you need AVI? There are probably better alternatives for your use case.

---

### Post by Langstracht on 2012-10-29
Well, o.k. You are probably right.

So, the story is ... I have a large number of split .m4v files that I want to concatenate.  The only successful concatenations I have made in endless hours of messing around have been with .avi files and avidemux.  Every other thing I tried resulted in audio that was totally out-of-sync.

So, if there is a foolproof way of concatenating .m4v files, please, bring it on ...

And, again, TIA

---

### Post by goldshirt9 on 2012-10-29
[LIST=1]**Use Zamzar**

[*] 									1 									 												Visit Zamzar. This is a website that converts various files online for free. 											
 									
[*] 									2 									 												Click "Browse" under "Step 1." Select the file you would like to convert and click "Open." 											
 									
[*] 									3 									 												In "Step 2" choose "AVI" from the drop-down menu. 											
 									
[*] 									4 									 												Enter your e-mail address in the box for "Step 3." 											
 									
[*] 									5 									 												Click "Convert" under Step 4. Your conversion will begin.  You can view your progress below. You can also navigate away from the  page and Zamzar will e-mail you once the process is finished. Once the  conversion is complete, click the link that Zamzar e-mails you to  download your file

[/LIST]
Downloadable software alternatives exist as well. Try: Tunebite, FFMpeg or AVC.


see 
[http://www.ehow.co.uk/how_5132529_convert-mv-avi-linux.html](http://www.ehow.co.uk/how_5132529_convert-mv-avi-linux.html)

---

### Post by evilsoup on 2012-10-30
If you want to losslessly convert from M4V to AVI, the correct ffmpeg command would be

```
ffmpeg -i input.m4v -acodec copy -vcodec copy output.avi
```

Depending on the video files, you may not be able to concatenate them together with cat. AVI and M4V/MP4 are 'container' formats, which the video and audio streams - sometimes different streams, e.g. for multiple languages - are contained within. Most old AVI files use MPEG2 video, which can be used with cat with no problems; but your M4V (and most modern AVIs) probably uses the objectively-superior (in terms of quality per kb) h.264 video; and AFAIK, that's not so great for concatenating with cat.

HOWEVER
Don't give up hope; there's a commandline tool that should be able to concatenate your M4V files without messing around with AVI: MP4Box

```
sudo apt-get install gpac
```

Then, to concatenate your M4V (assuming they're all the same aspect ratio, etc)

```
MP4Box -cat input1.m4v -cat input2.m4v -cat input3.m4v -new output.m4v
```

Note the capitalisation of MP4Box, if you use 'mp4box' it won't work.

Also, this only works if all the settings on the files are the same, so it may or may not work for you (if the files are originally from the same source, then it *probably* will work).

---

### Post by Langstracht on 2012-10-30
Alas and alack.

I had used (or tried to use) MP4Box before and, based on your suggestion, gave it another go.  With the same result.  It combined the two files just fine but, while I suppose all of the first file's audio is fine, the audio is WAY out of sync in the second half.  From what I am able to check, the 2 files appear to use the same streams, codecs, bit rates etc.  and indeed are two halves of a split movie.

As for the command to convert to avi, well, it appeared to work, i.e. it created an .avi file.  However both VLC (which in my experience will pretty much play anything) and Movie Player refuse to play the file.  And I can't even get the Property Manager to bring up a window of the file's properties.

So ... what to do?

It may work perfectly but I can't say that I'm especially enamoured of up and down loading files to Zamzar ...

---

### Post by VanillaMozilla on 2012-10-30
> **Langstracht said:**
> Every other thing I tried resulted in audio that was totally out-of-sync.
The AVIDemux Web site has some technical help on out of synch files.  There's a program I think called ProjectX that often fixes those up.  Just "add" the program and push the button.  Which button, I forget, and I don't have it here to look at.  Ignore all the blinking lights and black magic.  It will split the file into separate audio and video (and fix them in the process).  Then you can recombine audio and video in Avidemux.  It's one more little step, but XProject is extremely fast.

---

### Post by Langstracht on 2012-10-31
Unfortunately I couldn't find the referenced help on the AVIDemux site.  Much appreciate it if anyone can tell me the url.  Or indeed on any other site which would "help"

I did find on another thread the opinion that project-x is not easy to use and a help file is at [http://www.doom9.org/index.html?/DigiTV/projectx.htm](http://www.doom9.org/index.html?/DigiTV/projectx.htm).

Well if it is I can't find it.  So again if anyone can assist.

All of that said, if I understand correctly I am to concatenate the files into an .avi file.  Use project-x to strip out and somehow fix the non-synced audio.  And then in AVIDemux combine the video file and audio file.  Correct?

Again, TIA

---

### Post by VanillaMozilla on 2012-10-31
Part of the Avidemux site seems to be missing in action.  The actual name of the program is ProjectX.  You can find it in the Ubuntu Software Center.  Here are the directions from my notes.

This program is EXTREMELY fast, and it worked for me.  It's a Java program that can be installed from Ubuntu repositories.  Don't be dismayed by the complicated appearance.  Just add the file from the File menu, then press the "Quick" button to split the file into separate audio and video files.

---

