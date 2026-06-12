---
title: "How do I play movies, etc???"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by ChrisUK on 2007-04-13
Hi all.

This is probably a simple question.
I am new to Linux and have moved some of my audio and movies from Windows which are in .mp3, .avi, .wmv etc. How do I play them?
I click on the movie I want to play and it opens with Totem player and says:

"You do not have a decoder installed to handle this file. You might need to install the necessary plugins."

So what do I need to play these file types?
I have tried downloading VLC Player and that wont play them either :confused: :(

---

### Post by jrib on 2007-04-13
Hi take some time to read through [http://help.ubuntu.com/ubuntu/desktopguide/C/common-tasks-chap.html](http://help.ubuntu.com/ubuntu/desktopguide/C/common-tasks-chap.html)
and [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) .

Those two links should get you all setup.  Ask here, if anything isn't clear there.

---

### Post by ChrisUK on 2007-04-13
Thanks for the replay.
I am trying to follow the instructions under DVD playback
[https://help.ubuntu.com/ubuntu/desktopguide/C/video.html#dvdplayback](https://help.ubuntu.com/ubuntu/desktopguide/C/video.html#dvdplayback)

I have installed the libdvdread3 package, but when I type the command "sudo /usr/share/doc/libdvdread3/examples/install-css.sh" I get the following error:


sudo: /usr/share/doc/libdvdread3/examples/install-css.sh: command not found

---

### Post by IcemanV9 on 2007-04-13
Correct syntax command is:

```
sudo **sh** /usr/share/doc/libdvdread3/examples/install-css.sh
```

---

### Post by ChrisUK on 2007-04-13
> **IcemanV9 said:**
> Correct syntax command is:

```
sudo **sh** /usr/share/doc/libdvdread3/examples/install-css.sh
```

I just tried that and it said "sh: Can't open usr/share/doc/libdvdread3/examples/install-css.sh"

---

### Post by jrib on 2007-04-13
What does this command return:
```
apt-cache policy libdvdread3
```

---

### Post by cantormath on 2007-04-13
> **ChrisUK said:**
> Hi all.

This is probably a simple question.
I am new to Linux and have moved some of my audio and movies from Windows which are in .mp3, .avi, .wmv etc. How do I play them?
I click on the movie I want to play and it opens with Totem player and says:

"You do not have a decoder installed to handle this file. You might need to install the necessary plugins."

So what do I need to play these file types?
I have tried downloading VLC Player and that wont play them either :confused: :(

I would suggest Automatix2.  It will install all of that stuff for you, its free and easy.  There are also alot of other packages that automatix2 will install if you choose them.  There is also Easy Ubuntu.  I dont have have alot of experience with this one, but I here i is ok.

[http://getautomatix.com](http://getautomatix.com) is the website. I dont know where easy ubuntu is.

good luck.

---

### Post by ChrisUK on 2007-04-13
> **_jason said:**
> What does this command return:
```
apt-cache policy libdvdread3
```

libdvdread3:
  Installed: 0.9.6-3ubuntu1
  Candidate: 0.9.6-3ubuntu1
  Version table:
 *** 0.9.6-3ubuntu1 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Packages
        100 /var/lib/dpkg/status

---

### Post by ChrisUK on 2007-04-13
> **cantormath said:**
> I would suggest Automatix2.  It will install all of that stuff for you, its free and easy.  There are also alot of other packages that automatix2 will install if you choose them.  There is also Easy Ubuntu.  I dont have have alot of experience with this one, but I here i is ok.

[http://getautomatix.com](http://getautomatix.com) is the website. I dont know where easy ubuntu is.

good luck.

Thanks for the info and link. I have just installed that program and it looks really good, so I will see if it can help.
I might need to reinstall Ubuntu though because since installing Beryl and my GFX drivers, my graphics have been very slow. :(

---

### Post by leucippus on 2007-04-13
> **cantormath said:**
> I would suggest Automatix2.  It will install all of that stuff for you, its free and easy.  There are also alot of other packages that automatix2 will install if you choose them.  There is also Easy Ubuntu.  I dont have have alot of experience with this one, but I here i is ok.

[http://getautomatix.com](http://getautomatix.com) is the website. I dont know where easy ubuntu is.

good luck.

 Cool...thanks for the link :)

---

### Post by leucippus on 2007-04-13
Hey Chris...did you get it working? I installed getautomatix, and under the codecs links, i downloaded the codecs that said (non-free) codecs. Now, i can finally play my DVD's and WMV files!!

I use the "Movie Player" from the>Applications> sound and video>Movie Player>...good luck.

Thanks again for the link Cantormath :)

---

### Post by ChrisUK on 2007-04-14
> **leucippus said:**
> Hey Chris...did you get it working? I installed getautomatix, and under the codecs links, i downloaded the codecs that said (non-free) codecs. Now, i can finally play my DVD's and WMV files!!

I use the "Movie Player" from the>Applications> sound and video>Movie Player>...good luck.

Thanks again for the link Cantormath :)

Yep, it seems to be working now I have the codecs installed. It's a great little program that automatrix.

---

