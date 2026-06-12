---
title: "Problem Reading DVDs"
date: 2008-08-17
forum: Multimedia Software
---

### Post by tswann on 2008-08-17
Hello

I'm having a problem reading DVDs which other users seem to have also encountered.  On Totem Movie Player it says 'cannot read from resource' and VLC just closes and nothing else happens.  I've tried two other programmes with no luck.

I've read the other posts on this site and followed all the instructions which have helped other users exactly and I still have the same problem.

I hope someone can help with this.

Yours,

Thomas

---

### Post by cooke77 on 2008-08-17
I think you're going about it the wrong way...with Totem Player.
Opem 'File'...
See what it says.
I have used Totem, in my experimenting with Ubuntu.
Never had your problem.
It (Totem) played OK, for me.
KLC (in Kubuntu 8.04)...works in a similar manner.
All that is needed is...a bit patience, a good read (in opening everything up, to know what is there) before doing anything.
What do I know about Linux/Ubuntu/Kbuntu?
Nadda!
And, I've only been 'tinkering' with Linux....for a month.

---

### Post by GreenVoid on 2008-08-18
tswann: What kind of hardware do you have?

I have Lenovo 3000 N200 and I have the same problem.
I installed libdvdcss2, libdvdread, libdvdnav and still nothing. I even installed ubuntu-restricted-extras, too.
I tried kaffeine, xine, totem-xine, mplayer, vlc, but neither plays DVDs.

---

### Post by Rumel on 2008-08-18
Your best choice is Ogle.
```
sudo apt-get install ogle
```
It's dedicated for DVDS. I'm not sure though if it comes with libdvdcss2, libdvdnav, or libdvdread, so if Ubuntu just doesn't start playing it with Ogle install those and then it should work. Also Ogle is the only thing out there that can play DVD Menus.

---

### Post by GreenVoid on 2008-08-18
Unfortunately ogle doesn't do anything either, despite all the packages you mentioned are already installed.

---

### Post by JEDIDIAH on 2008-08-18
> **GreenVoid said:**
> tswann: What kind of hardware do you have?

I have Lenovo 3000 N200 and I have the same problem.
I installed libdvdcss2, libdvdread, libdvdnav and still nothing. I even installed ubuntu-restricted-extras, too.
I tried kaffeine, xine, totem-xine, mplayer, vlc, but neither plays DVDs.

Once you have all of the dvd libraries loaded including CSS, it should
be a non-issue. All the players use the same libs, so if there is a 
problem it would effect all of them (the downside of code reuse).

Particular DVD's can be a problem. If you've got a criterion DVD, I would
suggest starting with one of those. A homemade DVD might also be a good
test but those can be odd.

---

### Post by GreenVoid on 2008-08-18
JEDIDIAH:
I have Hardy on my desktop, too, with the same packages installed and there I could play Wire, both 2nd and 3rd series. On my laptop, I can't play either. That's what makes me really puzzled.

Is there some config thing with the laptop's dvdrom, maybe?

---

### Post by Julian David Pitt on 2008-08-18
Hi All
I have the same issue on my Thinkpad T23, namely I cannot play DVD's with any of the players available, including VLC, MPlayer, Ogle and Kaffeine. It seems to be a laptop issue as I do not have any issues with my desktop installation. Help !!

---

### Post by mc4man on 2008-08-18
You should double ck. if a region has been set on the drive (note it only has to be set **once**, don't change regions to match disks

See here for how to ck.
[http://ubuntuforums.org/showthread.php?p=5451540#post5451540](http://ubuntuforums.org/showthread.php?p=5451540#post5451540)

For laptops it's good to know model of drive
```
sudo lshw -C disk
```


If it's a **matshita drive** in most cases you can only play dvds from the **same region drive is set to**, no way around ( again in this case don't change regions to match disks, set or leave at region that matches most of your titles and that's the best you can do

If region has been set, and you can't playback in vlc with libdvdcss2 installed, then open vlc from the terminal, try a disk and post errors.

Sometimes it also is good to go into home dir., find .dvdcss folder (hidden) and shift+delete the folders inside

---

### Post by GreenVoid on 2008-08-19
Well, I **set the region code**, re-installed dvdcss, restarted the system and voila. DVDs play nice.

Thanks.

---

### Post by Julian David Pitt on 2008-08-19
I already have the region set to region 2 and though I can read DVD's the playback is awful, very blocky with a stuttering picture that alternates between the playback and multiple blocky colours, whichever player I use, Ogle included.

---

