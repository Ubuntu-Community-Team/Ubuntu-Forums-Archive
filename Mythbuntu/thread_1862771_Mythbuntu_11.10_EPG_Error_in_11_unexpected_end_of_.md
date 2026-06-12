---
title: "Mythbuntu 11.10 EPG Error in 1:1: unexpected end of file"
date: 2011-10-17
forum: Mythbuntu
---

### Post by map7 on 2011-10-17
I've just installed Mythbuntu 11.10 from scratch and I'm trying to use 'shepherd' as my grabber like I have always done since Mythbuntu 8.04. 

I've setup my video source as 'melb' short for Melbourne, Australia and I've run the following commands after my initial channel scan:

$ shepherd --configure
$ tv_grab_au --notimetest

Shepherd collects all the info and stores it in .shepherd/output.xmltv.

If I now try and run
$ mythfilldatabase --refresh-all

It fails with the following error message:

```
2011-10-17 19:15:59.923 Using runtime prefix = /usr
2011-10-17 19:15:59.924 Using configuration directory = /home/bender/.mythtv
2011-10-17 19:15:59.924 Empty LocalHostName.
2011-10-17 19:15:59.924 Using localhost value of bender
2011-10-17 19:15:59.926 New DB connection, total: 1
2011-10-17 19:15:59.929 Connected to database 'mythconverg' at host: localhost
2011-10-17 19:15:59.930 Closing DB connection named 'DBManager0'
2011-10-17 19:15:59.931 Connected to database 'mythconverg' at host: localhost
2011-10-17 19:15:59.932 Current locale en_AU
2011-10-17 19:15:59.932 No locale defaults file for en_AU, skipping
2011-10-17 19:15:59.933 Loading en_us translation for module mythfrontend
2011-10-17 19:15:59.934 Current MythTV Schema Version (DBSchemaVer): 1264
2011-10-17 19:15:59.936 New DB connection, total: 2
2011-10-17 19:15:59.936 Connected to database 'mythconverg' at host: localhost
2011-10-17 19:15:59.937 Updating source #1 (tv) with grabber tv_grab_au
2011-10-17 19:15:59.937 Found 20 channels for source 1 which use grabber
2011-10-17 19:16:00.136 Grabber has capabilities: baseline manualconfig preferredmethod 
2011-10-17 19:16:00.323 Grabber prefers method: allatonce
2011-10-17 19:16:00.324 New DB connection, total: 3
2011-10-17 19:16:00.324 Connected to database 'mythconverg' at host: localhost
2011-10-17 19:16:00.325 XMLTV config file is: /home/bender/.mythtv/tv.xmltv
2011-10-17 19:16:00.325 New DB connection, total: 4
2011-10-17 19:16:00.325 Connected to database 'mythconverg' at host: localhost
2011-10-17 19:16:03.303 Error in 1:1: unexpected end of file
2011-10-17 19:16:03.303 IconData: Updating icons for sourceid: 1
2011-10-17 19:16:03.304 New DB connection, total: 5
2011-10-17 19:16:03.304 Connected to database 'mythconverg' at host: localhost
2011-10-17 19:16:03.305 No programs found in data.
2011-10-17 19:16:03.306 Data fetching complete.
2011-10-17 19:16:03.306 Adjusting program database end times.
2011-10-17 19:16:03.306     0 replacements made
2011-10-17 19:16:03.306 Marking generic episodes.
2011-10-17 19:16:03.307     Found 0
2011-10-17 19:16:03.307 Fudging non-unique programids with multiple parts.
2011-10-17 19:16:03.307     Found 0
2011-10-17 19:16:03.307 Marking repeats.
2011-10-17 19:16:03.308     Found 0
2011-10-17 19:16:03.308 Unmarking new episode rebroadcast repeats.
2011-10-17 19:16:03.309     Found 0
2011-10-17 19:16:03.309 Marking episode first showings.
2011-10-17 19:16:03.309     Found 0
2011-10-17 19:16:03.309 Marking episode last showings.
2011-10-17 19:16:03.310     Found 0
2011-10-17 19:16:03.311 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2011-10-17 19:16:03.315 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-10-17 19:16:03.315 Using protocol version 63
2011-10-17 19:16:03.319 Received a remote 'Clear Cache' request
2011-10-17 19:16:04.319 mythfilldatabase run complete.
2011-10-17 19:16:04.319 DataDirect: Deleting temporary files

```


However, if I run this command
$ mythfilldatabase --file 1 .shepherd/output.xmltv

It works!

Why is this so?

I've always just ran mythfilldatabase --refresh-all and had it work. Is it missing a file?
Should there be a melb.xmltv file in my .mythtv, because there isn't any such file?

---

### Post by SL666 on 2011-12-10
I have this exact same issue (thanks for your little work around there).

Ive had Shepherd and Mythtv running fine for about 3 years? and this issue just started randomly a few weeks ago.

Mines also looking for a config file that doesn't exist - and that i don't know what the content should be.

If anyone has any ideas - im happy to investigate.

---

### Post by paulsmith99 on 2012-10-26
I had this problem and found it ran successfully as root so I did some digging. Here's the detail but if you want to fix it just look at the end of this post.

The backend runs as mythtv and therefore starts mythfilldatabase as that user.

Adding xmltv debugging output to the command will show more info the next time it runs, so add -v xmltv in the mythfilldatabase command line options.

Rather than wait until the next scheduled event, log on as the mythtv user. I do this rather than try to figure out what the mythtv user's password is:

```

sudo -i

```
... and type the password for your user, followed by a switch user once you've logged in as super user.
```

su - mythtv

```

Now, as the mythtv user, run the command that the backend would do overnight (with extra debugging though):

```

mythfilldatabase --only-update-channels --loglevel debug -v xmltv

```

This will show some extra output, specifically, this sort of line:

```

2012-10-26 18:15:08.927109 I  Grabber Command: nice tv_grab_uk_rt --config-file '/home/mythtv/.mythtv/Freesat.xmltv' --output /tmp/mythRYygDM
2012-10-26 18:15:06.824876 I  ----------------- Start of XMLTV output -----------------
2012-10-26 18:15:07.624255 I  ------------------ End of XMLTV output ------------------
2012-10-26 18:15:07.625517 E  FillData: xmltv returned error code 13
2012-10-26 18:15:07.626464 E  Error in 1:1: unexpected end of file

```

To see more detail on what 'error code 13' is about, you need to run the above grabber command yourself (make sure you delete the temporary file first or use another name):

```

nice tv_grab_uk_rt --config-file '/home/mythtv/.mythtv/Freesat.xmltv' --output /tmp/some_file

```

There'll be some output from the grabber but it ends with this sort of error line:

```

http://xmltv.radiotimes.com/xmltv/1544.dat: Failed to write to /home/paul/.xmltv/cache/cee7045083ec249fcc825ddc15b840fa.tmp15724 at /usr/share/perl5/HTTP/Cache/Transparent.pm line 379.

```

This shows the problem. It is trying to write cache files to another user's home dir.

So this means that there is a config file that has the other user called 'paul' instead of 'mythtv'...

```

find ~mythtv/.mythtv -exec grep -l paul {} \;

```

...reveals...

```

/home/mythtv/.mythtv/Freesat.xmltv
/home/mythtv/.mythtv/Freeview.xmltv

```

Edit these files and change the cache settings from this:
```

cachedir=/home/paul/.xmltv/cache

```

to this:
```

cachedir=/home/mythtv/.xmltv/cache

```

Rest assured that when mythfilldatabase runs again it will work - or encounter another error with your setup :wink:.

I'm not sure how it got in that state but this fixes the issue. :P

---

