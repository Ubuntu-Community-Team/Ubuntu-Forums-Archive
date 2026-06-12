---
title: "/etc/hdparm Doesn't Work!"
date: 2009-04-30
forum: Mythbuntu
---

### Post by tobiz on 2009-04-30
Mythbuntu 8.10. I've tried putting /dev/sdc {spindown_time = 60} in /etc/hdparm.conf and it has no effect after reboot, ie hdparm -C /dev/sdc always returns "idle/active". Running hdparm -S 60 /dev/sdc from the command line has the right result. Elsewhere it's suggested that the hdparm tuning service has to be enabled but no such service appears under "Services". Any ideas how to make this work welcome.

---

### Post by ian dobson on 2009-04-30
Hi,

hdparm -S30 /dev/sdc works for me. Maybe add it to /etc/rc.local so that it runs on every boot.

regards
Ian Dobson

---

### Post by tobiz on 2009-04-30
> **ian dobson said:**
> Hi,

hdparm -S30 /dev/sdc works for me. Maybe add it to /etc/rc.local so that it runs on every boot.

regards
Ian Dobson
 Hi,
Yes hdparm -S n /dev/sdc works for me too, ie it spins down the disc but if you do the equivalent in /etc/hdparm.conf it has no effect on boot.  The only way I've got it to have any effect is to sudo the command in an autostart script (v.ugly). Also if the disc is then spun up it never gets spun down unless the command is repeated, this is not what I want. I want the disc spun down all day, spun up to do the backup at 04:00 and then spun down - seemed simple at first!

---

### Post by ian dobson on 2009-05-01
Hi,

The command is hdparm -S30 /dev/sdc  without a space between S and the delay.

I think you only need to set it once and the drive remembers the value (My 1Tb Samsung seems to anyway).

Regards
Ian Dobson

---

### Post by tobiz on 2009-05-01
Ian Hi,
I'll try without the space but since the discs spin down with a space in the command when run from the command line that would be a very subtle (but not unknown type of) difference.

---

### Post by ian dobson on 2009-05-03
And........ did it work?

Regards
Ian Dobson

---

### Post by tobiz on 2009-05-03
> **ian dobson said:**
> And........ did it work?

Regards
Ian Dobson
Ian, sorry forgot to mention the all important bit! No it didn't. In fact for some reason I can't work out the discs don't spin down at all now on issuing any command.  Is this progress!

---

### Post by ian dobson on 2009-05-03
Hi,

Using hdparm -S30 /dev/sdc  will set the powerdown to 2minutes 30 seconds. The drive will only power down, when it's not used. On my server I used a 1Tb samsung drive for backup, so it was only mounted/used for about 15minutes per week.

If you umount (or unmount for those with a working n key :)) the drive should power down. I think if it's still mounted it won't power down, I'm not sure.

Maybe it's releated to this [http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/](http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/)

Regards
Ian Dobson

---

### Post by tobiz on 2009-05-03
Ian,

Seems we are both doing the same thing, ie use a disc for backup and when the backup is not taking place the disc is spun down. When I first tried hdparm from the command line the sdc disc did spin down after the specified time. The next thing was to run the hdparm command at boot. As far as I can see this should be done by setting  up /etc/hdparm.conf. There are two ways of doing this either by a stanza for the spindown time or a stanza to run an hdparm command, both should give the same result. For me neither produced any resut  ie after boot sdc did not spin down (note when I tried hdparm from the command line sdc was mounted). I then investigated ways of getting an hdparm command issued during the boot sequence and eventually added it to the autostart program list as a sudo script. I then noticed that after the disc had spun up after a spindown, ie after a overnight backup, it did not spindown again. I've found that someone has developed a spindown daemon which would probably fix my spindown after spin up problem but not the nicest solution. I'd anticipated hdparm would set a disc into a 'state' rather than a one off event per command. The really bad news is that I've changed something (probably when following the 'laptop power issue' since it seemed to be related,  eg /et/hdpar.conf not being used unless in 'laptop-mode') and hdparm when run from the command line, with or without a space between the -S and the time value, now has no efect what so ever. At the moment I'm completely stuck and until I can find out why  hdparm has no effect when run from the command line getting the disc into the required state at boot time will have to wait. One issue I have with the hdparm command is that it does not log anything as far as I can see which makes diagnosing any problems difficult.

---

### Post by tobiz on 2009-05-04
Ian,
Cracked it! After much googling I found that spindown time (-S) is affected by the Advanced Power Management facility (-B). For -Bn where n>128, spindown time is ignored. I found the disc had an APM value of 254 so set it to 127 and tried -S12, result spindown now works again. Well it works in that the disc spins down, need to check whether it spins down after spin up without having re-issued the command.

---

