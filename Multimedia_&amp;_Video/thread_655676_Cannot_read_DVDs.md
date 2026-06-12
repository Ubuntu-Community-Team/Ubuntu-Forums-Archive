---
title: "Cannot read DVDs"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by DocForbin on 2008-01-01
For a while I've been having intermittent problems reading DVDs on my thinkpad t43, both in 7.04 and 7.10. In the past I could read DVDs again after a reboot. Now I can't at all. This happens with both blank and commercial DVDs. CDs work fine. I'm pretty clueless on troubleshooting hardware issues and would appreciate any advice.

---

### Post by DocForbin on 2008-01-01
bump

---

### Post by dsimpson on 2008-01-01
Scroll forward about 1 day to the post that says;[COLOR="Blue"] DVD not recognized[/COLOR], this is a post by me, and there are several suggestions that was made to help me with my dvd problems, non worked for me but you might find a solution there, good luck!

---

### Post by derek45 on 2008-01-02
this website worked for me, follow the steps...

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

### Post by DocForbin on 2008-01-02
> **dsimpson said:**
> Scroll forward about 1 day to the post that says;[COLOR="Blue"] DVD not recognized[/COLOR], this is a post by me, and there are several suggestions that was made to help me with my dvd problems, non worked for me but you might find a solution there, good luck!
Thanks for the help. I actually read that thread before posting and just went through it again.

This is interesting. I can read a DVD I burned a few weeks ago fine. But I still cannot read a blank DVD (tried several) or a commercial DVD (even one I have played before, btw).

---

### Post by DocForbin on 2008-01-02
> **derek45 said:**
> this website worked for me, follow the steps...

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

Thanks. libdvdread3 is installed and it has worked in the past. I will try installing VLC now.

---

### Post by DocForbin on 2008-01-02
I installed VLC and set it as default but no luck. When I put in Blade Runner: The Final Cut, the player churns for a while, then nothing. If I click on the drive in my computer I get "unable to mount media". And again a DVD I burned recently works fine. ugh

---

### Post by DocForbin on 2008-01-02
bump, still getting nowhere here

---

### Post by gmaniac on 2008-01-02
> **DocForbin said:**
> 
... In the past I could read DVDs again after a reboot. Now I can't at all..

Have you thought the possibility of a malfunctioning drive. If you put stress for the drive (i.e too many scratched dvds) you could wear it out.
One way (not an easy one) i could thing  of testing would be by installing another os :(. If it fails there then you have a problem.

But before all that, could you post the output of 
```
dmesg
```

---

### Post by DocForbin on 2008-01-02
Thanks for the help. I thought it may be a bad drive too, but if so it seems strange that CDs and DVDs I've burned continue to work 100% of the time ya know. Reinstalling the OS is something I'm strongly considering anyway as I've had various problems since upgrading to Gutsy, just not looking forward to it. Here's the dmesg output:

edit: That was long and probably not helpful, so I purged dmesg, and here is the output after trying to mount a commercial DVD:

[ 2886.896000] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[ 2886.896000] sr: Sense Key : Hardware Error [current] 
[ 2886.896000] sr: Add. Sense: Focus servo failure
[ 2886.908000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 2886.908000] sr: Sense Key : Hardware Error [current] 
[ 2886.908000] sr: Add. Sense: Focus servo failure
[ 2886.920000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 2886.920000] sr: Sense Key : Hardware Error [current] 
[ 2886.920000] sr: Add. Sense: Focus servo failure
[ 2888.920000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 2888.920000] sr: Sense Key : Hardware Error [current] 
[ 2888.920000] sr: Add. Sense: Focus servo failure
[ 2890.924000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 2890.924000] sr: Sense Key : Hardware Error [current] 
[ 2890.924000] sr: Add. Sense: Focus servo failure
[ 2892.920000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 2892.920000] sr: Sense Key : Hardware Error [current] 
[ 2892.920000] sr: Add. Sense: Focus servo failure
[ 2894.928000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 2894.928000] sr: Sense Key : Hardware Error [current] 
[ 2894.928000] sr: Add. Sense: Focus servo failure
[ 2896.928000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 2896.928000] sr: Sense Key : Hardware Error [current] 
[ 2896.928000] sr: Add. Sense: Focus servo failure
[ 2898.932000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 2898.932000] sr: Sense Key : Hardware Error [current] 
[ 2898.932000] sr: Add. Sense: Focus servo failure
[ 2900.928000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 2900.928000] sr: Sense Key : Hardware Error [current] 
[ 2900.928000] sr: Add. Sense: Focus servo failure
[ 2902.932000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 2902.932000] sr: Sense Key : Hardware Error [current] 
[ 2902.932000] sr: Add. Sense: Focus servo failure
[ 2904.932000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 2904.932000] sr: Sense Key : Hardware Error [current] 
[ 2904.932000] sr: Add. Sense: Focus servo failure
[ 2906.928000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 2906.928000] sr: Sense Key : Hardware Error [current] 
[ 2906.928000] sr: Add. Sense: Focus servo failure
[ 2908.932000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 2908.932000] sr: Sense Key : Hardware Error [current] 
[ 2908.932000] sr: Add. Sense: Focus servo failure

---

### Post by DocForbin on 2008-01-02
I purged dmesg again and loaded a burned DVD, which worked fine as it always done. Here is the output after that:

[ 3110.164000] UDF-fs: Partition marked readonly; forcing readonly mount
[ 3110.252000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'A_MAN_ESCAPED', timestamp 2007/11/02 20:27 (1e98)

---

### Post by gmaniac on 2008-01-02
> Sense: Focus servo failure

First link in google ...
[http://forums.afterdawn.com/thread_view.cfm/172293](http://forums.afterdawn.com/thread_view.cfm/172293)
You can search more...

PS I didn't say reinstalling though i said trying it in an other os like windows :(. I suggested that just to be sure that it isn't linux related.
bye

---

### Post by DocForbin on 2008-01-02
I don't have another OS installed or the free disk space to install one. Thanks for the link. I really think this is a software issue though since burned (and unencrypted) DVDs work perfectly.

---

### Post by gmaniac on 2008-01-02
When you said you had to reboot to make it mount and now it doesn't mount it seems like a situation going from bad to worst. This, at least for me, points me to hardware error. If you want to search at the software side then the kernel and the mount command are responsible for mounting.

Offtopic/
Since i like watching movies, A_MAN_ESCAPED seems an interesting film ,i will watch it . I have seen a godard film which i moderately liked, Alpaville.
thnx for the film;) and good luck.

---

### Post by DocForbin on 2008-01-02
It's a great film :)

Maybe it is hardware, just so weird that it would only affect commercial and blank DVDs. Can't find any firmware updates for the drive. I might try a cleaning kit. I'm making sure I have everything backed up at the moment and will probably do a clean install anyway. Major upgrades always seem a bit flaky and a few things have never worked right since the Gutsy upgrade.

---

### Post by DocForbin on 2008-01-02
Well I just finished a clean install of 7.10, and commercial DVDs appear to be working fine so far.

---

### Post by gmaniac on 2008-01-03
> **DocForbin said:**
> Well I just finished a clean install of 7.10, and commercial DVDs appear to be working fine so far.
nice to hear this :), and also strange :confused:. Maybe an update then messed it up for you..

---

