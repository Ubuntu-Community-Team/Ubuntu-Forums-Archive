---
title: "DVD converting - how to get mp4 less than 1 gb"
date: 2010-12-14
forum: Multimedia Software
---

### Post by Ordes on 2010-12-14
hi..

searching for this the last days... unsuccessful so far..
i am converting my DVDs into a media library. The ripping itself is no problem. (using Xilisoft dvd-rip under wine; works flawless).

when i convert to a mp4 file, with good quality, the output is always around 1.2 -1.8 gb. depending on the movie file. i tried Xvid and the size is pretty much the same. only by reduucing the pixel size etc... i get like a 600-800 mb file.

now i wonder. when i see other ripped movies, with about the same movie length, they getting 800mb mp4, in perfect quality, no smaller screen, pixels are great etc... is there any kind of advanced setting to it? bitrate, audio? to get down to this file size..?

txs

---

### Post by forrestcupp on 2010-12-14
Are you including all the streams?  Try cutting out all of the subtitles and other audio streams and only keep the main video and audio stream.  It probably still won't help enough, but it's worth a try.

---

### Post by handy on 2010-12-14
I used HandBrake-CLI to convert my large DVD collection to 1GB sized .mp4 files. It worked without fault, & it was fast. The more cores you CPU has the faster it will work.

There is a GUI version in the Ubuntu repos also. I like the Terminal verion as it is quick & easy to use once you get yourself setup to use it. 

To make it easy to use, I keep a couple of my most used commands as aliases in my ~/.bashrc so that I can call them up for reference to save me reinventing the wheel.

When I call it with the alias it fails to work, I then copy the failed command line which was printed into the Terminal when I called it via the alias (handbrake) & paste it to the active command line. Then I may edit it to suit my needs hit the return key, make sure it gets going & go to another workspace to do whatever.

If it doesn't succeed the first time, (it only takes a short time to find out) then you have a look at the output & find the number of the title that you want, which is quite easy, then change the command line so that it processes that number directly, instead of looking for the main-feature, which is my default setting. 

Here are the three command lines that I have in my .bashrc for processing videos, the first cd's into the directory where I send the output, or sometimes I'll put a file in their that I want to transcode or shrink, the other two should be self explanatory. Also calling the hanbrake-cli --help in another tab of the Terminal or another Terminal if you have to is very informative indeed, they also have a great website:

```
alias .tmp="cd /mnt/store/pkg/vid/.tmp"

alias hb="echo handbrake-cli -t --main-feature -i /media/dvd -o NAME.HERE.mp4 -e x264 -b 1000 -B 192 -s 1 --subtitle-burn"

alias hbt="echo HandBrakeCLI -t <title number here> -i /media/dvd -o NAME-HERE.mp4 -e x264 -b 1000 -B 192 -s 1 --subtitle-burn"


```

---

### Post by Ordes on 2010-12-14
@forrest; yes i do take of everything. and just convert the main vid

...
will take a look at handbrake. though i am pretty pleased with my dvd ripper.

...
doing more research. i think the secret is fine tuning with the bit rate.

---

### Post by cra1g321 on 2010-12-16
have you tried dvd:rip ?? i think it has encoding options

---

