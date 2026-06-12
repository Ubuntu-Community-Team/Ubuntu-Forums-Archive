---
title: "EIT not working amongst other problems"
date: 2010-02-18
forum: Mythbuntu
---

### Post by JohnReid on 2010-02-18
I have the following system:

                                  **Intel DH55TC 9.10 system**             
                                                                _**Hardware**_
**Motherboard: **Intel TOM COVE DH55TC
** CPU:** intel Core i3 530
**RAM:** Crucial 4GB
**Video Card: **Integrated
**Sound Card: **Integrated
**HD: **Western Digital 1.5TB Hard Drive SATAII 5400rpm 
**Remote:** none yet
**Tuners: **Hauppage 2200
**Country: **UK
**TV provider: **Freeview
**TV signal type: **DVB-T
**Mythbuntu Version: **9.10I've had quite a struggle getting this far but now I can watch TV on mythbuntu. For the life of me I can't get EIT to work.

I'll just write down what I remember of what I have had to do to get this far:
Set options on the card driver to let it know the card type was 4.
The channel scanning didn't work until I scanned outside of mythtv and used the channels.conf file as the source for the channels.

I now can't get EIT to work. I follow the backend setup and I think I've done everything correctly but when I go to watch TV on the frontend I never get the programme information.

I've also tried using XMLTV from bleb.org and the Radio Times but had no joy there either. I believe EIT is supposed to be easier to use. Am I right?

I have a few other problems that I don't think are related:
- the screen flickers and does not update properly. Often I need to move the mouse or press a key before a screen refresh happens.
- the automatic login sometimes asks for my password, sometimes not
- when mythtv boots up it says the backend is not running although then it goes on to watch TV just fine
- some of the backend configuration screens are too large. I can navigate the controls on the page with my keyboard but sometimes it seems as though there is a control off the screen that has the focus. I have no way of knowing what I've set the value of that control to.

Any help with any of the above would be appreciated but it is the EIT problem that is holding me back most.

Thanks in advance!
John.

---

### Post by Neon Dusk on 2010-02-18
I think to get EIT to work you need to scan within mythtv. What errors did you get when you scanned using mythtv?

---

### Post by JohnReid on 2010-02-18
> **Neon Dusk said:**
> I think to get EIT to work you need to scan within mythtv. What errors did you get when you scanned using mythtv?

It just didn't find any channels.

---

### Post by ian dobson on 2010-02-19
Hi,

Using channels.conf to get the channel information is OK, but sometimes it doesn't fill in all the information required. 

Go into mythtv-setup and rescan the existing channels and make sure you have EIT enabled for your tuner. There is an option to keep the tuner open all the time, enable it so that it always scans for EIT rather than just when recording.

Regards
Ian Dobson

---

### Post by JohnReid on 2010-02-19
> **ian dobson said:**
> Go into mythtv-setup and rescan the existing channels and make sure you have EIT enabled for your tuner. There is an option to keep the tuner open all the time, enable it so that it always scans for EIT rather than just when recording.

Ok on my card was already set up that way. I had increased the timeouts following some advice I'd read elsewhere. I have:

SIgnal timeout: 3000 msec
Tuning timeout: 4000 msec
DVB tuning delay: 400 msec

Wait for SEQ start header: ON
Open DVB card on demand: OFF
Use DVB card for active EIT scan: ON

I think I should also say that once I have used channels.conf subsequent full scans do seem to pick the channels up. It is only when I do a full scan on a new Input Connection that I never tried to use channels.conf on that I cannot find any channels.

