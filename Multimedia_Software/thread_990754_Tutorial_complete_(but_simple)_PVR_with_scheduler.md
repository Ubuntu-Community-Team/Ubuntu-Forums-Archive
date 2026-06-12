---
title: "Tutorial: complete (but simple) PVR with scheduler"
date: 2008-11-23
forum: Multimedia Software
---

### Post by lovinglinux on 2008-11-23
This is a byproduct of my tutorial "[[COLOR="DarkRed"]**Firefox Media Center**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=913671")". I decided to create a new thread because some people might not be interested in the other stuff from the Firefox tutorial, so here you will just learn how to create a simple tv recording scheduler, with recording start date, start time, runtime, panel notification/stop icon and schedule browser.

[COLOR="Red"]**Requirements:**[/COLOR] You need a tv card already working with TVTime. I also recommend that you read my other tv tutorials [[COLOR="DarkRed"]**Simple PVR**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=923836") and [[COLOR="DarkRed"]**Simple TV Recorder**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5831356#post5831356"), because they can be combined to create a complete PVR system. 

To have a complete PVR system we need a way to schedule recordings. This is what we are going to create now, using an SQLite database and a few scripts.

As far as I know, SQLite is already installed on a fresh Ubuntu installation. Nevertheless you can run the following command, just to make sure:

```
sudo apt-get install sqlite sqlite3 sqlitebrowser
```

SQLite is a standalone and serverless database, so you don't have to worry about services listening to ports and other server security issues. The database is a simple file that can be read directly by applications like Firefox and our scripts. The sqlitebrowser is a GUI for browsing and editing sqlite databases. You can use it if you like, but we are going to create scripts to manage the recording schedules, so there is no need to use it. Additionally, you can install [[COLOR="DarkRed"]**SQLite Manager**[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/5817") extension for Firefox, which integrates a sqlite browser inside Firefox (very cool).

We also need to install transcode, ffmpeg and zenity. Type the following command on a terminal:

```
sudo apt-get install transcode ffmpeg zenity
```

Then download it [[COLOR="Red"]**the database here**[/COLOR]]("http://www.mediafire.com/download.php?wkzjilrmmne") and save it somewhere like ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**Databases**[/COLOR]/scheduler.sqlite. This path will be used as example throughout this section, but you can choose wherever path you want, as long you make the necessary changes in the scripts paths.

Now let's create some scripts!

Create the file ~/bin/tvcontrolcenter. This script will be our control center, from which we will be able to launch all other scripts.
```

gedit ~/bin/tvcontrolcenter
```

Add the following code to it and save it:
```

#!/bin/bash

ACTION=$(zenity --list --height=300  --width=300 --text "Select an action" --radiolist  --column "Pick" --column "Action" \
1 'schedule-add' \
2 'schedule-list' \
3 'schedule-clear')

${ACTION}
```

You can add more actions if you already have the scripts from [[COLOR="DarkRed"]**Simple PVR**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=923836") and [[COLOR="DarkRed"]**Simple TV Recorder**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5831356#post5831356") tutorials.

Create the file ~/bin/schedule-add. This script is the one we will use to add new recordings to our scheduler.
```

gedit ~/bin/schedule-add
```

Add the following code to it and save it:
```
#!/bin/bash

START=$(zenity --title "Recording start" --entry --text "Type date and time to start recording (YYYY-MM-DD HH:MM)")
RUNTIME=$(zenity --list --text "Choose a recording runtime" --radiolist  --column "Pick" --column "Recording runtime" 00:15:00 '00:15:00' 00:30:00 '00:30:00' 00:45:00 '00:45:00' 01:00:00 '01:00:00' 01:15:00 '01:15:00' 01:30:00 '01:30:00' 01:45:00 '01:45:00' 02:00:00 '02:00:00' 02:15:00 '02:15:00' 02:30:00 '02:30:00' 02:45:00 '02:45:00' 03:00:00 '03:00:00' 03:15:00 '03:15:00' 03:30:00 '03:30:00' 03:45:00 '03:45:00' 04:00:00 '04:00:00' 06:00:00 '06:00:00' 12:00:00 '12:00:00')
CHANNEL=$(zenity --title "Channel" --entry --text "Type the channel to be recorded")
sqlite3 ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**Databases**[/COLOR]/scheduler.sqlite "insert into record (start,runtime,channel) values ('${START}','${RUNTIME}','${CHANNEL}');"
```


