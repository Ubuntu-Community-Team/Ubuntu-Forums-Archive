---
title: "Hello silence my old friend..."
date: 2006-09-02
forum: Multimedia &amp; Video
---

### Post by GuiGuy on 2006-09-02
I've been running Ubuntu fine for about a month now. Four days ago the sound stopped working. 

I've established the hardware (on the mobo) is fine- I have a swappable HDD that lets me boot into WinXP, which confirmed the sound is OK.

I feel like I have exhausted almost every thread, every post, every [guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide") on the subject with absolutely no luck. Worse,I can no longer play video clips as they lock up the application (kaffeine etc) or worse, the desktop (KDE). I suspect that's because the sound hardware/ configuration isn't doing what it's supposed to.

However, according to the steps set out in the [Comprehensive_Sound_Problems_Solutions_Guide]("http://www.ubuntuforums.org/showthread.php?t=205449") all should be well.

Anyway, I've now given up on trying to fix the sound "in situ" as it were.   Given that the sound was working and should be working I figure that at my level of frustration, limited knowledge and intolerance for non-gui interfaces :wink: a complete reinstall is in order.

Question- will the Ubuntu installer do a 'repair' or will it insist on wiping the partitions?

regards

---

### Post by Garyu on 2006-09-02
I tried once to install Ubuntu over a previous install without formatting. It didn't turn out very well. So I recommend you do a backup of your home directory ("cp -a /home/ /destination" or use tar) and do a complete reinstall with formatting. 

One thing to remember though if you use tar for backup (I found this out the hard way); if you backup to a FAT32 drive (dual boot windows, like I had) the FAT32 partition can't deal with files over 4gig... Files larger than that will simply be truncated and everything will be lost forever. So make sure you double-check that the backup was OK before you format everything.

Also, if you only copy files, make sure you use the "cp -a" or possibly the cpio command, or you will have monstrous problems trying to set ownership and user priviliges on all the files again.

But if you're going to setup your system from scratch anyway, why not make a separate /home partition? That way it is easier to format OS-partions in the future.

Good luck!

---

### Post by GuiGuy on 2006-09-03
> **Garyu said:**
> I tried once to install Ubuntu over a previous install without formatting. It didn't turn out very well. So I recommend you do a backup of your home directory ("cp -a /home/ /destination" or use tar) and do a complete reinstall with formatting. 

Thanks. That's essentially what I do. After some disasters I should not mention I have learnt to maintain backup images :biggrin: 

Anyway, after near a week of no sound, endless hours trying to sort it without joy, I rebooted yet again a few moments ago and, yes, the silence is gone. :twisted: 

Go figure :confused: . No, better not. Don't touch it....

regards

---

