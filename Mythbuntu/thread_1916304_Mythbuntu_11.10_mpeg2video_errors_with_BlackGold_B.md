---
title: "Mythbuntu 11.10 mpeg2video errors with BlackGold BGT3650"
date: 2012-01-27
forum: Mythbuntu
---

### Post by ecwanet on 2012-01-27
Hi everyone, my first post please excuse etiquette errors and general lack of myth knowledge.

As part of a project to build a dedicated HTPC I have extended my Win7 + Slackware 13.37 desktop with some extra disks and a BlackGold BGT3650 quad DVB-T2 tuner card. Spec posted here [http://ubuntuforums.org/showpost.php?p=11644928&postcount=344](http://ubuntuforums.org/showpost.php?p=11644928&postcount=344)

I've installed Myhtbuntu 11.10 onto one of the extra disks and have had hours of fun getting the hang of Mythtv. I've got the BGT3650 running using the 0.791 64bit BlackGold binary drivers. I've worked out how to set up the video sources to get only the muxes I want (UK Freeview hd, Crystal Palace) and to receive the EIT guide data rather than using the RT listings.

There are a number of snags, the main problem being that sometimes, after changing channel, I get blizzards of video decode errors manifesting themselves as a completely broken up picture and staccato audio, and this just continues without ever correcting itself. Usually, swapping to another channel and back again clears the problem. It does not appear to be limited to a particular channel or mux and happens about once in every 20 to 30 channel changes.

Some examples of the error messages are:
[mpeg2video @ 0x<address> ] ac-tex damaged at 0 19
[mpeg2video @ 0x<address> ] invalid mb type in I Frame at 0 11
[mpeg2video @ 0x<address> ] skipped MB in I frame at 1 34
[mpeg2video @ 0x<address> ] Warning MVs not available
[mpeg2video @ 0x<address> ] Header missing
[mpeg2video @ 0x<address> ] 00 motion_type at 41 33
[mpeg2video @ 0x<address> ] slice mismatch
plus others with the same prefix, interspersed with audio decode errors:
[mp2 @ 0x7f6dedf9f700]Header missing
AFD Error: Unknown audio decoding error

There does not seem to be a preceding error that heralds the start of the blizzard. It's as if the decoding starts 'out of step' and never gets back in step.

I get the same symptoms, again occasionally, using mplayer from the command line. However, when I boot the machine into Windows 7 the picture and sound breakup does not happen with Media Centre.

I have used tzap to tune to channels in the different muxes but the BER and UNC counts are consistently zero, the signal strength is usually above c000 and snr usually around 010b.

How can I diagnose this problem? I can't reproduce it at will. Where do I look? Are there any messages I can turn on (and how do I do that)? Is this post too long?

Thanks for listening.

---

### Post by ecwanet on 2012-02-05
Ok, no suggestions yet so I have written a bash script to pick a TV channel at random, use tzap to tune to that channel then invoke ffplay (an ffmpeg utility) to decode and play the transport stream.

tzap runs as a co-process with the -r option so the stream is available on /dev/dvb/adapterN/dvrN and it keeps running on that channel until the script kills it.

When I terminate ffplay playback the script will retry playback of the same live stream, pick another channel, or quit according to my input.

```
#!/bin/bash
#
# zaploop
#
# This script uses tzap to tune to digital tv channels
# using the selected dvb adapter
# takes a parameter, adapter no (0 - 3) 
#
# pick a channel at random then tune to it
# output channel name & frequency plus some lines of tuning status and ffplay's stderr to a log file
# continue until cancelled
# 
	ADAPTER=$1	
	LOGFILE="zloop"$ADAPTER".txt"
	ZAPLOG="zaplog"$ADAPTER".txt"
	FFLOG="fferrs"$ADAPTER".txt"
	SAVE_IFS=$IFS
	IFS=$'\n'
#	extract channel name and freq into arrays	
	ALLCHANS=( $( sed 's/\(^[^:]*\).*/\1/' <channels.conf) )
	ALLFREQS=( $( sed 's/^[^:]*:\([^:]*\).*/\1/' <channels.conf) )
	IFS=$SAVE_IFS
	CHANS=${#ALLCHANS[@]}-1
	ACTION=""
	while [ "$ACTION" = "" ] ; do
#	pick a channel at random (not 1-4, they're HD)
	  IND=-1
	  while [ $IND -lt 4 ]; do
	    let "IND=$RANDOM%$CHANS"
	  done
	  CHANNEL=${ALLCHANS[$IND]}
	  echo "$(date +%F' '%T) $CHANNEL on ${ALLFREQS[$IND]}" >>$LOGFILE 
	  coproc tzap -a $ADAPTER -r -c channels.conf "$CHANNEL" >/dev/null 2>$ZAPLOG
	  ZPID=$COPROC_PID
	  # allow time to tune
	  sleep 2
	  echo "start ffplay for channel $CHANNEL"
	  echo $CHANNEL > zchan$ADAPTER.txt
	  echo "start ffplay for channel $CHANNEL" 1>$FFLOG
	  # decode and show with ffplay. 
	  # ESC to stop ffplay then "r" for a retry, "" for next channel, anything else exit script
	  ACTION="r"
	  while [ "$ACTION" = "r" ] ; do
	    ffplay -f mpegts /dev/dvb/adapter$ADAPTER/dvr0 -window_title "$CHANNEL on adapter $ADAPTER" 2>>$FFLOG
	    echo "$(date +%F' '%T) ffplay terminated ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~" >>$FFLOG
	    read ACTION
	    echo "ACTION='$ACTION'" >>$FFLOG
	  done
	  #
	  kill $COPROC_PID >/dev/null
	  grep -v "FE_HAS_LOCK" $ZAPLOG >>$LOGFILE
	  tail --lines=1 $ZAPLOG >>$LOGFILE
	  cat $FFLOG >>$LOGFILE
	done
exit 0 

```

There's another script, using tzap and ffplay in the same manner, that can tune to and play the same channel but using a different adapter.

Using these scripts I have determined that, if playback starts "broken" as described in the OP, restarting ffplay (but not tzap) does not solve the problem. The results also show that the problem can occur on any frequency.

However, if another adapter is tuned to the same channel, even while the original is still playing but broken, the playback on the different adapter is good. So it's not a signal quality issue.

The tzap logs show that, once an adapter is tuned, status 1f and FE_HAS_LOCK are maintained along with good signal strength, irrespective of whether the ffplay output is good or broken.

So it would appear that occasionally the transport stream is invalid or incomplete in some way that makes it impossible for Mythtv, mplayer, or ffplay to produce correct playback.

How do Mythtv BE or mplayer tune adapters, do they invoke tzap?

Any suggestions as to the cause of this problem or how I could identify the fault(s) in the stream?

The logs are very long (50k lines!) due to the blizzard of decode errors so not included in post. Would an example of the broken video file be of interest? Although I'm not sure how I would provide that.

mods: Does this belong on a different forum? if so, where?

---

### Post by nickrout on 2012-02-06
Are the channels encrypted?

Does the binary closed driver comply with the linux usual kernel api model?

---

### Post by ecwanet on 2012-02-06
nickrout:
None of the channels are encrypted. I used scan to generate the channels.conf, specifying -x 0 (only FTA channels) and -t 1 (TV only).

I understand your question about the API model but I'm not expert enough in that area to answer it. But with regard to the drivers, when the first module, dvb-core, is loaded there is a message about the media stack version. I don't really understand it, nor the following message about backporting. A snippet from dmesg covering the loading of all the drivers for this card is here

```
[   17.587784] WARNING: You are using an experimental version of the media stack.
[   17.587785] 	As the driver is backported to an older kernel, it doesn't offer
[   17.587786] 	enough quality for its usage in production.
[   17.587787] 	Use it with care.
[   17.587787] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[   17.587788] 	7e58b3e9d49b9a447eba9d8ba6f1d40f002d53e7 Merge tag 'v3.1' into staging/for_v3.2
[   17.587789] 	c3b92c8787367a8bb53d57d9789b558f1295cc96 Linux 3.1
[   17.587790] 	6a0596583fadd15dca293736114abdea306d3d7c Merge git://git.infradead.org/iommu-2.6
[   17.896039] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   17.907213] ata1.00: configured for UDMA/133
[   17.920022] ata1: EH complete
[   18.783173] SAA7231 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.783181] SAA7231 0000:05:00.0: setting latency timer to 64
[   19.072025] DVB: registering new adapter (SAA7231 DVB External Adapter:1)
[   19.384646] DVB: registering adapter 0 frontend 0 (Sony CXD2820R (DVB-T/T2))...
[   19.400038] DVB: registering new adapter (SAA7231 DVB External Adapter:0)
[   19.713552] DVB: registering adapter 1 frontend 0 (Sony CXD2820R (DVB-T/T2))...
[   19.728072] SAA7231 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.728079] SAA7231 0000:06:00.0: setting latency timer to 64
[   20.020022] DVB: registering new adapter (SAA7231 DVB External Adapter:1)
[   20.329547] DVB: registering adapter 2 frontend 0 (Sony CXD2820R (DVB-T/T2))...
[   20.345400] DVB: registering new adapter (SAA7231 DVB External Adapter:0)
[   20.750976] DVB: registering adapter 3 frontend 0 (Sony CXD2820R (DVB-T/T2))...

```

Some weeks ago I googled the "experimental media stack" message and got some hits but none for this particular device so I was unable to judge the severity of the caution. Any opinions?

I downloaded the 1.0.0.791 64bit linux drivers from the selection on this page [http://shop.blackgold.tv/epages/BT3159.sf/en_AU/?ObjectPath=/Shops/BT3159/Categories/Support/Current_Drivers](http://shop.blackgold.tv/epages/BT3159.sf/en_AU/?ObjectPath=/Shops/BT3159/Categories/Support/Current_Drivers)

How would I establish whether or not the drivers comply with the API model?

---

### Post by ecwanet on 2012-02-06
I've now found the origin of the "experimental media stack" message here [http://www.spinics.net/lists/linux-media/msg30481.html](http://www.spinics.net/lists/linux-media/msg30481.html) but the implications of the information on there are beyond my level of understanding of how this all hangs together, other than the fact that the BlackGold supplied dvb-core driver was compiled from code that contains the patch described.

Is it just something that should be borne in mind for the future or is it a serious flaw?

It might be more pertinent to ask whether this could have anything to do my problem of mashed up video playback.

Any suggestions?

---

### Post by nickrout on 2012-02-06
> **ecwanet said:**
> Ok, no suggestions yet so I have written a bash script to pick a TV channel at random, use tzap to tune to that channel then invoke ffplay (an ffmpeg utility) to decode and play the transport stream.

tzap runs as a co-process with the -r option so the stream is available on /dev/dvb/adapterN/dvrN and it keeps running on that channel until the script kills it.

When I terminate ffplay playback the script will retry playback of the same live stream, pick another channel, or quit according to my input.

```
#!/bin/bash
#
# zaploop
#
# This script uses tzap to tune to digital tv channels
# using the selected dvb adapter
# takes a parameter, adapter no (0 - 3) 
#
# pick a channel at random then tune to it
# output channel name & frequency plus some lines of tuning status and ffplay's stderr to a log file
# continue until cancelled
# 
	ADAPTER=$1	
	LOGFILE="zloop"$ADAPTER".txt"
	ZAPLOG="zaplog"$ADAPTER".txt"
	FFLOG="fferrs"$ADAPTER".txt"
	SAVE_IFS=$IFS
	IFS=$'\n'
#	extract channel name and freq into arrays	
	ALLCHANS=( $( sed 's/\(^[^:]*\).*/\1/' <channels.conf) )
	ALLFREQS=( $( sed 's/^[^:]*:\([^:]*\).*/\1/' <channels.conf) )
	IFS=$SAVE_IFS
	CHANS=${#ALLCHANS[@]}-1
	ACTION=""
	while [ "$ACTION" = "" ] ; do
#	pick a channel at random (not 1-4, they're HD)
	  IND=-1
	  while [ $IND -lt 4 ]; do
	    let "IND=$RANDOM%$CHANS"
	  done
	  CHANNEL=${ALLCHANS[$IND]}
	  echo "$(date +%F' '%T) $CHANNEL on ${ALLFREQS[$IND]}" >>$LOGFILE 
	  coproc tzap -a $ADAPTER -r -c channels.conf "$CHANNEL" >/dev/null 2>$ZAPLOG
	  ZPID=$COPROC_PID
	  # allow time to tune
	  sleep 2
	  echo "start ffplay for channel $CHANNEL"
	  echo $CHANNEL > zchan$ADAPTER.txt
	  echo "start ffplay for channel $CHANNEL" 1>$FFLOG
	  # decode and show with ffplay. 
	  # ESC to stop ffplay then "r" for a retry, "" for next channel, anything else exit script
	  ACTION="r"
	  while [ "$ACTION" = "r" ] ; do
	    ffplay -f mpegts /dev/dvb/adapter$ADAPTER/dvr0 -window_title "$CHANNEL on adapter $ADAPTER" 2>>$FFLOG
	    echo "$(date +%F' '%T) ffplay terminated ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~" >>$FFLOG
	    read ACTION
	    echo "ACTION='$ACTION'" >>$FFLOG
	  done
	  #
	  kill $COPROC_PID >/dev/null
	  grep -v "FE_HAS_LOCK" $ZAPLOG >>$LOGFILE
	  tail --lines=1 $ZAPLOG >>$LOGFILE
	  cat $FFLOG >>$LOGFILE
	done
exit 0 

```

There's another script, using tzap and ffplay in the same manner, that can tune to and play the same channel but using a different adapter.

Using these scripts I have determined that, if playback starts "broken" as described in the OP, restarting ffplay (but not tzap) does not solve the problem. The results also show that the problem can occur on any frequency.

However, if another adapter is tuned to the same channel, even while the original is still playing but broken, the playback on the different adapter is good. So it's not a signal quality issue.

The tzap logs show that, once an adapter is tuned, status 1f and FE_HAS_LOCK are maintained along with good signal strength, irrespective of whether the ffplay output is good or broken.

So it would appear that occasionally the transport stream is invalid or incomplete in some way that makes it impossible for Mythtv, mplayer, or ffplay to produce correct playback.

How do Mythtv BE or mplayer tune adapters, do they invoke tzap? I believe that they use their own code, but it may use ideas from tzap (I simply do not know). I guess you could track down the source code and see :) > 

Any suggestions as to the cause of this problem or how I could identify the fault(s) in the stream?

The logs are very long (50k lines!) due to the blizzard of decode errors so not included in post. Would an example of the broken video file be of interest? Although I'm not sure how I would provide that.


Could be a signal strength problem, with dropouts in the stream. 

My knowledge ends about there. You might try the mythtv-users mailing list.

---

### Post by ecwanet on 2012-02-07
> **nickrout said:**
> I believe that they use their own code, but it may use ideas from tzap (I simply do not know). I guess you could track down the source code and see :) 

