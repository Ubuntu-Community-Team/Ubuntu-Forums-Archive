---
title: "Runs Mplayer with cron??"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by letex on 2007-07-05
Hello!
  I've an Ubuntu Feisty and i'm trying to set cron to record radio from internet throught mplayer.
  I use an script to record DBV-T with mencoder, and it runs, but mplayer don't.
  The script is:
[INDENT]  
!/bin/bash
# Script for record and internet radio station
#Original idea from ([www.tabernadelturco.com](www.tabernadelturco.com))
#
# Pplux ([www.pplux.com](www.pplux.com))

#station
emisora=http://emision.canariasahoraradio.com:8000

#minutes
minutos=1

#Name for recoding
programa=chabanel

#path  ('.' = actual)

dir=/home/ordenata/chabanel

# file name
nombre=${dir}/${programa}_`date +%y_%m_%d`.mp3
#------------------------------------------------#
#Doing a pipe
[ -e /home/ordenata/radio_pipe ] && rm /home/ordenata/radio_pipe
mkfifo /home/ordenata/radio_pipe

#Lame
lame /home/ordenata/radio_pipe $nombre 2>/dev/null 1>/dev/null &

#mplayer
mplayer $emisora -cache 32 -ao pcm:file=/home/ordenata/radio_pipe 2>/dev/null </dev/null &

#Waiting said time
sleep $(($minutos * 60))

#kill mplayer
	kill %2

#delete the pipe file
	rm /home/ordenata/radio_pipe[/INDENT]

  I do it run with cron and with ps axu search the process and it isn't. There is lame.

  Thinking on it, I tried to run with cron mplayer with a simple file, and not runs!!!

  There is any list of alloweds process to be runed with cron?? Can be runed a program with GUI?

Thank you in advance...and sorry for my poor english...

---

### Post by letex on 2007-07-05
nothing about this?? 

.......continue searching

---

### Post by RailRover on 2007-07-07
Hi letex,

I am able to record streams using mplayer via a cron job; here's how I did it:

I have a Dell Optiplex running Dapper Server, which is my home file server.  I record streams from a few favorite radio stations, and made a bash script for each of them, called "record_<station callsign>.sh", which initiates the recording process.  I also made a script called "end_record.sh" which terminates any running mplayer process.  I have mplayer save the streams to a directory /opt/streams, under which there is subdirectories for each date, and then in there, the stream files for what I have recorded.

Here is a file I have for recording station WHIO-AM in Dayton, Ohio ("record_whio.sh"):

#!/bin/sh
test -d /opt/streams/`date +%Y%m%d` || mkdir /opt/streams/`date +%Y%m%d`
nohup mplayer mms://uni1.cox.streamaudio.com/WHIO_AM -dumpstream -dumpfile /opt/streams/`date +%Y%m%d`/whio`date +%Y%m%d%H%M%S`.ram &

Then here is "end_record.sh":

#!/bin/sh
kill `ps -C mplayer -o pid=`


Here are the cron jobs to run this.  Note, in this example I'm recording a 3 hour show in 3 segments, not one big segment.  This is so that I can download the segments in smaller chunks and listen to them before the show is over (we're not allowed to stream at work, but we can download files just fine):

# m h  dom mon dow   command
#
# WHIO AM
#
00 11 * * 1-5 /home/support/record_whio.sh
59 11 * * 1-5 /home/support/end_record.sh
00 12 * * 1-5 /home/support/record_whio.sh
59 12 * * 1-5 /home/support/end_record.sh
00 13 * * 1-5 /home/support/record_whio.sh
59 13 * * 1-5 /home/support/end_record.sh


Now I realize the way I'm doing it is really simple and somewhat kludgy - for example, I can't use "end_record.sh" to terminate a particular mplayer process, it kills 'em all.  Also, the default format that mplayer is saving to (for me) is a .ram file (RealAudio), and not .mp3.  I'm not sure how to get mplayer to save it as an .mp3 file, but, since Windows Media Player (on my work computer) plays .ram files just fine, I haven't really worried about that either.

Maybe someday I will get motivated enough to streamline this a little more.  But I hope you can get some ideas from it!

