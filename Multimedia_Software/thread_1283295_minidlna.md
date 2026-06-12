---
title: "minidlna"
date: 2009-10-05
forum: Multimedia Software
---

### Post by desimoviebuff on 2009-10-05
hi i am trying to get my ubuntu jaunty laptop setup as a media server so that i can watch my movies on sony bravia. did some searching to find that only minidlna seems to support Sony (or is it the other way). tried installing but it does not run. does any one have a clean set of instructions to make this work. i downloaded binaries from sourceforge. when i run minidlna it gives an erros saying some file is not being created. also i am not sure about how to set up the conf files. any help will be appreciated. thanks

---

### Post by mihaki on 2009-10-14
Hi!

I have been playing with minidlna now for some time and I made it show photos and play music. However so far, I still haven't been able to make it play movies (which doesn't necessarily mean it can't be done).

Here is simple HOW-TO:
1. I created a hiden folder in my home directory and copied there two files I got from sourceforge (minidlna and minidlna.conf - version 1.0.15). 

2. Then I edited minidlna.conf. Basically the only thing that is required is to set 
media_dir=/<folder_where_I_keep_my_media_files>. 
That is, you must tell minidlna where you keep your media files. (see the example in comments). Also some people may need to change the port to which minidlna listens... for me the default 8200 was OK.

3. Then I added the following command in 
System->Preferences->Startup Applications,
Name = "MiniDlna" (or whatever), 
Command = "<path_to_minidlna>/minidlna -f minidlna.conf", 
Comment = "Whatever is OK"

4. Then click OK and restart the computer. Next time the computer starts, minidlna should be up and running.

5. Then I added some media content (jpg, mp3, etc.) to the folder
/<folder_where_I_keep_my_media_files>

6. Then I started the TV and tried to look-up the server through TV's menues. Minidlna was usually found w/o any problem. Pictures and music should also be accessible after that.


As far as the video goes, there are two problems:
a) One must choose the video format that minidlna recognizes
b) That same video format must also be supported by TV and sony TV sets are known to be quite picky... No direct AVI or FLASH support at the moment I am afraid.

Still looking for the solution...

---

### Post by mihaki on 2009-10-14
OK!

I found solution (it is actually quite simple .. I am embarrassed:oops:).
It turns out that minidlna can handle mpeg2 quite gracefully.
The following command should do the trick:

ffmpeg -i <video_to_convert> -target ntsc-dvd <out_file.mpg>

For those who have PAL TV (Europe etc.), '-target pal-dvd' can be used.
The resulting .mpg file should then be placed into minidlna's media folder.
After that my TV (40V1) played basically any video I tried.

There is also another thread which deals with the issue in more details:
[http://swiss.ubuntuforums.org/showthread.php?t=1185619](http://swiss.ubuntuforums.org/showthread.php?t=1185619)

Still trying to figure out about HighDefinition content...

---

### Post by joepz on 2009-12-30
Hi,

Just bought a Sony Bravia W5500 and hoping to get DLNA working (like you). First a basic question;
Is MiniDLNA simulating a DLNA compatible device? I am running Ubuntu 9.10 on a desktop PC. Would MiniDLNA indeed do the trick?

Then; converting all the movie files to MPEG2 seems a bit too much. Any alternatives?

Thanks,
Joep

---