Could be a signal strength problem, with dropouts in the stream. 

My knowledge ends about there. You might try the mythtv-users mailing list.

Track down the source code.... ummm (scratches head:confused:)

I don't believe it's a signal strength issue. I can get good playback of a mis-behaving channel/adapter for the same channel using another adapter on the same card at the same time. Somewhere on the dvb-apps documentation is says that a signal strength of over 0x8000 is required for reasonable playback. The captured tzap logs show ss varying between 0xb800 and 0xce00 or thereabouts.

I have managed to frighten up some interest on mythtv-users.

Thanks for your input.

---

### Post by ianc on 2012-02-10
OK... following up my post (nemo) on the mailing list.

I've tried out the script and can confirm the behaviour you're seeing: if the steam fails initially to lock properly it stays that way forever. Well, for as long as I can be bothered to keep stopping & restarting ffplay anyway.

It's interesting that the card is OK under Win7 - that I guess implies a problem with the 1.0.0.791 driver. Shame it's closed-source.

I'm running out of ideas to be honest - I've eliminated (at least to my satisfaction) all the other possible causes I can think of: signal strength/signal-noise ratio, interference, channel configuration, etc.

---

### Post by ecwanet on 2012-02-12
In reply to an earlier question by nickrout, the documentation associated with the 0.790 drivers indicates that they require the dvb API to be v 5.0 minimum. I would not expect the 0.791 to be lower.

