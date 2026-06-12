---
title: "Ubuntu 11.04 alpha 2 does not work on my AMD computer"
date: 2011-02-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by SuperUserDO on 2011-02-06
I can't try Ubuntu 11.04 via live cd on my amd computer,i just get this screen in the attachments and nothing happen and i must restart the computer.but i tried it on my Intel computer and it worked.so what is the problem?:(

---

### Post by dino99 on 2011-02-06
your sreenshot is what we is called a kernel panic.

 On the boot line (hold "shift" key down at end of bios process to see grub menu, or alt+F6 or F6 when installing to remove "quiet splash" and/or add nomodeset noacpi, then ctrl+x to boot

---

### Post by Roosje on 2011-02-07
> **SuperUserDO said:**
> I can't try Ubuntu 11.04 via live cd on my amd computer,i just get this screen in the attachments and nothing happen and i must restart the computer.but i tried it on my Intel computer and it worked.so what is the problem?:(
I have the same problem over here, my HTPC who is still on Karmic because Lucid and Maverick still crash randomly on this 4 core AMD machine, shows the exact same screen when i try to boot 11.04, while my main I7 920 Computer, the rather irritating Toshiba laptop (noacpi) and an ancient HP laptop run it without (much, hey it is Alpha) troubles. What's up here, do they only support Intel from now on? I feel rather unsettled. Why the Toshiba ACPI support is not there is frelling, but understandable. But why would a Desktop PC that had ACPI support until Lucid now loose that? Are we now doomed to use Intel only with Ubuntu?
I have waited for a year now to let them find a fix for the random slowdown/crash/keyboard/mouse not working pileup, and see no positive development, in stead AMD is now seemingly thrown aside as viable  CPU option. I must say i am really disappointed!

---

### Post by SuperUserDO on 2011-02-07
I made acpi=off  and it worked well , much much faster than 10.10 :),but what does acpi=off mean? and is this problem because it is still an alpha release or  will i have to buy a new computer ? Thank You.

---

