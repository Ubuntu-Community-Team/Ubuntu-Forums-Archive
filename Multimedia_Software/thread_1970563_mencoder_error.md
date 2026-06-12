---
title: "mencoder error"
date: 2012-05-01
forum: Multimedia Software
---

### Post by fidelandche on 2012-05-01
Hi all,

I am trying to convert a AVI file with subtitles, both files have the same name, however when I try to convert this file I get an error message and this message is failed to convert it appears to be an error of mencoder. I have converted other files and Devede has worked fine but for some reason it will not convert this file. I am not changing any of the settings of devede as I know this can sometimes produce this error.

Any ideas would be great

Cheers

---

### Post by andrew.46 on 2012-05-02
Can you copy the entire MEncoder output and paste it here?

---

### Post by fidelandche on 2012-05-02
How do I do that?

---

### Post by andrew.46 on 2012-05-02
I am not familiar with devede but is there an error dialogue that comes up, hopefully a terminal screen with the MEncoder output?

---

### Post by fidelandche on 2012-05-02
Sorry no dialogue appears, but I typed mencoder into the terminal and got this output - andyandmillie@andyandmillie-Satellite-L300:~$ mencoder
mencoder: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
MEncoder SVN-r33713-4.6.1 (C) 2000-2011 MPlayer Team
No file given

Exiting... (error parsing command line)
andyandmillie@andyandmillie-Satellite-L300:~$

---

### Post by andrew.46 on 2012-05-02
This error could very well have little to do with the problem you are facing but perhaps it might be worthwhile updating your copy of MEncoder with the Medibuntu version. This is a little more capable than the Ubuntu repository version and may be enough to get your encode going, particular if there is a missing codec problem.

If you are not familiar with MEdibuntu there is a nice Ubuntu Community Docs page here:

Medibuntu
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

with details of how to enable this repository. If you are happy to try this first follow their directions and then try:

```
sudo apt-get install mplayer mencoder
```

just to be sure :).

---

### Post by fidelandche on 2012-05-02
I have installed the packages following their instructions and also put your code into the terminal, however I still get the same error message.

---

### Post by andrew.46 on 2012-05-02
Hmmmm..... looks like newer versions of devede actually use FFmpeg rather than MEncoder. Are you sure this a *mencoder* error?

---

### Post by fidelandche on 2012-05-02
The dialogue box states that it could be an mencoder error

---

### Post by andrew.46 on 2012-05-02
Sounds like a Mencoder error then :). It is a great pity that Devede does not generate a proper error log. Can you grab a screenshot of the error message? Then we both might have to wait for a Devede expert to come along :(.

---

