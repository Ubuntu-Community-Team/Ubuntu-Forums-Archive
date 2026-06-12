---
title: "Modified Commflag job never completing"
date: 2009-08-29
forum: Mythbuntu
---

### Post by TrevE on 2009-08-29
I am trying to get mythnuv2mkv working by automatically loading the commercial skip list to cut list when Flag Commercials is called, then run a User Job for mythnuv2mkv.  The Flag Commercials job never seems to show complete in the backend status, i have to kill the backend to stop it.  Here is what I have setup:

I created a file called /mnt/recordings/CommFlag.sh File contains:
```

#!/bin/sh
VIDEODIR=$1
FILENAME=$2
VERBOSE=$3
mythcommflag -f $VIDEODIR/$FILENAME -V $VERBOSE
ERROR=$?
if [ $ERROR -gt 126 ]; then
echo "Commercial flagging failed for  $1 $2 with error $ERROR"
exit $ERROR
fi
mythcommflag --gencutlist -f $VIDEODIR/$FILENAME
ERROR=$?
if [ $ERROR -ne 0 ]; then
echo "Copying cutlist failed for  $1 $2  with error $ERROR"
exit $ERROR
fi
exit 0

```

In mythweb under settings I set JobQueueCommFlagCommand to: 
/mnt/recordings/CommFlag.sh %DIR% %FILE% 8

I can run this manually and it runs and exits fine. Here is the output if it helps, it all looks normal to me:
```

trevor@mediapc:/mnt/recordings$ ./CommFlag.sh /mnt/recordings/ 1074_20090829093000.nuv 8

MythTV Commercial Flagger, started at Sat Aug 29 16:46:54 2009
Flagging commercial breaks for:
ChanID  Start Time      Title                                      Breaks
------  --------------  -----------------------------------------  ------
1074    20090829093000  Celebrity Deathmatch                        99%/4      

Finished commercial break flagging at Sat Aug 29 16:48:23 2009

2009-08-29 16:48:23.853 Using runtime prefix = /usr
2009-08-29 16:48:23.853 Empty LocalHostName.
2009-08-29 16:48:23.857 New DB connection, total: 1
2009-08-29 16:48:23.859 Closing DB connection named 'DBManager0'
2009-08-29 16:48:23.860 New DB connection, total: 2
trevor@mediapc:/mnt/recordings$ 

```

When I run Flag Commercials from mythtv it seams to create the commercial skip list, generate the cutlist, then hang at Status Running forevor.  Any ideas?

---

