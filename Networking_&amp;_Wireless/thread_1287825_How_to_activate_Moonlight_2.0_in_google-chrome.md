---
title: "How to activate Moonlight 2.0 in google-chrome?"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by vickoxy on 2009-10-10
Hi,
i just install with shiretoko3.5 moonlight 2 beta 5 on my dell mini 9. Anyone knows is it possible to activate this plugin in google-chrome?

Flash and Java were just accepted from Firefox setup...

Thanks

---

### Post by vickoxy on 2009-10-11
Well, i made some progress, but still ca not watch silverlight movies. I found moonlight 2:

```
/home/++++/.mozilla/firefox/dz8sws51.default/extensions/moonlight@novell.com/plugins/
```

Here is one file and one folder:
```
libmoonloaderxpi.so
moonlight
```-here i have some files (see pict. 1)

I made shortcut in ```
/opt/google/chrome/plugins/
``` to ```
libmoonloaderxpi.so
```

But it shows that this plugin is crashed when i try to watch silverlight movies.

Should i point the shortcut to some other file? Does anyone knows what really plugin is there?

---

### Post by vickoxy on 2009-10-11
Anyone tried to activate moonlight 2 in chrome/chromium?

---

### Post by MelDJ on 2009-10-11
tried: [http://blog.bodhizazen.net/linux/how-to-moonlight/?](http://blog.bodhizazen.net/linux/how-to-moonlight/?)

---

### Post by vickoxy on 2009-10-11
Moonlight 2 is working in firefox 3/3.5, but the chrome is problem. It loads something, i even get play icon for few seconds, but then it reports crashing...

If i try to open:
[http://www.bug.hr/bugtv/dell-inspiron-mini-10v/610.aspx](http://www.bug.hr/bugtv/dell-inspiron-mini-10v/610.aspx)

I get crash report-see picture.

About loading-see pict.

Thanks!

---

### Post by vickoxy on 2009-10-11
Bump!

---

### Post by vickoxy on 2009-11-13
Anyone tried? Is there something new with silverlight 2/moonlight 2 and chromium browser?

---

### Post by buu700 on 2009-12-19
Just extract the contents of the plugins folder in the [.xpi archive]("http://www.go-mono.com/moonlight/download.aspx") to /usr/lib/mozilla/plugins/. I just tried it and it works.

---

### Post by vickoxy on 2009-12-19
> **buu700 said:**
> Just extract the contents of the plugins folder in the [.xpi archive]("http://www.go-mono.com/moonlight/download.aspx") to /usr/lib/mozilla/plugins/. I just tried it and it works.

Thanks for answer but nothing by me. When i try to open this page:
[http://www.bug.hr/bugtv/panasonic-viera-cast/621.aspx](http://www.bug.hr/bugtv/panasonic-viera-cast/621.aspx)

i get error report (see picture)

---

### Post by buu700 on 2009-12-19
Hm, apparently it's a codec problem. It crashes in Chromium for me as well, but in Firefox it prompts to install codecs. Installing the codecs in Firefox and moving ~/.mozilla/plugins/moonlight/silverlight-media-pack-linux-x64-16-1.so to /usr/lib/mozilla/plugins/ didn't fix the crashes in Chromium, but Firefox still detected the plugin despite the new location. Not sure how to fix this.

---

### Post by vickoxy on 2010-02-15
bump

---

### Post by krige on 2010-03-25
I installed the moonlight add-on on Firefox and it worked fine. I hope the guys working on moonlight will release soon an equivalent Chrome extension.

---

### Post by vickoxy on 2010-04-05
Bump-still nothing. Using firefox 3.6 and working fine... but chrome still nothing...

---

### Post by dwarfolo on 2010-04-17
This "alpha" release of Moonlight seems to partially work for me.

[http://go-mono.com/moonlight/prerelease.aspx](http://go-mono.com/moonlight/prerelease.aspx)

Chromium 5.0.379.0 (44736) Ubuntu
No crash since now but most movies are not playable.

[http://tirania.org/blog/archive/2010/Apr-16.html](http://tirania.org/blog/archive/2010/Apr-16.html)

I think we're going to wait just a little more.

---

### Post by vickoxy on 2010-04-17
> **dwarfolo said:**
> This "alpha" release of Moonlight seems to partially work for me.

[http://go-mono.com/moonlight/prerelease.aspx](http://go-mono.com/moonlight/prerelease.aspx)

Chromium 5.0.379.0 (44736) Ubuntu
No crash since now but most movies are not playable.

[http://tirania.org/blog/archive/2010/Apr-16.html](http://tirania.org/blog/archive/2010/Apr-16.html)

I think we're going to wait just a little more.

I tried to install this add on with firefox 3..3 but i can´t. How did you install it?

---

### Post by dwarfolo on 2010-04-17
In Chromium just click on the download link and it will be installed as an extension 
[http://go-mono.com/moonlight/downloads/2.99.0.6/novell-moonlight-2.99.0.6-i586.crx](http://go-mono.com/moonlight/downloads/2.99.0.6/novell-moonlight-2.99.0.6-i586.crx)

[ATTACH]153549[/ATTACH]

I haven't tryed to install the plugin for Firefox.
Which version of Chromium are you using?

---

### Post by vickoxy on 2010-04-17
> **dwarfolo said:**
> In Chromium just click on the download link and it will be installed as an extension 
[http://go-mono.com/moonlight/downloads/2.99.0.6/novell-moonlight-2.99.0.6-i586.crx](http://go-mono.com/moonlight/downloads/2.99.0.6/novell-moonlight-2.99.0.6-i586.crx)

[ATTACH]153549[/ATTACH]

I haven't tryed to install the plugin for Firefox.
Which version of Chromium are you using?

Thanks for answer-i installed it. No crushing-but also no working...

I am using chrome: 5.0.342.9 beta

---

### Post by manoynmonic on 2010-05-26
Anyone get this working?  I am using Chromium 5.0.388.0 with the April released prealpha moonlight plugin.  So far nothing.  Actually, the firefox plugin isn't much better, very hit and miss, seems to only work with the most basic silverlight stuff.

Mostly want it to work so the wife can watch her Filipino tv shows on [http://www.tvadik.co.cc/](http://www.tvadik.co.cc/) .  Hmmm, on second thought maybe I should be thankful the plugin doesn't work.:P

---

### Post by kimberlite on 2010-06-15
> **dwarfolo said:**
> This "alpha" release of Moonlight seems to partially work for me.

[http://go-mono.com/moonlight/prerelease.aspx](http://go-mono.com/moonlight/prerelease.aspx)

Chromium 5.0.379.0 (44736) Ubuntu
No crash since now but most movies are not playable.

[http://tirania.org/blog/archive/2010/Apr-16.html](http://tirania.org/blog/archive/2010/Apr-16.html)

I think we're going to wait just a little more.

It is still true. :-(. Alpha release displays the player app, but does not play the video.

---

### Post by gehzumteufel on 2010-06-23
> **kimberlite said:**
> It is still true. :-(. Alpha release displays the player app, but does not play the video.

I'd just like to say that the newest one seems to be working. I can see a Silverlight built site.

Make sure NOT to use that direct link above. Go to their pre-release site and install the latest.

To test you can go to [www.t-mobileclue.com](www.t-mobileclue.com). It works for me.

Just beware, the plugin crashes without warning.

---

### Post by vickoxy on 2010-06-23
> **gehzumteufel said:**
> I'd just like to say that the newest one seems to be working. I can see a Silverlight built site.

Make sure NOT to use that direct link above. Go to their pre-release site and install the latest.

To test you can go to [www.t-mobileclue.com](www.t-mobileclue.com). It works for me.

Just beware, the plugin crashes without warning.

Could you just post that link (pre-release site)?

Thanks

---

### Post by gehzumteufel on 2010-06-23
> **vickoxy said:**
> Could you just post that link (pre-release site)?

Thanks

It was posted a few posts back, but here it is anyway.

[http://go-mono.com/moonlight/prerelease.aspx](http://go-mono.com/moonlight/prerelease.aspx)

It is only a minor release change from the previous one, but it seems to actually work on the one site I tried.

---

### Post by vickoxy on 2010-06-24
> **gehzumteufel said:**
> It was posted a few posts back, but here it is anyway.

[http://go-mono.com/moonlight/prerelease.aspx](http://go-mono.com/moonlight/prerelease.aspx)

It is only a minor release change from the previous one, but it seems to actually work on the one site I tried.

Well it is not working here. It is buffering, but showing no movie.
i use google-chrome 5.0.375.70. What do you use?

Thanks

---

### Post by gehzumteufel on 2010-06-24
> **vickoxy said:**
> Well it is not working here. It is buffering, but showing no movie.
i use google-chrome 5.0.375.70. What do you use?

Thanks
The same.

---

### Post by vickoxy on 2010-06-24
> **gehzumteufel said:**
> The same.

Could you try to watch this movie?

[http://www.bug.hr/bugtv/gps-navigacija-motociklima/654.aspx](http://www.bug.hr/bugtv/gps-navigacija-motociklima/654.aspx)

Thanks

---

### Post by gehzumteufel on 2010-06-24
> **vickoxy said:**
> Could you try to watch this movie?

[http://www.bug.hr/bugtv/gps-navigacija-motociklima/654.aspx](http://www.bug.hr/bugtv/gps-navigacija-motociklima/654.aspx)

Thanks

I'll have to try it tomorrow when I go back into the office. On a Mac right now and a proper MS Silverlight plugin is installed on here.

---

### Post by F4l3 on 2010-06-27
> **vickoxy said:**
> Could you try to watch this movie?

[http://www.bug.hr/bugtv/gps-navigacija-motociklima/654.aspx](http://www.bug.hr/bugtv/gps-navigacija-motociklima/654.aspx)

Thanks


Not really :( (see screenshot)

---

### Post by vickoxy on 2010-06-27
Ok, so we need to wait...

Thanks

---

### Post by manoynmonic on 2010-06-28
With the newest moonlight preview (Jun 17-2010 release), I can get as far as your video loading ([http://www.bug.hr/bugtv/gps-navigacija-motociklima/654.aspx](http://www.bug.hr/bugtv/gps-navigacija-motociklima/654.aspx)) and seeing the "preview" image - but when I click the play button nothing happens.

Still nothing from this site: [http://www.tvadik.co.cc/](http://www.tvadik.co.cc/)  But even at this site, there is a message that the stream is loading - just that it never gets beyond that.  Bummer, but this is still an improvement from earlier chrome moonlight pre-releases.  Almost there guys!

---

### Post by vickoxy on 2010-07-31
FINALLY!!!!
Google-chrome supports now moonlight 2 movies....

[http://go-mono.com/moonlight/prerelease.aspx](http://go-mono.com/moonlight/prerelease.aspx)

Maybe is still not perfect but on tested sites (e.g. here [http://www.bug.hr/bugtv/zotac-h55-itx-wifi/656.aspx](http://www.bug.hr/bugtv/zotac-h55-itx-wifi/656.aspx) - it works....)

Great news, isn´t it?

---

### Post by krul on 2010-09-29
> **vickoxy said:**
> FINALLY!!!!
Google-chrome supports now moonlight 2 movies....

[http://go-mono.com/moonlight/prerelease.aspx](http://go-mono.com/moonlight/prerelease.aspx)

Maybe is still not perfect but on tested sites (e.g. here [http://www.bug.hr/bugtv/zotac-h55-itx-wifi/656.aspx](http://www.bug.hr/bugtv/zotac-h55-itx-wifi/656.aspx) - it works....)

Great news, isn´t it?

Works for me! Thnx

---

### Post by WitchCraft on 2010-10-09
Nice post. Works.

---

### Post by scarleo on 2010-12-16
I'm still unable to use moonlight with 10.10, Chrome 8.0.552.215 (67652) and the plugin Silverlight Plug-In 4.0.50826.0 from link in previous post. Also with the package in Ubuntu repos Chrome won't start at all, as reported earlier. Can you guys wath Sky News Live? I'm just seeing the buffering icon 0% for a second, then it goes away and nothing else happens. Also if I visit this site: [http://www.bug.hr/bugtv/gps-navigacija-motociklima/654.aspx](http://www.bug.hr/bugtv/gps-navigacija-motociklima/654.aspx) I get massive hdd I/O so much the whole box becomes unresponsive (doesn't hang, just very very slow) until the plugin crashes (crash message from Chrome).

---

### Post by alex_andrascu on 2011-08-13
> **scarleo said:**
> I'm still unable to use moonlight with 10.10, Chrome 8.0.552.215 (67652) and the plugin Silverlight Plug-In 4.0.50826.0 from link in previous post. Also with the package in Ubuntu repos Chrome won't start at all, as reported earlier. Can you guys wath Sky News Live? I'm just seeing the buffering icon 0% for a second, then it goes away and nothing else happens. Also if I visit this site: [http://www.bug.hr/bugtv/gps-navigacija-motociklima/654.aspx](http://www.bug.hr/bugtv/gps-navigacija-motociklima/654.aspx) I get massive hdd I/O so much the whole box becomes unresponsive (doesn't hang, just very very slow) until the plugin crashes (crash message from Chrome).

Yep ...trying to watch Sky News Live...#fail

---

