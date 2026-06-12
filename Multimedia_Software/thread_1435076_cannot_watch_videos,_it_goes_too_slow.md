---
title: "cannot watch videos, it goes too slow"
date: 2010-03-21
forum: Multimedia Software
---

### Post by abelito8 on 2010-03-21
Hi there, 

I have Kubuntu 9.10 on an Acer Aspire One 160 GB HDD 

I had a problem with games for the system got stuck when trying to start supertux. Now I noticed that I cannot even watch videos. I have VLC installed but when I play the feature it does not go fast enough (so it basically shows a number of photograms rather than a movie)

the video card should be ok for I have a partition and in windows works 

any help?

---

### Post by ashu. on 2010-03-21
its not a problem of the os or hardware but platforms.all videos are native to windows as they are mostly of .avi,.mkv,or.flv etc so making it run on ubuntu or kubuntu ,or any other linux is using external codecs.in most of the cases it works but some are exceptions so try playing exceptions in windows.if every video u play is having problems then try repairing the packages using recovery mode or remove all n try installing all the external codecs.it might work then

---

### Post by abelito8 on 2010-03-21
I have Ubuntu 9.04 installed on my main computer and all those videos work fine with it so it is something related either to Ubuntu 9.10 (but such a bug for videos is unlikely...too big not to be noticed) or to my personal settings

---

### Post by themusicalduck on 2010-03-21
I have Ubuntu 9.10 installed on an Acer Aspire One and don't have these problems at all.

Although it isn't a particularly powerful netbook. If the videos you are trying to play are in HD then it might be choppy. DVD quality should be fine though. Also, Kubuntu is a bit heavier than Ubuntu which might slow things down further.

If you run this in a terminal ```
lspci | grep VGA

``` then you can find out exactly what graphics hardware you have and search to see if it has any specific problems with Kubuntu.

---

### Post by abelito8 on 2010-03-21
Thanks, in the end I was pretending too much from this little aa1, it works fine if I run the movie from the internal HDD but from the external it does

and you're right, kubuntu is too heavy...I notice only now I used the wrong name, I have xubuntu for the problem you were talking about

---

