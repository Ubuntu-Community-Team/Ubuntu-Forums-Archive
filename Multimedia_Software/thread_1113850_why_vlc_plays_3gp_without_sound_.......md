---
title: "why vlc plays 3gp without sound ......?"
date: 2009-04-02
forum: Multimedia Software
---

### Post by brijith on 2009-04-02
Hai friends,
While playing 3gp file in vlc I cann't get sound for it. Can any body help me to solve this issue. 

Can any one suggests good 3gp player...

also a good (GUI based) video converter to convert other video formats to 3gp

My distro is HARDY....



[COLOR="DarkOrange"]**Thanks**[/COLOR]

---

### Post by _Purple_ on 2009-04-02
Can you please run it from the terminal and paste the audio error here?

---

### Post by thewolfman on 2009-04-02
Hi,

sounds to me like you don't have all the necessary codecs installed if you are getting no sound!. check out which codecs you may need for all of your media needs and install them "en bloc" (all at once) and see if that solves the problem. A good example of a codecs pack would be the win32 codecs which is required to play windows media among others. There is also realplayer.

So basically you are looking for:

win32codecs
realplayer 
(available as a deb package direct from [http://www.real.com/linux](http://www.real.com/linux))

gstreamer of which there are various versions in the repository so check them out!.

Take a careful look at any other codecs you may need.

A good place to go for deb packages is: 

[http://www.geekconnection.org/downloads.htm](http://www.geekconnection.org/downloads.htm)

Which is a one stop shop for most codecs you may need and gstreamer are in the ubuntu repo.

Have a great day in India.

---

### Post by brijith on 2009-04-02
Thanks for your quick reply ...

I will try what you suggested....

Any good video converter....     any video format to 3gp


Thanks

---

### Post by aeiah on 2009-04-02
> **brijith said:**
> Thanks for your quick reply ...

I will try what you suggested....

Any good video converter....     any video format to 3gp


Thanks

perhaps winff if you want a gui. if not i imagine mencoder or ffmpeg will do the trick. of course, if your computer cant read 3gp sound it cant encode to/from it. you'll need to get the sound codec issue sorted first

---

### Post by paul.gevers on 2009-04-03
> **aeiah said:**
> if your computer cant read 3gp sound it cant encode to/from it.

AFAICT this is not correct for ffmpeg/winff. Those programs come with their own codec library and might still be able to convert while your viewers are not.

For most conversions to work in ffmpeg you will want to install ubuntu-restricted-extras or kubuntu-restricted-extras or xubuntu-restricted-extras (depending on your flavor of ubuntu). What version of Ubuntu are you running?

---

### Post by brijith on 2009-04-03
> **paul.gevers said:**
> What version of Ubuntu are you running?

I am using Ubuntu Hardy 8.04 ...

---

### Post by paul.gevers on 2009-04-03
> **brijith said:**
> I am using Ubuntu Hardy 8.04 ...

Then [Medibuntu]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories") is probably what you want. Add the repository as described in the previous link and install libdvdcss and w32codecs using your favorite package manager.

---

### Post by brijith on 2009-04-03
Thanks Friends

---

### Post by andrew.46 on 2009-04-03
Hi,

I look after an MPlayer guide for Hardy Heron that will give you a copy of the svn MPlayer + SMplayer that is capable of playing back 3gp files. This guide can be [seen here]("http://ubuntuforums.org/showthread.php?t=558538").

These files for the most part are h263 video and amr sound and usually pretty bad quality. I hope after all your efforts to play them you are not too disappointed :-).

All the best,

Andrew

---

### Post by mshtawythug on 2009-09-12
guys all i had to do is install realplayer for ubuntu
[http://www.real.com/unix/download/?action=CheckUpdate&playerVersion=11.0.1.1056&playerName=RealPlayer%2010&playerDistcode=RXEN11L&playerOrigcode=RXEN11L&language=en&operatingSystem=Linux&kernelVersion=2.6.28-15-generic&processorType=i686&distribId=Ubuntu&distribRelease=9.04&distribDescription=Ubuntu%209.04&distribCodename=jaunty&gccVersion=3.4.6](http://www.real.com/unix/download/?action=CheckUpdate&playerVersion=11.0.1.1056&playerName=RealPlayer%2010&playerDistcode=RXEN11L&playerOrigcode=RXEN11L&language=en&operatingSystem=Linux&kernelVersion=2.6.28-15-generic&processorType=i686&distribId=Ubuntu&distribRelease=9.04&distribDescription=Ubuntu%209.04&distribCodename=jaunty&gccVersion=3.4.6)

---

