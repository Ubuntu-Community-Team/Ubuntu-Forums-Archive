---
title: "Alpha 3"
date: 2011-03-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by firstc624 on 2011-03-03
So i know it is released today, i need o redownload my kubuntu version since my current version is borked and chroot into it won't work...does anyone know the est time?

---

### Post by jppr on 2011-03-03
[http://cdimage.ubuntu.com/kubuntu/daily-live/20110303/](http://cdimage.ubuntu.com/kubuntu/daily-live/20110303/)

---

### Post by cariboo on 2011-03-03
There really isn't a set time for the release, it will be released when it's ready

---

### Post by ubuntu27 on 2011-03-03
Real Alpha3 is here:

[http://cdimage.ubuntu.com/releases/natty/alpha-3/](http://cdimage.ubuntu.com/releases/natty/alpha-3/)

---

### Post by chrisccoulson on 2011-03-03
> **ubuntu27 said:**
> Real Alpha3 is here:

[http://cdimage.ubuntu.com/releases/natty/alpha-3/](http://cdimage.ubuntu.com/releases/natty/alpha-3/)

Until it is accounced officially, those ISO's could change at any moment, resulting in people downloading broken ISO's and wasting a lot of time

---

### Post by webme on 2011-03-03
> **chrisccoulson said:**
> Until it is accounced officially, those ISO's could change at any moment, resulting in people downloading broken ISO's and wasting a lot of time

When will firefox integration with Global-M land in Natty main repo (not the PPA)?

---

### Post by chrisccoulson on 2011-03-03
> **webme said:**
> When will firefox integration with Global-M land in Natty main repo (not the PPA)?

Not sure how that's relevant to this thread ;)

But, to answer your question - about 25 minutes ago [https://launchpad.net/ubuntu/+source/firefox/4.0~b12+build1+nobinonly-0ubuntu3]("https://launchpad.net/ubuntu/+source/firefox/4.0~b12+build1+nobinonly-0ubuntu3")

---

### Post by webme on 2011-03-03
> **chrisccoulson said:**
> Not sure how that's relevant to this thread ;)

But, to answer your question - about 25 minutes ago [https://launchpad.net/ubuntu/+source/firefox/4.0~b12+build1+nobinonly-0ubuntu3]("https://launchpad.net/ubuntu/+source/firefox/4.0%7Eb12+build1+nobinonly-0ubuntu3")

I asked the question in the sense that perhaps it will land with Natty Alpha 3.
Thanks, nice to hear.

---

### Post by KegHead on 2011-03-03
Hi!

I'm using a3 as I write this memo.

I love 10.10.

KegHead

---

### Post by plun on 2011-03-03
Out:

[http://www.ubuntu.com/testing/natty/alpha3](http://www.ubuntu.com/testing/natty/alpha3)



--

---

### Post by jppr on 2011-03-03
> **plun said:**
> Out:

[http://www.ubuntu.com/testing/natty/alpha3](http://www.ubuntu.com/testing/natty/alpha3)



--

Doesn´t work, why Canonical publishes crap like this which isn´t even able to install?  :confused:  System is amd athlon II, nvidia, asus, 4 Gt ddr2

---

### Post by Harry33 on 2011-03-03
Please read this claim in Ubuntu alfa3 announcement:
[http://www.ubuntu.com/testing/natty/alpha3](http://www.ubuntu.com/testing/natty/alpha3)

```
**Known issues**
...  
Graphics and Display
  
The binary video drivers -fglrx and -nvidia do not have XServer 1.10 compatibility,
so do not function in Alpha 3.
We anticipate receiving an updated driver with this support from NVIDIA in the coming weeks,
and an updated -fglrx from AMD at some point prior to Natty's release,
but do not know their exact ETAs.  
``` 

Well I do not accept this. I do not think it is true. **It is an error**.
Nvidia binary drivers in Natty repos (270.29) do work and support the latest xserver 1.10 rc2 in Natty repos.
Natty alfa3 has exactly the same xserver 1.10 rc2 as in official repos at the moment.

I have those installed, I bet Nvidia drivers work better than any other driver around with this xserver rc2.

---

### Post by cariboo on 2011-03-03
Harry33 you can create a bug about it, but I think they are just trying to err on the side of caution, just in case they don't work. Remember Ubuntu still doesn't recommend 64-bit versions, even though most of us have been using it for years.

---

### Post by Harry33 on 2011-03-03
> **cariboo907 said:**
> Harry33 you can create a bug about it, but I think they are just trying to err on the side of caution, just in case they don't work. Remember Ubuntu still doesn't recommend 64-bit versions, even though most of us have been using it for years.

That is true, after all.

---

### Post by VastOne on 2011-03-03
Been having issues trying to install Alpha for several days. On a clean install it gets to nearly the end and fails.  Alpha3 did the same today, so I decided to install a fresh Maverick and upgrade (update-manager -d)

This failed too (Unable to calculate) and the var/log showed ubuntu-desktop as the issue. 

I removed ubuntu-desktop and now it is installing with about an hour to go and will post when finished.

Edit: This in fact did work, it wasn't pretty but it got me to Natty Alpha 3 to at least help in the testing.

My first impression is everything is considerably slower....

One other note on this, I loaded Xubuntu Natty (Alpha) and had none of these issues, so it is definitely related to the Ubuntu-Desktop

---

### Post by KegHead on 2011-03-03
Hi!

I know it's an alpha and it's OK.

I'm just spoiled w/10.10.

KegHead

---

### Post by ubuntu27 on 2011-03-03
> **chrisccoulson said:**
> Until it is accounced officially, those ISO's could change at any moment, resulting in people downloading broken ISO's and wasting a lot of time

It was already announced ;-) That was the official URL given in the Alpha 3 announcement. :popcorn:

---

### Post by Quackers on 2011-03-04
Mine doesn't work either. It got to 86% the first time then just hung there and gave me a live desktop instead. The second and third time it said "we're sorry the installer crashed". Nice :-)  Waste of time and effort, but nice. I have a new coaster anyway :wink:

Aha! I just ran the md5sum and it gives no output whatsoever! What the? 688.8MB of nothing?

---

### Post by NightwishFan on 2011-03-04
> **jppr said:**
> Doesn´t work, why Canonical publishes crap like this which isn´t even able to install?  :confused:  System is amd athlon II, nvidia, asus, 4 Gt ddr2

:lolflag: This gave me a chuckle. Where did you learn how to ask for help? Trust me. This is not how you do it. :D

The alpha/beta releases are for developers and testers only. They are certainly not "published" and not release ready. Also "not install" is not descriptive enough. You should start a new thread and give relevant information about your problem. If you are not able to do this, generally you should stick to the released versions.

(also forgive if I sound condescending, I am not trying to be)

> **Quackers said:**
> Aha! I just ran the md5sum and it gives no output whatsoever! What the? 688.8MB of nothing?

Usually no output is good output though I still think it should run through the file list. You need to be in the directory of the CD for it to work.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by kansasnoob on 2011-03-04
> **chrisccoulson said:**
> Until it is accounced officially, those ISO's could change at any moment, resulting in people downloading broken ISO's and wasting a lot of time

+1!

I did quite a bit of iso-testing and the release team may well have decided to delay the official release.

---

### Post by Quackers on 2011-03-04
I was in the correct directory but after 2 tries which gave no output I gave up.
However, I just tried again and the output appeared :-) It was correct.

On a different note, I think jppr may be beyond asking for help! I don't think that was his/her point :-)
He does have a point, I believe. If a cd image is released, and assuming that the download is complete and correct, it should work! End of story! Whether it's for an alpha/beta or whatever.
The image takes time to download and uses up (for some people) a chunk of their monthly download limit. A certain amount of annoyance is perfectly normal, I would suggest :-)

---

### Post by Quackers on 2011-03-04
> **kansasnoob said:**
> +1!

I did quite a bit of iso-testing and the release team may well have decided to delay the official release.

It has been announced hasn't it? My Kubuntu alpha 3 was D/L'd from officialdom.

---

### Post by VMC on 2011-03-04
> **Quackers said:**
> ...

Aha! I just ran the md5sum and it gives no output whatsoever! What the? 688.8MB of nothing?

It has to give some output. How did you run md5sum? 
If you download to your home folder, then from a terminal ```
md5sum natty-desktop-amd64.iso [or whatever arch your using]
```

---

### Post by Quackers on 2011-03-04
It was on my desktop, I cd'd to Desktop and ran md5sum natty-desktop-amd64.iso and it hung there for about 5 seconds and then the prompt returned. I tried it again and the same thing happened.

---

### Post by chrisccoulson on 2011-03-04
> **ubuntu27 said:**
> It was already announced ;-) That was the official URL given in the Alpha 3 announcement. :popcorn:

That official URL is online for some time before the announcement. At the time that the URL had been mentioned in this thread, there had been no announcement

---

### Post by VMC on 2011-03-04
> **Quackers said:**
> It was on my desktop, I cd'd to Desktop and ran md5sum natty-desktop-amd64.iso and it hung there for about 5 seconds and then the prompt returned. I tried it again and the same thing happened.

From you Desktop, right-click and open with archive manager. See if it errors out or does in fact open up.

---

### Post by Quackers on 2011-03-04
It opens up ok. Shows all the folders/files.

---

### Post by VMC on 2011-03-04
> **Quackers said:**
> It opens up ok. Shows all the folders/files.

Try your md5sum on another know good ISO.

Also try:  ```
sum natty-desktop-amd64.iso
``` on that questionable file.

---

### Post by Quackers on 2011-03-04
This is the output
```
nattyalpha@nattyalpha-VGN-AR51SU:~$ cd ~/Desktop
nattyalpha@nattyalpha-VGN-AR51SU:~/Desktop$ sum natty-desktop-amd64.iso
09628 705304
nattyalpha@nattyalpha-VGN-AR51SU:~/Desktop$ 

```

---

### Post by VinDSL on 2011-03-04
It  *probably* goes without saying, for the majority of you, but...

HTTP file transfers are notoriously flaky!

I prefer to use FTP transfers, but HTTP is more convenient, soooo...

The hot setup, when doing HTTP transfers is to use a download manager.

Assuming that you are using Firefox for HTTP file transfers, all you have to do is install an add-on called "DownThemAll" aka dTa.

Once you've installed dTa, go to the A3 page, select your download, enter the checksum and download location into dTa, and hit 'the button'.  dTa will take care of the rest.

Here's a screenie of Fx/dTa in action...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-4-mar-2011(3)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-4-mar-2011(3).png")[/INDENT]


Truthfully, I've NEVER had a HTTP download failure using Firefox / DownThemAll!  ;)

Ok, onward and upward!  I'm going to install A3 now...

---

### Post by VastOne on 2011-03-04
> **VinDSL said:**
> It  *probably* goes without saying, for the majority of you, but...

HTTP file transfers are notoriously flaky!

I prefer to use FTP transfers, but HTTP is more convenient, soooo...

The hot setup, when doing HTTP transfers is to use a download manager.

Assuming that you are using Firefox for HTTP file transfers, all you have to do is install an add-on called "DownThemAll" aka dTa.

Once you've installed dTa, go to the A3 page, select your download, enter the checksum and download location into dTa, and hit 'the button'.  dTa will take care of the rest.



Truthfully, I've NEVER had a HTTP download failure using Firefox / DownThemAll!  ;)

Ok, onward and upward!  I'm going to install A3 now...

I can officially state that I have seen your Conky screenshots 1100 more times than I have had a "flaky" http file transfer issue... :P

I use a different dload plugin and know for a fact my iso files were fine..

As stated above, ubuntu-desktop was the issue for me

---

### Post by TenPlus1 on 2011-03-04
xubuntu alpha 3 refused to boot, ending up in a use shell with 'cannot mount filesystem error'...

ubuntu alpha 3 booted into installer but desktop crashed my setup, turns out Unity causes all sorts of problems, so I updated my existing alpha 1 to alpha 3 and ran the classic desktop...

---

### Post by VastOne on 2011-03-04
> **TenPlus1 said:**
> xubuntu alpha 3 refused to boot, ending up in a use shell with 'cannot mount filesystem error'...

ubuntu alpha 3 booted into installer but desktop crashed my setup, turns out Unity causes all sorts of problems, so I updated my existing alpha 1 to alpha 3 and ran the classic desktop...

Similar to what I experienced ..to let you know, after running classic desktop and then back to Unity, it loaded fine... I am not sure if it was related to an update or not...

---

### Post by Quackers on 2011-03-04
My Kubuntu alpha 3 would not run the check for defects at all. It just loaded the live desktop instead. The md5sum is correct and I downloaded it from the Kubuntu site several hours after it was released. 
The installer runs ok up to about 68% then crashes, giving a "Sorry, but the installer has crashed" and giving details regarding bug reporting.
On the third installation attempt it completely wrecked grub, so had to purge/re-install grub from the live cd.
I have tried it since on usb rather than cd but the same thing happens (without the grub problem).

---

### Post by VMC on 2011-03-04
> **Quackers said:**
> This is the output
```
nattyalpha@nattyalpha-VGN-AR51SU:~$ cd ~/Desktop
nattyalpha@nattyalpha-VGN-AR51SU:~/Desktop$ sum natty-desktop-amd64.iso
09628 705304
nattyalpha@nattyalpha-VGN-AR51SU:~/Desktop$ 

```

I no longer have Alpha3, but using todays, Mar4th, ISO, here's what I got:

```
$ sum '/media/NTFS/natty-desktop-amd64.iso' 
54759 697776

```

---

### Post by Quackers on 2011-03-04
My version was Kubuntu, is yours?

---

### Post by VMC on 2011-03-04
> **Quackers said:**
> My version was Kubuntu, is yours?

No. Mine is Ubuntu.

---

### Post by Quackers on 2011-03-04
I already have several Ubuntu Nattys so I decided to give Kubunu a3 a try. It seems to have been a waste of effort :-)

---

### Post by VinDSL on 2011-03-05
> **VastOne said:**
> I can officially state that I have seen your Conky screenshots 1100 more times than I have had a "flaky" http file transfer issue... :P
I don't mean to belabor the point, but it's an important one.

All transfer protocols have error **[COLOR="Red"]detection[/COLOR]**, but few have error **[COLOR="red"]correction[/COLOR]**.

That's the beauty of FTP - it contains both error detection & error correction, and it's the main reason it's been around so long.  ;)

HTTP has error detection, but leaves error correction up to the user, thus the *need* for a download manager, when making large HTTP file transfers.


As for the veiled insult (ahem), I like to employ pics.  Why?

[LIST]
[*]A pic is worth 1000 words, and ppl will not read 1000 words.
[*]Talk is cheap!  Most ppl won't believe you, unless you *show* them. 
[*]Pics rule, and text drools!  Videos are even better, but you cannot embed them here.
[/LIST]

Anyway, to exemplify the situation at hand...

I downloaded the Alpha 3 file using the latest stable Google Chrome browser -- no DM -- straight up HTTP transfer, e.g. no error correction.

Here is the result:


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-5-mar-2011(1)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-5-mar-2011(1).png")[/INDENT]


As you can plainly *see*, the ISO was corrupt.  Brasero is on a slow boat to failure.  

The resultant burn is a 'coaster', and I judge that many ppl are using these coasters to install Ubuntu et al.

I didn't feel like sitting around for a couple of hours,  waiting for Brasero to give it up, so I downloaded a new ISO using Firefox / DownThemAll.

Here is the result:


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-5-mar-2011(2)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-5-mar-2011(2).png")[/INDENT]


Bingo!  :D

Ok, I'm going to go install Alpha 3 now.

Wish me luck, bro...

---

### Post by VastOne on 2011-03-05
> **VinDSL said:**
> I don't mean to belabor the point, but it's an important one.

All transfer protocols have error **[COLOR="Red"]detection[/COLOR]**, but few have error **[COLOR="red"]correction[/COLOR]**.

That's the beauty of FTP - it contains both error detection & error correction, and it's the main reason it's been around so long.  ;)

HTTP has error detection, but leaves error correction up to the user, thus the *need* for a download manager, when making large HTTP file transfers.


As for the veiled insult (ahem), I like to employ pics.  Why?

[LIST]
[*]A pic is worth 1000 words, and ppl will not read 1000 words.
[*]Talk is cheap!  Most ppl won't believe you, unless you *show* them. 
[*]Pics rule, and text drools!  Videos are even better, but you cannot embed them here.
[/LIST]

Anyway, to exemplify the situation at hand...

I downloaded the Alpha 3 file using the latest stable Google Chrome browser -- no DM -- straight up HTTP transfer, e.g. no error correction.

Here is the result:




As you can plainly *see*, the ISO was corrupt.  Brasero is on a slow boat to failure.  

The resultant burn is a 'coaster', and I judge that many ppl are using these coasters to install Ubuntu et al.

I didn't feel like sitting around for a couple of hours,  waiting for Brasero to give it up, so I downloaded a new ISO using Firefox / DownThemAll.

Here is the result:



Bingo!  :D

Ok, I'm going to go install Alpha 3 now.

Wish me luck, bro...

Good Luck Bro...

1102 - :D (<--- Note this) 

Never knew fact to be a veiled insult!  

You like DtM, I get it ... and it is good advice.  I think there are/were several issues in this thread, for me, a bad ISO was not one of them.  

I have Alpha3 stable now and am impressed with the Original Ubuntu Desktop (Gnome) Outside of some strangeness with Compiz that I have since cleared up... I can safely say I am on a journey to Natty on all systems

I was at the point of switching to Xubuntu but am not happy with it's dependencies and lack of basics that I am used to in Gnome.

I have loaded and tested Unity and it is what it is, bland but doing what it designed to do.

Good Luck!

---

### Post by ronacc on 2011-03-05
I use Opera to dl large files via http very often and can count the # of corrupted flies I have gotten on the toes of one hand even if the d/l was interrupted and had to be resumed , on the other hand brasero has never been trustworthy for me , I use K3B and don't get coasters .

---

### Post by VinDSL on 2011-03-05
> **ronacc said:**
> I use Opera to dl large files via http very often and can count the # of corrupted flies...
If you'll notice in my top panel...

I'm running (in order) Opera, Firefox, Chrome, and Midori -- and I'm fully aware of all of their foibles.

I'm on a rock-solid 7GB connection, and used an HP DVD burner & HP discs, for the demo.

Brasero has always worked great, for me!

Believe me on this, the ISO was corrupt...  ;)

Latez!  I gotta go install A3.

---

### Post by ronacc on 2011-03-05
I don't question that the .iso was corrupt , I would not be so quick to assign the fault to HTTP . I'm glad that brasero is solid for you , it has been on some releases for me and I have been playing with it since before it was a default app . I always give it a few tries at various points in the dev cycle but I always install K3b as a backup . I gave it a chance last a couple of days ago burning a daily , it refused to even try , telling me I had only 21.8 mb available on a fresh cd , k3b burned the same cd with no complaints and no errors .

---

### Post by seeker5528 on 2011-03-05
> **VinDSL said:**
> All transfer protocols have error **[COLOR="Red"]detection[/COLOR]**, but few have error **[COLOR="red"]correction[/COLOR]**.

FTP doesn't have error correction as far as I can tell.

[http://www.ietf.org/rfc/rfc0959.txt](http://www.ietf.org/rfc/rfc0959.txt)

>  There is no provision for detecting bits lost or scrambled in data
      transfer; this level of error control is handled by the TCP.
      However, a restart procedure is provided to protect users from
      gross system failures (including failures of a host, an
      FTP-process, or the underlying network).

FTP programs may make better use of these functions in TCP than many programs using http, I think this is more the program than the protocol. Wget seems pretty reliable with http and there are a few different download managers you can get that will work with firefox (or other web browser of your choice) that prove more reliable for downloading than just clicking a link and letting the web browser download it.

On the other hand even when clicking links in the web browser and letting the browser download the file, it seems marginally more reliable from an FTP link than a http link, but for all I know that has more to do with the sender and the way they are set up than the protocol being used.

Any protocol is not going to be more reliable than the method used to verify the data. I've had downloads that passed the md5sum check that were no good, so while the expectation is high (with good reason) that passing the md5sum check means it is good, it's not an absolute guarantee.

Later, Seeker

---

### Post by VinDSL on 2011-03-05
> **seeker5528 said:**
> FTP doesn't have error correction as far as I can tell.

[http://www.ietf.org/rfc/rfc0959.txt](http://www.ietf.org/rfc/rfc0959.txt)

> There is no provision for detecting bits lost or scrambled in data
transfer; this level of error control is handled by the TCP.
However, a restart procedure is provided to protect users from
gross system failures (including failures of a host, an
FTP-process, or the underlying network). 


That's one of those cases where... you have to read between the lines.  ;)

FTP does not detect lost bits or scrambled data, per se.

The way FTP handles errors is by rolling back the transfer (the "restart procedure" referred to in your quote) to the last known good.

FTP will simply go back to a point (in the transfer) that it *knows* was good, and "restarts" the transfer from there.

The problem with this "level of error control" is, it ends up wasting a lot of time, going back and downloading a lot of unnecessary bits, e.g. it's slow to recover from errors.

It's sort of like FAX machines -- it's a old skool technology, but it's simple and it works.

HTTP transfers, without a download manager, is a crap shoot.  Every once in a while, you're gonna roll snake eyes...

"Do you feel lucky today?  Well, do you?" *~ Dirty Harry*  

LoL!  :D

---

### Post by VinDSL on 2011-03-05
> **VastOne said:**
> Good Luck Bro [...]
Thanks!  All went well...

WoW!  That installer is sooooooo slick now!

It even reinstalled a lot of my (officially supported) programs, from A2.

I had to wrestle with some of the repo keys, but other than that, everything is lovely!  :)

---

### Post by VastOne on 2011-03-05
> **VinDSL said:**
> Thanks!  All went well...

WoW!  That installer is sooooooo slick now!

It even reinstalled a lot of my (officially supported) programs, from A2.

I had to wrestle with some of the repo keys, but other than that, everything is lovely!  :)

Great to hear... Keep me posted on any quirks or successes

---

### Post by Quackers on 2011-03-06
Brasero has produced many coasters for me in both Maverick and Natty. Conversely, my Lucid version of Brasero has been 100% reliable. Very strange.

---

### Post by cariboo on 2011-03-06
I haven't had a problem with brasero for several releases, I like the fact that it checks the iso's md5sum before and after the burn to make sure the burn is good. I've taken to using CDR/Ws since blank CDRs are getting hard to come by here. So far during this testing cycle I've only managed to create one coaster, and that only lasted until I blanked the disk.

---

### Post by VinDSL on 2011-03-06
> **VastOne said:**
> Great to hear... Keep me posted on any quirks or successes
Wow!  Just WOW!  :D

Day n' night difference here!

I had to do some more cleanup in the repos.

First of all it was the missing keys.  Then, I had dupes in the sources.list.

I found a few regressions.  

Example: nVidia X Server Settings requires auth to save xorg.conf

... haven't seen that one for a while.

Too much to list here, but basically I'm giddy as a schoolgirl!  A3 is working great for me!

LoL!  They're actually gonna pull off this Unity thing, aren't they?  :)

---

### Post by cariboo on 2011-03-06
> **VinDSL said:**
> Wow!  Just WOW!  :D

Day n' night difference here!

I had to do some more cleanup in the repos.

First of all it was the missing keys.  Then, I had dupes in the sources.list.

I found a few regressions.  

Example: nVidia X Server Settings requires auth to save xorg.conf

... haven't seen that one for a while.

Too much to list here, but basically I'm giddy as a schoolgirl!  A3 is working great for me!

LoL!  They're actually gonna pull off this Unity thing, aren't they?  :)