[COLOR="Red"]**Edit:** [/COLOR]   I realized a couple days after I wrote this reply that the format which mplayer saves to is based on the type of stream that comes from the station.  In this example, WHIO uses a Windows Media stream, so these are really .asf files (not RealAudio) that are being generated.  I changed the script so that now it writes the files with an .asf extension (to be proper).


RailRover

---

### Post by ZxEfR on 2007-08-09
RailRover,

Thank you  Thank you :)

You have done exactly what I needed......I'm pretty much a noob still and couldn't have come up with the record and end record scripts......your scripts are exactly what I needed and I can use them as a great starting place to start learning scripting.

I have modified them slightly to fit the station that I wanted (a streamaudio station...just a diff one) and I changed the folder path to fit my folder path needs.

Well anywho......I am having one problem......everything works fine except one thing.....when cron runs the record script it will create the folder but it won't start recording the stream  :confused:   Can cron run part of a script? That's what it seems like it's doing.

If I click on the script manually to start it then it works great........and cron runs the end_record just fine........so.......I know it's running both of them but only seems to run part of the record script? Any idea as to why?

And Thanks again for getting me this far....... :)

---

### Post by RailRover on 2007-09-08
ZxEfR,

You're welcome, I'm glad to hear it's (mostly) working for you!  That is a strange issue with the cron job not running the mplayer part of the script though.  Cron should run the script just as if you ran it interactively (from the command line), provided the user the cron job runs under has access to mplayer, etc.  Now, if the cron job was submitted under your account, then it should run as you, and (in theory) should work just the same as if you ran it from the command line.

That being said, I've come up with an improvement to this script setup - I now launch the "record" script for a preset amount of time, after which the "end mplayer" script activates and kills just that ONE particular instance of the record script.  This means that I can now record multiple stations, overlapping recording times, and I don't have to worry about the kill script stopping ALL the mplayer processes at once, like the old-style setup would do.  I am going to list both scripts here - they have both changed from the ones I listed in my first message.

First, the "end mplayer" script, which you'll notice now waits a certain amount of time (which is passed in as a command-line argument), and then it wakes up and kills a particular mplayer process (another command-line argument):


#!/bin/sh
mplayer_pid=$1
sleep_time=$2
sleep $sleep_time
kill $mplayer_pid


Next is the recording script, which changed quite a bit.  It records the same way as before, but now it also launches an "end mplayer" process for itself, to be run in the future after its allotted recording time is up.  The default recording time is 3600 seconds (= 1 hour):


#!/bin/sh

# Get recording time from command line
if test -z "$1"
then
        # No command line argument for time, use default time
        recording_time=3600
else
        # Use recording time that was passed in
        recording_time=$1
fi

# Create directory for stream if it doesn't exists
test -d /opt/streams/`date +%Y%m%d` || mkdir /opt/streams/`date +%Y%m%d`

# Schedule mplayer to rip stream to file
nohup mplayer mms://uni1.cox.streamaudio.com/WHIO_AM -dumpstream -dumpfile /opt/streams/`date +%Y%m%d`/whio`date +%Y%m%d%H%M%S`.asf &

# Get PID of this mplayer process
mplayer_pid=$!

# Schedule process to kill mplayer after designated time
nohup /home/support/end_mplayer.sh $mplayer_pid $recording_time &

(end of script)


The crontab is easier to manage now, because you don't need to have the "end_mplayer" scripts in there anymore (since they are launched automatically):

00 11 * * 1-5 /home/support/record_whio.sh 3600
00 12 * * 1-5 /home/support/record_whio.sh 3600
00 13 * * 1-5 /home/support/record_whio.sh 3600

(and yes, I didn't HAVE to specify 3600 as an argument in my crontab entries, since that's the default time anyway...BUT I'm anal retentive and listed it anyway, so I could look at my crontab and see the recording times at a glance)

If you try these scripts out, make sure that the line that runs mplayer, with all those command line arguments, is just ONE line in your script.  It is wordwrapping as I type in this message, but in reality it is just one long line.  If not, this could keep your recording from working properly too.

RailRover

---

