---
title: "Sound stopped working after update, cannot fix, getting desperate"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by cyrxi on 2007-04-22
The whole, long, story:

Back in November I installed Edgy on two laptops (mine and my girlfriends) and despite minor issues the sound has been working fairly well on both of them.  That is, until it "mysteriously" stopped working on my girlfriends computer sometime earlier this month (April 2007).  My guess is that it was caused by an update, so here is the history:

```

Commit Log for Sat Apr  7 11:40:18 2007

Upgraded the following packages:
kdelibs-data (4:3.5.5-0ubuntu3.2) to 4:3.5.5-0ubuntu3.3
kdelibs4c2a (4:3.5.5-0ubuntu3.2) to 4:3.5.5-0ubuntu3.3


Commit Log for Wed Apr 11 17:46:36 2007

Upgraded the following packages:
cdparanoia (3a9.8-13) to 3.10+debian~pre0-4build1~edgy1
desktop-file-utils (0.11-1ubuntu1) to 0.12-0ubuntu2~edgy1
gnucash (2.0.1-3ubuntu3) to 2.0.2-3ubuntu1~edgy1
gnucash-common (2.0.1-3ubuntu3) to 2.0.2-3ubuntu1~edgy1
libcdparanoia0 (3a9.8-13) to 3.10+debian~pre0-4build1~edgy1
linux-headers-2.6.17-11 (2.6.17.1-11.35) to 2.6.17.1-11.37
linux-headers-2.6.17-11-generic (2.6.17.1-11.35) to 2.6.17.1-11.37
linux-image-2.6.17-11-generic (2.6.17.1-11.35) to 2.6.17.1-11.37


Commit Log for Fri Apr 13 07:11:34 2007

Upgraded the following packages:
kdelibs-data (4:3.5.5-0ubuntu3.3) to 4:3.5.5-0ubuntu3.4
kdelibs4c2a (4:3.5.5-0ubuntu3.3) to 4:3.5.5-0ubuntu3.4
libqt3-mt (3:3.3.6-3ubuntu3) to 3:3.3.6-3ubuntu3.1

```

It was definitely broken after that.  My guess is that is broke when the kernel updated...

I have read numerous threads and tried a bunch of things including:
1)  Installing and booting from linux-image-2.6.17-50-generic (2.6.17.1-50.50) kernel
2)  Removing the following packages:
```
linux-generic
linux-image-2.6.17-11-generic
linux-image-generic
linux-restricted-modules-2.6.17-11-generic
linux-restricted-modules-generic
nvidia-glx
```
in order to remove and re-install ALSA (according to some thread that said this might help).
3)  various other commands/config edits that I cannot remember

So finally I decided to make sure that it wasn't some coincidence and my sound card just crapped out, so I went to boot from a livecd.  I couldn't find my original Edgy CD so I grabbed the Feisty 7.04 beta on 2007-04-14 (didn't realize the final release was coming so quickly).  Sound worked from the livecd, but I haven't had time to mess with it much since then.  

Today I noticed that Feisty was out of beta, and became very excited assuming the upgrade would fix the problem - I used the Upgrade feature in the update manager and 3 hours later I am running Feisty, but still have NO sound!  I'm growing increasingly frustrated and don't have as much time as I'd like to work on the issue.  My girlfriend keeps nagging me (rightly so, I wouldn't want to go without sound), and she's threatening to switch back to windows - hell I almost even suggested it so I could stop having to deal with this problem.  Please help!

Additional Notes:
The laptop is a Dell Inspiron 9300
lspci give me "00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)"

I have successfully hooked up an external sound card that produces some sound (though not from web pages, which seems to be a completely separate issue), but I'd rather fix the internal sound than work on debugging the external sound.

---

### Post by spin2cool on 2007-04-22
Try looking through this document:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by cyrxi on 2007-04-22
> **spin2cool said:**
> Try looking through this document:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

Thanks, but that is the main thread I followed when trying to fix my sound solution before - with no luck.  Just about the only thing on there I haven't tried is compiling the alsa drivers from scratch, which I will try if I can't find any other suggestions...