I have altered my bash scripts (see earlier post) to select a channel name at random and fire off tzap for that channel to record the stream from one adapter to disk for 30 secs and then two secs later start another tzap for the same channel, also recording 30 secs worth from another adapter (on the same card). This iterates 100 times, writing a log of start time, frequency and channel name.

When that finishes I start a script to read the log file and play back with ffplay all the recorded files for one of the adapters, logging decode errors to a separate file for each recording. Another instance of this script is run concurrently (just to save time) on the recordings made from the other adapter.

When the playbacks all finish I start a third script, also driven by the list of randomly selected channels, to check and record the line counts of the playback error logs, and marking as bad those having more than 1000 errors. The results are written to another file.

I will post the scripts and/or full results if anyone wants a look.

Analysis of the final file is quite revealing. The reason for tuning two adapters to the same channel concurrently is an attempt to rule out signal variations as a factor. 

So I have changed channel 200 times (100 names, 2 adapters), 26 of those changes led to bad recordings. 

Only once did both adapters produce bad recordings for the same channel at the same time. 

The rates of bad recordings for the two adapters were the same.

Being aware that with UHF transmissions the higher frequency bands tend to give lower signal strength, I decided to split out the successes and failures by frequency. This showed that the proportion of failures did not increase with frequency. However, it did show that the failure rate with multiplexes 2 and A was fairly low whereas on muxes 1, B, C, and D it was greater than 30%. 

