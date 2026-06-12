---
title: "Converting video to WMV - audio and video out of sync (ffmpeg and mencoder)"
date: 2012-11-07
forum: Multimedia Software
---

### Post by Treppiede on 2012-11-07
Guys,
I have an AVI video. I need to convert it to WMV.

I Googled "convert to WMV linux" and got a few results suggesting ffmpeg and mencoder.

In both cases, they seem to generate an identical file, but the audio goes out of synch by a few seconds.

Do you have any advice on how to resolve this issue?

If I recall correctly, the ffmpeg command I used didn't have special options besides input and output files... but this should be the mencoder command I ran:

mencoder -oac copy -ovc lavc -of mpeg -o output_file.wmv your_file.avi

Thank you in advance for the help!

-Walter

---

### Post by shantiq on 2012-11-07
what i would do here [for what it is worth] would be to turn your avi to mkv with handbrake to get a good and stable file   [avi often is not but mkv is]



> sudo add-apt-repository  ppa:stebbins/handbrake-releases 

> sudo apt-get update && sudo apt-get install handbrake lame


**to install; then** for example [adapt to your wishes]

>  HandBrakeCLI -i ~/Videos/yourvid.avi -o ~/Desktop/yourvid.mkv -e ffmpeg2  -b 1500 -E lame -B 96 -r 25   insert -w and -l with  number   say  -w 640 -l 320 if you wish to control width and height of vid


find all settings with > HandBrakeCLI -h   or use the gui


**then run the mkv to wmv the way you said**

> ffmpeg  -i yourvid.mkv    -acodec copy -vcodec copy   yourvid.wmv

---

### Post by CaptainLinux on 2012-11-07
Try adding -ofps to your mencoder command to make sure the frame rate is identical between the input and output files.

---

### Post by Treppiede on 2012-11-07
Awesome guys, thanks for the advice.
I'll try this later tonight or tomorrow and report back!

---

### Post by Treppiede on 2012-11-08
Guys,
I was able to use this command successfully:

mencoder -oac copy -ovc copy 1.avi 2.avi 3.avi 4.avi -o Full.wmv

One more question... I was asked to make the width of the viewing window 580 pixels, since he's putting it on a website and it should match the other embedded videos.

Right now the video is about 720px wide.

What's the most efficient way to accomplish this?

This is for a non-profit website, btw.

Thank you for your help.

-Walter

---

### Post by shantiq on 2012-11-08
check properties of current vid then use ffmpeg for conversion with   the


-s switch    as    -s 580x[whatever is your height]   see below for info


> -s size 
Set frame size. The format is wxh (ffserver default = 160x128, ffmpeg default = same as source). The following abbreviations are recognized: 
sqcif 
128x96 
qcif 
176x144 
cif 

352x288 
4cif 
704x576 
16cif 
1408x1152 
qqvga 
160x120 
qvga 
320x240 
vga 

640x480 
svga 
800x600 
xga 

1024x768 
uxga 
1600x1200 
qxga 
2048x1536 
sxga 
1280x1024 
qsxga 
2560x2048 
hsxga 
5120x4096 
wvga 
852x480 
wxga 
1366x768 
wsxga 
1600x1024 
wuxga 
1920x1200 
woxga 
2560x1600 
wqsxga 
3200x2048 
wquxga 
3840x2400 
whsxga 
6400x4096 
whuxga 
7680x4800 
cga 

320x200 

ega 

640x350 
hd480 
852x480 
hd720 
1280x720 
hd1080 
1920x1080


or again handbrake   see my first post above

---

### Post by Treppiede on 2012-11-09
> **shantiq said:**
> check properties of current vid then use ffmpeg for conversion with   the

-s switch    as    -s 580x[whatever is your height]   see below for info

or again handbrake   see my first post aboveDear Shantiq,
Thank you for the help.

I apologize, I hadn't seen the resizing option you had included in your original post.

To figure out correct height, I took a snapshot of the video via VLC, opened it in GIMP and resized the width of the picture to 580px. GIMP told me the height in scale would have been 387px.

I realize there are probably much more direct ways, but this did the trick. :)

I proceeded to resize the video using this command:

ffmpeg -i Full.wmv -s 580x378 Full_580x387.wmv

The new video has the correct size and is 20% the size of the original, but there are two issues:
[LIST]
[*]It has visibly large pixels, literally squares (tiled)
[*]Audio went out of sync again
[/LIST]

Is Handbrake the only option, or can I try one of the following?
[LIST]
[*]ffmpeg with a flag to prevent quality from dropping so much and another flag to keep audio synced
[*]mencoder with similar flags
[/LIST]

I ask because I am on my work PC and I can't add repositories for security purposes, so no Handbrake, but ffmpeg and mencoder are kosher.
I can always do this at home and use Handbrake, so no sweat, although it would be nice to get it done here, so I can upload the video using a decent connection. :)

Thanks for all the help!

---

### Post by tnob on 2012-11-09
[FONT="Arial"][/FONT]
Treppiede,

I'm not sure as to whether you're talking about a VHS tape, a DVD or a video file you'd need to convert to .wmv. A much less complicated way to do this might be with VLC media player.

Click Media (in the top bar) --> click medium you'd like to show, so VLC will recognize it (and check that it does indeed) --> click Save/Convert. Choose the format you prefer, from a drop-down menu, and a suitable location and title for saving - and Bob's your uncle! Most of the time anyway...

tnob

---

### Post by shantiq on 2012-11-09
hhhhhhhhhhhhha   should have advised you to try and use


> ffmpeg -i Full.wmv [COLOR="DarkRed"]**-acodec copy -vcodec copy **[/COLOR]-s 580x387 Full_580x387.wmv


with the line you used  what you got there is probably ffmpeg's default really low size [MB] quality conversion  [ i bet your video dropped a lot of MB :KS:KS:KS  ???   ]


so try it again with [COLOR="DarkRed"]**-acodec copy -vcodec copy **[/COLOR]   see if it is ok now

---

### Post by andrew.46 on 2012-11-10
You can avoid the defaults by specifying the codecs you want in the following manner:

```

fmpeg -i Cold_Chisel_Bow_River.mp4 \
       **[COLOR="Red"]-c:v wmv2[/COLOR]** -q:v 5 \
       **[COLOR="Red"]-c:a wmav2[/COLOR]** -b:a 128k -f asf \
       Cold_Chisel_Bow_River.asf

```

This should produce a file that will even keep windows users happy and also give you some scope for further experimentation :).

---

### Post by Treppiede on 2012-12-11
Hey Guys,
First of all, thank you for your time and helpful advice.

I just wanted to follow up on the solution I wound up using... I downloaded Microsoft Expression Encoder (Free version) and was able to get it done eventually.

This is not to take anything away from the great open source tools and options available, I blame my video editing ignorance and lack of time (needed to get this done and upload it asap for the website), but it is done at last.

Thank you again for your help.

-Walter

---

### Post by andrew.46 on 2012-12-11
> **Treppiede said:**
> This is not to take anything away from the great open source tools and options available, I blame my video editing ignorance and lack of time (needed to get this done and upload it asap for the website), but it is done at last.

I am a big fan of using the best tool available to at the time to get the job done, so good to hear that you have accomplished your goal. Perhaps one day you will return to the great open source tools mentioned in this thread and have a shot at these very fine applications...

---

