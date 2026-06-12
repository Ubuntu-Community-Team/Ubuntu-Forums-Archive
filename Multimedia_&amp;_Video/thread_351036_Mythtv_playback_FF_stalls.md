---
title: "Mythtv playback FF stalls"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by Panhead Bill on 2007-02-01
I'm sorting out some things with my Myth box.

  When I am playing back a recorded program and hit the fast forward the program will fast forward for about 3 seconds and then the image will freeze. 

 (EDIT)  More accurately; at 3X the program advances properly, but anything faster will incur the 3 second limit. (END EDIT) 

If I hit play the program resumes from that frozen point.

  Speeding up or slowing down will keep the forwarding active IF I hit either the FF or slow button within the 3 second limit, but only for another 3 seconds.

Where do I start looking?

Panhead Bill

---

### Post by Homer on 2007-09-04
I have exactly the same problem on a fresh new install (Ubuntu 7.04 with MythTV 0.20.2)...

On Ubuntu 6.06.1 with MythTV 0.20, It worked...

Did you find a fix ?

---

### Post by Homer on 2007-09-04
> **Homer said:**
> I have exactly the same problem on a fresh new install (Ubuntu 7.04 with MythTV 0.20.2)...

On Ubuntu 6.06.1 with MythTV 0.20, It worked...

Did you find a fix ?

Ok, found the blem :)

[http://forum.byopvr.com/dvr/index.php/topic,4332.0.html](http://forum.byopvr.com/dvr/index.php/topic,4332.0.html)

---

### Post by twkisner on 2007-09-04
I know this won't sound right, but this is not really your problem.  Your SQL database is likely hosed up.

start with:

<code>
sudo mysqlcheck -r -u mythtv -yoursqlpassword mythconverg
</code>

if that doesn't work search for (and download) the perl script "optimize_mythdb.pl"

and run:

<code>
sudo perl optimize_mythdb.pl
</code>

This will fix yourtroubles.

I went through fits with this same problem, even re-installing my mythtv box until I came across this.  When my wife has trouble, she just hits the reset button (I can't tell her to ssh into the box and reset x-windows).  This hoses the SQL database, which stores the frame information, which breaks fast forwarding and ocassionally all of the recorded programs.

---

### Post by roazena on 2007-09-05
BTW, if you can remember the MySQL password in the General setup screen, then log into phpmyadmin's web interface as mythtv using that password, you can do the same thing AND repair the table if it's corrupt. This worked beautifully for me, and I didn't even have to restart the frontend.

---

### Post by timgrin on 2007-11-20
I am having the same problem as this in Gutsy using myth 0.20.20070821-1 

Any livetv recordings are not commflaged and trying to fast forward them faster than 3x speed results in choppy playback, audio "blurping" and sometimes freezing of the frontend

Recorded tv shows seem to work fine (at least the ones that have been commflagged) - is there anyway to automatically commflag livetv as well as scheduled recorded showings.

a tail of /var/log/mythtv/mythfrontend.log gives multiple times per second this error:

2007-11-20 23:27:34.522 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!

any ideas - it is really annoying

---

### Post by timgrin on 2007-11-20
I should also mention repairing tables and optimising tables did not work, neither did emptying the hard drive of all the unwanted recordings, nor did restarting mythtv or rebooting

---

