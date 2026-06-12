---
title: "Earthsoft PT2 (Japanese ISDB-T/S Capture Card)"
date: 2012-09-08
forum: Multimedia Software
---

### Post by quequotion on 2012-09-08
This is an update to my [previous thread]("http://ubuntuforums.org/showthread.php?p=11398328").

I have managed to get the card working in Ubuntu 12.04.

The process is a bit easier this time, though quite *mendokusai* (troublesome).


[SIZE=3]**Part one - Setup**[/SIZE]

First of all, you're going to need the hardware:

1 **Earthsoft PT2** (although the process shouldn't be much different for pt1 or pt3)
1 **PCSC card reader** (lots of companies sell these)
1 **B-CAS card** (only available *with* a digital television, set-top box, or capture card; the [COLOR=Red]RED[/COLOR] one covers terrestrial and satellite broadcasting, the [COLOR=DeepSkyBlue]BLUE[/COLOR] one only terrestrial, i don't know which color covers cable)
1 **Computer** with enough CPU and/or GPU to decode the stream, and a monitor to watch it on (which is really beyond the scope of this tutorial).

Install PCSC daemon, tools, and development files:```
sudo apt-get install libccid libpcsclite-dev pcsc-tools pcscd
``` The latest versions should be fine!
[s]Newer versions of these packages are dangerous and broken. Install the versions from Maverick:```
mkdir pcsc-debs
cd pcsd-debs
wget http://launchpadlibrarian.net/35198253/libccid_1.3.11-1_amd64.deb
wget http://launchpadlibrarian.net/70522546/libpcsclite-dev_1.5.5-3ubuntu2.1_amd64.deb
wget http://launchpadlibrarian.net/70522551/libpcsclite1_1.5.5-3ubuntu2.1_amd64.deb
wget http://launchpadlibrarian.net/70522552/pcscd_1.5.5-3ubuntu2.1_amd64.deb
wget http://launchpadlibrarian.net/38659322/pcsc-tools_1.4.16-1_amd64.deb
sudo dpkg -i *.deb
cd ..
```Create apt-pins to keep them at those versions (in **/etc/apt/preferences.d/pcsc**)```
Package: libccid
Pin: version 1.3.11-1
Pin-Priority: 1001

Package: libpcsclite-dev
Pin: version 1.5.5-3ubuntu2.1
Pin-Priority: 1001

Package: libpcsclite1
Pin: version 1.5.5-3ubuntu2.1
Pin-Priority: 1001

Package: pcscd
Pin: version 1.5.5-3ubuntu2.1
Pin-Priority: 1001

Package: pcsc-tools
Pin: version 1.4.16-1
Pin-Priority: 1001
```[/s]You will need mercurial to use the repository, autoconf and automake for one of the compiles:```
sudo apt-get install mercurial autoconf automake
```Get the source code for "b25", an AIRB decryption program and library.```
hg clone http://hg.honeyplanet.jp/pt1 b25
```Make and install b25```
cd b25
hg update b25
cd arib25
make
make install
cd ../..
```Get the source code for the PT2 Driver and recpt1, the capture program.```

hg clone http://hg.honeyplanet.jp/pt1 PT2
```make  and install the driver```
cd PT2/driver
make
sudo make install 
cd ../..
```make and install recpt1```
cd PT2/recpt1
./autogen.sh
./configure --enable b25
make
sudo make install
cd ../..
```Finally, blacklist the outdated (though functional) v4l-dvb pt1 driver ( in **/etc/modprobe.d/blacklist-pt1**):```
blacklist earth_pt1
```This is a good time to reboot.

[SIZE=3]**Part 2 - Testing**[/SIZE]
[SIZE=2][s]**Important**: If Ubuntu will not reboot after the above process, you probably have the new PCSC packages. They are seriously broken; the latest version of the PCSC driver will freeze udev if a USB PCSC card reader is attached at boot. Disconnect the device and use the power button to reboot; make sure to downgrade those packages.[/s]
**Also Important**: Make sure everything is connected to the right connection, on, and functioning, particularly that something is connected to at least one of the PT2's 4 coaxial terminals (Sattelite1, Terrestrial1, Sattelite2, Terrestrial2).

Find a working channel:```
checksignal 0
```Keep increasing the number until you find one that works.

Try to record 10 seconds of channel 14 (NHK in Oita; use a channel that's available in your region):[/SIZE]```
recpt1 --b25 --strip 14 10 test.ts
```If this says "Fall back to encrypted recording" then there's a problem with the PCSC card reader.
Make sure the card is in the right way.
Make sure it's connected to the PC properly.
[s]Make sure you installed the old pcsc packages.[/s]
Check if it's working:```
sudo pcsc_scan
```If it worked, but the file is 0 bytes, check the PCSC card reader anyway, reboot, and try again.
If it worked, and the file is really a video (*a high-definition MPEG-2 or MPEG-4 transport stream to be precise*), play it with either **mplayer** or **vlc** (gstreamer, ie **totem**, is unlikely to work with this format)

If it works, you are ready to watch and record as much Japanese TV as you like.

**Useful**: You can output to stdout, pipe it through vlc/mplayer, and play stdin like this:```
recpt1 --b25 --strip 14 10 - | mplayer -
recpt1 --b25 --strip 14 10 - | vlc -
```To record or watch indefinetly, replace the timer with "-"```
recpt1 --b25 --strip 14 - - | vlc - 
```Take a look at ```
recpt1 --help
recpt1ctl --help
```**recpt1ctl** is particularly useful for changing channels, BUT it's not that easy: *different channels may be using different encodings*.
For example, in my area NHK broadcasts a particular type of MPEG-4 Transport Stream on two channels, but the local stations broadcast *different* MPEG-2 Transport Streams. [s]So one can change channels between the NHK stations while watching the stream in either mplayer or vlc, but changing to any local station, from NHK or any other local station (and therefore suddenly changing the video encoding) will crash either player.[/s] Crashing on channel change is fixed in vlc-git!

---

### Post by quequotion on 2012-09-08
I wrote this script using cVLC's MPRIS dBus interface (to avoid on-screen controls). VLC surprised me by auto-magically integrating with the sound indicator. Apparently the sound indicator is listening for MPRIS.

I set the different options to hotkeys so I can use my wireless keyboard as a remote control; better ideas are welcome. LIRC?

[Super]+[Play/Pause] = digitv on
[Super]+[up] = digitv chanup
[Super]+[down] = digitv chandown

Remote Control Script (in **/usr/local/sbin/digitv**):
```
#! /bin/bash
# This script controls an Earthsoft PT-series capture card

CHANNEL=`cat ~/.digitvrc`

ONSTATE="`qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.CanQuit`" #If vlc can quit, then it is on.

case "$1" in

    on) # Open or close PVR stream.
        if [ "$ONSTATE" == "true" ]; then
            qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Quit #If vlc is on, turn it off.
        else
            recpt1 --b25 --strip $CHANNEL - - | cvlc -I dbus --fullscreen - #Record stream to stdout, pipe to cvlc stdin
        fi
    ;;

# This is a list of terrestrial broadcasting channels from my area.
# This could be done better and, for longer channel lists, must be.

    chanup) # Raise channel

        case "$CHANNEL" in

            14)
                CHANGE=15
            ;;

            15)
                CHANGE=22
            ;;

            22)
                CHANGE=32
            ;;

            32)
                CHANGE=34
            ;;

            34)
                CHANGE=14
            ;;

            *)
                CHANGE=`cat ~/.digitvrc`
        esac

        echo $CHANGE > ~/.digitvrc #Save current channel

        if [ "$ONSTATE" == "true" ]; then
            qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Quit #If vlc is on, turn it off (just in case we are switching encodings)
            sleep 2
            recpt1 --b25 --strip $CHANNEL - - | cvlc -I dbus --fullscreen - #Record stream to stdout, pipe to cvlc stdin
        else
            exit 0;
        fi
    ;;

    chandown) # Lower channel

        case "$CHANNEL" in

            34)
                CHANGE=32
            ;;

            32)
                CHANGE=22
            ;;

            22)
                CHANGE=15
            ;;

            15)
                CHANGE=14
            ;;

            14)
                CHANGE=34
            ;;

            *)
                CHANGE=`cat ~/.digitvrc`
        esac

        echo $CHANGE > ~/.digitvrc

        if [ "$ONSTATE" == "true" ]; then
            qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Quit #If vlc is on, turn it off (just in case we are switching encodings)
            sleep 2
            recpt1 --b25 --strip $CHANGE - - | cvlc -I dbus --fullscreen - #Record stream to stdout, pipe to cvlc stdin
        else
            exit 0;
        fi
    ;;

    *) # Catch bad input.
        notify-send --icon=error --urgency=critical --expire-time=1000 "TV: Invalid input" "Tuner not initialized"
        exit 0;
    ;;