Can I test the EIT functionality of the card from the command line somehow? When setting the driver up, I followed the instructions here:
[http://www.xpmediacentre.com.au/community/linux-tutorials-guides/38864-hauppauge-hvr-2200-tuner-install-guide-5.html](http://www.xpmediacentre.com.au/community/linux-tutorials-guides/38864-hauppauge-hvr-2200-tuner-install-guide-5.html)
and set the card type to 4. I'm not 100% sure this is the correct number. It made the card start working and when I tried 5 or 6, the card didn't work. Is it worth spending the time to try all the other possibilities?

I've just finished redoing the scan and it found 55 off-air channels, which I deleted; 6 old DVB channels which I automatically added; and 55 new non-conflicting channels which I added.

I have just tried running 
sudo mythfilldatabase
from the command line and it has given me a segmentation fault
```
2010-02-19 09:21:19.918 Using runtime prefix = /usr
2010-02-19 09:21:19.918 Using configuration directory = /home/john/.mythtv
2010-02-19 09:21:19.918 Empty LocalHostName.
2010-02-19 09:21:19.918 Using localhost value of htpc
2010-02-19 09:21:19.921 New DB connection, total: 1
2010-02-19 09:21:19.926 Connected to database 'mythconverg' at host: localhost
2010-02-19 09:21:19.926 Closing DB connection named 'DBManager0'
2010-02-19 09:21:19.927 Connected to database 'mythconverg' at host: localhost
2010-02-19 09:21:19.930 Current MythTV Schema Version (DBSchemaVer): 1244
2010-02-19 09:21:19.932 New DB connection, total: 2
2010-02-19 09:21:19.932 Connected to database 'mythconverg' at host: localhost
2010-02-19 09:21:19.933 Source 1 configured to use only the broadcasted guide data. Skipping.
2010-02-19 09:21:19.934 Data fetching complete.
2010-02-19 09:21:19.934 Adjusting program database end times.
2010-02-19 09:21:19.935     0 replacements made
2010-02-19 09:21:19.935 Marking generic episodes.
2010-02-19 09:21:19.935     Found 0
2010-02-19 09:21:19.935 Fudging non-unique programids with multiple parts.
2010-02-19 09:21:19.936     Found -1
2010-02-19 09:21:19.936 Marking repeats.
2010-02-19 09:21:19.937     Found 0
2010-02-19 09:21:19.937 Unmarking new episode rebroadcast repeats.
2010-02-19 09:21:19.937     Found 0
2010-02-19 09:21:19.937 Marking episode first showings.
2010-02-19 09:21:19.938     Found 0
2010-02-19 09:21:19.938 Marking episode last showings.
2010-02-19 09:21:19.938     Found 0
2010-02-19 09:21:19.940 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2010-02-19 09:21:19.943 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-02-19 09:21:19.950 Using protocol version 50
2010-02-19 09:21:20.186 Received a remote 'Clear Cache' request
QMutex::lock: mutex lock failure: 
QMutex::lock: mutex unlock failure: 
2010-02-19 09:21:20.186 mythfilldatabase run complete.
2010-02-19 09:21:20.186 DataDirect: Deleting temporary files
Segmentation fault

```

I don't get the segmentation fault if I don't use sudo. Am I right that mythfilldatabase is only used for XMLTV, not for EIT?

Any help appreciated!
Thanks,
John.

---

### Post by JohnReid on 2010-02-19
I found some other EIT options in the backend setup General section. I have:

EIT transport timeout: 5 minutes
Cross source EIT: OFF
Backend idle before EIT crawl: 60 seconds

These all seem reasonable to me.
John.

---

### Post by Neon Dusk on 2010-02-20
[QUOTE=ian dobson]Using channels.conf to get the channel information is OK, but sometimes it doesn't fill in all the information required.[/quote]
Don't think this is correct for mythtv 0.22

John can you try the following
Make a note of your mysql password from /etc/mythtv/mysql.txt - there should be a field DBPassword

```

mysql -u mythtv -p
<enter mysql password>
use mythconverg;
select * from `dtv_multiplex`;

```

This should return a table like
```

+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+-----------+---------+------------+----------------+---------------------+-------------------+
| mplexid | sourceid | transportid | networkid | frequency | inversion | symbolrate | fec  | polarity | modulation | bandwidth | lp_code_rate | transmission_mode | guard_interval | visible | constellation | hierarchy | hp_code_rate | mod_sys   | rolloff | sistandard | serviceversion | updatetimestamp     | default_authority |
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+-----------+---------+------------+----------------+---------------------+-------------------+
|     651 |        1 |       12291 |      NULL | 658166670 | a         |          0 | auto | v        | qam_64     | 8         | 1/2          | 2                 | 1/32           |       0 | qam_64        | n         | 2/3          | UNDEFINED | 0.35    |            |             33 | 2010-02-20 11:05:42 |                   |
|     652 |        1 |       16384 |      NULL | 714166670 | a         |          0 | auto | v        | qam_16     | 8         | 3/4          | 2                 | 1/32           |       0 | qam_16        | n         | 3/4          | UNDEFINED | 0.35    |            |             33 | 2010-02-20 11:05:42 |                   |
|     653 |        1 |       20482 |      NULL | 746000000 | a         |          0 | auto | v        | qam_16     | 8         | 3/4          | 2                 | 1/32           |       0 | qam_16        | n         | 3/4          | UNDEFINED | 0.35    |            |             33 | 2010-02-20 11:05:42 |                   |
|     654 |        1 |       24578 |      NULL | 826000000 | a         |          0 | auto | v        | qam_16     | 8         | 3/4          | 2                 | 1/32           |       0 | qam_16        | n         | 3/4          | UNDEFINED | 0.35    |            |             33 | 2010-02-20 11:05:42 |                   |
|     650 |        1 |        8209 |      NULL | 682166670 | a         |          0 | auto | v        | qam_64     | 8         | 1/2          | 2                 | 1/32           |       0 | qam_64        | n         | 2/3          | UNDEFINED | 0.35    |            |             33 | 2010-02-20 11:05:42 |                   |
|     649 |        1 |        4156 |      NULL | 634166670 | a         |          0 | auto | v        | qam_16     | 8         | 3/4          | 2                 | 1/32           |       0 | qam_16        | n         | 3/4          | UNDEFINED | 0.35    |            |             33 | 2010-02-20 11:05:42 |                   |
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+-----------+---------+------------+----------------+---------------------+-------------------+
6 rows in set (0.00 sec)

```

The problem with using a channels.conf file in mythtv 0.22 is that the networkid value is always null.

Record all the values in the table.

In mythtv-setup -> channel editor -> Edit transport
Delete all exisitng transports (highlight transport then press d)

Go to channel scanner
Select Scan Type: Full Scan (Tuned)

Use the values recorded from the sql statement and then do a scan. You'll need to do this for the 6 muxes.

Hopefully this should find all the channels and if you repeat the sql commands you'll see the networkid value filled in. This should then allow the EIT EPG to work

---

### Post by JohnReid on 2010-02-21
> **Neon Dusk said:**
> Hopefully this should find all the channels and if you repeat the sql commands you'll see the networkid value filled in. This should then allow the EIT EPG to work

Great that's working now. I've no idea how I would have worked that out if I hadn't asked in here. Why doesn't it do it automatically?

Thanks a lot!
John.

---

### Post by Neon Dusk on 2010-02-21
It's a bug in the new MythTV 0.22 channelscanner when using a channels.conf file. Hopefully it will get fixed soon.

---

### Post by trainboy on 2010-03-19
There is a bit of mythology here about what it takes to get over-the-air guide
data working, using the EIT information.  Specifically, the part about the only
way to get it to work being to allow MythTV to scan for channels on the input
source and let it build the dtv_multiplex and channel tables.

I can categorically state that this isn't true.  I've built channel lineups
entirely from scratch, including setting up the dtv_multiplex table and the
channel table with information made up from a scan by a television set.

The most important information, from the EIT scan point of view, is the ATSC
major and minor channel numbers.  The atsc_major_chan and atsc_minor_chan
fields must be set in the channel table or EIT scan will not work.  This is
because the data in the EIT must be matched back up to the channel it belongs
to, so that it can be incorporated into the guide data, and this is where these
two fields come in.  That's swell because the tables I've seen generated by
scte65scan don't have those fields set.  And, apparently, importing a
channels.conf file from scan fails to set these fields.  So, EIT no workee.

Another thing to consider is that EIT scan only scans the first sub-channel
(called a program or service) that is mapped to the multiplex frequency.  For
true over-the-air channels, this isn't usually a problem, since each multiplex
frequency contains only the programs from a single broadcaster and the lowest
sub-channel is almost always a real channel that you're interested in.  But,
for HDTV channels, transmitted by your favorite cable provider, you may find
more than one real channel under a single multiplex frequency.  For example, in
my neck of the woods, Comcast is currently broadcasting the following on one
multiplex frequency:

  [FONT=Courier New]  WCVB HD   5_1     serviceid=1
  WHDH HD   7_1     serviceid=2
  This TV   7_2     serviceid=3
[/FONT] 
This means that, if I want to see EIT data from channel 7_1, I have to turn
it on for channel 5_1 (hey, that's intuitive).  Even more intuitive is the fact
that EIT may need to be turned on for all of the sub-channels in the multiplex
frequency for it to be used by any of them.  But, knowing this, we can now
construct a set of channel entries for our example:

  ```
insert into channel set chanid=1051, channum='5_1', freqid=113, sourceid=1,
       callsign='WCVB-HD', name='WCVB HD (ABC)', serviceid=1, mplexid=113,
       useonairguide=1, atsc_major_chan=5, atsc_minor_chan=1;
  insert into channel set chanid=1071, channum='7_1', freqid=113, sourceid=1,
       callsign='WHDH-HD', name='WHDH HD (NBC, Boston)', serviceid=2, mplexid=113,
       useonairguide=1, atsc_major_chan=7, atsc_minor_chan=1;
  insert into channel set chanid=1072, channum='7_2', freqid=113, sourceid=1,
       callsign='This', name='WHDH This TV', serviceid=3, mplexid=113,
       useonairguide=1, atsc_major_chan=7, atsc_minor_chan=2;

```Pay attention to the fact that the atsc_major_chan and atsc_minor_chan fields,
along with the useonairguide field are set.  Even if the visible field is set
to zero, the useonairguide field should be set on.

There is nothing unusual that needs to be done for the dtv_multiplex table
except that the multiplex ID must be set in the mplexid field.  Mind you,
without this field being set, you won't be looking at any picture or hearing
any sound so this is a no-brainer.

The next thing to do is make sure that active EIT scan is turned on for each of
the DVB cards that you want to use for active EIT scanning (you could just
allow passive scanning but this means that you actually have to view each of
the channels before its guide data will show up).  You'll want to have at least
one card that is mapped to each input source but you can have more since the
scan knows how to effectively use multiple cards.  You can do this from the
Capture Card section of the Myth Backend configuration application or you could
try something like this:

  ```
update capturecard set dvb_eitscan=1 where cardtype='DVB';
```Finally, you need to turn on EIT scanning for the input source in question.
You can do this from the Input Sources section of the Myth Backend
configuration application, at the same time you turn on active EIT scan, or
you could try something like this:

  ```
update videosource set xmltvgrabber='eitonly', useeit=1 where sourceid=1;

```You may need to recycle the backend on each of the machines that actually have
the capture cards that will do the EIT scanning installed, although launching
the Myth Backend configuration application takes care of this for you.

Note that, if over-the-air guide data via EIT still doesn't work, once you've
done all this, you should enter the following SQL command:

  ```
select channum, min(chanid), mplexid
    from channel, cardinput, capturecard, videosource
    where cardinput.sourceid=channel.sourceid
      and videosource.sourceid=channel.sourceid
      and capturecard.cardid=cardinput.cardid
      and channel.mplexid is not null and useonairguide=1 and useeit=1
      and channum!='' and cardinput.cardid=1
    group by mplexid
    order by cardinput.sourceid, mplexid, atsc_major_chan, atsc_minor_chan;
```Change the cardid value from "1" to the actual card number of the capture card
that's to do the EIT scanning.  You should see a table that looks something
like this:

  [FONT=Courier New]    +---------+-------------+---------+
  | channum | min(chanid) | mplexid |
  +---------+-------------+---------+
  | 27_1    |        1271 |      82 |
  | 10_1    |        1101 |      83 |
  | 68_1    |        1361 |      99 |
  | 7_2     |        1051 |     113 |
  | 25_1    |        1041 |     114 |
  | 2_1     |        1021 |     115 |
  | 38_1    |        1381 |     116 |
  +---------+-------------+---------+
[/FONT]
If you don't you've messed something up.  Keep checking things until such a
listing appears.  Then, check the channel table entries for each of the channel
IDs shown.  They, at least, must have their ATSC major and minor numbers set.
But, it wouldn't hurt to set the ATSC major and minor numbers for all of the
channels that have the same multiplex ID as those listed.

One final note.  Your friends at your favorite cable company may strip the
over-the-air guide data from your local HDTV channels.  This is definitely the
case with Comcast in our area, for example.  Whereas the EIT data from a
terrestrial broadcast of WCVB includes program names, episode titles and
extensive episode descriptions for the next 18-20 hours, the EIT data from WCVB
on Comcast cable only includes the program names, and only for the next 8-10
hours.  Not that it matters from the scheduler's point of view, mind you, since
guide data changes due to EIT scanning are reflected immediately but you will
be missing the extended program information such as episode titles and
descriptions.

---

### Post by Neon Dusk on 2010-03-19
> **trainboy said:**
> There is a bit of mythology here about what it takes to get over-the-air guide

...

The most important information, from the EIT scan point of view, is the ATSC
major and minor channel numbers.  The atsc_major_chan and atsc_minor_chan
fields must be set in the channel table or EIT scan will not work.
...


I think you've jumped on the wrong thread. This thread is about DVB-T in Europe not ATSC.

---

### Post by trainboy on 2010-03-20
Oh, yeah. Europe. My bad.

Funnily enough, active EIT scan still uses atsc_major_num and atsc_minor_num to do its select of the channels to scan. But, since they're only used to order the results of the select, I guess it makes no nevermind.

Meanwhile, the notes about needing some way to convert the information in the EIT into a channel ID that MythTV can use to store the data are still relevant. Only, for Europe, the channel ID is looked up using serviceid, networkid, transportid and optionally sourceid. So, if those fields are not set in your database you're going nowhere fast.

For ATSC, the returned EIT data must match this select:

```
select chanid, useonairguide from channel
  where atsc_major_chan=xx and atsc_minor_chan=yy
    and sourceid=1;

```Where xx and yy are the major and minor numbers and 1 is the source number (typically 1).

Otherwise, for everyone else, the returned EIT data must match this select:

```
select chanid, useonairguide from channel, dtv_multiplex
  where serviceid=xx and networkid=yy and transportid=zz
    and channel.mplexid=dtv_multiplex.mplexid;
```Where xx, yy and zz are the service ID, network ID and transport ID.

Optionally, if sourceid is set, the following is appended to the where clause:

```
  and channel.sourceid=1

```Where 1 is the source number (typically 1).

The rest of the discussion is more or less pertinent. The useonairguide, dvb_eitscan and useeit flags still must be set. And, the scan still looks for the lowest sub-channel in a particular multiplex frequency so if there's more than one program packed into a stream, you need to be aware of that fact.

Either way, Europe or North America, there doesn't seem to be much magic involved. You can take a look at the applicable code in eitscanner.cpp and eithelper.cpp (both in libs/libmythtv) if you still can't get it to work but it looks fairly straightforward. There is some special case stuff, supposedly for special EIT data from the German provider Premiere for the optional channels Premiere Sport and Premiere Direkt, but other than that, it looks like: read the EIT data; resolve the channel number; parse the data; stuff the data in the database.

---

