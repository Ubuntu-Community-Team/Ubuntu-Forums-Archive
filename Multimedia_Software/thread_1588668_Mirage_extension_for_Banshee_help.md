---
title: "Mirage extension for Banshee help"
date: 2010-10-05
forum: Multimedia Software
---

### Post by fergiies on 2010-10-05
Hi all, 
I'm new to Ubuntu and Ubuntu forums, so please forgive me if this has been posted already.  Before I switched, the only music player I ever used was itunes, and I really miss the Genius feature.  Having done a bit of looking around, I downloaded Banshee.  the mirage feature, though installed, does not show up in Banshee.  Help?

---

### Post by Mike V on 2010-11-13
Did you find how to bring up the playlist generator? I could not find it and it seems that no one else has this problem.

---

### Post by cheezbergher on 2010-11-14
I've been having the same problem. I've never been able to get the Playlist Generator to show. Can anyone offer any advice for how to get this to work?

---

### Post by Cronos89 on 2010-11-14
I'm on your same situation. I've added the ppa for banshee so that i could get the latest stable releases of banshee and its extensions.

After a clean reinstall, i've activated Mirage. And the only change that happens is that Tools -> Mirage Playlist Generator appears. Other than that, there's no extra funcionality.

Currently Running Ubuntu 10.10

---

### Post by Cronos89 on 2010-11-22
*bump

---

### Post by Remmelas on 2010-12-09
I hate to 'me too', but, me too.  Installed the extension, but doesn't behave as specified by the developers site.  I have the option to 're-scan my collection', but no playlist generation abilities.

---

### Post by Ronqui on 2010-12-24
[FONT=Arial]This is somewhat tricky as Banshee is developing quite quickly these days.  The procedure may be different for older versions, but for version 1.8.0, here is the recipe:
[/FONT]
[LIST=1]
[*][FONT=Arial]First ensure that the Mirage plugin is enabled. Go to Edit -> Preferences -> Extensions -> Community Extensions -> Mirage Similarity Engine and make sure it is checked. If you don't have any Community Extensions, install[/FONT] [FONT=Courier New]banshee-extension-mirage [FONT=Arial]or[/FONT] banshee-community-extensions.[/FONT]
[*][FONT=Courier New][FONT=Arial]Now that you've enabled Mirage, tell it to scan your music collection using Tools -> Mirage Playlist Generator -> Rescan the Music Library. This will take sometime, and plenty of CPU, if you have a large collection.[/FONT][/FONT]
[*][FONT=Courier New][FONT=Arial]Mirage then enables a new play mode called "play by similarity". You can change the play mode by clicking on the small pulldown menu just to the right of the advance track (fast forward) button on the top right.[/FONT][/FONT]
[*][FONT=Courier New][FONT=Arial]OR Click on "Play Queue" on the Side Bar, and at the top right, select Fill "by similar". Drag a song to the Play Queue and enjoy![/FONT][/FONT]
[/LIST]
[FONT=Courier New][FONT=Arial]Once you've enabled Mirage, new additions will be automatically scanned once they've been imported into your library. Again, this will use some CPU time.

[/FONT][/FONT]

---

### Post by apsot on 2011-02-27
i just installed banshee 1.8.1 on 10.10 and in the beginning I thought that the only impact mirage had was for the button &#8220;Mirage Playlist Generator&#8221; to appear under tools. Then I discovered that in play queue I could select fill by similar which was not available without mirage.

---

### Post by jjb2011 on 2011-06-13
Wasted hours on Banshee 2.0 (11.04, 64-bit). I got it configured, the Mirage Playlist Generator shows, and occasionally it will actually add more artists/songs. Other times, nothing. Very buggy. 

But here's the thing: 

1. Similar doesn't work but 
2. Score does work

So when I enter Enya song, I get things like "Rage Against the Machine" and heavy metal. Say what?? 

On iTunes or Microsoft's Zune (similar "Genius" function), they pick things that are actually similar! 

Does it work on older versions but not the latest one? One of the deal breakers with Linux is the music player. None are really up to the big boys, primarily because of (and ony because of) no reliable "similar artists" feature. Gone are the days when people listen to a single album (and I'm 48 so those days are gone for me too!). 

Any alternatives that actually work? I keep trying, trying, trying players but . . . buggy at best and insane results (see above).

---

### Post by sonnenwende93 on 2011-06-13
I am having the same issue as jjb2011. I can rescan my music library, but it does nothing. No increase in cpu usage or anything, and going to fill by similar in the play queue fills in tracks automatically, but they are anything but similar. The extension seems to just do nothing.

---

### Post by FatherVic on 2011-06-28
Same problem here.  Running Ubuntu 11.04-32bit
Banshee 2.0
Mirage 2.0

Running Banshee with --debug from terminal.

When I clock on Tools > Mirage Playlist Generator > Rescan the Music Library

...Nothing.  No debug messages...  nothing.  It appears to not be working at all.  Frustrated to no end.  All searches end up like this thread - dead end.

---

### Post by xpawnrip on 2011-09-13
i have the same problem. can anyone fix it?:(

---

### Post by fly996 on 2012-09-01
> **FatherVic said:**
> Same problem here.  Running Ubuntu 11.04-32bit
Banshee 2.0
Mirage 2.0

Running Banshee with --debug from terminal.

When I clock on Tools > Mirage Playlist Generator > Rescan the Music Library

...Nothing.  No debug messages...  nothing.  It appears to not be working at all.  Frustrated to no end.  All searches end up like this thread - dead end.

same problem. I'm using Ubuntu 12.04 LTS and Banshee 2.4.1 

would really like to get this to work. any help would be very much appreciated

---

### Post by wildmanne39 on 2012-09-02
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

