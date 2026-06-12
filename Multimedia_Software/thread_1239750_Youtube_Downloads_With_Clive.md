---
title: "Youtube Downloads With Clive"
date: 2009-08-13
forum: Multimedia Software
---

### Post by Cygnia on 2009-08-13
Hello all, there's a wonderful command-line program in the repos called Clive that downloads and converts Youtube videos. I've been using it with no problem for months. Now I get this error message when trying to use it:

> cygnia@cygniapolis:~$ clive [http://www.youtube.com/watch?v=ljHb1ZMNHik&feature=rec-HM-fresh+div](http://www.youtube.com/watch?v=ljHb1ZMNHik&feature=rec-HM-fresh+div)
[1] 14007
cygnia@cygniapolis:~$ /usr/lib/python2.6/dist-packages/clive/modules.py:114: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
clive 1.0.2 20081014  [Linux]
/usr/lib/python2.6/dist-packages/clive/cache.py:183: DeprecationWarning: BaseException.message has been deprecated as of Python 2.6
  if 'table exists already' in err.message:
[http://www.youtube.com/watch?v=ljHb1ZMNHik&fmt=18](http://www.youtube.com/watch?v=ljHb1ZMNHik&fmt=18)                       104.8KB
error: extraction url (&video_id) not found
error: Traceback (most recent call last):
  File "/usr/bin/clive", line 29, in <module>
    Clive().main()
  File "/usr/lib/python2.6/dist-packages/clive/main.py", line 49, in main
    Nomad().run(self._say)
  File "/usr/lib/python2.6/dist-packages/clive/nomad.py", line 96, in run
    self._check_raw_urls(raw_urls)
  File "/usr/lib/python2.6/dist-packages/clive/nomad.py", line 261, in _check_raw_urls
    self._show_queue(raw_urls)
  File "/usr/lib/python2.6/dist-packages/clive/nomad.py", line 402, in _show_queue
    Progress(None)._byteshuman(total_bytes),
  File "/usr/lib/python2.6/dist-packages/clive/progress.py", line 92, in _byteshuman
    i = int(math.floor(math.log(bytes,1024)))
ValueError: math domain error

The only change that I have made to my system that could be related is upgrading my Flash plugin using instructions from the System76 forum (since I have a System76 laptop.) But why would that affect downloading and converting? BTW I have tried uninstalling (plus purging) and then reinstalling Clive using apt-get with no change.

Otherwise the other specs on my machine are Ubuntu Jaunty with all the latest updates. Can anyone make sense of the error message? Thanks for any pointers.

---

### Post by yabbadabbadont on 2009-08-13
Try putting quotation marks around the URL since it contains an ampersand (which has special meaning to the shell).  It downloads fine using youtube-dl (which is also in the repositories).

---

### Post by deyoungster on 2009-08-15
Tried putting quotes around the URL but it still didn't work. Any other options?

UPDATE : Tried youtube-dl. Works great. Thanx [yabbadabbadont]("http://ubuntuforums.org/member.php?u=30249")

---

### Post by lieugene on 2009-08-15
The same error started occurring after updated following packages:
libxml2 (2.6.32.dfsg-5ubuntu4) to 2.6.32.dfsg-5ubuntu4.2
libxml2-utils (2.6.32.dfsg-5ubuntu4) to 2.6.32.dfsg-5ubuntu4.2
python-libxml2 (2.6.32.dfsg-5ubuntu4) to 2.6.32.dfsg-5ubuntu4.2

---

### Post by harry2006 on 2009-08-15
youtube-dl works great...apart from that you can make use of "get_flash_videos" from here:
 [http://code.google.com/p/get-flash-videos/](http://code.google.com/p/get-flash-videos/)
which supports a lot of other sites/protocols as well...btw, i use both a lot!!!

---

### Post by ubseamus on 2009-08-16
> **Cygnia said:**
> Can anyone make sense of the error message?

No, but I have got the same message today.

I have also been happily downloading with clive up to now. The only thing I changed recently was installing skype. 

If anybody can resolve this, it would make my day.

Thanks.

---

### Post by FreyGrimrod on 2009-08-16
Rumor going around is that on August 12th in an effort to begin monetizing the sight youtube has started actively trying to discourage the ability to download their videos.....

can anyone confirm?

That being said as noted above youtube-dl works great still

---

### Post by erbala05 on 2009-08-17
Try with an alternative to download youtube videos.  Install 'Download Helper' plugin for Firefox.

In Firefox, Tools-> Add-ons-> Get Add-ons.  Choose Download Helper from the list and install it.  It works simply good.

---

### Post by cobberdig on 2009-11-02
can anyone help us i am new to using clive. i seem to be able to download general content ok on youtube & dailymotion. but i'm not able to download flagged content on dailymotion. what is the trick my hunch is it to do with the family filter or logging in. i can log on to dailymotion no problem just want to get clive to download that content. any help appreciated.

---

### Post by ilia on 2010-02-04
There is **cclive** tool which is better clive rewritten in C++. See my post about it at [http://ubuntuforums.org/showthread.php?p=8772533#post8772533]("http://ubuntuforums.org/showthread.php?p=8772533#post8772533"). It supports many sites and can automatically choose a video format for the best available quality.

---

### Post by viking1au on 2010-02-04
Have a look at ANT downloader (Firefox). It sets up a symbol in the bottom right of the screen & otherwise works just like Downloadhelper.

---

### Post by majedaly on 2011-04-04
> **harry2006 said:**
> youtube-dl works great...apart from that you can make use of "get_flash_videos" from here:
 [http://code.google.com/p/get-flash-videos/](http://code.google.com/p/get-flash-videos/)
which supports a lot of other sites/protocols as well...btw, i use both a lot!!!
Thanks get_flash_videos did the trick. I tried clive and youtube-dl and both couldn't download.

---

### Post by horace on 2011-04-05
> **majedaly said:**
> Thanks get_flash_videos did the trick. I tried clive and youtube-dl and both couldn't download.

Useful page for getting youtube-dl to work again; read down far enough to the bit where you find you need to do it twice!
[http://www.ubuntugeek.com/howto-download-videos-from-youtube-in-ubuntu.html]("http://www.ubuntugeek.com/howto-download-videos-from-youtube-in-ubuntu.html")

---

