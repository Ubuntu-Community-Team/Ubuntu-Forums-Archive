---
title: "totem mozilla plug in and streaming wmv"
date: 2006-12-26
forum: Multimedia &amp; Video
---

### Post by dmizer on 2006-12-26
desperately seeking help with streaming video (wmv) in edgy.

i gave up on mplayer, see here: [http://www.ubuntuforums.com/showthread.php?t=322085](http://www.ubuntuforums.com/showthread.php?t=322085)

recap:
this is not a codec issue, both encrypted dvds and wmv DO play.  the problem is that the plug in will not play streaming video embedded in firefox.

using the mozilla media connectivity add-on works.  but this is an unacceptable arrangement for deployment to end users.

output from totem-gstreamer when used with the totem mozilla plug in:
```
** Message: totem_plugin_new_instance
totemGMPPlugin ctor [0x8fb6798]
mode 1
mime type: application/x-mplayer2
argv[0] type application/x-mplayer2
argv[1] pluginspage http://www.microsoft.com/Windows/MediaPlayer/
argv[2] src /2006/05/snakehippo.wmv
argv[3] autostart 1
argv[4] showcontrols 1
argv[5] volume -20
argv[6] height 285
argv[7] width 320
** Message: plugin_get_value 14 (e)

** Message: plugin_set_window
** Message: waiting for data to come
** Message: leaving plugin_set_window
** Message: plugin_get_value 15 (f)

** Message: unhandled variable 15 (f)
** Message: plugin_get_value 11 (b)

** Message: plugin_get_value 268435466 (1000000a)

** Message: GetHelperForLanguage 2
** Message: GetInterfaces
** Message: plugin_set_window
** Message: existing window
** Message: resize
** Message: leaving plugin_set_window
** Message: plugin_get_value 15 (f)

** Message: unhandled variable 15 (f)
** Message: plugin_get_value 11 (b)

** Message: plugin_get_value 268435466 (1000000a)

** Message: plugin_set_window
** Message: existing window
** Message: resize
** Message: leaving plugin_set_window
** Message: plugin_get_value 15 (f)

** Message: unhandled variable 15 (f)
** Message: plugin_get_value 11 (b)

** Message: plugin_get_value 268435466 (1000000a)

** Message: plugin_set_window
** Message: existing window
** Message: resize
** Message: leaving plugin_set_window
** Message: plugin_get_value 15 (f)

** Message: unhandled variable 15 (f)
** Message: plugin_get_value 11 (b)

** Message: plugin_get_value 268435466 (1000000a)

** Message: plugin_set_window
** Message: existing window
** Message: resize
** Message: leaving plugin_set_window
** Message: plugin_new_stream
** Message: plugin_new_stream type: text/plain url: http://www.ebaumsworld.com/2006/05/snakehippo.wmv
** Message: plugin_destroy
totemGMPPlugin dtor [0x8fb6798]
```

all i see is a gray box.  no audio or video plays at all, and no network activity takes place.

likewise, output from totem-xine:
```
** Message: totem_plugin_new_instance
totemGMPPlugin ctor [0x8dcb060]
mode 1
mime type: application/x-mplayer2
argv[0] type application/x-mplayer2
argv[1] pluginspage http://www.microsoft.com/Windows/MediaPlayer/
argv[2] src /2006/05/snakehippo.wmv
argv[3] autostart 1
argv[4] showcontrols 1
argv[5] volume -20
argv[6] height 285
argv[7] width 320
** Message: plugin_get_value 14 (e)

** Message: plugin_set_window
** Message: waiting for data to come
** Message: leaving plugin_set_window
** Message: plugin_get_value 15 (f)

** Message: unhandled variable 15 (f)
** Message: plugin_get_value 11 (b)

** Message: plugin_get_value 268435466 (1000000a)

** Message: GetHelperForLanguage 2
** Message: GetInterfaces
** Message: plugin_set_window
** Message: existing window
** Message: resize
** Message: leaving plugin_set_window
** Message: plugin_get_value 15 (f)

** Message: unhandled variable 15 (f)
** Message: plugin_get_value 11 (b)

** Message: plugin_get_value 268435466 (1000000a)

** Message: plugin_set_window
** Message: existing window
** Message: resize
** Message: leaving plugin_set_window
** Message: plugin_get_value 15 (f)

** Message: unhandled variable 15 (f)
** Message: plugin_get_value 11 (b)

** Message: plugin_get_value 268435466 (1000000a)

** Message: plugin_set_window
** Message: existing window
** Message: resize
** Message: leaving plugin_set_window
** Message: plugin_get_value 15 (f)

** Message: unhandled variable 15 (f)
** Message: plugin_get_value 11 (b)

** Message: plugin_get_value 268435466 (1000000a)

** Message: plugin_set_window
** Message: existing window
** Message: resize
** Message: leaving plugin_set_window
** Message: plugin_new_stream
** Message: plugin_new_stream type: text/plain url: http://www.ebaumsworld.com/2006/05/snakehippo.wmv
** Message: plugin_destroy
totemGMPPlugin dtor [0x8dcb060]
```

again, no audio, and a gray box appears where the video should be playing.  no network activity takes place.

with media player connectivity add-on enabled:
```
External func OLEAUT32.dll:8
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:230400  align:1
StreamCount r=0x0  1  1
Decoder supports the following YUV formats: YV12 YUY2 UYVY YVYU      
Decoder is capable of YUV output (flags 0x1b)
Total Unfree 60 bytes cnt 1 [(nil),0]
External func OLEAUT32.dll:8
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:230400  align:1
StreamCount r=0x0  1  1
Decoder supports the following YUV formats: YV12 YUY2 UYVY YVYU      
Decoder is capable of YUV output (flags 0x1b)
Total Unfree 60 bytes cnt 1 [(nil),0]
```
video plays fine, but there are two huge problems with this:
1) the target video area must be clicked on before the video will start to play.
2) it pops up in a new window, and must be manually closed.

