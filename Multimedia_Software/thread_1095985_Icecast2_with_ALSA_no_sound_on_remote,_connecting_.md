---
title: "Icecast2 with ALSA no sound on remote, connecting works"
date: 2009-03-14
forum: Multimedia Software
---

### Post by hachel on 2009-03-14
hello
I'm trying to stream everything sound I hear localy to the internet so that certain selected people can hear it (for various reasons).

I read about Icecast that it could stream anything that is output through Alsa or Oss. As far as I understand that means that if I play an mp3-file on my pc with whatever program it will be made possible to hear for those connected to my icecast-server.

Well, I downloaded icecast2 and ices2 via the reps and configured icecast2 and after starting it was able to access the web-interface.
And since I'm able to do that and people can connect to my server I figured that icecast2 is configured correctly and any sound-issues are with ices2, right?

This is my ices2-configfile, a sporadicly altered version of the alsa-example:
```
<?xml version="1.0"?>
<ices>

    <!-- run in background  -->
    <background>0</background>
    <!-- where logs go. -->
    <logpath>/var/log/ices</logpath>
    <logfile>ices.log</logfile>
    <!-- size in kilobytes -->
    <logsize>2048</logsize>
    <!-- 1=error, 2=warn, 3=infoa ,4=debug -->
    <loglevel>4</loglevel>
    <!-- logfile is ignored if this is set to 1 -->
    <consolelog>0</consolelog>

    <!-- optional filename to write process id to -->
    <!-- <pidfile>/home/ices/ices.pid</pidfile> -->

    <stream>
        <!-- metadata used for stream listing -->
        <metadata>
            <name>name</name>
            <genre>genre</genre>
            <description>description</description>
            <url>http://google.de</url>
        </metadata>

        <!--    Input module.

            This example uses the 'oss' module. It takes input from the
            OSS audio device (e.g. line-in), and processes it for live
            encoding.  -->
        <input>
            <module>alsa</module>
            <param name="rate">44100</param>
            <param name="channels">2</param>
            <param name="device">hw:0,0</param>
            <!-- Read metadata (from stdin by default, or -->
            <!-- filename defined below (if the latter, only on SIGUSR1) -->
            <param name="metadata">1</param>
            <param name="metadatafilename">test</param>
        </input>

        <!--    Stream instance.

            You may have one or more instances here.  This allows you to
            send the same input data to one or more servers (or to different
            mountpoints on the same server). Each of them can have different
            parameters. This is primarily useful for a) relaying to multiple
            independent servers, and b) encoding/reencoding to multiple
            bitrates.

            If one instance fails (for example, the associated server goes
            down, etc), the others will continue to function correctly.
            This example defines a single instance doing live encoding at
            low bitrate.  -->

        <instance>
            <!--    Server details.

                You define hostname and port for the server here, along
                with the source password and mountpoint.  -->

            <hostname>localhost</hostname>
            <port>8000</port>
            <password>****</password>
            <mount>/listen.ogg</mount>
            <yp>0</yp>   <!-- allow stream to be advertised on YP, default 0 -->

            <!--    Live encoding/reencoding:

                channels and samplerate currently MUST match the channels
                and samplerate given in the parameters to the oss input
                module above or the remsaple/downmix section below.  -->

            <encode>  
                <quality>2</quality>
                <samplerate>22050</samplerate>
                <channels>1</channels>
            </encode>

            <!-- stereo->mono downmixing, enabled by setting this to 1 -->
            <downmix>1</downmix>

            <!-- resampling.
            
                Set to the frequency (in Hz) you wish to resample to, -->
             
            <resample>
                <in-rate>44100</in-rate>
                <out-rate>22050</out-rate>
            </resample>
        </instance>

    </stream>
</ices>

```
I started ices with
```
$ices 2 /pathtoconfigfile
```
from the terminal and it gave me no message but stayed open (the prompt didn't come back), and after I refreshed the webinterface the mount-point got listed 

Any idea what might be wrong?

thanks

hachel

PS: i set all my sound-ouput to alsa (system->pref->sound) and tested before and after.

---

### Post by Darkade on 2009-03-14
I have configured a icecast server successfully, I'll go trough your config file and try to find an error. In the mean time check this thread

[http://ubuntuforums.org/showthread.php?t=862815](http://ubuntuforums.org/showthread.php?t=862815)

hope it helps

and please post the result of this command

```
cat /proc/asound/devices
```

ohhh and I guess you had a typo when you wrote the command in the forums
```
$ices 2 /pathtoconfigfile
```
if that's what you wrote in your terminal... that might be the error :lolflag:

---

### Post by hachel on 2009-03-14
hi,
i went through your post and after checking cat /proc/asound/devices it seems I have a similar problem described there, with both capture and playback on the same device:
```
:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 2]: digital audio capture
  5: [ 0- 1]: digital audio playback
  6: [ 0- 1]: digital audio capture
  7: [ 0- 0]: digital audio playback
  8: [ 0- 0]: digital audio capture
  9: [ 0]   : control

```

---

### Post by hachel on 2009-03-14
ok it has someting to do with the mixers at volume control.
I found out that on the remote there is indeed output, but very very quiet and with a noise.

I set everything to max at volume control, and apparently it has something to with the microphone.
When all microphone-related mixers are up to maximum i can here myself type on the remote. And it looks like with mic-boost my microphone records the minimalistic sound that comes through my headphones and ups the volume by a billion so that I can actually here the song I listen to on my headphones on the remote.

At the options-tab Input source is set to Mic, changing it to something else mutes the output on the remote.

Any new ideads?
Obviously the input source is wrong, but thats the only one that works...

thanks

hachel

---

### Post by Darkade on 2009-03-14
Ok, i got why you don't get your console back. Just look for the run in back ground value (at the very beggining of the file) and change it to 1

---

### Post by produnis on 2010-02-07
> **hachel said:**
> 

Any new ideads?
Obviously the input source is wrong, but thats the only one that works...


I faced the same probleme here..

How I solved it:

At the rear of my PC, I put a cable (which came with my monitor) from "Line Out" to "Mic".

So, the output signal is directly sent to my microphone-line...

Now it works...

ugly hack, but it works!

---

