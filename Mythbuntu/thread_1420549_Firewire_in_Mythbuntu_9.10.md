---
title: "Firewire in Mythbuntu 9.10?"
date: 2010-03-03
forum: Mythbuntu
---

### Post by usndmac on 2010-03-03
Hi,

I've searched and read a lot, but I have not been able to find out if firewire is enabled by default in the mythbuntu 9.10 iso.

I've tried some of things like plug report, mythprime, etc. Since they fail I'm guessing the firwire support is not there by default, but, in case I'm just not using them correctly I wanted to make sure before I go get the build essentials and source and start compiling.

Thanks, for any pointers.

---

### Post by 4dognight on 2010-03-03
firewire is supported in 9.10. I am using it now.

---

### Post by usndmac on 2010-03-03
Did you have to add any repositories to get mythprime  or plugscan to work?

---

### Post by 4dognight on 2010-03-03
I believe mythprime is used upon backend startup. I have not heard of plugscan. I can look and report back. I used to have to do manual tweaking in 8.04 for firewire. In 9.10 it worked 'out of the box'.

---

### Post by usndmac on 2010-03-04
Sorry I think it's called plug scan, my bad.

Mine doesn't seem to do uch of anything out of the box. Of course I'm stuck with doing a lot of setup by hand. The install assumes that dhcp is active, if not it doesn't get an IP address and then can't access the web to populate the database.

At that point, I quit, set the IP by hand and start the mythtv-setup.

It seems to run, says it's populating the channel db.

After that I have not found out how to see what it put in the db, how to poke the firewire to see if it sees the cable box, etc. (terminal programs listed here: [http://www.mythtv.org/wiki/FireWire](http://www.mythtv.org/wiki/FireWire)) don't seem to be installed.

---

