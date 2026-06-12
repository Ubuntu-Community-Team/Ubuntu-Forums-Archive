---
title: "Mytharchive mydata.xml job file doesn't look right"
date: 2012-03-23
forum: Multimedia Software
---

### Post by abcMikedef on 2012-03-23
I'm trying to run Mytharchive from the command line.  I started a Mytharchive from Mythfrontend and while running copied /var/lib/mytharchive/temp/config/mydata.xml into /tmp/config.   When I run /python/usr/share/mythtv/mytharchive/scripts/mythburn.py I receive the error:

***********************************
ERROR: Job file doesn't look right!
***********************************

Mydata.xml looks to be fine containing:
<!DOCTYPE NATIVEARCHIVEJOB>
<nativearchivejob>
    <job>
        <media>
            <file title="Touch" type="recording" delete="0" filename="/var/lib/mythtv/recordings/1181_20120322210000.mpg"/>
        </media>
        <options erasedvdrw="0" doburn="1" mediatype="3" dvdrsize="1057662924" savedirectory="/tmp/config" createiso="0"/>
    </job>
</nativearchivejob>

Manually created mydata.xml files process further but don't produce desired results hence why I'm trying to start with a mythfrontend created mydata.xml

Thoughts?

---

### Post by abcMikedef on 2012-03-30
I was trying to do a native file export.  Mytharchivehelper handles native exports -- not mytharchive/mythburn.py.  So, of course mythburn.py doesn't like mydata.xml

---

