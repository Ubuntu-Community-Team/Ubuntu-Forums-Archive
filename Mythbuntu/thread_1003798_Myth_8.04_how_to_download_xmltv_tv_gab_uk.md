---
title: "Myth 8.04 how to download xmltv tv_gab_uk"
date: 2008-12-06
forum: Mythbuntu
---

### Post by zf3636 on 2008-12-06
Hello I want to run mythfiledatabase in the Terminal window to select tv guide data, for my combined mythbackend and mythfrontend machine. I only receive tv channels over a analogue antenna not dvb. I would like to know how to set this up so mythfiledatabase can grab tv guide from [www.bleb.org/tv](www.bleb.org/tv) or tv_grab_uk_rt so it can compile XMLTV grabber info every time mythfiledatabase runs, this is my settings Video source: Pal/tv Listing grabber:United Kingdom (bleb.org) (XMLTV), tv_grab_uk (bleb):  configuration will run in the terminal window Channel frequencies: Europe West, I have also tried tv_grab_uk_rt this option just freezes at 50%, How do i run the configuration in the terminal window, and what steps can i take to set this up thx

---

### Post by zf3636 on 2008-12-07
I have visited the mythtv wiki tried this command in the terminal window by typing tv_grab_uk_rt --configure, it then went through all of 277 channels I selected only the ones i needed ie BBC1. BBC2, ITV, C4, C5 that i wanted by following the yes/no prompts, i then typed tv_grab_uk_rt> tv.xml, then it started to retrieve channel data by downloading the channel info, once completed i still do not know how to access this info through mythtv frontend. the downloaded files have been saved to /tv_grab_uk_rt.conf but they should have been saved to /mythtv/videosourcename.xmltv because where videosourcename is the name of the videosource I wish to bind the channels i have chosen.what I would like to know is what command to type to copy the tv_grab_uk_rt.conf to /mythtv/videosourcename.xmltv the above info I found at the following website hhtp://mythtv.org/wiki/index.php/uk_xmltv any help will be appreciated thx.

---

