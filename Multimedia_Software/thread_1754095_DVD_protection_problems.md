---
title: "DVD protection problems"
date: 2011-05-09
forum: Multimedia Software
---

### Post by Seamyst on 2011-05-09
It looks like my laptop (Toshiba Satellite running Lucid) can't play protected DVDs. It will, of course, play other DVDs just fine. I tried regionset, but the drive doesn't even recognize that I inserted a disc (currently using a Netflixed Avatar as my testing DVD). Libdvdread is installed, as is libdvdcss.

Help?

---

### Post by K_45 on 2011-05-09
Does VLC play it? You can try cracking the encryption with k9copy if that will not do it.

---

### Post by Seamyst on 2011-05-09
> **K_45 said:**
> Does VLC play it? You can try cracking the encryption with k9copy if that will not do it.

VLC doesn't play it, and k9copy can't even read the disc. As I said, nothing on my computer will recognize that there's a disc in the drive. (But it's not my drive that's having problems, as it recognizes and plays other DVDs, and my work computer - running Windows 7 - acknowledges that I put the DVD in, but says there's digital copy protection and can't play it without some sort of driver.) It's *possible* that the disc is bad, but this is the second Avatar DVD I've tried, plus two DVDs of the first disc of Firefly, that all had the same problem. (None of the discs looked severely scratched or marked, either.)

---

### Post by K_45 on 2011-05-09
According to this:

