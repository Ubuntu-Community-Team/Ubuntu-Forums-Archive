---
title: "Adobe Flash Player 10.1.53.64 - Final"
date: 2010-06-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-06-10
Adobe Flash Player 10.1.53.64 - Final was just released:
[http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)

i downloaded this:
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)

how can i install it now?

Thanks in advance.

---

### Post by go7Ul1ai on 2010-06-10
Download the .deb file ;)

---

### Post by Glenn nl on 2010-06-10
No need for a .deb.
It´s already in the updates (atleast for me).

---

### Post by Merk42 on 2010-06-10
Meanwhile those of us with the 64bit version are waiting around.
[Critical vulnerability](http://www.adobe.com/support/security/advisories/apsa10-01.html)? Pah you're running Linux, a 64bit version to boot, we don't care about you

---

### Post by chrisccoulson on 2010-06-10
> **Merk42 said:**
> Meanwhile those of us with the 64bit version are waiting around.
[Critical vulnerability](http://www.adobe.com/support/security/advisories/apsa10-01.html)? Pah you're running Linux, a 64bit version to boot, we don't care about you

Which is precisely the reason we don't ship the 64-bit version in the archive, despite repeated claims from users that it works better than the 32-bit version

---

### Post by kurros on 2010-06-10
> **Merk42 said:**
> Meanwhile those of us with the 64bit version are waiting around.
[Critical vulnerability](http://www.adobe.com/support/security/advisories/apsa10-01.html)? Pah you're running Linux, a 64bit version to boot, we don't care about you

Neither do any mythical hackers embedding 64bit linux code to execute in their malicious flash apps.

---

### Post by nilarimogard on 2010-06-10
> **aviramof said:**
> Adobe Flash Player 10.1.53.64 - Final was just released:
[http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)

i downloaded this:
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)

how can i install it now?

Thanks in advance.

You should get an update (I got it already). If you're not using Maverick (though this is the Maverick forum, but anyway), enable the Ubuntu Partner repository and you'll get an update.

---

### Post by kahumba on 2010-06-10
> **kurros said:**
> neither do any mythical hackers embedding 64bit linux code to execute in their malicious flash apps.
+1

---

### Post by go7Ul1ai on 2010-06-10
I would really like to be able to install flash x64 in Maverick. Right now I'm having trouble installing the 32 bit for some reason. Must have messed something up..

---

### Post by jfernyhough on 2010-06-10
Mint has a package for 64-bit FP in their repos.

Just be careful if you add their repos to your sources as many packages will "upgrade" the standard Ubuntu versions (you can use apt pinning to get round that, however).

Until today you could get the 64-bit FP direct from Adobe (and copied into /usr/lib/mozilla/plugins or similar), though as of an hour ago they seem to have deleted the page and most references to the 64-bit plugin. Useful.

---

### Post by rajeev1204 on 2010-06-11
> **chrisccoulson said:**
> Which is precisely the reason we don't ship the 64-bit version in the archive, despite repeated claims from users that it works better than the 32-bit version


So if apple says it's 32 bit plugin is safe, you are sure it is ?

Its a closed source plugin.Who knows what monsters it hides.

But i get your point though .

---

### Post by zika on 2010-06-11
Good bye 64-bit Flash plugin... Good bye all-64-bit machine, You'll be missed...

---

### Post by cariboo on 2010-06-11
I kept a couple of copies of the 64-bit version, just in case. :)

---

### Post by taavikko on 2010-06-11
> **cariboo907 said:**
> I kept a couple of copies of the 64-bit version, just in case. :)

Likewise.

But, luckily there's html5 coming...

---

### Post by cascade9 on 2010-06-11
> **jfernyhough said:**
> Until today you could get the 64-bit FP direct from Adobe (and copied into /usr/lib/mozilla/plugins or similar), though as of an hour ago they seem to have deleted the page and most references to the 64-bit plugin. Useful.

Leaving this- 

> Flash Player 10 for 64-bit Linux               

The Flash Player 10.1 64-bit Linux beta is closed.  We remain committed to delivering 64-bit support in a future release of Flash Player.  No further information is available at this time. Please feel free to continue your discussions on the [Flash Player 10.1 desktop forums]("http://forums.adobe.com/community/labs/flashplayer10/flashplayer10").[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

That is so commited that I'm speechless :|

*edit- here is hoping that they will move the 64bit flash for linux out of beta soon, but I'm not holding my breath (even though since I'm speechless it wouldnt make a difference).

---

### Post by rajeev1204 on 2010-06-11
Ok i too have kept some copies just in case there is no more 64 bit available.Wow breaking news :D

---

### Post by zika on 2010-06-11
> **cariboo907 said:**
> I kept a couple of copies of the 64-bit version, just in case. :)Nevertheless they are copies of dead-end... :)
I've tried 10.1 (32-bit) on my machine and all the troubles with flash plugin in FF3.7 etc, are gone. Obviously even FF and others are building around 10.1... Sad, but true...

---

