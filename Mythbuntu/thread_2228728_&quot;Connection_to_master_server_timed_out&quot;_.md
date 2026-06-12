---
title: "&quot;Connection to master server timed out&quot; - Can't start MythTV"
date: 2014-06-09
forum: Mythbuntu
---

### Post by patslap on 2014-06-09
Whenever I start Myth frontend I get an error messaqe saying "Could not connect to master backend. Mythcontext. Could not connect to the master backend server. Is it running?"
[ATTACH=CONFIG]253845[/ATTACH]

It doesn't appear as if the backend is running. When I run sudo service mythtv-backend start I can't see the process running in top.

If I run mythfilldatabase I get the following output

```
ndrew@htpc:~$ mythfilldatabase 
2014-06-09 11:35:17.908602 C  mythfilldatabase version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
2014-06-09 11:35:17.908619 C  Qt version: compile: 4.8.6, runtime: 4.8.6
2014-06-09 11:35:17.908622 N  Enabled verbose msgs:  general
2014-06-09 11:35:17.908630 N  Setting Log Level to LOG_INFO
2014-06-09 11:35:17.920768 I  Added logging to the console
2014-06-09 11:35:17.921874 I  Setup Interrupt handler
2014-06-09 11:35:17.921896 I  Setup Terminated handler
2014-06-09 11:35:17.921914 I  Setup Segmentation fault handler
2014-06-09 11:35:17.921932 I  Setup Aborted handler
2014-06-09 11:35:17.921949 I  Setup Bus error handler
2014-06-09 11:35:17.921967 I  Setup Floating point exception handler
2014-06-09 11:35:17.921987 I  Setup Illegal instruction handler
2014-06-09 11:35:17.922019 I  Setup Real-time signal 0 handler
2014-06-09 11:35:17.922083 N  Using runtime prefix = /usr
2014-06-09 11:35:17.922107 N  Using configuration directory = /home/andrew/.mythtv
2014-06-09 11:35:17.922228 I  Assumed character encoding: en_GB.UTF-8
2014-06-09 11:35:17.922866 N  Empty LocalHostName.
2014-06-09 11:35:17.922883 I  Using localhost value of htpc
2014-06-09 11:35:17.945417 N  Setting QT default locale to en_US
2014-06-09 11:35:17.945491 I  Current locale en_US
2014-06-09 11:35:17.945538 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2014-06-09 11:35:17.953457 I  Loading en_gb translation for module mythfrontend
2014-06-09 11:35:17.955552 I  Current MythTV Schema Version (DBSchemaVer): 1317
2014-06-09 11:35:17.958395 I  MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2014-06-09 11:35:17.959298 E  MythSocket(17b78c0:-1): Failed to connect to (127.0.0.1:6543) Connection refused
2014-06-09 11:35:17.959533 E  Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2014-06-09 11:35:17.959557 W  Failed to connect to master backend. MythFillDatabase will continue running but will be unable to prevent backend from shutting down, or triggering a reschedule when complete.
2014-06-09 11:35:17.993616 I  Source 1 configured to use only the broadcasted guide data. Skipping.
2014-06-09 11:35:17.996099 N  Data fetching complete.
2014-06-09 11:35:17.996131 I  Adjusting program database end times.
2014-06-09 11:35:18.013019 I      0 replacements made
2014-06-09 11:35:18.013027 I  Marking generic episodes.
2014-06-09 11:35:18.022897 I  New Client:  (#1)
2014-06-09 11:35:18.057792 I      Found 0
2014-06-09 11:35:18.057801 I  Extending non-unique programids with multiple parts.
2014-06-09 11:35:18.069437 I      Found 0
2014-06-09 11:35:18.069445 I  Fixing missing original airdates.
2014-06-09 11:35:18.083304 I      Found 0 with programids
2014-06-09 11:35:18.088927 I      Found 0 without programids
2014-06-09 11:35:18.088935 I  Marking repeats.
2014-06-09 11:35:18.124200 I      Found 0
2014-06-09 11:35:18.124208 I  Unmarking new episode rebroadcast repeats.
2014-06-09 11:35:18.159633 I      Found 0
2014-06-09 11:35:18.280483 I  Marking episode first showings.
2014-06-09 11:35:18.483465 I      Found 4962
2014-06-09 11:35:18.483477 I  Marking episode last showings.
2014-06-09 11:35:18.712727 I      Found 4577
2014-06-09 11:35:18.714026 I  
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2014-06-09 11:35:18.714701 I  MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2014-06-09 11:35:18.715456 E  MythSocket(17808d0:-1): Failed to connect to (127.0.0.1:6543) Connection refused
2014-06-09 11:35:18.715768 E  Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2014-06-09 11:35:18.715796 E  Error rescheduling MATCH 0 0 0 - MythFillDatabase in ScheduledRecording::SendReschedule
2014-06-09 11:35:18.715992 N  mythfilldatabase run complete.
2014-06-09 11:35:18.716068 I  MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2014-06-09 11:35:18.716090 I  Waiting for threads to exit.
2014-06-09 11:35:18.717323 E  MythSocket(7f565800ba60:-1): Failed to connect to (127.0.0.1:6543) Connection refused
2014-06-09 11:35:18.717563 E  Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2014-06-09 11:35:18.717605 I  MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2014-06-09 11:35:18.717874 E  MythSocket(7f565c00c070:-1): Failed to connect to (127.0.0.1:6543) Connection refused
2014-06-09 11:35:18.717949 E  Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

```

Can anyone help me to get the backend working with the  thanks

---

### Post by patslap on 2014-06-09
I've checked that video card (TBS6285) is configured and drivers are installed correctly by using scan, tzap and mplayer, and video stream plays fine, so this looks like a software problem. Any ideas anyone?

---

### Post by patslap on 2014-06-09
Backend and hardware logs are here:

[http://pastebin.com/bmFeu2v6](http://pastebin.com/bmFeu2v6)

---

### Post by patslap on 2014-06-09
This is strange, when I follow instructions [http://www.mythtv.org/wiki/Troubleshooting:MySQL_will_not_start](http://www.mythtv.org/wiki/Troubleshooting:MySQL_will_not_start),  specifically/etc/init.d/mysql start it returns an error message saying for not found. What am I doing wrong?

---

### Post by tgm4883 on 2014-06-09
How did you install? It doesn't look like the mysql is installed. Check to see if mythtv-backend-master is installed on that box.

---

### Post by patslap on 2014-06-09
It was mythbuntu installation and I configured it to primary backend and frontend and I set it up with all services apart from vnc.

Will have a look tomorrow for mythtv-backend-master installation.

Thanks

---

