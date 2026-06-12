---
title: "Suggestion: Lets get rid of Adobe flash for flv once and for all"
date: 2010-06-03
forum: Multimedia Software
---

### Post by deckoff on 2010-06-03
I have idea, which I hope will give Ubuntu FF users streaming video inside browser with best quality once and for all. 
What do we have :
1.players that play flv without any problems. 
2. video download helper add-on - 100s of sites supported, I havent stumbled on an unsupported site so far. I just got an e-mail that states "Getting a text file with the video url could easily be done with another  addon connected to DownloadHelper: our addon has an API for adding  services like this one."
3 Greasemonkey add-on scripts - this one[ http://userscripts.org/scripts/show/50771]("http://userscripts.org/scripts/show/50771") gives idea of how I think the whole thing should work and what the interface should look
My idea:
1. Write an add-on that generates an txt file that contains all links to flv found on a certain page and saves them in a folder. The file is named after the page name ors/t
2. A script very much similar to the one above which gets the links from the file and writes the links under the video.And so on.
I will do my best to write the java scipts, but have no idea how to do txt with the links magic. If someone comes with an add-on that does that all of the above - gets the links and proceeds all the better.
I hope s/o likes my idea and we do it before Adobe releases a really good flash plugin( but I can only pray for this to happen, and I am not the one that likes to wait)

[]("http://userscripts.org/scripts/show/50771")

---

### Post by dv3500ea on 2010-06-03
There is a good program called [clive]("apt:clive") (or [cclive]("apt:cclive")) that downloads flash videos into a number of formats to overcome the inadequacies of flash. There is also a gui for either of these programs ([abby]("apt:abby")). It doesn't support all sites but it does support some of the more popular sites like youtube. Personally, I find clive works better than cclive for now. Perhaps browser plugins using these as a backend would be useful.
see: [http://code.google.com/p/clive/]("http://code.google.com/p/clive/"), [http://code.google.com/p/cclive/]("http://code.google.com/p/cclive/")

---

### Post by deckoff on 2010-06-03
Might be another option for a workaround, too :)

---

### Post by lovinglinux on 2010-06-03
> **deckoff said:**
> My idea:
1. Write an add-on that generates an txt file that contains all links to flv found on a certain page and saves them in a folder. The file is named after the page name ors/t
2. A script very much similar to the one above which gets the links from the file and writes the links under the video.And so on.
I will do my best to write the java scipts, but have no idea how to do txt with the links magic. If someone comes with an add-on that does that all of the above - gets the links and proceeds all the better.
I hope s/o likes my idea and we do it before Adobe releases a really good flash plugin( but I can only pray for this to happen, and I am not the one that likes to wait)

[]("http://userscripts.org/scripts/show/50771")

I have already created an extension that replaces the flash video with available x-mplayer videos. The extension is called [FlashVideoReplacer](http://flvideoreplacer-extension.blogspot.com). The only problem is that it doesn't work on every site. Currently, it supports YouTube (not channels), Vimeo and Blip.tv. Nevertheless, I have plans to add more sites to the supported list on each new version of the extension. 

The extension is pretty new, so you can expect a lot of things to come. It has been approved by Mozilla and it is already used by a couple of hundred Firefox users.

BTW, [here is the thread](http://ubuntuforums.org/showthread.php?t=1487327) about if you want to discuss it.

---

### Post by deckoff on 2010-06-04
> **lovinglinux said:**
> I have already created an extension that replaces the flash video with available x-mplayer videos. The extension is called [FlashVideoReplacer]("http://flvideoreplacer-extension.blogspot.com"). The only problem is that it doesn't work on every site. Currently, it supports YouTube (not channels), Vimeo and Blip.tv. Nevertheless, I have plans to add more sites to the supported list on each new version of the extension. 

The extension is pretty new, so you can expect a lot of things to come. It has been approved by Mozilla and it is already used by a couple of hundred Firefox users.

BTW, [here is the thread]("http://ubuntuforums.org/showthread.php?t=1487327") about if you want to discuss it.

Big "Thank YOU"! I've stumbled upon it for sure, and I'll give it a try.
I started this thread because I think I found an easy to implement solution, which will replace lots of sites. With DW helper you have thousands of sites supported.  Grab the link and send it to vlc or mplayer. Unfortunately I am a dentist with poor javascript knowledge only, and cannot do much of the programing:(. Wanted to share an idea.

---

### Post by lovinglinux on 2010-06-04
> **deckoff said:**
> Big "Thank YOU"! I've stumbled upon it for sure, and I'll give it a try.
I started this thread because I think I found an easy to implement solution, which will replace lots of sites. With DW helper you have thousands of sites supported.  Grab the link and send it to vlc or mplayer. Unfortunately I am a dentist with poor javascript knowledge only, and cannot do much of the programing:(. Wanted to share an idea.

It would be easier to contact Video Download Helper developers and ask them to include an option to launch the video with an external player. They certainly would be able to do that in less than a day.

Anyway, my extension objective is to replace the embedded video instead of downloading or launching it through an external player. What you are looking for is [MediaPlayerConnectivity](https://addons.mozilla.org/en-US/firefox/addon/446/). The only problem with that extension is that once you configure it to catch flash content, all flash embedded items on a page are intercepted, so if you are visiting a page with flash interface you have to click all items to see the page properly. I haven't used it for a while, but I will give it another shot to see how it is working these days. BTW, you can find more flash replacer extensions and scripts in my tutorial [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html).

What about the e-mail you received? That sounds fishy. What extension they were promoting?

---

### Post by deckoff on 2010-06-04
I wrote to download helper and asked them if they were willing to implement playing with external player inside FF, or at least provide txt file with download locations for current place. The answer was that adobe was needed to get locations for all different file sizes of the video and cannot be replaced. On the other hand, if I want s/t implemented, I should propose a feature and see if it is implemented. I haven;t done that
I have tried MediaPlayerConnectivity. It does not work properly with flash - it gets the location of the first swf file, which contains the download locations to the real media(as far as I know, I might be wrong). Actually, I would have been quite happy with working MediaPlayerConnectivity, but alas. That is why I am here today, trying to figure easy and effective workaround for as many sites as possible

---

### Post by lovinglinux on 2010-06-04
> **deckoff said:**
> I wrote to download helper and asked them if they were willing to implement playing with external player inside FF, or at least provide txt file with download locations for current place. The answer was that adobe was needed to get locations for all different file sizes of the video and cannot be replaced. 

I haven't thought about that. I haven't looked into vdh code, but it only shows the video download links after the flash video starts playing.  This information is very helpful to me, because now I know I'm in the right track with my extension. I thought it would be possible to implement something more efficient like vdh, but it seems is not possible. What I do is to grab the links from the page code (some hacks are needed) and then replace the flash object. It doesn't require to start the video first, but it still requires flash plugin.

> **deckoff said:**
> I have tried MediaPlayerConnectivity. It does not work properly with flash - it gets the location of the first swf file, which contains the download locations to the real media(as far as I know, I might be wrong).

It doesn't work for either. It does grab the first swf file.

> **deckoff said:**
> That is why I am here today, trying to figure easy and effective workaround for as many sites as possible

I have an idea. Not exactly the way you want, but the result would be the same. I would let you know when I have something useful ready for testing.

---

