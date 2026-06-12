---
title: "asunder CD ripper not working after upgrading to Ubuntu 17"
date: 2017-12-14
forum: Multimedia Software
---

### Post by tmielke on 2017-12-14
Hello,

I have been running Ubuntu 14 for a long time but recently upgraded my old Dell XPS 16 to Ubuntu 17.
Since that upgrade the asunder CD ripper does not work anymore. 
Its able to read and lookup the CD content but when hitting the rip button it just hangs at 0% and the CD drive does not even start to spin.
This is irrespective of the actual CD, it happens with every CD.

Other applications like Rhythmbox have no problems accessing the CD drive and playing the same CD.
I configured asunder to log to /var/log/asunder.log but that log file does not get created.

In /var/log/system.log I get the following entries every time I hit the rip button in asunder:

Dec 14 20:38:37 XPS asunder: encode() waiting for 'barrier'
Dec 14 20:38:37 XPS asunder: encode() waiting for 'available'
Dec 14 20:38:37 XPS kernel: [ 1830.341488] audit: type=1400 audit(1513280317.781:110): apparmor="DENIED" operation="open" profile="snap.asunder-casept.asunder" name="/dev/sr0" pid=29696 comm="cdparanoia" requested_mask="w" denied_mask="w" fsuid=1000 ouid=0
Dec 14 20:38:37 XPS asunder: completed tracks 0, rip 0,00%; encoded tracks 0, mp3 0,00% ogg 0,00% opus 0,00% flac 0,00% wavpack 0,00% monkey 0,00% musepack 0,00% aac 0,00%


... and thought that apparmor may prevent access to the drive. So I stopped apparmor via sudo /etc/init.d/apparmor stop but that did not change anything. Am still getting above logging when trying to rip the CD.

Any help would be greatly appreciated. Even hints on how to trouble shoot this further.

Best Regards,
Torsten Mielke

---

### Post by tmielke on 2017-12-14
I finally figured out the problem.
After starting asunder from command line I received a pop-up message informing me that cdparanoia was not installed. After also installing lame, and some other encoding libraries like flac I am finally able to rip my CD.

Am somewhat surprised that starting Asunder via the Ubuntu start menu did not generate these errors. Am also surprised that at least cdparanoia was not installed as a package dependency together with Asunder.

Anyway my problem is resolved.

Thanks,
Torsten Mielke

---

