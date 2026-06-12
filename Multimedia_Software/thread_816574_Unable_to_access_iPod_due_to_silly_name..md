---
title: "Unable to access iPod due to silly name."
date: 2008-06-02
forum: Multimedia Software
---

### Post by Trampis on 2008-06-02
I got an ipod from a freind who has named it "Moira's Classic ipod"

I cannot add anything to the ipod becouse it is read only. 

I tried chmod +w /media/ipod with no success (there is no /media/ipod it is /media/Moira's Classic Ipod)
so I do chmod +w /media/Moira's Classic iPod, with predictable results, the spaces in the name mess everything up.
```
chmod: cannot access `/media/Moiras Classic iPod\n\nchmod +w /media/Moiras': No such file or directory
chmod: cannot access `Classic': No such file or directory
chmod: cannot access `iPod': No such file or directory

```

I can't change the name, it is read only, Is there a way to get around this from my machine (only running hardy no partition)?

My iPod is a first or second generation 20g. It has also been used exclusively on a Mac prior to this( i hear there is an issue with journaling?)

---

### Post by jackocleebrown on 2008-06-02
Hello,

To use spaces in the path from the command line you can either use quotes:
```
"/media/Moira's Classic iPod"
```
or backslashes:
```
/media/Moira's\ Classic\ iPod
```

The tab key is very helpful for this too, enter the first part of the path and press tab, it will help fill in the rest for you.

Also, you will probably need to use sudo in front chmod to get it to work.

Not familiar with Ipod's, can you use them just like a external disc then?

Good luck.

---

### Post by ChameleonDave on 2008-06-02
> **jackocleebrown said:**
> 
or backslashes:
```
/media/Moira's\ Classic\ iPod
```

You would need to escape the apostrophe too:

```
/media/Moira\'s\ Classic\ iPod
```

---

### Post by Trampis on 2008-06-05
Thanks a lot for the help thus far, adding the slashes or using tabs allowed me to access the iPod, name be damned, however, using
chmod +rw or sudo chmod +rw or sudo chmod ug+rw does not change the read or write attributes, i get the message:

```
 sudo chmod +rw -R /media/Moira\'s\ Classic\ iPod/
chmod: changing permissions of `/media/Moira\'s Classic iPod/': Read-only file system

```
obviously it is a read only file system, I am trying to change that. Am I doing something wrong?

---

### Post by ChameleonDave on 2008-06-05
> **Trampis said:**
> 

```
 sudo chmod +rw -R /media/Moira\'s\ Classic\ iPod/
chmod: changing permissions of `/media/Moira\'s Classic iPod/': Read-only file system

```
obviously it is a read only file system, I am trying to change that. Am I doing something wrong?

Well, there are two things here.  One is that the drive and its contents may be flagged so as not to give you write access; you can change this with "chmod".  The other is that the whole file system for the drive may be read-only; you know, like a CD-ROM.

If you type "mount" at the command line, you should see whether the drive is mounted as "r" or "rw".  I presume that you either need to mount it manually with different arguments, or undo some sort of lock on the iPod itself.

---

### Post by banjobacon on 2008-06-05
I was having the same problem with a used iPod I purchased. The solution was to restore the iPod using iTunes. I can now write files to my iPod without any problem. If you don't have a Windows installation, you can try running iTunes with Wine. Or you can ask your friend to restore the iPod for you.

---