Create the file ~/bin/schedule-list. This script will list the scheduler database entries.
```

gedit ~/bin/schedule-list
```

Add the following code to it and save it:
```
#!/bin/bash

sqlite3 ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**Databases**[/COLOR]/scheduler.sqlite "select * from record" | zenity --text-info --height=400  --width=300;

```


Create the file ~/bin/schedule-clear. This script will clean up the scheduler database and delete all recorded videos. Don't forget to change the paths in red accordingly.
```

gedit ~/bin/schedule-clear
```

Add the following code to it and save it:
```
#!/bin/bash

sqlite3 ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**Databases**[/COLOR]/scheduler.sqlite "DROP TABLE record"
sqlite3 ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**Databases**[/COLOR]/scheduler.sqlite "CREATE TABLE record ('start' DATETIME,'runtime' DATETIME,'channel' INTEGER, 'status' TEXT DEFAULT 'SCHEDULED')"
rm -fr ~/[COLOR="Red"]**Desktop**[/COLOR]/*.avi
```


Create the file ~/bin/schedule-start. This script will run as a cron job, to get the recording entries from the scheduler database and launch the recorder.
```

gedit ~/bin/schedule-start
```

Add the following code if you have a NTSC Tv card and save it:
```
#!/bin/bash

DATE=$( date +%Y-%m-%d )
TIME=$( date +%H:%M )
sqlite3 ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**Databases**[/COLOR]/scheduler.sqlite "update record set status='ON' where start='${DATE} ${TIME}' and status='SCHEDULED'"
STATUS=$(sqlite3 ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**Databases**[/COLOR]/scheduler.sqlite "select [status] from record where start='${DATE} ${TIME}'")
RUNTIME=$(sqlite3 ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**Databases**[/COLOR]/scheduler.sqlite "select [runtime] from record where start='${DATE} ${TIME}'")
SCHEDULE=$(sqlite3 ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**Databases**[/COLOR]/scheduler.sqlite "select [rowid] from record where start='${DATE} ${TIME}'")

if [ "$STATUS" = "ON" ] ; then
killall zenity
killall transcode
transcode -x v4l2,v4l2 \
	-M 2 \
	-i [COLOR="Red"]/dev/video0 [/COLOR]\
	-p [COLOR="Red"]/dev/dsp2 [/COLOR]\
	-y ffmpeg \
	-F mpeg4 \
	-c ${RUNTIME} \
	-g 720x480 \
	-f 0,4 \
	-I 1 \
	-u 100 \
	-Q 3 \
	-Z 360x240,fast \
	-E 48000,16,2 \
	--lame_preset medium \
	-o ~/[COLOR="Red"]**Desktop**[/COLOR]/${DATE}-${TIME}.avi & zenity --text "Recording started at ${TIME} with ${RUNTIME} preset time" --notification &&

killall zenity
killall transcode 
else
  echo "Doing nothing"
fi

sqlite3 ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**Databases**[/COLOR]/scheduler.sqlite "update record set status='RECORDED' where rowid='${SCHEDULE}'"
```

You will probably have to tweak this code and replace devices (in red) with your own. You can also choose other directories for saving the videos and the database.

For more command options visit [[COLOR="DarkRed"]**Transcode**[/COLOR]]("http://www.transcoding.org/cgi-bin/transcode?Transcode_Command_Line_Options") web site.

If you have a PAL Tv card, use the following code instead:
```
#!/bin/bash

DATE=$( date +%Y-%m-%d )
TIME=$( date +%H:%M )
sqlite3 ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**Databases**[/COLOR]/scheduler.sqlite "update record set status='ON' where start='${DATE} ${TIME}' and status='SCHEDULED'"
STATUS=$(sqlite3 ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**Databases**[/COLOR]/scheduler.sqlite "select [status] from record where start='${DATE} ${TIME}'")
RUNTIME=$(sqlite3 ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**Databases**[/COLOR]/scheduler.sqlite "select [runtime] from record where start='${DATE} ${TIME}'")
SCHEDULE=$(sqlite3 ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**Databases**[/COLOR]/scheduler.sqlite "select [rowid] from record where start='${DATE} ${TIME}'")

if [ "$STATUS" = "ON" ] ; then
killall zenity
killall transcode
transcode -x v4l2,v4l2 \
        -g 640x480 \
	-i [COLOR="Red"]/dev/video0 [/COLOR]\
	-p [COLOR="Red"]/dev/dsp2 [/COLOR]\
        -e 32000,16,2 \
        -N 0x1 \
	-J resample,levels,smartyuv \
        -w 4000 \
        -y ffmpeg \
        -F mjpeg \
	-c ${RUNTIME} \
	-o ~/[COLOR="Red"]**Desktop**[/COLOR]/${DATE}-${TIME}.avi & zenity --text "Recording started at ${TIME} with ${RUNTIME} preset time" --notification &&

killall zenity
killall transcode 
else
  echo "Doing nothing"
fi

sqlite3 ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**Databases**[/COLOR]/scheduler.sqlite "update record set status='RECORDED' where rowid='${SCHEDULE}'"
```