Here is some additional output that might help:  
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ lspci -v

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Dell Unknown device 0189
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at ed00 [size=256]
        I/O ports at ec40 [size=64]
        Memory at dffffe00 (32-bit, non-prefetchable) [size=512]
        Memory at dffffd00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```

---

### Post by spin2cool on 2007-04-22
How difficult would it be for you to install feisty from scratch?  if you have all your data on a seperate partition, you could probably get back up and running in an hour or two.  I had a computer with similar issues in the past, and a clean install fixed the problem when no other solution seemed to work.

I realize that it isn't ideal, but it may be one way to get your sound back.

---

### Post by cyrxi on 2007-04-22
> **spin2cool said:**
> How difficult would it be for you to install feisty from scratch?  if you have all your data on a seperate partition, you could probably get back up and running in an hour or two.  I had a computer with similar issues in the past, and a clean install fixed the problem when no other solution seemed to work.

I realize that it isn't ideal, but it may be one way to get your sound back.

Difficult.  Unfortunately I went with a friends recommendation to install everything "on one big partition" to minimize under-utilization of space.  His argument was "how often do you reinstall your operating system" - I should have realized that even though Linux is more stable than windows I'll probably still end up doing a fresh install about once every year, maybe two if I'm lucky.

Looking on the bright side, if it comes down to that this could be my justification for getting the external hard drive I've been itching for...

---

### Post by sav2005 on 2007-04-23
The problem is with cdparanoia. The last working version is cdaparanoia3a9.8-13. You will need to downgrade via synaptic's Package -> Force Version menu. When you have downgraded, lock the version (Synaptic Package -> Lock Version menu).

The whole sorry story is on this thread:  [http://ubuntuforums.org/showthread.php?t=407090&highlight=cdparanoia](http://ubuntuforums.org/showthread.php?t=407090&highlight=cdparanoia)

Laurie

---

### Post by cyrxi on 2007-04-24
> **sav2005 said:**
> The problem is with cdparanoia. The last working version is cdaparanoia3a9.8-13. You will need to downgrade via synaptic's Package -> Force Version menu. When you have downgraded, lock the version (Synaptic Package -> Lock Version menu).

The whole sorry story is on this thread:  [http://ubuntuforums.org/showthread.php?t=407090&highlight=cdparanoia](http://ubuntuforums.org/showthread.php?t=407090&highlight=cdparanoia)

Laurie

Thanks for the suggestion, but I don't think that cdparanoia has anything to do with my issue - the cdparanoia issue looks like it was localized to ripping programs, not all system sound.  Furthermore, I upgraded to Feisty which A) should have taken care of the problem and B) will not let me downgrade cdparanoia to even try it.

---

### Post by wesley_of_course on 2007-04-24
Good Evening  fellow nubee here and I had the same problem
      But the sound guide that is stickied worked for , however  found a thread , ( I staring at 15 updates myself ),
             so I bookmarked this one for when or if I need it afterwards. Haven't needed to try it but 
                         its one method I hadn't seen before now .  [http://ubuntuforums.org/showthread.php?t=418360](http://ubuntuforums.org/showthread.php?t=418360)

           Anyways Good Luck and let us know if it worked.

---

### Post by madscientist on 2007-04-24
I upgraded to Feisty today and my sound stopped working as well.  I rebooted and used my older Edgy kernel, and sound worked again.

I followed the note in this thread [http://ubuntuforums.org/showthread.php?t=414827](http://ubuntuforums.org/showthread.php?t=414827) and after modifying /etc/modprobe.d/alsa-base as described and rebooting, sound now works!

---

### Post by cyrxi on 2007-04-25
> **madscientist said:**
> I upgraded to Feisty today and my sound stopped working as well.  I rebooted and used my older Edgy kernel, and sound worked again.

I followed the note in this thread [http://ubuntuforums.org/showthread.php?t=414827](http://ubuntuforums.org/showthread.php?t=414827) and after modifying /etc/modprobe.d/alsa-base as described and rebooting, sound now works!

Thanks so much for the suggestion, but I tried it and it didn't work :(

---

