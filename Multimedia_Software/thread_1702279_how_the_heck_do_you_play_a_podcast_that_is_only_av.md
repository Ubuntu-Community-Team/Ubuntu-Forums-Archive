---
title: "how the heck do you play a podcast that is only available from itunes?"
date: 2011-03-07
forum: Multimedia Software
---

### Post by fpgdu on 2011-03-07
I'm trying to download a podcast, for example, exactly like the ones on this page [http://itunes.apple.com/us/podcast/health-talk-dr-ronald-hoffman/id203430536](http://itunes.apple.com/us/podcast/health-talk-dr-ronald-hoffman/id203430536)

and I can't seem to get it to play in any ubuntu player. I've also tried several old versions of iTunes on Wine. It just wont work. An error about this, an error about that, and, the biggest problem: no response at all when i click the play button or any button to try to download/update the podcast.

What is the secret here?

---

### Post by StephenDavison on 2011-03-07
Try the following link with something like gpodder or Rhythmbox and let me know if it works:
[http://www.wor710.com/pages/podcast/405.rss](http://www.wor710.com/pages/podcast/405.rss)

I came by the RSS feed link as follows.
Pointed Firefox to [http://www.wor710.com](http://www.wor710.com)
Clicked on the Podcasts link at the top of the page
Scrolled down to this show
Clicked the Subscribe button(link)
Opted to subscribe with LiveBookmarks and added the bookmark to Firefox
Looked at the bookmark properties to get the link to the RSS feed.

There's probably an easier way.

---

### Post by ron999 on 2011-03-07
I don't know whether you think this is any easier....

Right-click on the page and 'View page source'
then
Use **Ctrl-F** to search for **mp3**

This shows:-

> Health Talk with Dr. Ronald Hoffman - March 5, 2011 - Hour 1
[http://podcast.wor710.com/wor/2831802.mp3](http://podcast.wor710.com/wor/2831802.mp3)

> Health Talk with Dr. Ronald Hoffman - March 5, 2011 - Hour 2
[http://podcast.wor710.com/wor/2831792.mp3](http://podcast.wor710.com/wor/2831792.mp3)

> Health Talk with Dr.Ronald Hoffman-March 4,2011
[http://podcast.wor710.com/wor/2831125.mp3](http://podcast.wor710.com/wor/2831125.mp3)

Download them like this:-
```
wget http://podcast.wor710.com/wor/2831802.mp3
```
```
wget http://podcast.wor710.com/wor/2831792.mp3
```
```
wget http://podcast.wor710.com/wor/2831125.mp3
```

---

### Post by fpgdu on 2011-03-07
How did you get that link? I'd like to know so I can play other podcasts in the future that are only available on itunes.

---

### Post by StephenDavison on 2011-03-07
That probably is easier. I'm always thinking in terms of subscribing rather than downloading, even though the OP did write download.

---

### Post by StephenDavison on 2011-03-07
> **fpgdu said:**
> How did you get that link? I'd like to know so I can play other podcasts in the future that are only available on itunes.

If you're asking about the link to the WOR 710 page(s), it was easy to find given the information at the iTunes link you provided:  title and radio station call letters.  I used Google to find the web page of the radio station from which the podcast originated just by supplying the title of it.

Various podcast directories out there on the interwebs can help too.  Just because it is available on iTunes doesn't mean it is only available on iTunes. ;-)

---

### Post by fpgdu on 2011-03-07
> **StephenDavison said:**
> If you're asking about the link to the WOR 710 page(s), it was easy to find given the information at the iTunes link you provided:  title and radio station call letters.  I used Google to find the web page of the radio station from which the podcast originated just by supplying the title of it.

Various podcast directories out there on the interwebs can help too.  Just because it is available on iTunes doesn't mean it is only available on iTunes. ;-)

:cry: I've been searching Google up and down for the podcast im searching for, it is ONLY available on iTunes. I've also tried wget'ing the podcasts from the iTunes web page they're listed on--- that also didn't work.

---

### Post by fpgdu on 2011-03-07
> **ron999 said:**
> I don't know whether you think this is any easier....

Right-click on the page and 'View page source'
then
Use **Ctrl-F** to search for **mp3**

This shows:-





Download them like this:-
```
wget http://podcast.wor710.com/wor/2831802.mp3
``````
wget http://podcast.wor710.com/wor/2831792.mp3
``````
wget http://podcast.wor710.com/wor/2831125.mp3
```

Thanks ron999. Please see my post above.

---

### Post by cfhowlett on 2011-03-07
On the Itunes page for your podcast, see if there's a link to an associated website.  If so, search that site for the show notes.  You'll likely find that you can download individual episodes there.  If you look very carefully, you should find the rss feed.  Copy/paste that into your podcatcher (I use Rythmbox) and you should be fixed.

Example:

Podcasting for Dummies site: [http://www.wiley.com/WileyCDA/WileyTitle/productCd-047027557X,descCd-NOTE.html](http://www.wiley.com/WileyCDA/WileyTitle/productCd-047027557X,descCd-NOTE.html)


Podcasting for Dummmies rss feed: [http://etips.dummies.com/rss/podcastingfd.xml](http://etips.dummies.com/rss/podcastingfd.xml)

---

### Post by StephenDavison on 2011-03-07
> **fpgdu said:**
> :cry: I've been searching Google up and down for the podcast im searching for, it is ONLY available on iTunes. I've also tried wget'ing the podcasts from the iTunes web page they're listed on--- that also didn't work.

I get you now: "others exactly like" the one in your original post.  Would you mind posting another example -- of one only found in iTunes?

---

### Post by fpgdu on 2011-03-07
> **charlesh1609 said:**
> On the Itunes page for your podcast, see if there's a link to an associated website.  If so, search that site for the show notes.  You'll likely find that you can download individual episodes there.  If you look very carefully, you should find the rss feed.  Copy/paste that into your podcatcher (I use Rythmbox) and you should be fixed.

Example:

Podcasting for Dummies site: [http://www.wiley.com/WileyCDA/WileyTitle/productCd-047027557X,descCd-NOTE.html](http://www.wiley.com/WileyCDA/WileyTitle/productCd-047027557X,descCd-NOTE.html)


Podcasting for Dummmies rss feed: [http://etips.dummies.com/rss/podcastingfd.xml](http://etips.dummies.com/rss/podcastingfd.xml)

Thanks. I couldnt find the rss feed but at least now i can listen to the podcasts one-by-one.

---

### Post by markthekdeguy on 2011-03-07
sorry i'm late. theres a website to make it easier :)

[http://picklemonkey.net/flipper/](http://picklemonkey.net/flipper/)

---

### Post by nothingspecial on 2011-03-08
Sorry I'm even later. There is an app for that :-\"
```

wget http://sourceforge.net/projects/tunesviewer/files/tunesviewer_1.0.deb
```
```

sudo dpkg -i tunesviewer_1.0.deb
```

You'll find it under your internet menu.

Cheers

---

### Post by shantiq on 2011-03-08
> **ron999 said:**
> I don't know whether you think this is any easier....

Right-click on the page and 'View page source'
then
Use **Ctrl-F** to search for **mp3**

This shows:-





Download them like this:-
```
wget http://podcast.wor710.com/wor/2831802.mp3
```
```
wget http://podcast.wor710.com/wor/2831792.mp3
```
```
wget http://podcast.wor710.com/wor/2831125.mp3
```


love this Ron.  very neat:KS

---

