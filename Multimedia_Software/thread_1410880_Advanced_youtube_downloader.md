---
title: "Advanced youtube downloader"
date: 2010-02-19
forum: Multimedia Software
---

### Post by linuxyogi on 2010-02-19
Hi,

I use youtube-dl to download videos from youtube. 

My first problem is that sometimes while downloading the downloading process becomes very slow & sometimes inactive. Suppose I am downloading a file of 20 MB , now what happens is that the downloading process starts pretty fast but the speed falls & sometimes the downloading process is terminated midway. So I have to start the downloading process all over again.


My second problem is that youtube-dl doesn't allow more than one download. I only option left is to open the video url via a web browser & copy the video file from the cache.

Features Needed------

1 Support for pause / resume downloads 
2 Support for parallel downloads.
3 A Basic GUI.

Is there already a program available with all these features ?
Please reply.

---

### Post by Pauly BC on 2010-02-19
There is a very useful plugin for Firefox I have been using. It does not download streams, but it can download YouTube and other compatible video files.

[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

---

### Post by kostkon on 2010-02-19
You may like [*xVideoServiceThief*]("http://xviservicethief.sourceforge.net/").

---

### Post by dorothykinder on 2010-02-19
@Kostkon, 

Thanks for this source, i have been looking out also for a You tube video downloader service..
 :)

---

### Post by andrew.46 on 2010-02-19
Hi linuxyogi,

> **linuxyogi said:**
> I use youtube-dl to download videos from youtube. 

I wonder if you are using the version of youtube-dl provided by the Ubuntu repository, in which case you are using quite an aged copy. Perhaps try a newer version and at least *some* of your issues may be solved:

```

$ sudo apt-get remove youtube-dl
$ sudo wget http://bitbucket.org/rg3/youtube-dl/raw/2010.02.13/youtube-dl -O /usr/local/bin/youtube-dl
$ sudo chmod +x /usr/local/bin/youtube-dl

```

All the best,

Andrew

---

### Post by linuxyogi on 2010-02-20
> **andrew.46 said:**
> Hi linuxyogi,



I wonder if you are using the version of youtube-dl provided by the Ubuntu repository, in which case you are using quite an aged copy. Perhaps try a newer version and at least *some* of your issues may be solved:

```

$ sudo apt-get remove youtube-dl
$ sudo wget http://bitbucket.org/rg3/youtube-dl/raw/2010.02.13/youtube-dl -O /usr/local/bin/youtube-dl
$ sudo chmod +x /usr/local/bin/youtube-dl

```

All the best,

Andrew