The differentiating factor seems to be the constellation (QAM). From Crystal Palace, Muxes 2 and A are 64QAM whereas 1, B, C, and D are 16QAM. I have not checked other transmitters.

I must include the HD channels in my next test as they are 256QAM.

I am pleased to have discovered this factor but does it point towards a resolution of the problem? 

Any pearls of wisdom would be greatly appreciated.

---

### Post by ianc on 2012-02-13
Another possibly interesting analysis would be to look at whether there's any correlation with what the tuner's switching from & to (i.e. changing channels within a mux or changing from one mux to a different one that uses the same transmission mode or changing from one mux to a different one that uses a different transmission mode).

If you can post your scripts up somewhere I'll give them a whirl - my machine's sitting there not doing anything pending sorting this issue out so I might as well fire it up and gather some more data.

---

### Post by ecwanet on 2012-02-13
ianc, we are thinking along the same lines re further testing. Another useful test would be changing channel within the same mux.

Here are the three scripts. They expect to find a subdirectory called ztesting. First is the duplex tzap script. It is hardcoded to use adapters 0 & 1 in this version. I've added a line to pick out the QAM parameter in anticipation of the next testing phase but it's not used anywhere yet.

```
#!/bin/bash
#
# zap2loop
#
# This script uses tzap to tune to digital tv channels and record a segment of the stream
# using two dvb adapters
#
# pick a channel at random then tune to it
# output channel name & frequency plus some lines of tuning status
# continue until cancelled
# 
	LOGFILE="ztesting/z2loop.txt"
	touch $LOGFILE
	SAVE_IFS=$IFS
	IFS=$'\n'
#	extract channel name, freq, QAM_?? into array	
	ALLCHANS=( $( sed 's/\(^[^:]*\).*/\1/' <channels.conf) )
	ALLFREQS=( $( sed 's/^[^:]*:\([^:]*\).*/\1/' <channels.conf) )
	ALLQAMS=( $( sed 's/.*:\(QAM_[0-9]*\):.*/\1/' <channels.conf) )
	IFS=$SAVE_IFS
	CHANS=${#ALLCHANS[@]}-1
	CHANNEL=""
	PREVCHAN=""
	for (( I=0; $I<100; I++)); do
#	  pick a channel at random (not 1-4, they're HD. ffplay fails on HD, settings need some work)
	  IND=-1
	  while [[ $IND -lt 4 || $CHANNEL == $PREVCHAN ]]
	  do
	    let "IND=$RANDOM%$CHANS"
	    CHANNEL=${ALLCHANS[$IND]}
	    FREQ=${ALLFREQS[$IND]}
	  done
	  PREVCHAN=$CHANNEL
	  TSTMP=( $( echo $( date +%F_%T) ) )
	  PREF=$( echo _$TSTMP $FREQ $CHANNEL | sed -e 's/[ ]/_/g' -e 's/*/star/' )
	  echo "$PREF" >>$LOGFILE 
#	  invoke 2 x tzaps to tune same channel and write to a file for a while
	  coproc tzap -a 0 -c channels.conf -t 30 -o "ztesting/0$PREF.ts" "$CHANNEL" 2>"ztesting/0$PREF.zlog"
	  PID=$COPROC_PID
	  sleep 2
	  tzap -a 1 -c channels.conf -t 30 -o "ztesting/1$PREF.ts" "$CHANNEL" 2>"ztesting/1$PREF.zlog"
#	  check myth BE hasn't started
	  if pgrep mythbackend	  
	  then
	    echo mythbackend is running
	    read ans
	  fi
	done
exit 0 
```

