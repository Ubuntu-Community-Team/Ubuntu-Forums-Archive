---
title: "copy problem with creative zen vision:M"
date: 2008-06-13
forum: Multimedia Software
---

### Post by coreofreeality on 2008-06-13
i know i created another thread, its kinda irrelevant now

ok, i downloaded and installed libmtp and mtpfs, and got it to work quite nicely. i mounted my zen and copied it over, but it only got so far before it stopped and said there was an error while copying. i am new to linux, so does anyone have any tips about where to start debuging?

---

### Post by Seamyst on 2008-06-13
I had the same problem when first copying music over to my Creative Zen.  I solved it by only copying over three or four albums' worth at a time, letting those copy, then clearing the queue and going on to the next batch.  It's a pain, but they all copied over that way.

---

### Post by coreofreeality on 2008-06-16
yeah, i guess i'll have to do it that way

i was hoping there was a way to stop the errors.

oh well. thanks

---

### Post by hoatu on 2008-06-19
Hey,

How did you mount your zen? I'm having absolute hell trying to mount mine - I can't automount, and although I'm adverse to messing with fstab I have no idea how I specify the zen for the mount!

Cheers

hoatu

---

### Post by coreofreeality on 2008-06-30
this may be a little late, but you download both mtpfs and libmtp, which you can find using synaptic, after you've installed them, create a directory to use as a mountpoint (it usually has to be empty unless you use options) and then use:

lsusb

in the terminal to make sure ubuntu knows the zen is connected. if it is, use:

mtpfs <mountpoint directory>

i use a directory called ZEN in my home dir, so i use : mtpfs ./ZEN
and that should mount it just like any other local disk.

you shouldnt have to restart after installing mtpfs, but if it dosent work, that may be a good place to start.

it works, but its not problem free, i've found problems with unmounting and copying large ammounts of data.

EDIT:
i found a bug report detailing the same thing([https://bugs.launchpad.net/ubuntu/+source/libmtp/+bug/181977]("https://bugs.launchpad.net/ubuntu/+source/libmtp/+bug/181977")), and the report said it didnt happen under command line, like cp, so i think i'll be doing that

---

