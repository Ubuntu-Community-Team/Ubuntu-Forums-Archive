---
title: "Problem with disk mounting in Mythbuntu 10.04"
date: 2010-11-11
forum: Mythbuntu
---

### Post by anigodin on 2010-11-11
Hello,

I've been using Mythbuntu for a few years and a couple of weeks ago, after using the 8.04 LTS version (which worked fine!) I tried to upgrade the system and ended up braking it down so badly I had to re-install.

I installed Mythbuntu 10.10 first and no matter what I tried, I could not make the Myth fronthand to 'see' my media files.
The media is located on 3 HD:
1. 60 GB for music (internal)
2. 250 GB for TV shows (internal)
3. 1 TB for movies (External).

When I finished installing and pluged the external drive is, I saw in and could access is but when I tried to configure it as one of the media locations the frontjand just ignored it.. the same with the other two (which also did not apear in the file manager even though both where mounted..)

After 3 day I decided to try and go back one version and installed Mythbuntu 10.04.
The same problem here: only the External drive is visible but the other two are visible whth mount manager but not mounted. 
I tried a few times and nothing. I just cant get the system to read the disks and tell myth fronthand to read the movies.

What am I doing wrong? is it a permission problem?
I'll be grateful for a simple explanation..
A-1000 thanks in advance.

---

### Post by ian dobson on 2010-11-12
Hi,

Sorry if I'm being abit slow here, but do you have a separate frontend/backend? If you go to the terminal prompt any type
df

do you see the external drive.

What do you have on the external drive and how do you want to use it (MythVideo), if it's videos viewable in mythvideo have you done a scan for new media?

Regards
Ian Dobson

---

### Post by anigodin on 2010-11-12
> **ian dobson said:**
> Hi,

Sorry if I'm being abit slow here, but do you have a separate frontend/backend? If you go to the terminal prompt any type
df

do you see the external drive.

What do you have on the external drive and how do you want to use it (MythVideo), if it's videos viewable in mythvideo have you done a scan for new media?

Regards
Ian Dobson

Hmm.. I installed a Backhand/Fronthand system but I dont have a Backhand active, only Ftonthand.

When I plug the external drive I see it and can access it and the data. this drive contain movies.

I did not scan for new media.. I assumed that when I configure a drive as media source, the scan is automatic. in my old system, the 8.04, every time I added a movie all I needed to do was go one step up in the menus and the new movies was in the media list.
Anyway, eiter I'm going blind, or I just dont know where to look - I did not find anywhere a buttum called: scan for new media (or an option that does that).

---

### Post by ian dobson on 2010-11-13
Hi,

So scan for movies, you need to go to mythvideo then click on the info button (it's the I button on my remote) and then scan for new media.

Regards
Ian Dobson

---

### Post by anigodin on 2010-11-13
> **ian dobson said:**
> Hi,

So scan for movies, you need to go to mythvideo then click on the info button (it's the I button on my remote) and then scan for new media.

Regards
Ian Dobson

Eventually I figured it out.. :-) silly me.

---

