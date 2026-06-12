---
title: "Ubuntu 11.10 new kernel and Handbrake"
date: 2011-11-05
forum: Multimedia Software
---

### Post by mym2f on 2011-11-05
Hi everyone ....
 
I wonder if you can help me with Ubuntu 11.10 gnome version since I kind of new to linux and about half of the cool software did not work.

I followed the instructions specified at Official Ubuntu Documentation Website and in YouTube videos but no good resutls achieved.

These are two programs that I could not install successfully:

Kdenlive === Video Editing Software === failed bcuz MLT's SDL module problem

Handbrake ==== Video Conversion Software.

Thank you

---

### Post by wolfen69 on 2011-11-06
Handbrake:
```
sudo add-apt-repository ppa:stebbins/handbrake-snapshots

```
then
```
sudo apt-get update
```
then
```
sudo apt-get install handbrake-gtk ffmpeg
```


How did you try installing kdenlive?

---

### Post by TXPhisher on 2011-11-06
This worked for me.  Thanks for the help!  Now I need to work on a method for handbrake to monitor a folder and automatically convert any videos I drop in to the iPad preset :popcorn:

---

### Post by mym2f on 2011-11-07
Thank you very very very much wolfen69 .............. ;) :D

Handbrake installation was successful .... It appears that I added a wrong ppa (I previously tried handbrake-releases instead of -snapshots).

Kdenlive newest version (31-10-2011) worked as well following the instuctions

[http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages](http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages)

(Installation from a Terminal) ..... :D

I hope this thread will help others ....

---

### Post by marty331 on 2011-11-08
Was trying to download handbrake in 11.10 over the weekend, just found this thread and tried it, it WORKED!  Thanks guys!

---

### Post by Nakhoda ASAD on 2011-11-11
thank you so much
it totally worked

---

### Post by slick666 on 2011-12-23
Thanks for posting this. It helped me out a lot.

---

### Post by Derathor on 2011-12-25
Thank you very much. Worked for me too.

Cheers. :popcorn:

---

### Post by pchongdo on 2012-01-29
Thank you very much! This will help!

---

### Post by 2912pwil on 2012-01-30
Thanks wolfen, worked for me too!!! (& I'm only 64 yrs old...)

---

### Post by AllGamer on 2012-02-06
Thank you OP

that solution worked for me :D

however i'm on Linuxmint 12

---