esac

exit 0;
```Don't forget to make it executable:```
sudo chmod +x /usr/local/sbin/digitv
```

---

### Post by quequotion on 2012-09-09
I put together a rudimentary channel scanner:```
#!/bin/bash

for i in {0..62..1};  # 0 through 62, to check the Terrestrial Channels. You cold specify more if you have Satellite or Cable channels.
    do
        echo -e \\n$i >> ~/channels # channel number
        checksignal $i &>> ~/channels & # check frequency
        sleep 10 # this isn't enough time for a thorough scan, but picks up significantly strong signals.
        killall checksignal 
    done
```

---

### Post by quequotion on 2012-09-11
TV is working very well with this setup:

Chipset: Z68
CPU: Core I7 2770k, oc ~4.8GHz
GPU: GeForce GT 220, oc 700MHz clock and 900MHz memclock
SPU: SB Live! Audigy Value! 5.1, Analog 5.1 output.
Proprietary drivers for nVidia: 304.43
Kernel: 3.5.0-8-generic (#8-Ubuntu SMP Sat Aug 4 06:44:57 UTC 2012) AMD64
cVLC: 2.0.4 Twoflower (revision 2.0.3+git20120908+r378)
libva-driver-vdpau: 0.7.4.pre1-1 
libva1: 1.015-4

---

### Post by quequotion on 2012-09-19
Improvements to the controller script (in /**usr/local/sbin/digitv**):```
#! /bin/bash
# This script contols an Earthsoft PT-series ISDB-T/S capture card

CHANNEL=`cat ~/.digitvrc` #Get last channel

ONSTATE="`qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.CanQuit`" #Is the stream already on?

case "$1" in

    on)  #Initiate OR terminate video stream.
        if [ "$ONSTATE" == "true" ]; then
            qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Quit
            notify-send --icon=video-display-symbolic --urgency=critical --expire-time=700 "TV: OFF"
        else
            notify-send --icon=video-display-symbolic --urgency=critical --expire-time=700 "TV: ON" "CH: $CHANNEL" &
            recpt1 --b25 --strip $CHANNEL - - | cvlc -I dbus --fullscreen - &
        fi
    ;;

# This is a list of terrestrial broadcasting channels from my area. # This could be done better and, for longer channel lists, must be.

    chanup) # Raise channel

        case "$CHANNEL" in

            14)
                CHANNEL=15
            ;;

            15)
                CHANNEL=22
            ;;

            22)
                CHANNEL=32
            ;;

            32)
                CHANNEL=34
            ;;

            34)
                CHANNEL=14
            ;;

            *)
                notify-send --icon=error --urgency=critical --expire-time=1000 "TV: Invalid channel" "Dial reset"
                CHANNEL=14
            ;;
        esac

        if [ "$ONSTATE" == "true" ]; then
            qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Quit 
            notify-send --icon=video-display-symbolic --urgency=critical --expire-time=700 "TV: CH+" "CH: $CHANNEL"
            echo $CHANNEL > ~/.digitvrc
            recpt1 --b25 --strip $CHANNEL - - | cvlc -I dbus --fullscreen - &
        fi
    ;;

    chandown) # Lower channel

        case "$CHANNEL" in

            34)
                CHANNEL=32
            ;;

            32)
                CHANNEL=22
            ;;

            22)
                CHANNEL=15
            ;;

            15)
                CHANNEL=14
            ;;

            14)
                CHANNEL=34
            ;;

            *)
                notify-send --icon=error --urgency=critical --expire-time=1000 "TV: Invalid channel" "Dial reset"
                CHANNEL=14
            ;;
        esac

        if [ "$ONSTATE" == "true" ]; then
            qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Quit 
            notify-send --icon=video-display-symbolic --urgency=critical --expire-time=700 "TV: CH-" "CH: $CHANNEL"
            echo $CHANNEL > ~/.digitvrc
            recpt1 --b25 --strip $CHANNEL - - | cvlc -I dbus --fullscreen - &
        fi
    ;;

    *) # Catch bad input.
        notify-send --icon=error --urgency=critical --expire-time=1000 "TV: Invalid input"
    ;;

esac

