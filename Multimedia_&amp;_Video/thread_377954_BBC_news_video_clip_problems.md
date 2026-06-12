---
title: "BBC news video clip problems"
date: 2007-03-06
forum: Multimedia &amp; Video
---

### Post by mrhelpman on 2007-03-06
There was an update of Firefox the other day on both my Dapper and Edgy installations and from that time I have been unable to watch the BBC new video clips in a browser window. I have reinstalled realplayer 10.0.8.805 and checked that all the sym links are in the various plugin directories.

The video clips do work if launched in the stand alone player and the radio (listen again and live stream) works in a browser window - it is only the video clips that fail.

Anyone else getting the same symptoms?

John T.

---

### Post by sdowney717 on 2007-03-06
I can only get them to work with mplayer plugin.
Can you switch click preferences and select windows media?

---

### Post by mrhelpman on 2007-03-07
Which package(s) do I need to install to get the mplayer firefox plugin? I have standalone mplayer already installed.

Ta

---

### Post by bwallum on 2007-03-08
This worked for me. Follow it carefully.
[https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9](https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9)

I'm watching BBC News now (Ubuntu 6.10)

---

### Post by bwallum on 2007-03-15
I've written my first Wiki page to help with streaming setup. [https://help.ubuntu.com/community/FirefoxStreamingVideo](https://help.ubuntu.com/community/FirefoxStreamingVideo)

Hope it helps, if not, tell me and I will change the page for others following.

Kind regards
Bob

---

### Post by ajaustin on 2007-03-15
Bob, I followed the simple instructions on your wiki page and have some progress.  I can now play BBC News clips but only if I select "launch in standalone player".  The BBC News Player screen says "gxine browser plugin" but does not launch the clip automatically.

Tony

---

### Post by bwallum on 2007-03-15
It may because the w32 codecs haven't taken. The following should help [http://ubuntuforums.org/showthread.php?p=1649012](http://ubuntuforums.org/showthread.php?p=1649012)

Can you tell me if you have gstreamer installed please?

---

### Post by ajaustin on 2007-03-15
Bob, yes I have lots of bits of gstreamer installed (there's plenty of it in Synaptic), but not absolutely everything.  I seem to have both 0.10 and 0.08 installed, not sure if this is right.

My totem was the xine version so I have uninstalled that and installed the gstreamer version BUT I can't install the totem-gstreamer-firefox-plugin because it's version 1.4.1-0ubuntu1 and totem gstreamer is 1.4.3-0ubuntu1.

I refreshed the .gstreamer-0.10 registry.

Still don't get the stream to launch in BBC NewsPlayer.

Tony

---

### Post by bwallum on 2007-03-15
I would remove the gstreamer plugin and go down the xine route. 

Using Synaptic remove gstreamer and install gxine and gxineplugin. (that is you will be using totem-gxine-firefox-plugin rather than totem-gstreamer-firefox-plugin).

I lost a lot of time with gstreamer but if you do get it to work do let me know.

Bob

I may have omitted that you also need to load the totem-xine file. You can do this in Synaptic. You'll see alongside this file the totem-gstreamer file. That is basically the choice you have using totem, you can go gstreamer or xine. I have never manged to get gstreamer working yet but xine works ok.

---

### Post by ajaustin on 2007-03-15
OK, I have gone back to totem-xine and uninstalled all of gstreamer-0.08 and most of gstreamer-0.10 (some of it seemed to be needed for other applications, eg Rhythmbox).

I still have the same situation, which is, I can play the video clips with standalone player but not streaming in the BBC NewsPlayer.

Launching firefox from the command line gives me the following warning when the BBC NewsPlayer launches:-

```
tony@ubuntu:~$ firefox
Warning: Color name "black" is not defined
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset

```

Tony

---

### Post by bwallum on 2007-03-16
Hi Tony

Open a new tab in your firefox browser. Type in 'about:plugins'.   Check the list returned and see if gxine starter plugin is present. It should be. Also check to see if any gstreamer plugin is present. It should not be. Check with SPM that 'totem-xine' is installed. It should be.

Sorry this is taking a long time. It would be great if you could help me fix the Wiki page [https://help.ubuntu.com/community/FirefoxStreamingVideo](https://help.ubuntu.com/community/FirefoxStreamingVideo) when you get going.

Let me know your results

Kind Regards
Bob

---

### Post by ajaustin on 2007-03-16
Bob, thanks for your help - no need for apologies.

In about:plugins I have:-

> Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.622 built with gcc 3.2.0 on Jul 18 2006

> gxine starter plugin
    File name: gxineplugin.so
    will start external gxine media player for embedded media streams

> Java(TM) Plug-in 1.5.0_05-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_05

> Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r63

> Totem Mozilla Plugin

    File name: libtotem_mozilla.so
    The Totem 1.4.1 plugin handles video and audio streams.

I find the last one interesting, well a bit interesting ...

totem-xine is installed.

And so is totem-xine-firefox-plugin.

Tony

---

### Post by bwallum on 2007-03-16
You are looking for version Totem 2.16.2 plugin.

You can get it from this link. [https://launchpad.net/ubuntu/edgy/i386/totem-mozilla/2.16.2-0ubuntu3](https://launchpad.net/ubuntu/edgy/i386/totem-mozilla/2.16.2-0ubuntu3)

You are nearly there!

---

### Post by ajaustin on 2007-03-16
Not so sure that we are nearly there ...

I can't install the package you suggested as it has unsatisfied dependencies - I am on Dapper remember.

I tried upgrading to version 1.4.3 which is the latest available for Dapper, but this didn't solve it.

I have also tried upgrading gxine and gxineplugin to versions 0.5.7-1 which are the latest for Dapper (backport).

By co-incidence on another web site it wants to use the xine player plugin and also shows "gxine browser plugin" in the embedded window and then gives the following error:-

> The xine engine failed to start.

No demuxer found - stream format not recognised.

So it seems the problem is not just the BBC.

Tony

---

### Post by bwallum on 2007-03-16
Ah...
I forgot about Dapper. I have never used Dapper. I think it best you re post a new thread and ask for help from someone experienced with setting up Dapper.  If you post a new thread you will get an answer, don't wait for somebody  else to answer this thread now, its too long.

I'm really sorry about this
Bob

---

