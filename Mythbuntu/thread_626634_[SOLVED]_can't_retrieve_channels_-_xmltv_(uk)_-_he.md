---
title: "[SOLVED] can't retrieve channels - xmltv (uk) - help?"
date: 2007-11-29
forum: Mythbuntu
---

### Post by arjay1 on 2007-11-29
OK - installed mythbuntu from an iso - all looks fine except for only one or two remote keys for haup prv150 working (separate post for this)

I have tried to get channels using xmltv (tv_grab_uk_rt) in the video source page in the backend setup.  But even before I switch to the terminal it gives the error message "can't retieve channel information - see terminal".  When I switch to the terminal, I see:

```
2007-11-29 15:53:08.808 Using runtime prefix = /usr
2007-11-29 15:53:08.831 New DB connection, total: 1
2007-11-29 15:53:08.924 Connected to database 'mythconverg' at host: localhost
2007-11-29 15:53:08.927 New DB connection, total: 2
2007-11-29 15:53:08.928 Connected to database 'mythconverg' at host: localhost
2007-11-29 15:53:08.928 Updating source #1 (skybox) with grabber tv_grab_uk_rt
2007-11-29 15:53:08.928 No channels are configured to use grabber.
2007-11-29 15:53:08.937 Grabber has capabilities: baseline manualconfig cache preferredmethod 
2007-11-29 15:53:08.947 Grabber prefers method: allatonce
2007-11-29 15:53:08.948 New DB connection, total: 3
2007-11-29 15:53:08.948 Connected to database 'mythconverg' at host: localhost
2007-11-29 15:53:08.949 Grabber Command: nice tv_grab_uk_rt --config-file '/home/richard/.mythtv/skybox.xmltv' --output /tmp/mythmovsy4
2007-11-29 15:53:08.949 ----------------- Start of XMLTV output -----------------

All data is the copyright of the Radio Times website
<http://www.radiotimes.com> and the use of this data
is restricted to personal use only.

Radio Times reports available listings for 54 channels.

Retrieving channels
Bad line seen in RT channels.dat: <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" at /usr/local/bin/tv_grab_uk_rt line 223.
2007-11-29 15:53:09.323 ------------------ End of XMLTV output ------------------
2007-11-29 15:53:09.324 FAILED:  xmltv returned error code 65280.
Error in 1:1: unexpected end of file
2007-11-29 15:53:09.325 Updating icons for sourceid: 1
2007-11-29 15:53:09.326 New DB connection, total: 4
2007-11-29 15:53:09.326 Connected to database 'mythconverg' at host: localhost
2007-11-29 15:53:09.327 No programs found in data.
2007-11-29 15:53:09.329 New DB connection, total: 5
2007-11-29 15:53:09.333 Connected to database 'mythconverg' at host: localhost
2007-11-29 15:53:09.334 Failed to fetch some program info
2007-11-29 15:53:09.334 Adjusting program database end times.
2007-11-29 15:53:09.334     0 replacements made
2007-11-29 15:53:09.334 Marking generic episodes.
2007-11-29 15:53:09.335     Found 0
2007-11-29 15:53:09.335 Marking repeats.
2007-11-29 15:53:09.335     Found 0
2007-11-29 15:53:09.336 Unmarking new episode rebroadcast repeats.
2007-11-29 15:53:09.336     Found 0
2007-11-29 15:53:09.336 Marking episode first showings.
2007-11-29 15:53:09.336     Found 0
2007-11-29 15:53:09.336 Marking episode last showings.
2007-11-29 15:53:09.336     Found 0
2007-11-29 15:53:09.337 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2007-11-29 15:53:09.340 Connecting to backend server: 192.168.1.100:6543 (try 1 of 5)
2007-11-29 15:53:09.340 Using protocol version 31
2007-11-29 15:53:09.439 mythfilldatabase run complete.
2007-11-29 15:53:09.440 DataDirect: Deleting temporary files
richard@tranquil:~$ 
```


I have downloaded and installed the latest xmltv package (.50) but still no good get the same error line:
@Bad line seen in RT channels.dat: <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" at /usr/local/bin/tv_grab_uk_rt line 223.

Tried entering "tv_grab_uk_rt --configure" directly into a terminal but got the same thing.

Maybe I am doing something silly here but have install mythtv successfully before a year ago.  Google and forum searches don't turn up anything relevant.

TIA

Richard

---

### Post by roseway on 2007-11-29
Maybe I'm missing something here, but the PVR 150 is an analogue tuner, so you're not going to get the 54 channels mentioned above, just the 4 or 5 analogue ones.

---

### Post by arjay1 on 2007-11-29
> **roseway said:**
> Maybe I'm missing something here, but the PVR 150 is an analogue tuner, so you're not going to get the 54 channels mentioned above, just the 4 or 5 analogue ones.

Thanks for responding so quickly.  Sorry - my bad.  I should have explained that I am using a sky digibox which has hundreds of channels.

Your point about the "54 channels" in the error message is therefore doubly strange?

I have followed the procedure i always use to set up the xmltv epg - so not sure what I have done wrong this time.  In fact i had mythdora successfully up and running yesterday and there was no problem in downloading the channels from radio times etc.  The problem I had with mythdora is it would not recognise and operate the pvr150's remote.  Also I just cannot get on with the rpm business. It is positively antediluvian compared to apt!

Thanks again

Richard

EDIT - my guess is that the 54 channels is the number the script read up to the "BAD LINE" when it then stopped responding - hence only 54??

---

### Post by mythbird on 2007-11-29
Hi,  I have had mythfilldatabase working for over 4 weeks, but now also get the same message.  I think the service is down, if you take a look at :

[http://xmltv.radiotimes.com/xmltv/channels.dat](http://xmltv.radiotimes.com/xmltv/channels.dat)

There is currrently not a channels list, so therefore, i assume, it can't currently work.  When the service reappears, I guess we'll both start working again.

---

### Post by arjay1 on 2007-11-30
Yup - that's it.  Thanks for the info and the link.  The site is back up now.

What a crappy system xmltv is.  I know it is free but I would rather pay a little something and have a reliable epg that actually worked.  This is the third time I have tried mythtv and every time there has been a problem with installing and/or updating the epg for the UK.  I am sick and tired of it.  I looked at birtles/bleb or whatever it is and it looked as complicated as the normal tv-grab.

Is there anything better?  IMHO mythtv will never be a killer app until those that be, recognise that many if not most mythtv users don't live in the US.......

---

