---
title: "usb sound passthrough"
date: 2008-09-18
forum: Multimedia Software
---

### Post by bonzini on 2008-09-18
Good people;

I asked about this over on laptops & hardware but received no answers, so I'm trying here.

I have two different external DAC devices that connect to the computer by USB.  One is a DAC-headphone amp, one is a DAC that has RCA audio out.  In both cases, I wonder if they are getting my 16 bit FLACs "bit-perfect" or if those files are being resampled / remixed.

I see a bit of discussion of this general topic on this list but it all seems to centre around getting "passthrough" behaviour out an SPDIF port, which is NOT my problem (no SPDIF ports in sight).

For the record, I'm using 8.04 and currently Rhythymbox though the latter can change.

Does anyone have any ideas on how to go about verifying and / or enabling "passthrough" behaviour in this context?

Thanks in advance!!!

---

### Post by bwiberg on 2009-02-27
I have been struggling a while now with this too. I have recently bought a Cambridge DacMagic connected via USB, which fortunately displays the sample rate fed to it.

Using Rhythmbox I have not been able to prevent resampling to 48000.

Using PulseAudio I have not been able to prevent resampling to 44100.

Only way I have been able to directly pass sound is using aplay, which is a command line player and not a very satisfactory solution. But it does allow the desired passthrough. When I play a CD quality track (sample rate 44100) followed by a track sampled at 48000 I can see the indicators on the DacMagic change indicating no conversion done on the computer.

I saw on another forum that you have done some further digging into PulseAudio. I would like to know if you made progress? Also should you need info on how to use aplay to play through USB, let me know...

---

### Post by markbuntu on 2009-02-27
You can disable resampling in pulseaudio by editing the /etc/pulse/daemon.conf file. You can play around with these lines

resample-method = speex-float-1
; disable-remixing = no


; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2

The ; marks a comment line.

---

### Post by bwiberg on 2009-03-01
Thanks markbuntu for taking time to reply:popcorn:

Yes - I have read the man pages at [http://linux.die.net/man/1/pulseaudio](http://linux.die.net/man/1/pulseaudio) and tried various settings in daemon.conf, but they do not seem to allow disabling of resampling.

resample-method allows many ways to do resampling, but disabling seems not to be one of them.

disable-remixing has to do with channel mixing and probably not relevant to my purpose? Inspired by your post I did try setting to both yes and no, but as expected no difference.

I can of course set default-sample-rate each time the source changes sample rate, but that certainly is not what I'm looking for.

But I have not given up yet on PulseAudio - so I would really want to know - have you found a solution that works for you or do you not have the need?

---

### Post by markbuntu on 2009-03-01
I don't have a need for that myself so have not played around with it but that is an interesting question. You might find a better answer at the pulseaudio irc channel or mailing list. The devs hang out there but you need to be patient with them as they are very busy.

---

### Post by zika on 2009-06-04
> **bwiberg said:**
> Thanks markbuntu for taking time to reply:popcorn:

Yes - I have read the man pages at [http://linux.die.net/man/1/pulseaudio](http://linux.die.net/man/1/pulseaudio) and tried various settings in daemon.conf, but they do not seem to allow disabling of resampling.

resample-method allows many ways to do resampling, but disabling seems not to be one of them.

disable-remixing has to do with channel mixing and probably not relevant to my purpose? Inspired by your post I did try setting to both yes and no, but as expected no difference.

I can of course set default-sample-rate each time the source changes sample rate, but that certainly is not what I'm looking for.

But I have not given up yet on PulseAudio - so I would really want to know - have you found a solution that works for you or do you not have the need?
resample-method = copy ... ?

---

### Post by erniejunior on 2011-02-15
Bump

I have the exact same question even if this thread is very old now. Unfortunately my DAC does not show the sample rate so I don't even know if I get bit-perfect pass through. So
a) is there a way to see what sample rate is used and
b) is there a way to get bit-perfect sound?

greetings,


erniejunior

---

### Post by ronalde@launchpad.net on 2011-04-10
> **erniejunior said:**
> a) is there a way to see what sample rate is used

On the host connected to the USB DAC enter the following in a terminal (and leave that terminal open):

[FONT=Courier New]watch -n 1 "cat /proc/asound/card1/stream0"[/FONT]

The output contains at least two sections: a 'Status' section which shows the current 'mode' and at least one 'Interface' section which describes the modes supported by your USB device.

Mine looks like this when playing a simple 16bit/44.1KHz CD-ripped FLAC:

[FONT=Courier New]Playback:
  Status: Running
    Interface = 3
    Altset = 1
    URBs = 3 [ 8 8 8 ]
    Packet Size = 388
    Momentary freq = 44100 Hz (0x2c.199a)
  Interface 3
    Altset 1
    Format: S16_LE
    Channels: 2
    Endpoint: 3 OUT (ADAPTIVE)
    Rates: 44100, 48000, 96000
  Interface 3
    Altset 2
    Format: S24_3LE
    Channels: 2
    Endpoint: 3 OUT (ADAPTIVE)
    Rates: 44100, 48000, 96000
[/FONT]

Of course card1 and stream0 are system specific. To find which file you have to look at, you might use the following command:

[FONT=Courier New]grep -R S24_3LE /proc/asound/[/FONT]

This searches for any file in the proc filesystem which has a line with this string in it; for example in my case:

