---
title: "Sound Issues"
date: 2010-10-02
forum: Multimedia Software
---

### Post by AHayes88 on 2010-10-02
I installed the newest version of Ubuntu Netbook Remix. Initially sound was playing through the speakers, but not working when I plugged in head phones. I did a little googling and tried a few things, nothing too serious though. I installed ALSA Mixer and PulseAudio Preferences.

Neither of those did anything helpful.

Anyway, I'm using a Toshiba NB255-N250.
aplay -l tells me:
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
Subdevices: 0/1
Subdevice #0: subdevice #0

Ideally I'd like to get at least the speaker working again, but if you all could help me to get the headphones working as well that'd be great!

[Edit] Alright, I reinstalled adobe flash and that seems to have fixed the speaker issue. Headphones still don't work.

---

### Post by fuse_Man91 on 2010-10-02
I'm also having the same issues. I also installed ALSA Mixer and the Pulse Audio programs and I can't get the sound to come out through the headphones. I also have a Toshiba (Satellite A660). Maybe it's a Toshiba driver issue?

---

### Post by lidex on 2010-10-02
Both of you do this please. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by fuse_Man91 on 2010-10-02
I tried that but I got the message "alsa-info.sh: No such file or directory."

---

### Post by lidex on 2010-10-02
> **fuse_Man91 said:**
> I tried that but I got the message "alsa-info.sh: No such file or directory."

Dude, you're bringing me down :(
So either the file didn't download or downloaded to a non-default location. Is it in your user folder?

---

### Post by fuse_Man91 on 2010-10-02
Sorry about that.... Haha it was my fault I typed in also-info.sh so it saved the file as that rather than alsa-info.sh soooooooo....
 
Heres the link:
[http://www.alsa-project.org/db/?f=b770deb9bcbf0d80e65219fa0143387bb7c8475e](http://www.alsa-project.org/db/?f=b770deb9bcbf0d80e65219fa0143387bb7c8475e)

---

### Post by lidex on 2010-10-02
> **fuse_Man91 said:**
> Sorry about that.... Haha it was my fault I typed in also-info.sh so it saved the file as that rather than alsa-info.sh soooooooo....
 
Heres the link:
[http://www.alsa-project.org/db/?f=b770deb9bcbf0d80e65219fa0143387bb7c8475e](http://www.alsa-project.org/db/?f=b770deb9bcbf0d80e65219fa0143387bb7c8475e)

First upgrade your alsa install via the link in my sig. Post your results.

---

### Post by fuse_Man91 on 2010-10-02
Another stupid question... Where is the link? I'm not sure what your sig is... I'm a big noob haha :(

---

### Post by lidex on 2010-10-03
> **fuse_Man91 said:**
> Another stupid question... Where is the link? I'm not sure what your sig is... I'm a big noob haha :(

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

FYI: sig = signature, located at the bottom of a post.

---

### Post by AHayes88 on 2010-10-03
I have to say, I'm extremely new to this, so please bare with me here. I wanted to try something other than windows 7 on my netbook.

How do I run the alsa info script?

---

### Post by lidex on 2010-10-03
> **AHayes88 said:**
> I have to say, I'm extremely new to this, so please bare with me here. I wanted to try something other than windows 7 on my netbook.

How do I run the alsa info script?

Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by fuse_Man91 on 2010-10-03
[http://www.alsa-project.org/db/?f=1b41a1ea99b7ef981ea819d14a5f8e20d9d888f6](http://www.alsa-project.org/db/?f=1b41a1ea99b7ef981ea819d14a5f8e20d9d888f6)

---

### Post by AHayes88 on 2010-10-04
[http://www.alsa-project.org/db/?f=b4f32d50a3adf60b80aaee725526439d243652f9](http://www.alsa-project.org/db/?f=b4f32d50a3adf60b80aaee725526439d243652f9)

---

### Post by fuse_Man91 on 2010-10-04
I just tried the headphone jack out today and it works! Thanks lidex!

---

### Post by chesterlinux on 2010-10-04
I also have a ubuntu Toshiba netbook 255-450 and I cannot get my headphone jack to work at all very frustrating.
This is my link

[http://www.alsa-project.org/db/?f=b3a84842a0e878cd49444fa3ac5af27ad74bf73f](http://www.alsa-project.org/db/?f=b3a84842a0e878cd49444fa3ac5af27ad74bf73f)

Any Help would be greatly appreciated!

---

### Post by lidex on 2010-10-05
*chesterlinux & AHayes88*
Follow the link in my sig to update your alsa installs to 1.0.23

---

### Post by chesterlinux on 2010-10-05
Well I performed the steps listed in your link but I still seem to have the older version when I check the terminal and the problem persists.  What do I do?

---

### Post by lidex on 2010-10-05
> **chesterlinux said:**
> Well I performed the steps listed in your link but I still seem to have the older version when I check the terminal and the problem persists.  What do I do?

Make sure to uninstall alsa-backports first. Then try again.

---

### Post by AHayes88 on 2010-10-06
> **lidex said:**
> *chesterlinux & AHayes88*
Follow the link in my sig to update your alsa installs to 1.0.23

I was actually checking that out before, and downloaded the files and such. The step where it says to type in cd <download-directory> what is it looking for there? I've got the .tar files downloaded to my download folder, and I even tried extracting and copying the files to my documents. 

Thanks again for helping me.

Alright so after some reading I've been trying:
cd /<name>/downloads

But it doesn't work. How badly am I failing at this?

---

### Post by lidex on 2010-10-06
> **AHayes88 said:**
> I was actually checking that out before, and downloaded the files and such. The step where it says to type in cd <download-directory> what is it looking for there? I've got the .tar files downloaded to my download folder, and I even tried extracting and copying the files to my documents. 

Thanks again for helping me.

Alright so after some reading I've been trying:
cd /<name>/downloads

But it doesn't work. How badly am I failing at this?

Probably easiest to just follow the directions given exactly.
The cd command moves you to the directory specified. If you downloaded files to ```
~/Downloads
```you would cd to that:
```
cd ~/Downloads
```

---

### Post by AHayes88 on 2010-10-08
Thanks! That fixed it.

I actually tried that cd ~/Downloads command, but.. I typed downloads, not Downloads. 

Thanks again.

---

