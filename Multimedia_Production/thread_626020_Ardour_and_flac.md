---
title: "Ardour and flac"
date: 2007-11-28
forum: Multimedia Production
---

### Post by tessla8 on 2007-11-28
hi,
is there any way to import flac files in ardour coming with gutsy or hardy? I am only able to import wav-files.
I could compile it.. but i dont think thats the spirit of ubuntu :(

Thanks

---

### Post by tessla8 on 2007-12-04
Has no one an idea? Does it work for everyone?
It seems i am not able to import anything other than wav :-(

Ardour should be capable of much more!

---

### Post by mkc on 2008-01-14
I aggree! I have all my audio stored as .flac cos it takes up so much less space than wav. Why doesn't aurdour use flac?

---

### Post by nalmeth on 2008-01-14
FLAC is compressed audio. It essentially has the same quality as uncompressed formats like WAV, but perhaps you cannot import it for that reason.

I don't have a more solid reason, but this is a possibility.

---

### Post by Stochastic on 2008-01-17
At [http://ardour.org/node/861]("http://ardour.org/node/861")  I found this explanation:

> They have support for FLAC

They have support for FLAC in the code. This doesn’t necessarily translate to support for FLAC in the binary. That depends on whether you have the FLAC libs (and development stuff) installed when you build Ardour. Moreover, the FLAC people have recently made our life much harder - they changed their API, which means that if you install the latest FLAC libs, it will cause Ardour’s compile to fail.

If you want FLAC support, just be sure to have installed libflac and libflac-devel (might be called flac and flac-devel or flac-dev or who knows what) on your machine before you build Ardour. We should make this more clear in the build instructions.

---

### Post by Endolith on 2008-03-30
Can we get FLAC support built into Ardour by default?  I don't think users should have to re-compile it for this.

---

### Post by Endolith on 2008-07-02
I converted all my .wav files to .flac a long time ago, saving like 10 GB, but now of course, they are useless in Ardour.  I filed a bug report about this.

[https://bugs.launchpad.net/ubuntu/+source/ardour/+bug/245047](https://bugs.launchpad.net/ubuntu/+source/ardour/+bug/245047)

---

