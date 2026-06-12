---
title: "Anyone know how to capture streaming media?"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by SNYP40A1 on 2007-06-14
Does anyone know how to capture streaming video / audio?  Specifically, I would like to capture a streaming WMV content.  Anyone know how to do this?  Preferably for free.

---

### Post by mitch.c on 2007-06-15
I think with mplayer you can do something like:
```
$ mplayer mms://somehost.com/somedirectory/somefile.wmv -dumpstream -dumpfile myfile.wmv
```
Try it.

[[COLOR="Red"]UAResolved[/COLOR]]("http://ubuntuforums.org/showthread.php?t=377083")

---

### Post by SNYP40A1 on 2007-06-16
> **mitch.c said:**
> I think with mplayer you can do something like:
```
$ mplayer mms://somehost.com/somedirectory/somefile.wmv -dumpstream -dumpfile myfile.wmv
```
Try it.

[[COLOR="Red"]UAResolved[/COLOR]]("http://ubuntuforums.org/showthread.php?t=377083")

I am away from my home, but I will try it tomorrow when I get back.  Thanks for helping a fellow Oregonian (Portland).

---

### Post by linuxfan3 on 2007-06-16
Hi,
if you want to capure (also embedded) streamings from internet like youtube or google try "clive". It also encodes on the fly in avi, meg,... 
[http://home.gna.org/clive/examples.shtml](http://home.gna.org/clive/examples.shtml)
if you use firefox you could also use plugin like "videodownloader".

---

### Post by mitch.c on 2007-06-16
> **SNYP40A1 said:**
> Thanks for helping a fellow Oregonian (Portland).
No trouble.

Hey, there is a [[COLOR="Blue"]PDXTeam[/COLOR]]("https://wiki.ubuntu.com/PDXTeam") meeting this Saturday if you want to get involved with other Portlanders using Ubuntu!

When: 12 PM Saturday, June 16.
Where: [Old Town Pizza]("http://oldtownpizza.com/") [[COLOR="Blue"][map][/COLOR]]("http://tinyurl.com/23gjph")

---

### Post by SpiritIsReality on 2007-09-21
howdy
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org++capture+streaming+video&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org++capture+streaming+video&btnG=Search&meta=)
linuxfan3 ...thanks for the videodownloader tip

now to figure this mplayer command line stuff! haha!

trails

---

### Post by altonbr on 2008-01-15
I've been trying clive on a number of websites and can never seem to get it running...

That mplayer trick doesn't work with Apple either...

