---
title: "Looking for simple video converter program"
date: 2017-01-12
forum: Multimedia Software
---

### Post by Veronemilie on 2017-01-12
Hi, I am looking for a simple video conversion program, I used to use winff but that is no longer in the software center & doesn't work when installed from the PPA. I need a program that will convert mp4, mkv, etc... to AVI.  Thanks

---

### Post by howefield on 2017-01-12
Winff is still in the repositories, possibly one of the applications not to show in the Software Centre (there still is a few)

```
apt-cache search winff
winff - graphical video and audio batch converter using ffmpeg or avconv
winff-dbg - winff debugging symbols
winff-doc - winff documentation
winff-gtk2 - GTK+ variant of winff
winff-qt - Qt variant of winff
```

```
apt-cache policy winff
winff:
  Installed: (none)
  Candidate: 1.5.3-6
  Version table:
     1.5.3-6 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu xenial/universe i386 Packages
```

This is from a 16.04 installation.

Install with

```
sudo apt-get install winff
```

---

### Post by Bucky Ball on 2017-01-12
Thanks to both of you for the Winff tip. Currently [s]battling with settings[/s] exploring Handbrake as I have 136Gb of short clips to crush down. Winff is in Synaptic Package Manager, same version, 1.5.3-6, so going to give it a go now. :)

Getting there with Handbrake output but will see what Winff spits out.

---

### Post by Veronemilie on 2017-01-12
I just re-installed winff & it still isn't working. When I start the conversion the terminal window opens (as it should) & then nothing else happens it just sits there.   Any suggestions on what could be wrong?  Thanks

---

### Post by howefield on 2017-01-12
> **Veronemilie said:**
> I just re-installed winff & it still isn't working. When I start the conversion the terminal window opens (as it should) & then nothing else happens it just sits there.   Any suggestions on what could be wrong?  Thanks

Which version of Ubuntu, so that I can try on a like for like system ?

Also, are you getting any error in the terminal ?

---

### Post by Veronemilie on 2017-01-12
Version 16.10 No error messages just not doing anything. Thank you

---

### Post by The Cog on 2017-01-12
Are you sure it's not just a little slow? Try running the command **top** in another terminal and see what the CPU is up to.

---

### Post by howefield on 2017-01-12
Well, no issue here on 16.10 with winff converting an mp4 to avi.

Did you purge the existing install from the ppa before installing from the Ubuntu repositories ?

The winff command used to test was

```
/usr/bin/ffmpeg -y -i "/Data/Videos//BigBuckBunny_320x180.mp4" -acodec libmp3lame -vcodec msmpeg4 -b:a 192k -b:v 1000k -filter:v scale=w=640:h=480 -ar 44100 "/Data/Videos/BigBuckBunny_320x180.avi"
```

You could try that subbing your files/paths instead of the above.

---

### Post by Veronemilie on 2017-01-12
Here is a screenshot of the top command.

I went into the options in Winff under the FFmpeg tab & copied the command in the 1st pass box, pasted it into the terminal, hit enter & it started to convert the file. So it seems that it isn't the conversion part of the program that isn't working simply the part that starts it automatically. Although I am able to convert this way I can't set a batch of videos to convert & then run it overnight I have to run every file individually.

Does anyone have an idea of how to fix it? Thanks

---

### Post by SeijiSensei on 2017-01-13
> **Veronemilie said:**
> I can't set a batch of videos to convert & then run it overnight I have to run every file individually.
It's much easier to do this from the terminal.  Something like this using howefield's code:
```

cd /path/to/your/video/files
for f in *.mp4
do
     /usr/bin/ffmpeg -y -i "$f" -acodec libmp3lame -vcodec msmpeg4 -b:a 192k -b:v 1000k -filter:v \
          scale=w=640:h=480 -ar 44100 "$f.avi"
done

```
That sequence of commands iterates over all files with a .mp4 extension in the /path/to/your/video/files directory and runs ffmpeg to do the conversions.

---

### Post by Veronemilie on 2017-01-13
Just tried it & got this error message: *.mp4: No such file or directory  Sorry I don't have a lot of experience with terminal maybe I just didn't input it the right way, I put in the file directory (terminal validated it was a valid directory) & the I pasted I the code from the word "for" to "done" then hit enter & got the error message.   I really appreciate the help, Thanks

---