will someone please tell me what i'm missing.

---

### Post by Dies on 2006-12-26
Well it would seem that one of three things is happening here, either no one cares about this, no one knows the answer or whoever knows the answer isn't here.

I tried to get this working properly for a few hours but had no luck, tried different plugins, tried different combinations of plugins, but nothing seemed to work across the board, it fixed something while breaking something else.
Being a new user I just chalked this up to inexperience, and installed the FF add-on. I agree with you that this shouldn't be needed and I find it clunky.

I don't understand why something that is so easy to get going in other distros doesn't work, but there's a lot about Ubuntu that I don't understand. Like why the Nvidia driver is broken up into 52 different packages, lol or why it picked up the volume key on my keyboard but it doesn't do anything except display a nice little graphic.

But, overall it's a pretty nice package so I'll leave it on the drive and maybe get to know it when I have the time.

Sorry I can't help but *Bump*

---

### Post by jake3988 on 2006-12-26
For some oddball reason mplayer and totem plugins are incompatible.  That is, if you have both they negate each other and neither work.

I've never used totem plugin.  However, mplayerplug-in has a .conf file which you need to set noembed=0 in order for it to stay in the box.

---

### Post by dmizer on 2006-12-26
> **jake3988 said:**
> For some oddball reason mplayer and totem plugins are incompatible.  That is, if you have both they negate each other and neither work.
this is not oddball.  it makes perfect sense.  if you have two plugins which perform the same function, and both are installed at the same time, how is firefox suppose to decide which one it is supposed to use?

either way, i am well aware of this and this is not the problem in my case.
> I've never used totem plugin.  However, mplayerplug-in has a .conf file which you need to set noembed=0 in order for it to stay in the box.
in my other thread, the problem is not that the video plays embedded or not embedded, i could not get it to cache before streaming which again means user interaction is required in order to make the video play.

---

### Post by dmizer on 2006-12-27
this has to be a problem with the libtotem-gmp-plugin.so file which handles the wmv files.

quick time media plays embedded with no issue using totem.

---

### Post by Dies on 2006-12-27
> **jake3988 said:**
> For some oddball reason mplayer and totem plugins are incompatible.  That is, if you have both they negate each other and neither work.

I've never used totem plugin.  However, mplayerplug-in has a .conf file which you need to set noembed=0 in order for it to stay in the box.

Yeah, that's expected behavior and it wasn't the problem in my case either.
So you're saying that the mplayer plugin works perfect for you on a stock install?

On my other distros getting FF set up is a matter of having mplayer installed along with all it's codecs then installing the plugins, except for the Real Media one which I use Real Player for, and setting a key so that it handles mms by default.
But that didn't work for me, did I miss something?

The only thing I didn't try is using FF straight from Mozilla. I know some distros make changes to the version of FF they ship with but not sure if Ubuntu does or what those would be.

