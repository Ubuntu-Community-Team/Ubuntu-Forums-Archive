---
title: "can't burn a video DVD in brasero"
date: 2009-11-14
forum: Multimedia Software
---

### Post by samsamros on 2009-11-14
I tried for the first time to burn a video DVD and I get the following (the image) I use ubuntu 9.10. I tried with both normal and dual layer DVDS and nothing.[IMG]http://i705.photobucket.com/albums/ww59/samsamros/Screenshot-1-2.png[/IMG] Thank you very much in advance

---

### Post by conradin on 2009-11-19
HEYY!!!! SAME Problem Here!

---

### Post by conradin on 2009-11-19
Ok Before I start freaking out, how about staying calm?
What we can do is look in the synaptic package manager for brasero plugins

Im also going to install the DVD r+w debug tools and see what that gets me.


Also i just read K3B works for other users. I use it on my RHEL5 computer.
Try some of those, I guess, Ill post back if mine works.

---

### Post by conradin on 2009-11-19
Ok, so i tried installing plugins and other burners, that didnt work.
So i typed 
```

mount -a           
gksudo gedit /etc/fstab &
ls /dev/s*
ls /dev/c*

```

Then i looked for my CDROM Device. 
$ sudo mount /dev/cdrw3 /media/fck
mount: /dev/sr0: unknown device
$ sudo mount /dev/cdrom3 /media/fck
mount: /dev/sr0: unknown device

So Then i tried:
```

$ ls -l /dev/ | grep cdrom
lrwxrwxrwx  1 root root           3 2009-11-19 00:12 cdrom3 -> sr0
crw-rw----  1 root cdrom    21,   2 2009-11-19 00:12 sg2
brw-rw----+ 1 root cdrom    11,   0 2009-11-19 00:12 sr0


```

not really sure where to go after that.
Can anyone give some assistance?

---

### Post by samsamros on 2009-11-22
well I continue to have problems I also tried the Kb3 and nothing it gives me another error... it sucks 
If anybody else knows anything regarding this issue please feel free to give suggestions... I tried the plug ins for brassero and it didn't work :S

---

### Post by conradin on 2009-11-22
Hey all, I solved My problem. It turns out my burners can only handle single layer DVDs.

---

### Post by nmyrick on 2009-11-30
To the developers of Brasero,

I think it is a software design issue with Brasero.  I have the same issue and I think that the software must know what plugins I need, since it says that "I cannot burn the files with the current set of plugins". It just isn't telling me.

---