Then go to /home/[COLOR="Red"]**you**[/COLOR]/bin/, select the new scripts and open their properties. In the Permissions tab, make sure you tick "Allow executing file as program".

We need to create a button to start the control center. You can right-click in the Desktop and select "Create launcher" or you can add a "Custom Application Launcher" to the gnome panel. Either way, you are going to use the following settings:

**Type:** Application
**Name:** TV Control Center
**Command:** /home/[COLOR="Red"]**you**[/COLOR]/bin/tvcontrolcenter

After creating the button for the control center its time to test it. If everything works fine, then a dialog should be launched when you hit the control center button, so you can choose the action you want to perform. 

Select "schedule-add" to start inserting our first recording schedule.

When prompted for "date and time to start recording" you should enter a value in the format "YYYY-MM-DD HH:MM", using 15 minutes steps.

For example, if I want to start recording today at 5 am I should enter this:

```
2008-11-23 05:00
```

This format is mandatory and should be entered exactly like above, otherwise it won't work. For example, if I want to start recording next Tuesday at 12:20 I should enter this:

```
2008-11-25 12:[COLOR="Red"]**15**[/COLOR]
```

Note that since 12:20 is not within 15 minutes steps, then I have to use the next or previous value multiple of 15.

Click OK to proceed. When prompted for recording runtime, select an option from the list and click OK.

When prompted for the channel to record, type the channel number and click OK. The channel selection is not implemented yet, so please subscribe to this thread so when I update the scripts you will be informed. It works without the channel implementation when you have only one channel. For example, my Tv card is connected to a satellite setup box and I can't change channels with TVTime. So my channel is always 3 and I don't have to change it to record. 

After selecting the channel, the recording schedule will be inserted in the database. To check it, click the control center button again and select the "schedule-list" option. A window will pop up showing the current schedules in the database like this:
```

2008-11-25 05:00|00:15:00|3|SCHEDULED
```

New schedules will have "SCHEDULED" in the last value, while recorded schedules will have "RECORDED" instead.

Now click the control center button again and select "schedule-clear" then click the thumbnail again and select "schedule-list". The pop up window should be blank, because you cleared the database. Please notice that this will also delete all avi files from the recording path.

Now we need to create a cron job to run the script "~/bin/schedule-start" every 15 minutes. This script will retrieve the data from the database according to date and time and launch the recorder. To create the cron job follow the steps below:

1 - Type the following command in the Terminal to create a file named .change.cron

```
gedit ~/.change.cron
```

2 - Add the following lines to the file, replacing "[COLOR="Red"]**/home/you/**[/COLOR]" with your user path.

```

USER=[COLOR="Red"]**you**[/COLOR]
HOME=[COLOR="Red"]**/home/you**[/COLOR]
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/[COLOR="Red"]**you**[/COLOR]/bin
DISPLAY=:0.0
MAILTO=[COLOR="Red"]**you**[/COLOR]

00,15,30,45 * * * * /home/[COLOR="Red"]**you**[/COLOR]/bin/schedule-start >/dev/null 2>&1
```

This is how a cron job is layed out:

minute (0-59), hour (0-23, 0 = midnight), day (1-31), month (1-12), weekday (0-6, 0 = Sunday), command

This cron job will launch the "schedule-start" script every hour and 00 minutes, 15 minutes, 30 minutes and 45 minutes.

3 - Run System > Preferences > Sessions and add a startup program like the one below. Don't forget to replace "/home/you/" with your user path.

Name: Cron Changer
Command: crontab /home/[COLOR="Red"]**you**[/COLOR]/.change.cron
Comment: Will add jobs to cron

Run the following command to update the cron:

```
crontab /home/[COLOR="Red"]**you**[/COLOR]/.change.cron
```

