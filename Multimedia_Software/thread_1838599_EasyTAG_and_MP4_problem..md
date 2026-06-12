---
title: "EasyTAG and MP4 problem."
date: 2011-09-03
forum: Multimedia Software
---

### Post by mabo5184 on 2011-09-03
Hi,

I have been having problems with editing MP4 tags and I was hoping someone could suggest what I may doing wrong.

I have installed EasyTAG 2.1.6-1ubuntu1 and it works fine with MP3 files but it does not recognize MP4 files. All the dependencies are installed and I have also loaded a number of other packages.

For example I have installed all the recommended packages mentioned in this "Sticky: [all variants] Comprehensive Multimedia & Video". I have also installed libmp4V2-0 which did not help.

Here are the details on an example file;
$ file 01\ -\ I\ Shot\ The\ Sheriff 
01 - I Shot The Sheriff: ISO Media, MPEG v4 system, iTunes AAC-LC

I'm using ubuntu 11.04 with gnome3 desktop.

Regards
Marc

---

### Post by Lampi on 2011-09-04
there used to be a package called easytag-aac with builtin aac support

---

### Post by ron999 on 2011-09-04
> **mabo5184 said:**
> Hi,
I have been having problems with editing MP4 tags ...

I have installed EasyTAG 2.1.6-1ubuntu1 ...

I'm using ubuntu 11.04 with gnome3 desktop.


Hi
For Ubuntu 11.04 there are two versions of EasyTag provided.
One is:-
**easytag**
The other is:-
**easytag-aac**

For mp4 support you need to use the other version.

Do this:-
```
sudo apt-get remove easytag
```
Then:-
```
sudo apt-get install easytag-aac
```

---

### Post by mabo5184 on 2011-09-04
I just removed easytag and then installed easytag-aac, but unfortunately it still does not work?

It's very strange because I can play audio files with rhythmbox.

Thanks for the suggestion anyway.

---

### Post by mabo5184 on 2011-09-04
Another question?

I found this bug #196089 "ID3v2.3 tag writing support missing". 

Do you think this may be my problem?

---

