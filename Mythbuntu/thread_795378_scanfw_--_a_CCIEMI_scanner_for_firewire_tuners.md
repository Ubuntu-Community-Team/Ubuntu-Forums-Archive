---
title: "scanfw -- a CCI/EMI scanner for firewire tuners"
date: 2008-05-15
forum: Mythbuntu
---

### Post by majoridiot on 2008-05-15
[b]as of 7 december 2008, scanfw has proven to be stable and is still a beta release.
the text of this original post has been intact for historical reference.  the link to
the source will always be for the latest available release.[/b]

the mythbuntu MythTV development team is proud to announce the development of scanfw- an EMI/CCI 
scanner to help identify encrypted stb channels on firewire connections.

a motorola-only alpha version of scanfw is now available for wider testing.  a scientific atlanta version is 
in development and will be available for wider testing soon.

sample output of scanfw, scanning 35 channels, beginning at channel 256:

```
idiot@devbox:~/firewire_scanner$ scanfw -i channels.txt -p 44 -b 256 -s 6 -n 35

mythbuntu firewire scanner .081 alpha (motorola-fast)

reading channel file... done.
Checking for available firewire ports... 1 port(s) found
Acquiring handle on port 0.
Searching for an stb on port 0
Using STB located on port 0 node 0

channel 256 TVLAND is encrypted
channel 257 FAM is clear
channel 260 HALMRK is clear
channel 306 NIK is clear
channel 308 THEN is clear
channel 309 NIKTON is encrypted
channel 315 DISN is clear
channel 317 TOOND is clear
channel 325 TOON is clear
channel 335 NOGGIN is encrypted
channel 336 SPROUT is clear
channel 338 DCKIDS is encrypted
channel 356 SITV is encrypted
channel 357 UNI is clear
channel 383 MTV3S is clear
channel 406 FNC is clear
channel 407 CNN is clear
channel 409 CNNH is clear
channel 410 FBN is clear
channel 411 BLOOM is encrypted
channel 412 CNBC is clear
channel 414 MSNBC is clear
channel 430 TWC is clear
channel 431 WEEKDT2 is encrypted
channel 445 CSPAN is clear
channel 446 CSPAN2 is clear
channel 447 CSPAN3 is encrypted
channel 450 NGC is clear
channel 453 TRAV is clear
channel 455 ANIMAL is clear
channel 461 DSC is clear
channel 464 SCIENCE is encrypted
channel 483 HISTORY is clear
channel 506 ESPN is clear
channel 509 ESPN2 is clear

clear channels:
257 FAM
260 HALMRK
306 NIK
308 THEN
315 DISN
317 TOOND
325 TOON
336 SPROUT
357 UNI
383 MTV3S
406 FNC
407 CNN
409 CNNH
410 FBN
412 CNBC
414 MSNBC
430 TWC
445 CSPAN
446 CSPAN2
450 NGC
453 TRAV
455 ANIMAL
461 DSC
483 HISTORY
506 ESPN
509 ESPN2

encrypted channels:
256 TVLAND
309 NIKTON
335 NOGGIN
338 DCKIDS
356 SITV
411 BLOOM
431 WEEKDT2
447 CSPAN3
464 SCIENCE


 35 channels scanned:
 26 clear channels
  9 encrypted channels
  0 channels errored

idiot@devbox:~/firewire_scanner$
```

output demonstrating error-recovery and listing only encrypted channels in the summary:

