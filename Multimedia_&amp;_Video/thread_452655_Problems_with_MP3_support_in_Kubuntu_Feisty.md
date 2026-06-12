---
title: "Problems with MP3 support in Kubuntu Feisty"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by grehivin on 2007-05-23
Hello!

Last week I installed Kubuntu 7.04 Feisty Fawn on my Desktop Computer (which unfortunately does not have access to the Internet, so I can't run the apt-get install command because what I have is the alternate install CD as my only repository), now I want to hear some MP3, and I downloaded the Xine package with libraries, but when I try to install it using the command: sudo ./configure ; make ; make install I get this error:

              configure: error: zlib needed

Then I get into the aptitude installer and I confirm that the library was installed but the C compiler does not see it.

Does anyone can help me to find out how to fix this problem in order to install Xine.

Thank you in advance for your help.

---

### Post by mitch.c on 2007-05-23
You need libxine1-ffmpeg (assuming Amarok is installed). It sounds like you are trying to compile the source, but don't have everything you need. If you were able to download the source, you could just as easily download the Ubuntu package and then:
```
$ sudo dpkg -i libxine1-ffmpeg_1.1.4-2ubuntu3_i386.deb
```
That should solve all your problems.

Here are a list of mirrors that host the libxine1-ffmpeg:
Fiesty: [http://tinyurl.com/2wwbyk](http://tinyurl.com/2wwbyk)

---

### Post by grehivin on 2007-05-23
Thank you so much, I will do it today and will let you know how it went.

---

### Post by grehivin on 2007-05-25
> **mitch.c said:**
> You need libxine1-ffmpeg (assuming Amarok is installed). It sounds like you are trying to compile the source, but don't have everything you need. If you were able to download the source, you could just as easily download the Ubuntu package and then:
```
$ sudo dpkg -i libxine1-ffmpeg_1.1.4-2ubuntu3_i386.deb
```
That should solve all your problems.

Here are a list of mirrors that host the libxine1-ffmpeg:
Fiesty: [http://tinyurl.com/2wwbyk](http://tinyurl.com/2wwbyk)
Thank you so much I downloaded and installed the package without problems in my computer now I am able to hear MP3 and to see movies! My computer is now "flying".

Now I want to know how to make may webcam work, it is a logitech quickcam, should I open a new thread or may I use this one?

---