exit 0;
```I've fixed a few logic errors in the chanup and chandown algorithms, pulled out the sleeps, and added a couple of notify-osd popups. This feels more interactive, changes channels faster, and handles a few oddities better--like when a channel has stopped broadcasting.

I'd still like to streamline this a bit more and add a few features. In particular:

1. Check if channels are using the same encoding before changing channels. If they are, then recpt1ctl could be used for a smoother, faster change. Alternatively, if vlc could somehow handle sudden encoding changes, *if that is even possible*, recpt1ctl could do all channel changes.

2.  A more precise method to find ONSTATE; as in checking if the card is currently streaming video.

3. Consolidate the on switch and channel change stream activations. Basically the same thing is going on here, except that the initial activation doesn't need to save the channel and the channel change requires some delay or the stream will break.

4. Actually say something if a channel is not broadcasting, rather than just leaving the screen blank.

5. Add a stream & record function. VLC can record a playing video stream, but the MPRIS specification doesn't include a "record" function.

6. Translate the script and this entire thread into Japanese. It's very likely the number of English-speaking people using these cards can be counted on one hand.

---

### Post by quequotion on 2012-09-25
Outstanding issues:

1. Attempting to watch a program with bilingual audio in VLC, I ran into: ```
Multiple blocks per frame in ADTS not supported
```Patches for this are available and on their way into git. In the mean time take a look at [this VLC forum thread]("http://forum.videolan.org/viewtopic.php?f=4&t=104504&p=353827#p353836") for nkoriyama's patches and pre-built binaries.
Bilingual audio works and can be selected from vlc's right-click menu under Audio-> Audio Channels-> Stereo (simultaneous bilingual), Left (Japanese), Right (native language).

2. Sometimes while changing channels using the script above (digitv chanup / chandown), the arib25 library and pcsc card reader stop working together.
I suspect that some channels use different encryption or occasionally change encryption and the pcsc card reader is still decrypting for the previous algorithm. This should not be happening, since I've already terminated the stream once and restarted it. The solution for now, when changing to an affected channel, is to restart again, (digitv on, digitv on). [s]I'm going to try again with pcsc-lite 1.8.5 from quantal.[/s]
-Good news / Bad news:  Bad first, 1.8.5 doesn't solve this problem. The good news is that 1.8.5 seems safe to use, [s]so perhaps Quantal will have functional pcsc card support.[/s] Or maybe not. libccid 1.4.7-1 (quantal) is broken.

---

### Post by quequotion on 2012-10-25
I've updated the control script again.

Big changes:

-using **recpt1ctl** to change channels: This is in fact the proper way, but changing to or from certain channels is crashing both vlc and mplayer. I suspect that they are using different encodings and suddenly switching them confuses the video player.

-vlc configured to always have the dbus interface available: This puts vlc into the indicator-sound menu, under rhythmbox, permanently and means it isn't necessary to explicitly create dbus interfaces in the script.

```
#! /bin/bash
# This script contols an Earthsoft PT-series ISDB-T/S capture card

CHANNEL=`cat ~/.digitvrc`

case "$1" in

    on) # Open or close PVR stream.
        if [ "`qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.CanQuit`" == "true" ]; then
            qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Quit &
            notify-send --icon=video-display-symbolic --urgency=critical --expire-time=700 "TV: OFF" &
        else
            notify-send --icon=video-display-symbolic --urgency=critical --expire-time=700 "TV: ON" "CH: $CHANNEL" &
            recpt1 --b25 --strip $CHANNEL - - | vlc --fullscreen - &
        fi
    ;;

    chanup) # Raise channel

        case "$CHANNEL" in

            14)
                CHANNEL=15
            ;;

            15)
                CHANNEL=22
            ;;

            22)
                CHANNEL=32
            ;;

            32)
                CHANNEL=34
            ;;

            34)
                CHANNEL=14
            ;;

            *)
                notify-send --icon=error --urgency=critical --expire-time=1000 "TV: Invalid channel" "Dial reset" &
                CHANNEL=14
            ;;

        esac

        echo $CHANNEL > ~/.digitvrc &
        notify-send --icon=video-display-symbolic --urgency=critical --expire-time=700 "TV: CH+" "CH: $CHANNEL" &
        if [ "`pgrep recpt1`" -gt 0 ]; then
            recpt1ctl --pid "`pgrep recpt1`" --channel $CHANNEL &
        fi

        sleep 8 # VLC takes 8 seconds to crash, for me

        if [ "`qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.CanQuit 2>&1 >/dev/null`" == "Service 'org.mpris.MediaPlayer2.vlc' does not exist." ]; then
            # Removed section A
            recpt1 --b25 --strip $CHANNEL - - | vlc --fullscreen - &
        fi
    ;;

    chandown) # Lower channel

        case "$CHANNEL" in

            34)
                CHANNEL=32
            ;;

            32)
                CHANNEL=22
            ;;

            22)
                CHANNEL=15
            ;;

            15)
                CHANNEL=14
            ;;

            14)
                CHANNEL=34
            ;;

            *)
                notify-send --icon=error --urgency=critical --expire-time=1000 "TV: Invalid channel" "Dial reset"
                CHANNEL=14
            ;;

        esac

        echo $CHANNEL > ~/.digitvrc &
        notify-send --icon=video-display-symbolic --urgency=critical --expire-time=700 "TV: CH-" "CH: $CHANNEL" &
        if [ "`pgrep recpt1`" -gt 0 ]; then
            recpt1ctl --pid "`pgrep recpt1`" --channel $CHANNEL &
        fi

        sleep 8 # VLC takes 8 seconds to crash, for me

        if [ "`qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.CanQuit 2>&1 >/dev/null`" == "Service 'org.mpris.MediaPlayer2.vlc' does not exist." ]; then
            # Removed Section B
            recpt1 --b25 --strip $CHANNEL - - | vlc --fullscreen - &
        fi
    ;;

    *) # Catch bad input.
        notify-send --icon=error --urgency=critical --expire-time=1000 "TV: Invalid input" &
    ;;

esac

exit 0;
```There were two new parts that I removed. These sections are nearly identical and do the same thing: check if a channel is broadcasting before changing to it. This is poorly implemented, takes as long as changing a channel twice, and sometimes gives false errors that a channel is unavailable. Without these sections, the expected behavior when a channel is not broadcasting is the channel will not change, but no message is output to express what has happened.

Removed section A```
#qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Quit
             #if [ "`recpt1 --b25 --strip $CHANNEL 0 /dev/null 2>&1  >/dev/null | grep channel`" == "Cannot tune to the specified channel"  ]; then
                #notify-send --icon=error --urgency=critical --expire-time=1000 "TV: CH+" "CH: $CHANNEL Unavailable" &
            #fi #this is so slow
            #sleep 1
```Removed section B```
#qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Quit 
             #if [ "`recpt1 --b25 --strip $CHANNEL 0 /dev/null 2>&1  >/dev/null | grep channel`" == "Cannot tune to the specified channel"  ]; then
                #notify-send --icon=error --urgency=critical --expire-time=1000 "TV: CH-" "CH: $CHANNEL Unavailable" &
                
            #fi #this is so slow
            #sleep 1
