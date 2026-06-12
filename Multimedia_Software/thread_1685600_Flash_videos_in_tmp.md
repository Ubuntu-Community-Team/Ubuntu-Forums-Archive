---
title: "Flash videos in /tmp/"
date: 2011-02-10
forum: Multimedia Software
---

### Post by TheBuzzSaw on 2011-02-10
I used to be able to buffer YouTube videos and grab the video from /tmp/ and copy it to my home folder. Well, I just noticed that YouTube videos are no longer showing up in /tmp/. Did they change something? Is anyone else having this problem?

---

### Post by JOHNNYG713 on 2011-02-10
Yea They changed the way Firefox stores stuff, now they go to some waky folders and it is nearly imposable to find them ! There is a script floating around that will tell you where the clip is, (I will see if I can find it and post back) But I use "Down them all" In Firefox Addon's Works great and it lets you save in any folder you want ! There are several more add ons like this in Firefox add ons! Just click the "Tools" tab in Firefox then Add-ons, and search !

---

### Post by TheBuzzSaw on 2011-02-11
Arggggh... Any way to change it back? XD

---

### Post by polardude1983 on 2011-02-11
Same problem here, and just found this thread. We need this again. This was the one best thing about linux!

---

### Post by Bucky Ball on 2011-02-11
Tried Easy Youtube Video Downloader? It is a Firefox extension.

---

### Post by polardude1983 on 2011-02-11
For those who dont use firefox and use chrome or chromium. I found out how to do it now. but it makes it more complicated.

read this article hopefully my comments make it easier to get

