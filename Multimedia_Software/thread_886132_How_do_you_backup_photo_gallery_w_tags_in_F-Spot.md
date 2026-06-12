---
title: "How do you backup photo gallery w/ tags in F-Spot?"
date: 2008-08-10
forum: Multimedia Software
---

### Post by SlaughterDog on 2008-08-10
So I've got a bunch of pictures in F-Spot, all tagged and organized. They're all JPEG I think. 

Let's say I want to re-format. I *could* just make backups of my Pictures folder. But when I re-import them to F-Spot, won't I have to re-tag them all?

Is there any way to make a backup gallery so I don't have to re-tag and set tag icons again?

---

### Post by SlaughterDog on 2008-09-28
Well it's nearing time for me to make a backup. Am I really going to have to re-tag everything? At some point in time, I enabled metadata writing in F-spot, so some photos were imported before that, and some after.

---

### Post by zasf on 2009-08-02
According to [f-spot faqs]("http://f-spot.org/FAQ") you need to copy F-Spot database, which is normally placed in ~/.gnome2/f-spot/photos.db

What I'm doing is to place f-spot base folder in ~/Photos so that I can easily backup just that folder and save both pictures and tags.

To run f-spot with a different base directory:
```
matteo@burnt:~$ f-spot -b Dropbox/Photos/.f-spot/
```

I'm currently syncing the folder on another computer via dropbox and will report shortly if it works.

---

### Post by zasf on 2009-08-02
I just finished syncing the folder on another computer via dropbox and it works.

---

### Post by maxpathan on 2010-07-08
Question: I have f-spot on Ubuntu 8:04. If I upgrade to ubuntu 10:04 can I copy the fspot database from the old install to the new and will it be compatible??

Regards

---

### Post by xyepblra on 2013-04-07
Matteo, could you please specify the practical meaning of the [command you executed]("http://ubuntuforums.org/showthread.php?t=886132&p=7720222#post7720222")? Did you save the f-spot tags library to the Dropbox folder containing a backup of your photos?
Do you think it is possible to configure f-spot to use ~/Dropbox/Photos/ as default folder?

---

### Post by oldos2er on 2013-04-07
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

