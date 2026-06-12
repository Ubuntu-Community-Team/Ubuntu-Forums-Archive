---
title: "nvram wakeup repopulates"
date: 2013-02-17
forum: Mythbuntu
---

### Post by Red Bow Tie on 2013-02-17
Every time I blank the nvram-wakeup restart command which contained /sbin/grub-set-default 1) click finish, then recheck it either by re-entering mythwelcome or re-booting and checking mythwelcome the setting is back in there again. It doesn't matter how often I manually blank it it repopulates when I check. I do not need this setting as my mobo is quite recent.
I'm using ACPI wakeup and mythwelcome in Mythbuntu 12.04.2 x64.
How can I make this setting remain blank?

---

### Post by PhilWig on 2013-02-18
If it doesn't like a blank field, could you make it a comment with an initial #  ?
Phil

---

### Post by Red Bow Tie on 2013-02-18
I might add that I'm triple booting Mythbuntu with you know what. Mythbuntu is set as the default OS so that I can use ACPI wakeup. Would this have anything to do with it? Also I'm using a commercial program BootIt BM as the master bootloader. Grub is set to run from /sda1 the root partition. The Mythbuntu install cannot "see" the other OSes as it is configured only to "see" / /sdb1 (where I keep my recordings) and swap. It appears there are no ill effects as the machine comes on records and shuts down as it should.
Incidentally, I had to re-install Mythbuntu 11.10 x64 as I simply could not get 12.04.2 LTS x64 to work with ACPI wakeup despite having the same settings I had in 11.10. Countdown would occur only in 60 seconds intervals and when it got to 0 seconds it would simply start the countdown all over again infinitum. When I manually shutdown it would never wakeup.

---

### Post by *drew on 2013-02-18
I had the same problem with the nvram setting in mythwelcome.

I entered a single "space" character in the field and then saved the configuration.

That stuck, so I then edited it again, and this time I was able to delete the space, and re-save the configuration.

---

### Post by Red Bow Tie on 2013-02-18
I think it works. I've only tried it once, but I took PhilWigs suggestion and entered a # at the beginning of the line. Sorry drew I didn't receive your suggestion until after I tried PhilWigs. Anyway, after entering the # I clicked Finish, pressed F11 and there was the # at the beginning of the line. Making headway. So next I tried to delete the entire line EXCEPT the #, clicked on finish, pressed F11 sure enough now I just had a # on the line. Of course the next step was to try and remove the # leaving a blank line entirely. I clicked Finish pressed F11 and sure enough the entire line was now BLANK!!! There seems to be some kind of bug in that if you select the entire line and press delete it just repopulates itself after clicking Finish and pressing F11 to see the value return.
I'm sure drews suggestion would have worked as well. So if anyone is having trouble blanking the nvram wakeup line by doing as I did (highlighting the entire line and pressing delete) instead enter anything on the line, click Finish press F11, then blank whatever character you entered click Finish and press F11 to check it.
Thanks a ton to PhilWig and drew for pointing me in the right direction. With this line blank the box shut itself down as it's supposed to. I hope it keeps working on the next automatic startup. Keep you posted.
By the way the ACPI and even Mythwelcome documentation never mention what the setting should be for the "command to reboot computer" So, what should this be set to? sudo shutdown -r now?
I just might try going back to 12.04.2 x64 Mythbuntu and try it as it was preventing me from getting ACPI Wakeup to work in the same way.
Follow up:
It does indeed work. So if this happens to anyone running Mythbuntu with Mythwelcome and ACPI Wakeup here is the solution to the nvram setting repopulating.

---

### Post by PhilWig on 2013-02-20
Glad that worked.

My understanding was that nvram wakeup and acpi were totally different mechanisms and depended on which one your mobo supported.  Wiki is down just now so cannot check.
I have a vague recollection reading somewhere that some mobos needed some strange sequence like set wakeup time, then reboot, then closedown for the time to stick.  Hence the 'Command to reboot' option.

Guesses over now; hard fact.

With ACPI wakeup, Mythbuntu 12.04 on an Asus M3N78EM mobo (2009 vintage), I can confirm that my 'Command to reboot' in Mythwelcome / F11 is blank.

Phil

---

