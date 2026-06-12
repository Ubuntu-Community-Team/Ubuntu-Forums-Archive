---
title: "rip dvd isos from dvds"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by yon2501 on 2007-12-31
ok so a while back i had a dvd and was able to rip it no problem with just copying the dvd to the harddrive by right clicking but that was with an older dvd and i just bought a dvd and i cant seem to rip it when i do it says it finishes up but the is simply wont open. im thinking that theres some new security software the prevents the rip from working right. so whats a good way to bypass this or a program that rips the is and not just the video files from the iso?

---

### Post by markharding557 on 2007-12-31
there is a cmdline program called dvdbackup in the repositories which works well or if you prefer a gui you could try k9copy.
with dvdbackup you will need to convert to iso with a different utility.
k9copy will create iso as well.
for either method you will need libdecss installed(from mediubuntu repository)to decrypt dvd discs.
i think libdecss may be illegal in the usa,maybe an american user can clarify

---

### Post by yon2501 on 2007-12-31
thanks ill try this out when i have a chance.

---

### Post by Spike-X on 2007-12-31
DVD95 is a DVD Shrink-like program that will rip a DVD to an .iso file, with the option of shrinking it down to fit on a single layer DVD.

---

### Post by yon2501 on 2008-01-01
ok just an update turns out i was missing the libdvdcss2 codec so it wasnt reading the disc properly still dont know why the other disc worked and not this new one but anyway problem solved. wasnt my method just a missing file :)

---

### Post by Spike-X on 2008-01-02
> **yon2501 said:**
> still dont know why the other disc worked and not this new one 

I'm guessing the other one wasn't copy protected. libdvdcss2 is only needed to read copy protected discs.

---

### Post by gupta_sumesh63 on 2008-01-02
Use commandline. Open a terminal and type this:
code:

> dd if=/dev/dvd_rom of=/home/yourname/Videos/Name.iso

Here if -s input file (remains like this only)
/dev/dvd_rom is the address or path to your DVD ROM/RAM.(depends on path on your computer)
of is output file.(remains like this only)
/home/yourname/..... is the path where you want to save the .iso.(depends on you)

Hope this does it.

---

### Post by gupta_sumesh63 on 2008-01-02
Use commandline. Open a terminal and type this:
code:

> dd if=/dev/dvd_rom of=/home/yourname/Videos/Name.iso

Here if is input file (remains like this only)
/dev/dvd_rom is the address or path to your DVD ROM/RAM.(depends on path on your computer)
of is output file.(remains like this only)
/home/yourname/..... is the path where you want to save the .iso.(depends on you)

Hope this does it.

---

