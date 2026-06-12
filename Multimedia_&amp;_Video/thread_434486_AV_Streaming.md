---
title: "AV Streaming"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by spamking2000 on 2007-05-06
Hey,

I'm a new user to Ubuntu, but not so new to Linux... I've been using Fedora as my main OS since September of last year.

There must be something really simple and obvious that I'm missing. Both in Fedora and Ubuntu, I never can seem to get media to stream correctly using the mplayer plugin for Firefox. Looking at Ubuntu more specifically, I used Automatix2 to install mplayer and the plugins. Upon the lack of working codecs, I went out and got the "all" package from mplayer.hu and extracted the package into /usr/lib/win32.

No response however. I get the standard loading/buffering messages in the mplayer-plugin window on which ever site I'm trying to stream from. cnn.com is a good example, but it seems to happen everywhere.

I've always had the same trouble with Fedora as well. While Automatix2 was neat from the perspective that it downloaded and installed the packages automatically and with ease, it gave me the same result as installing the codecs and mplayer-plugin (with or without mozplugger) in Fedora... no actual streaming video. The plugin loads, but never actually brings me video.

In Fedora, I've worked around this by using the totem-gstreamer plugins which everyone claims to hate... but they seem to work just fine for me. On my Fedora load, I can do everything but RealMedia files just fine. Since most sites that don't use flash seem to use wmv, that's okay with me to a point.

Even under Fedora, streaming audio from radio stations online has never worked, which to this day has me keeping a PIII 550mhz box with Windows on it :(

Ubuntu looks promising to me, but I don't see a place in the Add/Remove Software (whatever the Ubuntu equivalent to Pirut is) where I can switch over to totem-mozilla or totem-xine-mozilla for the plugins in Firefox. So it looks like I would be stuck with mplayer, but I can't get that to work.

On the plus side, some RealPlayer stuff seems to be working in Ubuntu. My biggest test is if you go to cbs.com there is a window on the main page that includes a RealMedia video, and that works. However if you try to stream one of their shows, I get the audio, but not the video. I installed RealPlayer via Automatix2. I never got that far with Fedora... I could install RealPlayer, but it never seemed to get the plugin going right.

I even tried CrossOver Office to get the WindowsMedia working. However, using the unsupported options, neither Windows Media Player 9 or 10 seem to install. Once it pulls up the main application, I just get a message that the software couldn't find any updates and it aborts installation. From the supported software, Windows Media Player 6.4 installs nicely and the plugin automatically comes up in Firefox. However, since most sites seem to require a higher version of the WMV codecs, this doesn't seem to do much good.

As a side note, I'm finding that software installed under Automatix2 doesn't seem to show up as installed when I go to the Add/Remove software package manager.

I know I've seen people do this. It has to work, and in today's linux environment it seems to me like it should be simple, so I feel like I must just me missing something. What however it another matter.

HELP!!! <please>  :)

Derrick

---

### Post by reclusivemonkey on 2007-05-06
Use mozilla-mplayer, and remove all the totem plugins from /usr/lib/firefox/plugins. Make sure you get rid of any totem plugins in your home directory too. Here's mine just for reference;

```

monkey@mother:~$ ls /usr/lib/firefox/plugins/
flashplayer.xpt        mplayerplug-in-qt.xpt  mplayerplug-in-wmp.so
libflashplayer.so      mplayerplug-in-rm.so   mplayerplug-in-wmp.xpt
libunixprintplugin.so  mplayerplug-in-rm.xpt  mplayerplug-in.xpt
mplayerplug-in-qt.so   mplayerplug-in.so

```

---

### Post by spamking2000 on 2007-05-11
Sooooo.... I started to reply earlier today because this is very similar to the experience that I had with Fedora. mplayer-plugins didn't work consistently, and instead I could get connecting (info with the stream) and it would get to Connected, but the stream would never start. Instead, it would stop, go back to connecting and the cycle would start all over again.

My remedy for that with my Fedora build was to use the totem plugins. They work pretty well, but I still have trouble with a few things. This is more for documentation purposes as I know other people will find this thread when having the same problem.

