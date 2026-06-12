---
title: "K3b mp3 error message"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by wpshooter on 2007-04-20
On Feisty, I was getting an error message when opening the K3b program regarding a missing mad mp3 library files, etc.  And recommending that it be installed to avoid/get rid of this error.  

Well that good and fine, but when I go to Synaptic to look for the file mentioned in the error message I can not find anything under "MAD MP3".

Apparently I did finally find the correct program that needed to be installed BUT it would be nice if ever who writes these error messages would give the **EXACT correct name** of the program file that is needed to be installed.

Thanks.

---

### Post by snowstorm on 2007-04-22
I also have this problem. Could you tell us what exactly you installed, if you remember?

---

### Post by varangian on 2007-04-22
I'd guess this is not really the fault of the application author, he/she refers to the vanilla library which is the most generic thing to do. Seems Ubuntu doesn't package it under that name or supplies a different library  entirely. Anyway, try having a search in synaptic for k3b and you should find libk3b-mp3 (or something very like, I don't have it in front of me so may have got it slightly wrong). Apparently doesn't get installed by default when you install k3b due to the usual legal nonsense. Once I'd installed that the error message about mp3 encoding went away so hopefully this will work for you too.

---

### Post by snowstorm on 2007-04-22
I do have this installed, but still get the same error on k3b startup:

Mp3 Audio Decoder plugin not found.
K3b could not load or find the Mp3 decoder plugin. This means that you will not be able to create Audio CDs from Mp3 files. Many Linux distributions do not include Mp3 support for legal reasons.
Solution: To enable Mp3 support, please install the MAD Mp3 decoding library as well as the K3b MAD Mp3 decoder plugin (the latter may already be installed but not functional due to the missing libmad). Some distributions allow installation of Mp3 support via an online update tool (i.e. SuSE's YOU).

What I have is:

ii  k3b                 1.0-0ubuntu2        A sophisticated KDE CD burning application
un  k3b-i18n            <none>              (no description available)
un  k3blibs             <none>              (no description available)
ii  libk3b2             1.0-0ubuntu2        The KDE cd burning application library - runtime files
ii  libk3b2-mp3         0.12.17-1ubuntu5    The KDE cd burning application library - MP3 decoder
un  libk3bcore          <none>              (no description available)
un  libk3bplugin        <none>              (no description available)
un  libk3bproject       <none>              (no description available)
un  libk3btools         <none>              (no description available)

and

ii  libmad-ocaml        0.2.1-1             OCaml bindings for the MAD library
ii  libmad0             0.15.1b-2.1         MPEG audio decoder library

---

### Post by snowstorm on 2007-04-23
I seem to have resolved this issue by adding medibuntu to the sources.list and do an upgrade. This was very troublesome though because the medibuntu repo takes A LOT of time!

---

### Post by WelterPelter on 2007-04-24
All I did was to add libk3b2-mp3 with synaptic and that solved the error message problem.

---

### Post by Steve H on 2007-04-25
I had this problem for a while after upgrading to Feisty. I got rid of it by unistalling all my KDE apps, and then reinstalling them with their "Suggested Packages". When installing through Synaptic it is always a good idea to right click on the package you want to install and look at the bottom of the menu, there is sometimes "Recommended" or "Suggested" packages that package may need. K3b has a few of these suggested packages in the list. Install all of the "Suggested" ones, worked for me. I don't get the MAD Mp3 warning anymore.

---

### Post by crazyclown on 2007-04-27
> **WelterPelter said:**
> All I did was to add libk3b2-mp3 with synaptic and that solved the error message problem. I added the libk3b2-mp3 and this also resolved my error message.

---

### Post by gslo on 2007-05-05
Thanks Welter, fixed my K3B errors!

---

### Post by yurtos on 2007-05-09
thank you so much.

you made my day.

for the curious people i did: 
sudo apt-get install libk3b2-mp3

---

### Post by brixmitch on 2007-05-25
Worked for me.  Thanks!

---

### Post by lando786 on 2007-05-25
install this pack:
libk3b2-mp3

worked for me

---

### Post by alpopel on 2007-06-05
for me aswell.. :D
thanks!!

---

### Post by rvperez on 2007-09-28
Thank you very much:

I added the libk3b2-mp3 from synaptic and this also resolved my error message.
It wasn't installed

:)

---

### Post by wpshooter on 2007-09-28
> **rvperez said:**
> Thank you very much:

I added the libk3b2-mp3 from synaptic and this also resolved my error message.
It wasn't installed

:)

Like I said, this should be automatically installed when the K3b program is installed.

---