```

---

### Post by benmoran on 2012-11-25
Hi quequotion, 

Just wanted to say thanks for your awesome writeup. I currently have an Ubuntu 12.04/XMBC htpc that we've been using, and I really want to add an ISDB-T tuner to it. I've heard that the PT2s have a DVB-like driver that mimics the US standard, but I don't know much more than that. Any recommendations on how to get started? 

-Ben

---

### Post by quequotion on 2012-12-03
> **benmoran said:**
> Hi quequotion, 

Just wanted to say thanks for your awesome writeup. I currently have an  Ubuntu 12.04/XMBC htpc that we've been using, and I really want to add  an ISDB-T tuner to it. I've heard that the PT2s have a DVB-like driver  that mimics the US standard, but I don't know much more than that. Any  recommendations on how to get started? 

-Ben

Hello benmoran!

If you can read Japanese,  Google some guides by searching "&#12450;&#12540;&#12473;&#12477;&#12501;&#12488;PT1 Ubuntu" (minus quotes).  Unfortunately most of these guides are out of date and/or incomplete. 

There  is a DVB driver included in the kernel (earth-pt1), but it's not been  updated as recently as the honeyplanet driver (pt1-drv).  How  technologically similar either driver is to the US standard I don't  really know.  All the Japanese guides I can find recommend to blacklist  the kernel driver and use the honeyplanet driver instead.

If  you're looking for tips on getting set up, this thread has most of what  you need to know on the software side. The most difficult part is not  the system setup, but acquiring the hardware. Not many shops are selling  the PT-series cards, but they are available online. Unfortunately, they  don't come with a B-CAS card, and the cards are not for individual  sale, so you have to buy a *separate* device that includes one.

This  is actually a lot of trouble to go to just for watching TV, but that's  only one of several uses for the PT-series cards. These cards can be  used to record to disk and/or stream high-definition television through  your PC without the need to re-encode the original transmission. This  means your PC can be a DVR, a webcasting server, or both with zero  quality loss.

---

### Post by quequotion on 2012-12-03
New and very much improved control script!```
#! /bin/bash
# This script contols an Earthsoft PT-series ISDB-T/S capture card.

if [ ! -f ~/.digitvrc ]; then # True when no config file exists (first run).
    echo 14 > ~/.digitvrc # Create config file.
fi

CHANNEL=`cat ~/.digitvrc` # Set channel from config file (resume from last).

case "$1" in

    on) # ON/OFF
        if [ -n "`pgrep recpt1`" ]; then # True when recpt1 is running.
            kill "`pgrep recpt1`" "`pgrep vlc`" & # Just in case, kill both.
            notify-send --icon=video-display-symbolic --urgency=critical --expire-time=700 "TV: OFF" &
        else
            notify-send --icon=video-display-symbolic --urgency=critical --expire-time=700 "TV: ON" "CH: $CHANNEL" &
            recpt1 --b25 --strip $CHANNEL - - | vlc --fullscreen - & # Watch TV in vlc.
        fi
    ;;

    chanup|chandown) # CH+ & CH-

        if [ -n "`pgrep recpt1`" ]; then # True when recpt1 is running.

            case "$1" in

                chanup) # CH+

                    case "$CHANNEL" in # This part needs simplification. TODO: Channel names

                        14)
                            CHANNEL=15
                        ;;

                        15)
                            CHANNEL=22
                        ;;

                        22)
                            CHANNEL=32
                        ;;

                        32)
                            CHANNEL=34
                        ;;

                        34)
                            CHANNEL=14
                        ;;

                        *) # Catch bad input.
                            CHANNEL=14
                            notify-send --icon=error --urgency=critical --expire-time=1000 "TV: Invalid CH" "CH: $CHANNEL" &
                        ;;
                    esac

                    notify-send --icon=video-display-symbolic --urgency=critical --expire-time=700 "TV: CH+" "CH: $CHANNEL" &

                ;;

                chandown) # CH-

                    case "$CHANNEL" in # This part needs simplification. TODO: Channel names

                        34)
                            CHANNEL=32
                        ;;

                        32)
                            CHANNEL=22
                        ;;

                        22)
                            CHANNEL=15
                        ;;

                        15)
                            CHANNEL=14
                        ;;

                        14)
                            CHANNEL=34
                        ;;

                        *)
                            CHANNEL=14
                            notify-send --icon=error --urgency=critical --expire-time=1000 "TV: Invalid CH" "CH: $CHANNEL" &
                        ;;
                    esac

                    notify-send --icon=video-display-symbolic --urgency=critical --expire-time=700 "TV: CH-" "CH: $CHANNEL" &

                ;;
            esac

            echo $CHANNEL > ~/.digitvrc & # Save channel to config file.
            recpt1ctl --pid "`pgrep recpt1`" --channel $CHANNEL & # Change channel.
            sleep 2 # Wait to see if channel change crashed VLC.

            if [ -z "`ps \"\`pgrep vlc\`\" 2>/dev/null | grep Sl`" ]; then # True when vlc's STAT is not Sl or vlc is not running (crashed)
                kill "`pgrep recpt1`" "`pgrep vlc`" & # Just in case, kill both.
                notify-send --icon=video-display-symbolic --urgency=critical --expire-time=1000 "TV: Crashed, Resume" "CH: $CHANNEL" &
                sleep 2 # Wait for ??? (sometimes recpt1 cannot resume quickly).
                recpt1 --b25 --strip $CHANNEL - - | vlc --fullscreen - & # Watch TV in vlc.
            fi
        fi

    ;;

    *) # Catch bad input.
        notify-send --icon=error --urgency=critical --expire-time=1000 "TV: Invalid input" &
    ;;

esac