Totem / gstreamer / totem-xine all had the same results for me. In general, it handled Windows Media fine, but I had problems with a few sites including cspan.org and any streaming commercial radio station... such as the "listen live" links from 620kpoj.com and 850koa.com

In addition, if you go to cbs.com, there is a RealPlayer window on the right hand side that usually has a commercial or some program teaser of some kind. Depending on how I tweaked settings in mozplugger on the Fedora load, I once was able to get that to work, but that didn't last long.

If you use their "Innertube" portal for streaming TV show rebroadcasts, all the flash stuff would come up fine, but I would get an RTSP error before it would try to load any actual streaming content. I got past this at one point and I'm not sure what I did, but instead of getting an error, I just got a black screen for the portion of the screen where the stream should have been.

OK... so now that we have that for posterity, here's my experience with Ubuntu. First I had the same trouble with mplayer-plugin, but using Automatix, I didn't see an easy way to switch from mplayer to totem.

When I was going to respond to this, I wanted to include a screen shot of the mplayer-plugin not working. I took one shot after I had already hit stop, so that wasn't a very good example. Here's where it gets weird...

I hit play, and it worked. Its never worked before... I've always had the same result. I was testing using a news feed from cnn.com. I tried another one... it worked too.

I rebooted, tried again... this time it didn't work. Same connecting, connected, connecting, etc loop problem. So I hit stop, waited a few seconds, hit play - and what do you know? It worked.

OK... so on to my other more annoying problem, RealPlayer wasn't picking up shows through the flash enabled innertube portal. No change here - I still got audio and no video. I did a few searches on that and found a thread that led me to the **MediaPlayerConnectivity** addin for Firefox.

I installed it, left all the defaults at mplayer. Now everything works. Real Player picks up the Real Media streams, cbs.com has both audio and video, radio stations work, etc.

Here's the catch - With the exception of cbs.com, every piece of streaming media automatically opens up in an mplayer window. I had some trouble with cspan.org, so I tried using vlc... everything opens in vlc just fine and now I have controls for screen size adjustments, etc.

There's good and bad about this. In the good catagory, for the first time, every piece of streamed media I can throw at this thing seems to work one way or another. Of course this didn't affect Flash based streams which use the Adobe plugin and worked all along in either Fedora or Ubuntu.

Another really cool bit is that since radio stations open in a vlc or mplayer window, I can actually close the firefox window that they came from without interrupting the stream.

The downside is that I don't necessarily always want a new app window to open every single time I play a WindowsMedia based stream.

So on a hunch, I did a stupid user trick. I didn't uninstall MediaPlayerConnectivity, but I disabled it. Now WindowsMedia streams are back to the connecting, connected, connecting, connected loop until I hit stop, wait a few seconds and hit play... then they work just like before I installed MediaPlayerConnectivity. A little aggrivating, but not horrible. Radio streams work the same way. The real test was Real Player. I had tried alternating MediaPlayerConnectivity between mplayer, vlc, and RealPlayer when using innertube on cbs.com. Each time, it still chose RealPlayer and played the stream within the window.

With MediaPlayerConnectivity still installed, but disabled, I had the same result. RealMedia streams on innertube start up just fine and run the way they should using RealPlayer. Finally!

For anyone having these same problems, I'd recommend trying this out:
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

Note that I also tried it on my Fedora build (which is on FC6). Pretty much the same results with Windows Media, but it didn't change anything with the RTSP stream with Real Player. My guess is that its probably a configuration issue at this point.

Hope that helps a few people out there... and if anyone has any suggestions on how to get mplayer-plugin to load mms streams without hitting stop and play again... I'm all ears!

Thanks,
Derrick

---

### Post by nick1 on 2008-02-08
Greetings,

I too am experiencing a similar problem with watching c-span.org videos.
More details about my problem are located [here]("http://ubuntuforums.org/showthread.php?t=691153").

Were you able to resolve your problem and, if so, how did you do it?

Thanks,

---

