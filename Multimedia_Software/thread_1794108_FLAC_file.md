---
title: "FLAC file"
date: 2011-06-30
forum: Multimedia Software
---

### Post by rizon on 2011-06-30
Hello, I have a quick question. I got a flac file that is 280 mb, an entire cd in one file. Is there a way I can convert it into mp3 with the separate songs on different files? Thank you.

---

### Post by Yellow Pasque on 2011-06-30
Splitting the flac is the hard part. You need a .cue file to do it quickly/easily. Hopefully, the cue info is embedded in the flac file's metadata.
[http://nxadm.wordpress.com/2009/02/09/split-one-flac-cue-file-into-separate-tracks/](http://nxadm.wordpress.com/2009/02/09/split-one-flac-cue-file-into-separate-tracks/)
After you have all the split flac's, convert them using soundconverter program.

---

### Post by rizon on 2011-06-30
I followed the directions on the site, and this is what it gave me:

shnsplit: warning: none of the builtin format modules handle input file: [Black Label Society - The Song Remains Not The Same (flac).cue]
shnsplit: error: cannot continue due to error(s) shown above

Anyone know how I can fix this? Thanks.

---

### Post by cokicd on 2011-07-02
Try my script
[http://code.google.com/p/split-lossless/](http://code.google.com/p/split-lossless/)

---

### Post by shantiq on 2011-07-03
> **rizon said:**
> Hello, I have a quick question. I got a flac file that is 280 mb, an entire cd in one file. Is there a way I can convert it into mp3 with the separate songs on different files? Thank you.



there is a really good piece of software called which has a gui called **flacon**


```

sudo add-apt-repository ppa:flacon/ppa
sudo apt-get update
sudo apt-get install flacon
```

it is also in the software center on natty and probably earlier distros



**OR** the script designed by cokicd called **split-lossless**

```
sudo add-apt-repository ppa:cokicd/split-lossless
sudo apt-get update
sudo apt-get install split-lossless
```   which is superb:KS

---

