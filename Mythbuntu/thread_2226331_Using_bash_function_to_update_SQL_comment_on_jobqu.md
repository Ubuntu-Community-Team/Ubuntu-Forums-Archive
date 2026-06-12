---
title: "Using bash function to update SQL comment on jobqueue"
date: 2014-05-26
forum: Mythbuntu
---

### Post by bonelifer on 2014-05-26
I have a userjob in bash. I want to use a function to update the comment field for jobqueue.  Not sure I understand why the function doesn't work.

[http://pastebin.com/jddj1y5z](http://pastebin.com/jddj1y5z)

note: fixed and updated the pastebin for anyone looking for an example bash userjob script.

---

### Post by blm-ubunet on 2014-05-26
What error messages do you get if you invoke from cmd line (with all parameters) ?

You could pass the "JOBID" to the script & then use that to uniquely identify/update dBase.
Can also send message to FE with mythutil (notifications).

Can get the dBase credentials direct from config.xml.

The mythtv BE job command variable %STARTTIME% probably has to become %STARTTIMEUTC% (in more recent mythtv)..

I have had to quote the "time" due to spaces. e.g. from my script:
```
cuts=( `echo "select type,mark from recordedmarkup where chanid=$CHANID and starttime=\"$STARTTIME\" \

              and type in ($MARKTYPES) order by mark;" | mysql -N $USERPASSTABLE ` ) 
```

In my example $STARTTIME is value passed by %STARTTIMEUTC%.


A better way to update status could be by BE services API.
A delete rec example:
curl --data StartTime=2013-05&#8211;24T22:30:00 --data ChanId="1024" localhost:6544/Dvr/DeleteRecording

---

### Post by bonelifer on 2014-05-26
The body of the script works(ie the transcode/handbrakecli part goes through, finishes). In fact it's only the "fnUpdateStatus" function that's not working.  I'm trying to figure out why the bash function isn't working. This isn't anything special. I'm not trying to get output from the utils, I'm just trying to push a "comment" to the db, to tell me where in the script it's at. These aren't error comments, just predetermined "I"m here in the script" type comments.  The comments are being pushed just right before any of the utils are started.

---

### Post by steeldriver on 2014-05-26
What exactly is happening when you try to run it?

Are you intending for the shell to expand variables like $1 and $CHAN before writing them to the temp file? if so, I don't think you will be able to single-quote them like that

---

### Post by bonelifer on 2014-05-26
When I run it via userjob, the calls:
fnUpdateStatus "Fetching cutlist"

just quietly fail and moves onto the next command, which would be one of the myth utils or handbrakecli, all of which work and leave me with the final file.  I'll try commenting out the cleanup at the end and see if the sql file is even being written. My first thoughts is the "function" isn't working and so they wouldn't be anyway.  So for those looking at it(hopefully your looking at the pastebin), is the fnUpdateStatus function written correctly? Am I calling it correctly? Remember I'm totally going by internet examples, so I may of misinterpreted various examples. If not for examples, I wouldn't have this userjob script to begin with.

---

### Post by steeldriver on 2014-05-26
You might want to try using a heredoc instead of a temporary file and getting rid of the single quotes e.g.

```

mysql -h $DBSERVER -u $DBUSER -p$DBPASS $DBNAME << EOF
UPDATE jobqueue SET comment="$1" WHERE chanid=$CHAN AND starttime=$START AND status=4;
EOF

```

---

### Post by bonelifer on 2014-05-26
Still working on it, but the temp file is being written. Had to use " instead of a single quote on the CHAN and START, which got those into the SQL file, now I need to work on the comment as it is output without quotes like below and I'm sure that will/is causing problems. Now to wait for the current job to finish.

```
UPDATE jobqueue SET comment=Width of Three's Company - S5E17 - And Baby Makes Four is less than 1280 WHERE chanid=11126 AND starttime=20140525192600 AND status=4
```

---

### Post by bonelifer on 2014-05-26
Fixed it. Had to change it from

```
comment="$1"
```

to

```
comment="\"$1\""
```

The dreaded enemy of beginning script writers, the unescaped quote.


Thanks for the help blm-ubunet and steeldriver. Probably would of spent two or three days before I realized I need to escape the quotes.

---

