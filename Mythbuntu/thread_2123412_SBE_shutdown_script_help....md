---
title: "SBE shutdown script help..."
date: 2013-03-07
forum: Mythbuntu
---

### Post by bonelifer on 2013-03-07
I'm working on a SBE shutdown bash script. All done pretty much by the seat of my google-yahoo fu, since I don't know Bash personally.

Right now it checks for a lock file called "shutdown.lock" and whether or not some one is ssh'd on the default port.  If either of those are true then it returns a return code of rc=1. If rc=0, then it issues, "sudo shutdown -t 30 -h now".  I'd also like to have it check/parse the mythtv xml status port at [http://localhost:6544/xml](http://localhost:6544/xml) and parse out whether the "JobQueue" section has at least one "Program" entry with "hostname="enterprise".

My current script is below. I only need the code to find out if AT LEAST one instance of that hostname is in the JobQueue section.

```
#!/bin/bash

# Get a date/time stamp to add to output
DATE=`date +%F\ %T\.%N`
DATE=${DATE:0:23}
today=`date "+%a %Y/%m/%d"`
rc=0

# See if shutdown.lock exist to prevent shutdown from happening
# while doing maintenace or some other sort of important activity
if test -f /media/Store/incoming/shutdown.lock
then
    echo "$DATE Doing maintenance or something else - LOCK FILE (shutdown.lock) PRESENT  - don't shut down"
    rc=1
fi

sshnum=`netstat -n | grep :22 -c`

if [[ "$sshnum" != "0" ]] ; then
    echo "$DATE Doing maintenance or something else in SSH - don't shut down"
    rc=1
fi

if [[ "$rc" != 1 ]] ; then
    sudo shutdown -t 30 -h now
fi

exit $rc

```

---

