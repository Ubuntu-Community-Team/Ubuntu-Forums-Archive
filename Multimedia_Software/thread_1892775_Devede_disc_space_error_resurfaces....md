---
title: "Devede disc space error resurfaces..."
date: 2011-12-08
forum: Multimedia Software
---

### Post by mystmaiden on 2011-12-08
I've used devede a few times and was just getting the hang of making some mpegs (converted before using in devede) and then encoding them for burning to a dvd and whammo suddenly the devede disc space error reared its ugly head. I've tried every solultion I can find on the web to no effect (complete removal then reinstall, adding a video_format file, etc). I also read a solution that said just to go to the devede website and load the latest one. I did that but I get 
```
Error  - Dependency not satisfiable ffmpeg >=4:0.7.2
```What I can't find is ffmpeg 4.0.7.2 

Have any of you found a different solution for this? I'm running 10.04 LTS

thanks in advance

mystmaiden

---

### Post by forrent_apt on 2011-12-11
Ran into the same "maybe you ran out of disk space?" error with Devede. I too get the following errors when installing
devede_3.20.0-1~rastersoft1_all.deb :

 devede depends on ffmpeg (>= 4:0.7.2); however:
  Package ffmpeg is not installed.
 devede depends on libavformat-52 | libavformat-extra-53; however:
  Package libavformat-52 is not installed.
  Package libavformat-extra-53 is not installed.
 devede depends on libavcodec-52 | libavcodec-extra-53; however:
  Package libavcodec-52 is not installed.
  Package libavcodec-extra-53 is not installed.
dpkg: error processing devede (--install):
 dependency problems - leaving unconfigured

Any help out there?

Thanks

---

### Post by Les_W on 2011-12-18
Same problem! I have a feeling that we're going to have to go 12.04 for a solution...

---