Needing authorization to write changes to /etc/X11/xorg,conf started in Lucid, before that, you had to run nVidia X  Server Settings as root in order to change and save your settings.

I never had a doubt about Unity, I'm curious to see what they come up with for it at UDS-O.

---

### Post by VinDSL on 2011-03-06
> **cariboo907 said:**
> Needing authorization to write changes to /etc/X11/xorg,conf started in Lucid, before that, you had to run nVidia X  Server Settings as root in order to change and save your settings.[...]
Yeah, you're right!  You just need elevated privileges now, like everything else.  

Before you had to start the proggie with gksudo or whatever.

As an aside, I noticed that I can't specify ntp servers, in "Time & Date Settings" (indicator-datetime-preferences).  The option is ghosted out.

Hrm...

I wonder if I need to install the ntp daemon first?!?!?  

Think I'll try that, after I submit this reply.

It used to be, when you choose the option, it installed the daemon...

**EDIT**

Yep, that did the trick!

I installed ntp & ntpdate, and the setting automatically enabled itself.

It appears that you can't select the ntp server(s) now.

Maybe I can do that via rdate...  ;)

---

### Post by ikt on 2011-03-06
> **Quackers said:**
>  I have a new coaster anyway :wink:

Should use a USB drive, much easier, and no coasters.