### Post by moviemaniac on 2010-06-11
Damn, the new official 32-bit version broke flash in Opera for me :(
The plugin is detected but youtube only shows a "black hole".

Back to the old 64bit-build hoping no one will attack my system.

I tried gnash and other alternatives but none of these worked on *all* the sites I need. I hate flash :(

//edit: I figured it out. With Opera being the most intelligent browser it needs to be pointed to the 32-bit library as it has its own 64bit-wrapper. All's well now - except for that binary blob on my HDD. I don't like blobs.

---

### Post by taavikko on 2010-06-11
> **zika said:**
> Nevertheless they are copies of dead-end... :)


No dead-ends, just obstacles :)

Anyone tried the lightspark?

---

### Post by chrisccoulson on 2010-06-11
> **rajeev1204 said:**
> So if apple says it's 32 bit plugin is safe, you are sure it is ?

Its a closed source plugin.Who knows what monsters it hides.

But i get your point though .

Right, but that's a separate issue really.

The fact is that it's unacceptable for us to distribute such a widely used piece of software that does not receive patches or support for publicly disclosed security vulnerabilities with known exploits in the wild. The fact that it is closed source and could be hiding other vulnerabilities is another issue - those vulnerabilities are yet to be discovered or made public.

---

### Post by philinux on 2010-06-11
MAV 64 bit.

I just installed the 32 bit version and renamed my 64 bit plugin as .save.

First impressions are that the buttons all work as supposed to now. Full screen flash is not as good however. I guess I'll stick with this for now.
Better safe than sorry.

---

### Post by Merk42 on 2010-06-11
> **taavikko said:**
> Likewise.

But, luckily there's html5 coming...

Shut up Shut up SHUT UP! HTML5 IS NOT A DROP IN REPLACEMENT FOR FLASH
](*,)

---

### Post by taavikko on 2010-06-11
> **Merk42 said:**
> Shut up Shut up SHUT UP! HTML5 IS NOT A DROP IN REPLACEMENT FOR FLASH
](*,)

O'rly....

For most use cases the video tags in html5 offers the functionality that users need the flash.

Still need something to replace the games/ads/etc.

---

### Post by Merk42 on 2010-06-11
> **taavikko said:**
> O'rly....

For most use cases the video tags in html5 offers the functionality that users need the flash.

Still need something to replace the games/ads/etc.

Ya rly and you say as much in your post

There are sites that use Flash for games and ads like you said even websites built entirely out of Flash.

---

### Post by taavikko on 2010-06-11
> **Merk42 said:**
> Ya rly and you say as much in your post

There are sites that use Flash for games and ads like you said even websites built entirely out of Flash.

I do, don't I.

Those sites built entirely on flash shows the lack of common sense.
Like I said in previous post, that still is needed an alternative to flash concerning games/ads/sites_built_entirely_on_flash.

I still would claim that the most common use case for flash is video playback like youtube. Then html5 and whatever the video format is used is far better option than flash.

---

### Post by Merk42 on 2010-06-11
> **taavikko said:**
> I still would claim that the most common use case for flash is video playback like youtube. Then html5 and whatever the video format is used is far better option than flash.

I do not disagree with that.

A lot of people seem to think HTML5=Flash when really the only time that's applicable is video.

Unfortunately we won't see it widely adopted until something like 2015.
XP (supported until 2014) cannot upgrade to IE9 when it comes out and if you think a user is going to download and install a separate browser to watch your videos* you're mistaken.

*unless you're Youtube, but while they are converting videos, who knows when, if ever, they'll get rid of the Flash option

---

### Post by taavikko on 2010-06-11
> **Merk42 said:**
> if you think a user is going to download and install a separate browser to watch your videos* you're mistaken.

*unless you're Youtube, but while they are converting videos, who knows when, if ever, they'll get rid of the Flash option

Personally I would restrict access to my pages with IE*
But luckily I don't have to make that decision.

Google and Apple are not fond of flash, so switch from flash might be sooner than we anticipate. At least in videos.

Let's wait and see what happens in future...

---

### Post by xebian on 2010-06-11
Adobe just killed the 64-bit for Linux

[http://labs.adobe.com/technologies/flashplayer10/64bit.html):P](http://labs.adobe.com/technologies/flashplayer10/64bit.html):P)

---

### Post by pferraro on 2010-06-11
> **taavikko said:**
> No dead-ends, just obstacles :)

Anyone tried the lightspark?

Yes.  IMO, lightspark is *very* immature - though it is evolving quite rapidly (i.e. as opposed to gnash, they seem to release early and often).  The latest version (0.4.1) is supposed to support youtube videos.  As an owner of a intel graphics chip I'm not too keen on the design choice of using the opengl video sink.

There is a ppa for it, though it does not yet contain maverick packages:
ppa:sssup/sssup-ppa

Unfortunately, installing the lucid version will install libavutil49 and break your ffmpeg capabilities.

---

### Post by saturnblackhole on 2010-06-11
so from reading this thread adobe made a flash 10.1 64bit plugin and pulled it? can someone upload the plugin to a file hosting site? i would really like to use it

---

### Post by taavikko on 2010-06-11
> **saturnblackhole said:**
> so from reading this thread adobe made a flash 10.1 64bit plugin and pulled it? can someone upload the plugin to a file hosting site? i would really like to use it

No, 64bit plugin saw the day of light.
it remained at the version number of 10.42*

---