exit 0;
```Functionality has not changed. This script provides just three commands:
**digitv on** - an ON/OFF switch
**digitv chanup **- a CH+ button
**digitv chandown **- a CH- button

These can be run from the terminal, or configured to some hotkeys or actual remote control buttons if your computer supports one. I set them to Super+Play, Super+Up, and Super+Down respectively. 

**Big changes**:
-No more dbus interface as it proved insufficient and unnecessary for this purpose.
[B]
Fixed bugs[/B]:
-Automatically create config file on first run (since a channel must be specified to start watching) and subsequently recreate it if ever deleted.
-Changing channels when not watching TV does nothing (like a real tv; the previous script allowed the channel buttons to act as ON switches as well).
-Faster channel changing after crashes (certain channels may still crash vlc on change).
-Put in lots more comments to make everything make sense.

**TODO**:
-Portability: Make it easier to use another video player (currently only vlc and mplayer have full support) by adding this to the config file.
-Channels: Replace "case" lists with something more simple and more smooth, try to integrate channel scanning, and provide the names of channels.
-Translation: Into Japanese, because I can still count on one hand the number of native English speakers discussing these cards on the internet.

---

### Post by Artemis3 on 2012-12-05
Your work is remarkable!

I wonder if you could help me with another device, the cheap [usb stick S870](http://linuxtv.org/wiki/index.php/Geniatech/MyGica_SBTVD_Stick_S870) (Chinese brand), it is meant for ISDB-Tb, but I believe it should work with normal ISDB-T since the decoding is done by the player in software anyway.

I managed to make this device work with the early ubuntu 12.04 LTS kernels, by updating the v4l2 modules from their git server, but after some point with ubuntu kernel updates this stopped working altogether.

After that I tried with newer kernels, up to 3.5 unsuccessfully.

When it worked, I had to scan once to obtain the channels (using the [Brazillian ntsc type frequencies](http://www.linuxtv.org/wiki/index.php/ISDB-T_Frequency_Table)) this would produce a text file with a list of available channels which could then be opened with vlc just fine.

So if you could provide some help, it would be appreciated.

Also, consider adding your work with the Earthsoft to the [LinuxTVwiki](http://linuxtv.org/wiki/index.php/ISDB-T_Devices) so others can benefit; thanks!

---

### Post by quequotion on 2012-12-05
> **Artemis3 said:**
> Your work is remarkable!

I wonder if you could help me with another device, the cheap [usb stick S870]("http://linuxtv.org/wiki/index.php/Geniatech/MyGica_SBTVD_Stick_S870")  (Chinese brand), it is meant for ISDB-Tb, but I believe it should work  with normal ISDB-T since the decoding is done by the player in software  anyway.

I managed to make this device work with the early ubuntu 12.04 LTS  kernels, by updating the v4l2 modules from their git server, but after  some point with ubuntu kernel updates this stopped working altogether.

After that I tried with newer kernels, up to 3.5 unsuccessfully.

When it worked, I had to scan once to obtain the channels (using the [Brazillian ntsc type frequencies]("http://www.linuxtv.org/wiki/index.php/ISDB-T_Frequency_Table")) this would produce a text file with a list of available channels which could then be opened with vlc just fine.

So if you could provide some help, it would be appreciated.

Also, consider adding your work with the Earthsoft to the [LinuxTVwiki]("http://linuxtv.org/wiki/index.php/ISDB-T_Devices") so others can benefit; thanks!

Thanks  for the link! I'll have to try that method myself actually. This wasn't  documented when I started working on the earthsoft card. I'll see  about adding my guide there, and perhaps merging the two  methods.

Unfortunately I don't have one of those to test with, but I did take a look at the driver code in v4l-dvb ([dib0700]("http://git.linuxtv.org/media_tree.git/tree/HEAD:/drivers/media/dvb/dvb-usb")).  The last update on record for it was on September 21st 2011, and it  seems the v4l-dvb repository was last updated October 31st 2011 for  kernel 3.1.

12.04 ships with 3.2, but the v4l-dvb modules are probably outdated. The current kernel is 3.2.0.23.25, or  3.2.0.34.37 with updates or security updates; maybe something has  changed that breaks this driver?

Did you recompile and install from git after each kernel update?

---

### Post by annAnu on 2012-12-15
Great job quequotion! 
I have been looking for a "Japanese TV on Ubuntu how to guide", this is it. 

The thing is I am looking at getting the USB device rather than the PCI one. It is more for the set top box rather than for the PC. Any advise on which one would work with Ubuntu?

---

### Post by quequotion on 2012-12-16
> **annAnu said:**
> Great job quequotion! 
I have been looking for a "Japanese TV on Ubuntu how to guide", this is it. 

The thing is I am looking at getting the USB device rather than the PCI one. It is more for the set top box rather than for the PC. Any advise on which one would work with Ubuntu?

Thanks! Actually I figured most of this out myself by digging through Japanese blogs and how-to sites (which I can't actually read...) and added some experience with svn and scripting.

I don't know much about ISDB-T USB devices. When I bought my EarthSoft PT2, there were only three or four linux-compaitble ISDB-T devices on the market, all PCI. There are still very few, although there's been improvement: EarthSoft's PT3 is PCIe (x1 I think). It seems there are some new drivers in v4l-dvb and perhaps in the kernel for USB devices (Artemis3 mentioned one above). Unfortunately I don't have any of those devices to test.

One thing that puzzles me about new drivers in v4l-dvb or in the kernel is how they deal with encryption. All ISDB-T/S/C signals in Japan, except for One-seg, must be decrypted with a B-CAS smartcard. As far as I know there's no software implementation of this in the kernel and no video players available for linux that can do it either. The only decryption program I've come across is the airb25 library that was developed for Earthsoft PT-series cards (and ostensibly terminated).

Are you shopping for a new set-top box or do you have a dedicated machine running something like Mythbuntu as a set-top box?

---

### Post by Artemis3 on 2013-01-10
I read that this encryption is optional and none of the terrestrial channels uses it. ISDB-Tb (Latin America) actually removed encryption from the format altogether to ensure terrestrial signals are always free. For satellite, we are flooded with DVB-S2 signals instead, none of the ISDB-S sats reach.

I also read Japan would update their ISDB-T with the ISDB-Tb changes (mpeg4, better 1seg, ginga?) but i don't know if that also includes removing encryption.

---

### Post by BicyclerBoy on 2013-01-10
AFAIK Decryption can be handled by using virtual loopback device (kernel driver). Any 3rd party decrypt s/w is then independent of the PVR/DVR/media player & independent of v4l-dvb. see sasc-ng

I imagine you have more reward from the effort in making it work than watching live TV..

---

### Post by quequotion on 2013-02-01
> **Artemis3 said:**
> I read that this encryption is optional and none of the terrestrial channels uses it. ISDB-Tb (Latin America) actually removed encryption from the format altogether to ensure terrestrial signals are always free. For satellite, we are flooded with DVB-S2 signals instead, none of the ISDB-S sats reach.

I also read Japan would update their ISDB-T with the ISDB-Tb changes (mpeg4, better 1seg, ginga?) but i don't know if that also includes removing encryption.It's not optional in Japan; all of the terrestrial channels use encryption. There has been discussion of removing it, but it's unlikely to change in the near future. This is a somewhat politicized issue, as it also relates to Japan's pending membership in TPP. In order for Japan to participate in free trade, Galapagos market practices such as this have to come to an end, which amounts to a *huge* economic restructuring that no business or government leaders want.

Japan's broadcasters do not seem particularly interested in free broadcasting or broadcasting freedom. The monopoly responsible for the encryption algorithms and hardware licensing, B-CAS, is tied in to NHK and has *unofficial* government authority through that channel. To my knowledge, no broadcasters have made any public complaints about the regulations imposed by this private company and consumers are totally clueless (*very few people in Japan are aware of the existence of the B-CAS corporation and have absolutely no understanding of the concept of digital encryption*). Furthermore, Japan whole-heartedly ascribes to the principle of copy***right***, and publishers are delighted to have all of their content encrypted end-to-end (right up to the monitor through encrypted HDMI).

I actually bought an ISDB-T/S/C PVR (*to get a B-CAS card*) that can save recordings on an external usb stick. This came with three surprises: it's using [XFS]("http://en.wikipedia.org/wiki/XFS"); saves all recordings in encrypted files; and (analog) DVI output is limited to 720p.

On the other hand, Japan does have "Freedom of the Press" in most ways. News broadcasts frequently include scandals involving politicians and businessmen, government proceedings are publicly aired, over-the-air television occasionally features (mosaic) nudity, there don't seem to be any regulations on language, etc. etc.

---

### Post by benmoran on 2013-02-16
I just bought an Earthsoft PT3 tuner today, and am in the process of getting it working with my XBMC-based HTPC. The new XBMC has nice PVR support that works on Linux with TVHeadEnd, MythTV, or VDR. I haven't gottent his far yet, as I'm still trying to get one of them to work with the PT3. 

There is a recent (last year?) patch to the recpt1 program that adds --http daemon support, and a few recent guides out there on how to compile it for Ubuntu 12.04 (it works on 12.10 as well). For me, the http daemon support seems like a huge plus, because I've been able to get it working with a standard m3u VLC playlist like this: 
```

