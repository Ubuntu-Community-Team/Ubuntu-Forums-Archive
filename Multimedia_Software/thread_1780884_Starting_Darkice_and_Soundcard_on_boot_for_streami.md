---
title: "Starting Darkice and Soundcard on boot for streaming audio"
date: 2011-06-12
forum: Multimedia Software
---

### Post by agitkid on 2011-06-12
I had a difficult time getting darkice to start on boot, but managed to figure it out using a few scripts and a cron. What I discovered was that even if I got darkice to start using your standard boot parameters and run levels, the soundcard would not get initialized unless a user logged in via the GUI. As a result, the stream would be just white noise. The trick is to get the soundcard enabled before starting darkice, all automated right after boot. This solution will apply to a server install as well.

This server is used for an online radio station. It encodes the analog signal and streams it to an icecast server, which then distributes it to listeners. It needs to be able to auto-start the stream on boot, in case of a power outage. 

I am not covering the sound card installation here.

OS: Ubuntu 10.04 Desktop

## PACKAGES INSTALLED:

alsa-base 1.0.24+dfsg-0ubuntu1
alsa-oss 1.0.17-4
alsa-utils 1.0.24.2-0ubuntu6
oss-preserve 1.1-6
oss4-base 4.2-build2003-1ubuntu1
darkice 0.20.1-3ubuntu2


## USEFUL COMMANDS for seeing your soundcard details:

aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
lspci -vvnn


## ALSAMIXER setup:

Setup the alsamixer by running: /usr/bin/alsamixer
Hit 'F4' to only adjust the capture volume and set to about 50% for all 3 settings using up/down arrow keys. This will ensure you don't blast the volume too high on the output. 


Ok, Let's setup this simple script and cron

1. Add a line to /etc/rc.local that will flag a PID file. (NOTE: I am putting everything in /usr/local/bin, just because I want everything in the same directory. This PID file could go into /var/run/ . And yes, I know this is not really a PID, but that is what I am calling it ;) )

Let's create the PID file first:

```

touch /usr/local/bin/darkice_boot_pid

```

Use your favorite editor to edit /etc/rc.local and add:

```

echo 0 > /usr/local/bin/darkice_boot_pid

```

2. Add the script that will startup darkice and the soundcard on boot, depending on the contents of the PID file. If it is '0', then we will start darkice/soundcard, and if it is set to '1', we will exit.

Create the file with your favorite editor:

```

vi /usr/local/bin/darkice_start_on_boot.sh

```

and add the following:

```

#!/bin/sh

## The following entries are not used, but good practice
CURRENT_DATE=`date +%Y%m%d`
DATE=`date`
HOSTNAME=`hostname`

## The guts

X=`cat /usr/local/bin/darkice_boot_pid`

# Checking startup status for darkice

if [ $X = 0 ]; then
    echo "SUCCESS: We can now start darkice after boot"
    echo 1 > /usr/local/bin/darkice_boot_pid
    /usr/local/bin/alsa_force-reload.sh
    /usr/bin/darkice -v 10 -c /etc/darkice.cfg 
else
    echo "ERROR: PID does not equal 0, so we can't start"
    exit 1
fi

```


make sure this file is executable:

```

chmod a+x /usr/local/bin/darkice_start_on_boot.sh

```

3. Let's create the executable that will force reload the soundcard, which is listed directly above.

User your favorite editor to create /usr/local/bin/alsa_force-reload.sh:

```

vi /usr/local/bin/alsa_force-reload.sh

```

Add the following to this file:

```

#!/bin/sh
/sbin/alsa force-reload

```

make sure this file is executable:

```

chmod a+x /usr/local/bin/alsa_force-reload.sh

```

4. Now, lets add a crontab entry that will run this script every 2 minutes, but will only execute on boot based on the PID file setting. I put this in root's crontab.

run: crontab -e

And add the following line:

```

## Run this every 2 minutes, which will check PID in /usr/local/bin, and only start darkice if it's set to "0"
*/2 * * * * /usr/local/bin/darkice_start_on_boot.sh

```


That's it! Assuming that your darkice config file and soundcard has been tested, then this should work.

For those interested, I have included a copy of my /etc/darkice.cfg file below:

```


# this section describes general aspects of the live streaming session
[general]
duration        = 0        # duration of encoding, in seconds. 0 means forever
bufferSecs      = 10         # size of internal slip buffer, in seconds
reconnect       = yes       # reconnect to the server(s) if disconnected

# this section describes the audio input that will be streamed
[input]
#device          = /dev/dsp  # OSS DSP soundcard device for the audio input
device		= hw:0,0
#device		= default
sampleRate      = 44100     # sample rate in Hz. try 11025, 22050 or 44100
bitsPerSample   = 16        # bits per sample. try 16
channel         = 2         # channels. 1 = mono, 2 = stereo

[icecast2-0]
bitrateMode     = cbr       # constant bit rate
format		= mp3
bitrate         = 128        # bitrate of the mp3 stream sent to the server
quality         = 0.8       # encoding quality
server          = your.streamingserver.org
#bitrate		= 16
#channel		= 2
#sampleRate	= 44100
                            # host name of the server
port            = 8000      # port of the IceCast server, usually 8000
password        = yourpassword    # source password to the IceCast server
mountPoint      = yourstationname  # mount point of this stream on the IceCast server
name            = Free Radio Against Empire
                            # name of the stream
description     = Independent Radio
                            # description of the stream
url             = http://your.freeradio.org
                            # URL related to the stream
genre           = Anti-Fascist    # genre of the stream
public          = yes       # advertise this stream?


```

---

