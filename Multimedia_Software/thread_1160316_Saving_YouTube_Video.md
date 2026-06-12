---
title: "Saving YouTube Video"
date: 2009-05-15
forum: Multimedia Software
---

### Post by cneil on 2009-05-15
I've got a trick that I've used with Ubuntu for quite some time.  When I like  a Youtube video or any flash video, I just go to my /tmp folder and pull out the video.  Whenever I want to watch the video, I can launchthe file in VLC player.

However, tonight I tried it with a youtube video and it didn't seem to work.  VLC didn't read the file?

Anyone know what change has happened?

---

### Post by Labello on 2009-05-15
try to append ".flv" to the clips filename. maybe this might help you out.

---

### Post by FakeOutdoorsman on 2009-05-15
I explained one reason why it may not work in this thread: [Re: temporary flash videos](http://ubuntuforums.org/showpost.php?p=7284874&postcount=4).

---

### Post by soltanis on 2009-05-15
A public domain script for downloading youtube videos, you might find useful.

```

#!/usr/bin/perl
unless ($#ARGV == 1 && $ARGV[0]=~/^http\:\/\//i && $ARGV[0]=~/youtube/i) {
        print "\tUsage: mytube [Youtube URL] [destination]\n";
        exit;
}
print "Downloading HTML...\n";
$fsU = `wget -q -O .mytubeTMP.tmp $ARGV[0] && cat .mytubeTMP.tmp | grep fullscreenUrl`;
$fsU =~ /(video_id[\w\W]*)\;/i;
print "Downloading .flv...\n";
system("wget -q -O $ARGV[1] 'http://www.youtube.com/get_video?$1")

```

Usage: (script) (URL) (dest. file)

---

### Post by ckonestroh on 2009-05-23
Forget that go to Youtube watch Greasemonky...


Download addons for firefox that allow you to download streaming video...


You people are killing me....

good luck...

---

### Post by Rhubarb on 2009-05-23
Or you could quite simply grab a nice little script to grab it for you:
```
sudo aptitude install youtube-dl
```

Then you can use it like this:
```
youtube-dl -b -t http://www.youtube.com/watch?v=Yu_moia-oVI
```

---

### Post by imbjr on 2009-05-23
Try this as a bookmarklet in Firefox:

```

javascript:if(document.location.href.match(/http:\/\/[a-zA-Z\.]*youtube\.com\/watch/)){document.location.href='http://www.youtube.com/get_video?fmt='+(isHDAvailable?'22':'18')+'&video_id='+swfArgs['video_id']+'&t='+swfArgs['t']}

```

Click it when you're watching a video you want to download and you'll get an mp4 to download and a HD if its available.

---

