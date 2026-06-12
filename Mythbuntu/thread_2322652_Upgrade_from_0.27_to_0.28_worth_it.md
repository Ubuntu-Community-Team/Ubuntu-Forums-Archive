---
title: "Upgrade from 0.27 to 0.28 worth it?"
date: 2016-04-29
forum: Mythbuntu
---

### Post by mattlach on 2016-04-29
Hey all,

I've been so busy lately I didn't even notice 0.28 had launched.

I'm trying to figure out if upgrading to 0.28 is worth the risk of breaking something and having to spend days troubleshooting, or if I should just stay on 0.27.

My usage scenario:[list]
[*]Installed 14.04LTS + 0.27 off of Mythbuntu ISO about 2 years ago.
[*]I ONLY use mythtv as the backend.  I don't use the mythtv frontends anywhere
[*]MythTV is only used for recording, playback and LiveTV viewing of cable channels.
[*]My frontends are all Kodi-based using Janbar's MythTV plugin, and direct NFS mounts to my NAS for all other content.[/list]


From the release notes we have the following:

> 
Major UPnP overhaul The UPnP code has seen major changes, improved browsing modes, more metadata, artwork for all media, strict UPnP (2014) and DLNA compliance and support for additional UPnP features. (Note: Client support for additional metadata varies. Client behaviour depends on UPnP compliance.)

I'm not quite sure what UPnP does in this context.  As far as I was concerned this is a risky service that automatically opens ports / does port forwards on consumer routers.   What does it do as part of MythTV, and how (if at all) would it benefit me?

> 
The cardinput table is no longer used, data has moved to capturecard [3e8bd6b]


I don't have a clue how this might impact me.  it sounds like a database reorganization.  Does it make the system more reliable, or perform better?

> 
MythMusic now uses storage groups you just have to tell the master or a slave backend where your music is located and all frontends will have access to it (no need to mount it using NFS or Cifs).
MythMusic Lyrics View MythMusic can now search for the lyrics for the currently playing track.
Updated MythMusic Radio Stream List MythMusic now downloads from our server an updated list of over 31000 radio streams from all around the world.

I don't use mythmusic or local video content at all for that matter.  My MythTV setup is used only for live and PVR TV playback.  All other content is handled with NFS mounts to my NAS on my Kodi frontends.

> 
MythZoneMinder popup notifications on alarms Shows a live view of the alarmed camera in a popup window.
Replacement Gallery using MythUI & storage groups Backend manages images in Storage Group and supports multiple frontends/service clients

I have no idea what Mythzoneminder is or what cameras have to do with mythtv?

> 
Add VBox TV Gateway support [a3eb10d0] See VBox.


Vbox?

> 
Add H.265 (HEVC) and VP9 support.

Since all my local video content is handled separate from mythtv on the kodi frontend does this actually matter?   I'm fairly certain all of my TV channels are mpeg2.

> 
Using FFmpeg 3.0

I don't do transcodes on the backend, and I don't use the MythTV frontend, so does this impact me at all?




Are there any other features not listed here that might be of use to me?  Any significant stability/bug/performance improvements in 0.28 that might justify my upgrade?  Will 0.27 still receive security/stability updates?

I'm just looking for any reason I should risk pissing off everyone in the house when there is no TV or recordings after the upgrade inevitably breaks something I have to spend hours/days troubleshooting.

Appreciate any thoughts!

---

### Post by gottabefoss on 2016-04-29
I noticed several improvements when I upgraded from 27.6 to 28:

(1) recordings are now .ts files, which is "proper" given that HD recordings are TS streams. Other programs are happier when accessing these files.

(2) mythtvbackend is much better at detecting and labeling damaged recordings. inasmuch as my local PBS channel is somewhat flakey, it's a godsend, as mythtv automatically reschedules a rerecord for the late-night repeat, which it didn't before when I was running .27

(3) upgrading to 28 is required if you want to upgrade to 16.04 LTS

I run solely a kodi frontend as well.

---

### Post by mattlach on 2016-04-29
> **gottabefoss said:**
> I noticed several improvements when I upgraded from 27.6 to 28:

(1) recordings are now .ts files, which is "proper" given that HD recordings are TS streams. Other programs are happier when accessing these files.

(2) mythtvbackend is much better at detecting and labeling damaged recordings. inasmuch as my local PBS channel is somewhat flakey, it's a godsend, as mythtv automatically reschedules a rerecord for the late-night repeat, which it didn't before when I was running .27

(3) upgrading to 28 is required if you want to upgrade to 16.04 LTS

I run solely a kodi frontend as well.


Appreciate the input.

How did you do the upgrade?   Did you select the .28 repositories in the myth control center, upgrade using apt and then do-release-upgrade your distribution to 16.04?   Or did you do a clean install from the new ISO?

Did you experience any complications when importing your .27 database into .28?