---

### Post by dmizer on 2006-12-28
bump

---

### Post by dmizer on 2007-01-05
this issue remains unresolved.

is it simply not possible to play embedded media as embedded media in ubuntu edgy?

---

### Post by uncreative on 2007-01-06
Bump for the good guys....Edgy fried Totem, YIKES!


seriously though, I have been busting my head for a week trying to get this darn thing going.  I was talked into edgy by the promise of my Treo working...and then it killed totem!  Still didn't get that darn treo working either...

---

### Post by uncreative on 2007-01-06
OK, I had to come back and reply...I finally have video via mplayer.  It plays all forms embedded in web pages.  I've tried wmv (8 and 9), mpg, and avi.

Here's what I did.  when to usr/lib/firefox/plugins and removed everything that had totem in the file name.

Then ran this guy's script [http://www.ubuntuforums.org/showthread.php?t=323181&highlight=mplayer+wmv](http://www.ubuntuforums.org/showthread.php?t=323181&highlight=mplayer+wmv) (its a txt file, but download it and rename it to a .sh file, then sudo sh whatever.sh)

And bam, video played.


Hope this helps, I'll PM you too so you are sure to see this.

---

### Post by dmizer on 2007-01-07
thank you very kindly for at least trying, but that did not fix my mplayer problem.

my problem with mplayer is not that it would not play video.  in fact, it played video fine.  so does totem, and vlc for that matter.

my problem is that NONE of the above options will play correctly as an embedded player.

1) mplayer will not cache, so it tries to playe the video the instant it becomes available, and fails.  then mplayer caches the entire video and does not auto play.  you must right click and select "play" before the video will play.
2) totem with either gstreamer or xine simply displays a gray square where the video should be playing and no network activity takes place (problem described in this thread)
3) vlc does essentially the same thing as totem, only with a black screen which states that no video is available. 

this does not leave me with any options for playing embedded video in edgy.  zero, nada, nanimo nai, nothing ... unless i use the media player connectivity plug in.  which is completely undesirable in my particular deployment needs.

---

### Post by Gremlinzzz on 2007-01-07
Didi you config the mplayer plugin and install the codecs needed?try just having mplayer plugin installed only. then go to a site where you use it right click on screen then click configure   choose X11 then alsa for audeo.  heres the codecs that work best with mplayer.                                                    [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

---

### Post by dmizer on 2007-01-07
thank you for your reply.

codecs are not my problem.  video DOES play.  what's more, video plays clearly and with sound in sync.  i can make it play just fine with totem-gstreamer, totem-xine, mplayer, and vlc ... but ONLY if i use the media player connectivity plug in for firefox.

without the media player connectivity plugin for firefox, mplayer simply attempts to play the video without caching.  then, the entire video caches to 99% and sits there.  after which, i can play the video embedded if i right click and select "play".  otherwise it simply sits there and does nothing.

i need to avoid user interaction when playing embedded media.

---

### Post by motang on 2007-01-09
> **uncreative said:**
> OK, I had to come back and reply...I finally have video via mplayer.  It plays all forms embedded in web pages.  I've tried wmv (8 and 9), mpg, and avi.

Here's what I did.  when to usr/lib/firefox/plugins and removed everything that had totem in the file name.

Then ran this guy's script [http://www.ubuntuforums.org/showthread.php?t=323181&highlight=mplayer+wmv](http://www.ubuntuforums.org/showthread.php?t=323181&highlight=mplayer+wmv) (its a txt file, but download it and rename it to a .sh file, then sudo sh whatever.sh)

And bam, video played.


Hope this helps, I'll PM you too so you are sure to see this.

Dude it works really great, thanks.  This Ubuntu community is helpful. :-D

---

### Post by goonies on 2007-04-06
i removed totem and everything having to do with Totem off my system, installed win32 codecs and mplayer and the mozilla-mplayer plugin and wmv cache and play fine on my machine, here are some screenshots

[[IMG]http://xi.zshare.net/thumb/1483611/thumb.png[/IMG]](http://www.zshare.net/image/screenshot-4-png.html)[[IMG]http://lambda.zshare.net/thumb/1483617/thumb.png[/IMG]](http://www.zshare.net/image/screenshot-5-png.html)

as you can see in the first screenshot it starts to cache, u see its at 3%, for that particular video when it got to 7% it started playing

if u dont need totem get rid of it, all it did was cause problems for me and wmv

---