The log created by the script contains lines like this:
```
_2012-02-12_18:30:38_561833330_5_USA
```

After running zap2loop, the ztesting directory contains two recordings and two tuning logs for each of these entries. Recordings have suffix .ts, logs have suffix .zlog, and each is prefixed with the adapter number (0 or 1 in this case)

Then run this to read, decode and display the recordings for each set of files (0's and 1's):
```
#!/bin/bash
#
# ffrloop
#
# This script uses ffplay to play back digital tv channel stream segments recorded by tzap
# using the selected dvb adapter
# takes a parameter, adapter no (0 - 3) 
#
# read recording log containing file name prefices and attempt to play back files
# log the errors
# 
	ADAPTER=$1	
	LOGFILE="ztesting/z2loop.txt"
	for MID in $( cat "$LOGFILE"); do
	  PREF="$ADAPTER$MID"
#	  invoke ffplay to decode and display stream segments and write errors to a log file
	  echo $PREF
	  ffplay -f mpegts "ztesting/$PREF.ts" -autoexit -window_title "$PREF" 2>"ztesting/$PREF.flog"
#	  allow a moment between clips to cancel 
	  sleep 1
	done
exit 0 
```

ffplay puts a status line on stdout and updates it in place. Don't be tempted to use a redirect to trap it because that produces thousands of lines. I copied and pasted the stdout from the terminal window into a file after the script had completed. I haven't really looked closely at the meanings of the values, especially the "f=xx/xx". Example output of a good followed by a bad:

