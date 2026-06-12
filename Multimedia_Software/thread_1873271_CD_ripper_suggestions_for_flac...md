---
title: "CD ripper suggestions for flac.."
date: 2011-11-01
forum: Multimedia Software
---

### Post by Baldrick_NZ on 2011-11-01
Hi all,

Can anyone suggest a really good cd ripper that encodes to flac please?

I have been using sound juicer, but many tracks have artefacts through them. Asunder seems to do the trick, but speed doesn't seem to be consistent, it's either really, really unbearably slow or about right. Asunder also doesn't remember where you want to encode your files to after you close the app.

I really want something I can install without compiling first. 

I hate the thought of using Windows to rip and encode to a open source format when an open source os like Ubuntu should do it better.

Any help would be greatly appreciated!

---

### Post by Steeperton on 2011-11-01
abcde:
[http://www.andrews-corner.org/abcde.html#flac](http://www.andrews-corner.org/abcde.html#flac)

(Yes it's command line, but it's the best I've found!

---

### Post by andrew.46 on 2011-11-01
> **Steeperton said:**
> abcde:
[http://www.andrews-corner.org/abcde.html#flac](http://www.andrews-corner.org/abcde.html#flac)

Nice page that one, and I believe the owner of the page is a regular on these Forums as well and usually ready to help out with abcde issues :).

---

### Post by beew on 2011-11-01
soud juicer is fine for me. You may try k3b, which also works great, but for the flac option to be available for k3b you have to install the libflac packages first.

---

### Post by shantiq on 2011-11-01
[**rubyripper**]("http://linuxappfinder.com/package/rubyripper")   for an EAC-type rip [secure/two rips compared to make sure it is right]

**or**


commandline


**pacpl**   ```
sudo apt-get install pacpl
```

```
pacpl  --outdir ~/Desktop --rip all  -t  flac --fcomp 8

```
or for single trax


```
pacpl  --outdir ~/Desktop --rip 1,2,3  -t  flac --fcomp 8
```



or** ripit**


```
sudo apt-get install ripit

```

create folder called newtrax on Desktop


```
ripit --outputdir ~/Desktop/newtrax  --playlist 0 -c 2 flac-8 --eject --save
```

---

### Post by aeiah on 2011-11-01
i always liked asunder

they're all pretty similar though. they'll all use the same backend. i found asunder to be more reliable at pulling metadata than soundjuicer

---

### Post by 2F4U on 2011-11-01
I am currently using Audex

[http://kde-apps.org/content/show.php?content=77125](http://kde-apps.org/content/show.php?content=77125)

---

### Post by Baldrick_NZ on 2011-11-02
Thanks for all your replies, much appreciated.

Decided to settle on Audex. Seems quite quick and stable. Nice.

My only prob now is to try to stop RhythmBox from starting up when a CD is inserted. Any ideas anyone?

Cheers.

---

