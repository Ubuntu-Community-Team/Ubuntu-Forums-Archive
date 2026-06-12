---
title: "Logitech Webcam Pro 9000 &amp; Stickam"
date: 2008-07-27
forum: Multimedia Software
---

### Post by pfeels on 2008-07-27
Just can't seem to get it to work on Stickam, I have to go and use Vista and I hate leaving Ubuntu Hardy, anyone figure out a fix yet?

---

### Post by kdiddy on 2008-08-07
I have same issue , cant get stikam to work, works great under skype and cheese , have you figured this out yet ? 

thanks

---

### Post by pfeels on 2008-08-07
Nope

---

### Post by kdiddy on 2008-08-12
I followed this , I am not a Linux guru and I was able to follow it , stickam now works . It basically switches the v4l2 to v4l that webcams work on. When the adobe flash windows opens on stickam instead if picking your camera , pick the loopback0 option, good luck 

[http://www.swift-tools.net/Flashcam/](http://www.swift-tools.net/Flashcam/)

kev

---

### Post by pfeels on 2008-08-12
I don't have a clue how to use the command in Terminal ...

This is the first step ...

Get the source
 flashcam-1.1.tgz from this site.

That was easy, then 
  Unpack them (and here's the code to put in terminal)
  [olivier]$ tar xvf flashcam-X.Y.tgz 
  [olivier]$ cd flashcam-X.Y

I changed to my Desktop directory where I have the download, I removed [olivier]$ ... and still Terminal doesn't see it, no directory found ...

any help?

---

### Post by kdiddy on 2008-08-13
ok , lets say your username is kdunn and you save the file to your desktop , 
at the command line you would type

cd /home/kdunn/Desktop

then

tar -xvf flashcam-1.1.tgz  (unzips the files to your desktop to folder flashcam1.1)

then 

cd /home/kdunn/Desktop/flashcam-1.1

then

make 
make install

---

### Post by pfeels on 2008-08-13
Worked up until 
make
make install

kdunn@kdunn-desktop:~/Desktop/flashcam-1.1$ make
make: Nothing to be done for `all'.
kdunn@kdunn-desktop:~/Desktop/flashcam-1.1$ make install
install -d /usr/local/flashcam
install: cannot change permissions of `/usr/local/flashcam': No such file or directory
make: *** [install] Error 1
kdunn@kdunn-desktop:~/Desktop/flashcam-1.1$ 

Yeah, I changed my name and directory, don't feel comfortable posting it for the world, probably doesn't make a difference ...

In terminal do I put in BOTH make AND make install or just make install ... thanks for the help by the way ...

---

### Post by kdiddy on 2008-08-13
you have to do make and make install as root so , 

sudo make

then 

sudo make install

---

### Post by pfeels on 2008-08-16
I did that but still no luck, when adobe flash opens I only have the one choice of web cam, I ran the test that was on the page you linked and it didn't look right ... It's ok though, I appreciate the help

---

### Post by kdiddy on 2008-08-16
sorry , wish i could help more ,

---

### Post by pfeels on 2008-08-18
Well at least I know it's possible so I'm sure I'll figure it out, the when is the question, thanks for your help

---

### Post by kdiddy on 2008-09-03
flash 10 works on stickam , flashcam is not required . It is still in beta 
but I find it to work well

---

