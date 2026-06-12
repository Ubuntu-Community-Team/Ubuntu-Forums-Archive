---
title: "Can't download podcasts"
date: 2009-05-01
forum: Multimedia Software
---

### Post by glendavee on 2009-05-01
I've just updated to Jaunty. I've tried to subscribe to BBC podcasts using both Rythmbox and Banshee. Neither work. Rythmbox gives following error :

[COLOR="Red"]The URL 'http://downloads.bbc.co.uk/podcasts/radio4/iot/iot_20090430-1045a.mp3' does not appear to be a podcast feed. It may be the wrong URL, or the feed may be broken. Would you like Rhythmbox to attempt to use it anyway?[/COLOR]

Nothing happens at all with Banshee.

What am I doing wrong?

---

### Post by mister_p_1998 on 2009-05-01
Try Icepodder.. dead simple...

---

### Post by bobbob1016 on 2009-05-01
> **mister_p_1998 said:**
> Try Icepodder.. dead simple...

"Use this completely different program" should only be a last resort.  More so when his problem seems to be a problem with the feeds, and not the program.  I'd say remove and re-add the feeds to rhythmbox and/or banshee.  If that doesn't work, see if anyone else can get podcasts from there.

---

### Post by Windsurfer619 on 2009-05-01
Typically, feeds do not end in ".mp3". Try something that either ends in a number, or .xml. If you open the link in Firefox, it should ask you if you want to open it in google reader or something like that.

---

### Post by glendavee on 2009-05-01
I think feed is ok - I can play it online. What I want to do is transfer it to ipod via Banshee/Rhthmbox.
Tried to instal Icepodder, but can't find source for python.xmms which is a dependency, ie 
[COLOR="Red"]david@david-desktop:~$ sudo apt-get install build-essential python python-xmms bittorrent python-wxgtk2.6 python-pyrss2gen python-feedparser
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
python is already the newest version.
Package python-xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-xmms has no installation candidate
david@david-desktop:~$ [/COLOR]

---

### Post by Windsurfer619 on 2009-05-01
"[COLOR=Red]http://downloads.bbc.co.uk/podcasts/radio4/iot/iot_20090430-1045a.mp3[COLOR=Black]" is not a feed! It is an MP3 file. A feed is an XML file that lists links to MP3 files, along with titles and descriptions. A feed reader like Rhythmbox downloads this file and checks it for changes. If there is a new link to an MP3 file, it will go to that link (which is not a "feed", but rather an MP3 file) and download that.
You'll need an XML file, like I said.

For instance, the feed for "In Our Time" is "http://downloads.bbc.co.uk/podcasts/radio4/iot/rss.xml"
[/COLOR][/COLOR]

---

### Post by Ericyzfr1 on 2009-05-01
> **glendavee said:**
> I've just updated to Jaunty. I've tried to subscribe to BBC podcasts using both Rythmbox and Banshee. Neither work. Rythmbox gives following error :

[COLOR="Red"]The URL 'http://downloads.bbc.co.uk/podcasts/radio4/iot/iot_20090430-1045a.mp3' does not appear to be a podcast feed. It may be the wrong URL, or the feed may be broken. Would you like Rhythmbox to attempt to use it anyway?[/COLOR]

Nothing happens at all with Banshee.

What am I doing wrong?

The link appears to be the file location, not the feed. Should look like this

[http://downloads.bbc.co.uk/podcasts/radio4/r4choice/rss.xml](http://downloads.bbc.co.uk/podcasts/radio4/r4choice/rss.xml)

---

### Post by glendavee on 2009-05-02
Thanks, Windsurfer619 and Ericyzfr1. Problem solved using the .xml file

---

### Post by AlanaLearningLinux on 2010-07-27
Hey all, 
I'm a beginner to Linux and I'm finally starting to get everything set up. The one problem I'm having is trying to download and subscribe to podcasts through Banshee and Rhythmbox.  After reading this post I tried 'This American life' url that had the xml file which you suggested and it didn't work for me.  I got an error message. 

What am I doing wrong?  Or should I download a different music player to get podcasts?

Thanks in advance!

---

### Post by NFblaze on 2010-07-27
Alana, I think that feed from that site 

[http://feeds.thisamericanlife.org/talpodcast/](http://feeds.thisamericanlife.org/talpodcast/)

is that. And This American Life has moved to only broadcasting the last podcast on the feed. I believ you have to subscribe or donate to get the full feed now.

---

### Post by AlanaLearningLinux on 2010-07-27
Thanks for getting back to me.

The URL I used was [http://www.thisamericanlife.org/podcast.xm](http://www.thisamericanlife.org/podcast.xm) but I still don't understand why these programs won't let me subscribe to the feeds.  I understand that This American Life only updates with the last episode, but I can't seem to get them into my feed.  How do I do this?

---

### Post by NFblaze on 2010-07-27
[http://www.thisamericanlife.org/podcast.xm](http://www.thisamericanlife.org/podcast.xm)

should have an 'l':

[http://www.thisamericanlife.org/podcast.xml](http://www.thisamericanlife.org/podcast.xml)

Second try, File > Add Podcast Feed

---

### Post by AlanaLearningLinux on 2010-07-27
Ah yes, I think I may have just deleted the 'l' when typing this, but I tried it with the xml, as well as the File--> Add Podcast Feed.  Rhythmbox is giving me this message: 

There was a problem adding this podcast: Unable to parse the feed contents.  Please verify the URL: [http://www.thisamericanlife.org/podcast.xml](http://www.thisamericanlife.org/podcast.xml)

---

### Post by NFblaze on 2010-07-27
So, I came home I checked my feed and I have [http://feeds.thisamericanlife.org/talpodcast?format=xml](http://feeds.thisamericanlife.org/talpodcast?format=xml)

Try that.

---

### Post by AlanaLearningLinux on 2010-07-27
I put that in but I got the same message: There was a problem adding this podcast: Unable to parse the feed contents.  Please verify the URL: [http://feeds.thisamericanlife.org/talpodcast?format=xml](http://feeds.thisamericanlife.org/talpodcast?format=xml).

Thanks again!

---

### Post by NFblaze on 2010-07-28
This might be a bug. I say try restarting the application and computer. If it still doesnt work, you may have to file a bug report.

---