[http://www.moviecodec.com/video-codecs/netflix-dvd-movies-will-not-play-49821/](http://www.moviecodec.com/video-codecs/netflix-dvd-movies-will-not-play-49821/)

Its the DRM. Does a regular DVD player work?

---

### Post by Seamyst on 2011-05-09
> **K_45 said:**
> According to this:

[http://www.moviecodec.com/video-codecs/netflix-dvd-movies-will-not-play-49821/](http://www.moviecodec.com/video-codecs/netflix-dvd-movies-will-not-play-49821/)

Its the DRM. Does a regular DVD player work?

Well, crap. That would make sense, as Avatar was released on DVD last year; and Firefly, while a few years older, is popular enough that it might well have DRM protection. Does that apply to movies you purchase yourself (like, say, I want to buy Firefly from Target), or is it only Netflix's DVDs?

And I don't have access to a regular DVD player, so I can't say.

---

### Post by K_45 on 2011-05-09
Netflix and other online services. The one you buy has protection which you can crack. This is why I'll never use these useless services.

---

### Post by mc4man on 2011-05-09
Have never seen any commercial dvd in good physical condition that isn't mounted _due to_ css or any additional structure protection. ( avatar in R1 has no structure protection
This also applies to netfix dvd's

There have been a few threads  recently concerning some drives not mounting commercial dvd's, maybe yours has a similar issue (the drive

May be interesting to see what drive you have, listed under the *-cdrom section
(if running below do it w/ the avatar dvd in the drive
```
sudo lshw -C disk
```

As far as regionset - 
whether a drive has a region set or not shouldn't affect mounting the filesystem on, if you want to ck. if a region has been set then put any disk in the drive, doesn't matter what (cd, dvd, audio cd, blank disc, ect.
(only thing to keep in mind is sometime you need to point regionset to the device, use the /dev/link from the lshw command
regionset /dev/sr0 or regionset /dev/sr1 ect.

---

### Post by Buntumatic on 2011-05-09
Region can be set in drive hardware, in this case DVD will not be read if region does not match. Google will tell more about this, problem is very existent outside of region 1.

---

### Post by mc4man on 2011-05-09
> **Buntumatic said:**
> Region can be set in drive hardware, in this case DVD will not be read if region does not match. Google will tell more about this, problem is very existent outside of region 1.

That is only partially true - 
The vast majority of dvd drives don't enforce region coding and no open source, unlicensed player does
Many Matshita laptop drives do enforce regions, it that case if there is a region mismatch playback will not be allowed.

Otherwise region mismatches present no real issue - the one thing that does happen is libdvdcss will use a different cracking routine.
The can lead to a failure to get proper keys on small sample titlesets like some extras. The main movie titleset is normally not an issue.

There are structure protections that can affect playback and in some rare cases make it not possible. (and it is more likely that Regions 2 & 4 will get SP
But I doubt that is the case here

---

### Post by akand074 on 2011-05-09
You mean there are dvds that don't work even with ubuntu-restricted-extras and libdvdcss2 installed? :/ I suppose I don't watch directly from disks on my computer anyways...

---

### Post by Seamyst on 2011-05-15
> **mc4man said:**
> Have never seen any commercial dvd in good physical condition that isn't mounted _due to_ css or any additional structure protection. ( avatar in R1 has no structure protection
This also applies to netfix dvd's

There have been a few threads  recently concerning some drives not mounting commercial dvd's, maybe yours has a similar issue (the drive

May be interesting to see what drive you have, listed under the *-cdrom section
(if running below do it w/ the avatar dvd in the drive
```
sudo lshw -C disk
```


I'd already returned the Avatar disc, so here's the output with the first disc of Law & Order Season 14 in the drive:

> 
*-cdrom
       description: DVD-RAM writer
       product: CDDVDW TS-L633C
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TF20
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=busy
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb


At this point I'm thinking of dropping my Netflix subscription to the two-a-month plan and only using it for older movies.

---

### Post by mc4man on 2011-05-15
> configuration: ansiversion=5 status=[COLOR="Red"]busy[/COLOR]

That means the drive is currently trying to detect the disk (type & fs, if any
Why your drive can't is the question, it's not because of anything netflix has done or has be done to disks they buy (if a disk has been abused by renters then that could present issues for drives
I'm 99.99% sure if I had netfix send your current title it would be detected properly  and play, the .01% is for condition

On dvd_video media (udf), once it's detected and mounted then you'd see this - the blue is added with the current method of no fstab entry for cd/dvd drives
This would be seen whether the disk is in use (playing) or not.

> configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,dmode=500,iocharset=utf8 state=mounted [COLOR="Blue"]status=ready[/COLOR]

There are a number of similar threads where the ability to mount or access some or all comm. dvd's has been lost, some have found solutions, many haven't, maybe search them out
(by access I mean having the udf filesystem mounted is not a always a prerequesite to playback

---

### Post by Seamyst on 2011-05-16
> **mc4man said:**
> That means the drive is currently trying to detect the disk (type & fs, if any
Why your drive can't is the question, it's not because of anything netflix has done or has be done to disks they buy (if a disk has been abused by renters then that could present issues for drives
I'm 99.99% sure if I had netfix send your current title it would be detected properly  and play, the .01% is for condition

On dvd_video media (udf), once it's detected and mounted then you'd see this - the blue is added with the current method of no fstab entry for cd/dvd drives
This would be seen whether the disk is in use (playing) or not.



There are a number of similar threads where the ability to mount or access some or all comm. dvd's has been lost, some have found solutions, many haven't, maybe search them out
(by access I mean having the udf filesystem mounted is not a always a prerequesite to playback

What kills me is that I've played loads of Netflixed DVDs since I got this computer in November, plus a number of my own movies (plus, hell, two or three DVDs that my dad burned from VHS). And I also tried the Avatar DVD on my work computer (which is about a year old and runs Windows 7), and it came back with a digital copy protection error (wish I'd written it down). So my drive and/or computer isn't the problem, and given the number of discs I've tried with this same problem, it's highly unlikely that I'm receiving a bunch of bad discs in a row.

I've searched the forums here using a number of different search words/phrases; nearly all of the posters who received answers and posted back said that it was libdvdcss or libdvdread.

---

### Post by mc4man on 2011-05-16
Well we have 2 new releases here from netfix - they both play with no issue on 3 setups, 4 different drives. (Black Swan and Harry Potter
Just to see i'll send them back tomorrow and get Avatar and the first disc of Law & Order Season 14, should be here Weds.

If you wish i'll find some similar threads and link here later.

---