[FONT=Courier New]/proc/asound/Module/stream0:    Format: S24_3LE
/proc/asound/card1/stream0:    Format: S24_3LE[/FONT]

[FONT=Courier New]S24_3LE[/FONT] means 24 bits packed in 3 bytes as explained in [this excellent page on the MultimediaWiki]("http://wiki.multimedia.cx/index.php?title=PCM#24-Bit_PCM"). 

> **erniejunior said:**
> b) is there a way to get bit-perfect sound?

Yes, but currently not with pulseaudio, as explained by the maintainers in [ticket #930 on the pulseaudio website]("http://www.pulseaudio.org/ticket/930#comment:2").

Any alsa client can do it however, when it (the client) uses [FONT=Courier New]hw:0,0[/FONT] instead of the default resampling [FONT=Courier New]hwplug:0,0[/FONT] interface. 

The easiest way is to do the following on the host to which the USB DAC is connected:

1. disable pulseaudio by making sure the parameter `autospawn` is set to `no` in `/etc/pulse/client.conf` (and of course delete the comment sign `;` in front of it:

[FONT=Courier New]autospawn = no[/FONT]


2. install music player daemon (mpd):

[FONT=Courier New]apt-get install mpd[/FONT]

3. configure mpd by making a section like this:

[FONT=Courier New]audio_output {
    type        "alsa"
    name        "Pink Faun 3.24 USB-DAC"
    device        "hw:1,0"    # optional
}
[/FONT]
Of course you'll have to point to right directoriesd on your system for the audio library etc.

4. restart mpd

[FONT=Courier New]/etc/init.d/mpd restart[/FONT]

5. install a mpd client on this host or any other in your network

[FONT=Courier New]apt-get install gmpc gmpc-plugins[/FONT]

See [http://www.computeraudiophile.com/content/Bit-perfect-audio-Linux-882-and-1764-now-possible](http://www.computeraudiophile.com/content/Bit-perfect-audio-Linux-882-and-1764-now-possible).


UPDATE (2 may 2011): The Tenor chip in my DAC (providing USB audio) does not support 88.200 and 176.400 sample rates. My solution for those tracks (like the ones for which HDtracks.com do not offer 96.000 versions themselves, like North by Elvis Costello @ 88.200 KHz and Wagner by Netherlands Phylharmonics Orchestra @ 176.400KHz) is to upsample material at 88.200 and downsample files at >96.000 using the following offline script.

[FONT=Courier New]
#!/bin/bash

# script to upsample 24 bit flac files to 96.000KHz using the 
# Shibatch SRC in twopass non-fast mode while preserving the 
# flac metadata stored in the original files.
# 
#  88.200 KHz (DVD-audio) files are upsampled
# 176.400 KHz files are downsampled
#
# author: ronalde
# may 2011

# Shibatch sampling rate converter version 1.30
SSRC=~/ssrc-1.30/ssrc

# temporary directory (below current) for storing intermediate files
# will be cleaned afterwards
TMPTARGET=$(mktemp -d "original.XXXXXXXXXX")

SAVEIFS=$IFS
IFS=$(echo -en "\n\b")

# process each flac in current directory
for f in *.flac
do
    SRC="$f"
    # extract basename (ie filename without extension)
    BASENAME=$(echo "${SRC}" | cut -d \. -f 1 -)
    WAVTARGET="${BASENAME}.wav"
    mv "${SRC}" ${TMPTARGET}/
    # decode original flac file to wav file 
    flac -s -d "${TMPTARGET}/${SRC}"
    # upsample original wav to 96.000 KHz using best profile
    ${SSRC} --rate 96000 --twopass --profile standard "${TMPTARGET}/${WAVTARGET}" "${TMPTARGET}/Upsampled ${WAVTARGET}"
    # encode upsampled wav file to flac
    flac -s "${TMPTARGET}/Upsampled ${WAVTARGET}" -o "${SRC}"
    # remove original and upsampled wavtargets
    rm "${TMPTARGET}/Upsampled ${WAVTARGET}" "${TMPTARGET}/${WAVTARGET}"
    # store flac tags from original flac file in upsampled flac file
    metaflac --export-tags-to - "${TMPTARGET}/${SRC}" | metaflac --import-tags-from - "${SRC}"
done

tar cf original-flacs.tar "${TMPTARGET}"
echo Done\! 
echo ... original flac files copied to tarball "original-882000-flac.tar"
echo ... upsampled flac files with metadata available in this directory
rm -rf "${TMPTARGET}"

IFS=$SAVEIFS

[/FONT]

Good luck

---

### Post by undecidable on 2012-03-13
Your post helped me with my own usb DAC issues.
Here is an alternate solution if you don't want to install mpd
(or disable pulseaudio)

[http://ubuntuforums.org/showthread.php?t=1939711]("[URL="http://ubuntuforums.org/showthread.php?t=1939711")

---

### Post by zika on 2012-03-13
> **undecidable said:**
> Your post helped me with my own usb DAC issues.
Here is an alternate solution if you don't want to install mpd
(or disable pulseaudio)

[http://ubuntuforums.org/showthread.php?t=1939711]("http://[URL=%22http://ubuntuforums.org/showthread.php?t=1939711")
As far as I know, pulseaudio has got direct out as of new major version change...

---

### Post by undecidable on 2012-03-13
Nice news.  
Any idea if this will be in 12.04?

As I still (barely) pass my sanity test,
I will not be un/re-installing pulse or alsa by hand.

---