---

### Post by VinDSL on 2011-03-06
> **ikt said:**
> Should use a USB drive, much easier, and no coasters.
Heh!  I don't trust thumb drives.  :D

A couple dozen programmers wearing flip-flops and drinking Red Bull can do a lot of damage with those little suckers!

That's how Stuxnet spread around the world...

---

### Post by ikt on 2011-03-06
> **VinDSL said:**
> Heh!  I don't trust thumb drives.  :D

A couple dozen programmers wearing flip-flops and drinking Red Bull can do a lot of damage with those little suckers!

That's how Stuxnet spread around the world...

Start up disk creator allows you to format the drive first.

---

### Post by jerrylamos on 2011-03-06
> **ikt said:**
> Should use a USB drive, much easier, and no coasters.
USB stick is fine for install.

USB hard drive runs Natty quite happily on this netbook Acer Aspire.  It's a left over laptop 40 GB drive in a inexpensive USB case, with three partitions - Maverick, Natty, and Archive to store stuff when I do new installs.

The USB stick installs Natty onto one of the USB hard drive partitions.

O.K., why not just use a partition on the Aspire's 250 GB drive?  I've got it split between Maverick and Windoze 7 now.

Alpha's and Beta's and even RC's are infamous for fowling up things like partition tables and booting and grub and I don't want to mess around with the Windoze 7 boot.  Take a look at the Ubuntu forums for lots of tales of woe.  Aspire Windoze 7 has a nice Skype webcam setup already installed and running for example.

Oh, why Maverick on  the USB hard drive?  When I do a Natty install the resulting Natty grub boot choices are all fowled up and unintelligible to mere mortals.  So after the Natty install really messes up grub, I do a Maverick update-grub, grub-install /dev/sda and everything is O.K.

Jerry

---

### Post by Quackers on 2011-03-06
> **ikt said:**
> Should use a USB drive, much easier, and no coasters.

Startup Disk Creator hasn't worked with a usb for me since Lucid!

---

### Post by jerrylamos on 2011-03-06
> **Quackers said:**
> Startup Disk Creator hasn't worked with a usb for me since Lucid!
Startup disk creator works for me on my desktop that will boot from USB.  I have tried to create USB startup on my older pc's that don't boot from USB and the resulting USB stick won't boot anywhere.

Jerry

---

