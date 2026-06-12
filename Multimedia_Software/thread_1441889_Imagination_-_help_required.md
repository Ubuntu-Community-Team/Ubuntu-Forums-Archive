---
title: "Imagination - help required"
date: 2010-03-29
forum: Multimedia Software
---

### Post by redenex on 2010-03-29
I installed Imagination from the repositories (Ubnutu 9.10 64 bit), and it is version 1.5. When I try to add sound, it displays a message saying "no handler for given file type `mp3'"

Can someone help?



Also, to install Imagination version 2 for Ubuntu 64 bit, what do I do?

---

### Post by redenex on 2010-03-29
;)

---

### Post by lyall on 2010-03-29
Simple DVD Slide Show Maker for Linux: Imagination from the web site 
[http://www.webupd8.org/2009/09/simple-dvd-slide-show-maker-for-linux.html]("http://www.webupd8.org/2009/09/simple-dvd-slide-show-maker-for-linux.html")

it says that Ubuntu users can download this 2.0b1 version from GetDeb
[http://www.getdeb.net/app/Imagination]("http://www.getdeb.net/app/Imagination")

good luck and have fun learning

---

### Post by redenex on 2010-03-30
Thank you lyall, will check it out!

---

### Post by redenex on 2010-03-30
hmmmm it is still installing version 1.5 that is available in the repository, and when I try to add sound it says **no handler for given file type `mp3'**

Any help? please!

---

### Post by redenex on 2010-03-30
Anyone? :P

---

### Post by Chronon on 2010-03-31
Have you installed the ubuntu-restricted-extras package?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by redenex on 2010-04-01
> **Chronon said:**
> Have you installed the ubuntu-restricted-extras package?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Of course yes, I have, I am playing mp3, wma and all formats without any problem, except when I open it through Imagination.

Let me check again.

---

### Post by redenex on 2010-04-01
Yes, it is already installed and all working fine. But when I open an mp3 through Imagination, it still gives this error. Perplexing!

---

### Post by Chronon on 2010-04-01
Unfortunately, I don't have any specific advice.  Maybe you can find something in the application's settings.  I had a similar problem with Audex due to a poorly configured encoding profile (i.e. the codec I wanted to use was installed but the command wasn't entered properly in the settings).

---

### Post by redenex on 2010-04-01
Fine no worries, perhaps I can find the solution soon. I re-installed the packages concerned, still no luck.

Thanks for the time!:popcorn:

---

### Post by Chronon on 2010-04-01
You could see if the "recommended" packages help.

[LIST]
[*]ffmpeg
 multimedia player, server and encoder 

[*]libavcodec-extra-52
   ffmpeg codec library 

[*]libavformat-extra-52
   ffmpeg file format library 

[*]libavutil-extra-49
   ffmpeg utility library
[/LIST]


Also, here's a forum thread by the developer about Imagination: [http://ubuntuforums.org/showthread.php?t=1047150](http://ubuntuforums.org/showthread.php?t=1047150)

You might get a response from him[?] if you post there.

---

### Post by rossofiorentino on 2010-04-07
Install libsox-fmt-all

---

### Post by leonidas666 on 2011-04-15
> **rossofiorentino said:**
> Install libsox-fmt-all

Just for the record: I had the same problem, and installing that libsox-fmt-all made it work for me.

---

### Post by ZPetrovich on 2012-01-09
The same for me.
Previous mentioned approach works great!!!

---

