---
title: "raw1394 as a webcam"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by eldragon on 2007-11-08
skype2.0 with video support is out, and it works ok. but it takes the video input from a v4l device.

ive got a sony handycam hc32 dv camera which already works with kino, (can capture)...

i plan to use it as a webcam, is this possible? how can i bridge the raw1394 port and a video4linux port so that skype can see it.? ive searched the web for some help but nothing useful yet :(

thanks in advance

---

### Post by rickdog on 2008-01-02
I'm wondering abou the same thing. I have a sony dcr-trv19 and would like to use it as a webcam. Somebody must know something out there...

---

### Post by phyre-x on 2008-01-11
i've been trying to sort something out like this for a while, its tricky though as the device used for webcam is run by driver like v4l2 etc. To get the dv video to work you have to do something along the lines of this

 [http://ubuntuforums.org/showthread.php?t=606110](http://ubuntuforums.org/showthread.php?t=606110)

Hope it goes well

---

### Post by phyre-x on 2008-01-11
I might have a solution, posted here [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=664596](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=664596)

good luck !

---

### Post by bewo02 on 2008-01-19
> **eldragon said:**
> skype2.0 with video support is out, and it works ok. but it takes the video input from a v4l device.

ive got a sony handycam hc32 dv camera which already works with kino, (can capture)...

i plan to use it as a webcam, is this possible? how can i bridge the raw1394 port and a video4linux port so that skype can see it.? ive searched the web for some help but nothing useful yet :(

thanks in advance

Skype works with camcorders using dv4lstart from the dv4linux utilities, see  [http://dv4l.berlios.de](http://dv4l.berlios.de).

---

### Post by tetsuc on 2008-01-27
How excatly do you use dv4lstart? I have installed it, dv4l, and vloopback but can't seem to find the right combination of commands to get something working.

What worked for someone else was a simple
dv4lstart skype /dev/video0

but this doesn't seem to work for me - Skype loads fine and I can select the device in the video options but it is black (and I know it works, I can see myself through Kino).

I have also tried adding videodev and vloopback to the kernel via modprobe.... Just not sure what to try next. I should note that I also have an MSI TV@nywhere card that Skype seems to like using as its primary video device...

any help would be appreciated!

---

### Post by bewo02 on 2008-01-28
> **tetsuc said:**
> How excatly do you use dv4lstart? I have installed it, dv4l, and vloopback but can't seem to find the right combination of commands to get something working.

What worked for someone else was a simple
dv4lstart skype /dev/video0

but this doesn't seem to work for me - Skype loads fine and I can select the device in the video options but it is black (and I know it works, I can see myself through Kino).

I have also tried adding videodev and vloopback to the kernel via modprobe.... Just not sure what to try next. I should note that I also have an MSI TV@nywhere card that Skype seems to like using as its primary video device...

any help would be appreciated!

Skype doesn't work with vloopback as vloopback doesn't implement the 'select' system call properly.

Just do
dv4lstart skype
and click Options -> Video Devices 

Skype itself is beta and has trouble with more than one video device.
1. unload all video devs, including your tv card
2. run dv4lstart skype. It should show only the DV4linux device. Select it. The test should work. click 'apply'
3. exit skype
after the initial configuration, you should be able to run skype video even with
your tv card module loaded.

---

### Post by tetsuc on 2008-01-29
Thanks bewo02. I am trying to get this setup so that we can communicate with some people back in Germany...

I did as you directed
removed the TV@nywhere drivers - modprobe -r cx88-blackbird (and all of the other modules for the conexant video driver starting with cx88 )
checked to make sure that skype could not see the card (ran skype, checked the video options)
but when I dv4lstart skype I don't get any choices for video.

Perhaps I have missed some of my other video modules...? I am not sure how to find which other ones are installed and that I can take out (modprobe -l doesn't give me the currently installed modules, as I thought it would and modconf isn't as self explanatory as I had hoped).

Cheers!

---

### Post by bewo02 on 2008-01-29
> **tetsuc said:**
> 
..but when I dv4lstart skype I don't get any choices for video.


Ah, OK, looks like a general problem with LD_PRELOAD. You don't
need any video modules other than those needed for firewire
(check if kino or ekiga detect your camcorder).

try
   dv4lstart ls -l /dev/video0
you should see something like
crw-rw---- 0 root video 81, 10 Jan  1  1970 /dev/video0
If you see something different, LD_PRELOAD is disabled on your machine.
Do you run SELinux?

if ls -l /dev/video0 works, check if you have a group 'video' and if you're member of it.

Check if
    ldd `which skype`|grep libc| wc -l
prints '1'. If it shows '0', you have a statically linked libc, which means that
dv4lstart can't work. 

Check if skype has an 's' bit set. Go to the directory that contains the skype binary,
run ls -l skype. Does it look like
-rwxr-xr-x 1 root root 20429924 Dec  2 14:45 skype
or like
-rwsr-xr-x 1 root root 20429924 Dec  2 14:45 skype
?

---

### Post by tetsuc on 2008-01-29
> **bewo02 said:**
> Ah, OK, looks like a general problem with LD_PRELOAD. You don't
need any video modules other than those needed for firewire
(check if kino or ekiga detect your camcorder).

try
   dv4lstart ls -l /dev/video0
you should see something like
crw-rw---- 0 root video 81, 10 Jan  1  1970 /dev/video0

if ls -l /dev/video0 works, check if you have a group 'video' and if you're member of it.

Check if
    ldd `which skype`|grep libc| wc -l
prints '1'. If it shows '0', you have a statically linked libc, which means that
dv4lstart can't work. 

Check if skype has an 's' bit set. Go to the directory that contains the skype binary,
run ls -l skype. Does it look like
-rwxr-xr-x 1 root root 20429924 Dec  2 14:45 skype
or like
-rwsr-xr-x 1 root root 20429924 Dec  2 14:45 skype
?

Thanks for giving me some hope!

I am running Ubuntu GG (7.10) -- all up to date
I booted up, removed all of the cx88* modules, turned on my dvcam, and tried your steps

chris@princess:~$ dv4lstart ls -l /dev/video0
ls: /dev/video0: No such file or directory
crw-rw---- 0 root video 81, 10 1969-12-31 19:00 /dev/video0

and I am a user of video. Tthough it is strange because this does not show up in Ubuntu's GUI groups settings and when I run Kino it tells me it can't detect the raw1394 device... However, running kino as superuser appears to work ok (though I could swear that the quality seems to be lower than it was before I started messing around with this...) --> could this be the issue?
chris@princess:~$ groups
chris adm dialout cdrom floppy audio video plugdev scanner netdev lpadmin powerdev admin fuse vboxusers

chris@princess:~$  ldd `which skype`|grep libc| wc -l
1
Why would weither or not I have a statically linked libc make a difference?

and.... the 's' bit is not set
chris@princess:~$ !ls
ls -al /usr/bin/skype
-rwxr-xr-x 1 root root 13929332 2008-01-05 13:02 /usr/bin/skype

Mucho gracias!

note: dmesg ieee messages
[ 1068.453809] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0800460101bb507a]
[ 1068.453850] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 1068.513755] ieee1394: raw1394: /dev/raw1394 device initialized
[ 1068.534101] NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release. Use raw1394 instead.

---

### Post by bewo02 on 2008-02-03
Sorry for the delay. Can't see irregular things in your output.
Put your TV driver module back as it was before.

Some thing I noticed with Skype:
- when changing the video device, skype doesn't really change it. one has to
select/deselect some box (eg "enable skype video"), so that the "Apply" button
becomes active. Clicking "Apply" activates the change and clicking "Test" works.
- In some rare cases, the Skype video test shows only a black screen. My
suspicion is that running mplayerTV before has something to do with it, but
I'm not sure.

---

### Post by tetsuc on 2008-02-09
Thanks again for the help. I still haven't been able to get it to work... 

The new version of skype released earlier this month (2.0.43) looks a bit better - it gives me the option to select "previous webcam not detected" from /dev/video1 in addition to the TVTime card at video0. When I run it with dv4lstart it just gives me the "previous webcam not detected (/dev/video1)"

could it be a problem with permissions? I have added myself to the video group and when video0 exists it is listed as owned by root and video but... I don't have an entry for video0 or video1 in /etc/udev/rules.d/40-permissions.rules

Chris

---

