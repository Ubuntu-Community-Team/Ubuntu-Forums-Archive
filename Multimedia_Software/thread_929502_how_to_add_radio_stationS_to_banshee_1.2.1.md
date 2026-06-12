---
title: "how to add radio stationS to banshee 1.2.1"
date: 2008-09-25
forum: Multimedia Software
---

### Post by spandanj on 2008-09-25
Hi,

I reinstalled banshee from PPA. latest 1.2.1 - 3


There are no radio stations in 'radio'. How can I add all the popular radio stations that normally come listed under radio with banshee. I know there are because I had them in my previous installation. I don't want to add stations one at a time. Is there a way I can get a list and copy/paste somewhere?

thanks

---

### Post by meho_r on 2008-12-01
Good question. Same with 1.4.1. Anyone?

---

### Post by santosomar on 2008-12-23
same here with Banshee 1.2.1

---

### Post by andoni on 2009-03-18
I've got the same problem. I don't know why banshee's developers erased all the radio stations.

I used to listen to them, so, if anyone could bring us the URLs of those radio stations, I would really appreciate it.

Greetings from Spain :).

---

### Post by mattisking on 2009-03-27
I'm not sure how to get those back... but I just added a radio station from Live365.com.
1) Go to Live365.com
2) Look down at the bottom... for "Listening Settings".
3) For MP3 Player, you'll under the Web Player, "Additional Options". Choose from them, "MP3 Desktop Player".
4) Save your settings, and then search for a radio station.
5) Choose one and start it playing... it will let you download a file ... generally something like play.pls. Save this file on your desktop or wherever.
6) Open the file with gedit or look at it in a terminal. You'll see a long url that looks something like: 
```
File1=http://www.live365.com/play/341355?auth=b926481039488ee73bfb4ea7670f4910-1238162608-unclebuster&tag=live365&token=11c1bcd2be4c1c8809036acb1a13f280-0306270080400000&sid=71.75.251.99-1237357245479&lid=517-usa&from=pls
```
7) Just grab the [http://.](http://.)... part after the File1= and copy it.
8) In Banshee while looking at your stations, click the Add Station icon up top by the volume icon. Fill out the bits you want and put that long URL in for Stream URL. Save. Enjoy.

In general this should work for any Online Radio station. You just need a way to access the stream URL.

---

### Post by spandanj on 2009-03-31
> **mattisking said:**
> 
In general this should work for any Online Radio station. You just need a way to access the stream URL.

Hey, Thanks.

It works. However, I wish there was a file that contained all the URL streams lists so that I didn't have to add one station at a time.

Is there such a file? or such an "add-on" for banshee. eg. A "live365.com" radios add-on which would prompt you to choose which radio stations to add for you.

thanks

---

### Post by spandanj on 2009-03-31
Also,

do the URL addresses for the radio stream change? ever?

---

### Post by indwic on 2009-05-25
Thanx mattisking, now the problem is I don't know the artist and song title that currently playing...

---

### Post by artisan002 on 2009-09-12
Actually, spandanj, a lot of web radio URLs go dead, more than change. However, plenty of them change, as well. This has been cited by the lead developer of Banshee as to why he isn't including radio stations in newer versions. See his remarks here: [http://abock.org/2008/11/17/a-couple-of-ideas-for-contributing-to-banshee](http://abock.org/2008/11/17/a-couple-of-ideas-for-contributing-to-banshee)

As you'll notice, he's looking at putting it back in for later versions, as an extension. But, the speed of that will depend entirely on the amount of help they can get on the matter. It's not high up on his to-do list.

---

### Post by Ghost|BTFH on 2009-10-28
*semi* simple trick to *fix* this issue - Rhythmbox is installed by default.  Rhythmbox has an internet radio playlist, yet sadly has issues with the streaming media.

So kill two birds with one stone and steal the Rhythmbox's internet radio playlist.  It's found under /usr/lib/rhythmbox/plugins/iradio/iradio-initial.pls

For those who really don't feel like looking it up or don't happen to have rhythmbox for some reason, allow me to share the urls:

[playlist]

# [http://www.absoluteradio.co.uk/listen/on_your_computer.html](http://www.absoluteradio.co.uk/listen/on_your_computer.html)
file1=http://network.absoluteradio.co.uk/core/audio/ogg/live.pls?service=vr
title1=Absolute Radio (Modem)
genre1=Pop

