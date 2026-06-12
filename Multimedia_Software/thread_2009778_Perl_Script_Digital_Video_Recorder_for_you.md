---
title: "Perl Script Digital Video Recorder for you"
date: 2012-06-24
forum: Multimedia Software
---

### Post by fixitdude on 2012-06-24
Here's a Perl script I wrote that uses the over the air Electronic Program Guide (EPG) data to schedule TV program recording.

Features:
[list]
[*]Uses keywords to find your favorite TV programs.
[*]Manual recording settings too, also using days of the week / weekends.
[*]Can scan many channels to get EPG program data.
[*]Finds your programs on any of the scanned channels.
[*]Runs without GUI in the background, even on remote machines.
[*]Saves energy, can be run on a remote laptop 24/7 using only 20W.
[*]Controlled by simple to edit text files.
[*]Easy setup.
[*]Written with user modification in mind, make it do special things.
[/list]

Most digital TV channels broadcast "TV Guide" data over the air along with the video feed. This script picks up that data, looks through it for your favorite TV programs and records them to your hard drive for later viewing. It's pretty much like having a Tivo without the monthly fee.

I wrote it in as simple a Perl format as possible, and with many comments so it would be easy for people to modify and customize it.

I use ATSC broadcast for this program, it should work with a little tweaking on other EPG formats and possibly XML TV guides.

To get started, you need to get to the point where you can use "mencoder" from the command line and successfully save a video file, or make a command line that works for you and outputs the format you want.

A working example I use is included and works with Ubuntu 12.04 and "Xine" to play back the saved files. I like to use little CPU and memory so I do no big conversions on the video format and the files get to be 1.8GB for a hour show, watch, delete, so what. If you want something different, you will need to create your own mencoder options and change the mencoder line in the source code. For now, just try it.

You also need to be able to get EPG data using the "atsc_epg" program from command line.

Here's some examples that should work if you substitute your TV channel NAME for "TV11 below, and also get channel info for "atsc_epg" from your "~/.mplayer/channels.conf" file. It will get 5mb of TV and stop. Use google and the man pages to help you with the formats for the commands.
```

mencoder -endpos 5mb -ovc copy -oac pcm -o "testvideo.avi" dvb://TV1
atsc_epg -a0 -f 177000000:8VSB:65:68:4

```

If you can't do the above commands from the command line then this program will not work, get that working first.

Next, create a directory to store the videos, I call mine "tv-recording".

Then create a keyword file based on program names you like, it will find partial names. It's a simple text file named "tv-keywords.txt", one line per keyword (spaces are OK in keywords). This keyword also becomes the saved filename. Example:
```

Hawaii Five-O
Mission
Twilight Zone
M*A*S*H
Hogan's Heroes

```

Notice that "Mission: Impossible" has a ":" in it, and the "tv-schedule.txt" file uses those, so please leave those out of the keyword file.

The next file is the "tv-always.txt", you can create it and leave it empty, but it MUST exist. This is for things you want recorded via time and day all the time, regardless of EPG data or not. One line per entry that you want added to the TOP of the "tv-schedule.txt" file, the line must be in "tv-schedule.txt" file format.

You can use the "tv-always.txt" file to schedule programs for channels that don't broadcast EPG data, or make another script that adds special movie times to this file.

Now you need to enter some channels to do a EPG scan on. The source code has an example near the top, you need to change those to your channels from the ~/.mplayer/channels.conf file. You can add as many as you want, just remember the "," after each one except the last one.

Next you need to create a "tv-schedule.txt" file this ONE TIME by uncommenting the special "goto" line and running the program. You should rename the program file you got here "perl-dvr.txt" to "perl-dvr.pl" and "chmod 755 perl-dvr.pl" so it will run. Leave logging enabled for a while so you can check up on how the program is doing.

```

# goto MAKE_SCHEDULE_NOW; # un-comment this line like below

goto MAKE_SCHEDULE_NOW;

```

Now run the program and it should get the EPG data and create a "tv-schedule.txt" file if it found any programs in that data.

You should only have to do this once manually to check if the program is working correctly and your EPG data is OK.

It also creates a "tv-epg-output-log.txt" file that is a copy of the output from the "atsc_epg" call. You can look through that to understand why it may have not picked up program from the keywords.

If everything works, you need to comment the "goto" line again so it doesn't do that every time it runs, and create a cron entry so this program runs every minute, use "crontab -e" to edit your cron file.

