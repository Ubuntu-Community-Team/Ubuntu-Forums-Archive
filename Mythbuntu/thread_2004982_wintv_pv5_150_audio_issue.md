---
title: "wintv pv5 150 audio issue"
date: 2012-06-16
forum: Mythbuntu
---

### Post by someitalian123 on 2012-06-16
I don't have this issue all the time, it's about 1 out of every 20 times I change the channel. Here's a sample so you understand what the audio problem is.

[http://www.mediafire.com/?33jto320561o2f9](http://www.mediafire.com/?33jto320561o2f9)

I found this 

[http://www.mythtv.org/wiki/Hauppauge_PVR-150#Issues_and_Problems](http://www.mythtv.org/wiki/Hauppauge_PVR-150#Issues_and_Problems)

"There can be intermittent problems with the audio encoder, causing the audio track to have a "tinny" sound every 10-20 channel changes. A known workaround is to place the following code at the end of your channel changer script (typically /usr/bin/changechannel.sh) which resets the audio input to the PVR-150 encoder:"
```

sleep 5; v4l2-ctl --set-audio-input 1 -d /dev/video0 > /dev/null 2>&1
```

I have already added that to the end of my script but I'm still having this issue with the audio every once in awhile. Did I add at the wrong spot? Is there something else wrong with my script?

```
     #! /bin/sh
     # Shell script used to send channel change commands to a set top box (STB)
     # or digital transport adapter (DTA) via LIRC.
     #
     # This script is commonly used by applications such as Myth TV to change
     # the channels on a STB/DTA when the STB/DTA must be used to convert the
     # channels that a subscriber can see to a single channel (e.g. when
     # digital channels are to be viewed by the application on channel 3 with
     # an analog decoder card).
     #
     # The application invokes this script and passes the channel number to it
     # as the first parameter.  This script deconstructs the channel number and
     # decides what command sequence the STB/DTA's remote would have to send in
     # order to change to that channel (typically its the channel number,
     # followed by the Enter button).  It sends the channel change commands to
     # the STB/DTA through the IR blaster that was started by lircd.  The
     # information necessary to do this is obtained from the lircd config file
     # /etc/lirc/hardware.conf.
     #
     # If you need to send commands to a different IR emitter than number 1,
     # you can alias this script and use the aliases to send to any emitter
     # from 1 thru 4.  You must set up the aliases as follows:
     #
     #   ln -s IRChangeChannel IR1ChangeChannel
     #   ln -s IRChangeChannel IR2ChangeChannel
     #   ln -s IRChangeChannel IR3ChangeChannel
     #   ln -s IRChangeChannel IR4ChangeChannel
     #
     # You can then send commands to the alternate emitters as follows:
     #
     #   /path/to/scripts/IR1ChangeChannel 12
     #   /path/to/scripts/IR2ChangeChannel 22
     #        .
     #        .
     #        .
     #
     # Because of the nature of the way that the program name is determined,
     # you must use some kind of path prefix on the name (i.e. at the very
     # least, use "./IR3ChangeChannel 44").
     #
     # Note that, unless you are using stereo emitters on the IguanaIR, the two
     # emitters on the stick are IR1 and IR3 (two and four are not used).
     #
     # Some DTAs do not change the channel reliably, every time.  Or, they do it
     # fine with one IR blaster and not another.  In this case, if they typically
     # miss some digits and do nothing because of it (i.e. stay on the same
     # channel that they were originally on), you can set CHANGE_TRIES to
     # something other than one (below).  This will cause the script to try
     # changing the channel the number of times given and, hopefully, one will
     # stick.
     ##########################################################################
     # Constants that define how this script works.  Set these up once at
     # install time.
     # Where we load irsend from (depends whether this is a system install or
     # a local build).
     #ew LOAD_PATH=/usr/bin
     LOAD_PATH=/usr/bin
     # The delay (in seconds) that we should sleep between each key press (a
     # half a second seems to be a reasonable number).
     KEY_DELAY=0.5
     # The number of times this script should try changing the channel (see
     # above).
     CHANGE_TRIES=1
     # See if we can find the send module in the place where the user told us to
     # look.  If not, we're outta here quick.
     test -f ${LOAD_PATH}/irsend || exit 0
     # The user can symlink to this program to use an emitter other than 1.  We
     # figure this out from our invoking program name.
     Emitter=0
     ProgName=`echo $0 | sed -r s:.+/\([^/]+\)$:\\\1:`
     if [ ! -n "$ProgName" ] || [ "$ProgName" = "IRChangeChannel" ]; then
         Emitter=1
     else
         case "$ProgName" in
             IR1ChangeChannel)
                 Emitter=1
                 ;;
             IR2ChangeChannel)
                 Emitter=2
                 ;;
             IR3ChangeChannel)
                 Emitter=3
                 ;;
             IR4ChangeChannel)
                 Emitter=4
                 ;;
             *)
                 Emitter=1
         esac
     fi
     # Let's get the config file that was used to start lircd with.  It will
     # tell us what remote we're using (hopefully).
     if [ -f /etc/lirc/hardware.conf ]; then
         . /etc/lirc/hardware.conf
     fi
     # We need a remote name.
     if [ -z "$TRANSMITTER" ] || [ "$TRANSMITTER" = "none" ]; then
         exit 0
     fi
     # Figure out where the transmitter is.
     if [ -n "$PIPE_PATH" ] && [ "$PIPE_PATH" != "none" ]; then
         DEV_PATH=$PIPE_PATH
     else
         DEV_PATH="/var/run/lirc"
     fi
     # If there's a transmitter device or driver defined, the lirc init script
     # started a second copy of lircd.
     if [ ! -z "$TRANSMITTER_DEVICE" ] \
         || [ ! -z "$TRANSMITTER_DRIVER" ]; then
         DevArgs="--device=$DEV_PATH/lircd1"
     else
         DevArgs="--device=$DEV_PATH/lircd"
     fi
     # Select the appropriate IR emitter on the device.
     ${LOAD_PATH}/irsend $DevArgs set_transmitters $Emitter
     # Try setting the channel the number of times the user has requested us to
     # do so (some DTAs with some blasters don't get the message the first
     # time).
     Tries=1
     while [ $Tries -le $CHANGE_TRIES ]; do
      # Send the channel number.
      for Digit in $(echo $1 | sed -e 's/./& /g'); do
          case "$Digit" in
              1)
                  Key="One"
                  ;;
              2)
                  Key="Two"
                  ;;
              3)
                  Key="Three"
                  ;;
              4)
                  Key="Four"
                  ;;
              5)
                  Key="Five"
                  ;;
              6)
                  Key="Six"
                  ;;
              7)
                  Key="Seven"
                  ;;
              8)
                  Key="Eight"
                  ;;
              9)
                  Key="Nine"
                  ;;
              *)
                  Key="Zero"
          esac
          ${LOAD_PATH}/irsend $DevArgs send_once $TRANSMITTER $Key
          sleep 0.5
      done
      # Send the enter key.
      ${LOAD_PATH}/irsend --device=/dev/lircd SEND_ONCE $TRANSMITTER Enter
      if [ $Tries -lt $CHANGE_TRIES ]; then
          sleep $KEY_DELAY
      fi
      # Increment the try count, in case we're doing this more than once.
      Tries=`expr $Tries + 1`
     done

sleep 5; v4l2-ctl --set-audio-input 2 -d /dev/video2501 > /dev/null 2>&1
```

---

### Post by nickrout on 2012-06-16
When I had a PVR150 I used to run the v4l line once every 10sec by a cron script. (cron can set something to run every minute, so the script was someting like

```
for X in 1 2 3 4 5 6;
do v4l2-ctl --set-audio-input 1 -d /dev/video0 > /dev/null 2>&1
sleep 10;
done
```

---

### Post by someitalian123 on 2012-06-16
> **nickrout said:**
> When I had a PVR150 I used to run the v4l line once every 10sec by a cron script. (cron can set something to run every minute, so the script was someting like

```
for X in 1 2 3 4 5 6;
do v4l2-ctl --set-audio-input 1 -d /dev/video0 > /dev/null 2>&1
sleep 10;
done
```

Wouldn't running a script every 10 seconds take up a lot of extra processing power though?

---

### Post by someitalian123 on 2012-06-16
I found this patch, but I don't want to try and apply it because it's from 2009 and I'm not sure if it will work or it will break everything. Also this looks complicated and I have a feeling it's beyond me.

[http://www.mythtvtalk.com/pvr-150-audio-issues-w-patch-12183/](http://www.mythtvtalk.com/pvr-150-audio-issues-w-patch-12183/)

If a patch exists why hasn't this been fixed upstream yet?

---

### Post by nickrout on 2012-06-17
> **someitalian123 said:**
> Wouldn't running a script every 10 seconds take up a lot of extra processing power though?

No. Have you seen the number of processes your system is running already?

---

### Post by ck102 on 2012-06-21
I have the following added to the bottom of my change channel script for the pvr-150

```
( sleep 4; v4l2-ctl --set-audio-input 1 -d /dev/video-pvr150 > /dev/null 2>&1 ) &

```
 The round braces and ampersand sign cause the change channel script to end and returning control to mythtv immediately.  Then 4 seconds later the v4l2-ctl is run while mythtv is recording.

Once in a while I will hear the static for a second or two, but then it clears up for the rest of the recording.

---

### Post by someitalian123 on 2012-06-22
> **ck102 said:**
> I have the following added to the bottom of my change channel script for the pvr-150

```
( sleep 4; v4l2-ctl --set-audio-input 1 -d /dev/video-pvr150 > /dev/null 2>&1 ) &

```
 The round braces and ampersand sign cause the change channel script to end and returning control to mythtv immediately.  Then 4 seconds later the v4l2-ctl is run while mythtv is recording.

Once in a while I will hear the static for a second or two, but then it clears up for the rest of the recording.

I' think it's working, do get the tiny audio sometimes when I change channels but it disappears after about 5 seconds

---

