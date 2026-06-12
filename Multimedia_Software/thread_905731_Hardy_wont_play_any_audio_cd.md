---
title: "Hardy wont play any audio cd"
date: 2008-08-30
forum: Multimedia Software
---

### Post by moyam01 on 2008-08-30
No matter what program I use, Hardy wont play any .wav file. I used many original commercial cd's and they just won't play. I have installed all the restricted format packages, and got all other formats to work, except this. 

Programs tried:

VLC 
Rhythm Box
Mplayer

---

### Post by moyam01 on 2008-08-31
any ideas?

---

### Post by moyam01 on 2008-08-31
Tried it again today, and got this message:

"Unable to mount Audio disc

Cannot connect to system bus"

---

### Post by wolfen69 on 2008-08-31
search synaptic for gstreamer and make sure you have it installed. there are 3 sets: good, bad, and ugly.

---

### Post by wolfen69 on 2008-08-31
post the output of```
cat /etc/fstab
```

---

### Post by moyam01 on 2008-08-31
the output:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=45c4b8c5-2e2a-4ce3-9201-5cbb15606acb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=bae0a309-f502-4f97-a5ba-c6415da72ad2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

Edit:

I also have Gstreamer installed.

I tried again this morning and it gave me this error:

Unable to mount Audio Disk

Cannot connect to system bus.


Then, I tried to put in another data cd, but it wouldn't mount

---

### Post by moyam01 on 2008-08-31
I was able to mount the data cd using the command:

sudo mount /dev/scd0 /media/cdrom0

But when I tried to to mount the audio cd, it gave me this error:

mount: you must specify the filesystem type

---

### Post by moyam01 on 2008-08-31
le bump

---

### Post by trash on 2008-09-03
I have the same problem on my laptop now, i think it started after i disabled automount for my usb devices. However, even though i can't mount the cd I can play it if i go through vlc.

On my server it won't even recognize the audio cd, i get the same errors as you if i try to mount it manually.

---

### Post by RGPerson on 2009-03-01
We have a similar problem. Just noticed it tonight. Or maybe it's related to the other night.

We tried watching a show on the internet but the sound was off.  No sound or sound that stuck in a loop.  We would pause that show and then try a wav file, anything, but there was no sound.  We had to reboot.  Then we were able to get sound again.

That worked for a few days until it happened to me again tonight. I came home to watch a CSI ep but the sound was off and funky again. This time, I tried an audio CD, which used to play just fine.

Now it says "unable to mount audio cd"

Funny thing is, you put a data cd in the same drive and it shows up with no problem.  Just not an audio CD

We're running 8.04 LTS and we're still fairly new.  We've run into little and big problems since we got this a couple of weeks ago.

We lost Nautilus awhile ago and I got it reinstalled. It's mostly behaving but it says it can't handle location: network.  I don't know if all this stems from the problem that led to the losing of Nautilus.  

But this is getting discouraging. Should we give up on 8.04. Should we give up on Ubuntu?  I think it's probably where the most support is when you do have problems so I think it's best to stay with Ubuntu, but really, I don't want a different problem like this every week.

Gabrielle
who also needs help with samba and ssh

---

