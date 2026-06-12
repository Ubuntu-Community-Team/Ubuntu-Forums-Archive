---
title: "Steps to insert tv_grab_uk_rt to run mythfilldatabase"
date: 2008-12-13
forum: Mythbuntu
---

### Post by zf3636 on 2008-12-13
Hi I would like some help on how to configure mythfilldatabase for u.k to run my xmltv in the uk, and what commands to type to set this up, I have a combined mythbuntu 8.04 0.21 Hardy  backend/frontend machine. I have typed the following in the Terminal tv_grab_uk_rt --configure it then runs the all the channels for selection with yes or no prompts once completed,I type tv_grab_uk_rt>PAL-TV.XML,it starts to retrieve channel list once download completes I run mythfilldatabase --manual this fails with FAILED: xmltv returned error code 65280.No channels are configured to use grabber can anyone help thx.

**THIS IS MY MYTHFILLDATABASE LOG**

sohail@sohail-desktop:~$ mythfilldatabase --manual
###
### Running in manual channel configuration mode.
### This will ask you questions about every channel.
###
2008-12-13 13:32:46.822 Using runtime prefix = /usr
2008-12-13 13:32:46.823 Empty LocalHostName.
2008-12-13 13:32:46.823 Using localhost value of sohail-desktop
2008-12-13 13:32:46.842 New DB connection, total: 1
2008-12-13 13:32:46.850 Connected to database 'mythconverg' at host: localhost
2008-12-13 13:32:46.851 Closing DB connection named 'DBManager0'
2008-12-13 13:32:46.852 Connected to database 'mythconverg' at host: localhost
2008-12-13 13:32:46.862 New DB connection, total: 2
2008-12-13 13:32:46.863 Connected to database 'mythconverg' at host: localhost
2008-12-13 13:32:46.864 Source 1 configured to use only the broadcasted guide data. Skipping.
2008-12-13 13:32:46.866 Updating source #2 (PAL-TV ) with grabber tv_grab_uk_rt
2008-12-13 13:32:46.867 No channels are configured to use grabber.
2008-12-13 13:32:46.888 Grabber has capabilities: baseline manualconfig cache preferredmethod 
2008-12-13 13:32:46.912 Grabber prefers method: allatonce
2008-12-13 13:32:46.914 New DB connection, total: 3
2008-12-13 13:32:46.914 Connected to database 'mythconverg' at host: localhost
config file /home/sohail/.mythtv/PAL-TV .xmltv is empty, please delete and run me with --configure
2008-12-13 13:32:48.757 FAILED: xmltv returned error code 65280.
2008-12-13 13:32:48.758 Error in 1:1: unexpected end of file
2008-12-13 13:32:48.759 Updating icons for sourceid: 2
2008-12-13 13:32:48.760 New DB connection, total: 4
2008-12-13 13:32:48.761 Connected to database 'mythconverg' at host: localhost
2008-12-13 13:32:48.763 No programs found in data.
2008-12-13 13:32:48.764 Failed to fetch some program info
2008-12-13 13:32:48.764 Adjusting program database end times.
2008-12-13 13:32:48.765     0 replacements made
2008-12-13 13:32:48.765 Marking generic episodes.
2008-12-13 13:32:48.766     Found 0
2008-12-13 13:32:48.766 Marking repeats.
2008-12-13 13:32:48.769     Found 0
2008-12-13 13:32:48.769 Unmarking new episode rebroadcast repeats.
2008-12-13 13:32:48.769     Found 0
2008-12-13 13:32:48.770 Marking episode first showings.
2008-12-13 13:32:48.771     Found 0
2008-12-13 13:32:48.772 Marking episode last showings.
2008-12-13 13:32:48.772     Found 0
2008-12-13 13:32:48.775 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2008-12-13 13:32:48.784 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-12-13 13:32:48.785 Using protocol version 40
2008-12-13 13:32:48.800 Received a remote 'Clear Cache' request
2008-12-13 13:32:48.807 mythfilldatabase run complete.
2008-12-13 13:32:48.807 DataDirect: Deleting temporary files
sohail@sohail-desktop:~$

---

### Post by ian dobson on 2008-12-13
Hi,

You've created a PAL-TV.xmltv file the user that was logged on when you ran tv_grab_uk_rt --configure but not for the mythtv user. So do the following to copy the configuration to the correct user:-

updatedb
locate PAL-TV

it'll list files with the name PAL-TV
copy the file PAL-TV.xmltv to /home/mythtv/.mythtv/PAL-TV .xmltv 

Or run mythtv-setup say yes to run mythfilldatabase configure, and when the update stops at 50% go to the active terminal windows and complete the configuration. The configuration script seems to start in the background so you don't see it on the screen until you task switch.

Regards
Ian Dobson

---

### Post by zf3636 on 2008-12-15
Hi I am trying to sign into the Terminal window as the mythtv user when I type su mythtv enter, does not allow me to type my password on the next line, I have even opened a second Terminal window to try copy and paste with no luck any other option can I try thx.

---