Can anyone capture this URL: [http://stream.qtv.apple.com/events/jan/f27853y2/m_972345688g_350_ref.mov](http://stream.qtv.apple.com/events/jan/f27853y2/m_972345688g_350_ref.mov) ???

wget doesn't work either.

---

### Post by andrew.46 on 2008-01-15
Hi,

 I have met this problem before:

> **altonbr said:**
> I've been trying clive on a number of websites and can never seem to get it running...

That mplayer trick doesn't work with Apple either...

Can anyone capture this URL: [http://stream.qtv.apple.com/events/jan/f27853y2/m_972345688g_350_ref.mov](http://stream.qtv.apple.com/events/jan/f27853y2/m_972345688g_350_ref.mov) ???

wget doesn't work either.

Apple masks the real filename for their own obscrure reasons but it is relatively easy to extract the correct address by using the strings utility. Download the file using wget and you will be left with the file m_972345688g_350_ref.mov, then run:

```
$ strings m_972345688g_350_ref.mov
```The result will be:

```
andrew@ilium~/Desktop$ strings m_972345688g_350_ref.mov 
%moov
rmra
rmda
Trdrf
url 
@http://stream.qtv.apple.com/events/jan/f27853y2/qt7required.mov
rmdr
rmvc
qtim
rmda
]rdrf
url 
Ihttp://stream.qtv.apple.com/events/jan/f27853y2/972345688g_1_350_ref.mov
rmdr
rmvc
qtim

```And I successfully played the stream from the second url (obviously without the 'I').  strings is a great little utility which the man pages declare:

 > strings -- find printable strings in a filePretty much what it does :-)

     Andrew

---

### Post by altonbr on 2008-01-15
Hey, that's a neat little trick, but can you actually download the video to your desktop?

I haven't been able to...

---

### Post by andrew.46 on 2008-01-15
Hi,

> **altonbr said:**
> Hey, that's a neat little trick, but can you actually download the video to your desktop?

I haven't been able to...

Hmmm.... oddly enough I cannot. Not sure if it is an Apple trick or I am not clever enough. Certainly if you can play it you should be able to save it. And it plays well, particularly if you give it a big cache:

```
$ mplayer -cache 30000 <address>
```Anybody else have any ideas? 

Only possible problem I can see is a large number of server shifts before mplayer latches onto the stream. I have sent a message to the mplayer-users where wiser heads than mine should prevail. I saw the 'strings' trick there a while ago and have used it extensively since.

       Andrew

---

### Post by cor2y on 2008-01-15
or use the DownloadHelper plugin for firefox it can download most streaming media for you.
I say most because i have never tested it against the fladh rtmp protocol.
Also you can use mplayer's mozilla plugin to save a file to your home folder but this only works for anything not flash and requires you have downloaded the whole file to the temp folder first.

---

### Post by mandrill on 2008-01-15
You mean this? [http://stream.qtv.apple.com/events/jan/f27853y2/m_972345688g_350_ref.mov](http://stream.qtv.apple.com/events/jan/f27853y2/m_972345688g_350_ref.mov)

Easy.  vlc. click file>open network stream>HTTP/HTTPS/FTP/MMS,... paste the url and you're off and flying....just did it. Something about Apple with Steve Jobs.

Good Luck!

---

### Post by andrew.46 on 2008-01-15
Hi again,

 Thanks to Jorge of the mplayer-users there is a solution. The problem is the nest of redirects that the initial file leads you through. If you play the file with mplayer and wait until it declares: 'Playing ...' ***this*** is the actual address of the file. Why they have to do this I don't know ......

Anyway thanks to Jorge the syntax to save offline is:

```
mplayer -dumpstream -dumpfile trailer.mov http://events.apple.com.edgesuite.net/f27853y2/iphone/972345688g_1_ip.3gp
```

Must be a big file, I have downloaded 45 megs so far and it is still coming in :-)

           Andrew

---

### Post by andrew.46 on 2008-01-15
Hi,

I am not familiar with vlc:

> **mandrill said:**
> You mean this? [http://stream.qtv.apple.com/events/jan/f27853y2/m_972345688g_350_ref.mov](http://stream.qtv.apple.com/events/jan/f27853y2/m_972345688g_350_ref.mov)

Easy.  vlc. click file>open network stream>HTTP/HTTPS/FTP/MMS,... paste the url and you're off and flying....just did it. Something about Apple with Steve Jobs.

Good Luck!

but will it also save the stream for offline? mplayer does, as I have posted above somewhere, but Apple has made it a little difficult to do so :-)

              Andrew

---

### Post by mandrill on 2008-01-15
videolan media player aka vlc is downloadable either from the site (newer) or the repositories. And yes, if memory serves me correctly, it can save the streams to your pc.

Happy Streaming!

---

### Post by tact on 2008-01-15
For youtube videos its no harder than clicking on the link and waiting for the clip to fully play in your web browser... dont close the browser or navigate away...  open your /tmp folder and you will find the fully downloaded clip there.  copy and paste it to wherever you want to store it, rename it.  Done.

Not sure if this works with anything other than youtube.  but it does work with youtube.

---

### Post by andrew.46 on 2008-01-15
Hi,

 I read with interest your comments on youtube videos:

> **tact said:**
> For youtube videos its no harder than clicking on the link and waiting for the clip to fully play in your web browser... dont close the browser or navigate away...  open your /tmp folder and you will find the fully downloaded clip there.  copy and paste it to wherever you want to store it, rename it.  Done.

Not sure if this works with anything other than youtube.  but it does work with youtube.

There is a nice script called youtube-dl written by  [Ricardo Garcia Gonzalez]("http://www.arrakis.es/%7Erggi3/youtube-dl/") that works very well. Main trouble seems to be the quality of the videos themselves: blocky, poor colours, jerky etc. But nice script anyway.

  Andrew

---

### Post by altonbr on 2008-01-17
> **mandrill said:**
> You mean this? [http://stream.qtv.apple.com/events/jan/f27853y2/m_972345688g_350_ref.mov](http://stream.qtv.apple.com/events/jan/f27853y2/m_972345688g_350_ref.mov)

Easy.  vlc. click file>open network stream>HTTP/HTTPS/FTP/MMS,... paste the url and you're off and flying....just did it. Something about Apple with Steve Jobs.

Good Luck!

Hey, pretty neat. I use VLC all the time and never knew of that... but now, how do I save it?

> **andrew.46 said:**
> Hi again,

 Thanks to Jorge of the mplayer-users there is a solution. The problem is the nest of redirects that the initial file leads you through. If you play the file with mplayer and wait until it declares: 'Playing ...' ***this*** is the actual address of the file. Why they have to do this I don't know ......

Anyway thanks to Jorge the syntax to save offline is:

```
mplayer -dumpstream -dumpfile trailer.mov http://events.apple.com.edgesuite.net/f27853y2/iphone/972345688g_1_ip.3gp
```

Must be a big file, I have downloaded 45 megs so far and it is still coming in :-)

           Andrew

Hey that's great! I'm downloading it now as well :D. How did you finally come up with that URL?

---

### Post by andrew.46 on 2008-01-18
Hi,

 Not really my solution:

> **altonbr said:**
> 
Hey that's great! I'm downloading it now as well :D. How did you finally come up with that URL?

but Jorge from mplayer users. Look for the final 'Playing ... <address>' just before the file actually loads (in the terminal window).

               Andrew

---

### Post by ubuntu-freak on 2008-01-18
I just open the terminal and
 
gksudo gedit /etc/mplayerplug-in.conf
 
and change the 'keep-download' value from 0 to 1. Then it saves everything to my home folder.
 
Check out my how-to for everything multimedia and video related. Including encrypted DVD playback.
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