#EXTM3U
#EXTINF:0,1 - NHK1
http://localhost:8800/27
#EXTINF:0,2 - NHK2
http://localhost:8800/26
```
etc.....

So far in VLC it's working awesome! I just start the recpt1 http daemon, load up the m3u playlist in VLC, and I can change the channels on the fly. MythTV seems like it has m3u support for iptv, but it doesn't seem to work with the http streams. I may try using VLC to convert to a UDP multicast and see how that goes..

---

### Post by benmoran on 2013-02-18
I just wanted to add that I finally got it working nicely with XBMC! I found this addon:
[https://github.com/afedchin/xbmc-addon-iptvsimple](https://github.com/afedchin/xbmc-addon-iptvsimple)
Which did exacly what I needed. It lets you specify an "m3u" format playlist containing the http streams, and you can use a local or remote xmltv format EPG guide. 

So basically what I did:
1. Got my BCAS card set up in the manner **quequotion** described above.
2. Compiled the PT3 driver with the http patch. I found a few nice guides at this site:
[http://aqua-linux.blog.so-net.ne.jp/2012-07-27](http://aqua-linux.blog.so-net.ne.jp/2012-07-27)
3. Create an m3u style playlist, as shown in the example above, that matches my local channels in Tokyo. 
4. Launch the pt3 html daemon on startup, by adding this command to my /etc/rc.local file:
recpt1 --device /dev/pt3video2 --b25 --sid hd --http 8800
As a note, I found it necessary to specify the device manually, as pt3video0 and 1 were the satellite tuners. 2 and 3 are terrestrial broadcast. 
5. Compile and install the XBMC iptvsimple addon, as linked above, and point it to my m3u playlist. 


It works great for just watching live TV in XBMC, but it has some drawbacks. Firstly, there is no subtitle support or over the air EPG support, even though it's part of the .ts video stream. I'm not sure if it's possible to get these working over the http stream or not, but I'll look into it. EPG can be done by xmltv, so that's OK. 
Secondly, there is no record, time-shift, or other support. I don't believe the iptvsimple addon supports this functionality, so it's not a perfect setup yet. 

I'm no expert, but I'll help if anyone has any questions.

--------------------EDIT-----------------------
Looks like this github repository has everything you need for pt1/2/3 in one place, including the http patch for recpt1 pre-patched:
[https://github.com/stz2012](https://github.com/stz2012)

---

### Post by jopa222 on 2013-02-25
Thanks a lot to quequotion and benmoran for this write-up!

It's really hard to find information on getting ISDB-T working under Ubuntu!

I'll be going down to Japan next month to setup a Ubuntu-based PC as a PVR (with a PT3) so my wife can watch TV and I was searching a lot for how to get it working under Ubuntu. I already have DVB-T running for European broadcasts under Ubuntu and that was super-easy to setup. All the info here will surely help a lot! Thank you!

As for B-CAS card and PT1/2/3 you can call the B-CAS people and say "I bought a used TV, it didn't have a B-CAS card" and they will sell you one. Should be cheaper than buying a whole tuner just for the card.

---

### Post by quequotion on 2013-03-07
> **benmoran said:**
> I just wanted to add that I finally got it working nicely with XBMC! I found this addon:
[https://github.com/afedchin/xbmc-addon-iptvsimple](https://github.com/afedchin/xbmc-addon-iptvsimple)
Which did exacly what I needed. It lets you specify an "m3u" format playlist containing the http streams, and you can use a local or remote xmltv format EPG guide. 

So basically what I did:
1. Got my BCAS card set up in the manner **quequotion** described above.
2. Compiled the PT3 driver with the http patch. I found a few nice guides at this site:
[http://aqua-linux.blog.so-net.ne.jp/2012-07-27](http://aqua-linux.blog.so-net.ne.jp/2012-07-27)
3. Create an m3u style playlist, as shown in the example above, that matches my local channels in Tokyo. 
4. Launch the pt3 html daemon on startup, by adding this command to my /etc/rc.local file:
recpt1 --device /dev/pt3video2 --b25 --sid hd --http 8800
As a note, I found it necessary to specify the device manually, as pt3video0 and 1 were the satellite tuners. 2 and 3 are terrestrial broadcast. 
5. Compile and install the XBMC iptvsimple addon, as linked above, and point it to my m3u playlist. 


It works great for just watching live TV in XBMC, but it has some drawbacks. Firstly, there is no subtitle support or over the air EPG support, even though it's part of the .ts video stream. I'm not sure if it's possible to get these working over the http stream or not, but I'll look into it. EPG can be done by xmltv, so that's OK. 
Secondly, there is no record, time-shift, or other support. I don't believe the iptvsimple addon supports this functionality, so it's not a perfect setup yet. 

I'm no expert, but I'll help if anyone has any questions.

--------------------EDIT-----------------------
Looks like this github repository has everything you need for pt1/2/3 in one place, including the http patch for recpt1 pre-patched:
[https://github.com/stz2012](https://github.com/stz2012)
 
Awesome work!

There's [EPGrec]("http://www.mda.or.jp/epgrec/index.php") which I've seen mentioned in a few of the Japanese PT-series guides. I haven't really tried to get it working yet, but it looks like the concept is to have a remotely accessible and controllable PVR.

Also, it seems [VLC has built-in EPG support]("http://www.linuxtv.org/wiki/index.php/VLC_media_player#Electronic_Program_Guide_Information") but the Japanese information appears as mojibake.

Have you gotten subtitle support in anything else? I haven't had a chance to capture a broadcast with subtitles yet (that I know of). It's possible this feature isn't implemented in XMBC's backend (mplayer/libav/ffmpeg?).

---

### Post by quequotion on 2013-03-07
> **jopa222 said:**
> As for B-CAS card and PT1/2/3 you can call the B-CAS people and say "I bought a used TV, it didn't have a B-CAS card" and they will sell you one. Should be cheaper than buying a whole tuner just for the card. Do they ask any questions? I've heard B-CAS is holding their cards very tightly; only offering to replace damaged/destroyed/lost cards if customers could provide the serial number for their original card. I'm going to give this a shot and see if my japanese is up to the task.

---

### Post by benmoran on 2013-03-13
> **quequotion said:**
> Awesome work!

There's [EPGrec]("http://www.mda.or.jp/epgrec/index.php") which I've seen mentioned in a few of the Japanese PT-series guides. I haven't really tried to get it working yet, but it looks like the concept is to have a remotely accessible and controllable PVR.

Also, it seems [VLC has built-in EPG support]("http://www.linuxtv.org/wiki/index.php/VLC_media_player#Electronic_Program_Guide_Information") but the Japanese information appears as mojibake.

Have you gotten subtitle support in anything else? I haven't had a chance to capture a broadcast with subtitles yet (that I know of). It's possible this feature isn't implemented in XMBC's backend (mplayer/libav/ffmpeg?).

I confirm that the EPG data is also scrambled in VLC for me. Probably just not supported yet. I haven't really checked if there are any patches out there yet, since my main goal is to get it working in my XBMC htpc.  I did look into EPGrec, and actually tried to install it on my 12.10 box (had some error and didn't spend time troubleshooting yet). Esentially what it does for epg, is just to call the epgdump program periodically - most likely using the second tuner if using an earthsoft card. Epgdump just spits out xmltv files, which seems to be the standard. I guess it would be fairly easy to write up a script that runs periodically and does the same thing as EPGrec. 

I haven't had any luck with jimaku, but there is a jimakudump program out there for the earthsoft cards. It seems to work in much the same way as epgdump does, so its probably not usable for live tv. 

Have you had a chance to try out the http daemon patch yet? It really works great with VLC + m3u file or that IPTVSimple XBMC plugin, and I think it's probably the easiest solution for someone who just wants to watch live TV.  I think I couldn't get it to work with the MythTv backend yet though. It works with VDR, but only when using the VLC option to transcode the streams... It seems VDR is picky about the type of IPTV streams it will accept. Having VLC transcode the streams just uses way too much CPU though, so I gave up on VDR for now.  The IPTVsimple author said he plans to add some simple pause/time shift support in the future, so maybe it will eventually be a nice solution for a PVR under XBMC.

---

### Post by jopa222 on 2013-03-15
> **quequotion said:**
> Do they ask any questions? I've heard B-CAS is holding their cards very tightly; only offering to replace damaged/destroyed/lost cards if customers could provide the serial number for their original card. I'm going to give this a shot and see if my japanese is up to the task.

I haven't tried it myself, it's the information my wife found.

It's the top rated answer in this thread: [http://oshiete.goo.ne.jp/qa/7591277.html](http://oshiete.goo.ne.jp/qa/7591277.html) - according to this thread they will send you a card for 2000 yen if you say you bought an old TV etc without a card.
There's also a link there to the B-CAS site with instructions on what to do.

Edit: Nice to see more and more info being added here :) I'm setting up a box with PT3 in a couple of weeks, streaming live to another box running XMBC.

2nd edit: Any link to the jimakudump program? I'd like to take a look at it once I get my box set up later, maybe there's a way to get it working with live TV.

---

### Post by benmoran on 2013-03-15
Guys, just wanted to bring this to your attention in case you haven't seen it:
[http://chinachu.akkar.in/](http://chinachu.akkar.in/)
It's basically a modern alternative to epgrec. I just installed it, and its working well. Check out the github page if you're interested. The wiki has some nice install instructions. I actually think this is much easier to install than epgrec, since the entire thing is installed directly under a home directory (new or existing user), and it has it's own built-in web server. All you do is run the install script, and it will automatically download and compile all components.  It also has streaming support for recorded files. Only two /etc/init.d/ scripts need to be copied into the root of the system. 

My personal goal is to get PVR functionality working in my HTPC, but this + VLC seems like a nice solution for a desktop PC.

---

### Post by jopa222 on 2013-03-16
> **benmoran said:**
> Guys, just wanted to bring this to your attention in case you haven't seen it:
[http://chinachu.akkar.in/](http://chinachu.akkar.in/)


That looks pretty nice. Seems to be based on epgdump and Node.js so shouldn't be too hard to modify either if it's needed.

---

### Post by lleclerc on 2013-03-20
Re: Earthsoft PT2 card with EPGREC (a digital recorder with an EPG - Electronic Program guide).

**Requirements:**

I have gotten this to work completely (for terrestrial TV only, I don't have cable) in the last few weeks. It is running on Ubuntu 10.04.4 (Lucid Lynx, without updates. Note, I had problems getting this to work with later versions of Ubuntu Linux. 10.04.4 (with no 'updates')) is fine though. Then it works and works well. 

Some parts of EPGREC were a bit flakey (i.e. recording consecutive programs did not seem to work well) which I fixed with a sort of ugly hack to config.xml and some other changes here and there to the php scripts. 
[B]
Remote viewing Mods:[/B]

I also modified the epgrec scripts (do-record.sh and config.php) in particular to support watching Japanese TV from a computer in another city by automatically making compressed video files and sending them to another computer elsewhere on the internet for viewing. 

The user can go into the password protected webpages (done with .htaccess on apache), and select the programs they want to record as well as the sound / image quality they want to record at (saves space this way). The resulting file sizes are much much smaller than the native recorded DTV files (about 2 or 3% of original size), compressed with ffmpeg x264 at various resolutions and qualities (low, standard, high and ultra). The scripts automatically put the completed compressed files on another server with rsync once recording and compression is done. This lets you watch the TV programs from another city or where Japan DTV is not available, easily soon after they are recorded.

100meg / hour compressed at 96kbps AAC stereo audio (sounds great!) and 480x360 x264video gives an NTSC quality video stream, and 300meg / hr x264 at 640x480 x264 is much better and very nice for watching. I also tested 800x600 and 1280x960 ffmpeg x264 / AAC audio compressed streams, they are truly beautiful to insanely great, with sizes of around 450 and 600 meg per hour (I use CRF 28 for x264 compression, which is adequate for DTV and makes a compromise small file sizes with a nice picture).

 Though  there is a several hour delay only for the recording, compression and  file transfer, it means you can watch Japanese broadcasts on a PC or TV  anywhere on the internet, and even on your iphone (just set one of the  options for ffmpeg to make iphone streams, I tested that too, it works).

**Need to do:**

I haven't figured out how to get the compression and file transfer to start concurrently with the start of recording (+ a few seconds delay). It should be possible but my shell scripting and pipe skills are not that good), then conceivably, you should be able to start watching a TV program only a few minutes after it started broadcasting in Japan, even if you were in Canada or South America.

**It works!**

Linux, a PT2 card and epgrec is a very very cool combination, is stable  and with a minimum amount of mods, lets you watch Japanese TV with an easy to use program guide from anyplace in the world!

The PT2 card and recording computer do need to be in Japan of course, somewhere that Digital TV broadcasts can be received. As well, EPGREC only works in Japanese. (not a problem as I can read / speak Japanese, but if a non-Japanese speaker were setting this up for a friend, it may be a bit of an issue. It doesn't look like it would be hard to modify EPGrec to work in english, it is only a small set of pretty easy to understand php scripts and a mysql database using an open source php template engine called 'Smarty'). 

Good luck and happy watching!

---

### Post by IamHungry on 2013-03-30
If anyone is looking for more info, I have a couple of links (in Japanese):


[http://www43.atwiki.jp/mythtv-dvb/pages/2.html](http://www43.atwiki.jp/mythtv-dvb/pages/2.html)  --  Setup of Mythtv using fuse_b25 and native driver

[https://github.com/fukumen/mythtv/wiki](https://github.com/fukumen/mythtv/wiki)  --  Github of patches to Mythtv for Japanese TV

[http://blog.lwlv.net/](http://blog.lwlv.net/)  --  Blog about Japanese TV and Linux (mostly)

---

### Post by jopa222 on 2013-04-10
> **quequotion said:**
> Do they ask any questions? I've heard B-CAS is holding their cards very tightly; only offering to replace damaged/destroyed/lost cards if customers could provide the serial number for their original card. I'm going to give this a shot and see if my japanese is up to the task.

I'm quoting this again now that I've (actually my wife) has called the B-CAS people to get an extra card.
All they asked was the model of the "used tv" we bought, they use that to see which B-CAS card it can use.
The mailman delivered the card the next day and we paid him the 2000 yen.
No problems at all.

I finally had the chance to set up my own PC for recording/streaming Japanese TV.
Using the steps from quequotion and the repo posted by benmoran everything works like a charm, not a single problem so far :)
I'm only using chi deji since we don't have access to cable/satelitte.

I'm running Ubuntu 12.04 on a headless, core i5 pc with 8gb ram and a Earthsoft PT3.
Doing two recordings at same time is no problem on this (not so super) PC either.

Thanks to everyone for the help, once I get back from Japan I'm gonna start looking at making some changes to the EPG/streaming/etc software to get some easier usage.

---

### Post by quequotion on 2013-10-23
> **lleclerc said:**
> I have gotten this to work completely....which I fixed with a sort of ugly hack to config.xml and some other changes here and there to the php scripts.   Would you mind posting the details of how you installed EPGREC and the modifications you made in English?

---

### Post by quequotion on 2013-11-14
Rather than work on one of the more elaborate and feature-complete DVR apparatus available, I've continued to hack out a more advanced "basic remote control" script. The scripting is more advanced, the control is more basic.

What I'm going for is a trivial controller like this:```
[PWR] [REC]
[CH-] [CH+]
``` which can be set to any hotkeys / lirc remotes / etc.

For example I do:```
[Super]+[Play] = [PWR]
[Super]+[R]    = [REC]
[Super]+[Up]   = [CH+] (because my keyboard does not have ">>")
[Super]+[Down] = [CH-] (because my keyboard does not have "<<")
```

You can turn the TV on and off with a single [PWR] (also use to stop recording), start recording what you are watching immediately (breaks view: cards only support one stream per input; watching the presently recording file in VLC possible, but not yet implemented),  and the [CH+] and [CH-] buttons are much improved.
Changing channels still crashes video players on occasion (including vlc and mplayer, this is peculiar to Japan's ISDB-T encoding standards). The delay when crashing has been reduced by a new crashtesting "algorithm" (test once every second for ten seconds to verify that vlc and recpt1 still run).
The new feature, [REC], begins recording immediately to a timestamped file name, whether or not you are watching TV. In the case you are watching, the feed is cut: only one recpt1 stream is supported per input, so the stream going to the file is not displayed (unless any one knows some *script fu* to duplicate a binary std_out stream). The currently recording file is perfectly viewable in VLC while recording. Since HD recordings are very large, a default 2hr time limit (approx. 14.7GB) is set. More features are available by command line, including more DVR-like functionality.   Most of the functions still make use of notify-send for feedback. There are limitations in the design of notify-send beyond my control that make it difficult to use for certain purposes, particularly real-time OSD.

Note: These scripts now also include use of "schedtool" to specify the IDLE_PRO and ISO_SCHED schedulers available in the BFS patchset. These require a custom kernel with the BFS patchset and the code should probably be removed unless you have or plan to install a kernel with the BFS (aka by it's author: con-kolivas) patchset. I recommend installing it for a better desktop experience as well as real-time task managment.

[Remote Control]("http://pastebin.com/503gLrkU")
[Recorder Control]("http://pastebin.com/DGR8skvM") (dependency, a separate script for recordings)

The recorder control script defaults to make timestamped files in a specific capture directory so there's no need to concern oneself with how/where etc. when recording what's on the screen.

It can be used directly for more advanced record commands, such as:```
digitvrec 32 60 chThirtytwo-sixtySec
```***Rec**ord channel **thirty**-**two** for **sixty** seconds to the file ~\Videos\Uncompressed Capture\**chThirtytwo-sixtySec**.mp4*

I'm looking into wrapping this command with a scheduler of some kind to make a poor-programmer's DVR.

There are still a lot of features I want to work on later, like the http streaming and supporting multiple instances and cards.

---

### Post by quequotion on 2013-12-05
I had a brainstorm and improved this script by some orders of magnitude.

I added a new button & feature: REC+Play```
[PWR][REC]
[REC+PLAY]
[CH+][CH-]
```This is about as feature-complete as I plan for it to ever be. The script provides basic TV and VRC type controls to make a computer into a simple DVR.

Hit [REC] while watching tv: the screen blinks for a moment and comes back on; now watching a recording *while it is saved to the hard drive*. The recordings are saved to ~/Videos/Uncompressed Capture/CH#+YYYY-MM-DD+HH:MM:SS.mp4 (each recording gets unique, timestamped name). The files can get big, so the default recording time is capped at 2 hours.

It's also possible to specify the details of a recording on the command line, see the script header for a how-to.

New control script: [without BFS features]("http://pastebin.com/RBKGs390") or [with BFS features](http://pastebin.com/nvgUXd1N)
New DVR backend script: [With one small but important change]("http://pastebin.com/2ghn3By9")

I also took some time to look into a few more important issues:
[Crashing while changing channels may be taken care of in VLC 2.1.1]("https://trac.videolan.org/vlc/ticket/10038")
[Need to find nkoriyama and his patches for merging to fix bilingual audio]("https://trac.videolan.org/vlc/ticket/10041")
[Possible progress reading EPG in VLC; patches need to be tested and merged]("https://trac.videolan.org/vlc/ticket/10040")

So now when the NHK tax guy comes to my apartment and I say I don't have a television, because it's true, I can giggle inside because my PC is a television... and DVR....

---

