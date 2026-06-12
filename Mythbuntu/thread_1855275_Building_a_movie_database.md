---
title: "Building a movie database"
date: 2011-10-05
forum: Mythbuntu
---

### Post by linuxhippy on 2011-10-05
I have a bunch of shows recorded in mythbuntu 11.04 on drive partition sda4.  I also have an older version of mythbuntu (10.04) installed on sda1.  Because I was having trouble with audio in 11.04 I would like to go back to 10.04.  I made a backup of my recording in 11.04 which made this file:

mythconverg-1264-20111005195753.sql.gz

Unfortunately when my 10.04 system restores this backup I am given this error:


"Error: MythTV database has a newer TV schema (1264) than expected (1254)"

So, it seems that I just need to take the recorded shows and make a new database that 10.04 can use.  Is this possible and if so how?

---

### Post by ian dobson on 2011-10-06
Hi,

The information for recorded shows is stored in the follwoing tables:-

1) Recorded
2) Recordedmarkup
3) Recordedprogram
4) Recordedseek

So what you need to do is export these tables into a text file. Install/restore a database version that your backend accepts then import the tables exported above.

**_[COLOR="Red"]SCREWING ABOUT WITH THE DATABASE MANUALLY IS NOT RECOMMENDED, YOU`VE BEEN WARNED!!![/COLOR]_** 

On my website I have a script that checks the mythtv database for errors, I'd imagine you'll need it as you might need to manually correct afew things in the database.

Regards
Ian Dobson

---

### Post by linuxhippy on 2011-10-06
One thing I really want is to modify the channel frequency in Hz that I had set up in 11.04.  In 10.04 I can import a file called channels.conf but I cannot find this file in 10.04 or 11.04.  Is this file called something else now?

---

### Post by nickrout on 2011-10-06
> **linuxhippy said:**
> One thing I really want is to modify the channel frequency in Hz that I had set up in 11.04.  In 10.04 I can import a file called channels.conf but I cannot find this file in 10.04 or 11.04.  Is this file called something else now?

Update to the same version of mythtv via mythbuntu-repos then the database will restore.

---

### Post by ian dobson on 2011-10-07
Hi,

The channels.conf file is not created by mythtv. Normally when mythtv fails to scan for channels in mythtv-setup, you need to create the channels.conf file using w_scan, or some other external program. 

Regards
Ian Dobson

---

### Post by linuxhippy on 2011-10-07
that makes sense...I'll try that with synaptic and let you know how it goes!

---

