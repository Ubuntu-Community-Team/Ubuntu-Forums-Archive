---
title: "Miro Playback Broken on 8.04?"
date: 2008-04-25
forum: Multimedia Software
---

### Post by Jimbotronics on 2008-04-25
Hi,

Almost everything is working on my Hardy installation, but Miro Net TV is an exception (Compiz Fusion is a little flaky so far too, but right now I'm just running with Metacity).  All of Miro's features, like channels, libraries, searches and so forth work perfectly...

...until I try to play a video, and then everything Miro-ish instantly disappears, leaving me back on a fully functional desktop.

Graphics -- ATI Radeon Xpress series (integrated on the MB) with ATI driver 8.47.3 and fglrx 2.1.7412.

Wondering if I should file a bug report... [COLOR="Indigo"]**or if it's just me!!**[/COLOR]

---

### Post by Islington on 2008-04-25
same here, it errored the first time, but after the updates everything seems fine.

EDIT: BLASKJ{FAD. STILL BROKEN GIVES ME ^ SECONDS OF PLAYBACK AND CRASHES.

---

### Post by Jimbotronics on 2008-04-25
Islington wrote:

[COLOR="Teal"]same here, it errored the first time, but after the updates everything seems fine.[/COLOR]

Hi, Islington,

Are you referring to updates to Miro or to Hardy?  Nothing has changed for me since I first fired up Miro on Hardy Heron final about 10 hours ago.  Thanks for replying; any more info would be most appreciated.

---

### Post by Islington on 2008-04-26
my apologies, miro playback on hardy *is* broken for me.It gives me exactly 6 seconds of playback before crashing. Is there any error output when run from the terminal? I am away from my linux box, and will look at this closer later today.

---

### Post by FredB on 2008-04-26
Just try to launch miro from command line.

I think installing openjdk could help fixing these bugs...

---

### Post by Islington on 2008-04-26
> **FredB said:**
> Just try to launch miro from command line.

I think installing openjdk could help fixing these bugs...

Well now, here is something interesting..
```
WARNING  Menu item action "RenameVideo" not implemented
INFO     Finished startup sequence
WARNING  Menu item action "FastForward" not implemented
TIMING   idle (finishStartup() (using asUrgent)) too slow (0.586 secs)
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented

```

when playing a video:
```
INFO     got file:///tmp/tmpftZpWT.html
INFO     First URL is https://www.miroguide.com/
INFO     *** Daemon ready ***
WARNING  eventloop: Interrupted system call
WARNING  eventloop: Interrupted system call
WARNING  eventloop: Interrupted system call
WARNING  eventloop: Interrupted system call
INFO     got file:///usr/share/miro/resources/html/guide-navigation.html
INFO     First URL is https://www.miroguide.com/
INFO     got about:blank
INFO     First URL is https://www.miroguide.com/
INFO     got https://www.miroguide.com/
INFO     First URL is https://www.miroguide.com/
TIMING   timeout (Save database) too slow (0.551 secs)
INFO     got file:///tmp/tmpFf6mvq.html
INFO     First URL is https://www.miroguide.com/
INFO     got action:handleSelect?area=tablist&viewName=guideTabs&id=22&shiftDown=0&ctrlDown=0
INFO     First URL is https://www.miroguide.com/

```

any ideas?

---

### Post by Islington on 2008-04-26
On a further note miro's site isnt loading for me..

---

### Post by Snyper64 on 2008-04-26
I can verify, its down. Also the home page in Miro is also down so I can't verify the video problem.

---

### Post by Jimbotronics on 2008-04-26
I checked [www.getmiro.com](www.getmiro.com) just now and it seemed to be working OK.  Anyway, the Miro player loads up on my desktop without a problem.  Invoking it from the terminal, I get the following messages at startup:

```

*************** INITIALIZE MOZEMBED
location: /usr/lib/xulrunner-1.9b5/libxpcom.so 
before 3
INFO     Starting up Miro
INFO     Version:    1.1.2
INFO     Revision:   https://svn.participatoryculture.org/svn/dtv/tags/Miro-1.1.2/tv/resources - 6194
INFO     Builder:    buildd@vernadsky
INFO     Build Time: 1202986841.91
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/jim/.miro/sqlitedb
TIMING   Database load slow: 1.712
TIMING   idle (Initializing database) too slow (2.280 secs)
INFO     Spawning auto downloader...
INFO     Displaying main frame...
INFO     *** Launching Downloader Daemon ****
INFO     Creating video display...
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
INFO     loaded renderer 'xinerenderer'
TIMING   gtkAsyncMethod: <function initRenderers at 0x8a6f534> took too long: 1.650
TIMING   gtkSyncMethod: <function getDisplay at 0x8b0387c> took too long: 1.806
INFO     First URL is https://www.miroguide.com/
INFO     got file:///tmp/tmpJRs0og.html
TIMING   Icon clear: 0.166
INFO     Starting movie data updates
INFO     Finished startup sequence
TIMING   idle (finalizing startup) too slow (2.545 secs)
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
INFO     *** Daemon ready ***
INFO     got file:///tmp/tmpfmBgSc.html
INFO     First URL is https://www.miroguide.com/
INFO     got file:///usr/share/miro/resources/html/guide-navigation.html
INFO     First URL is https://www.miroguide.com/
INFO     got https://www.miroguide.com/
INFO     First URL is https://www.miroguide.com/
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
INFO     unknown url type http://feeds.feedburner.com/~r/tmv/~3/272783531/, not generating enclosure
INFO     unknown url type http://feeds.feedburner.com/~r/tmv/~3/272783533/, not generating enclosure
INFO     unknown url type http://feeds.feedburner.com/~r/tmv/~3/272783534/, not generating enclosure
INFO     unknown url type http://feeds.feedburner.com/~r/tmv/~3/272783535/, not generating enclosure
GCJ PLUGIN: thread 0x82f3370: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x82f3370: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x82f3370: NP_GetValue
GCJ PLUGIN: thread 0x82f3370: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x82f3370: NP_GetValue return
GCJ PLUGIN: thread 0x82f3370: NP_GetValue
GCJ PLUGIN: thread 0x82f3370: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x82f3370: NP_GetValue return
GCJ PLUGIN: thread 0x82f3370: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x82f3370: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x82f3370: NP_GetValue
GCJ PLUGIN: thread 0x82f3370: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x82f3370: NP_GetValue return
GCJ PLUGIN: thread 0x82f3370: NP_GetValue
GCJ PLUGIN: thread 0x82f3370: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x82f3370: NP_GetValue return

```

But when I try to play a video, Miro just vanishes, leaving the following traces in the terminal, which seem to suggest a segmentation fault involving xinerenderer:

```
INFO     got action:handleSelect?area=tablist&viewName=staticTabs&id=2819&shiftDown=0&ctrlDown=0
INFO     got file:///tmp/tmpO1LCEO.html
INFO     got action:playViewNamed?viewName=matchingItems&firstItemId=2778
INFO     Playing item with renderer: <frontend_implementation.xinerenderer.Renderer instance at 0xb10b742c>
[COLOR="Red"]Segmentation fault[/COLOR]
jim@JimboTron:~$ 
jim@JimboTron:~$ 
jim@JimboTron:~$ 
jim@JimboTron:~$ 
jim@JimboTron:~$ 
WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...
jim@JimboTron:~$ 
jim@JimboTron:~$
``` 

Odd, because everything seemed to work perfectly in 7.10.

---

### Post by Islington on 2008-04-26
> **Jimbotronics said:**
> I checked [www.getmiro.com](www.getmiro.com) just now and it seemed to be working OK.  Anyway, the Miro player loads up on my desktop without a problem.  Invoking it from the terminal, I get the following messages at startup:

```

*************** INITIALIZE MOZEMBED
location: /usr/lib/xulrunner-1.9b5/libxpcom.so 
before 3
INFO     Starting up Miro
INFO     Version:    1.1.2
INFO     Revision:   https://svn.participatoryculture.org/svn/dtv/tags/Miro-1.1.2/tv/resources - 6194
INFO     Builder:    buildd@vernadsky
INFO     Build Time: 1202986841.91
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/jim/.miro/sqlitedb
TIMING   Database load slow: 1.712
TIMING   idle (Initializing database) too slow (2.280 secs)
INFO     Spawning auto downloader...
INFO     Displaying main frame...
INFO     *** Launching Downloader Daemon ****
INFO     Creating video display...
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
INFO     loaded renderer 'xinerenderer'
TIMING   gtkAsyncMethod: <function initRenderers at 0x8a6f534> took too long: 1.650
TIMING   gtkSyncMethod: <function getDisplay at 0x8b0387c> took too long: 1.806
INFO     First URL is https://www.miroguide.com/
INFO     got file:///tmp/tmpJRs0og.html
TIMING   Icon clear: 0.166
INFO     Starting movie data updates
INFO     Finished startup sequence
TIMING   idle (finalizing startup) too slow (2.545 secs)
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
INFO     *** Daemon ready ***
INFO     got file:///tmp/tmpfmBgSc.html
INFO     First URL is https://www.miroguide.com/
INFO     got file:///usr/share/miro/resources/html/guide-navigation.html
INFO     First URL is https://www.miroguide.com/
INFO     got https://www.miroguide.com/
INFO     First URL is https://www.miroguide.com/
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
INFO     unknown url type http://feeds.feedburner.com/~r/tmv/~3/272783531/, not generating enclosure
INFO     unknown url type http://feeds.feedburner.com/~r/tmv/~3/272783533/, not generating enclosure
INFO     unknown url type http://feeds.feedburner.com/~r/tmv/~3/272783534/, not generating enclosure
INFO     unknown url type http://feeds.feedburner.com/~r/tmv/~3/272783535/, not generating enclosure
GCJ PLUGIN: thread 0x82f3370: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x82f3370: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x82f3370: NP_GetValue
GCJ PLUGIN: thread 0x82f3370: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x82f3370: NP_GetValue return
GCJ PLUGIN: thread 0x82f3370: NP_GetValue
GCJ PLUGIN: thread 0x82f3370: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x82f3370: NP_GetValue return
GCJ PLUGIN: thread 0x82f3370: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x82f3370: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x82f3370: NP_GetValue
GCJ PLUGIN: thread 0x82f3370: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x82f3370: NP_GetValue return
GCJ PLUGIN: thread 0x82f3370: NP_GetValue
GCJ PLUGIN: thread 0x82f3370: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x82f3370: NP_GetValue return

```

But when I try to play a video, Miro just vanishes, leaving the following traces in the terminal, which seem to suggest a segmentation fault involving xinerenderer:

```
INFO     got action:handleSelect?area=tablist&viewName=staticTabs&id=2819&shiftDown=0&ctrlDown=0
INFO     got file:///tmp/tmpO1LCEO.html
INFO     got action:playViewNamed?viewName=matchingItems&firstItemId=2778
INFO     Playing item with renderer: <frontend_implementation.xinerenderer.Renderer instance at 0xb10b742c>
[COLOR="Red"]Segmentation fault[/COLOR]
jim@JimboTron:~$ 
jim@JimboTron:~$ 
jim@JimboTron:~$ 
jim@JimboTron:~$ 
jim@JimboTron:~$ 
WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...
jim@JimboTron:~$ 
jim@JimboTron:~$
``` 

Odd, because everything seemed to work perfectly in 7.10.

indeed I tried playing with gstreamer and no luck..

---

### Post by FredB on 2008-04-26
*Stinks* like a xine issue. What is your xine version ? Do you have libxine installed ?

---

### Post by Snyper64 on 2008-04-27
Well I just got around to playing a video in Miro, and with the exception of my audio coming out of my laptop speakers instead of my external sound cards speakers everything is working fine. As for this being a Xine issue I don't think it is as I am using Xine for everything as far as I know.

---

### Post by FredB on 2008-04-27
could be a conflict between libxine and miro. Just guessing, of course ;)

---

### Post by Jimbotronics on 2008-04-27
> **FredB said:**
> *Stinks* like a xine issue. What is your xine version ? Do you have libxine installed ?

Synaptic says the libxine* files are all v. 1.1.11.1.  Not sure which file from list below determines the xine version.  I'm using Gnome desktop, so I just installed gxine, but it doesn't seem to make any difference.

Here's a list of the related files I've got installed:

gxine                 0.5.901
gxineplugin           0.5.901
libxine1              1.1.11.1
libxine1-bin          1.1.11.1
libxine-1-console     1.1.11.1
libxine1-ffmpeg       1.1.11.1
libxine1-gnome        1.1.11.1
libxine1-misc-plugins 1.1.11.1
libxine1-plugins      1.1.11.1
libxine1-x            1.1.11.1
libxinerama1          2:1.0.2
libxinerama-dev       2:1.0.2
x11proto-xinerama-dev 1.1.2-4

---

### Post by goggins on 2008-05-07
I just started a new thread named:
 "miro works fine for me - here's what I did"
see if it works for you.

---

### Post by levidos on 2009-01-01
i'm having lots of trouble with miro, too.. very annoying, someone should fix those bugs... it's been 2 years daah

---