Based on the release notes it looks like the .28 database is different than the .27 database.  I'm guessing this means that an upgrade to 0.28 is a one way street (in other words, you can't go back without restoring from an older 0.27 database, which will be missing the most recent recordings)

My install further complicates the process as I can't install directly from an ISO, as I am running mythbuntu inside an LXC container on my Proxmox server, and managing it using x2go for GUI based condiguration.   There doesn't seem to be an LXC template for 16.04 yet, and I'm not even sure if I can do-release-upgrade from inside a container without breaking it.  (I've never tried)

---

### Post by gottabefoss on 2016-04-29
Installation:

Backup database!

change repositories in mythbuntu-control-centre

sudo apt-get update && sudo apt-get dist-upgrade

run mythtv frontend once to upgrade the database to .28

--

No complications. everything ran smoothly

-- 

upgrading to 28 is a one-way street. you can't go back to 27

--

I am still running 14.04 LTS

---

### Post by mattlach on 2016-05-01
> **gottabefoss said:**
> 
run mythtv frontend once to upgrade the database to .28


Interesting.  The frontend is responsible for the database conversion, not the backend?

---

### Post by nmw01223 on 2016-05-02
I posted a similar question. My conclusion was - leave it for now.

The only real benefit I can see (for me) with 0.28 is support for the DVB/T2 delivery system on tuners with Si2168 chips, which effectively means HD on UK Freeview with those tuners (HDHomeRun tuners always were OK).

So since there seem - not surprisingly - to be teething problems, and 0.27 appears bulletproof at the moment, I'm going to wait. If you do upgrade, I'd recommend a full partition backup first. Then if necessary, you can totally revert to where you were.

I also use Kodi 100% as the front end.

---

### Post by mattlach on 2016-05-02
> **nmw01223 said:**
> I posted a similar question. My conclusion was - leave it for now.

The only real benefit I can see (for me) with 0.28 is support for the DVB/T2 delivery system on tuners with Si2168 chips, which effectively means HD on UK Freeview with those tuners (HDHomeRun tuners always were OK).

So since there seem - not surprisingly - to be teething problems, and 0.27 appears bulletproof at the moment, I'm going to wait. If you do upgrade, I'd recommend a full partition backup first. Then if necessary, you can totally revert to where you were.

I also use Kodi 100% as the front end.

I'm leaning the same way.   And yes, I agree.   Personally - considering how fragile the mythtv backend can be - I back up an image every time I even run an "apt-get upgrade" just in case.  Or I used to when I was running it in a VM.  I'd shut it down, make a copy of the drive image, and then do my updates.   Now that I am running it in an LXC container on top of a ZFS pool, I just snapshot the dataset it is in.  Much more convenient.

Anyway, meanwhile I am testing 0.28 on 16.04 in a different container.  Right now I am running into problems with a required package (avahi) not installing properly as posted [here](http://ubuntuforums.org/showthread.php?t=2322939), but this seems to be an LXC container compatibility issue.

---

### Post by nmw01223 on 2016-05-02
> **mattlach said:**
> I back up an image every time I even run an "apt-get upgrade" just in case.

So do I!

---

### Post by clueo8 on 2016-05-03
> **nmw01223 said:**
> So do I!

I got mine setup once a week to reboot itself, boot into a clonezilla iso, automatically back up the entire boot drive to separate hard drive, keeping just 2 weeks worth of backups and rolling off anything older... I can also do the opposite, which is to restore the latest image with no user input required.. It took awhile to perfect it, but I have it down to a science and it worked well when I had issues going from 0.27 to 0.28 recently... I created a blog post with the steps on how to implement this: [https://whatthefdidido.wordpress.com/2016/05/04/automated-clonezilla-backuprestore/]("https://whatthefdidido.wordpress.com/2016/05/04/automated-clonezilla-backuprestore/")

---

### Post by nmw01223 on 2016-05-06
> [COLOR=#000000]I created a blog post with the steps on how to implement this: [/COLOR][https://whatthefdidido.wordpress.com...backuprestore/]("https://whatthefdidido.wordpress.com/2016/05/04/automated-clonezilla-backuprestore/")
Very interesting.

---

### Post by mattlach on 2017-02-19
So, 

My backend is still humming along happily on .27.6 in 14.04.

HAs anything changed in the 10 or so months since my original question?

Is .28 over its teething issues?   Is an upgrade from .27.6 now recommended?

Appreciate the input,
Matt

---

### Post by nmw01223 on 2017-02-20
I am in the same situation. Having seen that MythBuntu has apparently died, and thinking how long it took me to get the whole thing to work, I don't think I want to touch it.

The only real issue I came across was it's inability to handle DVB/T2 multiplexes (ie mainly HD TV) as it did not use V5 of the Linux DVB library, but I got around that by using HDHomerun tuners. I think DVB/T2 support was going to be added to 0.27 at some point, but I don't think it ever was.

---