### Post by drifting on 2008-12-07
Go take a look at [http://parker1.co.uk/mythtv_id.php](http://parker1.co.uk/mythtv_id.php) very helpful guide that got me working, although I now use EIT.

Regards Paul.

---

### Post by zf3636 on 2008-12-08
Hello I would like to know is what command to type to copy the tv_grab_uk_rt.conf to /mythtv/videosourcename.xmltv

---

### Post by zf3636 on 2008-12-10
Hi I would like some help in finding A Method to simplify inserting xmltvids" stuff this is what i am missing to link the schedule data with the channels table, and also what command to type to find the channel table or how to edit the info and compile a script for tv_grab_uk_rt uk xmltv mythfiledatabase in the Terminal window, can anyone help with this step by step guide thx.

this is my mythfilldabase log which i ran manually

sohail@sohail-desktop:~$ mythfilldatabase --manual
###
### Running in manual channel configuration mode.
### This will ask you questions about every channel.
###
2008-12-10 20:23:19.065 Using runtime prefix = /usr
2008-12-10 20:23:19.066 Empty LocalHostName.
2008-12-10 20:23:19.066 Using localhost value of sohail-desktop
2008-12-10 20:23:19.078 New DB connection, total: 1
2008-12-10 20:23:19.083 Connected to database 'mythconverg' at host: localhost
2008-12-10 20:23:19.084 Closing DB connection named 'DBManager0'
2008-12-10 20:23:19.085 Connected to database 'mythconverg' at host: localhost
2008-12-10 20:23:19.090 New DB connection, total: 2
2008-12-10 20:23:19.091 Connected to database 'mythconverg' at host: localhost
2008-12-10 20:23:19.091 Source 1 configured to use only the broadcasted guide data. Skipping.
2008-12-10 20:23:19.093 Updating source #2 (PAL-TV ) with grabber tv_grab_uk_bleb
2008-12-10 20:23:19.093 No channels are configured to use grabber.
2008-12-10 20:23:19.102 Grabber has capabilities: baseline manualconfig 
2008-12-10 20:23:19.103 
2008-12-10 20:23:19.103 Checking day @ offset 0, date: Wed Dec 10 2008
2008-12-10 20:23:19.104 Data refresh needed because no data exists for day @ offset 0 from 8PM - midnight.
2008-12-10 20:23:19.105 Refreshing data for Wed Dec 10 2008
2008-12-10 20:23:19.106 New DB connection, total: 3
2008-12-10 20:23:19.106 Connected to database 'mythconverg' at host: localhost
config file /home/sohail/.mythtv/PAL-TV .xmltv is empty, please delete and run me with --configure
2008-12-10 20:23:19.957 FAILED: xmltv returned error code 65280.
2008-12-10 20:23:19.959 Error in 1:1: unexpected end of file
2008-12-10 20:23:19.959 Updating icons for sourceid: 2
2008-12-10 20:23:19.961 New DB connection, total: 4
2008-12-10 20:23:19.966 Connected to database 'mythconverg' at host: localhost
2008-12-10 20:23:19.967 No programs found in data.
2008-12-10 20:23:19.967 Grabber is no longer returning program data, finishing
2008-12-10 20:23:19.968 Failed to fetch some program info
2008-12-10 20:23:19.968 Adjusting program database end times.
2008-12-10 20:23:19.968     0 replacements made
2008-12-10 20:23:19.968 Marking generic episodes.
2008-12-10 20:23:19.969     Found 0
2008-12-10 20:23:19.969 Marking repeats.
2008-12-10 20:23:19.971     Found 0
2008-12-10 20:23:19.971 Unmarking new episode rebroadcast repeats.
2008-12-10 20:23:19.972     Found 0
2008-12-10 20:23:19.972 Marking episode first showings.
2008-12-10 20:23:19.973     Found 0
2008-12-10 20:23:19.973 Marking episode last showings.
2008-12-10 20:23:19.973     Found 0
2008-12-10 20:23:19.975 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2008-12-10 20:23:19.985 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-12-10 20:23:19.987 Using protocol version 40
2008-12-10 20:23:19.998 Received a remote 'Clear Cache' request
2008-12-10 20:23:20.002 mythfilldatabase run complete.
2008-12-10 20:23:20.002 DataDirect: Deleting temporary files
sohail@sohail-desktop:~$ /home/sohail/.mythtv/PAL-TV .xmltv --configure
bash: /home/sohail/.mythtv/PAL-TV: No such file or directory

---

### Post by ian dobson on 2008-12-10
Hi,

You need to create a configuration file for the user that will run the script so.

```

su mythtv (or your mythtv user)
tv_grab_uk_bleb --configure (this will create the config file for the myth user)
mythfilldatabase

```

Regards
Ian Dobson

---

### Post by zf3636 on 2008-12-11
Hi have done the above and has not worked this is the result of mythfilldatabes even compiled a script as follows i will appreciate any help thx. 

update channel set xmltvid="north.bbc1.bbc.co.uk" where callsign="http://www.lyngsat-logo.com/logo/tv/bb/bbc1.jpg";
update channel set xmltvid="north.bbc2.bbc.co.uk" where callsign="http://www.lyngsat-logo.com/logo/tv/bb/bbc2.jpg";
update channel set xmltvid="yorkshire.itv1.itv.co.uk" where callsign="http://www.lungsat-logo.com/logo/tv/ii/itv1_yorkshire.jpg";
update channel set xmltvid="channel4.com" where callsign="http://www.lyngsat-logo.com/logo/tv/cc/channel4.jpg";


### Running in manual channel configuration mode.
### This will ask you questions about every channel.
###
2008-12-11 22:02:06.704 Using runtime prefix = /usr
2008-12-11 22:02:06.705 Empty LocalHostName.
2008-12-11 22:02:06.705 Using localhost value of sohail-desktop
2008-12-11 22:02:06.717 New DB connection, total: 1
2008-12-11 22:02:06.722 Connected to database 'mythconverg' at host: localhost
2008-12-11 22:02:06.723 Closing DB connection named 'DBManager0'
2008-12-11 22:02:06.724 Connected to database 'mythconverg' at host: localhost
2008-12-11 22:02:06.728 New DB connection, total: 2
2008-12-11 22:02:06.728 Connected to database 'mythconverg' at host: localhost
2008-12-11 22:02:06.730 Source 1 configured to use only the broadcasted guide data. Skipping.
2008-12-11 22:02:06.732 Updating source #2 (PAL-TV ) with grabber tv_grab_uk_rt
2008-12-11 22:02:06.733 No channels are configured to use grabber.
2008-12-11 22:02:06.747 Grabber has capabilities: baseline manualconfig cache preferredmethod 
2008-12-11 22:02:06.762 Grabber prefers method: allatonce
2008-12-11 22:02:06.769 New DB connection, total: 3
2008-12-11 22:02:06.770 Connected to database 'mythconverg' at host: localhost
config file /home/sohail/.mythtv/PAL-TV .xmltv is empty, please delete and run me with --configure
2008-12-11 22:02:07.453 FAILED: xmltv returned error code 65280.
2008-12-11 22:02:07.454 Error in 1:1: unexpected end of file
2008-12-11 22:02:07.455 Updating icons for sourceid: 2
2008-12-11 22:02:07.456 New DB connection, total: 4
2008-12-11 22:02:07.457 Connected to database 'mythconverg' at host: localhost
2008-12-11 22:02:07.459 No programs found in data.
2008-12-11 22:02:07.460 Failed to fetch some program info
2008-12-11 22:02:07.460 Adjusting program database end times.
2008-12-11 22:02:07.460     0 replacements made
2008-12-11 22:02:07.460 Marking generic episodes.
2008-12-11 22:02:07.461     Found 0
2008-12-11 22:02:07.461 Marking repeats.
2008-12-11 22:02:07.463     Found 0
2008-12-11 22:02:07.464 Unmarking new episode rebroadcast repeats.
2008-12-11 22:02:07.464     Found 0
2008-12-11 22:02:07.464 Marking episode first showings.
2008-12-11 22:02:07.465     Found 0
2008-12-11 22:02:07.465 Marking episode last showings.
2008-12-11 22:02:07.465     Found 0
2008-12-11 22:02:07.468 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2008-12-11 22:02:07.477 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-12-11 22:02:07.479 Using protocol version 40
2008-12-11 22:02:07.494 Received a remote 'Clear Cache' request
2008-12-11 22:02:07.498 mythfilldatabase run complete.
2008-12-11 22:02:07.502 DataDirect: Deleting temporary files
sohail@sohail-desktop:~$

---

### Post by zf3636 on 2008-12-12
Hi can anyone show me the steps to do this, a way to copy /home/mythtv to /root/.mythtv it's got something to do with mythfilldatabase running as root but not having the "videosource.xmltv file". Log in as root and copy your "videosourcename.xmltv" file from /home/mythtv over to /root/.mythtv I had a look at this site [http://fionn-mythtv.blogspot.com/2008/01/program-guide-setup.html](http://fionn-mythtv.blogspot.com/2008/01/program-guide-setup.html) this might be what I a missing to do thx.

---

