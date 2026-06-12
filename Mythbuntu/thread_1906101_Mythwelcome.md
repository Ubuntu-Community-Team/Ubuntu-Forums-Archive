---
title: "Mythwelcome"
date: 2012-01-08
forum: Mythbuntu
---

### Post by jimyhunt on 2012-01-08
Hello, I am try to use a script with mythwelcome to handle the sleep commands.

But it comes back with the following error, i cant see whats wrong.

/usr/bin/setwakeup.sh: 27: Syntax error: "(" unexpected

```
#!/bin/sh
#
# . Sets ACPI wakeup time
#
# . Input parameters $* are the date/time in any valid format
#
# . Assumes that RTC is localtime and not UTC
#
# . Works whether system sets ACPI wakeup time with either:
#    /proc/acpi/alarm
#    /sys/class/rtc/rtc0/wakealarm
#
# . Corrects schedulting conflicts between recording time and daily
#    wakeup time caused by Mythwelcome (at least in MythDora 5.0)
#
# . Appends status messages to log file: /var/log/mythtv/wakeup.log
#
# . Keeps record of wakeup time in file: /var/log/mythtv/wakeupspec
#    File format is "%s %s"
#        - where first item is epoch seconds of when requested
#        - where second iten is epoch seconds of wakeup time

# Current time and date
NOW=`date "+%b %d %H:%M:%S"`

# Helper prints messages to wakeup log
function logtowakeup()
{
    #echo "$NOW setwakeup - $1" >> /var/log/mythtv/wakeup.log
}

# Rewrite time/date parameter into standardized format. If failure,
# then try again assuming input is in epoch seconds. A second failure
# produces error for invalid date and exits.
DATE=`date -d "$*" "+%F %H:%M:%S" -u`
if [ $? -ne 0 ]; then
    DATE=`date -d "@$*" "+%F %H:%M:%S" -u`
    if [ $? -ne 0 ]; then
    logtowakeup "$* invalid date specification"
        exit 1
    fi
fi

# Log the wakeup request
logtowakeup "$* wakeup requested"

# Current time in seconds
NOWSECS=`date -d "$NOW" "+%s"`

# Requested wakeup time in seconds
SECS=`date -d "$DATE" "+%s" -u`

# If this wakeup setting has been issued within a second of the previous
# one, then mythwelcome is schizophrenic. Actually, this happens because
# there is both a daily wakeup and a scheduled recording. Mythwelcome
# will fire off both requests without predjudice. The earlier of the two
# wakeup times is retained.
if [ -e /var/log/mythtv/wakeupspec ]; then
    set -- `cat /var/log/mythtv/wakeupspec`
    if [ $(($NOWSECS-$1)) -lt 2 ] && [ $SECS -gt $2 ]; then
        LASTDATE=`date -d "@$2" "+%F %H:%M:%S" -u`
        logtowakeup "keeping previous wakeup $LASTDATE"
        exit 0
    fi
fi

# Save wakeup specification
echo "$NOWSECS $SECS" > /var/log/mythtv/wakeupspec

# There are two methods for setting the ACPI wakeup time. Newer Linux
# kernels write epoch time to /sys/class/rtc/rtc0/wakealarm. wakealarm
# must be set zero prior to setting the desired value.
if [ -e /sys/class/rtc/rtc0/wakealarm ]; then
    echo 0 > /sys/class/rtc/rtc0/wakealarm
    echo $SECS > /sys/class/rtc/rtc0/wakealarm
    logtowakeup "$DATE to /sys/class/rtc/rtc0/wakealarm"
fi

```

Its related to the logtowakeup function.

What am i missing? 

Thanks in advance.
Jim

---

### Post by alien878 on 2012-01-10
I think the problem is that logtowakeup has empty {}.  If you want it to do nothing, try sending the output to /dev/null instead of commenting out the line.

---

### Post by jimyhunt on 2012-01-10
Thanks for the reply. Opps that was a error in the post.:oops:

Should be