then check if the cron job was added by running the following command:

```
crontab -e
```

We are done. Now you can launch the control center again to add a recording schedule and test if it works. Don't forget to use always multiple of 15 minutes in the recording start time.

When the cron job encounters a valid schedule it will launch the recorder and a notification icon will show up in the panel notification area. Move the mouse over the notification icon and a tooltip will display the time the recording started and the recording time preset. The corresponding avi file should be created in the directory you have chosen for saving the recordings.

You can stop the recording at any time by hitting the notification icon in the panel. It will remain on the panel if you do not touch it, even after the preset recording time ends (although the recording itself will stop automatically).

[COLOR="DarkRed"]**Gmail Scheduler**[/COLOR]

Now we will enhance the scheduler with Gmail support, so we can schedule recordings remotely by simply sending e-mails to a Gmail account.

First of all, open the file "~/bin/schedule-start"

```

gedit ~/bin/schedule-start
```

and replace the following line

```
  echo "Doing nothing"
```

with

```
schedule-gmail
```

This will make the cron job from the previous section to launch the gmail script if it does not find a valid scheduler entry in the database. This way, the database schedules will have priority over gmail schedules.

Then go to your Gmail account, click "Settings" then select the "Filters" tab and click "Create a new filter".

In the pop up window type "record" in the "Subject" field. Then click "Next step", select "Skip the Inbox (Archive it)" and "Apply the label:" >>> "Choose label"  >>> "New label..." and type "record" (without quotes) in the "New label" field. Click OK and then "Create Filter".

In terms of security, I think there isn't anything harmful that someone could do by sending a fake "record" e-mail to you. But I'm not a security expert, so you might want to use another filter like a string of random characters. Just make sure you replace "record" in the script when necessary. You can also specify other things like the "From" field if you will always send recording schedules from the same e-mail address. This will help avoiding filtering wrong messages, if someone sends you a message with "record" in the subject field. The label "record" doesn't really matter in terms of security, so leave it unchanged.

To test if the filter is working, send a message to yourself with the subject "record", then open the "All Mail" folder and check if the message is there with a "record" label. If it is there, then delete it.

In order to allow the scheduler to get entries from Gmail messages we need to download a copy of the e-mails to a local folder. We do this with offlineimap and GMail IMAP support.

Go to your Gmail "Settings", select the "Forwarding and POP/IMAP" tab and enable IMAP. Save it.

Now create a "mail" folder in your Desktop (if you want another path, just make sure you replace the [COLOR="Red"]**Desktop/mail**[/COLOR] path in the scripts when necessary). This is were the mail files and folders will be stored. 

Then create the offlineimap configuration file in your home folder:

```
gedit ~/.offlineimaprc 
```

Add the following code to it and save it:

```
[general]
accounts = GMail

ui = Noninteractive.Basic

[Account GMail]
localrepository = GMailLocalMaildirRepository
remoterepository = GMailServerRepository

[Repository GMailLocalMaildirRepository]
type = Maildir
localfolders = ~/[COLOR="Red"]**Desktop/mail/**[/COLOR]

[Repository GMailServerRepository]
type = IMAP
remotehost = imap.gmail.com
remoteuser = [COLOR="Red"]**yourgmailaccount**[/COLOR]@gmail.com
remotepass = [COLOR="Red"]**yourgmailpassword**[/COLOR]
ssl = yes

```

Change the values in red to match your account and paths.

Now install offlineimap, mpack and atool.

```
sudo apt-get install offlineimap mpack atool
```

