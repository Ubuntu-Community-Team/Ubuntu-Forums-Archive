---
title: "Cannot play DVD, neither with VLC"
date: 2010-10-28
forum: Multimedia Software
---

### Post by Nemomnis on 2010-10-28
Hi, I have installed Kubuntu 10.10 on an EEETop Asus, which runs quite smoothly. The problem is that I can't make it play DVDs: inserting a DVD-Video (I've tried with a Bourne DVD), Dragon Player can't read and the window screen remains black; VLC opens the first window of the DVD, but when I select the language "English or Italian", it stops and nothing 
Thanks

---

### Post by dasan on 2010-10-28
It may be an encrypted DVD 

Install libdvdcss

[http://packages.medibuntu.org/maverick/index.html](http://packages.medibuntu.org/maverick/index.html)

[http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html)

---

### Post by Nemomnis on 2010-10-28
> **dasan said:**
> It may be an encrypted DVD 

Install libdvdcss

[http://packages.medibuntu.org/maverick/index.html](http://packages.medibuntu.org/maverick/index.html)

[http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html)

Yes, it's encrypted! Thanks, but now how can I install the package from Medibuntu for Kubuntu 64bit ?

---

### Post by ankspo71 on 2010-10-28
Hi,
This information is borrowed from here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

The large command below will add the Medibuntu repository for you. Open up your terminal and paste the following command. 

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Now you will be able to find libdvdcss2 in Software Center, Kpackagekit, Synaptic Package Manager, etc. 

Or you can use the command below to install libdvdcss2
```
sudo apt-get install libdvdcss2
```

Optionally, "w64codecs" is also a nice to have codecs package for viewing some Windows formats, Real, and Apple Quicktime, etc.
```
sudo apt-get install w64codecs
```

Hope this helps.

---

### Post by dasan on 2010-10-29
Or
you can download that package and install it by double click
[http://packages.medibuntu.org/maverick/libdvdcss2.html](http://packages.medibuntu.org/maverick/libdvdcss2.html)

---

### Post by herve77 on 2010-12-26
Hello,

I also installed Kubuntu 10.10 and followed the various instructions to play movie DVD. I managed to read some movie DVDs but for some of them, the DVD is neither recognized nor mounted (the DVDs are all from the same region, 2). It seems that the most recent DVDs are not successfully read. Any idea why this is happening ? 
Thanks in advance for any help !

Hervé

---

### Post by herve77 on 2010-12-26
I finally managed to read all kind of DVDs ! I think the problem came from my DVD player which is apparently not able to read new DVDs. I tried with a external DVD player (more recent) and the problem disappeared :D

---

### Post by X_Splinter on 2011-11-16
> **ankspo71 said:**
> Hi,
This information is borrowed from here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

The large command below will add the Medibuntu repository for you. Open up your terminal and paste the following command. 

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Now you will be able to find libdvdcss2 in Software Center, Kpackagekit, Synaptic Package Manager, etc. 

Or you can use the command below to install libdvdcss2
```
sudo apt-get install libdvdcss2
```

Optionally, "w64codecs" is also a nice to have codecs package for viewing some Windows formats, Real, and Apple Quicktime, etc.
```
sudo apt-get install w64codecs
```

Hope this helps.

Thank you man :guitar:

---