```
idiot@devbox:~/firewire_scanner$ scanfw -i channels.txt -p 44 -b 906 -s 8 -e

mythbuntu firewire scanner .081 alpha (motorola-fast)

reading channel file... done.
Checking for available firewire ports... 1 port(s) found
Acquiring handle on port 0.
Searching for an stb on port 0
Using STB located on port 0 node 0

channel 906 WEEKDT is encrypted
channel 908 WHOIDT is clear
channel 910 WYZZDT is clear
channel 912 WMBDDT is clear
channel 913 WGNHD is clear
channel 916 WTVPDT2 is clear
channel 919 CNNHD is encrypted
ERROR scanning channel 921, recovering...
channel 921 GOLFVS is clear
channel 922 CSNCHD is clear
channel 923 ESPNHD is encrypted
channel 924 ESPN2 is encrypted
channel 925 TNTHD is encrypted
channel 926 TBSHD is clear
channel 927 NGCHD is clear
channel 930 DISNHD is clear
channel 931 FAMHD is clear
channel 934 APLHD is clear
channel 935 HDT is clear
channel 936 DSCHD is clear
channel 937 UHD is clear
channel 938 SCIFIHD is encrypted
channel 939 USAHD is encrypted
ERROR scanning channel 940, recovering...
channel 940 AETVHD is encrypted
channel 941 HSTRYHD is encrypted
channel 942 HGTVD is clear
channel 943 FOODHD is clear
channel 944 TLCHD is clear
channel 945 MHDTV is encrypted
channel 947 MOJOHD is clear
channel 951 AMCHD is clear


encrypted channels:
906 WEEKDT
919 CNNHD
923 ESPNHD
924 ESPN2
925 TNTHD
938 SCIFIHD
939 USAHD
940 AETVHD
941 HSTRYHD
945 MHDTV


 30 channels scanned:
 20 clear channels
 10 encrypted channels
  0 channels errored

idiot@devbox:~/firewire_scanner$
```

the scanfw wiki page with source files and pre-compiled amd64 and i386 binaries can be found here:

[https://help.ubuntu.com/community/MythTV_Firewire/scanfw](https://help.ubuntu.com/community/MythTV_Firewire/scanfw)

this is still alpha, so feedback with any issues or useful additions, etc. is encouraged.

happy scanning! :D

---

### Post by murchball on 2008-05-15
This is great! I definitely would've found this useful when I began my MythTV journey (ie before I realized that my cable company encrypts everything except for what I get OTA). I only have a Scientific Atlantic box, but I'll volunteer to test once the SA version is ready.

---

### Post by majoridiot on 2008-05-17
code for scientific atlanta boxes is taking shape.  if you are interested in testing, please PM 
me with the following info:

your stb model number (e.g. 4250HDC, 3250HD, etc.)

the model it is configured as in mythbackend setup

your OS (i386 or amd64)

your email address

---

### Post by Peacekeeper on 2008-05-21
This is great! I am patently wait for he SA version... :)

-PK

---

### Post by mkramer on 2008-07-04
NM...I got it to compile...ill come back with my results

---

### Post by majoridiot on 2008-07-04
version .98 beta is now available for download.

for reasons known to the intertube gods alone, i can not edit the scanfw wiki page.  the source can be found here:

