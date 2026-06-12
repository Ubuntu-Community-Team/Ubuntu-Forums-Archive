---
title: "Quick video editing app?"
date: 2014-02-09
forum: Multimedia Software
---

### Post by typos1 on 2014-02-09
Should it take a couple of hours and use virtually all my resources just to edit a 2 hour video into a half hour clip ? I appreciate video editing does take a lot of processing power, but I would have thought just extracting a clip from a video would be relatively simple as nothing extra has to be rendered, just 75% of the video not rendered, so I would have thought it would effectively copy and paste the section of the video I wanted and take a lot longer.

Am I doing something wrong ? Is there an app that does it quicker ?

edit - sorry, forgot to put in a title, can a mod please edit ?

---

### Post by timsdeepsky on 2014-02-09
Ffmpeg is your friend,,and will only take a few minutes to cut a part out of your video....
```
ffmpeg -ss 00:00:12.00 -i input.foo -acodec copy -vcodec copy -t 120 output.foo
```
I open a terminal in the folder the video is in....Then i use this ffmpeg code to cut and copy part of the video....
The 12 is how many seconds in to start grabbing the video....The 120 is how many seconds in to stop grabbing video....
Cheers....

---

### Post by typos1 on 2014-02-09
Ok, thanks. you mean that I modify the code depending on where I want it to start and where I want it to stop ?

Looks like it also copies the exact format the original video is in as well from the "acodec copy" and "vcodec copy" bits, thats great as all the apps I ve tried give you loads of options, but none for keeping things the same as in the orignal file

---

### Post by timsdeepsky on 2014-02-09
Yes....
You tell it how far into the video to start....And how far into the video to stop....(hours,,minutes,,and seconds in to start)
```
00:00:12.00
```

(how many seconds in to stop)
```
-t 120
```

I usually open the video in vlc and watch the timer to see how many seconds into the video to start grabbing....

You also have to change to your video name your grabbing from....
```
input.foo
```

And to the name you want the video saved as....```
output.foo
```

Remember to open terminal in the folder the video is in....
This will simply copy the section of video you want ....

---

### Post by typos1 on 2014-02-09
Great, thanks, I ll give it a go !

Cant use VLC cos it stopped working ages ago - now if I click on "open with VLC" nothing happens, I ve tried uninstalling and re-installing it but still the same, so I ll have to use buggy old UMplayer or buggy old SMplayer !

---

### Post by timsdeepsky on 2014-02-09
Smplayer has a nice little second timer on bottom right....I use it also....

---

### Post by typos1 on 2014-02-09
Yeah, its great for when its actually does play something !!

Dont suppose you know how to fix VLC do you ?

I opened a thread about that aswell, but know ones replied yet.

---

### Post by typos1 on 2014-02-09
Someone has replied now and sorted it for me.

I ll try your suggestion for editing tomorrow and let your know how I get on.

Thanks for your help so far.

---

### Post by varunendra on 2014-02-09
> **typos1 said:**
> Looks like it also copies the exact format the original video is in as well from the "acodec copy" and "vcodec copy" bits, thats great as all the apps I ve tried give you loads of options, but none for keeping things the same as in the orignal file

Then you perhaps didn't use AviDemux. It offers the option to simply "Copy" both audio and video streams, no transcoding or demuxing/remuxing is done. I use the GTK+ version and works great here.

The same thing can also be done with MKVToolnix (MKVmerge GUI > Global > Enable Splitting), but it doesn't offer a video play/preview, needs the timings to be manually typed (in correct format, for example, 01:24 is correct, 1:24 is not) and the output can only be .mkv (input maybe anything). MKV is just a container, so changing the extension (if the input is other than mkv) doesn't mean it'll be transcoded. It is simply packed into the mkv 'container'.

---

### Post by Bucky Ball on 2014-02-09
Title changed. You can edit the thread title yourself for a half hour after the first post by clicking 'Go Advanced'.

---

### Post by typos1 on 2014-02-10
> **timsdeepsky said:**
> Ffmpeg is your friend,,and will only take a few minutes to cut a part out of your video....
```
ffmpeg -ss 00:00:12.00 -i input.foo -acodec copy -vcodec copy -t 120 output.foo
```
I open a terminal in the folder the video is in....Then i use this ffmpeg code to cut and copy part of the video....
The 12 is how many seconds in to start grabbing the video....The 120 is how many seconds in to stop grabbing video....
Cheers....

I get this error when I try and do it:

"No command '-ss' found, did you mean:
 Command 'ass' from package 'irpas' (multiverse)
 Command 'ss' from package 'iproute' (main)
 Command 'gss' from package 'libgss-dev' (universe)
-ss: command not found"


Used my intiative and did sudo apt-get install for irpass, iproute and libgss-dev. 
irpas installed fine, it said iproute was already the newest version and libgss-dev installed fine. 

Tried again and still got the same errors saying the packages werent installed. I did close and re-open the terminal. Do I have to re-boot ?

