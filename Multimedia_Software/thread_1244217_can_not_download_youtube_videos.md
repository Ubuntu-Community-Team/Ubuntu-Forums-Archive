---
title: "can not download youtube videos"
date: 2009-08-19
forum: Multimedia Software
---

### Post by bilol on 2009-08-19
Hi all,
 I can watch some  youtube videos but can not download.
I did the following:
 sudo apt-get install youtube-dl
 youtube-dl -u username -p password "url"
But I am getting the following error:
```
Logging in... done.
Confirming age... done.
Retrieving video webpage... done.
Extracting URL "t" parameter... failed.
Error: unable to extract URL "t" parameter.
Try again several times. It may be a temporary problem.
Other typical problems:

* Video no longer exists.
* Video requires age confirmation but you did not provide an account.
* You provided the account data, but it is not valid.
* The connection was cut suddenly for some reason.
* YouTube changed their system, and the program no longer works.

Try to confirm you are able to view the video using a web browser.
Use the same video URL and account information, if needed, with this program.
When using a proxy, make sure http_proxy has http://host:port format.
Try again several times and contact me if the problem persists.
```

need your help.....

---

### Post by pmlxuser on 2009-08-19
if you can watch them, then just open ~/.mozilla/firefox/*whatevercharacters.default/Cache/

repalce *whatever characters with what you find in firefox folder similar to 'y7ji2hue.default'

you are going to see all the flv movies you have watched. just copy then to your desired folder and add .flv and change the names to make more sense.

---

### Post by stinger30au on 2009-08-19
[this will help]("http://www.google.com.au/search?hl=en&q=download+youtube+mp4&btnG=Google+Search&meta=&aq=f&oq=")

---

### Post by bilol on 2009-08-19
Thanks pmlxuser,
Do I need to watch the whole movie clip to get it from ~/.mozilla/firefox/*whatevercharacters.default/Cache/ ? 
If yes ,then please suggest another method.

---

### Post by pmlxuser on 2009-08-19
> **bilol said:**
> Thanks pmlxuser,
Do I need to watch the whole movie clip to get it from ~/.mozilla/firefox/*whatevercharacters.default/Cache/ ? 
If yes ,then please suggest another method.

unfortunately yes.

so here is another way

open firefox goto tools then add-ons search "Ant.com" or just look at "download"

---

### Post by andrew.46 on 2009-08-19
Hi bilol,

> **bilol said:**
> ```
 sudo apt-get install youtube-dl
 youtube-dl -u username -p password "url"
```

The repository version of youtube-dl is quite old and this could be part of the problem. Perhaps try a newer version:

```
$ sudo apt-get remove youtube-dl
$ sudo wget http://bitbucket.org/rg3/youtube-dl/raw/2009.08.08/youtube-dl -O /usr/local/bin/youtube-dl
$ sudo chmod +x /usr/local/bin/youtube-dl
```

Hopefully you will have more luck with this version, try the *-b* option as well:

```
-b, --best-quality  download the best quality video possible
```

All the best,

Andrew

---

### Post by matrixx007 on 2009-08-19
[SIZE=4][COLOR=Red]I have found a another website from where you can watch & download youtube video in different format. no need to download any software.
link is [http://video.deshibinodon.com](http://video.deshibinodon.com)[/COLOR][/SIZE]

---

### Post by Raffles10 on 2009-08-19
[This]("https://addons.mozilla.org/en-US/firefox/addon/3006") will do it simply enough.

---

### Post by lisati on 2009-08-19
Careful: this thread might be encouraging people to violate Youtube's terms and conditions. Please read the discussion at [http://ubuntuforums.org/showthread.php?t=1165163](http://ubuntuforums.org/showthread.php?t=1165163)

---

### Post by ibutho on 2009-08-19
I use an app called [CaC]("http://sourceforge.net/projects/cac/") (Catch and Convert). Never had a problem downloading youtube videos with it.

---

### Post by wotsit on 2009-08-19
Please correct me if I am wrong... But won't the vids be saved as a .flv in the tmp folder after they have loaded fully? Then, would you not be able to just click and drag them on to the desktop or something, so that they don't get wiped from tmp?

Would save you typing in the terminal or downloading any programs to do it.

---

### Post by lisati on 2009-08-19
> **ibutho said:**
> I use an app called [CaC]("http://sourceforge.net/projects/cac/") (Catch and Convert). Never had a problem downloading youtube videos with it.

As long as no-one downloads my contributions to Youtube without my permission. I have a couple there that other people hold the copyright for and they might get upset if people are downloading them willy-nilly.

---

### Post by bilol on 2009-08-26
Thank you all for your valuable suggestions.
Thanks a lot andrew.46.The method worked nicely.

---

