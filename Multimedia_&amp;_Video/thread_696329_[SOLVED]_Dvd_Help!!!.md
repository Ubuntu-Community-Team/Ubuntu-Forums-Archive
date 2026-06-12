---
title: "[SOLVED] Dvd Help!!!"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by joegiampaoli on 2008-02-13
Just Installed new SATA DVD writer, enabled all codecs along with libdvdcss2 libdvdnav4 and the rest from medibuntu, I pop in a dvd movie (yes protected) and I still cant watch it, it will show me maybe first 5 secs of the film then it stops. Xine tells me I don't have permission, totem marks errors, VLC just stops. :confused::confused::confused:

Please help, what am I doing wrong????

Here's my specs

Ubuntu Feisty 32 bit
AMD Athlon64 3000
1GB RAM

---

### Post by ubuntu-freak on 2008-02-13
Check out part 3 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833), and paragraph 9 of the troubleshooting section if you still have problems. Make VLC default for DVDs too, has best menu support.
 
Nathan

---

### Post by joegiampaoli on 2008-02-13
Not working.....:mad:

I can't even rip a dvd it goes extremely slow.

Any other ideas?

Thx for help

---

### Post by ubuntu-freak on 2008-02-13
You did the whole build-essential, fakeroot etc in part 3? Do other DVDs work? Did you try part 1? Only some new DVDs should cause problems, and troubleshooting deals with that in paragraph 9.
 
Nathan

---

### Post by joegiampaoli on 2008-02-14
Yes, Idid it all, still no good. I don't understand what the heck is going on here I'm busting my head.

No DVD will play, period.:(

---

### Post by ubuntu-freak on 2008-02-14
Try this command which is slightly different;
 
**sudo /usr/share/doc/libdvdread3/examples/install-css.sh**
 
Nathan

---

### Post by joegiampaoli on 2008-02-14
I get this:

**sudo: /usr/share/doc/libdvdread3/examples/install-css.sh: command not found**

When I do:

**sudo /usr/share/doc/libdvdread3/install-css.sh**

I get this:

[B]Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178        33.19K/s             

23:38:23 (33.13 KB/s) - `/tmp/dvdcss-NZ8917/libdvdcss.deb' saved [25178/25178]

dpkg - warning: downgrading libdvdcss2 from 1.2.9-2medibuntu2+build1 to 1.2.5-1.
(Reading database ... 210076 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-2medibuntu2+build1 (using .../dvdcss-NZ8917/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...
[/B]

The update manager tells me to upgrade the same file, but I try without upgrading and DVD wont ply yet. Then upgrade again and nothing.

I really want to thank you this is so weird, every forum posts same thing and everyone has dvd playback working, and I just can't seem to make it run.

---

### Post by ubuntu-freak on 2008-02-14
I don't understand it. That command seemed to work fine. Have you tried with desktop effects switched off? System>Preferences>Appearance>Effects.
 
Nathan

---

### Post by joegiampaoli on 2008-02-14
My Desktop effects are always disabled.

I know this is absolutely crazy, I just cant find any info on google for this. It's like I'm the only one with this bug:-k

---

### Post by joegiampaoli on 2008-02-14
Maybe if I purge remove all my multimedia libs/codecs and reinstall?

Which libs/codecs should I do?

---

### Post by bodycoach2 on 2008-02-14
I've had this happen before. If no DVD will play, you can't rip, etc, try cleaning the laser lens. There are cleaner kits available for pretty cheap.

---

### Post by joegiampaoli on 2008-02-14
Hmmm this is a brand new drive, I don't think that's the problem.

---

### Post by joegiampaoli on 2008-02-14
:lolflag::guitar::popcorn::popcorn::popcorn:

I didn't let it do the sudo /usr/share/doc/libdvdread3/install-css.sh

Left latest version, somehow that downgrades to another one

Turned PC off, changed SATA cable to SATA2 (it was on SATA1), maybe too much dust?

Rebooted, inserted a DVD and now it plays and rips fine.

THX for your help anyway, this was frustrating but I knew something was not normal.

---

### Post by ubuntu-freak on 2008-02-14
Hey great! I was asleep that's why I didn't reply. I've noticed that it downgrades and re-upgrades libdvdcss2, but the Ubuntu wiki recommends it and it's helped a lot of people.
 
Good job anyway,
 
Nathan

---

### Post by joegiampaoli on 2008-02-14
Yeah I know all wikis and pages I've seen say the same thing but the new libdvdcss2 also belongs to the medibuntu repository, so I guess its just a new version of that lib. So I'll just leave it as it is now, still works fine.

Thanks for your help anyway.

---

