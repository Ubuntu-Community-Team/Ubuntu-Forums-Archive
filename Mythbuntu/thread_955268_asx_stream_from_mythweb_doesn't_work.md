---
title: "asx stream from mythweb doesn't work"
date: 2008-10-22
forum: Mythbuntu
---

### Post by ubnewbie2 on 2008-10-22
When I go to the mythweb recorded programs page, a click on the asx stream button for one of the programs, my desktop (ubuntu 8.04) offers to open it in media player (Totem), so I say yes.  Totem launches, then just sits there forever with  a black screen. It won't close either - I have to 'force quit' it.

The mythtv server and my ubuntu desktop are both on a 100Mb switch and can communicate. (I have nfs drives mapped between them, and I can download the show using the button just below the asx button in mythweb).

---

### Post by jaakan on 2008-10-22
what are the specs of your computers?

What kind of transfer rates are you getting across your network.

What format are you trying to stream? SD or HD
and whats the recording Size?  (file size and picture size)


I recorded 30-Minute Meals off the Food Network HD a well back
786 MB / SD / MPEG2

took about 5 to 10 seconds to start playing and only buffered once at the beginning.

than I just pick a show of the local CBS HD here that was a show in HD
6.7Gb / HD / MPEG2

took about 5 to 10 seconds to start playing and buffered every few seconds


my server : Q6600 Quadcore / 2Gb ram / HD tuner pci-e / 250Gb
-- local Playback : NV8400 / Digital Audio out
-- mythbunu 8.04.1

my client: Dell Vostro 1000 : AMD64x2 / 1Gb ram / G wireless
U 8.10 beta / ATI drivers non-open 

network Dlink 514+ : 10/100 + 802.11G

---

### Post by 4dognight on 2008-10-22
I too have had this problem. Windows MP doesnt work. I had to use VLC in windows to get it to work.
In firefox on linux, VLC prompts for authentication continuously, even though I know the user/password is correct.

---

### Post by newlinux on 2008-10-22
the aunthentication used by defualt with mythbuntu when you turn on password protection isn't yet supported in many media players. So that could be part of the problem.

---

### Post by 4dognight on 2008-10-22
so I need to uncheck the mythweb password setting in the Control center?

---

### Post by newlinux on 2008-10-22
> **4dognight said:**
> so I need to uncheck the mythweb password setting in the Control center?

yes that will help make more media players work with it. You could implement password protection using a different authentication method than the one used by MCC that will work with more players. I did this before I used mythbuntu but I'm don't know all the steps, but I did it based on google.

---

### Post by gfowler on 2008-10-22
> **ubnewbie2 said:**
> When I go to the mythweb recorded programs page, a click on the asx stream button for one of the programs, my desktop (ubuntu 8.04) offers to open it in media player (Totem), so I say yes.  Totem launches, then just sits there forever with  a black screen. It won't close either - I have to 'force quit' it.

The mythtv server and my ubuntu desktop are both on a 100Mb switch and can communicate. (I have nfs drives mapped between them, and I can download the show using the button just below the asx button in mythweb).

It worked once for me on a 1/2 hour movie, never since.  Instead of fighting the problem I mounted the samba share to my laptop and access the recording that way.  The titles are arcane machine names but I sort out the mpg files and use Totem to view them over my network.  Not the most elegant solution but functional.

Jerry

---

### Post by ubnewbie2 on 2008-10-22
Authentication sounds like it may be the problem. I'll try vlc, and look into the authentication thing.

---

### Post by newlinux on 2008-10-22
> **gfowler said:**
> It worked once for me on a 1/2 hour movie, never since.  Instead of fighting the problem I mounted the samba share to my laptop and access the recording that way.  The titles are arcane machine names but I sort out the mpg files and use Totem to view them over my network.  Not the most elegant solution but functional.

Jerry

You can use mythrename.pl (maybe setup a cron or a job to run after each recording) to change the names to something useful.

[http://www.mythtv.org/wiki/index.php/Mythrename.pl](http://www.mythtv.org/wiki/index.php/Mythrename.pl)

---

### Post by newlinux on 2008-10-22
> **ubnewbie2 said:**
> Authentication sounds like it may be the problem. I'll try vlc, and look into the authentication thing.


The last time I checked this, I found VLC in windows worked, but not the version that installs by default in ubuntu. I think they all worked with authentication turned off. I think there are a couple other posts here (or maybe some other forum, I get them confused) about the authentication issue that may have more info,

---

### Post by anonymousdog on 2008-10-22
I find the asx stream uses too many resources (bandwidth, and processing on the client box) to be useful for most applications.  So, I'll use this post as an opportunity to plug [my minor rewrite](http://ubuntuforums.org/showthread.php?t=922937) of the MythWeb MythStreamTV plugin which uses vlc on the MythWeb box to transcode recordings (not imported videos) on the fly so they are accessible over nearly any bandwidth and on nearly any client device.  There are a couple of caveats I cover in post linked above but nothing too restrictive.  The rewrite includes changes to make it work in the WAP MythWeb template too (so, think Slingbox substitute).

---

