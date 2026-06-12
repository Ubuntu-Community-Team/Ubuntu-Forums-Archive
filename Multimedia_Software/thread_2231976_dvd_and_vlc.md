---
title: "dvd and vlc"
date: 2014-06-29
forum: Multimedia Software
---

### Post by maclenin on 2014-06-29
I am unable to play video from a DVD (via VLC) in 13.10 on a latest Acer Aspire laptop.

**Essentially:**

**1.** After inserting a DVD (which mounts automatically), I run vlc from the terminal (for debugging purposes)... 
```

vlc /dev/sr0

```

**2.** ...the DVD navigation menu appears in a vlc window...

**3.** ...and the following (error) messages are displayed in the terminal:

First...
```

VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b)
[0x8dd9908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.13 for DVD access

*** libdvdread: CHECK_VALUE failed in ifo_read.c:578 ***
*** for vmgi_mat->vmg_last_sector != 0 ***

*** libdvdread: CHECK_VALUE failed in ifo_read.c:580 ***
*** for vmgi_mat->vmgi_last_sector * 2 <= vmgi_mat->vmg_last_sector ***

*** libdvdread: CHECK_VALUE failed in ifo_read.c:581 ***
*** for vmgi_mat->vmgi_last_sector * 2 <= vmgi_mat->vmg_last_sector ***

*** libdvdread: CHECK_VALUE failed in ifo_read.c:594 ***
*** for vmgi_mat->vmgm_vobs == 0 || (vmgi_mat->vmgm_vobs > vmgi_mat->vmgi_last_sector && vmgi_mat->vmgm_vobs < vmgi_mat->vmg_last_sector) ***

libdvdnav: DVD Title: Untitled Project
libdvdnav: DVD Serial Number: 44b673f1        
libdvdnav: DVD Title (Alternative): Untitled Project
libdvdnav: Unable to find map file '/home/currentuser/.dvdnav/Untitled Project.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000127
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000064e3
libdvdread: Elapsed time 0
libdvdread: Found 0 VTS's
libdvdread: Elapsed time 0

```
..and 2 of these errors:
```

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1262 ***
*** for vts_ptt_srpt->title[i].ptt[j].pgcn != 0 ***

```
...and 15 of these errors:
```

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1673 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***

```
...and 1 more of this error:
```
*** libdvdread: CHECK_VALUE failed in ifo_read.c:1262 ***
*** for vts_ptt_srpt->title[i].ptt[j].pgcn != 0 ***

```
..and finally:
```

[0xb5300618] main input error: ES_OUT_RESET_PCR called
[0xb5300618] main input error: ES_OUT_RESET_PCR called
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"

```

**4.** When I then try to play video by selecting one of the "scenes" displayed in the DVD navigation menu, a "blank" screen (displaying the VLC cone) appears, no video plays and these 2 lines are appended to the previously iterated error messages:
```

[0xb5400618] main input error: ES_OUT_RESET_PCR called
[0xb5400618] main input error: ES_OUT_RESET_PCR called

```

**Notes:**

I have installed the most current "read", "nav", and "css" libraries as well as "ubuntu-restricted-extras".

The /usr/share/doc/libdvdread4/install-css.sh script has also been run....

This [discussion]("https://answers.launchpad.net/ubuntu/+question/242767") describes my predicament - fairly accurately, but does not offer a solution.

**Interesting aside?**

After inserting the DVD, if I run...
```

sudo regionset

```
...I receive the following:
```

regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.

```


Thanks for any suggestions.

---

### Post by coldraven on 2014-06-29
Try cleaning the lens. DVDs are very susceptible to dust and hairs that get in the tray. If you smoke it's even worse :(
I use a cotton bud and methylated spirits and **very gently stroke** the lens but even a bit of spit would work.

---

### Post by maclenin on 2014-06-29
Thanks for the reply / suggestion, **coldraven**! Lens looks whistle clean to me.... Besides, the lappy's not more than 3 months old and DVD drive almost never used - so, minimal opportunity for inflitration!

---

### Post by mc4man on 2014-06-29
Regarding regionset - 
no need for sudo
any disc will do
point to device

So try
```
regionset /dev/sr0
```

If you have a matshita dvd drive then a region must be set & you'll only be able to play dvd's from that region ( as far as commercial dvds
```
sudo lshw -C disk
``` would show

---

### Post by maclenin on 2014-06-29
Thanks, **mc4man**.

As far as regionset is concerned, it seems the device is an Hitachi (["HL-DT-ST"]("http://en.wikipedia.org/wiki/Hitachi-LG_Data_Storage")) and has no region, um...set, as yet*****....

A run of...```
regionset /dev/sr0
```...yields:
```

regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:

```
**NOTA BENE:** I AM able to play BOTH region 1 AND region 2 DVDs in the drive - as the drive is currently confirgured (see regionset settings, above).

**THE ISSUE, HOWEVER, ** (and focus of my original post) centers on a PARTICULAR DVD - which - according to this line...

```
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
```

...from section 3. of the OP shows a Region mask that appears fairly universal and might be, ironically, the source of the trouble - as it's expecting a number 1 through 8 and seeing nothing before the "," after "drive plays discs from region(s):"?

Thanks, again, for any thoughts!

*****Interesting whatnot re: [regionset]("http://mummila.net/nuudelisoppa/2013/05/10/example-run-of-regionset/")....

---

### Post by mc4man on 2014-06-29
With the exception of matshita drives,  in linux regions aren't enforced by players so usually not an issue
(it doesn't hurt though to set a drive to your main region.

It's also possible that the issue is with that particular dvd.
If it's a self made dvd then there could be an issue with the authoring or dvd disk condition
If it's a commercial dvd then it could have some structure protection that's causing vlc an issue.

In the later case sometimes opening the dvd without menus (dvdsimple) helps, in other cases you need to determine the actual real titleset for the main movie & have vlc open just that title #

---

### Post by maclenin on 2014-06-29
Thanks, **mc4man**, for sticking with this....

The dvd in question is of the "self made" variety (small, independent video producer) - so, I am thinking your suggestion to: "determine the actual real titleset for the main movie & have vlc open just that title #" might be the ticket - or at least a good place to start. Can you elaborate? What are the "action steps" to test your suggestion?

I also still harbor a hunch that if the dvd player had a region, um...set (to any number, 1-8) - the self made would play (given this line: **libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8**).... Does this strike you as a plausable assumption?

I appreciate the help!

---

### Post by coldraven on 2014-06-30
The reason that I recommended cleaning the lens was because I once had three DVDs that would not play. They were all brand new shop bought DVDs.
After messing around with software for a while with no results I cleaned the lens and two would play. But I had to clean the lens again to get the last one to play.
I guess that the lens had acquired an invisible film of tobacco smoke or perhaps a microscopic piece of crud on it. Certainly some DVDs are more temperamental than others.
Hope you manage to get it working.

---

### Post by maclenin on 2014-06-30
**coldraven!**

I hear you - thanks, again. I did get 2 dvds (from 2 different regions) to work with the **drive in question**, while watching the issue with the (brand new and squeaky clean) **dvd(s) in question** (multiple copies from the same producer) present similarly across several different machines / drives. So, all of this together reenforces my hunch that it's (probably) a software (regionset?) issue, rather than a tidiness one.... Yes, though, I am also all too familiar with having to clean up and off any number of dvds and drives - weilding all sorts of liquids, tools and hankies!

Thanks for the follow-up!

---

