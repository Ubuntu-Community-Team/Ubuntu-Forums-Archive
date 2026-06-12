---
title: "RealPlayer and Firefox 2"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by tiagobt on 2007-01-14
I'm using Ubuntu 6.10 and Mozilla Firefox 2.0.0.1, which is the current version in Ubuntu repositories. I'm trying to get the RealPlayer plugin to work with Firefox, but I'm having no luck. I installed RealPlayer 10 using the binary file (RealPlayer10GOLD.bin) and the installation was fine. RealPlayer itself is working, but not the plugin. I even uninstalled **mozilla-mplayer** to make sure the other streaming plugins would not interfere. I checked Firefox plugin folder and found both **nphelix.so** and **nphelix.xpt**, meaning the installation of the plugin was successful as well. When I type **about:plugins** in Firefox, I even get the text:

```
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

File Name: nphelix.so
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.622 built with gcc 3.2.0 on Jul 18 2006

MIME Type                            Description                         Suffixes          Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	           Yes
```

However, every time I try to play a RealPlayer streaming in Firefox, the plugin is not launched. I've read all [FAQs]("https://player.helixcommunity.org/2005/help/playerfaq.html") in Helix Community website, and I suspect the problem might be that RealPlayer and Firefox were built with two GCC different versions. The code above shows me that RealPlayer was built with GCC 3.2.0, whereas the command **about:buildconfig** in Firefox tells me that the browser was compiled with GCC 4.1.2.

Do you think that could be the problem? Is there any way to solve it? I'd rather not downgrade Firefox.

Thanks a lot,
Tiago

---

### Post by obsidion on 2007-01-14
> **tiagobt said:**
> I'm using Ubuntu 6.10 and Mozilla Firefox 2.0.0.1, which is the current version in Ubuntu repositories. I'm trying to get the RealPlayer plugin to work with Firefox, but I'm having no luck. I installed RealPlayer 10 using the binary file (RealPlayer10GOLD.bin) and the installation was fine. RealPlayer itself is working, but not the plugin. I even uninstalled **mozilla-mplayer** to make sure the other streaming plugins would not interfere. I checked Firefox plugin folder and found both **nphelix.so** and **nphelix.xpt**, meaning the installation of the plugin was successful as well. When I type **about:plugins** in Firefox, I even get the text:

```
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

File Name: nphelix.so
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.622 built with gcc 3.2.0 on Jul 18 2006

MIME Type                            Description                         Suffixes          Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	           Yes
```

However, every time I try to play a RealPlayer streaming in Firefox, the plugin is not launched. I've read all [FAQs]("https://player.helixcommunity.org/2005/help/playerfaq.html") in Helix Community website, and I suspect the problem might be that RealPlayer and Firefox were built with two GCC different versions. The code above shows me that RealPlayer was built with GCC 3.2.0, whereas the command **about:buildconfig** in Firefox tells me that the browser was compiled with GCC 4.1.2.

Do you think that could be the problem? Is there any way to solve it? I'd rather not downgrade Firefox.

Thanks a lot,
Tiago

  No mine works fine

Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.622 built with gcc 3.2.0 on Jul 18 2006

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes


  However you don't give a link to what doesn't work, it might be a website problem or a firewall problem as opposed to the real plugin not working. Mine works fine at Nasa and the BBC but I can't vouch for other places. Not however I am using a firefox build from mozilla not from ubuntu, so that could be the difference.

---

### Post by tiagobt on 2007-01-14
That's funny. I guess you're right. BBC videos do work inside Firefox using the RealPlayer plugin. Before, I was testing the plugin with [Real Guide]("http://guide.real.com/") videos, which I thought was the most straightforward way of testing. Turns out I was wrong. While most Real Videos play fine with it, the ones from Real Guide don't launch the plugin. Instead, Firefox asks me if I want to download the RA or RAM file.

Now, I just have to figure out why the videos look choppy sometimes. I guess I read something in the Helix Community FAQ. I'm going back there.

Thanks a lot for the help.

**Update:** I fixed the choppy video problem by following the tips I found in the Helix Community FAQ. What causes the problem is that RealPlayer uses OSS to output sound. Using the package alsa-oss, you can use ALSA instead by emulating OSS support. More information [here]("https://player.helixcommunity.org/2005/help/playerfaq.html#mozTocId185548").

---

### Post by obsidion on 2007-01-14
> I was testing the plugin with [Real Guide]("http://guide.real.com/") videos, which I thought was 
> the most straightforward way of testing. Turns out I was wrong. While most Real Videos play fine with it, the >ones from Real Guide don't launch the plugin. Instead, Firefox asks me if I want to download the RA or 
>RAM file.

  I would suspect that the fault lies in the realguide page using javascript

---

### Post by lokeshwer on 2007-02-17
I was able to play audio from real guide, bbcnews etc. But it doesnt work for raaga.com, musicindiaonlie.com. any idea?

---