```

# Helper prints messages to wakeup log function
logtowakeup() {     
         echo "$NOW setwakeup - $1" >> /var/log/mythtv/wakeup.log 
}

```I have updated the commented out code in the function but it still complains.

---

### Post by alien878 on 2012-01-11
Now that is weird....

I tried in cygwin and it worked fine (after removing the comment before the echo).  I tried on ubuntu and I got your error.

I think the problem is that on ubuntu, sh is not sh.  It is a link to dash.  I have no idea why this was done....

If you change it as follows, I think it will work:

```
# Helper prints messages to wakeup log
logtowakeup ()
{
    echo "$NOW setwakeup - $1" >> /var/log/mythtv/wakeup.log
}
```

---

### Post by jimyhunt on 2012-01-16
Thanks. That works. The other option that i was told and have tried that works is to replace /bin/sh to /bin/bash

Due to /bin/sh ISN'T bash, it's             dash.

Hope that help someone else.

Heres my final setwakeup.sh that i am using on Mythbuntu 11.10

```
#!/bin/sh
#
# . Sets ACPI wakeup time
#
# . Input parameters $* are the date/time in any valid format
#
# . Assumes that RTC is localtime and not UTC
#
# . Works whether system sets ACPI wakeup time with either:
#    /proc/acpi/alarm
#    /sys/class/rtc/rtc0/wakealarm
#
# . Corrects schedulting conflicts between recording time and daily
#    wakeup time caused by Mythwelcome (at least in MythDora 5.0)
#
# . Appends status messages to log file: /var/log/mythtv/wakeup.log
#
# . Keeps record of wakeup time in file: /var/log/mythtv/wakeupspec
#    File format is "%s %s"
#        - where first item is epoch seconds of when requested
#        - where second iten is epoch seconds of wakeup time

# Current time and date
NOW=`date "+%b %d %H:%M:%S"`

# Helper prints messages to wakeup log
logtowakeup()
    {
    echo "$NOW setwakeup - $1" >> /var/log/mythtv/wakeup.log
    }

# Rewrite time/date parameter into standardized format. If failure,
# then try again assuming input is in epoch seconds. A second failure
# produces error for invalid date and exits.
DATE=`date -d "$*" "+%F %H:%M:%S" -u`
if [ $? -ne 0 ]; then
    DATE=`date -d "@$*" "+%F %H:%M:%S" -u`
    if [ $? -ne 0 ]; then
    logtowakeup "$* invalid date specification"
        exit 1
    fi
fi

# Log the wakeup request
logtowakeup "$* wakeup requested"

# Current time in seconds
NOWSECS=`date -d "$NOW" "+%s"`

# Requested wakeup time in seconds
SECS=`date -d "$DATE" "+%s" -u`

# If this wakeup setting has been issued within a second of the previous
# one, then mythwelcome is schizophrenic. Actually, this happens because
# there is both a daily wakeup and a scheduled recording. Mythwelcome
# will fire off both requests without predjudice. The earlier of the two
# wakeup times is retained.
if [ -e /var/log/mythtv/wakeupspec ]; then
    set -- `cat /var/log/mythtv/wakeupspec`
    if [ $(($NOWSECS-$1)) -lt 2 ] && [ $SECS -gt $2 ]; then
        LASTDATE=`date -d "@$2" "+%F %H:%M:%S" -u`
        logtowakeup "keeping previous wakeup $LASTDATE"
        exit 0
    fi
fi

# Save wakeup specification
echo "$NOWSECS $SECS" > /var/log/mythtv/wakeupspec

# There are two methods for setting the ACPI wakeup time. Newer Linux
# kernels write epoch time to /sys/class/rtc/rtc0/wakealarm. wakealarm
# must be set zero prior to setting the desired value.
if [ -e /sys/class/rtc/rtc0/wakealarm ]; then
    echo 0 > /sys/class/rtc/rtc0/wakealarm
    echo $SECS > /sys/class/rtc/rtc0/wakealarm
    logtowakeup "$DATE to /sys/class/rtc/rtc0/wakealarm"
fi

```

---

