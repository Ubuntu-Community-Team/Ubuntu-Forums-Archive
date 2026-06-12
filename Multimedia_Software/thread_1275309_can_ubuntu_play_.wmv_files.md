---
title: "can ubuntu play .wmv files"
date: 2009-09-25
forum: Multimedia Software
---

### Post by Arminius on 2009-09-25
I'm trying to play windows media videos? and I'm guessing it can't be done, it keeps looking for codecs when I start them, and keeps failing.

so does anything know of anything official or more likely unofficial that can help?

---

### Post by Lampi on 2009-09-25
get w32codecs from mediabuntu repository:
```
~$ apt-cache policy w32codecs
w32codecs:
  Installed: 20071007-0medibuntu4
  Candidate: 20071007-0medibuntu4
  Versions:
 *** 20071007-0medibuntu4 0
        500 http://packages.medibuntu.org jaunty/non-free Packages
        100 /var/lib/dpkg/status
```

---

### Post by Arminius on 2009-09-25
I'm still a bit newbish, I typed that in
I got
~$ apt-cache policy w32codecs
w32codecs:
  Installed: (none)
  Candidate: (none)

so how do I just get w32codecs from the mediabuntu repository
I looked in synaptic, but came up with nothing

---

### Post by brookie on 2009-09-25
Hello, this site [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) tells you how to add the medibuntu repositiory to your system software sources. After you add it you should be able to install your codecs. 

Also, more info here at the medibuntu site: 
[http://www.medibuntu.org/](http://www.medibuntu.org/)

Remember to add the repository for your distribution of Ubuntu. I had to add the repo for Intrepid. 

Cheers, 
brook

---

### Post by martinbaselier on 2009-09-25
You would need to enable the multiverse in softwaresources to be able to install win32 codecs. But I'd advise you to follow this guide:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

It will make your machine more multimedia ready and play all the stuff.

---

### Post by andrew.46 on 2009-09-25
Hi Arminius,

> **Arminius said:**
> I'm trying to play windows media videos? and I'm guessing it can't be done, it keeps looking for codecs when I start them, and keeps failing.

A wmv file can hold a few different audio and video codecs so I guess it really depends exactly what sort of file you are dealing with. And there are a few other variables as well, for example the so-called w32codec package that Medibuntu holds will assist with the 32bit MPlayer but not vlc as it is distributed by Ubuntu, while the 64bit codec package will not assist with wmvs. I am not sure which *other* media players can also use this package.

So is there a link to one of these files that are causing trouble? For the most part they can be played on Linux but sometimes a little work is involved :).

Andrew

---

### Post by brookie on 2009-09-25
I just remembered one more thing. I installed Restricted Extras through the Applications/Add Remove, select All, click on Show:, select All Available Applications. Type Restricted Extras in the search bar. Select Ubuntu Restricted Extras. Apply. I don't know if this allowed me to play wmv's or if it was the w32 codec, but I can play wmv's with Totem Movie Player. :)

---

### Post by AlexanderDGreat on 2010-02-02
Hey, I just installed mplayer and it works fine now, here's the link:

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-904-jaunty.html]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-904-jaunty.html")

This is for Jaunty 32 bit, however the libdvdcss2 is quite obsolete, it's libdvdcss4 now I believe. Correct me if I'm wrong.

---

