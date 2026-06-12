---
title: "Regional DVDs"
date: 2009-07-11
forum: Multimedia Software
---

### Post by Speed8 on 2009-07-11
I live in Germany but came from the states. I brought my computer with me from the states as well as some dvds. Since then I have installed linux and played a couple German Region dvds. This is the first time im trying to play my american dvds and none of them are working with the same message saying that I cannot play this dvds region. Anyone have any ideas on what I should do? I am looking for a media player that will play from all regions. I currently am using Movie Player and/or VLC Player. I have also tried opening the dvds with Banshee and KMPlayer. Rather than downloading every media player i can find I was wondering if you all could help. 

[http://img18.imageshack.us/img18/9335/screenshotfon.png](http://img18.imageshack.us/img18/9335/screenshotfon.png)

---

### Post by SuperSonic4 on 2009-07-11
I recommend the regionset program that is in the repos, either search for *regionset* in Synaptic or paste the following into a terminal:

```
sudo apt-get install regionset
```

Once install open a terminal (if one is not open and type) ```
sudo regionset
``` and select your code (1 for the USA). Beware you may only do this so often

---

### Post by Speed8 on 2009-07-11
awesome thanks, took a restart to get it to work but now its just fine!

---

### Post by SuperSonic4 on 2009-07-11
No problem, just remember you may want to get a second dvd drive if you regularly watch both region 1 and 2 DVDs

---

### Post by bd10 on 2010-03-28
Dear all,

I wish to follow up on this post.

I am running Ubuntu 9.10 on my Sony laptop which I bought in the UK. I am running dual-boot with Ubuntu and Windows 7. I have not bought a commercial DVD player for 7, just running VLC on both OSs.

So far, I have exclusively played DVDs from region 2 on my laptop. Most surprisingly, it also played region 1 DVDs.

I installed regionset and am puzzled with the output (see below) I ran after watching DVDs from region 1:


me@me-laptop:~$ regionset /dev/dvd
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 2, mask=0xFD

Would you like to change the region setting of your drive? [y/n]:n


The vendor seems to allow for a max of 4 changes in region. It seems that the drive is set for region 2. Is the regional setting simply being ignored? Should the region not having been changed from 2 to 1, with the resets available dropping to 3?
If so, would this imply that regional setting would never become an issue, ie allowing to switch between regions without limitation? Am I mistaken?

Many thanks,

bd10

---

### Post by ron999 on 2010-03-28
Hi
Sometimes the DVDs are 'Region 0' so that they will play on any setting of DVD drive/player - even though on the sleeve it might still specify a particular region.

---

### Post by mc4man on 2010-03-28
> Is the regional setting simply being ignored?

Not exactly - open source (unlicensed) players don't enforce region coding so you can play disks from any region.
The only diff. when there is a region mismatch is that libdvdcss2 uses a different method to extract the keys which is generally successful. ( may occasionally fail on small titles like an extra

The exception is when one has a matshita drive - those drives do enforce region coding and there is nothing to be done there for matshita laptop drives other than change the region which has the obvious limitation of 5 total before the drive becomes locked.
( with the lone exception of 1 model used on mac's.

---

### Post by BicyclerBoy on 2011-01-07
have you installed ubuntu-restricted-extras ?

Have read the ubuntu website help regarding dvd playback ?
It really does explain all of this..

Do you have libdvdnav read css2 libraries installed from medibuntu ?

Some DVD optical drives need firmware "upgrades".
LG & Lite-on seem the best supported.

---

### Post by tikitikimaji on 2011-09-20
Does this change when you use a netbook?  I tried putting the "sudo regionset" but it says there is not a dvd in the drive (but there is).

---

### Post by mary.ydm on 2011-10-17
Hi Im having problems with the regionset the message I keep on getting is: Setting up amavisd-new-postfix (1:2.6.5-0ubuntu2) ...
postconf: warning: spf-policyd_time_limit: unknown parameter
Selected policy name, policy-spf, already in master.cf.                      Master.cf not updated.
Selected service name, smtp-amavis, or smtpd port, 10025,                     already in master.cf.  Master.cf not updated.
 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                         [ OK ] 
Stopping amavisd: (not running).
Starting amavisd: head: cannot open `/etc/mailname' for reading: No such file or directory
  The value of variable $myhostname is "mary-desktop", but should have been
  a fully qualified domain name; perhaps uname(3) did not provide such.
  You must explicitly assign a FQDN of this host to variable $myhostname
  in /etc/amavis/conf.d/05-node_id, or fix what uname(3) provides as a host's 
  network name!
(failed).
invoke-rc.d: initscript amavis, action "restart" failed.
dpkg: error processing amavisd-new-postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 amavisd-new-postfix

---

