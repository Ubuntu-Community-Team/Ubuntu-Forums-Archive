---
title: "Cannot see network"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by LaptopU on 2010-05-05
Two machines with Lucid installed last week, both installed with the same standard settings.  One machine can see the network and both itself and the other machine, the other PC cannot see the first machine or itself.  In the Network window all I get is a folder saying 'Windows Network' and clicking that ticks away for a minute or so before saying error, cannot connect to it.

On both machines I have created a shared folder on the desktop to trigger an installation of samba shares which has happened.  I cannot connect to the other PC by entering its IP address into location either.

Does anyone have any ideas or can you point me in the right direction please?

---

### Post by LaptopU on 2010-05-06
Any advice is appreciated.

---

### Post by Iowan on 2010-05-06
Do pings work?

---

### Post by LaptopU on 2010-05-06
> **Iowan said:**
> Do pings work?

Yes, there has been a bit of a development on this.  Now I can enter the IP address of either machine and it will bring up the shares.  However in the Network folder, machine A is very slow and sometimes does not even bring itself up in the folder.  Machine B behaves normally, bringing itself up in the folder and machine A too.

I have run a command which for some odd reason I cannot remember now, something like fmsmb (and I deleted my history on terminal), which lists the machines a computer can find.  Computer B comes up as normal, listing it is connected to workgroup, it is using Samba then the version, then operating system as Unix, and also lists computer A.  Computer A does this for itself but then pauses for a while, then lists computer B only as being connected to workgroup - it does not list Samba version or OS at all.

---

