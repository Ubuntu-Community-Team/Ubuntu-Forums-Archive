---
title: "tvtime can it use a v4l capture device avc-2010"
date: 2009-10-11
forum: Multimedia Software
---

### Post by sdowney717 on 2009-10-11
i wanted to try it out. but it does not work. 
I can use vlc to capture and reord to mpg 

vlc /dev/video0 captures the video and audio.

tvtime /dev/video0 gives me a blue screen, and says no signal, no video source, 

ivtv invalid argument, can not open capture device /dev/video0

seeing that card is a v4l capture card does this mean that tvtime is not a v4l application?

> scott2@scott2-desktop:~$ tvtime /dev/video0
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/scott2/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/scott2/.tvtime/tvtime.xml: Permission denied.
videoinput: Card failed to allocate capture buffers: Invalid argument
I/O error : Permission denied
I/O error : Permission denied


if i try to configure thru the gui and select video source, it never gives me any options

---

### Post by lovinglinux on 2009-10-11
You need to make sure the card is properly detected at startup.

This is how I did it: [http://ubuntuforums.org/showpost.php?p=5971890&postcount=2](http://ubuntuforums.org/showpost.php?p=5971890&postcount=2)

---

### Post by saedelaere on 2009-10-29
> **sdowney717 said:**
> i wanted to try it out. but it does not work. 
I can use vlc to capture and reord to mpg 

vlc /dev/video0 captures the video and audio.

tvtime /dev/video0 gives me a blue screen, and says no signal, no video source, 

ivtv invalid argument, can not open capture device /dev/video0

seeing that card is a v4l capture card does this mean that tvtime is not a v4l application?



if i try to configure thru the gui and select video source, it never gives me any options

You could try [TV-Viewer]("http://home.arcor.de/saedelaere/index_eng.html"), please let me know if it works with your device!

Regards

---

### Post by sdowney717 on 2009-10-30
hi, i downloaded activetel and the installer put it in opt
but i still get an error installing tv-viewer 
is active tel installed in the wrong place?

> scott@scott-desktop:~/tv-viewer-0.7.7$ ./tv-viewer_install.sh
Program error. You'll need Tcl version 8.5 or higher.

Found version: 8.4.19
Have a closer look to the user guide for the system requirements.
If you've installed more than one version of Tcl, the symlink wish
might not point to the correct location.
/usr/bin/wish is pointing to:
/etc/alternatives/wish



> 
scott@scott-desktop:~/ActiveTcl8.5.7.1.291226-linux-ix86-threaded$ sudo ./install.sh
_____________________________________________
Launching graphical installer on :0.0
...
scott@scott-desktop:~/ActiveTcl8.5.7.1.291226-linux-ix86-threaded$ 


---

### Post by saedelaere on 2009-10-31
> **sdowney717 said:**
> hi, i downloaded activetel and the installer put it in opt
but i still get an error installing tv-viewer 
is active tel installed in the wrong place?

Hi,

first of all you should try the latest beta, it is worth it. Second you can install Tcl/Tk 8.5 via synaptics.
If you have more than one Version installed of Tcl you must make sure the symlink wish points to wish8.5 and not wish8.4
So first of all install Tcl via Synaptics then run 

```
sudo update-alternatives --config wish
```

And change the symlink to wish8.5

then you should be able to install TV-Viewer 0.8.1b1....

Regards

---

### Post by eliofall on 2009-11-02
hey i'm having the same problem but i cant find how to change the symlink.

i installed TCL 8.5 

just tried runing 

sudo update-alternatives --config wish
No alternatives for wish.

this card is givinig me so muh trouble i'm not sure what to do

---

### Post by sdowney717 on 2009-11-02
you can use the card with VLC
and you can record video streams as mpg files

simply run it like this from commandline
if your card is dev video0 then type
vlc /dev/video0

select view advanced controls and you will get a record button
if you try open capture device from the vc menu it wont work because it is a bug that got fixed in debian and i dont know when they will get around to it.

(the video goes in svideo port)

---

### Post by doogiekd on 2011-01-10
thank you saedelaere!

tv-time was not opening from the menu.


i had two version of tcl installed and changed the the symlink to use 8.5 instead of 8.4.

tv-time now opens.

thank you!

---

