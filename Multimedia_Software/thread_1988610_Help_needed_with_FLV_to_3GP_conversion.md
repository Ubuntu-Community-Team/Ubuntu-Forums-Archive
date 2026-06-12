---
title: "Help needed with FLV to 3GP conversion"
date: 2012-05-27
forum: Multimedia Software
---

### Post by S2UIRR3L on 2012-05-27
Long story short...

I uploaded some videos to YouTube and the kids got to my phone and I lost all my original files. I can download them from YouTube, but they're in FLV format.

I have an LG VX8575 Chocolate Touch with Verizon Wireless. It only plays videos with the file format extension of 3G2 (maybe 3GP as well, but not totally sure).

I have (and really like) OpenShot Video Editor. I can open just about anything in here, and save the output as just about anything with OpenShot Video Editor.

When I try to save a file out put to 3G2 or 3GP, OpenShot just closes it's self with no warning and no error messages. I've tried just about everything on it so...

MY MAIN QUESTION - IS THERE ANYONE ELSE WHO HAD TRIED SOMETHING LIKE THIS AND AM I MISSING ANY KINDS OF CODECS NEEDED TO SAVE IN 3G2 or 3GP?

I'm a little bit of a beginner, so most of everything I do is through Synaptics Package Manager or more recently, the Ubuntu Software Center. It's just really easy.

If you need more information to help me out, please feel free to post a command for terminal and I'll give you all the output you need to know about everything.

By the way... I'm still using Ubuntu 10.04 until it's no longer supported and I "NEED" to move to Precise or what ever is out at the time of Lucid's demise lol!!!

This is the best page that I can dig up after about an hour or two of Googling around. My phone is the Chocolate Touch VX8575 (Verizon Wireless): [http://www.ehow.com/info_8630742_video-do-lg-chocolates-use.html](http://www.ehow.com/info_8630742_video-do-lg-chocolates-use.html)

Thanks a million in advance...
You guys are the best there is!!!

-Leo in Massachusetts (us)

---

### Post by Vereinfachen on 2012-05-28
[LIST=1]
[*]Install ffmpeg (sudo apt-get install ffmpeg)
[*]use this code in the terminal to convert to 3gp.
[/LIST]
```
ffmpeg -i inputfile.flv -s qcif -vcodec h263 -acodec libamr_nb -ac 1 -ar 8000 -r 25 -ab 12200 -y outputfile.3gp
```

---

### Post by S2UIRR3L on 2012-05-28
I'm just curious to know how it works and what it does exactly, before I sudo apt-get and do all this stuff.

And is there a way to undo all this stuff, just in case there's the chance of it conflicting with other things?

I just did a search for it in the Ubuntu Software Center and it shows up. At least there, I know how to delete it.

-Leo

---

### Post by Vereinfachen on 2012-05-28
Yea, sorry. You can also install ffmpeg using the software center. Whatever way you prefer :)

---

### Post by S2UIRR3L on 2012-05-28
Okay - thanks a million for everything... This is what I've done:

#1 - I found out that my phone will also play MP4, in addition to 3G2 and 3GP.
#2 - I've used Ubuntu Software Center to download ffmpeg, in case I needed it.
#3 - Used OpenShot to convert, put it on mini-sd, and my phone plays the video.

Only problem now is that there's no sound when I play it on the phone. I take the mini-sd card out of my phone and plug it back into my computer, everything plays. But I guess my phone has some issues, perhaps it doesn't have the correct encoders or what not, to play the video in the way I'm saving it?

Here's a few photos of what I did.
Photo #1 shows the ffmpeg thing that I downloaded from Ubuntu Software Center.
Photo #2 shows all the choices I get when I'm about to save the movie to desktop.

[IMG]http://i292.photobucket.com/albums/mm10/s2uirr3l/Screenshot0001.png[/IMG]

[IMG]http://i292.photobucket.com/albums/mm10/s2uirr3l/Screenshot0002.png[/IMG]

I hope this helps...? By the way, there were a few MP4 choices, I tried them all, they all work on my computer, but sound doesn't play on my phone. As for the Mobile 360p, that's the only target that will "fit" my phone because you can only use resolutions that are at or below 320 by 240 pixels, The quality means nothing, since neither one of them will be heard on my phone.


-Leo in Massachusetts

---

### Post by FakeOutdoorsman on 2012-05-29
Do you have a video that does work with the device? You can inspect it with ffmpeg to see what is inside:
```
ffmpeg -i the_actual_name_of_your_input_file_that_works_on_your_phone.3gp
```

---

### Post by S2UIRR3L on 2012-06-02
I've tried a million different thing, and I've come to the conclusion that it's probably my phone being a piece of rubbish... so I'll mark this thread as SOLVED as there's a lot of great advice that's worked for me, minus the sound lol.

Thanks a million for everything. As always, Ubuntu Forums wouldn't be great without all the help and advice from eveyone... Thanks!!!

-Leo

---