file2=http://network.absoluteradio.co.uk/core/audio/ogg/live.pls?service=vrbb
title2=Absolute Radio (Broadband)
genre2=Pop

file3=http://network.absoluteradio.co.uk/core/audio/ogg/live.pls?service=vx
title3=Absolute Xtreme (Modem)
genre3=Modern Rock

file4=http://network.absoluteradio.co.uk/core/audio/ogg/live.pls?service=vxbb
title4=Absolute Xtreme (Broadband)
genre4=Modern Rock

file5=http://network.absoluteradio.co.uk/core/audio/ogg/live.pls?service=vc
title5=Absolute Classic Rock (Modem)
genre5=Rock'n'Roll

file6=http://network.absoluteradio.co.uk/core/audio/ogg/live.pls?service=vcbb
title6=Absolute Classic Rock (Broadband)
genre6=Rock'n'Roll

file7=http://ubuntu.hbr1.com:19800/trance.ogg
title7=HBR1.com - I.D.M. Tranceponder
genre7=Trance

file8=http://ubuntu.hbr1.com:19800/tronic.ogg
title8=HBR1.com - Tronic Lounge
genre8=House

file9=http://ubuntu.hbr1.com:19800/ambient.ogg
title9=HBR1.com - Dream Factory
genre9=Ambient

# [http://www.wknc.org/listen.php](http://www.wknc.org/listen.php)
file10=http://wknc.org:8000/wknclq.ogg.m3u
title10=WKNC 88.1 FM (NC State) (Modem)
genre10=Music

file11=http://wknc.org:8000/wkncmq.ogg.m3u
title11=WKNC 88.1 FM (NC State) (Broadband)
genre11=Music

# [http://www.cbc.ca/listen/ogg.html](http://www.cbc.ca/listen/ogg.html)
file12=http://www.cbc.ca/livemedia/cbcr1-toronto.m3u
title12=CBC Radio One (Canada)
genre12=General

file13=http://www.cbc.ca/livemedia/cbcr2-toronto.m3u
title13=CBC Radio Two (Canada)
genre13=General

# [http://www.nrk.no/lyd/](http://www.nrk.no/lyd/)
file14=http://media.hiof.no/streams/m3u/nrk-p1-172.ogg.m3u
title14=NRK P1 (Norway)
genre14=General

file15=http://media.hiof.no/streams/m3u/nrk-p2-172.ogg.m3u
title15=NRK P2 (Norway)
genre15=General

file16=http://media.hiof.no/streams/m3u/nrk-petre-172.ogg.m3u
title16=NRK P3 (Norway)
genre16=General

file17=http://media.hiof.no/streams/m3u/nrk-alltid-nyheter-172.ogg.m3u
title17=NRK Alltid Nyheter (Norway)
genre17=

file18=http://media.hiof.no/streams/m3u/nrk-mpetre-172.ogg.m3u
title18=NRK mP3 (Norway)
genre18=

file19=http://media.hiof.no/streams/m3u/nrk-alltid-klassisk-172.ogg.m3u
title19=NRK Alltid Klassisk (Norway)
genre19=

Copy the http section and paste that into the URL.  Give it a name, and select a genre and away you go.

Maybe that'll give you a start. :)

Cheers,
Ghost|BTFH

---

### Post by w-sky on 2009-12-19
That is a nice idea! Actually, I think it would be even nicer to have a clean, comprehensive and well-sorted list of internet radio stations, that would be community-maintained... not like shoutcast.com, which lists just everything.

Do you know where Banshee has its stations file and if the file from Rhythmbox can be copied or adapted?

I'd like to add something to the post from Mattisking, about adding stations (an excerpt from my reply to [this other thread]("http://forums.linuxmint.com/viewtopic.php?f=47&t=33346")):

So you find radio links here, on station's web pages, and on sites like [http://yp.shoutcast.com/](http://yp.shoutcast.com/) or [http://dir.xiph.org/](http://dir.xiph.org/). And when you click on a link, the browser will probably ask what to do with the file, and the nicest thing were to just choose "open with Banshee" and the station plays. Sadly however, I could not get it to work like this with Firefox and Banshee. :(

