---
title: "probems installing flvstreamer in get_iplayer"
date: 2009-07-05
forum: Multimedia Software
---

### Post by gra1 on 2009-07-05
I am trying to install flvstreamer in get_iplayer. I have downloaded (bin file) onto my desktop but I am not sure how to make get_player read it (needs to know exact path)

Thanks.

---

### Post by dbd on 2009-07-11
You're better off just downloading the .deb and installing that.

Go here:
[http://www.very-clever.com/download/nongnu/flvstreamer/linux/](http://www.very-clever.com/download/nongnu/flvstreamer/linux/)

You probably want to download flvstreamer_ubuntu-jackalope-x86-32bit_latest (assuming you are running a 32bit os)

---

### Post by BFG on 2009-07-30
> **dbd said:**
> ...(assuming you are running a 32bit os)

There are no builds for 64bit. Does that mean it's unsupported?

---

### Post by deadlydes on 2009-08-17
> **dbd said:**
> You're better off just downloading the .deb and installing that.

Go here:
[http://www.very-clever.com/download/nongnu/flvstreamer/linux/](http://www.very-clever.com/download/nongnu/flvstreamer/linux/)

You probably want to download flvstreamer_ubuntu-jackalope-x86-32bit_latest (assuming you are running a 32bit os)

this could be me being stupid but i cant see a .deb file there.
I scroll down the the bottom and there is a link for the latest one you suggest, i download that and its a bin file.
what do i do from there? (sorry a newb again)

---

### Post by ron999 on 2009-08-18
Hi
I would like to know how to install flvstreamer too.
Any more ideas?

Edit

OK, I've solved it.
Download the file from the very-clever link:- [http://www.very-clever.com/download/nongnu/flvstreamer/linux/]("http://www.very-clever.com/download/nongnu/flvstreamer/linux/")
It is named **flvstreamer_ubuntu-jackalope-x86-32bit_latest**.
Rename it just **flvstreamer**.
Then make it executable by using right-click > properties > permissions.
Then put it into the folder usr > bin, (I had to use **sudo nautilus** for this).

---

### Post by mctt on 2009-11-11
Just as a footnote here the question was asked "Is there a 64 bit build of flvstreamer?". I thought I needed this too in order to run some pvr files such as;

flvstreamer /home/user/Desktop/flvstreamer
force 1
modes hhigh,flvhigh1,flashhd,flashvhigh,flashhigh
pid b00n48tv
type tv

As it turns out all I needed to do was download flvstreamer_ubuntu-jackalope-x86-32bit_latest, rename to flvstreamer put it on my Desktop and allow it to be executed as a program (Right click and Permissions tab > Check box "Allow executing file as a program").
No need for 64 bit version.

---

