---
title: "Printer No Longer Working (CIFS host)"
date: 2010-09-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by DedMoroz on 2010-09-22
I upgraded to 10.10 and printing no longer works for me. Ive tried deleting my printer and re-adding it to no avail. Any help would be appreciated! All the other 10.04 systems connected to the network print fine :) Just not mine.

Dont know if this will help, but I ran the debugging feature in the printing section...

[http://paste.ubuntu.com/498731/](http://paste.ubuntu.com/498731/)

When looking at the properties of my printer, I see this error:

"Unable to connect to CIFS host, will retry in 60 seconds..."

---

### Post by cariboo on 2010-09-22
How are you connecting to the printer? USB cable, network, connected to a computer running Windows, another computer running Ubuntu?

---

### Post by DedMoroz on 2010-09-22
The printer computer is running XP and we have about 6 computers networked to that running Ubuntu 10.04 lucid. Those all print fine. I upgraded to 10.10 and now unable to print.

---

### Post by DedMoroz on 2010-09-22
So to clarify... all the networked computers are running Ubuntu and are hardwired to the main computer which is XP and has the printer. All printing works fine with the 10.04 computers. My computer was upgraded to 10.10 and now printing does not work. I am also unable to find the network or the printer now as well.

The connection info is (or was):

smb://MSHOME/NET/Printer

Which pulls up nothing. Ive even tried installing the HP Toolbox to see if it would find the printer and no luck. 

Ive also tried finding the printer in [http://localhost:631/](http://localhost:631/) with no luck either. 

Maverick doesnt seem to be able to see the network at all now.

---

### Post by cariboo on 2010-09-22
There is a problem with smbclient, that should be fixed before the final release.

---

### Post by DedMoroz on 2010-09-22
Can I file a bug on launchpad to help escalate this? I did a bunch of gwibber debugging before 10.04 came out so would be willing to help on this in any way as well.

---

### Post by cariboo on 2010-09-22
Is this the bug you reported? Bug #[lpbug]645630[/lpbug]

---

### Post by DedMoroz on 2010-09-22
> **cariboo907 said:**
> Is this the bug you reported? Bug #[lpbug]645630[/lpbug]

Yes. Hope I did it right. I noticed samba wasnt installed. I installed it, but that didnt help either.

---

### Post by cariboo on 2010-09-22
You only need samba for sharing files with Windows computers. I've added my me too. to your bug.

---

