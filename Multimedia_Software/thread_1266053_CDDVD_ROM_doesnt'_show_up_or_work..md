---
title: "CD/DVD ROM doesnt' show up or work."
date: 2009-09-14
forum: Multimedia Software
---

### Post by sparker1 on 2009-09-14
I installed Ubuntu today and I have been impressed with it. The only problem (so far) is that I cannot get my DVD/CD Rom to work. It doesn't show up in "computer" and the few commands I have tried say that it "cannot be mounted".  The drive works fine in windows XP (dual boot system). the fstab has the following entry 

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

When I put the Ubuntu DVD in or any other DVD nothing happens. As I said there is no entry in "computer" for a CD/DVD rom.

I am a Ubuntu newbie. Any ideas?

[COLOR=Blue]Update: my burner is a [/COLOR][COLOR=Blue]HL-DT-ST DVD-RAM GSA-H55N; I have been over to CD Freaks and the specifications for this burner do not list Linux as a compatible operating system[/COLOR]. [COLOR=Black]I am hoping there is some workaround? Can anybody help?[/COLOR]

---

### Post by sparker1 on 2009-09-15
I fixed it! The problem was in the bios and the JB Micron Raid controller. It was set to Raid or Sata but needed to be set to IDE. Once that change was made Ubuntu found the dvd immediately.:P

---

