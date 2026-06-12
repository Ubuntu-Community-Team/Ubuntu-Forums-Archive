---
title: "Live365 Radioio Rhythmbox Ubuntu 9.10"
date: 2010-01-26
forum: Multimedia Software
---

### Post by dln9 on 2010-01-26
Ubuntu 9.10

Rhythmbox 0.12.5

How does a person determine the URL of the audio stream for a Live365 broadcast in order to create a new radio station entry in Rhythmbox?  I would like to be able to access and listen to the audio stream completely from within Rhythmbox.  

Same question for a Radioio stream.  

Thanks in advance.

---

### Post by e.m.fields on 2010-02-07
This video should explain it without words:
[http://www.veoh.com/browse/videos/category/educational_and_howto/watch/v18942785XgZ28b64]("http://www.veoh.com/browse/videos/category/educational_and_howto/watch/v18942785XgZ28b64")

I'm trying to figure this out myself.
I'm sure there's some automated way to browse through live365 channels - I used to use StreamTuner, and it was great, but it seems to be broken.

In the meantime - [LIST=1]
[*]Go to Live365.com
[*]Click on a station you want.
[*]Select "open this with Winamp or other application"
[*]Select Save as PLS. (saves to your desktop as pls file.)
[*]Open the file with Gedit or another text editor. 
[*]You should see a list of http links - pick one and copy it.
[*]Go to rhythmbox. Go to Radio, right-click and select Add New Internet Radio.
[*]Paste the URL. Click save.
[*]Hit Play and enjoy.
[/LIST]

PLEASE MARK THIS THREAD AS SOLVED
if this was a solution for you, and make it easier for future people to find answers. 
peace, thanks!

---

### Post by dln9 on 2010-02-07
Thanks for the reply. 

I'm curious - did you actually succeed at doing this for Live365 stations?  

The video showed how to do this with Shoutcast stations.  A few points:  

First of all, Rhythmbox has an option to tune into Shoutcast stations, so this technique really isn't needed for Shoutcast stations.  ("Radiobrowser" in the "Library" - I don't recall if that is built in to Rhythmbox, or if it is an extra Rhythmbox feature that I downloaded and installed.)  

Second, the technique shown in the video doesn't address the problem of how to know which URL to copy and paste.  Some of these stations will present you with 20 or 30 URLs.  The one you pick today may not work tomorrow - tomorrow you may have to pick one of the other URLs for that station.  So, how would a person set this up so that Rhythmbox will always somehow figure out to look through all those URLs and pick one that will work?  (And - without clogging up your internet radio stations list with 20 - 30 entries for each station.)  

Anyway - The URL for Live365 that is downloaded appears to be in a format that Rhythmbox cannot work with.  Have you been able to make this work with Live365?  I'm interested in what you've learned.

---

### Post by mc4man on 2010-02-07
Not a fan of Live365 at all, prefer stations that don't force a player/service on you - though maybe in some cases they need that survive.

I actually do contribute to a few stations that are more open with access and quality - [Radio Paradise]("http://www.radioparadise.com/") is an ex.

Anyway  it's probably better to play them in the 365 player, though all the stations are available otherwise.
Some, if you go directly to station site, will have alternate means shown, or all 365 stations can be accessed by, or set in a player using - 

```
http://www.live365.com/play/XXXXXX
```

where XXXXXX.. is the station id

You can get the id by opening the 365 stream and looking in the page source of the pop up player (blue area

Ex. picked a [URL="http://www.live365.com/stations/cimg"]station at random
[/URL]

The url for a player is 
```
http://www.live365.com/play/334794
```

---

### Post by dln9 on 2010-02-08
Thanks for the feedback.  A couple questions, I'm not sure I'm understanding what you wrote.  

You said to "open the stream" to find the station id.  Can you explain what you mean by, "open the stream"?  I'm sorry, I don't know how to do that.  

Also, you then said that with the URL that includes the station ID, the station could be played in a player.  Which player(s) do you have in mind?  I tried the URL/station ID combo you included in your post, but when I put that into Rhythmbox as an internet radio URL, Rhythmbox didn't know what to do with it.  It said that the stream "has no data", or something like that.

---

### Post by yateendra on 2013-04-18
I'm largely unfamiliar with live365, but googled this forum post after attempting to hear stations there. I hope I might have stumbled on something that could be helpful.

I visited to two web pages associated with live365 stations using a browser (Firefox 20.0 on Kubuntu 12.10). These two station web pages each had a media player applet (probably implemented in JavaScript). After temporarily allowing the scipts to run, I observed that everything worked visually, but there was no sound. Just for kicks, I changed the user agent (this is possible using the "user agent switcher" Firefox add-on) to Internet Explorer 8. Upon refreshing the page, voila, the sound emerged!

In another case the applet was on a webpage proper to the broadcaster (not in the live365 domain) and I assume the player was embedded from live365. I was unable to make this embedded player work, but I noticed variations in the display when adding and subtracting script domains using NoScript, so I can't rule out that it could work.

I just realized my solution may lack some of the sophisticated options available using a media player like rhythmbox, but it seems good for casual listening.

My Test URLS:
[http://www.live365.com/stations/prayerfulliving](http://www.live365.com/stations/prayerfulliving)
[http://www.live365.com/stations/kurradio?site=pro](http://www.live365.com/stations/kurradio?site=pro)

Good Luck!

---

### Post by wildmanne39 on 2013-04-18
Thread closed. Please do not post in old threads.

---