### Post by Toz on 2011-12-18
See: [https://bugs.launchpad.net/ubuntu/+source/devede/+bug/755340]("https://bugs.launchpad.net/ubuntu/+source/devede/+bug/755340"). The proposed solution there is to export a VIDEO_FORMAT value prior to executing devede (can be tested first in terminal).

---

### Post by woo10jw on 2012-02-10
NooB needs help. Read the thread & the solutions, but I'm confused about solution.

# export VIDEO_FORMAT=NTSC
# devede

haven't the foggiest about how to do this, any help appreciated.

fresh install 11.04 used devede 100 times with 10.04 no problems

---

### Post by Toz on 2012-02-10
To test to see if this fix works for you, open a terminal window and type in the command:
```
export VIDEO_FORMAT=NTSC
```
...to set the variable VIDEO_FORMAT, then enter in the same window:
```
devede
```
...to run the program. 

Devede will now open. Try to create a DVD and see if it works.

BTW, this has been reportedly fixed in the latest version of devede. Have you updated your system since the fresh install to get the latest versions of dvdauthor and devede? In the same terminal window, type in these commands to see which versions of dvdauthor and devede are installed:
```
apt-cache policy dvdauthor
apt-cache policy devede
```
...post back the results.

---

### Post by woo10jw on 2012-02-12
Stupid me put the # sign in the terminal the first time before I posted for help. I did what you said and it worked. Burnt 2 movies, 1 worked on old dvd player the other didn't. Both worked on new Phillips player & computers. Last cmd on fresh install is always update & upgrade
here is what you requested:

dvdauthor:
  Installed: 0.7.0-1
  Candidate: 0.7.0-1
  Version table:
 *** 0.7.0-1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/universe amd64 Packages
        100 /var/lib/dpkg/status

devede:
  Installed: 3.16.9-0ubuntu3
  Candidate: 3.16.9-0ubuntu3
  Version table:
 *** 3.16.9-0ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/multiverse amd64 Packages
        100 /var/lib/dpkg/status

Went to Devede downloaded ver 3.21.0 deb pkg tried to install thru software center this error came up (devede depends on ffmpeg (>= 4:0.7.2))
greyed out the install button

Do you have to do this everytime you use devede

---

### Post by Toz on 2012-02-12
> **woo10jw said:**
> Stupid me put the # sign in the terminal the first time before I posted for help. I did what you said and it worked. Burnt 2 movies, 1 worked on old dvd player the other didn't. Both worked on new Phillips player & computers. Last cmd on fresh install is always update & upgrade
here is what you requested:

dvdauthor:
  Installed: 0.7.0-1
  Candidate: 0.7.0-1
  Version table:
 *** 0.7.0-1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/universe amd64 Packages
        100 /var/lib/dpkg/status

devede:
  Installed: 3.16.9-0ubuntu3
  Candidate: 3.16.9-0ubuntu3
  Version table:
 *** 3.16.9-0ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/multiverse amd64 Packages
        100 /var/lib/dpkg/status

Went to Devede downloaded ver 3.21.0 deb pkg tried to install thru software center this error came up (devede depends on ffmpeg (>= 4:0.7.2))
greyed out the install button

Do you have to do this everytime you use devede

I guess the fix hasn't been backported to Natty.
Try adding:
```
export VIDEO_FORMAT=NTSC
```
...to the end of your ~/.bashrc file. Log out and back in again. Try running devede from the menu and see if it works.

---

### Post by woo10jw on 2012-02-13
I put export VIDEO_FORMAT=NTSC @ the end of the ~/.bashrc file, but it made no difference. Same error, it makes a .mpg file but no iso. If you go thru the terminal like you said everything is okay. Still don't know how to get the latest version of devede, update doesn't do it

Thanks for all your help.

---

### Post by Toz on 2012-02-13
Did you log out and back in again? If so, try this alternative procedure:

1. Open the devede.desktop for editing:
```
gksudo gedit /usr/share/applications/devede.desktop
```
2. Change the line:
> Exec=devede
...to read:
```
Exec=export VIDEO_FORMAT=NTSC;devede
```
3. Save the file and try again using the menu/launcher.

---

### Post by woo10jw on 2012-02-14
****> **Toz said:**
> Did you log out and back in again? If so, try this alternative procedure:

1. Open the devede.desktop for editing:
```
gksudo gedit /usr/share/applications/devede.desktop
```
2. Change the line:

...to read:
```
Exec=export VIDEO_FORMAT=NTSC;devede
```
3. Save the file and try again using the menu/launcher.

1. Yes I did log out and back in. 
2. I changed the line to:Exec=export VIDEO_FORMAT=NTSC;devede
3. Saved the file and when I opened devede thru the menu it gave error message: Could not launch 'DeVeDe' - Failed to execute child process "export" (No such file or directory) seems like you need to make a file someplace, but that is way above my head.
4. If I run devede thru the terminal it works

---

### Post by SeijiSensei on 2012-02-14
> **woo10jw said:**
> seems like you need to make a file someplace, but that is way above my head

In the Terminal, run the command "nano devede-fix" and an editor will open.  It has a convenient menu of commands at the bottom of the screen.  Now type:

```

#!/bin/bash
export VIDEO_FORMAT=NTSC
devede

```

Then use Ctrl-S to save the file and Ctrl-X to exit.

At the command prompt, type the command:

```
chmod a+x devede-fix
```

to make the file executable.  

Now follow the same steps you did before and make the Exec line read:

```
Exec=/path/to/devede-fix
```

replacing "/path/to" with the complete directory path to the program.  (If you followed the steps above, the file is probably in /home/username unless you chose to store it somewhere else.)

---

### Post by woo10jw on 2012-02-14
I followed your instructions SeifiSensei and everything worked fine, from the menu & terminal. I've never used nano before, tried 3 times & everytime I hit Ctrl-S it put .save on the end of devede-fix file. Then chmod couldn't find file or dir. So I just used gedit and created the file, wish I wasn't so dumb but I'm learning thanks to everyone on the forum.
Thanks Toz and SeijiSensei for all your help. much appreciated

By the way I emailed Devede and this was his reply.

"The problem is that you need Ubuntu 11.10, not 11.04, because Devede 3.21.0 needs the last version of FFMpeg."

This should answer some of the questions at the beginning of this post.

---

