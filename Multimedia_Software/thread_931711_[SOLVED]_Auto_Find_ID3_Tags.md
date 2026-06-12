---
title: "[SOLVED] Auto Find ID3 Tags"
date: 2008-09-27
forum: Multimedia Software
---

### Post by AmbiguousOutlier on 2008-09-27
Hi, I have a large library of music with inconsistent tags, is there an app that will search the net and replace them. Or something that I can manually go through and change them in a batch type job?

---

### Post by mihaiv on 2008-09-27
Try kid3. It has a nice gui where you can simultaneously edit multiple files. You can also retrieve the tags from a few online databases.
```
sudo apt-get install kid3
```

---

### Post by AmbiguousOutlier on 2008-09-28
I found picard which did half of the tags. And I've now manually gone from half of the others. So I'm a little to afraid to try that now incase in it undoes all my hard work. 

Another thing though, a lot of the tracks are locked so I can't edit them. Any ideas why that is?

---

### Post by davidryder on 2008-09-28
I have tried a few of them and I liked Easy Tag the most. It takes a little getting used to but IMO has the simplest interface.

---

### Post by mihaiv on 2008-09-28
> **RhysGM said:**
> So I'm a little to afraid to try that now incase in it undoes all my hard work. 

You can make a backup copy first. Anyway kid3 won't save any modifications until you press the save button.
> **RhysGM said:**
> 
Another thing though, a lot of the tracks are locked so I can't edit them. Any ideas why that is?
Do you have all the music in one place? Maybe some of it is on a readonly mounted drive.

---

### Post by AmbiguousOutlier on 2008-09-28
It was on a usb drive, but picard wouldn't read it, so i coppied most of it onto the c: drive. It's all under the music folder, which allows to create and delete files.

---

### Post by davidryder on 2008-09-28
You could have changed the permissions on the USB drive - which was likely the problem...

---

