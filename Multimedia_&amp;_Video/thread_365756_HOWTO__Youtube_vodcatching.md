---
title: "HOWTO:  Youtube vodcatching"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by Mateo on 2007-02-20
[http://www.mackers.com/projects/theyoke/](http://www.mackers.com/projects/theyoke/)
[http://www.arrakis.es/~rggi3/youtube-dl/](http://www.arrakis.es/~rggi3/youtube-dl/)

This utilizes two excellent projects to automatically download new videos from youtube rss feeds.

_**1) Install theyoke**_

```
wget http://www.mackers.com/projects/theyoke/theyoke.txt
chmod 755 theyoke.txt
sudo mv theyoke.txt /usr/bin/theyoke
```

Now to set up the yoke:

```
theyoke
```

That should create your directories.  Now edit the feeds file with some feeds.

```
gedit ~/.theyoke/feeds
```

Here are a couple of examples, one is the series "God Inc." the other is NBC's feed.

[http://www.youtube.com/rss/user/francisstokesdotcom/videos.rss](http://www.youtube.com/rss/user/francisstokesdotcom/videos.rss)
[http://www.youtube.com/rss/user/nbc/videos.rss](http://www.youtube.com/rss/user/nbc/videos.rss)

Next we'll run theyoke once to make sure we don't accidentally download too many files.

```
theyoke --link --no-feedname --no-title > ~/.theyoke/videos
```

now edit the created file and look and see if you want to download any of the videos, and which you don't.  In the future all new videos will be downloaded.

```
gedit ~/.theyoke/videos
```

_**1) Install youtube-dl**_

```
wget http://www.arrakis.es/~rggi3/youtube-dl/youtube-dl
chmod 755 youtube-dl
sudo mv youtube-dl /usr/bin/
```

Now, if before you edited the videos file and want to download what you left, run this:

```
while read line; do youtube-dl -f "${line}"; done < <(cat ~/.theyoke/videos)
```

**Warning**:  if you don't run this now, it'll likely overwrite this file later when you run the script.  The only way to fix this is to delete the files in ~/.theyoke/.feeds and then rerun theyoke command I showed before.  Then edit the file to keep the videos you want, then run the command directly above.  From now on you can just run the script to download all new videos.

_**3) Configure and install script**_

Otherwise, this is the script:

```
gedit ytcatcher
```

```
#/bin/bash
theyoke --link --no-feedname --no-title > ~/.theyoke/videos
cd ~/
while read line; do youtube-dl -t "${line}"; done < <(cat ~/.theyoke/videos)
rm -f ~/.theyoke/videos
exit
```

after saving...

```
chmod 755 ytcatcher
sudo mv ytcatcher /usr/local/bin/
```

Now you can run it any time by typing ytcatcher.  You can create a launcher, add a rule to crontab, whatever meets your needs.

---

### Post by just1dave on 2008-01-27
Thanks this helped a lot!

---