The problem is that the web page you mentioned [http://bitbucket.org/](http://bitbucket.org/).....
is not responding. I tried to open it with FF, Opera, Chrome but nothing worked.

I just want to copy the file to my home directory & run it from there only.

I will write back if I am successful in downloading the file. 

Thanks a lot.

---

### Post by ismaelito on 2010-02-20
Why don't you use Video DownloadHelper ?, is an add-on in firefox, is really very useful to download videos from youtube

---

### Post by linuxyogi on 2010-02-20
> **ismaelito said:**
> Why don't you use Video DownloadHelper ?, is an add-on in firefox, is really very useful to download videos from youtube

Hi, 
Thanks a lot for trying to help me but look I don't want to install something which says "author not verified". I guess I will wait until the youtube-dl download site starts working again.

THANK YOU.

---

### Post by andrew.46 on 2010-02-20
Hi linuxyogi,

> **linuxyogi said:**
> The problem is that the web page you mentioned [http://bitbucket.org/](http://bitbucket.org/).....
is not responding.

The main page is [http://bitbucket.org/rg3/youtube-dl/wiki/Home](http://bitbucket.org/rg3/youtube-dl/wiki/Home) and this is certainly working from my end of the world at the moment, hopefully from yours now as well...

Andrew

---

### Post by linuxyogi on 2010-02-25
> **andrew.46 said:**
> Hi linuxyogi,



The main page is [http://bitbucket.org/rg3/youtube-dl/wiki/Home](http://bitbucket.org/rg3/youtube-dl/wiki/Home) and this is certainly working from my end of the world at the moment, hopefully from yours now as well...

Andrew

Finally [http://bitbucket.org](http://bitbucket.org) opened. I downloaded the the youtube-dl & copied it to my home dir. 

Now when I try to download a video it says ---------

The program 'youtube-dl' is currently not installed.  You can install it by typing:
sudo apt-get install youtube-dl
youtube-dl: command not found


I used to run youtube-dl from my home directory while using both Hardy & Jaunty.

Is there something in Karmic which stops programs from running from the home dirctory ?

I right clicked the "youtube-dl" & selected "allow executing file as program"

Please reply. Thanks.

---

### Post by andrew.46 on 2010-02-25
Hi linuxyogi,

> **linuxyogi said:**
> 

Now when I try to download a video it says ---------

```
The program 'youtube-dl' is currently not installed.  You can install it by typing:
sudo apt-get install youtube-dl
youtube-dl: command not found
```



The script must be in your $PATH, or you can simply navigate to the exact location of youtube.dl and run it as:

```
**[COLOR="Red"]./[/COLOR]**youtube-dl *etc etc*
```

Andrew

---

### Post by linuxyogi on 2010-03-04
> **andrew.46 said:**
> Hi linuxyogi,

The script must be in your $PATH, or you can simply navigate to the exact location of youtube.dl and run it as:

```
**[COLOR="Red"]./[/COLOR]**youtube-dl *etc etc*
```

Andrew

Thanks a lot. Its working.

I read that youtube-dl can download multiple videos if the url of a playlist is given. 

But what about parallel downloads ? 

Is that at all possible with youtube-dl?  

If no, I will continue using youtube-dl & wait for the inclusion of the feature in future versions of youtube-dl.


Thanks again.

---

### Post by andrew.46 on 2010-03-04
Hi linuxyogi,

> **linuxyogi said:**
> Thanks a lot. Its working.

Excellent news :).

> I read that youtube-dl can download multiple videos if the url of a playlist is given. 

But what about parallel downloads ? 

It can download from a list using *--batch-file=F* where F is the name and path to the file. BTW you may be aware that full usage can be seen by running *youtube-dl --help*? I am not aware that youtube-dl can actually do parallel downloads but I have been wrong before :).

Andrew

---

### Post by AndrewSimoes on 2010-05-04
Hey is there any way to couple a download accelerator like lftp pget along with youtube-dl?
andrew46 I'm also looking forward to an mplayer guide for Lucid.
Thanks :D

---

### Post by andrew.46 on 2010-05-04
Hi Andrew,

> **AndrewSimoes said:**
> andrew46 I'm also looking forward to an mplayer guide for Lucid.

Unfortunately I am not going to be all that heavily involved with Lucid and I suspect I will not be writing an MPlayer guide this time... :(.

Apologies,

Andrew

---

### Post by Xcursion666 on 2010-12-19
i dont use youtube dl i use keepvid  [http://keepvid.com/](http://keepvid.com/) it supports pause and resume and you can dl multiple files at once beware it might cause firefox to crash it happened to me a few times

---

### Post by linuxyogi on 2010-12-19
Presently I am using a firefox addon called netvideohunter.
Supports multiple downloads as well as pause/resume.

---

### Post by brutus83 on 2011-02-22
hi Andrew, i have question 

I try to download youtube and follow your instruction.
But it appears this on my terminal :
my@my-laptop:~$ youtube-dl [http://www.youtube.com/watch?v=cltyYa-B1tE](http://www.youtube.com/watch?v=cltyYa-B1tE)
[youtube] Setting language
[youtube] cltyYa-B1tE: Downloading video webpage
[youtube] cltyYa-B1tE: Downloading video info webpage
[youtube] cltyYa-B1tE: Extracting video information
ERROR: unable to download video (format may not be available)

Any idea what should i do?
Thanks.

---

### Post by andrew.46 on 2011-02-25
> **brutus83 said:**
> I try to download youtube and follow your instruction.But it appears this on my terminal :

```
my@my-laptop:~$ youtube-dl [http://www.youtube.com/watch?v=cltyYa-B1tE](http://www.youtube.com/watch?v=cltyYa-B1tE)
[youtube] Setting language
[youtube] cltyYa-B1tE: Downloading video webpage
[youtube] cltyYa-B1tE: Downloading video info webpage
[youtube] cltyYa-B1tE: Extracting video information
ERROR: unable to download video (format may not be available)
```

Any idea what should i do?

Well, it is against youtube's terms of use to download their videos in this way but I see no problem in demonstrating in *general* terms how to update and use youtube-dl. Be aware however that youtube-dl should only be used with *other* supporting sites, these can be seen in the [documentation]("http://rg3.github.com/youtube-dl/documentation.html"). I suspect that your version is too old, try updating as follows:

```

$ sudo apt-get remove youtube-dl
$ sudo rm /usr/local/bin/youtube-dl
$ sudo wget --no-check-certificate https://github.com/rg3/youtube-dl/raw/2011.02.25c/youtube-dl -O /usr/local/bin/youtube-dl
$ sudo chmod +x /usr/local/bin/youtube-dl

```

Usage can be as follows:

```
youtube-dl -o '%(stitle)s.%(ext)s' '*file_2_download*'
```

where of course *file_2_download* is the url of your desired file. An easy way to update your installation is to periodically run:

```
sudo youtube-dl --update
```

Andrew

---

### Post by brutus83 on 2011-03-08
hi andrew,

thanks!
It works!
Yeahhh...

> **andrew.46 said:**
> Well, it is against youtube's terms of use to download their videos in this way but I see no problem in demonstrating in *general* terms how to update and use youtube-dl. Be aware however that youtube-dl should only be used with *other* supporting sites, these can be seen in the [documentation]("http://rg3.github.com/youtube-dl/documentation.html"). I suspect that your version is too old, try updating as follows:

```

$ sudo apt-get remove youtube-dl
$ sudo rm /usr/local/bin/youtube-dl
$ sudo wget --no-check-certificate https://github.com/rg3/youtube-dl/raw/2011.02.25c/youtube-dl -O /usr/local/bin/youtube-dl
$ sudo chmod +x /usr/local/bin/youtube-dl

```

Usage can be as follows:

```
youtube-dl -o '%(stitle)s.%(ext)s' '*file_2_download*'
```

where of course *file_2_download* is the url of your desired file. An easy way to update your installation is to periodically run:

```
sudo youtube-dl --update
```

Andrew

---

### Post by andrew.46 on 2011-03-08
> **brutus83 said:**
> hi andrew,

thanks!
It works!
Yeahhh...

Great news :).

Andrew

---

### Post by linuxyogi on 2011-07-03
Hi, I came to know about Minitube fairly recently, downloaded the latest ver 1.4.3 from their website thinking that the version in the repos is a bit old.

But the problem is when I click on the resolution button nothing happens. No change in resolution whatsoever.

Flash in FF often hangs the PC completely.

I am using Umplayer to watch youtube videos.

---

### Post by Paschalis89 on 2011-08-01
I installed Python, and Jython..
i get this problem:

```
youtube-dl
Traceback (most recent call last):
  File "/usr/local/bin/youtube-dl", line 15, in <module>
    import gzip
  File "/usr/local/lib/python2.7/gzip.py", line 9, in <module>
    import zlib
ImportError: No module named zlib

```

I reinstalled Python, and i get the same error again.
Any suggestions?

---

### Post by xtremyst on 2011-10-28
hey there
here's what i did and worked just fine:

I went to [zlib]("http://zlib.net/") home page
and downloaded the zlib source code, version 1.2.5, 
tar.gz format file found there.
extracted the content, opened the terminal,
went in that folder and typed
```
./configure && make && sudo make install
```

after installation of zlib i reinstalled python using the same method (configure-make-make install)

youtube-dl worked perfectly!

hope it helped
greetings from Greece

---

### Post by coffeecat on 2011-10-28
Please read the forum policy on youtube downloading:

[http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

This is not supported.

Thread closed.

---

