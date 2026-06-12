---
title: "install vlc on ubuntu 11.04 without internet"
date: 2011-11-20
forum: Multimedia Software
---

### Post by jrmchess on 2011-11-20
I want to install vlc on ubuntu 11.04 so I can play video and mp3 files. But I don't have internet on this pc. I can download the installation packages from another windows pc and install them on ubuntu. but when I tried searching for these installation packages I didn't get any. can somebody please help me?

---

### Post by SteveDee on 2011-11-20
> **jrmchess said:**
> ...can somebody please help me?

You should be able to download any required package on a Windows machine from here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

For VLC on 11.04 I think you need this one: [http://packages.ubuntu.com/natty/video/vlc](http://packages.ubuntu.com/natty/video/vlc)

---

### Post by jrmchess on 2011-11-20
> **SteveDee said:**
> You should be able to download any required package on a Windows machine from here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

For VLC on 11.04 I think you need this one: [http://packages.ubuntu.com/natty/video/vlc](http://packages.ubuntu.com/natty/video/vlc)

I copied the downloaded vlc package on a pendrive and when I tried installing it by double clicking the file I get an error "dependency is not satisfiable: vlc nox(=1.1.9-1ubuntu1.3)". What should I do now?

---

### Post by SteveDee on 2011-11-20
> **jrmchess said:**
> ...What should I do now?

Go back to here: [http://packages.ubuntu.com/natty/video/](http://packages.ubuntu.com/natty/video/)
...and download vlc-nox

Looking at my installation of vlc I seem to have:
vlc
vlc-nox
vlc-data
vlc-plugin-notify
vlc-plugin-pulse

I hope this helps.

---

### Post by jrmchess on 2011-11-20
> **SteveDee said:**
> Go back to here: [http://packages.ubuntu.com/natty/video/](http://packages.ubuntu.com/natty/video/)
...and download vlc-nox

Looking at my installation of vlc I seem to have:
vlc
vlc-nox
vlc-data
vlc-plugin-notify
vlc-plugin-pulse

I hope this helps.

I tried to install vlc-nox and it gave me the following error "dependency is not satisfiable: liba 52-0.7.4". the only file that got installed out of the above list was vlc-data. now what??? ](*,):-({|=

---

### Post by SteveDee on 2011-11-20
> **jrmchess said:**
> ...now what??? ](*,):-({|=

Hmmm! Well looking at this page again: [http://packages.ubuntu.com/natty/video/vlc](http://packages.ubuntu.com/natty/video/vlc)
...I see that all the 'red' packages are dependencies, and will need to be downloaded too.

The 'green' ones are recommended (which probably means you need these as well).

...Oh, and don't forget the 'blue' ones!

Are you sure you can't just temporarily connect this box to the internet?

---

### Post by jrmchess on 2011-11-21
> **SteveDee said:**
> Hmmm! Well looking at this page again: [http://packages.ubuntu.com/natty/video/vlc](http://packages.ubuntu.com/natty/video/vlc)
...I see that all the 'red' packages are dependencies, and will need to be downloaded too.

The 'green' ones are recommended (which probably means you need these as well).

...Oh, and don't forget the 'blue' ones!

Are you sure you can't just temporarily connect this box to the internet?

wtf??? you mean to say I have to download each of those packages separately just to install vlc? wow ubuntu is really user friendly! Actually this internet thing was my main problem. Let me start from the beginning. I have a hp compaq V6430ee laptop. I had win xp as my primary OS. I decided one day to install ubuntu. So I did so using wubi and I am running ubuntu 11.04 from within xp. Now this laptop connects to the internet via wifi. I have a wireless router which connects both my desktop and laptop to the internet. I can use the internet from xp but when I switch to ubuntu I cannot do so. I had posted my problem earlier but got no satisfactory responses. So I decided why not just download vlc and install it on ubuntu since I couldn't to the internet. I though this might be a very straight forward process as connecting to the internet might require me to do a lot of networking stuff which would be very complicated. But it seems everything on ubuntu is complicated. Even installing a simple vlc file is such a pain in the ***. I am really getting frustrated with it and planning on deleting ubuntu. I don't know why ppl complain about windows? It's so much better.

---

