---
title: "Rhythmbox Won't Parse Podcast Feeds in Jaunty"
date: 2009-04-24
forum: Multimedia Software
---

### Post by vishnu on 2009-04-24
I love Rhythmbox and it's iPod functionality.  I really don't want to leave it but I will have to if this problem isn't solved.  That or go back to 8.10.

Since upgrading to Jaunty when I add a podcast to Rhythmbox I get:

There was a problem adding this podcast: Unable to parse the feed contents.  Please verify the URL: [http://downloads.bbc.co.uk/podcasts/radio2/ross/rss.xml](http://downloads.bbc.co.uk/podcasts/radio2/ross/rss.xml).  Would you like to add the feed anyway.

The feed works, or at least did in Rhythmbox under Intrepid.  Anyone else get this?  I can use this feed in gPodder and other podcast apps but I want to use it in Rhythmbox.  I tried to reinstall GVFS Backend as someone suggested in another thread but no luck.

---

### Post by willharris on 2009-04-25
I get this exact same error as well, it doesn't seem to be a proxy issue since lastfm and magnatune work. They had a problem with this before in Intrepid and I reported the bug to them, they fixed it briefly and then it came back in jaunty. 

so far my solution has been:

sudo apt-get remove rhythmbox
sudo apt-get install banshee or amarok

---

### Post by vishnu on 2009-04-25
my solution has been to go back to 8.10 for now.
if it ain't broke don't fix it so i'm staying with what works for me for now.

i had a problem in rhythmbox once before where deleting tracks from the ipod didn't work correctly.  took a few releaes and they sorted it.  i'll just be patient i suppose.

---

### Post by vishnu on 2009-06-01
still no luck with this. i tried again today and wiped out my rhythmbox install by using apt-get purge and then deleting all ./ folders like .gnome2/rhythmbox.

anyone got any ideas????

---

### Post by edwardtilbury on 2009-08-21
same here... I have 9.04 64bit.. I'm going to uninstall Rythmbox and try something else :(

---

### Post by vishnu on 2009-08-22
must have been something in my profile and ./ folders because I made a new user and it worked fine with it. so i migrated over to a new user login and all is well.

---

### Post by edwardtilbury on 2009-08-27
Since I need to sync my iphone anyways, what I did was share my /username folder in virtualbox in vista... 

I download my podcasts in a virtual box of itunes.. and it saves it to my music folder.. then I play it in rhythmbox , works great.

---

### Post by Bluebris on 2009-11-22
> **vishnu said:**
> I love Rhythmbox and it's iPod functionality.  I really don't want to leave it but I will have to if this problem isn't solved.  That or go back to 8.10.

Since upgrading to Jaunty when I add a podcast to Rhythmbox I get:

There was a problem adding this podcast: Unable to parse the feed contents.  Please verify the URL: [http://downloads.bbc.co.uk/podcasts/radio2/ross/rss.xml](http://downloads.bbc.co.uk/podcasts/radio2/ross/rss.xml).  Would you like to add the feed anyway.

The feed works, or at least did in Rhythmbox under Intrepid.  Anyone else get this?  I can use this feed in gPodder and other podcast apps but I want to use it in Rhythmbox.  I tried to reinstall GVFS Backend as someone suggested in another thread but no luck.

  The only way i've been able to get this to work, is by installing gpodder from synaptic.  Also works on password protected podcasts (which i think might be the cause of this problem).

---

### Post by cytenticle on 2010-05-23
Have a solution for password protected podcasts and rhythmbox

When you add the podcast feed add it in this format

```
http://username:password@podcasturl.com
```
for example

your username - user
your password - password
podcasturl - secretpodcast.com/podcast.xml

the way you would add the feed is -

```
http://user:password@secretpodcast.com/podcast.xml
```

Hope that helps - worked for me.

---