[https://wiki.ubuntu.com/majoridiot](https://wiki.ubuntu.com/majoridiot)

.98 includes support for both moto and SA stbs and has changes not included in the wiki.  please refer to to README file
for up-to-date information, until the login problem is fixed and the wiki page can be updated.

please post, PM or email me your bug reports and feedback.

enjoy.

---

### Post by dsbw on 2008-07-05
They took away my SA 4250 box (due to some *probably* unrelated wonkiness...I plugged in an HDMI TV, and that caused the box to scramble exactly one hi-def channel permanently!)

But I think the local TWC is moving toward those SA boxes minus the cable card versions, so I'll probably have one again soon enough.

---

### Post by theophile on 2008-07-11
I've tried this on my sa3250hd but it does not work reliably. Channels change but it cannot get a lock, even on known good channels.

If it uses the same methodology as mythprime, this is probably the reason. Mythprime works on my system about 3% of the time so I don't use it. Instead, I use sa3250ch and firewire_tester in conjunction with [Benton Roberts' excellent shell scripts](http://bentonroberts.com/personal/media-server/code/), modified to fit my hardware.

For raw channel changing, I use this. It lives at /usr/bin/changer.sh

```
#!/bin/sh

l=`echo $1 | awk '{print length($0)}'`

if [ $l -eq 3 ]
then
 sa3250ch -s $1
fi

if [ $l -eq 2 ]
then
 sa3250ch -s 0
 sa3250ch -s $1
fi

if [ $l -eq 1 ]
then
 sa3250ch -s 0
 sa3250ch -s 0
 sa3250ch -s $1
fi
```

MythTV changes the channels with this. No matter the state of my firewire connection, this script achieves a connection and data transfer for clear channels 100% of the time:

```
#!/bin/sh
# This script is designed to reliably change channels
# on the the Scientific Atlanta 3250HD via firewire
# Please see the accompanying README for usage

##########################
#### SECTION 0:  Configuration defaults
####    you may have to change some of these
####    Also, see "Derived Commands", section 1.1, below
CLEAR_CHANNEL=403
RESET="yes"
RESET_DELAY=2
TUNING_DELAY=2
TESTS=3
RESETS=3
PORT=0
NODE=0
SINGLE=""

##########################
#### SECTION 1: Parse and validate arguments
SCRIPT=`basename $0`
USAGE="Usage: $SCRIPT -hvsR -p <port> -n <node> [channel]"
while getopts p:n:hsvR o
do case "$o" in
    p)  PORT="$OPTARG";;
    n)  NODE="$OPTARG";;
    v)  VERBOSE=" -v" && QUIET="";;
    R)  RESET="no";;
    s)  SINGLE=" -s";;
    h)  echo $USAGE && exit 0;;
    ?)  echo $USAGE && exit 1;;
esac
done
# Reset $@
shift `echo $OPTIND-1 | bc`
CHANNEL=$1

##########################
#### SECTION 1.1: Derived Commands - IMPORTANT CONFIGURATION HERE!
#### You may well have to change some of these -- test them manually first
TESTER="/usr/bin/firewire_tester${VERBOSE} -p -n $NODE -P $PORT -r $TESTS"
CHANGER="/usr/bin/changer.sh"
RESETTER="/usr/bin/firewire_tester${VERBOSE} -P $PORT -n $NODE -R"

##########################
#### SECTION 1.2: Debug output
#echo "Port = $PORT"
#echo "Node = $NODE"
#echo "Reset? = $RESET"
#echo "Channel = $CHANNEL"
#echo "Tester = $TESTER"
#echo "Changer = $CHANGER"
#echo "Resetter = $RESETTER"

##########################
#### SECTION 2: Test the bus, reseting if necessary,
#### then change channels when bus test passes
echo "Testing node $NODE on port $PORT..."
$TESTER ; SUCCESS=$?
if [ $SUCCESS -eq 0 ]; then
        echo "Initial input test passed."
else
        echo "Initial test of port $PORT FAILED!"
        if [ $RESET != "yes" ]; then
                echo "No bus reset requested - giving up changing to channel $CHANNEL."
                exit 1;
        else
                TRIES=1
                # Change to the clear channel first, then pause
                echo "Tuning to clear channel $CLEAR_CHANNEL for bus reset..."
                $CHANGER $CLEAR_CHANNEL; sleep $TUNING_DELAY
                while [ "$TRIES" -le "$RESETS" -a "$SUCCESS" -gt 0 ]; do
                        echo "Reseting firewire bus $PORT, attempt $TRIES of $RESETS.."
                        # New reset the bus, pause, and test again
                        $RESETTER
                        sleep $RESET_DELAY
                        echo "Re-testing after bus reset..."
                        $TESTER ; SUCCESS=$?
                        let TRIES=$TRIES+1;
                done
                if [ $SUCCESS -gt 0 ]; then
                        echo "Bus reset tests FAILED - giving up changing to channel $CHANNEL."
                        exit 1;
                else
                        echo -n "Bus reset restored input on clear channel $CLEAR_CHANNEL"
                        echo " - changing to target channel $CHANNEL."
                fi
        fi
fi

##########################
#### SECTION 3: Change to the target channel once the bus test passes
echo "Changing to target channel $CHANNEL..."
$CHANGER $CHANNEL
echo "Pausing $TUNING_DELAY seconds for tuner to stabilize..."
sleep $TUNING_DELAY
echo "Performing a final input test on target channel $CHANNEL..."
$TESTER ; SUCCESS=$?
if [ $SUCCESS -gt 0 ]; then
        echo -n "WARNING: Final input test FAILED on channel $CHANNEL "
        echo " - blank recording likely!"
#       exit $SUCCESS
else
        echo "Input looks good on target channel $CHANNEL. "
fi
echo "$0 finished."
exit 0
```

Using these, I can generate a list of channels which can be received and those which cannot, which fall within a specified range. Again, these are Benton's scripts slightly modified to work for me:

```
#!/bin/bash
# This script is designed to walk the channels
# on the the Scientific Atlanta 3250HD via firewire
# and try a test recording on each

##########################
#### SECTION 0:  Configuration defaults
####    you may have to change some of these
####    Also, see "Derived Commands", section 1.1, below
VIDEO_FILES_DIR="."
START_CHANNEL=2
END_CHANNEL=399
RECORD_DURATION=10
CLEAR_CHANNEL=403
RESET="yes"
RESET_DELAY=2
TUNING_DELAY=2
TESTS=3
RESETS=3
PORT=0
NODE=0
SINGLE=""

##########################
#### SECTION 1: Parse and validate arguments
SCRIPT=`basename $0`
USAGE="Usage: $SCRIPT -hvsR [-p <port>] [-n <node>] [-d <duration>] [start channel] [end channel] [directory]"
while getopts p:n:d:hsvR o
do case "$o" in
    p)  PORT="$OPTARG";;
    n)  NODE="$OPTARG";;
    d)  RECORD_DURATION="$OPTARG";;
    v)  VERBOSE=" -v" && QUIET="";;
    R)  RESET="no";;
    s)  SINGLE=" -s";;
    h)  echo $USAGE && exit 0;;
    ?)  echo $USAGE && exit 1;;
esac
done
# Reset $@
shift `echo $OPTIND-1 | bc`

if [ "$1" != "" ]; then
        START_CHANNEL=$1; fi
if [ "$2" != "" ]; then
        END_CHANNEL=$2; fi
if [ "$3" != "" ]; then
        VIDEO_FILES_DIR=$3; fi

##########################
#### SECTION 1.1: Derived Commands - IMPORTANT CONFIGURATION HERE!
#### You may well have to change some of these -- test them manually first
TESTER="/usr/bin/firewire_tester${VERBOSE} -p -n $NODE -P $PORT -r $TESTS"
CHANGER="/usr/bin/changer.sh"
RESETTER="/usr/bin/firewire_tester${VERBOSE} -P $PORT -n $NODE -R"
TEST_MPEG="test-mpeg2 -p $PORT -r $NODE"


##########################
#### SECTION 2: Walk through the channels,
#### resetting the bus when the signal drops
CHANNEL=$1
CHAN=$START_CHANNEL
SCRIPT_NAME=`basename $0`
# Create the output directory if necessary
if [ ! -d $VIDEO_FILES_DIR ]; then
        echo "ERROR: Output directory $VIDEO_FILES_DIR must exist!"
        exit 1
fi
while [ $CHAN -le $END_CHANNEL ] ; do
        echo "Testing channel $CHAN..."
        $CHANGER $CHAN
        sleep $TUNING_DELAY
        OUTFILE="$VIDEO_FILES_DIR/$SCRIPT_NAME-$CHAN.mpg"
        echo "Recording $RECORD_DURATION seconds of video to $OUTFILE"
#       echo "Running $TEST_MPEG > $OUTFILE ...."
        $TEST_MPEG > $OUTFILE &
        sleep $RECORD_DURATION
        kill %1
        killall test-mpeg2
        SIZE=`du $OUTFILE | awk '{print $1}'`
        if [ -s $OUTFILE ] ; then
                echo "Channel $CHAN seems to work (read $SIZE Kbytes)."
        else
                echo "Unable to read from channel $CHAN."
                echo "Resetting firewire bus..."
                TRIES=1
                # Change to the clear channel first, then pause
                echo "Tuning to clear channel $CLEAR_CHANNEL for bus reset..."
                $CHANGER $CLEAR_CHANNEL; sleep $TUNING_DELAY
                while [ "$TRIES" -le "$RESETS" -a "$SUCCESS" -gt 0 ]; do
                        echo "Reseting firewire bus $PORT, attempt $TRIES of $RESETS.."
                        # New reset the bus, pause, and test again
                        $RESETTER
                        sleep $RESET_DELAY
                        echo "Re-testing after bus reset..."
                        $TESTER ; SUCCESS=$?
                        let TRIES=$TRIES+1;
                done
                if [ $SUCCESS -gt 0 ]; then
                        echo "Bus resets FAILED to restore input - giving up."
                        exit 1;
                else
                        echo -n "Bus reset restored input on clear channel $CLEAR_CHANNEL"
                        echo " - moving on to next target channel."
                fi
        fi
        let CHAN=$CHAN+1
done
```

That script is called walkSA3250channels.sh and if you run it to output to a file, you can generate your clear/encrypted lists:

./walkSA3250channels.sh > log.txt

*wait forever*

cat log.txt | grep work
Channel 15 seems to work (read 2880 Kbytes).
Channel 34 seems to work (read 4 Kbytes).
Channel 41 seems to work (read 1352 Kbytes).
Channel 46 seems to work (read 28 Kbytes).
Channel 48 seems to work (read 72 Kbytes).

or

cat log.txt | grep Unable
Unable to read from channel 2.
Unable to read from channel 3.
Unable to read from channel 4.
Unable to read from channel 5.
Unable to read from channel 6.
Unable to read from channel 7.
Unable to read from channel 8.
Unable to read from channel 9.
Unable to read from channel 10.
Unable to read from channel 11.
Unable to read from channel 12.
Unable to read from channel 13.
...


and so on.

One thing, though, is this only tells you whether data could be recorded from the channel but it doesn't say why or why not. For example, I am on Comcast (Jackson, Mississippi) and all the over-400 HD channels come it free and clear. But even though the lower numbered SD channels are all 5c=0, I can't seem to get them over firewire. I'd like to know why this is.

Anyway, this setup has saved me a great deal of frustration and I hope it helps others.

---

### Post by majoridiot on 2008-07-11
> **theophile said:**
> I've tried this on my sa3250hd but it does not work reliably. Channels change but it cannot get a lock, even on known good channels.

If it uses the same methodology as mythprime, this is probably the reason. Mythprime works on my system about 3% of the time so I don't use it. Instead, I use sa3250ch and firewire_tester in conjunction with [Benton Roberts' excellent shell scripts](http://bentonroberts.com/personal/media-server/code/), modified to fit my hardware.
<snip>...

a. scanfw usues a totally different methodology than mythprime.  in fact,
mythprime will be updated to include scanfw's methodologies.  the current
version of mythprime was a temporary, last-minute solution for 
mythbuntu 8.04- to fix issues with the primer and scripts i was unaware
of until almost too late.

b. i have no clue what, if any, problem you are reporting with scanfw.

c. if there are problems, it would be best to run scanfw, log the results
to a text file, pastebin them with a link here and then discuss it.

and- with all due respect- thank you for sharing, but:

d. if you have no intention of helping with the refinement/bug-hunting
of scanfw, your "solution" is best posted to a thread of its own, so it does
not confuse the issue here.  this is a thread for scanfw, *not* work-arounds.

---

### Post by theophile on 2008-07-11
My intention was to show what does work on my system. I am happy to help, though, that's what I'm trying to do. I can't tell you why scanfw doesn't work, but I can show you what does.

Anyway, I could not figure out how to run in verbose or debug mode. I checked the README and the help page but could not find such info. Here's what happens when I try to scan a known good channel:

```
root@farmer:~/scanfw# scanfw -i text.txt -p 403 -c 403

mythbuntu firewire scanner .98a beta

reading channel file... done.
Checking for available firewire ports... 1 port(s) found
Acquiring handle on port 0.
Searching for an stb on port 0
Using STB located on port 0 node 0
STB Vendor ID: 0x1692 Model ID: 0x0be0, Scientific Atlanta Model SA3250HD

ERROR scanning channel 403, recovering...
ERROR scanning channel 403 ESPN

Errors encountered during scan.  Attempting to re-scan 1 channels.
failed to prime stb- aborting re-scan


errored channels:
403 ESPN


  1 channels scanned:
  0 clear channels
  0 encrypted channels
  1 channels errored

```

By contrast:

```
root@farmer:~/scanfw# mySA3250change.sh 403
Testing node 0 on port 0...
Action: Test P2P connection 3 times, node 0, channel 0
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
Initial test of port 0 FAILED!
Tuning to clear channel 403 for bus reset...
Reseting firewire bus 0, attempt 1 of 3..
Action: Resetting the firewire bus
Bus reset succeeded
Re-testing after bus reset...
Action: Test P2P connection 3 times, node 0, channel 0
P2P: Testing...Success, 428 packets received
P2P: Testing...Success, 425 packets received
P2P: Testing...Success, 427 packets received
/usr/bin/mySA3250change.sh: 90: let: not found
Bus reset restored input on clear channel 403 - changing to target channel 403.
Changing to target channel 403...
Pausing 2 seconds for tuner to stabilize...
Performing a final input test on target channel 403...
Action: Test P2P connection 3 times, node 0, channel 0
P2P: Testing...Success, 25 packets received
P2P: Testing...Success, 292 packets received
P2P: Testing...Success, 265 packets received
Input looks good on target channel 403.
/usr/bin/mySA3250change.sh finished.
```

I've tried forcing the channel changer, it doesn't make a difference. I'd be happy to do any other testing you like.

---

### Post by majoridiot on 2008-07-11
> **theophile said:**
> My intention was to show what does work on my system. I am happy to help, though, that's what I'm trying to do. I can't tell you why scanfw doesn't work, but I can show you what does.

Anyway, I could not figure out how to run in verbose or debug mode. I checked the README and the help page but could not find such info. Here's what happens when I try to scan a known good channel:
<snip>...

I've tried forcing the channel changer, it doesn't make a difference. I'd be happy to do any other testing you like.

forcing the channel changer is not needed if it correctly changes channels.

have you tried trying a bit broader scan than just one channel?  if the
stb is unstable, then running it on just one channel can often fail- 
especially if the one channel you are scanning is also your priming channel.

before dismissing it as "not working for (your) stb", i would recommend
running a broader-range scan, make sure the channel for your -p option is
a solid, known-clear channel and trying -s 6 or higher, in the event your stb
is taking awhile to stabilize after channel-change and/or bus reset.

although it has been tested far more on moto boxes than SA, scanfw has worked
without issue on other SA3250s.

---

### Post by theophile on 2008-07-12
```
root@farmer:~/scanfw# scanfw -i text.txt -p 403 -b 432 -s 8

mythbuntu firewire scanner .98a beta

reading channel file... done.
Checking for available firewire ports... 1 port(s) found
Acquiring handle on port 0.
Searching for an stb on port 0
Using STB located on port 0 node 0
STB Vendor ID: 0x1692 Model ID: 0x0be0, Scientific Atlanta Model SA3250HD

ERROR scanning channel 432, recovering... 
ERROR scanning channel 432 NBC
ERROR scanning channel 433, recovering... 
ERROR scanning channel 433 CBS
ERROR scanning channel 434, recovering... 
ERROR scanning channel 434 FOX
ERROR scanning channel 440, recovering... 
ERROR scanning channel 440 PBS

Errors encountered during scan.  Attempting to re-scan 4 channels.
failed to prime stb- aborting re-scan


errored channels:
432 NBC
433 CBS
434 FOX
440 PBS


  4 channels scanned:
  0 clear channels
  0 encrypted channels
  4 channels errored
```

---

### Post by mineson on 2008-07-24
Hi,
Is scanfw meant to replace mythprime or augment it?  Is it normal that all my channels worked great, then all of them broke forever after I unplugged the STB?  Is scanfw what prevents that?

I'm running a new rig with 8.04 amd64 connecting to a SA4250HD from Cablevision of Westchester, NY.  I had firewire working really easilly for about a week using mythprime.  It tuned all channels (even Voom HD) with no problems. Then I unplugged the STB and moved it, and now it stopped working.  I've tried the power cycle trick, but no luck.  I run the mythprime small v and it says 55b, big V and it says :

Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
  
I noticed that when I installed proprietary codecs for DVD, I included w64.  I've removed but it didn't fix the problem, though I havent rebooted yet...

Your guidance on this is greatly appreciated.  Please let me know how I can help test.

---

### Post by majoridiot on 2008-07-26
sorry for the tardy reply, but real-life takes priority, you know? ;)