```
0_2012-02-11_00:12:18_QUEST
69845.64 A-V: -0.594 s:0.0 aq=    0KB vq=  160KB sq=    0B f=0/1   f=0/0   
0_2012-02-11_00:12:50_Channel_4
73556.78 A-V:  0.000 s:13.3 aq=    0KB vq=    0KB sq=    0B f=149/195      

```

Each recording will now have a playback log with suffix .flog and the third script, again hard-coded with 0 & 1, checks them:

```
#!/bin/bash
#
# fflogchk
#
# This script inspects the logs created by ffplay during playback of sequences of 
# tzap stream segments recorded in parallel across two adapters
# input is the log from zap2loop
#
# read recording log containing file name prefices and check the .flog file sizes
# large log means persistent stream faults
# 
	LOGFILE="ztesting/z2loop.txt"
	CHKFILE="ztesting/z2chk.txt"
	for MID in $( cat "$LOGFILE"); do
#	  get line counts for play back logs for adapters 0 & 1
	  C0=$( wc -l "ztesting/0$MID.flog" | sed 's/\(^[0-9]* \).*/\1/' )
	  C1=$( wc -l "ztesting/1$MID.flog" | sed 's/\(^[0-9]* \).*/\1/' )
	  OUTCOME=""
	  if [[ $C0 -gt 1000 ]] ; then OUTCOME=" 0_BAD"; fi 
	  if [[ $C1 -gt 1000 ]] ; then OUTCOME="$OUTCOME 1_BAD"; fi 
	  printf "%-55s %8s %8s %s\n" "$MID" "$C0" "$C1" "$OUTCOME" >>$CHKFILE
	done
exit 0 
```

