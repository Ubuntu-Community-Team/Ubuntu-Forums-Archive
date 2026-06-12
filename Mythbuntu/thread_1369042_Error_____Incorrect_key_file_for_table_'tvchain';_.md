---
title: "Error    : Incorrect key file for table 'tvchain'; try to repair it"
date: 2009-12-31
forum: Mythbuntu
---

### Post by rusty0101 on 2009-12-31
This is currently 'solved' but I'm posting it in case someone else runs into a similar issue and is looking for some help. Solution found by scroling down to {{{######}}}

But I'll start with the frustration I ran into.

So when I attempt to watch live TV, I silently get thrown back into the menu with no explanation in the ui. So I did a follow on the local front end running on 'lenny' and get the following:
```

2009-12-31 09:09:09.426 TV: Attempting to change from None to Watching WatchingLiveTV
2009-12-31 09:09:09.435 MythContext: Connecting to backend server: 192.168.1.5:6543 (try 1 of 1)
2009-12-31 09:09:09.442 Using protocol version 50
2009-12-31 09:09:09.626 Spawning LiveTV Recorder -- begin
2009-12-31 09:09:12.203 Spawning LiveTV Recorder -- end
2009-12-31 09:09:12.204 Error preparing query: SELECT chanid, starttime, endtime, discontinuity, chainpos, hostprefix, cardtype, channame, input FROM tvchain WHERE chainid = :CHAINID ORDER BY chainpos;
2009-12-31 09:09:12.205 Driver error was [2/1034]:
QMYSQL3: Unable to prepare statement
Database error was:
Incorrect key file for table 'tvchain'; try to repair it

2009-12-31 09:09:12.205 GetEntryAt(-1) failed.
2009-12-31 09:09:12.210 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2009-12-31 09:09:12.210 TV Error: HandleStateChange(): LiveTV not successfully started
2009-12-31 09:09:12.211 We have a RingBuffer
2009-12-31 09:09:12.261 TV Error: LiveTV not successfully started
2009-12-31 09:09:12.282 ScreenSaverX11Private: DPMS Deactivated 1
2009-12-31 09:09:12.282 ScreenSaverX11Private: DPMS Reactivated 1
2009-12-31 09:09:14.468 Error preparing query: DELETE FROM tvchain WHERE chainid = :CHAINID ;
2009-12-31 09:09:14.468 Driver error was [2/1034]:
QMYSQL3: Unable to prepare statement
Database error was:
Incorrect key file for table 'tvchain'; try to repair it

2009-12-31 09:09:14.468 DB Error (LiveTVChain::DestroyChain):
Query was:
DELETE FROM tvchain WHERE chainid = ? ;
Bindings were:
:CHAINID=live-Lenny-2009-12-31T09:09:09
No error type from QSqlError?  Strange...

```

Ah, so the recommended action at the moment is to try to repair tvchain. Ok. So I go to the back end, and try to repair it using the command:  "mysqlrepair -r mythconverg -u root -p" and get back:
```

Enter password: 
mythconverg.archiveitems                           OK
mythconverg.callsignnetworkmap                     OK
mythconverg.capturecard                            OK
mythconverg.cardinput                              OK
<clip of a bunch of 'OK' results>
mythconverg.schemalock                             OK
mythconverg.settings                               OK
mythconverg.storagegroup                           OK
mythconverg.tvchain
Error    : Incorrect key file for table 'tvchain'; try to repair it
error    : Corrupt
mythconverg.tvosdmenu                              OK
mythconverg.upnpmedia                              OK
mythconverg.videocast                              OK
mythconverg.videocategory                          OK
mythconverg.videocountry                           OK
<clip>

```

The Error line, followed by the error line are the ones I'm concerned about. I've tried renaming the various tvchain.??? files in /var/lib/mysql/mythconverg to see if I can get the repair function to regenerate the appropriate index, to no avail.

If I could figure out how to generate 'that' collection of files so that they are correct, and can be used to replace the corrupt file, it would probably be of help. Unfortunately I have no idea what data is actually stored in that table, other than the presumption that it is critical for watching 'live' tv, but completely unimportant so far as recording shows, or watching the recordings, including while they are being recorded.

The result of no live tv does not matter whether it is a remote front end, or on the same system as the master back end.

Since I know that people are going to ask:

Ubuntu release: Karmic 9.10 distribution: Mythbuntu
MythTV release: MythTV 0.22
Tuners (Multiple) 2 HDHomerun devices (4 total capture devices) 1 hvr-1600 (2 tuners, 1 analog, 1 atsc) 2 pvr-250 (single tuner each) 1 Pinnical tuner capable of digital or analog, set up for digital ota.

Analog tuners and one of the hdhomerun devices are attached to cable for analog and qam unencrypted capture. Remaining digital tuners are capturing OTA.

All software is the standard repository software, not the nightly builds editions. As of December 31, 2009.

{{{######}}}
Solution:
{{{######}}}
Ok. this is only useful if at some time before you run into this problem (i.e. like almost immediately after you confirm that all the tables check out OK with 'mysqlcheck mythconverg -u root -p' you perform a database backup.) If you haven't already, this table could be rebuilt from someone else's backup, but that is not true for other databases.

I was frustrated enough that even if the data in the backup was missing information for later backups, I would rather have something  to start with than the broken state I was in. Not generally a good state to be in, but desperate measures.

If you have done a mythconverge_backup.pl at some point, then in the /var/backups folder there should be one or more files that are named mythconverg.sql.gz[.#] (where the [.#] is a sequential number incremented for each backup with the oldest having the highest number.)

I copied the oldest of these to my home directory, then ran gunzip against the file and ended up with the file mythconverg.sql which is a text file.

I then ran less to view the contents of the file, and used the key sequence /tvchain to find the first instance of 'tvchain' in the file. I then selected the mysql commands related to dropping, creating, and rebuilding the content of this table, which put the selected text into a copy buffer.

In a separate text view I ran the command 'mysql mythconverg -u root -p' and entered my password. At the mysql> prompt I pasted in the text from the mythconverg.sql file.

From what I can tell, this table is either primarily, or exclusively used by mythtv to keep track of what channel is being watched by what front end in live tv mode. 

Once you have confirmed that you have a database that tests 'OK' I would recommend opening a command shell to the master back end system, and executing the command /usr/share/mythtv/mythconverg_backup.pl to generate a fresh backup.

If you are getting similar results to what I was (mysqlrepair is not repairing the tvchain table, claims that the keyfile for the table is invalid, recommends 'repairing' it, then gives an error: corrupt result) I have attached the excerpted mysql commands that recreates this file on my system. I would definately not recommend trying to use this file with any release of mythtv that is not table compatible with 0.22. For example I would be very concerned about trying to use this file on 0.21 or earlier releases.

---

