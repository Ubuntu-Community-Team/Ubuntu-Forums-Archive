---
title: "Software to use my TV Tuner."
date: 2006-12-14
forum: Multimedia &amp; Video
---

### Post by deodeep on 2006-12-14
Hey all,

I have a basic TV Tuner Card that comes with supporting "TVR" software for Windows..

I was wondering if there was any similar software for Ubuntu too. Something that a newbie like me could install.

Also, will it record the stream ?

Help appreciated :)

Thanks

---

### Post by josesanders on 2006-12-14
I use MythTV to record, but it can be difficult to get it working, especially if you don't have good hardware.  What TV card do you have?  There are a number of good guides depending on what you have.  There may be some much more basic programs out there, but MythTV seems to be the most popular.

---

### Post by deodeep on 2006-12-14
Yea,

I have been to the MythTV website. ANd frankly, I liked the application. However, I didnt find the application easy to install ( .tar.gz file ) so I didnt give it a try..

I have a normal ( read: local ) company TV Tuner Card. I think its frontech. The application provided for Windows says "TVR". I think the card is of "Dazzle" make.

Thanks.

Is there a simple installation for MythTV ?

---

### Post by Rodneyck on 2006-12-14
There are several apps to try, but if it does not start-up on your first try (recognized immediately) then you need to do some research to try and find out what chip is being used on your card. Usually that info is printed on the chip which will require you to open up your computer and have a looksie. Once you have that info, then hunting down solutions becomes a little easier.

A good tuner app to try is Tvtime. KDE has a good one that recognizes a lot of chips, but I can't remember the name of it...K*something*, as usual, lol.

Mythtv seems to be everyones favorite, but for the life of me, i can't figure it out. I don't think it works with my chip, as do any of the others. *sigh* Maybe someday, in one of the kernel upgrades...here's hoping.

---

### Post by Naegling23 on 2006-12-14
For watching tv, tvtime is a great program, but it wont record.  I have never had any luck with any tv recording programs other than mythtv.

The good news is that mythtv on edgy is very easy to install.  Setup can be confusing, but its not too bad, just follow a walkthrough.  Tweaking it to work right takes time, but its not difficult, there are just a lot of options.  Mythtv used to be harder to set up, but the 0.2 version on edgy is actually pretty easy.

---

### Post by Naegling23 on 2006-12-14
I think mythtv is in the universe repositories, enable them and try through synaptic/adept

---

### Post by Rodneyck on 2006-12-14
I think mythtv is in synaptic. If I remember correctly there was something called the backend and frontend (sorry, I had to take a moment to laugh) to download. Do you need both of these to run mythtv?

---

### Post by deodeep on 2006-12-14
Damn,

I tried to Install MythTV and it said it needed to install 22MB ( :-o ) of files. It did and then during installation, it says it needs MySQL backed password :lol:

Anywez, so I tried TvTime, it was there in the Add/Remove... it just downloaded 762 KB of files, installed itself, ran a scan and Voila. I have TV on Ubuntu.

Guess what, the video is better than what I get on Win !! And the UI is so much simpler..

Thanks for tha name guys !! 

Awesome !

---

### Post by josesanders on 2006-12-14
A very simplified way to install MythTV on Edgy:

$ sudo gedit /etc/apt/sources.list

Remove the '#' before the lines with the locations of the repositories, and also add the word 'multiverse' to the end of the line.  This will enable the necessary repositories.  I assume you must have already done this if you found MythTV.

$ sudo apt-get install lame liblame0
$ sudo apt-get install mysql-server
$ sudo apt-get install mythtv

When it asks for the mysql password, just leave that line blank, assuming that you haven't changed the root password for mysql.

Anyway, that's the easy part.  The hard part may be getting your TV card to work, and also the TV output on your video card, if you have or want to use that.

---

### Post by deodeep on 2006-12-14
Hmmmm,

I think I'll stick to TvTime :D 

Thanks to all :)

---

### Post by Rodneyck on 2006-12-14
Glad it worked out for you, I am envious. It did detect one of my channels, but no sound, so at least I got that. 

For others reading this thread and having trouble, the KDE tv app was nice because it allowed an option to manually input a channel's frequency setting. I never found a website that told me what my broadcast tv channel settings were unfortunately, but a nice feature all the same. So basically, it bypasses the need for specific driver/software for certain cards.

---

### Post by superm1 on 2006-12-15
For those of you guys following this thread and a bit confused whats required to get mythtv going on Edgy, look at the community documentation:

[http://help.ubuntu.com/community/MythTV/](http://help.ubuntu.com/community/MythTV/)

---