[http://n00bsys0p.wordpress.com/2011/02/10/how-to-download-flash-10-2-video-streams-in-linux/#comment-92](http://n00bsys0p.wordpress.com/2011/02/10/how-to-download-flash-10-2-video-streams-in-linux/#comment-92)

---

### Post by Cr0wza on 2011-02-11
Google for an app called "ClipGrab"

It works great in Firefox!

---

### Post by polardude1983 on 2011-02-11
Clipgrab is nice but it can't get videos from [www.narutoget.com](www.narutoget.com)

---

### Post by Myone on 2011-02-11
The solution posted in the link  by polardude ( [http://n00bsys0p.wordpress.com/2011/02/10/how-to-download-flash-10-2-video-streams-in-linux/#comment-92](http://n00bsys0p.wordpress.com/2011/02/10/how-to-download-flash-10-2-video-streams-in-linux/#comment-92) )

works well in Firefox 3.6.13, 32 bit.

---

### Post by fmdex2011 on 2011-02-11
on Ubuntu 10.10 i386
take a peak in:

/home/yourlogin/.mozilla/firefox/xxxxxxxx.default/Cache

turn on view hidden files

---

### Post by fmdex2011 on 2011-02-11
PS   Make sure you increase your cache size in Firefox to fit whatever you are watching, otherwise the file will vaporize after the download is complete.  The default size is 50MB, I changed mine to 300MB to be safe.  In Firefox click Edit, Preferences, Advanced, and the Network tab, use the Offline Storage spinner

Also, the files will stay in the Cache if you move to another web page, so make sure you have enough space
By the way.  divx and avi files still go to /tmp/    Hope this helps

---

### Post by xtremethegreat1 on 2011-02-12
They really did change it then. And I thought it was some problem with my browser.

---

### Post by mikewhatever on 2011-02-12
Why do people think the change has anything to do with Firefox? Apparently, it's not, as Firefox hasn't been updated for the past two months or so. :P
The downloaded files are easily locatable, and there are a couple of threads explaining how to find them. Just use the search function.

---

### Post by TheBuzzSaw on 2011-02-13
Yeah, I bookmarked the new location. It's just harder to see the videos now since they are usually surrounded in clutter. I'll live. I just miss going to /tmp/.

And wow, only 300 MB? I think I cranked my cache to 2 GB. XD

---

### Post by maghoxfr on 2011-02-17
> **Myone said:**
> The solution posted in the link  by polardude ( [http://n00bsys0p.wordpress.com/2011/02/10/how-to-download-flash-10-2-video-streams-in-linux/#comment-92](http://n00bsys0p.wordpress.com/2011/02/10/how-to-download-flash-10-2-video-streams-in-linux/#comment-92) )

works well in Firefox 3.6.13, 32 bit.

It also worked on chromium.

---

### Post by WSmart on 2011-02-17
Is it Fedora 14 now?  Wonder if it's botched there too?  

Problem with increasing your cache -that can cause your browser to bog down, fyi.

Thanks all!

Beer is queer.  Be real, be sober.

---

### Post by kn0w-b1nary on 2011-02-17
Why not use Karbon? It's also a Firefox addon.

---

### Post by maghoxfr on 2011-02-17
> **kn0w-b1nary said:**
> Why not use Karbon? It's also a Firefox addon.

Is there any addon or plugin for chromium that you know?

---

### Post by kn0w-b1nary on 2011-02-18
> **maghoxfr said:**
> Is there any addon or plugin for chromium that you know?

I don't, but you can also use [www.savevid.com](www.savevid.com)
copy-paste the URL, works with more than youtube.

---

### Post by joomy2 on 2011-02-18
Hi guys, I`m using Linux Mint but I guess it`s the same thing as Ubuntu,
I followed these instructions here

[http://www.tubemaster.net/down.html](http://www.tubemaster.net/down.html)

Mint already has [B][Java SE Runtime Environment (JRE).]("http://java.sun.com/javase/downloads/index.jsp") 
and [/B][B][Java SE Development Kit (JDK).]("http://java.sun.com/javase/downloads/index.jsp")  preinstalled, I`m not sure about Ubuntu.

[/B]Tubemaster captures "locked" swf videos that many sites use these days. Not sure
why these sites want to stop people from saving their videos, it`s not like they
are copyright protected but I guess they have their reasons.
Anyway this programs great, give it a try.
joomy

---

### Post by dabl on 2011-02-18
> **maghoxfr said:**
> Is there any addon or plugin for chromium that you know?

[http://www.chromeextensions.org/utilities/chrome-youtube-downloader/](http://www.chromeextensions.org/utilities/chrome-youtube-downloader/)

---

### Post by maghoxfr on 2011-02-18
> **dabl said:**
> [http://www.chromeextensions.org/utilities/chrome-youtube-downloader/](http://www.chromeextensions.org/utilities/chrome-youtube-downloader/)

thanks, but that's just for youtube. I think I'll stick to the "new" methodology. If someone comes up with a script it would be awesome if it was posted here ;)

---

### Post by eire spade on 2011-02-19
I don't know why, but recently, it doesn't work anymore.

I don't know what files are normally needed to get it fixed immediately, since I'm not that much of genius to know what files are inside my tmp folder before the downloadings stopped. I also don't know how to use the terminal yet... or know how to save one.

Can anyone help me fix this problem? I think I have to delete some unwanted files in /tmp so it would work again. Can someone please help me delete some of them so I can have the normal working /tmp which downloads the videos I finish loading?

How can I make it work again? Am I missing some files from /tmp?

---

### Post by howefield on 2011-02-19
Threads merged.

---

### Post by chetancrasta on 2011-02-24
Hello everyone.
None of the methods described by previous posters are as convenient as just copying the flash file from the tmp directory.

Therefore, what I did was downgrade my Flash to 10.1.102.64

The download link for older versions of flash is [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Download the (large) file named "Flash Player 10.1.102.64 and 9.0.289.0".
After downloading, extract the file named flashplayer10_1r102_64_linux.tar.gz

From this file extract libflashplayer.so and overwrite the file at /usr/lib/flashplugin-installer (you will need root privileges, try gksudo nautilus)

Restart Firefox and your flash videos will land up in the /tmp directory as before! This won't work for Google Chrome, it will continue to use the latest version of Flash.

Note: For the above steps to work, a version of Adobe Flash should have been previously installed.

---

### Post by WSmart on 2011-02-24
@chetancrasta   That explains it.  Thanks.

i say we go Apple and ditch Flash.

---

### Post by JRV on 2011-02-25
If I downgrade flash will the update manager try to upgrade it again?

What about a future flash upgrade?

---

### Post by ron999 on 2011-02-25
> **JRV said:**
> If I downgrade flash will the update manager try to upgrade it again?
No.
Synaptic package manager thinks that 10.2 is installed, but Firefox knows that 10.1 is installed.

---

### Post by JRV on 2011-02-25
Thank you Ron, that's great.

---

### Post by daveola on 2011-03-13
> **maghoxfr said:**
> If someone comes up with a script it would be awesome if it was posted here ;)

Here's a script that will help you copy flash (and other) files that are using the open/delete technique that Chrome/Firefox and the new flash plugin are using:

[http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html]("http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html")

Hope it's useful!

(The script is at the bottom of the page)

---

### Post by maghoxfr on 2011-03-13
> **daveola said:**
> Here's a script that will help you copy flash (and other) files that are using the open/delete technique that Chrome/Firefox and the new flash plugin are using:

[http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html]("http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html")

Hope it's useful!

(The script is at the bottom of the page)

THANK YOU!!!!!!!!!!!!!!!!! You are awesome! Thanks for that, it worked great.

---

### Post by TheBuzzSaw on 2011-04-01
Hmmm... So, now I cannot find the videos even in the cache folder. Where are videos hidden in Firefox 4?

---

### Post by wolfen69 on 2011-04-01
I use a firefox add-on called VideoDownloadHelper. It's awesome and will even convert the videos to another format.

---

### Post by maghoxfr on 2011-04-01
> **wolfen69 said:**
> I use a firefox add-on called VideoDownloadHelper. It's awesome and will even convert the videos to another format.

That's awesome. I'm using chromium and it's a great browser, but Firefox is pretty great too. I'll try that.

---

### Post by TheBuzzSaw on 2011-04-02
Ho hum. I finally cracked and installed a add-on. (I wasn't opposed to add-ons for this job before. I just liked knowing I could grab the raw buffer myself.)

---

### Post by maghoxfr on 2011-04-02
> **TheBuzzSaw said:**
> Ho hum. I finally cracked and installed a add-on. (I wasn't opposed to add-ons for this job before. I just liked knowing I could grab the raw buffer myself.)

Yeah me too, I really dislike this new flash.

---

### Post by lpwaqas on 2011-04-03
Hmm

Why not copy the already buffered flash content from  Home > You > .mozilla > firefox > your.default > Cache that would save the bandwidth too :) cause once it was browsed got pre-buffered so it basically works likes copying from /tmp like in old days :D

I wouldn't go for downgrading the whole  flash player for this.

---

### Post by TheBuzzSaw on 2011-04-04
> **lpwaqas said:**
> Hmm

Why not copy the already buffered flash content from  Home > You > .mozilla > firefox > your.default > Cache that would save the bandwidth too :) cause once it was browsed got pre-buffered so it basically works likes copying from /tmp like in old days :D

I wouldn't go for downgrading the whole  flash player for this.

I *was* doing this until Firefox 4 came out. Now, I can't see anything in my cache. I see an endless tree of numbered folders.

---

### Post by chetancrasta on 2011-04-10
Here is script that makes downloading flash videos even easier than copying it from /tmp: [http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html](http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html)
This technique is better than downgrading Flash because older versions of Flash have security vulnerabilities.

---

### Post by maghoxfr on 2011-04-10
> **chetancrasta said:**
> Here is script that makes downloading flash videos even easier than copying it from /tmp: [http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html](http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html)
This technique is better than downgrading Flash because older versions of Flash have security vulnerabilities.

That's what I'm using and it works great. You can't choose which videos to get, it rips every video you have in the folder. But it has already been posted in this thread.

---

