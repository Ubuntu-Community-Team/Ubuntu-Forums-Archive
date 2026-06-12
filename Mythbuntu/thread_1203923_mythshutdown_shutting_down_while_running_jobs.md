---
title: "mythshutdown shutting down while running jobs ?"
date: 2009-07-04
forum: Mythbuntu
---

### Post by laffinet on 2009-07-04
I'm using the following scripts to shut down my machine when idle and bringing it back up for recordings and other predetermined times.

MythSetWakeup
```
#!/bin/sh
# MythSetWakeup

echo 0 > /sys/class/rtc/rtc0/wakealarm
echo $1 > /sys/class/rtc/rtc0/wakealarm
```

MythShutdown
```
#!/bin/sh -x
# Shutdown the Mythbox

DAY=$(date +%u)
HOUR=$(date +%k)
MIN=$(date +%M)

# wake-up time for scheduled recording
WUP=$(cat /sys/class/rtc/rtc0/wakealarm)


# generic wake-up time
#   Mo-Fr @ 6.30am & 4.30pm
if [ $DAY -eq 5 ] && [ $HOUR -gt 16 ];then
	GWU=$(date -d '+ 3 days 6:30' +%s)
	elif [ $DAY -le 5 ] && [ $HOUR -ge 6 ] && [ $HOUR -lt 16 ];then
		GWU=$(date -d '16:30' +%s)
		elif [ $DAY -le 5 ] && [ $HOUR -eq 16 ] && [ $MIN -lt 30 ];then
			GWU=$(date -d '16:30' +%s)
			elif [ $DAY -le 4 ] && [ $HOUR -gt 16 ];then
				GWU=$(date -d '+ 1 day 6:30' +%s)
				elif [ $DAY -eq 6 ];then
					GWU=$(date -d '+ 2 days 6:30' +%s)
					elif [ $DAY -eq 7 ];then
						GWU=$(date -d '+ 1 day 6:30' +%s)
else
	GWU=$(date -d '06:30' +%s)
fi


# if there is no scheduled recording or
#   next generic wake-up is earlier
#   then set to that time
 if [ -z $WUP ] || [ $GWU -lt $WUP ] ; then
   echo 0 > /sys/class/rtc/rtc0/wakealarm
   echo $GWU > /sys/class/rtc/rtc0/wakealarm
 fi

mythshutdown -q
```

MythShutdownCheck
```
#!/bin/sh -x
# Check generic running time to shutdown

DAY=$(date +%u)
HOUR=$(date +%k)
MIN=$(date +%M)

if [ $DAY -le 5 ] && [ $HOUR -lt 6 ]; then
   exit 0
elif [ $DAY -le 5 ] && [ $HOUR -eq 6 ] && [ $MIN -lt 30 ]; then
   exit 0
elif [ $DAY -le 5 ] && [ $HOUR -ge 8 ] && [ $HOUR -lt 16 ]; then
   exit 0
elif [ $DAY -le 5 ] && [ $HOUR -eq 16 ] && [ $MIN -lt 30 ]; then
   exit 0
elif [ $DAY -le 5 ] && [ $HOUR -ge 20 ]; then
   exit 0
elif [ $DAY -ge 6 ]; then
   exit 0
else
   exit 1
fi
```

I thought that using mythshutdown in the shutdown script would prevent the machine from going down while running jobs (eg transcoding etc.). However that is not the case. I've got a few user jobs running yet the machine happily shuts down. What am I missing ?

---

### Post by laffinet on 2009-07-05
Bump.

---

### Post by joho500 on 2009-07-05
I use a script I found her on the forum and adjusted it a bit. It checks for an active remote connection and for running programs and I've added a check for a VNC connection. You can add a check for the transcoding program yourself.
Hope this helps you.

Cheers,
Joost

```
#!/bin/sh
#
# MythShutdownCheck
#
# Cancels shutdown when:
#	1. mythcommflag or mythfilldatabase job is running
#	2. any other user is logged in before idle shutdown
#	3. VNC connection exits
#	   Add option -accept <cmd> to x11vnc command line in /usr/share/mythbuntu/session.sh
#	   where <cmd> can be any script you want. This sets environment variable $RFB_MODE 
#	   to 'accept' when a connection is established.
#	4. time is during afternoon/evening or weekend
#
# returns "1" if yes, cancels shutdown
# returns "0" if ok to shutdown
#

# check running programs
# to not shutdown during mythcommflag process, uncomment the following line
ps ax | grep -v grep | grep -q mythcommflag && exit 1
# the same when mythfilldatabase is running
ps ax | grep -v grep | grep -q mythfilldatabase && exit 1

# check for active *remote* login?
#echo  >> ~/loggedin.log
if last | head | grep "pts/.*still logged in" >> ~/loggedin.log
then
   exit 1
fi

# check for VNC connection
if [$RFB_MODE = "accept"]; then
   exit 1
fi


# only shutdown at certain times
DAY=$(date +%u)
HOUR=$(date +%k)

#Mon-Thu 8.00-16.00 ok to shutdown
#Mon-Thu 23.00-24.00 ok to shutdown
#Mon-Fri 0.00-6.00 ok to shutdown
#Sat-Sun 0.00-7.00 ok to shutdown
if [ $DAY -le 4 ] && [ $HOUR -ge 8 ] && [ $HOUR -lt 16 ]; then
   exit 0
elif [ $DAY -le 4 ] && [ $HOUR -ge 23 ]; then
   exit 0
elif [ $DAY -le 5 ] && [ $HOUR -ge 0 ] && [ $HOUR -lt 6 ]; then
   exit 0
elif [ $DAY -ge 6 ] && [ $HOUR -lt 7 ]; then
   exit 0
else
   exit 1
fi


```

