---
title: "Satellite tv for linux"
date: 2010-03-09
forum: Multimedia Software
---

### Post by komitaltrade on 2010-03-09
Somebody know some software for watching satellite tv on pc (linux)?

For windows and mac is all bunch of software (e.g. one small list is on [http://free-satellite-tv.qarchive.org](http://free-satellite-tv.qarchive.org)), but for linux I found just two (not available for South America and "just" with few hundreds channels).

---

### Post by lovinglinux on 2010-03-09
From that link...

> No need to pay for monthly satellite tv or cable tv anymore with Satellite TV Free PC 1.5. Internet connection required to stream satellite tv channels to your PC.

> Most cable tv channels such as HBO, Disney, CNBC, CNN and more are free to watch on your PC 24 hours a day. No need to pay for monthly subscription satellite tv charges.

> Watch over 3000 satellite tv channels on your PC including premium cable TV channels such as HBO, cinemax, CNN, Disney, Animax, Discovery channel etc and more. No need to pay monthly satellite tv channels anymore. 

That's certainly illegal and thus not allowed in the forums. 

You could try Miro, which has some featured legal channels, but if you are looking for watching premium channels like HBO, then I would advise to subscribe to an official service and get a TV card.

If you own a cable/satellite setup-box/subscription you can hook it to a TV card and watch TV on your PC. You will need a program like tvtime or kaffeine to tune and watch. Both are available in the repositories.

---

### Post by steefjeqv on 2010-03-10
The best program for sat tv is VDR (linux video disk recorder).

If you like to use this together with Ubuntu then the ppa of the VDR Team is the best place to start :

[https://launchpad.net/~the-vdr-team/+archive/vdr-ubuntu-karmic]("https://launchpad.net/~the-vdr-team/+archive/vdr-ubuntu-karmic")

They also have an Ubuntu based VDR distro (including XBMC) :

[http://www.yavdr.org/]("http://www.yavdr.org/")

If you want to use something a bit less complicated then I'd suggest Kaffeine.

Greetings,
Steven

---

### Post by 2hot6ft2 on 2010-03-10
Watching TV on PC
Get the TV-Fox Plugin for firefox here:
[http://addons.mozilla.org/en-US/firefox/addon/11200](http://addons.mozilla.org/en-US/firefox/addon/11200)

It boasts 2780 Live Streaming TV Stations

Seems to work ok. The Mplayer plugin is no longer supported and is now replaced with gecko-mediaplayer (per the info in Synaptic).
First remove the Mplayer plugin
```
sudo apt-get remove mozilla-mplayer
```
Then install Gecko Media Player.
```
sudo apt-get install gecko-mediaplayer
```
Edit the file as recommended on the plugin page.
```
gksu gedit /etc/mplayerplug-in.conf
```
changing
> #cachesize=512
to
> cachesize=512
save and close
close firefox then open it again.

It works pretty well although the full screen doesn't look that good. But it's FREE.;)

---

### Post by Atilana on 2010-03-10
Hi, i-m agree with you try

[[COLOR=#444444]https://launchpad.net/~the-vdr-team/...-ubuntu-karmic[/COLOR]]("https://launchpad.net/~the-vdr-team/+archive/vdr-ubuntu-karmic")

[[COLOR=#444444]http://www.yavdr.org/[/COLOR]]("http://www.yavdr.org/")

---

### Post by komitaltrade on 2010-03-11
Thanks for [2hot6ft2]("http://ubuntuforums.org/member.php?u=568708")

It can to work, but it is still not same.

So, I need it for Cyber Cafe. Operator will be able to switch sessions for regular internet users, gamers, VoIP and TV. As for VoIP, session will be Ekiga fullscreen mode, I want something same for TV session (thats why I need application and not addon).

VDR is obviously not solution (it is made for other purpose).

Also reply for lovinglinux.

As I mention, it is for Cyber Cafe. You should to know how over 90% of channels are free (from this 3000+) and it is my first target (foreign tourists want to see the news from his country).

Sure how also second client group can be interesting (Premium channels like ESPN, HBO, Disney, etc.). Is it illegal. Absolutely can`t be illegal. Answer is quite simple (thats how Microsoft lost trial from MiniFrame). Company just sell the tool what enable user to watch whatever is available on net to be watched (so, it is problem of HBO how they make security of distribution - thats how Microsoft lost case, and not of the company who make software wich enable you to watch tv). Pay attention on two simple facts - it is one time payment (because you pay software and not channels) and all of companies are US based companies (if thats illegal, HBO will already long time ago made case against companies - remember the case of the puor guy with mp3).

Finally, it is also few web pages with bunch of the channels (they will be on the court also).

So, please lets go back on the subject - somebody know for some application or not?

---

### Post by mocha on 2010-03-12
There's lots of apps for DVB on linux.  Me-TV, Kaffeine, mplayer, MythTV, VDR, xine, etc....  Look on the linuxTV website.

---

### Post by BenginM on 2012-06-04
Salutation , How about tv-maxe .

:popcorn:

---

### Post by nothingspecial on 2012-06-04
Old thread.

Closed.

---

