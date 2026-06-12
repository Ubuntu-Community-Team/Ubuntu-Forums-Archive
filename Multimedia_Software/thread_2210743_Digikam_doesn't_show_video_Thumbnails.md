---
title: "Digikam doesn't show video Thumbnails"
date: 2014-03-12
forum: Multimedia Software
---

### Post by davidvandoren on 2014-03-12
Hi!
I am on Ubuntu 12.04 and installed Digikam 2.5.0
Mplayerthumbs are installed but still, the thumbs don't show any preview image.
The video playback works fine.
Searching google for hours didn't deliver any help.

So did anyone here get this working?
thanks!

---

### Post by 23dornot23d on 2014-03-12
Hi David ....... I am not sure about what is needed to get the thumbnails working in 12.04 for video - but just to let you know the thumbnails for videos in 3.5.0 of Digikam work ... but I had to log out of it and back in again as it hung on the videos to start with.

Now all is well though ......... but as far as I know I did not load anything special in .......... although I do run kdenlive as well so whether that application brings in more things in for videos and thumbnails ......... or if its just that I am running a later version.

---

### Post by davidvandoren on 2014-03-12
Thanks!
I installed KDenlive just now since I use it anyway, didn't help with the thumbnails though.

How did you get version 3.5.0?
Did you install it from source?

---

### Post by 23dornot23d on 2014-03-12
I am playing around with the new version of Ubuntu 14.04 .... and it just downloaded as that version.

Thought I would just check it out while its in testing ...... to see if that problem you mentioned still existed and it

seems not to ......... here is a quick video I just did ......... 

[http://youtu.be/aF08obydXKY](http://youtu.be/aF08obydXKY)

seems pretty quick too .

---

### Post by davidvandoren on 2014-03-12
Thanks I got it working.

Here is what I did. Please let me know if this is recommendable.
Opened synaptic package manager ...settings  ....repositories and added there

```

ppa:kubuntu-ppa/backports
```
reloaded the index and upgraded Digikam to version 3.2.0
It pulled a bunch of dependencies and upgraded some packages.
everything works great so far.

Question 

should I remove the  ppa:kubuntu-ppa/backports now or will it work fine with future updates.
Or was that a bad idea to begin with?

---

### Post by 23dornot23d on 2014-03-12
I am just another user testing things ....... but what you did seems ok

to be sure not to keep loading and mixing things up - just disable the ppa if you are at all
concerned it may mess anything up ......... but I often use ppa's then as soon as I have 
what I need - I disable the ppa by un-ticking it in synaptic repositories.

Glad you got it working ok ......

---

### Post by davidvandoren on 2014-03-12
Yeah! After checking the update-manager, I already unchecked the ppa, since the update-manager had a lot of updates and gave me a warning that only a partial update was possible.
So I unchecked it. Now, I can only see a hand full of security updates.

---

### Post by monkeybrain20122 on 2014-03-12
It works with digikam 3.5 on Ubuntu 13.10 as well. I installed from a ppa.

---

### Post by 23dornot23d on 2014-03-13
Good to see its working in 13.10 as well - there used to be a problem with vast numbers of photos ........ my collection
is well over 40,000 now and it used to struggle - but this time it seems to have read them all in and created thumbnails
for everything ........ takes some checking though ........ but now I can quickly browse through them all to find something
that suits what I need .......... 

Getting better all the time ....... there used to be a time when I had to use another OS for this - but not anymore.

---