### Post by Roosje on 2011-02-07
> **SuperUserDO said:**
> [SIZE=3]I made acpi=off  and it worked well , much much faster than 10.10 :),but what does acpi=off mean? and is this problem because it is still an alpha release or  will i have to buy a new computer ? Thank You.
[/SIZE]
ACPI has something to do with powermanagement, Advanced Configuration and Power Interface, i think. I can not use that on my HTPC because that causes my CPU to stay on max all the time :-(
The WiKi says "defines platform-independent interfaces for hardware discovery, configuration, power management and monitoring" Pff yeah right..

---

### Post by rbrick49 on 2011-02-07
for me and me only I think these releases are coming out to soon alpha 1 dont release till tested for 3 months hardware is changing all the time,then when alpha 1 released let it go for testing. these people that are building these systems have to learn from nvidia and ati mr mark slow it down a little bit your developers must be getting tired. I love ubuntu and what it stands for but dont kill your developers or your system will die
I had a boss once that said there was a truck driver behind every tree his buisness went legs up guess why
regards Ronnie
ps Mark Shuttleworth if you want to contact me my email is <snip>
all the best folks

---

### Post by Roosje on 2011-02-07
I agree, what pulled me in on Ubuntu, the fast development, has become a hindrance. They have to break the huffing and puffing race to the not existing finish line, and take the time to fix the really big problems that are still floating around. I can only see the users thank Ubuntu for this, not complain.

---

### Post by vishalrao on 2011-02-07
I was facing similar issues - Ubuntu installed fine on my Intel desktop and AMD tablet but Kubuntu was panicking on my tablet while working fine on desktop.

A few lines above the end of the panic output there were SQUASHFS error lines so I thought - could this be a bad USB stick? Why was it working on my desktop?

I anyways recreated the USB image on to another stick and, lo and behold, no panics on my AMD laptop!

Installing Kubuntu natty alpha2 at the moment, want to try the alternate ISO too to see if BTRFS compression is any help on my SSD :D

---

### Post by teh603 on 2011-02-09
> **Roosje said:**
> ACPI has something to do with powermanagement, Advanced Configuration and Power Interface, i think. I can not use that on my HTPC because that causes my CPU to stay on max all the time :-(
The WiKi says "defines platform-independent interfaces for hardware discovery, configuration, power management and monitoring" Pff yeah right..Remember the SCI_EN bug on Arrandale-based computers? ACPI is more of a non-standard.

---

### Post by Roosje on 2011-02-10
> **teh603 said:**
> Remember the SCI_EN bug on Arrandale-based computers? ACPI is more of a non-standard.

That may be true but there is still the big question why it did work until Karmic (and even with keyboard/mouse crashes in Lucid and Maverick), and now suddenly gives a kernel panic :confused:
That points at a break somewhere, and seeing that even problems giving birth to more then 100 pages responses don't get fixed, i am starting to let my head hang in disappointment, and probably start looking at what can replace this :( 
Not that i want to, it feels to much like a pair of long loved shoes, they fit perfectly, but the soles are getting holes. Still took me over 6 month to throw those away :P

---

### Post by Roosje on 2011-03-07
Alpha 3 just booted of CD without a single problem? But now i have the 10.10 version finally working without trouble on my AMD machine, It initially hung short after installation, but after  reboot and a update it has behaved extremely well ;) Quite a release, dont wanne do the distro shuffle again :D Maybe i was to quick with blaming, have to keep in mind that it is a Alpha version, it is so stable on my main rig, i keep forgetting that..

---

### Post by Roosje on 2011-04-03
Arg, this drives me crazy! I had 10.10 problems with playing video (NVidia card) and the more i try to fix it the worse it became :( so i installed 11.04 (For some reason the latest nightly give me no problem accept for a warning about the temp. controller that is incompatible it claims).
It went all fine and played video like a charm, then i opened firefox, went to youtube and the whole system froze. That is to say the mouse pointer could move, but there was no response to any click, none whatsoever :(
A ctrl-alt-sysreq-b  made the system reboot (ctrl-alt-del did also nothing, just as ctrl-alt-F1 to check out what the problem was)
After the reboot (with diskcheck) the system froze while i just opened the Appearance menu.....

I have made a clean install (wiped all hidden folders in /home) in 11.04, did the same with going back to 10.10, it also crashes, but it takes more then a week and sometimes a month to choke.. 9.10 was the last stable release, but i am sick and tired of old software, and need a more recent version of things like Rhythmbox,  Libreoffice etc. It is just not working right.

Any suggestions? Any AMD users tried other distro's that are more up-to date then 9.10 and don't have problems with AMD systems?

The painfull thing is that all other systems i have around the house are Intel based, and they take (even the oldest, a rickety old laptop 1.2 Ghtz 512Mb mem) to 10.10 and 11.04 like fish to water. Maybe i should replace my lovely quad core AMD media-centre with a Intel one, sigh.

---

### Post by Roosje on 2011-04-05
Sigh, no respons.. A shame, hoped someone had a perfect solution ;) Silly me! I am back to Karmic Koala for my Media-Centre, all later versions keep crashing randomly :(

Guess i have no option but to replace the AMD stuff with Intell to get rid of this problem. Maybe a good idea to make a big announcement on the Ubuntu site for all after 9.10 versions, 'Will not run stable on AMD gear' Grr

---

### Post by Hakunka-Matata on 2011-04-05
> **Roosje said:**
> Sigh, no respons.. A shame, hoped someone had a perfect solution ;) Silly me! I am back to Karmic Koala for my Media-Centre, all later versions keep crashing randomly :(

Guess i have no option but to replace the AMD stuff with Intell to get rid of this problem. Maybe a good idea to make a big announcement on the Ubuntu site for all after 9.10 versions, 'Will not run stable on AMD gear' Grr

11.04 Alpha **WHAT? - .amd64, or the 32bit kernel, it makes a difference....**

I'm sorta in your camp, see signature for hardware.  I'm lovin 11.04.amd64, but now keep both amd.64 and the 32bit kernel in my Grub choices menu.  Seems VLC and some other medibuntu lovin apps are having trouble on 64bit kernel.  Well, not seems, it's plain and simple when I try to download libraries for medibuntu, the 64bit ones don't exist or fail during attempted download.

Is what I say m.o.m. in keeping with your experiences?

---

### Post by Roosje on 2011-04-05
> **Hakunka-Matata said:**
> 11.04 Alpha **WHAT .amd64, or the 32bit kernel, it makes a difference....**

I'm sorta in your camp, see signature for hardware.  I'm lovin 11.04.amd64, but now keep both amd.64 and the 32bit kernel in my Grub choices menu.  Seems VLC and some other medibuntu lovin apps are having trouble on 64bit kernel.  Well, not seems, it's plain and simple when I try to download libraries for medibuntu, the 64bit ones don't exist or fail during attempted download.

Is what I say m.o.m. in keeping with your experiences?

The AMD64 is the 64Bit version of the system for AMD and Intel, The 64Bit version/library has always been a distend and unloved cousin to the 32Bit version. But my troubles are more in the line of a probable BIOS incompatibility or some such. If you look around there is a very, very long thread (100+ pages) about crashes, hang-ups and whatnots attached to 10.4 and 10.10, those troubles seem to centre around AMD (CPU) systems, with possible relations to the number of cores. I have not seen a working fix for them, or a workaround that removes this thorn for me, and hoped that 11.xx would be the saviour of all those users that suffer these infernal crashes, but that is not the case. :(

---