edit: now it does work without those errors, so teh packages must have installedd ok. 

But now I get the error "input.video1.avi: No such file or directory", closed down the terminal and re-=opend again in folder, still get same error.

---

### Post by timsdeepsky on 2014-02-10
You do not need ```
input.video1.avi
```....
You need ```
video1.avi
```....
Let me know how this works....

---

### Post by typos1 on 2014-02-11
Doh !

Working now, mostly, although it does do some funny things somethimes: 

I can split 1 half hour clip from a 2 hour film and then try and split another from the same film (the unaltered original file) and I ll get an "[ac3 @ 0xe0dc20] frame sync error" 

or an

"[avi @ 0x10ee540] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 8 >= 8
av_interleaved_write_frame(): Invalid argument" error.

I got round the problem by converting the audio to mp3 for most clips, but there are a couple that I still get the error even after converting the audio to mp3. 

Any ideas ?

---

### Post by timsdeepsky on 2014-02-11
I have never seen this error myself....But there does seem to be some info floating around with others having this issue....
Some places to start....
[https://trac.ffmpeg.org/ticket/1154](https://trac.ffmpeg.org/ticket/1154)
[http://ubuntuforums.org/showthread.php?t=2127620](http://ubuntuforums.org/showthread.php?t=2127620)
[http://trac.ffmpeg.org/ticket/2210](http://trac.ffmpeg.org/ticket/2210)
[http://stackoverflow.com/questions/533469/ffmpeg-a-few-errors-including-invalid-frame-size-and-incomplete-frame](http://stackoverflow.com/questions/533469/ffmpeg-a-few-errors-including-invalid-frame-size-and-incomplete-frame)
Good luck....

---

### Post by FakeOutdoorsman on 2014-02-12
> **typos1 said:**
> Any ideas ?
[list=1]
[*]Get a [recent build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds).
[*]If it continues to fail then please show your ffmpeg commands and the complete console outputs.
[/list]

```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date +"%F").tar.gz
tar xzvf ffmpeg.static.32bit.$(date +"%F").tar.gz
./ffmpeg -i input ... output
```

Notice the **./** before the ** ffmpeg**.

---

### Post by dannyboy79 on 2014-02-12
if you're just looking for cutting and joining support in a GUI, then check out avidemux

---

### Post by typos1 on 2014-02-12
Ok, thanks timdeepsky.

I ve never get on with tarballs, they never work for me and dont want to spend ages compiling ffmpeg myself - you have to do 15 odd lines of code for each codec !! Tried several times to install latest ffmpeg tarball, though but I cant get it to install.

I did try Avidemux the other day, dannyboy79, but gave up, tried again today and got it to work !

I would like the latest version of ffmpeg on my pc though, any tips for quickly installing the ffmpeg tarball, FakeOutdoorsman ?

Thanks for everyones help so far !

---

### Post by FakeOutdoorsman on 2014-02-12
> **typos1 said:**
> I would like the latest version of ffmpeg on my pc though, any tips for quickly installing the ffmpeg tarball, FakeOutdoorsman ?

You don't need to install it. It's just a binary that you can execute. The commands I provided earlier in this thread should download the latest build and extract the archive. Then you can run it:
```
./ffmpeg -i input output
```
or use the full path:
```
/home/typos1/ffmpeg -i input output
```

If you want to include it into your PATH (I haven't tested this in a recent Ubuntu):
```

mkdir ~/bin
mv ~/ffmpeg ~/bin
. ~/.profile
```

Now the binary will be executed by simply entering "ffmpeg" in your console.

---

### Post by typos1 on 2014-02-12
Lol, I dont believe it, I didnt really notice that code and wasted a long time trying to do it myself !! 

I had a long, stressful day !

Once I run it once, its all on my system ? I mean I dont have to run it all again everytime I want to use ffmpeg ? And things (like Winff) that use ffmpeg will be able to use the more up to date version ?

edit: think your edit has answered my questions !

My system is 64bit BTW

Tried the first line and it says "ERROR 404: page not found"

---

### Post by FakeOutdoorsman on 2014-02-12
> **typos1 said:**
> Once I run it once, its all on my system?
There is no installing. It's just a binary file. You can place it anywhere you want to. To execute (run) it you can either:
[list]
[*]navigate to the directory containing the ffmpeg binary and run "./ffmpeg -i input output" (notice the **./** before the **ffmpeg**)
[*]use the full path as in "/home/typos1/ffmpeg -i input output" 
[*]or place the binary somewhere in your PATH
[/list]
See my previous post for more details on these points.

> I mean I dont have to run it all again everytime I want to use ffmpeg ?
Do you mean downloading and extracting the binary? No, you don't have to do that every time you want to use it.

> And things (like Winff) that use ffmpeg will be able to use the more up to date version ?
It depends. Only if you place the binary in a location in your user's PATH (and if the program uses the user's PATH instead of a "hardcoded" location), and if the program uses the ffmpeg binary and not the ffmpeg libraries. See my last post for more info, and also see [Ubuntu Wiki: Persistent Environment Variables](https://help.ubuntu.com/community/EnvironmentVariables#Persistent_environment_variables ) for more info.

However, WinFF and other programs may not work with a recent ffmpeg because the command presets are likely outdated.

> Tried the first line and it says "ERROR 404: page not found"
Do you mean the wget command? Try just [downloading it with your browser](http://ffmpeg.gusari.org/static/32bit/?C=M;O=D) (I provided the link previously too). Or try:

```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date -d yesterday +%F).tar.gz
```

---

### Post by typos1 on 2014-02-13
Tried the other link, it worked, then tried the second command, it didnt, so I modified it to relfect the different file I downloaded using your other suggestion. that worked. 

But the "./ffmpeg -i input ... output" lists the libraries, but syays "input: no such file or directory". 

So tried the original link, again the last command gives the same error . . . oh, hold on, the last command is for ffmpeg usage, not to install it etc ? Its an example for use ? think thats its lol.

So now if I try what timsdeepsky suggested, I still type"ffmpeg" at the begiining ? Or now ./ffmpeg ?

---

### Post by FakeOutdoorsman on 2014-02-13
> **typos1 said:**
> So tried the original link, again the last command gives the same error . . . oh, hold on, the last command is for ffmpeg usage, not to install it etc ? Its an example for use ? think thats its lol.
Yes, it was a simple usage example, but I have the feeling you are executing commands without fully reading the post. You should slow down and read the whole post before attempting any shown commands.

> **typos1 said:**
> So now if I try what timsdeepsky suggested, I still type"ffmpeg" at the begiining ? Or now ./ffmpeg ?
It depends&#8482;. As I mentioned before there are several methods:

[list]
[*]If you type "ffmpeg", and you have the fake ffmpeg from the repository installed, then this command will use the fake ffmpeg from the repository.
[*]If you type "./ffmpeg" in the same directory as your new ffmpeg binary, then your new ffmpeg binary will be used.
[*]If you type the full path to your new ffmpeg binary, such as "/home/typos1/ffmpeg" then your new ffmpeg binary will be used.
[*]If you moved the ffmpeg binary to a location in your PATH, then typing "ffmpeg" will use your new ffmpeg binary (I gave an example of this earlier in this thread).
[/list]

Although I tend to recommend and encourage usage of command line tools, they are not for everyone. Perhaps using avidemux is a better method for you since you mentioned before that it eventually worked for you.

---

### Post by typos1 on 2014-02-14
Thanks, I ve used command line many times in the 5 years I ve had ubuntu, I m far from the most proficicent user of it, but I m ok using it thanks. 

I just want to update to the latest version and I had no idea there were so many ways to do it and places to put it, I would have thought updating to the latest version would overwrite any previous version and I ve not heard of or kmowingly installed a fake version.

I may forget all this in months time and try and use it normally by just typing "ffmpeg".

So if I search for the original version and replace the folder with the version i just installed, will that give my the normal latest ffmpeg in the normal place on my pc ? I m not use to specifying paths to for software, software centre, synapptic or package installer usually does that for me.

---

### Post by FakeOutdoorsman on 2014-02-14
> **typos1 said:**
> I just want to update to the latest version and I had no idea there were so many ways to do it and places to put it, I would have thought updating to the latest version would overwrite any previous version
You didn't install the binary (not that you need to), so nothing is being replaced.

> **typos1 said:**
> I ve not heard of or kmowingly installed a fake version.
I believe that is the intention by the fork. See:
[list]
[*][Who can tell me the difference and relation between ffmpeg, libav, and avconv?](http://stackoverflow.com/a/9477756/1109017)
[*][The FFmpeg/Libav situation](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html)
[/list]

> **typos1 said:**
> So if I search for the original version and replace the folder with the version i just installed, will that give my the normal latest ffmpeg in the normal place on my pc ?
That can potentially break stuff that depends on the repository version.

> **typos1 said:**
> I m not use to specifying paths to for software, software centre, synapptic or package installer usually does that for me.

The reason I do not recommend performing a standard installation of ffmpeg to the system is because things that depend on ffmpeg will be expecting the version from the repository, and since it is so old this can potentially cause issues since they are looking for a specific version. Not installing the binary that you downloaded allows the other programs to use the old, buggy, Libav fork version from the repository, but also allows you to use a recent, real version of ffmpeg from FFmpeg. So if you want to just type "ffmpeg" and have it use your new ffmpeg, and allow (most) of the repository packages to use the crappy fake ffmpeg, then: make a **bin** directory in your home directory, move the ffmpeg file into that bin directory, then in Terminal run ". ~/.profile && hash ffmpeg".

To undo this just move the ffmpeg file out of that same bin directory and in Terminal run ". ~/.profile && hash ffmpeg".

---

### Post by typos1 on 2014-02-15
Ok, thanks used a combination of Avidemux and /home/typos1/ffmpeg ! Thanks for all your help !

---

