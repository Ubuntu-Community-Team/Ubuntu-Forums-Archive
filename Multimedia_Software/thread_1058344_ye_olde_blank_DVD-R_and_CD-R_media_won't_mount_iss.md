---
title: "ye olde blank DVD-R and CD-R media won't mount issue"
date: 2009-02-02
forum: Multimedia Software
---

### Post by maclenin on 2009-02-02
Essentially, blank DVD-R (e.g. Verbatim) and blank CD-R (e.g. Philips) media will not mount when snapped into the...

*-cdrom
description: DVD-RAM writer
product: DVD-RAM UJ-842S
vendor: MATSHITA
physical id: 0.0.0
bus info: scsi@3:0.0.0
logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/dvd
logical name: /dev/dvdrw
logical name: /dev/scd0
logical name: /dev/sr0
version: 1.01
capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration: ansiversion=5 status=nodisc

...inside my hp6910p running 8.10 (2.6.27-11-generic).

With either a blank DVD-R or blank CD-R in the drive...

```
dmesg | tail
```

...reveals...

[  xxx.xxxxxx] cdrom: This disc doesn't have any tracks I recognize!
[  xxx.xxxxxx] end_request: I/O error, dev sr0, sector 0
[  xxx.xxxxxx] Buffer I/O error on device sr0, logical block 0
[  xxx.xxxxxx] end_request: I/O error, dev sr0, sector 0
[  xxx.xxxxxx] Buffer I/O error on device sr0, logical block 0

...any thoughts?

NB: I have no issues with pre-burned CDs and/or DVDs (commercial or otherwise) - they all mount properly.

It's the blanks that are at issue here.

Thanks for any suggestions!

---

### Post by lenzoid on 2009-02-02
Why would one want to mount an empty disc?

Can you burn CDs using K3B for example? I don't know much about the burnin process in linux. You want to burn from command line?

---

### Post by maclenin on 2009-02-04
**lenzoid:**

The key is that the machine needs to be able to first "see" (and then grab hold, or mount) the discs before it/software - via the command line or elsewhere - can burn anything to them....

Has anyone found a cure?

---

### Post by ohgodnotanother1 on 2009-02-04
Did this work before?

Since a blank CD and DVD has no filesystem or whatsoever when it's empty, I doubt that you will be able to mount it.

I think that's why it says:
> cdrom: This disc doesn't have any tracks I recognize!

---

### Post by markbuntu on 2009-02-04
Does the blank disk show up on your desktop?

---

### Post by redroad55 on 2009-02-04
just a thought..Is it possible that for example when you have a regional conflict with media recorded from a different region than what your player 's region is .. I don't know for example if media like from phillips ( a German company) has for example in its so called blank state , say 2 different forms european and US market .. Just a thought .. Where did you get the blanks from ? ..Best to you

---

### Post by maclenin on 2009-02-04
**folks!**

Thanks for the reflections - the issue is (as **markbuntu** mentions) that (the drive whirrs but) the media does not show up on the desktop.

---

### Post by mc4man on 2009-02-04
To d. check the media recognition, if the drive settles after inserting blank media then run the sudo lshw -C disk again.

If you see this, then no media has been found

> configuration: ansiversion=5 status=[COLOR="Red"]nodisc[/COLOR]

If it shows this, then the media has been recognized (whether it shows on desktop or not

> configuration: ansiversion=5 status=[COLOR="Red"]ready[/COLOR]

---

### Post by markbuntu on 2009-02-05
Many people have reported problems with memeorex dvd-r, they would not show up on the desktop as a blank dvd. TDK worked fine though and I have not heard of any problems with Verbatim. Maybe you should try a different dvd manufacturer or a different drive.

---

### Post by maclenin on 2009-03-02
Thanks, again, folks.

**mc4man**:

With reference to your "lshw" test, I ran it using both a blank cd-r and a blank dvd-r...

...with the blank disc in the drive I received the following...
> configuration: ansiversion=5 status=[COLOR="SeaGreen"]**ready**[/COLOR]

...with no disc in the drive I received the following...  
> configuration: ansiversion=5 status=[COLOR="SeaGreen"]**nodisc**[/COLOR]

...the question remains, however: how do I "access" (or mount) the blank disc so that I can burn to it?

Thanks for continued insights!

---

### Post by punx45 on 2009-03-02
well if you are looking to do it via the CLI, you dont mount the disc first, because as stated already, it doesnt really exist yet.   what you do is create an image with mkisofs, then burn it to the disc using cdrecord.(even if its a dvd)   just google linux burn cd or soemthing to that effect.   for GUI just use a utility like K3B

if you are expecting the blank disk to, like in windows and mac,  appear like an empty folder that you fill with files and then click a button to burn it, im not sure if gnome works that way.

---

### Post by maclenin on 2009-03-02
**punx45**:

Thanks for the reply! I think perhaps I need to clarify my situation - differently....

Back in my Feisty days, using the identical hardware I use now, I was able to:

1. Pop open my cd/dvd drive.
2. Clip in a blank cd-r.
3. Close the drive tray.
4. Wait for the whirring drive to settle.
5. Seconds later find a "blank disc icon" on my xubuntu desktop.
6. Use xfce-burn to add media to the blank cd-r.

Steps 5. and 6. are not happening in Intrepid.

Any thoughts?

---

### Post by punx45 on 2009-03-03
is it safe to assume that you are still using XFCE?

---

### Post by maclenin on 2009-03-03
Yep. I am using XFCE in Intrepid and was using the same (XFCE) in Feisty.

However, for disc-burning in Intrepid I have Brasero rather than xfce-burn as my current option....

---

### Post by markbuntu on 2009-03-03
Are you sure your user has the proper permissions?

---

### Post by maclenin on 2009-03-05
All seems to be in order regarding permissions - e.g. 24(cdrom) - is there something specific re: permissions for which I should be on the lookout?

Thanks for the help.

---

### Post by maclenin on 2009-03-12
Sorry, y'all (and thank you) - twas a much much much simpler solution than I had (obviously) ever imagined:

Here are the steps I followed:

1. Navigate to...
```
Applications/Settings/Settings Manager/Removable Drives and Media 
```
2. ...then select...
```
Burn a CD or DVD when a blank disc is inserted
```
...from under...
```
Blank CDs and DVDs

```
3. ...and we're done!

Thanks, again, all, for trying the learn me!

---

