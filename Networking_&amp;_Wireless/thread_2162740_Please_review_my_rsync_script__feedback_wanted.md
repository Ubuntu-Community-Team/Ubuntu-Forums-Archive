---
title: "Please review my rsync script : feedback wanted"
date: 2013-07-15
forum: Networking &amp; Wireless
---

### Post by m79b01 on 2013-07-15
These are the first scripts I have wrote.  I am looking for feedback on anything I could have done better.  They are functional as is.

The first script only starts the xterm and the fires up my rsync script.

```

#!/bin/bash
#
#This is only intended to start the backup job at /home/mike/scripts/server_check.sh
JOB1=/home/mike/scripts/server_check.sh
#set -x
xterm -eH "bash $JOB1;bash"
exit
```

This is the one that checks my server and gives me a few options.

```

#!/bin/bash
#
#This is the hardware address for wakeup
HDW=(mac address here)

#This is what you call your server
VAR1=DVR

#this is what you want to copy
FROM1=/home/mike

#this is where you want it to go
DEST1=/home/dvr3/

#This is the destinaiton address 
COMP1=(ip address here)

#this is the user on the destination
USR1=dvr3

#this is a compilation of above
REMOTE1="$USR1@$COMP1:$DEST1"

#this is the exclude file
EXCLUDE1=$FROM1/scripts/sync/rsync_exclude

#this is the rsync log file
LOG1=$FROM1/scripts/sync/rsync_log

#This is the log file for this script
LOG2=$FROM1/scripts/test_ping.log

#This is the rsync command it is waiting for the server to be awake
RSNC="rsync -avhtPO --stats --timeout=600 --log-file=$LOG1 --exclude-from=$EXCLUDE1 -e ssh $FROM1/ $REMOTE1"

#set -x

#This part will take care of the server if it is off
echo "
---------------------------------Hello $USER---------------------------------
"
echo "Just wait I am checking to see if the $VAR1 is awake

$(date)
"
echo "Server test pings issued at $(date)" >> $LOG2
ping=$(ping -c 2 "$COMP1" 2>&1| grep "% packet" | cut -d" " -f 6 | tr -d "%")
  if [ "$ping" = "+2" ]; then
  echo "The $VAR1 is off!

Would you like to start it???
    "
  echo "$COMP1 is not running" >> $LOG2
  while true; do
      read this
      echo
  case $this in
    yes)
    echo "Alright I'll try sending the wake command to $VAR1

Now you need to wait until the $VAR1 is running
"
    command wakeonlan $HDW
    command sleep 180;$RSNC
    exit
    ;;
    no)
    echo "Goodbye
        "
    exit
    ;;
    *)
    echo "You know you need to enter "yes" or "no", then press [ENTER].

    Why do you keep doing it wrong?"
    ;;
  esac
  done
#This part runs if the server was already on
else
echo "We are already connected!!

Now I will backup
"
command $RSNC
    echo "
Thats finally done!
"
    echo " === Complete ===" >> $LOG2
echo " === Last Sync Completed at $date ===" >> $LOG2
fi
exit
```

Please any feedback would be great I am looking to improve my abilities.

---

