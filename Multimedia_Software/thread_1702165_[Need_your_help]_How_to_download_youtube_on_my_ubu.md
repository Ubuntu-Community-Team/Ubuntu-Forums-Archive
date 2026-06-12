---
title: "[Need your help] How to download youtube on my ubuntu 10.10 machine"
date: 2011-03-07
forum: Multimedia Software
---

### Post by brutus83 on 2011-03-07
Hi all,

I have few question regarding how to download youtube video on my
ubuntu 10.10 machine :
1. I use this step : $ sudo apt-get remove youtube-dl
and then
$ sudo wget [https://github.com/rg3/youtube-dl/raw/2011.02.25c/youtube-dl](https://github.com/rg3/youtube-dl/raw/2011.02.25c/youtube-dl)
-O /usr/local/bin/youtube-dl
Then, i type this command :
$ youtube-dl [http://www.youtube.com/watch?v=8OE4fkorNlk](http://www.youtube.com/watch?v=8OE4fkorNlk)
[youtube] Setting language
[youtube] 8OE4fkorNlk: Downloading video info webpage
[youtube] 8OE4fkorNlk: Extracting video information
[youtube] 8OE4fkorNlk: URL:
[http://www.youtube.com/get_video?video_id=8OE4fkorNlk&t=vjVQa1PpcFMhRSUQXqZND6FCsPZFex4b6Mn3EY0Cxww=&eurl=&el=detailpage&ps=default&gl=US&hl=en](http://www.youtube.com/get_video?video_id=8OE4fkorNlk&t=vjVQa1PpcFMhRSUQXqZND6FCsPZFex4b6Mn3EY0Cxww=&eurl=&el=detailpage&ps=default&gl=US&hl=en)
ERROR: format not available for video

And it's still not working.
Question :

(?) Why it does not work ?
(?) How to use Python in youtube-dl ?
(?) Why the format not available for video?

Thanks.

Cheers,
Anton

---

### Post by ron999 on 2011-03-07
Hi
Works OK for me:-
```
ron@ubuntu:~$ youtube-dl "http://www.youtube.com/watch?v=8OE4fkorNlk"
[youtube] Setting language
[youtube] 8OE4fkorNlk: Downloading video webpage
[youtube] 8OE4fkorNlk: Downloading video info webpage
[youtube] 8OE4fkorNlk: Extracting video information
[download] Destination: 8OE4fkorNlk.flv
[download] 100.0% of 18.76M at   79.78k/s ETA 00:00 

```

Make sure you have the latest version installed:-
```
sudo youtube-dl --update
```
**Updated to version 2011.02.25c**

Also 
```
sudo apt-get install python
```


...

---

### Post by brutus83 on 2011-03-08
Hi Ron, i checked again on my youtube-dl files in /usr/local/bin/youtube-dl and it was empty file.
(?) How do i download the youtube-dl from github-com ?
Because i already used these 2 commands, and both didn't work !
```
sudo wget http://github.com/rg3/youtube-dl/raw/2011.02.25c/youtube-dl -O /usr/local/bin/youtube-dl

```

The response on my terminal is :
```
brutus83@brutus-laptop:~$ sudo wget http://github.com/rg3/youtube-dl/raw/2011.02.25c/youtube-dl -O /usr/local/bin/youtube-dl
--2011-03-08 11:11:01--  http://github.com/rg3/youtube-dl/raw/2011.02.25c/youtube-dl
Resolving github.com... 207.97.227.239
Connecting to github.com|207.97.227.239|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://github.com/rg3/youtube-dl/raw/2011.02.25c/youtube-dl [following]
--2011-03-08 11:11:01--  https://github.com/rg3/youtube-dl/raw/2011.02.25c/youtube-dl
Connecting to github.com|207.97.227.239|:443... connected.
ERROR: certificate common name `*.github.com' doesn't match requested host name `github.com'.
To connect to github.com insecurely, use `--no-check-certificate'.

```

And i tried the 2nd command :
```
sudo curl http://github.com/rg3/youtube-dl/raw/2011.02.25c/youtube-dl -O /usr/local/bin/youtube-dl

```

And the response is :
```
brutus83@brutus-laptop:~$ sudo curl http://github.com/rg3/youtube-dl/raw/2011.02.25c/youtube-dl -O /usr/local/bin/youtube-dl
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   185  100   185    0     0    398      0 --:--:-- --:--:-- --:--:--  1491
curl: (3) <url> malformed

```

(?) Any idea? 
Do you have better command?
Thanks.

cheers,
Anton
> **ron999 said:**
> Hi
Works OK for me:-
```
ron@ubuntu:~$ youtube-dl "http://www.youtube.com/watch?v=8OE4fkorNlk"
[youtube] Setting language
[youtube] 8OE4fkorNlk: Downloading video webpage
[youtube] 8OE4fkorNlk: Downloading video info webpage
[youtube] 8OE4fkorNlk: Extracting video information
[download] Destination: 8OE4fkorNlk.flv
[download] 100.0% of 18.76M at   79.78k/s ETA 00:00 

```

Make sure you have the latest version installed:-
```
sudo youtube-dl --update
```
**Updated to version 2011.02.25c**

Also 
```
sudo apt-get install python
```


...

---

### Post by ron999 on 2011-03-08
Hi
I don't use github for youtube-dl.

Try this:-
```
sudo apt-get install youtube-dl
```
Then
```
sudo youtube-dl --update
```

My youtube-dl script is installed in /usr/bin folder.
So delete that empty youtube-dl file from your /usr/local/bin folder.

---

### Post by AbuSix on 2011-03-08
Hi if you need an alternative easy way:
if you are using firefox make sure you have Greasemonkey installed and then install this script

[http://userscripts.org/scripts/show/62634](http://userscripts.org/scripts/show/62634)

(in chrome you can install it directly without Greasemonkey)

> 
YouTube Video Download
By rossy!
Scans the YouTube page for all download formats, from iPod compatible MP4s to high definition 1080p. Compatible with Greasemonkey, Opera, Chrome and more. Runs entirely on the YouTube page without using any external sites. Also, WebM support.
Version: 2.3.7
License: MIT License 

---

### Post by brutus83 on 2011-03-08
Hi Ron, 

thanks for the advice.
stupid question :
(?) How to delete file youtube-dl in my /usr/local/bin folder ?
I've tried using command sudo del, sudo delete, sudo remove but it didn't work.
```
brutus83@brutus-laptop:/usr/local/bin$ ls
youtube-dl
brutus83@brutus-laptop:/usr/local/bin$ sudo remove youtube-dl
sudo: remove: command not found
brutus83@brutus-laptop:/usr/local/bin$ sudo del youtube-dl
sudo: del: command not found
brutus83@brutus-laptop:/usr/local/bin$ sudo delete youtube-dl
sudo: delete: command not found
brutus83@brutus-laptop:/usr/local/bin$ 


```
Thanks.
cheers,
Anton
> **ron999 said:**
> Hi
I don't use github for youtube-dl.

Try this:-
```
sudo apt-get install youtube-dl
```
Then
```
sudo youtube-dl --update
```

My youtube-dl script is installed in /usr/bin folder.
So delete that empty youtube-dl file from your /usr/local/bin folder.

---

### Post by ron999 on 2011-03-08
> **brutus83 said:**
> 
(?) How to delete file youtube-dl in my /usr/local/bin folder ?


I would use
```
gksudo nautilus /usr/local/bin
```
Then right-click and 'Move to trash'.

---

### Post by aeiah on 2011-03-08
> **brutus83 said:**
> Hi Ron, 

thanks for the advice.
stupid question :
(?) How to delete file youtube-dl in my /usr/local/bin folder ?
I've tried using command sudo del, sudo delete, sudo remove but it didn't work.
```
brutus83@brutus-laptop:/usr/local/bin$ ls
youtube-dl
brutus83@brutus-laptop:/usr/local/bin$ sudo remove youtube-dl
sudo: remove: command not found
brutus83@brutus-laptop:/usr/local/bin$ sudo del youtube-dl
sudo: del: command not found
brutus83@brutus-laptop:/usr/local/bin$ sudo delete youtube-dl
sudo: delete: command not found
brutus83@brutus-laptop:/usr/local/bin$ 


```
Thanks.
cheers,
Anton

the remove command in linux is rm
```

sudo rm /usr/local/bin/youtube-dl

```


i always think things like youtube-dl and clive can be rather pointless under most circumstances. you've used a browser to get to the youtube video, why not use it to download the video too with an extention or something. there's a good one for chromium that gives you a download link - i assume that greasemonkey one does a fine job for firefox with a similar thing

---

### Post by brutus83 on 2011-03-08
Ok thanks to Ron999 and Abusix.

I've solved the problem on how to download youtube on my ubuntu 10.10 machine (yeahhh!)

There are 4 options how you can download ubuntu :
1. You can use terminal-based command :
```
$ sudo apt-get install youtube-dl
$ sudo youtube-dl --update
$ sudo apt-get install python

```

Then, to download the youtube-video, simply type :
```
$ youtube-dl http://www.youtube.com/watch?v=wcVvE-BNWPs


```

2. You can use Videodownload helper
[HTML]http://www.vidohe.com/site.php?site=71[/HTML]

3. You can use Youtube-Video download for Greasemonkey
if you are using firefox make sure you have Greasemonkey installed and then install this script

[HTML]http://userscripts.org/scripts/show/62634[/HTML]

(in chrome you can install it directly without Greasemonkey)

4. You can use [HTML]http://keepvid.com/[/HTML]
But you need to install Java, here :
[HTML]http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com[/HTML]

Then, hopefully it will help you.

Cheers,
Anton

---

### Post by brutus83 on 2011-03-08
Hi AbuSix,

i have question :
(?) How to install Greasemonkey on my Firefox browser ?
Thanks.

Cheers,
Anton
> **AbuSix said:**
> Hi if you need an alternative easy way:
if you are using firefox make sure you have Greasemonkey installed and then install this script

[http://userscripts.org/scripts/show/62634](http://userscripts.org/scripts/show/62634)

(in chrome you can install it directly without Greasemonkey)

---

### Post by brutus83 on 2011-03-08
You can use this link
[HTML]https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/[/HTML]

> **brutus83 said:**
> Hi AbuSix,

i have question :
(?) How to install Greasemonkey on my Firefox browser ?
Thanks.

Cheers,
Anton

---

### Post by andrew.46 on 2011-03-08
> **brutus83 said:**
> 
(?) Any idea? 
Do you have better command?


Hi Anton,

First make sure that you are not using youtube-dl with youtube as this violates its EULA, (oops I meant 'Terms of Use'), youtube-dl can be used without restriction on *other* sites:

[http://rg3.github.com/youtube-dl/documentation.html#d4](http://rg3.github.com/youtube-dl/documentation.html#d4)

For this usage you can try the following commands:

```

$ sudo wget --no-check-certificate \
      http://github.com/rg3/youtube-dl/raw/2011.02.25c/youtube-dl \
      -O /usr/local/bin/youtube-dl
$ sudo chmod +x /usr/local/bin/youtube-dl

```

although it sounds as if you have it all sorted now :).

Andrew

---

### Post by brutus83 on 2011-03-08
Hi Andrew,

i did not use github.com as it was required "check-certificates".
i went back to youtube-dl provided on ubuntu.
oh yeah, i have question :
(?) What is the difference between youtube-dl command which i used from ubuntu, and from github.com ?
thanks

cheers,
anton

> **andrew.46 said:**
> Hi Anton,

First make sure that you are not using youtube-dl with youtube as this violates its EULA, (oops I meant 'Terms of Use'), youtube-dl can be used without restriction on *other* sites:

[http://rg3.github.com/youtube-dl/documentation.html#d4](http://rg3.github.com/youtube-dl/documentation.html#d4)

For this usage you can try the following commands:

```

$ sudo wget --no-check-certificate \
      http://github.com/rg3/youtube-dl/raw/2011.02.25c/youtube-dl \
      -O /usr/local/bin/youtube-dl
$ sudo chmod +x /usr/local/bin/youtube-dl

```

although it sounds as if you have it all sorted now :).

Andrew

---

### Post by andrew.46 on 2011-03-08
> **brutus83 said:**
>  What is the difference between youtube-dl command which i used from ubuntu, and from github.com ?

The Ubuntu repository carries an older version of youtube-dl while the version that is found at [http://rg3.github.com/youtube-dl/](http://rg3.github.com/youtube-dl/) is current and much more likely to work :). As for the actual commandlines needed, this can be seen by running the following:

```

youtube-dl --help

```

Some great tips for the output format [here...]("http://rg3.github.com/youtube-dl/documentation.html#d7")

Andrew

---

### Post by brutus83 on 2011-03-09
Ok Andrew, thanks for your sharing.
i'll put that on my youtube-downloader manual :-)

> **andrew.46 said:**
> The Ubuntu repository carries an older version of youtube-dl while the version that is found at [http://rg3.github.com/youtube-dl/](http://rg3.github.com/youtube-dl/) is current and much more likely to work :). 
Andrew

---

### Post by SinkingRocket on 2011-06-08
> **AbuSix said:**
> Hi if you need an alternative easy way:
if you are using firefox make sure you have Greasemonkey installed and then install this script

[http://userscripts.org/scripts/show/62634](http://userscripts.org/scripts/show/62634)

(in chrome you can install it directly without Greasemonkey)

Wow this worked for me!!!thanks alot!! no more going to keepvid.com to download vids lol

---

### Post by tg3793 on 2011-06-10
I highly recommend Minitube (in the repositories) for those like myself who have problems with caching Youtube videos. The program looks a bit retro but it works great.

And you don't even have to wait until the video is completed downloaded. You can watch partial videos with VLC or any other player that will watch videos in packets (not quite the right way of putting but you get my drift).

---

### Post by boscharun on 2012-01-20
Full proof and easiest solution is to use ClipGrab. 

It gives many cool features like choosing the quality and format of video to download. There is also a search and download video feature as well.

[ClipGrab to download youtube video in Ubuntu]("http://www.skipser.com/p/2/p/download-youtube-video-in-ubuntu.html").

---

### Post by nothingspecial on 2012-01-20
[http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

Closed

---

