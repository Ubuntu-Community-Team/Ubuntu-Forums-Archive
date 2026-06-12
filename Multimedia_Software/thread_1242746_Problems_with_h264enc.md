---
title: "Problems with h264enc"
date: 2009-08-17
forum: Multimedia Software
---

### Post by dsc13 on 2009-08-17
I'm trying to use h264enc to encode a video file.

When I try to run the program, it tells me either that MEncoder is missing or MPlayer is missing.  However, I have installed both of these programs and they are present in /usr/local/bin.  

Any idea what I could do to solve this error?  Thanks in advance.

---

### Post by Nepherte on 2009-08-17
Is the /usr/local/bin directory in your executable path? You can verify it with the following command:
```
echo $PATH
```

---

### Post by dsc13 on 2009-08-17
I did as you suggested and the output was:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

So, /usr/local/bin does seem to be in the executable path.  

Any other thoughts?  Thanks.

> **Nepherte said:**
> Is the /usr/local/bin directory in your executable path? You can verify it with the following command:
```
echo $PATH
```

---

### Post by mc4man on 2009-08-17
Did you build your own mplayer and if so did you install from a checkinstall or sudo make install?

---

### Post by dsc13 on 2009-08-17
I did build my own mplayer, and i installed from a sudo make install

> **mc4man said:**
> Did you build your own mplayer and if so did you install from a checkinstall or sudo make install?

---

### Post by mc4man on 2009-08-17
Well I've got to get back to a job, but here's what I believe your issue is.

If you built mplayer then it  installed mencoder as part of the mplayer install.

The problem is that some other apps won't recognize mencoder as being installed, and in addition if you try to install a mencoder  package now it may fail (error - trying yo overwrite mencoder which is also part of package mplayer....

Ther are several solutions, ck. this thread or I'll be around in several hours for a different one ( see below

[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

Andrew.46 is in Australia, will also be around in several hours 

What will work is to build mplayer as a debian package set, I just did with todays svn. This gives you a separate mplayer and mencoder package, see screen.

Then h264enc should have no issue, also just installed, from sanity check


```
doug@doug-laptop:~$ h264enc -sc

-> Checking for 'MPlayer'..................... OK
-> Checking for 'MEncoder'.................... OK
-> H.264 video support in MEncoder............ YES
-> AAC (FAAC) audio support in MEncoder....... YES
-> MP3 (LAME) audio support in MEncoder....... YES
-> AC3 (lavc) audio support in MEncoder....... YES
-> PCM audio support in MEncoder.............. YES

```

Edit 
 I usually use -debuild and my own .diff to build mplayer packages due to using heavily modded hardy 
What I did in screen is something I thought would be very easy for you, using a diff from rvm (smplayer

I really don't have time to explain the few edits you need to make, some in the rules file, some in the control. Plus your current libx264-dev may or may not be a factor.

Will give you the command set, also rvm is around alot and knows his .diff best

Make a folder mplayer1 and cd to it
```
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk svn
```

```
wget http://smplayer.svn.sourceforge.net/viewvc/smplayer/mplayer-builds/patches-ubuntu/debian.diff

```

 ```
cd svn && patch -p0 -E -i ../debian.diff
```

**Now some edits should be made**

then

```
chmod 755 create_deb.sh && ./create_deb.sh
```

That's it (unless your libx264-dev is an issue

---

### Post by dsc13 on 2009-08-17
I followed all of the instructions on the webpage and everything seemed to work fine but I'm still getting the same error from h264.  Oh well, thanks for your help!

---

### Post by mc4man on 2009-08-17
Are you failng the sanity check in this regard (mplayer and mencoder) or passing it and a problem when running?

```
h264enc -sc
```

---

