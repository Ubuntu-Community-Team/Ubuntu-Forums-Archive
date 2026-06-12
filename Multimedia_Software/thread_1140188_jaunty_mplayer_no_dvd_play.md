---
title: "jaunty mplayer no dvd play"
date: 2009-04-27
forum: Multimedia Software
---

### Post by mihaicj on 2009-04-27
Hi guys. I can't seem to be able to play dvds in mplayer. I installed the packages, and totem or vlc can play the dvd. I like mplayer better and I was wondering what the problem is. Thanks.

---

### Post by VMC on 2009-04-27
> **mihaicj said:**
> Hi guys. I can't seem to be able to play dvds in mplayer. I installed the packages, and totem or vlc can play the dvd. I like mplayer better and I was wondering what the problem is. Thanks.

Two questions. What happens when you try to play? What video chip do you have (lspci|grep VGA)?

---

### Post by mihaicj on 2009-04-27
I have nvidia: nVidia Corporation Quadro NVS 140M (rev a1)

I attached the entire output. Not sure what is relevant. Might be the

The selected video_out device is incompatible with this codec.

but I tried with several video drivers and I get the same thing.

---

### Post by mihaicj on 2009-04-27
anybody?

---

### Post by hatalar205 on 2009-04-27
Did you add Medibuntu repositories and install necessary codecs?

---

### Post by VMC on 2009-04-27
Sorry. I don't have an nVidia chip. You might want to search this from for nVidia problems.

---

### Post by mihaicj on 2009-04-27
> **hatalar205 said:**
> Did you add Medibuntu repositories and install necessary codecs?

Yes, I did. Installed eveything I heard of. It works on VLC but not on mplayer.

---

### Post by mihaicj on 2009-04-27
anybody? any ideas?

---

### Post by mc4man on 2009-04-27
Couple of things
(you can post your terminal outputs in your post and put in a quote box, easier to read and refer to.

How are you trying to play the dvd with mplayer, a gui or a command line?
If a command line post what command your using.

Your .txt mentioned the dvd had 3 titles and the one being played back had *one chapter* which wouldn't be a main movie (if that's what you were attempting to play. 
"end of file" may mean just that - nothing to play.
(I've only seen one dvd movie that was only 1 chapter

If your not using the command line then find out which title is the movie and for the moment use something simple (where red is the title number
```

mplayer dvd://[COLOR="Red"]1[/COLOR]
```

Then post the terminal output start to finish in your reply

---

### Post by xc3RnbFO8P on 2009-04-27
It is a bug.
I have the same problem,
I play DVDs like **Die Hard 4** if I do:
> mplayer dvd://16
The last title (16)
But if I play **Garfield 2** I do:
> mplayer dvd://3
Title 3 of (16)

---

### Post by mihaicj on 2009-04-27
Thanks for the tips. It works if I run```
mplayer dvd://3 
``` or ```
gmplayer dvd://3 
```. For title 2 it shows some kind of intro. So every time I play a dvd I will have to see which title it is? Totem is much better at this part. It shows the menu, you can select and everything. I will just run it with dvd://3 for now. Thanks.

---

### Post by mc4man on 2009-04-27
For a gui smplayer is far superior to gmplayer, I don't believe he's done a jaunty version yet.
homepage
[http://smplayer.sourceforge.net/index.php?tr_lang=en](http://smplayer.sourceforge.net/index.php?tr_lang=en)

(a thread titled "smplayer for jaunty" should get you some info from the developer (rvm) or others very quickly

---

### Post by Zero Prime on 2009-04-27
I have to ask, have you installed libdvd yet?

---

### Post by mihaicj on 2009-04-27
> **Zero Prime said:**
> I have to ask, have you installed libdvd yet?

Yes, I have. I suppose you mean libdvdcss, libdvdnav4 or libdvdread4. I have them all.

---

### Post by mihaicj on 2009-04-27
> **mc4man said:**
> For a gui smplayer is far superior to gmplayer, I don't believe he's done a jaunty version yet.
homepage
[http://smplayer.sourceforge.net/index.php?tr_lang=en](http://smplayer.sourceforge.net/index.php?tr_lang=en)

(a thread titled "smplayer for jaunty" should get you some info from the developer (rvm) or others very quickly

smplayer is in the repos. I have it, just that it acts wird. the place where the image is supposed to be is actually transparent.

---

### Post by mc4man on 2009-04-27
A quick check shows there is a jaunty smplayer and if you add his repo you can also get an updated mplayer

Highly recommended

I believe he builds his mplayer package dvdnav enabled. While there are issues running mplayer with dvdnav enabled it will help even in the 'normal' mode or thru smplayer in non navigation 'mode' with certain structure protected titles.

To add repo in jaunty go here, copy and paste the  source lines into System -> Admin... -> Software Sources -> third Party.

[https://launchpad.net/~rvm4000/+archive/ppa](https://launchpad.net/~rvm4000/+archive/ppa)

Then reload, install smplayer and upgrade mplayer (all can be done in synaptic

Edit : missed your post
I'd add the rvm repo, update smplayer and mplayer if available and if having issue start thread with "smplayer blah, blah"
you'll get good support

---

### Post by mihaicj on 2009-04-27
> **mc4man said:**
> A quick check shows there is a jaunty smplayer and if you add his repo you can also get an updated mplayer

Highly recommended

I believe he builds his mplayer package dvdnav enabled. While there are issues running mplayer with dvdnav enabled it will help even in the 'normal' mode or thru smplayer in non navigation 'mode' with certain structure protected titles.

To add repo in jaunty go here, copy and paste the  source lines into System -> Admin... -> Software Sources -> third Party.

[https://launchpad.net/~rvm4000/+archive/ppa](https://launchpad.net/~rvm4000/+archive/ppa)

Then reload, install smplayer and upgrade mplayer (all can be done in synaptic

Tried the repo already but the packages are probably not built yet for Jaunty. I'll install them when they appear.

---

### Post by rvm4000 on 2009-04-27
> **mihaicj said:**
> Tried the repo already but the packages are probably not built yet for Jaunty. I'll install them when they appear.

That PPA does include packages for jaunty.

There's also a new PPA with even newer versions of mplayer and smplayer, with packages for hardy, intrepid and jaunty:
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

(the jaunty and intrepid packages compiled with vdpau support!)

If not using jaunty it will necessary to add this PPA too (includes some updated libraries required for mplayer):
[http://launchpad.net/~rvm/+archive/libs](http://launchpad.net/~rvm/+archive/libs)

In order to enable dvd menus in smplayer, you need:

* Check the option "Enable DVD menus" in Preferences -> Drives.
* Assign the action "Activate option in DVD menus" (Preferences -> Keyboard and mouse) to the left mouse button (so you can select the options in the menus with the mouse).

---

### Post by mihaicj on 2009-04-28
I did that. I think the packages for jaunty were just added. I still have the problem that the movie window is transparent in smplayer. this doesn't happen in mplayer or gmplayer. might be caused by compiz.

---

### Post by kibster on 2009-04-28
I have the same problem.. But I,m using a GUI ..error pops up saying i am try to play an encrypted format.   and if i am its not going to work . I was trying to use Movie Player  then I tried VNC  still wouldnt work.  I think I down loaded all the stuff to play it.

Russ

---