Then run the following command to sync your Gmail account with the local folder [COLOR="Red"]**~/Desktop/mail/**[/COLOR]

```
offlineimap
```

This can take a while if you have many e-mails and attachments. The ideal is to use a Gmail account just for this, but once you sync for the first time the process will be much faster in the subsequent synchronizations.

Check if your messages and folders were downloaded to the[COLOR="Red"]** ~/Desktop/mail/**[/COLOR] directory. [COLOR="Red"]**[B]DON'T DELETE THEM! IF YOU DELETE THEM, YOUR MESSAGES WILL BE ALSO DELETED IN THE GMAIL SERVER IN THE NEXT SYNC!**[/B][/COLOR]

Now create the ~/bin/schedule-gmail script:

```
gedit ~/bin/schedule-gmail 
```

and add the following code to it, if you have a PAL Tv  card:

```
#!/bin/bash

DATE=$( date +%Y-%m-%d )
TIME=$( date +%H:%M )
START=$(ls ~/[COLOR="Red"]**Desktop**[/COLOR]/ | grep -e '\.date' | sed 's/.date//g')
RUNTIME=$(ls ~/[COLOR="Red"]**Desktop**[/COLOR]/ | grep -e '\.runtime' | sed 's/.runtime//g')
CHANNEL=$(ls ~/[COLOR="Red"]**Desktop**[/COLOR]/ | grep -e '\.channel' | sed 's/.channel//g')

if [ "$START" = "${DATE} ${TIME}" ] ; then
rm -fr ~/[COLOR="Red"]**Desktop**[/COLOR]/*.date
rm -fr ~/[COLOR="Red"]**Desktop**[/COLOR]/*.channel
rm -fr ~/[COLOR="Red"]**Desktop**[/COLOR]/*.runtime
killall zenity
killall transcode
transcode -x v4l2,v4l2 \
        -g 640x480 \
        -i [COLOR="Red"]**/dev/video0 \**[/COLOR]
        -p [COLOR="Red"]**/dev/dsp1 \**[/COLOR]
        -e 32000,16,2 \
        -N 0x1 \
	-J resample,levels,smartyuv \
        -w 4000 \
        -y ffmpeg \
        -F mjpeg \
	-c ${RUNTIME} \
	-o ~/[COLOR="Red"]**Desktop**[/COLOR]/${DATE}-${TIME}.avi & zenity --text "Recording started at ${TIME} with ${RUNTIME} preset time" --notification

killall zenity
killall transcode 

else
offlineimap && munpack -C /home/[COLOR="Red"]**you**[/COLOR]/[COLOR="Red"]**Desktop**[/COLOR]/ /home/[COLOR="Red"]**you**[/COLOR]/[COLOR="Red"]**Desktop**[/COLOR]/mail/record/new/* && aunpack --extract-to=/home/[COLOR="Red"]**you**[/COLOR]/[COLOR="Red"]**Desktop**[/COLOR]/ /home/[COLOR="Red"]**you**[/COLOR]/[COLOR="Red"]**Desktop**[/COLOR]/record.zip && rm -fr /home/[COLOR="Red"]**you**[/COLOR]/[COLOR="Red"]**Desktop**[/COLOR]/mail/record/new/* && offlineimap
fi

rm -fr ~/Desktop/record.desc
rm -fr ~/Desktop/record.zip

```

If you have a NTSC Tv card then use this code instead:

```
#!/bin/bash

DATE=$( date +%Y-%m-%d )
TIME=$( date +%H:%M )
START=$(ls ~/[COLOR="Red"]**Desktop**[/COLOR]/ | grep -e '\.date' | sed 's/.date//g')
RUNTIME=$(ls ~/[COLOR="Red"]**Desktop**[/COLOR]/ | grep -e '\.runtime' | sed 's/.runtime//g')
CHANNEL=$(ls ~/[COLOR="Red"]**Desktop**[/COLOR]/ | grep -e '\.channel' | sed 's/.channel//g')


if [ "$START" = "${DATE} ${TIME}" ] ; then
rm -fr ~/[COLOR="Red"]**Desktop**[/COLOR]/*.date
rm -fr ~/[COLOR="Red"]**Desktop**[/COLOR]/*.channel
rm -fr ~/[COLOR="Red"]**Desktop**[/COLOR]/*.runtime
killall zenity
killall transcode
transcode -x v4l2,v4l2 \
	-M 2 \
	-i [COLOR="Red"]**/dev/video0 \**[/COLOR]
	-p [COLOR="Red"]**/dev/dsp2 \**[/COLOR]
	-y ffmpeg \
	-F mpeg4 \
	-c ${RUNTIME} \
	-g 720x480 \
	-f 0,4 \
	-I 1 \
	-u 100 \
	-Q 3 \
	-Z 360x240,fast \
	-E 48000,16,2 \
	--lame_preset medium \
	-o ~/[COLOR="Red"]**Desktop**[/COLOR]/${DATE}-${TIME}.avi & zenity --text "Recording started at ${TIME} with ${RUNTIME} preset time" --notification

killall zenity
killall transcode 