> **mineson said:**
> Hi,
Is scanfw meant to replace mythprime or augment it?

scanfw is a stand-alone tool in and of itself.

> **mineson said:**
> Is it normal that all my channels worked great, then all of them broke forever after I unplugged the STB?

no, this is not normal.

i recommend checking what the stb status of channels are- you can find
this info out through the diagnostic screens of the stb.  you are looking
for CCI=0x02- if you see this on your channels, they have been encrypted.

> **mineson said:**
> Is scanfw what prevents that?

no.

scanfw only tunes stations and reads information from packet headers
in the firewire stream.

> **mineson said:**
> I'm running a new rig with 8.04 amd64 connecting to a SA4250HD from Cablevision of Westchester, NY.  I had firewire working really easilly for about a week using mythprime.  It tuned all channels (even Voom HD) with no problems. Then I unplugged the STB and moved it, and now it stopped working.  I've tried the power cycle trick, but no luck.  I run the mythprime small v and it says 55b, big V and it says :

Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.

two possibilities come to mind:

1. your cable co. *coincidentally* encrypted their channels around the same time
you unplugged the stb

2. the stb went bad.  this does happen.
  
> **mineson said:**
> Your guidance on this is greatly appreciated.  Please let me know how I can help test.

if you are still fighting this, i would try:

