---
title: "what file holds the scanned channel information?"
date: 2009-04-19
forum: Mythbuntu
---

### Post by neutron68 on 2009-04-19
When you perform a channel scan with the Mythtv GUI during Mythtv setup, where does the scanned channel information get stored?  Which file?

I searched the hard drive and didn't find any obvious files called "channel" or "channels", etc.

The reason for the question - a friend was asking me how to view the list of scanned channels and their information.  He has a pcHDTV HD-5500 card for over-the-air DTV and QAM over cable.

Appreciated,
Eric

---

### Post by tgm4883 on 2009-04-19
Everything is kept in the database.  What channel info do you want to see?  Listings or frequency and name stuff?

---

### Post by neutron68 on 2009-04-19
> **tgm4883 said:**
> Everything is kept in the database.  What channel info do you want to see?  Listings or frequency and name stuff?
I suspect he wants to see: ATSC/QAM channel numbers, callsign, frequency, tvformat.
He'll probably want to have a text file of this info, in the end.

Eric

---

### Post by tgm4883 on 2009-04-19
> **neutron68 said:**
> I suspect he wants to see: ATSC/QAM channel numbers, callsign, frequency, tvformat.
He'll probably want to have a text file of this info, in the end.

Eric

Why would you want a text file of this info?

---

### Post by neutron68 on 2009-04-19
> **tgm4883 said:**
> Why would you want a text file of this info?
I believe he wants to compare channel lineup changes over time, as his cable provider has been swapping channels around.

Is there a way to read the database and extract that channel information?

Hopeful,
Eric

---

### Post by tgm4883 on 2009-04-19
Well you can see this info in mythweb go to

```
http://BACKENDIP/mythweb/settings/tv/channels
```

Alternatively, you could write a script to print that table to a file

---

### Post by neutron68 on 2009-04-19
> **tgm4883 said:**
> Well you can see this info in mythweb go to

```
http://BACKENDIP/mythweb/settings/tv/channels
```
That might be good enough for him.  I'll tell him about it.

> **tgm4883 said:**
> 
Alternatively, you could write a script to print that table to a file
I think a text file created from the database content is probably the way to go.  
But, if I knew how to write a script to harvest the data from the database, I wouldn't be here asking how to do it.  Would I? ;)

Eric

---

### Post by nickrout on 2009-04-19
[http://www.mythtv.org/wiki/Channel_table](http://www.mythtv.org/wiki/Channel_table) probably has what you want.

---

### Post by neutron68 on 2009-04-19
Hi, I got what I was looking for.  I got some help from a guy over on the Knoppmyth forum.  This command line dumps the channel list to a text file!
```
mysql -uroot mythconverg -B --exec "select channum,callsign,freqid,atsc_major_chan,atsc_minor_chan from channel;" > /home/user/scannedchannels.txt
```
The output looks like this:
```
channum   callsign   freqid   atsc_major_chan   atsc_minor_chan
2.4   tpt Wx   16   2   4
2.9   data2   16   2   9
29.1   WFTC-HD   21   29   1
29.2   WFTC-SD   21   29   2
9.1   KMSP-HD   26   9   1
9.2   KMSP-SD   26   9   2
4.1   WCCO-DT   32   4   1
2.1   tpt 2   34   2   1
2.2   tpt MN   34   2   2
11.1   KARE-HD   35   11   1
11.2   KARE-WX   35   11   2
41.1   ION   40   41   1
41.2   qubo   40   41   2
41.3   IONLife   40   41   3
41.4   Worship   40   41   4
45.1   KSTCDT1   44   45   1
5.1   KSTPDT1   50   5   1
5.2   KSTPDT2   50   5   2
2.3   tptLife   16   2   3
23.1   WUCW-HD   22   23   1
23.2   WUCW-SD   22   23   2
```

Cheers!
Eric

---