else
offlineimap && munpack -C /home/[COLOR="Red"]**you**[/COLOR]/[COLOR="Red"]**Desktop**[/COLOR]/ /home/[COLOR="Red"]**you**[/COLOR]/[COLOR="Red"]**Desktop**[/COLOR]/mail/record/new/* && aunpack --extract-to=/home/[COLOR="Red"]**you**[/COLOR]/[COLOR="Red"]**Desktop**[/COLOR]/ /home/[COLOR="Red"]**you**[/COLOR]/[COLOR="Red"]**Desktop**[/COLOR]/record.zip && rm -fr /home/[COLOR="Red"]**you**[/COLOR]/[COLOR="Red"]**Desktop**[/COLOR]/mail/record/new/* && offlineimap
fi

rm -fr ~/Desktop/record.desc
rm -fr ~/Desktop/record.zip

```

Don't forget to change the permission of the script to allow it to run as program.

Now it's time to test the script.

To schedule the recordings we will basically send an e-mail to the the Gmail account with the suject "record" and including a zip file with the recording settings. You don't need to add any text in the body of the message. 

So create 3 **empty** files somewhere (not in the [COLOR="Red"]**~/Desktop**[/COLOR] if you didn't changed the paths) like this:

```
2008-11-24 16:15.date
```

This is the file that will determine when  to start recording. You must use the format "YYYY-MM-DD HH:MM" like in the previous section and the ".date" file extension, otherwise it won't work. Additionally, since our cron job from the previous section is set to run every 15 minutes, you must use multiples of 15 minutes in the time settings.


```

3.channel
```

This is the file that will determine tha channel to record. You should set the channel as file name and use the extension ".channel". This feature is not yet implemented in the code. 

```
00:15:00.runtime
```

This is the file that will determine for how long the recorder will run. You must use the format "HH:MM:SS" and the file extension ".runtime", otherwise it won't work. 

Compact these 3 files into a "record.zip". You must use "record.zip" every time, otherwise it won't work.

Here is a script to create these files automatically:
```

#!/bin/bash

MONTH=$(zenity --list --height=360 --text "Select the month" --radiolist  --column "Pick" --column "Month" 01 '01' 02 '02' 03 '03' 04 '04' 05 '05' 06 '06' 07 '07' 08 '08' 09 '09' 10 '10' 11 '11' 12 '12')

DAY=$(zenity --list --height=620 --text "Select the day" --radiolist  --column "Pick" --column "Day" 01 '01' 02 '02' 03 '03' 04 '04' 05 '05' 06 '06' 07 '07' 08 '08' 09 '09' 10 '10' 11 '11' 12 '12' 13 '13' 14 '14' 15 '15' 16 '16' 17 '17' 18 '18' 19 '19' 20 '20' 21 '21' 22 '22' 23 '23' 24 '24' 25 '25' 26 '26' 27 '27' 28 '28' 29 '29' 30 '30' 31 '31')

HOUR=$(zenity --list --height=620 --text "Select the starting time" --radiolist  --column "Pick" --column "Time" 00 '00' 01 '01' 02 '02' 03 '03' 04 '04' 05 '05' 06 '06' 07 '07' 08 '08' 09 '09' 10 '10' 11 '11' 12 '12' 13 '13' 14 '14' 15 '15' 16 '16' 17 '17' 18 '18' 19 '19' 20 '20' 21 '21' 22 '22' 23 '23')

MINUTES=$(zenity --list --height=200 --text "Select starting minutes" --radiolist  --column "Pick" --column "Minutes" 00 '00' 15 '15' 30 '30' 45 '45')

RUNTIME=$(zenity --list --height=460 --text "Select the runtime" --radiolist  --column "Pick" --column "Runtime" 00:15:00 '00:15:00' 00:30:00 '00:30:00' 00:45:00 '00:45:00' 01:00:00 '01:00:00' 01:15:00 '01:15:00' 01:30:00 '01:30:00' 01:45:00 '01:45:00' 02:00:00 '02:00:00' 02:15:00 '02:15:00' 02:30:00 '02:30:00' 02:45:00 '02:45:00' 03:00:00 '03:00:00' 03:15:00 '03:15:00' 03:30:00 '03:30:00' 03:45:00 '03:45:00' 04:00:00 '04:00:00')

CHANNEL=$(zenity --entry --text "Type the channel number")

print > ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**2008**[/COLOR]-${MONTH}-${DAY}\ ${HOUR}:${MINUTES}.date

print > ~/[COLOR="Red"]**Desktop**[/COLOR]/${RUNTIME}.runtime

print > ~/[COLOR="Red"]**Desktop**[/COLOR]/${CHANNEL}.channel

zip -j ~/[COLOR="Red"]**Desktop**[/COLOR]/record.zip ~/[COLOR="Red"]**Desktop**[/COLOR]/${RUNTIME}.runtime ~/[COLOR="Red"]**Desktop**[/COLOR]/${CHANNEL}.channel ~/[COLOR="Red"]**Desktop**[/COLOR]/[COLOR="Red"]**2008**[/COLOR]-${MONTH}-${DAY}\ ${HOUR}:${MINUTES}.date

rm -fr ~/[COLOR="Red"]**Desktop**[/COLOR]/2008-${MONTH}-${DAY}\ ${HOUR}:${MINUTES}.date

rm -fr ~/[COLOR="Red"]**Desktop**[/COLOR]/${RUNTIME}.runtime

rm -fr ~/[COLOR="Red"]**Desktop**[/COLOR]/${CHANNEL}.channel
```

You need to replace "2008" next year.

If you want to the script above to send the e-mail automatically, then install sendEmail:

```
sudo apt-get install sendemail
```

and add the following lines to the end of the script:

```
sendEmail -f [COLOR="Red"]**sender@foo.com**[/COLOR] -t [COLOR="Red"]**youremail@gmail.com**[/COLOR] -u "record" -s [COLOR="Red"]**smtp.foo.com**[/COLOR]:25 -a /home/[COLOR="Red"]**you**[/COLOR]/Desktop/record.zip -xu [COLOR="Red"]**smtpusername**[/COLOR] -xp [COLOR="Red"]**smtppassword**[/COLOR]

rm -fr ~/Desktop/record.zip
```

Otherwise, add this zip to the mail attachment and send it. You should send the e-mail at least 30 minutes before the scheduled time, to make sure nothing goes wrong.

Then run the gmail script manually to sync the files for the first time.

Basically the script will do this the first time you run it:

1 - Sync the messages and folders from the Gmail account with a local copy in the ~/Desktop/mail/ folder

2 - Extract the content of the new message with the "record" label to the /home directory. Since the body of the message will be empty, it will only extract the "record.zip" file from the message.

3 - Unpack the zip content to the  [COLOR="Red"]**~/Desktop **[/COLOR] directory and delete the "record.zip" file.

4 - Delete the local copy of the "record" message and sync with Gmail again to delete in the server.


Next time you run the script, it will check if the current date and time is the same as the file name of the extracted **~/Desktop/YYYY-MM-DD HH:MM.date**. If yes, then it will delete the extracted files and start recording. It will also use the name of the file **~/Desktop/HH:MM:SS.runtime** to set the recording time.

So if you send the e-mail just after the recording starting time, the script will not find any ".date", ".channel" and ".runtime" files and will not start recording. It will then extract the "record.zip" file, but next time the cron job for the scheduler will run, the time will not match the file name of **~/Desktop/YYYY-MM-DD HH:MM.date**. 

The script is setup this way to avoid delays in the Gmail sync download if you have additional new e-mails with big attachments. So the first time it encounters a new message with the "record" label it will only extract the content of the message and will check them in the next cron job. 

For this to work you need to setup the cron job for the "~/bin/schedule-start" script (see previous section) to run every 15 minutes, schedule your recordings with 15 minutes intervals and send the e-mail at least 30 minutes before the recording start.

With this method you can only send on recording schedule at at time, but at least it is a simple way of scheduling a recording remotely if you forgot to schedule your  favorite Tv show, without requiring to remotely connect to your machine. I'm not sure if someone could send you an e-mail to run arbitrary code, but I guess this is unlikely, because the files sent with the attachment are not executables and they do to have the specified format, the script will not run. This provides the advantage of not opening your machine to the internet with services like ssh or vnc.

---

### Post by lovinglinux on 2008-11-24
I have updated the cron part, because it wasn't really working with the previous code.

---

### Post by lovinglinux on 2008-11-24
**[COLOR="Red"]Another important update![/COLOR]**

I have expanded the tutorial to include support for scheduling TV recordings by e-mail, using a Gmail account.

So now we can tell our media center to record a TV show by simply sending an e-mail with the configuration files.

:popcorn:

Since the the method was created by me with programs not designed to do this, it isn't very elegant, but it works. I would appreciate comments about it's functionality.

---