---

### Post by laffinet on 2009-07-06
Thanks, I will try that.

Since I'm trying to learn a bit about scripts and linux in general, can you explain in detail what this bit:
```
ps ax | grep -v grep | grep -q mythcommflag
```

does ? I guess it somehow checks for a process mythcommflag, but how exactly (grep is a bit of a mystery for me...) ?

Thanks.

BTW I also found a script mythidle.pl [here]("http://www.xpmediacentre.com.au/community/225797-post308.html") which does something very similar.

---

### Post by SiHa on 2009-07-06
```
ps ax
```
**ps** lists running processes, the **ax** switch forces it do display **all** processes.
```
|
``` This is a 'pipe' and it pipes the output into the command that follows, in this case
```
grep -v grep
``` **grep** is a powerful string-matching tool, and will return all instances of the string that follows, except when the **-v** switch is used, the search is inverted, so it returns all lines in the piped output of ps that **don't **contain the search string - in this case 'grep'.

This is the bit that confused me when I first started to look at this stuff. Some switches for **ps** also include the calling commandline for the process in the output, I assume **ax** is one of those. So, eg ```
ps ax | grep mythcommflag
``` would return **two** hits (assuming mythcommflag were running). One for the query and one for the mythcommflag process. If mythcommflag weren't running you would still get a hit for the query. So it always produces a positive hit - not much use. **grep -v grep** simply removes the commandline from the output of the **ps** command.
```
| grep -q mythcommflag
```

Takes the filtered output of the preceding grep operation and searches for all lines containg 'mythcommflag'. The **-q** switch tells it to suppress any output just return the appropriate return code (0 for a match, 1 for no match)

Two points.
1) I think the ax switch is left there for legacy support, I don't think it is officially supported.

2) Myself I prefer ```
ps -A
``` specifically because it doesn't return the commandline, so the required command is less messy.```
ps -A | grep mythcommflag > null
``` will do. Although, I suppose I could use the -q switch for grep to neaten it up further and remove the redirect of the output to the null device.



When trying to decipher a command I've found in a script, I've found the manpages to be extremely useful,for example.
```
man ps
``` will print out the manual for **ps** along with all supported switches.

---

### Post by laffinet on 2009-07-06
Thanks for the explanation. Just another question:

```
| grep -q mythcommflag
```

So this returns a 0 or 1, depending on wether mythcommflag was found or not. And then what ?
Ultimately the script needs to return 0 if shutdown is ok, and 1 if not ok, so if mythcommflag is found it should return 1. 
With the above returning 0 if mythcommflag is found, how does this result in a 1 from the script? I know that the full line is
```
ps ax | grep -v grep | grep -q mythcommflag && exit 1
```
which includes the "&& exit 1" at the end but when does this get executed and when not ? Is it the case that the && exit 1 bit gets executed only if the "ps...mythcommflag" bit returns 0 ?

---

### Post by SiHa on 2009-07-07
> Is it the case that the && exit 1 bit gets executed only if the "ps...mythcommflag" bit returns 0 ? Yes - here's why.

When any command executes it returns an error code. If it completed sucecssfully it will return '0'. If it is unsuccessful it returns a non-zero value (doesn't have to be '1').

**&&** is the Bash logical AND operator, and a quirk of the Bash shell (possibly all, I don't know) is that it will only evaluate the second term in a logical expression if it needs to.

In other words if the first term is true (returns a '0') the second term will be evaluated, and if it is a command it must be run in order for it to return a value. If the first term is false, it doesn't need to go any further to know that the result of the **AND** is false, so the second argument is never eveluated and the command is not run.

So, if > grep -q mythcommflag returns a '0' (ie, mythcommflag is running) the ```
exit 1
``` is executed, the script exits with a return value of '1' - not safe to shutdown. Otherwise it is ignored and the sript will run on to the next line.

---

### Post by joho500 on 2009-07-07
Thanks, SiHa, for that explanation. I just used the code but now I understand why it works. O:) Never to old to learn.

Cheers,
Joost

---

### Post by SiHa on 2009-07-07
I've done plenty of cut'n'paste in my time as well. The problem comes when you need to customize someone else's scripts, so I've had to learn a few bits. Google + manpages usually provide enough information to figure out what's going on.

---

### Post by laffinet on 2009-07-07
Thanks a lot for the very detailed and helpful explanation. While I'm quite happy to copy and paste and use other people's scripts I always like to know what I'm doing ! Plus it never hurts to learn a bit more about linux. 
Thanks again.

---

