---
title: "avertv usb dvb-t a800 how to get mythtv to recognise"
date: 2006-10-24
forum: Multimedia &amp; Video
---

### Post by Bobajot on 2006-10-24
I got this usb device about a week ago and it runs fine under xp pro. I set the whole thing up according to this [http://parker1.co.uk/mythtv_ubuntu.php]("http://parker1.co.uk/mythtv_ubuntu.php") and it worked ok on 

tzap -r "BBC ONE"

dvbstream -o -ps 600 601 -qam 16 -cr 3_4 | mplayer -

although it lost sound occasionally fixed by rerunning dvbstream (this may be due to signal strength or some configuration).
Problem I have is with the mythtv-setup how do I get it to recognise the device?

$ grep DVB  /var/log/dmesg
[   38.068974] dvb-usb: found a 'AVerMedia AverTV DVB-T USB 2.0 (A800)' in warm state.
[   38.069329] DVB: registering new adapter (AVerMedia AverTV DVB-T USB 2.0 (A800)).
[   38.074688] DVB: registering frontend 0 (DiBcom 3000P/M-C DVB-T)...
[   38.074843] input: IR-receiver inside an USB DVB receiver as /class/input/input2
[   38.074875] dvb-usb: AVerMedia AverTV DVB-T USB 2.0 (A800) successfully initialized and connected.

Only choice I get in mythtv-setup for capture cards is some analogue thingie.

I'm fast going off mythtv and wondered if there was another option? All I want to do is watch tv on the desktop and this software is over complex for a simple task. All it seems to need is a shell script to select a channel from a list extract the relevant bits for the
tzap -r "BBC ONE" or relevant channel name
and the relevant bits from the channels.conf to build the dvbstream
dvbstream -o -ps 600 601 -qam 16 -cr 3_4 | mplayer -
all non required output can go to /dev/null.
I'd like to get mythtv working but suspect it would be quicker to write the script.](*,)

---

### Post by Bobajot on 2006-10-29
OK so nobody knows much about mythtv with a USB device?

I wrote a script that selects a Mplayer start up which essentially is in the form mplayer "dvb://ITV4" or any other program (like ITV4) in the conf file previously scanned [http://www.ubuntuforums.org/showthread.php?t=173778](http://www.ubuntuforums.org/showthread.php?t=173778).
the simple script is

# channels for mplayer

rm choices.lst
FILENAME=/home/bob/channel.lst

cat channels.conf | cut -d ':' -f1 | (tr " " _) > $FILENAME
for channel in $(cat $FILENAME)
do
#  echo 'mplayer "dvb://'$channel'"'
   channel1=`echo $channel | (tr _ " ")`
   echo -n  $channel1
   echo 'mplayer "dvb://'$channel1'"'>>choices.lst
done
rm choices.list
cat -n choices.lst>choices.list
cat choices.list
set goodtogo="n"
while [ "$goodtogo" != "y" ]
do
   echo -n "Enter Channel Number and press [Enter];"
   read channel_number
   wanted=`grep -w "  "$channel_number choices.list |awk '{ print $2 " " $3 " " $4 " " $5" " $6 }'`
   echo $wanted
   echo -n "Enter y/n"
   read goodtogo
done
echo $wanted

[B]last few lines of output
    75  mplayer "dvb://Q"
    76  mplayer "dvb://Magic"
    77  mplayer "dvb://The Hits Radio"
    78  mplayer "dvb://BBC World Sv."
    79  mplayer "dvb://oneword"
    80  mplayer "dvb://smooth fm"
    81  mplayer "dvb://Kerrang!"
    82  mplayer "dvb://Smash Hits!"
    83  mplayer "dvb://Kiss"
    84  mplayer "dvb://Ideal World"
    85  mplayer "dvb://f tn"
    86  mplayer "dvb://UKTV Br'tIdeas"
    87  mplayer "dvb://TMF"
    88  mplayer "dvb://The HITS"
    89  mplayer "dvb://Film4"
Enter Channel Number and press [Enter];78
mplayer "dvb://BBC World Sv."
Enter y/ny
mplayer "dvb://BBC World Sv."
bob@linux-ubuntu64:~$ [/B]

$wanted gives the desired result. ie mplayer "dvb://BBC World Sv." for selection number 78.

However now I need to be able to 
1. kill any mplayer session started in (2)
2. Use the output $wanted to start mplayer.
 :-?

Anybody got any ideas? btw copy/paste of mplayer "dvb://ITV4" to another terminal window works great.
There are some other issues with mplayer like configuring it and getting it to use video acceleration but one thing at a time.

---