About adding stations manually: You may have to remove the filename part of the address. For example, with an internet radio link from xiph.org:
**[http://dir.xiph.org/listen/14793999/listen.m3u](http://dir.xiph.org/listen/14793999/listen.m3u)**
Add this as stream address to Banshee:
**[http://dir.xiph.org/listen/14793999/](http://dir.xiph.org/listen/14793999/)**
"listen.m3u" is a playlist file, which could also be of pls, asx or xspf type and more. But often the playlist file contains of more than one actual stream addresses (in case one is offline or overloaded), and then the shorter URL can not work.

On [banshee-project.org]("http://banshee-project.org/download/archives/1-5-0/") they advertise their "Rhythmbox Migrator" new in Banshee 1.5, but I didn't test it.

But I also made interesting experiments with another application, "Tunapie", which can list radio stations from Shoutcast and Xiph, and open them in a media player like Banshee!

---

### Post by Pifilatakanemu on 2010-01-26
you should definitely check this extension:  [http://code.google.com/p/banshee-radiostationfetcher/](http://code.google.com/p/banshee-radiostationfetcher/)   once you got it installed you can easily load tons of radio stations directly into banshee.

---

### Post by afrodeity on 2010-03-23
How can I add [SomaFM]("http://somafm.com/") to the radio prefetch? I don't want to have have to add each one of the channels individually?

---

### Post by zodiacdm on 2010-06-14
There is actually an easier way to add stations to the playlist than to open each file downloaded and copy the url.

If you just right click the link to download the playlist, and copy link location, then paste that link into banshee, it will add that station like magic. ;)

The reason I came to this thread, was I recently changed some software that forced me to reinstall banshee, and before I reistalled it, I had an extension to access the shoutcast and various other radio libraries, and now that I have reinstalled bansee, these are no longer there... Was hoping to find out why they dissapeared.

---

### Post by afrodeity on 2010-06-15
I found the prefetcher, it grabs stations, but none of them seem to play. Having more success with streamtuner right now, with audacious.

---

### Post by oraculum on 2011-05-14
> **mattisking said:**
> I'm not sure how to get those back... but I just added a radio station from Live365.com.
1) Go to Live365.com
2) Look down at the bottom... for "Listening Settings".
3) For MP3 Player, you'll under the Web Player, "Additional Options". Choose from them, "MP3 Desktop Player".
4) Save your settings, and then search for a radio station.
5) Choose one and start it playing... it will let you download a file ... generally something like play.pls. Save this file on your desktop or wherever.
6) Open the file with gedit or look at it in a terminal. You'll see a long url that looks something like: 
```
File1=http://www.live365.com/play/341355?auth=b926481039488ee73bfb4ea7670f4910-1238162608-unclebuster&tag=live365&token=11c1bcd2be4c1c8809036acb1a13f280-0306270080400000&sid=71.75.251.99-1237357245479&lid=517-usa&from=pls
```
7) Just grab the [http://.](http://.)... part after the File1= and copy it.
8) In Banshee while looking at your stations, click the Add Station icon up top by the volume icon. Fill out the bits you want and put that long URL in for Stream URL. Save. Enjoy.

In general this should work for any Online Radio station. You just need a way to access the stream URL.


There is a second option to hear the banshee live365.com. You do not need premium account as your method described above

See link >> [http://oraculum.blog.br/blogoraculum/index.php/2011/05/14/houvindo-as-melhores-radios-on-line-no-banshee/](http://oraculum.blog.br/blogoraculum/index.php/2011/05/14/houvindo-as-melhores-radios-on-line-no-banshee/)

---

### Post by Zlatan on 2011-06-01
you can add radio extensions for Banshee via Ubuntu Software Center

---

### Post by mamasiga on 2011-07-03
Hi,
Install this:

Software manager > banshee-extension-liveradio

Restart Banshee. Now enable liveradio in Banshee:
Edit > Preferences > Extensions > Liveradio

Now you will have in Banshee in left menu under Online Media "Liveradio":
- live365.com
- magnatune.com
- RealRadios.com
- xiph.com

All the best at on-line listening.
Tomas

---

### Post by fmmarzoa on 2011-12-23
> **Pifilatakanemu said:**
> you should definitely check this extension:  [http://code.google.com/p/banshee-radiostationfetcher/](http://code.google.com/p/banshee-radiostationfetcher/)   once you got it installed you can easily load tons of radio stations directly into banshee.

That extension is not working for me at least. I have installed it in my Ubuntu 11.10 through aptitude, enabled it, but when I go into Banshee to Tools/Radiostation Fetcher, and press the button "Get Stations" after selecting a Genre, it does nothing, no matter if I use Southcast or Xiph.

I'm using Banshee 2.2.1

Regards,

---

### Post by florian22 on 2012-08-03
thanks it works

---