```

# min hr day mo day-week (sun=0) command
* * * * * /home/USERNAME/perl-dvr.pl >/dev/null 2>&1

```

The above cron makes the script run every minute. It will go through the "tv-schedule.txt" file and see if a program needs to be recorded, it will even start a little late by a few minutes.

If it's not recording, it will scan the channels you gave it for EPG data and schedule new programs. It can't be recording because it will need to switch channels to find EPG data on other channels.

That's about it. You should now be automatically recording TV programs!

For your info, the format of the "tv-schedule.txt" file is:

Channel:Hour:Min:Duration:NOT-Days:Filename

Example:

TV1:18:00:60:06:Star Trek

Means record on channel "TV1" starting at 18:00 for 60 minutes and name the file "Star Trek" only on week days.

The "NOT-Days" field is special, 0 means Sunday, 3 is Wednesday, 6 is Saturday etc.. These are days to NOT record a show. Example:

TV1:18:00:60::Star Trek

Means record it every day.

TV1:18:00:60:1:Star Trek

Means don't record on Monday only. You can add as many numbers as you need in this field. 012345 would mean only record on Saturday.

Enjoy!

Please post if you like this program and are using it, and also post any any improvements or cool modifications you make so others can use them too!

(I will try to edit this post and update the program from time to time, but always look below for more messages about any improvements)

Edit: Minor text changes above

---

### Post by fixitdude on 2012-06-30
Sometimes a channel scan won't pick up all your local stations. This could be caused by the signal not being strong enough. Digital TV receivers seem to like a very strong signal so you may need a 10 or 20 db amplifier or move your antenna around, position can be important, it also may be getting signal reflections from behind the antenna, so you may find it gets a better signal when you move it to the side a bit or tilt it.

You can use "Kaffeine" to watch live TV and do your adjustments. Remember the lower (US) channels are at 57 Mhz and then jump to 177 Mhz for the next and go all the way up to 850 Mhz so it's quite a wide frequency range to cover.

So when you are checking channels, try the lowest and step up a few at a time. The highest channels should be easier to pick up even with a simple wire.

A good old fashioned TV antenna with VHF and UHF works great, you just need to combine both VHF and UHF signals into the one input with either a device made for that or just use a splitter. Try things and experiment before spending a lot of money. If you know what a dipole is, you can make one of those out of wire and clothespins if you are not too far from the transmitters. 

When you pick keywords and put them in the "tv-keywords.txt" file, put them in priority order. The script starts from the top and works it's way down and will basically start recording with the first match it finds.

---

### Post by fixitdude on 2013-04-24
Update for those who might find this via google search and may be using a USB tuner device.

You may not have to do this, but I found it useful to do a driver reset / reload just before the script tries to get the EPG data, so if you are having stuck driver problems this seems to help and I am posting it so people who know what they are doing in linux and perl can do this too, I am sure you know what to do, you figure out where to add this in the script.

The concept is to have the perl script put a empty file in your home directory called "reset-au0828.txt" and then have the below script in your root home directory and run from cron every minute. When it sees the "reset-au0828.txt" file it will do a driver reset / reload via root, and then it will delete that file from your home directory as a sort of "handshake" so the perl script knows that it was reset, you make the perl script check for it before proceeding to do a EPG scan. If you didn't get all that, read this again. You figure out how to set up cron to run the script, lots of posts out there telling how to do that.

This is for my driver and USB TV device, a Hauppauge WinTV HVR 950Q (USB ATSC tuner) that uses the au0828 driver so you need to modify it to work with yours of course, use google.

Here's the shell script that goes in your root home folder, use at your own risk:
```

#! /bin/sh

# started every minute by cron
# then every 10 seconds we check to see if the reset file exists
# if it does we do the reset and then remove the file
# we only do this till the minute is up and cron starts another one
# I checked this and it checks at exactly 50 seconds but then sits for 10

for i in 1 2 3 4 5 6
do
echo "check" $i

if [ -f /home/USERNAME/reset-au0828.txt ]
then
echo "reset file exists, resetting USB au0828"
killall mencoder
killall atsc_epg
sleep 1
sync; echo 3 > /proc/sys/vm/drop_caches
sleep 1
/sbin/modprobe -r au0828
sleep 2
/sbin/modprobe au0828
sleep 2
rm -f /home/USERNAME/reset-au0828.txt
break
fi
sleep 8

done



```

I really enjoy having it record things so I can watch them when I have the time, it's great, so thanks to all the driver developers who made it possible!

---