shut off the computer, unplug the stb for five minutes, plug it back in and 
let it *fully* reboot (give it an hour or so to pull the data it needs).

then, try firing up the computer and trying priming and/or scanning.

try the second firewire port on the stb to see if it gives better results.

---

### Post by majoridiot on 2008-12-07
a new version of scanfw is now available.

***Added for .98b beta:***

updated SA and moto vendor info for various models and improved moto channel changer selection

latest source is available here: [https://wiki.ubuntu.com/majoridiot](https://wiki.ubuntu.com/majoridiot)

---

### Post by majoridiot on 2008-12-17
source code for scanfw version .98d beta has been posted at: [https://wiki.ubuntu.com/majoridiot](https://wiki.ubuntu.com/majoridiot)

changes include:

added vendor and model info for new moto and sa stbs

fixed a priming bug on bad channel recovery 

default motorola channel changer is now the single-digit method (7)

if you experience issues with your motorola stb with changer 7, you can force the "fast" changer with -f 6.

if the new changer affects you, please email me... i am trying to sort out where the various firmwares
are being deployed. my email addy is in the README.

---

### Post by DrJohn999 on 2009-03-14
With scanfw.0.98d-beta, after make and install and copying mythtv.firewire.channels.pl to /usr/bin, the script isn't able to open the database:

```
/etc/mythtv$ sudo mythtv.firewire.channels.pl
DBI connect('database=mythconverg:host=localhost;port=3306','mythtv',...) failed: Access denied for user 'mythtv'@'localhost' (using password: YES) at /usr/share/perl5/MythTV.pm line 337
Cannot connect to database:

```

Mythtv itself has no problems with channels / schedules, and:

```
 $mysql -u mythtv -p******* mythconverg
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 277
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>

```

So why is the script unable to connect?

Thanks,

--DJ

---

