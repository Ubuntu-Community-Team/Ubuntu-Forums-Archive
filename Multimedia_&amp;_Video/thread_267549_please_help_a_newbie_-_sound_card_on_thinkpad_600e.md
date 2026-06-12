---
title: "please help a newbie - sound card on thinkpad 600e"
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by tcturner2002 on 2006-09-28
Hi all,
I seem to have a common problem on Dapper: The volume control icon has a red muted symbol and when I click it I get this:
No volume control GStreamer plugins and/or devices found.
I've also gotten the longer message that says bascially the same thing.  I've searched for this online and here and I realize there are many pages written about it, but the problem is I'm new to Linux and can't understand any of it.  "Just add this to the GRUB menu.lst file and you're good to go!"  Or, you could use this command... or that... :confused: :confused: :confused: Anyway, I have close to no idea how any of this works and I don't want to mess with GRUB or the Terminal in case I do the wrong thing.  Could anyone explain this in (close to) plain English?  Thanks so much!
-Caleb

---

### Post by Kateikyoushi on 2006-09-28
Did you install ubuntu and have no sound ?

Then your sound card's dirver was not installed.

[This is what you need]("http://www.ubuntuforums.org/showthread.php?t=205449").
If the guide does not seem to help or is not clear just ask.

---

### Post by tcturner2002 on 2006-09-29
looks good, i'll try it tomorrow and let u know if it works.  thx

---

### Post by tcturner2002 on 2006-10-01
Kateikyoushi-
Thanks for your post.  As the guide suggested, I ran modprobe snd-cs46xx (that's my sound card, Cirrus Logic CrystalClear SoundFusion 4610/11) successfully (I think) and even added the name to etc/modules and restarted, but the sound card still doesn't work, same message as before.  I don't know what else to do, any ideas?  Thanks again!
C

---

### Post by Kateikyoushi on 2006-10-01
Does Ubuntu see your soundcard ?
Check it in System >> Administration >> Device manager.

---

### Post by tcturner2002 on 2006-10-04
Yes, it's there.  It sees it in lspci -v (looks like what it says in Device Manager), but aplay -l says "no soundcards" or something like that.

---

### Post by tcturner2002 on 2006-10-19
Anyone have any ideas?  Thanks!

---

### Post by tommcd on 2006-10-19
Found this by googleing 'linux sound ibm thinkpad 600' (without quotes).
[http://www.levien.com/tp600.html](http://www.levien.com/tp600.html)
scroll down the page for sound.
Also:
[http://jeremy.zawodny.com/misc/thinkpad-600e-sound.html](http://jeremy.zawodny.com/misc/thinkpad-600e-sound.html)
From an ubuntu-breezy thread:
[http://www.ubuntuforums.org/showthread.php?t=94414](http://www.ubuntuforums.org/showthread.php?t=94414)
It seems you need to edit /etc/conf.modules (make a backup copy of the file first). Hope this can help.
EDIT: I would try following the suggestion by grumpymole on the ubuntu thread first.

---

### Post by tcturner2002 on 2006-10-20
Hi tommcd thanks for your response!

Followed grumpymole's steps like this:

1. There is no etc/hotplug.  Instead I added these lines to etc/modprobe.d/blacklist:

blacklist snd-cs46xx
blacklist cs46xx

2. Added exactly these lines to etc/modprobe.d/alsa-base.
3. Added snd-cs4236 to etc/modules.
4. Rebooted with nothing extra in boot/grub/menu.lst
5. Disabled Quick Boot.
Still no sound, so added acpi=off pnpbois=off to the end of the 'kernel' line in GRUB.  No sound, and the following error messages (same as before I think):

modprobe snd-cs4236:

FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.15-23-386/kernel/sound/isa/cs423x/snd-cs4236.ko): Operation not permitted

alsamixer:

alsamixer: function snd_ctl_open failed for default: No such device

OK, now I'm following instructions from a different website that say to add these lines to etc/modprobe.conf.  Since that doesn't exist, I'm removing what was in etc/modprobe.d/alsa-base (as suggested by grumpymole) and putting them there:

options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
alias snd-card-0 snd-cs4236 (same as before but with much less extra stuff)

"You can test this immediately by doing: modprobe snd-cs4236"  Same message as before, but now I realize it looks like a permissions issue.  So I try sudo modprobe snd-cs4236 and get this:

Unknown parameter 'snd-card-0'
FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.15-23-386/kernel/sound/isa/cs423x/snd-cs4236.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Is that why it's not working?  I'm afraid I don't know what else to do, any ideas?  Thanks and sorry for the long post, just trying to give as much info as possible.  -CT

---

### Post by tommcd on 2006-10-21
This seems to be a tough one. There are numerous threads on thinkpad 600E in the forums. Some people got it to work, many did not. I saw this thread:
[http://www.ubuntux.org/please-help-no-sound-on-my-ibm-thinkpad-t43](http://www.ubuntux.org/please-help-no-sound-on-my-ibm-thinkpad-t43)
see the last post on that thread. Sorry to ask, but is there a button on your thinkpad that mutes the sound? If that is not muted I don't know what else to do. Perhaps some thinkpad owners could help out here.

---

### Post by tcturner2002 on 2006-10-21
Good idea, but it's not muted; the system beep still works and I can switch right over to Windows and get sound.  I'll look into it some more and let you what I find out. -C

---

### Post by tommcd on 2006-10-23
tcturner, have you seen this new thread:
[http://ubuntuforums.org/showthread.php?t=282624](http://ubuntuforums.org/showthread.php?t=282624)
This just may be the answer you (and many others) have been looking for! Let me know if it helps.

---

### Post by clembone on 2006-10-23
> **tcturner2002 said:**
> Good idea, but it's not muted; the system beep still works and I can switch right over to Windows and get sound.  I'll look into it some more and let you what I find out. -C

I just posted a fix for you. You will need to know how to use your terminal and VI though.

---

### Post by clembone on 2006-10-24
I have a post out there that fixes my 600e. :grin: I am able to duplicate the fix. I have tried to put it in a format that you will understand. You seemed a bit frustrated with all of the geek talk. Take a look at my post and let me know if you need clarification on any of the steps. Here is the link to my post.

[http://ubuntuforums.org/showthread.php?t=282624](http://ubuntuforums.org/showthread.php?t=282624)

---

### Post by tcturner2002 on 2006-10-24
AWESOME!!!!  IT WORKS!!!!

Thanks so much, it's perfect!  Seems funny since it was so close to the other suggestions that didn't work, but oh well.  That was what was frustrating to me, that everyone had a different idea of how to do it (and they all said their way worked!), but I guess the distribution/version made a difference too.

Thanks again!

---

### Post by clembone on 2006-10-24
Sweet!

---