It outputs a file with entries like this:

```
_2012-02-12_18:32:47_537833330_ITV4                        7644       36   0_BAD

```

In this example the recording on adapter 0 was rubbish whereas the one on adapter 1 was fine.

The analysis of my results split by muxes is as follows:

```
"UK Mux" "QAM"  "no. of times tuned to"  "bad recordings"
   1      16         28                      6
   2      64         40                      1
   A      64         58                      4
   B      16         16                      3
   C      16         34                      7
   D      16         24                      5

```
I stated incorrectly in my previous post that the failure rate on 16QAM was over 30%. But as each channel was tuned to on two adapters my "no. of times tuned" should have been doubled. The figures in this post are correct.

I'm not sure that the duplex tuning is required any more. I believe I have proved that it's not a signal quality related problem. Any views?

I'm afraid Bash scripting is not the best arrow in my quiver so the coding is somewhat ham-fisted. But if they can help lead to a resolution then who cares? As the machine with this card installed is dual boot I will have another crack with Win7 Media Centre to see whether I can scare up any failures.

---

### Post by ecwanet on 2012-02-13
This post is from within Windows 7 and I have just closed Media Centre having swapped channels dozens of times across all the muxes including HD using the BGT3650 card, all without a single instance of bad video or audio quality (from a technical point of view that is, not a matter of personal taste:)).

So it's back to looking at the Linux drivers, tuners, and decoders.

---

### Post by ianc on 2012-02-15
Thanks for the scripts & I confirm I get similar results so it seems highly likely that we're seeing the same problem.

My card's about to head back to Blackgold to be checked out: I'll try to post again once I know more...

---

### Post by ianc on 2012-04-09
Just to tidy up this thread:

At their request I sent my card back to Blackgold for some unspecified changes to be made & subsequently it was returned to me within a couple of days.

Unfortunately it still showed the same problems, so it then went back permanently...

I've since installed a PCTV nanoStick T2 290e in addtion to my Nova-T 500, and it's working fine. It's a bit second-choice (I really wanted to have just one internal card rather than a mix of internal card + external usb), but it'll do for now.

---

### Post by Fruitysoup on 2012-05-06
Just my 2c

I too have had these problems, and running the tests showed a 15-20% failure rate in the records. I've tried to get in contact with the BGT support, but I've had next to no contact in over 3 weeks. :-(

---