### Post by mc4man on 2017-01-13
> **Veronemilie said:**
> I just re-installed winff & it still isn't working. When I start the conversion the terminal window opens (as it should) & then nothing else happens it just sits there.   Any suggestions on what could be wrong?  Thanks
Maybe take a screen shot of the terminal that's 'just sitting there' & attach to a post. Use Alt+PrtSc (Print) to just grab the terminal in screenshot

---

### Post by SeijiSensei on 2017-01-13
> **Veronemilie said:**
> Just tried it & got this error message: *.mp4: No such file or directory

Are you starting with MP4 files or something else like Matroska (.mkv)?  The line
```
for f in *.mp4
```
matches files with the .mp4 extension.  If your files are in another container format like .mkv, you need to use that instead of "*.mp4" in the code.

Before you travel too far down this road, try converting one file using the /usr/bin/ffmpeg command with the input file and output file like those shown in [Howefield's post above](https://ubuntuforums.org/showthread.php?t=2349239&p=13593881&viewfull=1#post13593881).

---

### Post by Veronemilie on 2017-01-13
> **mc4man said:**
> Maybe take a screen shot of the terminal that's 'just sitting there' & attach to a post. Use Alt+PrtSc (Print) to just grab the terminal in screenshot  Here is the picture, as I said just sitting there doing nothing, a few posts earlier there is a screenshot of what my cpu is doing & I have let it sit like this for 30+ minutes & it still won't do anything.

> **SeijiSensei said:**
> Are you starting with MP4 files or something else like Matroska (.mkv)? The line ```
for f in *.mp4
``` matches files with the .mp4 extension. If your files are in another container format like .mkv, you need to use that instead of "*.mp4" in the code.  Before you travel too far down this road, try converting one file using the /usr/bin/ffmpeg command with the input file and output file like those shown in [Howefield's post above](https://ubuntuforums.org/showthread.php?t=2349239&p=13593881&viewfull=1#post13593881).  The folder I used to test it was full of mp4's, at least a dozen.  The code that I have been using from the FFmpeg tab inside the WinFF program is almost identical to the one posted in Howefield's post, here is an example  ```
/usr/bin/avconv -y -i "/home/vero/Downloads/Ice Age Collision Course (2016) MULTi [1080p] BluRay x264-PopHD.mkv" -f avi -r 29.97 -vcodec libxvid -vtag XVID -filter:v scale=w=640:h=480 -aspect 4:3 -maxrate 1800k -b:v 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -trellis 1 -flags +aic -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -b:a 128k -ac 2 "/home/vero/Ice Age Collision Course (2016) MULTi [1080p] BluRay x264-PopHD.avi"
```  I can convert videos, just not by using the convert button in the program, I have to copy the code & paste it into the terminal.

---

### Post by SeijiSensei on 2017-01-13
> **Veronemilie said:**
> The folder I used to test it was full of mp4's, at least a dozen.
And they have lower-case extensions, not *.MP4 or *.Mp4?  (Unix shells are case-sensitive.)  Just to make sure I wasn't living in la-la land, I ran the sequence
```

for f in *.mp4
do
ls $f
done

```
and it returned a list of the mp4 videos in the current directory.

---

### Post by igdfpm on 2017-01-14
May be a brainfart in the gui when using avconv? - I have ffmpeg installed and do not see this behaviour.

---

### Post by mc4man on 2017-01-14
Re: winff
You need to check in winff's menu > Preferences > Linux & make sure that it's using the proper binary & path to that binary. As you've never mentioned what release of Ubuntu it could be avconv (too bad) or ffmpeg (better
screen shows default setup in 16.04 which uses ffmpeg

---

### Post by Veronemilie on 2017-01-14
> **mc4man said:**
> Re: winff You need to check in winff's menu > Preferences > Linux & make sure that it's using the proper binary & path to that binary. As you've never mentioned what release of Ubuntu it could be avconv (too bad) or ffmpeg (better screen shows default setup in 16.04 which uses ffmpeg  I did mention that I use 16.10 on page 1 (post #6) I did go through & change my settings to match yours & it works great now. Thank you :)

---

### Post by justanuddawannabe on 2017-03-27
how is this marked as "solved" ?

---

### Post by vasa1 on 2017-03-27
> **justanuddawannabe said:**
> how is this marked as "solved" ?
You can only mark support threads **you** start [SOLVED]. For how to do so look at [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by deadflowr on 2017-03-27
> **justanuddawannabe said:**
> how is this marked as "solved" ?

It's entirely up to the Original Poster to determine the reasons any thread is solved.
Any reason will do.

But from the look of it, the OP got winff installed, and set it up to work well enough for them.

---

