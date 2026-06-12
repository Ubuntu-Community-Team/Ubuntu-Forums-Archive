---
title: "MP4Box Help"
date: 2009-06-10
forum: Multimedia Software
---

### Post by tkdiamond08 on 2009-06-10
Hey,

I seem to be having some issues with MP4Box, any help would be greatly appreciated.

For some reason MP4Box can not hint videos from any other disk than the one the video is stored in. What I am trying to accomplish is make a PHP script that will auto convert an uploaded video and then hint it, and then move it into the correct folder for streaming (all of which is done on an external disk).

Everything works in the script BUT MP4Box (including ffmpeg, and other commands), and after a little more investigating I realized that the reason it isn't is that MP4Box will fail if the command is executed on anywhere else other than the external disk. So trying to hint a file on the external drive "/media/disk/videos" from "/" in the command prompt won't work, however executing it from "/media/disk" will. I'm assuming that because the script is in "/var/www/" this is why it doesn't work.

Here's part of the error output

*** glibc detected *** MP4Box: free(): invalid pointer: 0xb7c5c170 ***

Is this a bug? Any other command will work on both my internal and external drive...

The only work arounds I can think of are:

- fix MP4Box
- somehow get the script to execute itself on the hard disk, or change the directory in the script? (don't know how to do this)
- change the default upload to reside on the server itself (not the hard disk) but this would require moving the file once it is finished (seems counter-intuitive and would take much longer)

It is VERY important that I get this working before Friday (last day of school) as it is a project I'm working on for my high school, and I'm graduating this year, so I'd really like to get it done.

P.S. sorry for the wall of text. :(

thanks

---

### Post by tkdiamond08 on 2009-06-10
bump :(

---

### Post by FakeOutdoorsman on 2009-06-10
Not really a solution, but if you are simply rearranging the moov atom to the front of the video file you can try qt-faststart instead of MP4Box:
```
qt-faststart input.mp4 output.mp4
```
This tool is included in Jaunty's FFmpeg, or if you compile FFmpeg yourself it is in the *tools* directory of your FFmpeg source:
```
cd ~/ffmpeg/tools
make qt-faststart
sudo cp qt-faststart /usr/local/bin
```

---

### Post by tkdiamond08 on 2009-06-10
> **FakeOutdoorsman said:**
> Not really a solution, but if you are simply rearranging the moov atom to the front of the video file you can try qt-faststart instead of MP4Box


Thanks for the reply outdoorsman,

doesn't moving the moov atom to the front just make it so that the video will be able to play at the begining but still have to download the full thing (instead of streaming)? The ability to stream is a vital part of the project. I am using Darwin Streaming Server as well to accomplish this (my mistake for leaving that out).

---

### Post by FakeOutdoorsman on 2009-06-11
I believe this allows the video to begin playing before it completely downloads the whole file.  Similar to what YouTube does I think.  I assumed you weren't streaming and I have little experience with streaming video.

---

### Post by tkdiamond08 on 2009-06-11
> **FakeOutdoorsman said:**
> I believe this allows the video to begin playing before it completely downloads the whole file.  Similar to what YouTube does I think.  I assumed you weren't streaming and I have little experience with streaming video.

Haha, it's ok, I guess that's a pretty plausible solution though nonetheless, so thanks for your help!

But it would be reallllly nice to get this hinting problem resolved. Seems odd I can't execute a command on a different disk, no?

---

### Post by tkdiamond08 on 2009-06-11
Nobody knows why this might be happening? Surely someone else has MP4Box and can test and see if they are having this problem.

---

### Post by FakeOutdoorsman on 2009-06-11
Did you compile GPAC/MP4Box yourself or are you install from the Ubuntu repository?  The latest GPAC is 0.4.5, but the version in the Jaunty repo is 0.4.4.  What version of Ubuntu are you using?

---

### Post by tkdiamond08 on 2009-06-12
> **FakeOutdoorsman said:**
> Did you compile GPAC/MP4Box yourself or are you install from the Ubuntu repository?  The latest GPAC is 0.4.5, but the version in the Jaunty repo is 0.4.4.  What version of Ubuntu are you using?

Hello again outdoorsman,

I am using Ubuntu 8.10, and GPAAC version is 0.4.4 (installed it with apt-get), I don't really want to compile from the source code, I had to do that with ffmpeg since my school firewall blocks SVN, but I guess that is a possibility, if you have MP4Box, can you test and see if you are getting the same kind of error I am (assuming you have 0.4.5)?

---

### Post by FakeOutdoorsman on 2009-06-12
> **tkdiamond08 said:**
> Hello again outdoorsman,

I am using Ubuntu 8.10, and GPAAC version is 0.4.4 (installed it with apt-get), I don't really want to compile from the source code, I had to do that with ffmpeg since my school firewall blocks SVN, but I guess that is a possibility, if you have MP4Box, can you test and see if you are getting the same kind of error I am (assuming you have 0.4.5)?

What is your MP4Box command?

---

### Post by FlintyVamp on 2009-06-14
I'm also getting the same error.. 

I run "MP4Box -inter 200 video.mp4"  to move the atom to the start to allow playback while the video is still downloading.

I'll use qt-quickstat for now.

---

### Post by tkdiamond08 on 2009-06-15
> **FakeOutdoorsman said:**
> What is your MP4Box command?

MP4Box -hint /full/directory/to/file.mp4

I've been investigating this further, and it turns out I can't execute MP4Box from anywhere other than my /home/user folder or "~" without putting sudo infront of it, so "sudo MP4Box -hint /full/directory/to/file.mp4" will work from "/", and it will also work if i am acting as sudo user (sudo -i), however if you remove the sudo it will not, even if I change the permissions on the files and the folders so that anyone can do anything to it, it doesn't work.

So for my script to work i would somehow have to get it to think it's root executing the commands, and I thought using visudo would solve this, but it did not. 

So **does anyone know how to execute a command as root in php?**

---

