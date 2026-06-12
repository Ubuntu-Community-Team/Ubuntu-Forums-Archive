---
title: "No Sound!!! Please help!"
date: 2009-02-17
forum: Mythbuntu
---

### Post by t_hutch on 2009-02-17
I've been beating my head against a wall for days now with no luck getting my audio to passthrough to my SPDIF (digital coax). I've got mythbuntu 8.10 running. I can't get any player to output sound. I know the sound works because it still works on my MCE partition.

I have a foxconn 6150 board that comes with realtek alc850 sound. I've tried all the basic "how-to's" I could find with no success at all. I've unmuted the IEC958 channel in alsamixer (however it doesn't allow the volume to be turned up, which I believe is normal).

If anyone can help me out of this mess, it would be greatly appreciated....

---

### Post by fatmonk on 2009-02-18
I had a lot of trouble with this at the start, but since then can't figure out why I did! I've rebuilt a number of times since the first couple of builds, and at different version (8.04 and 8.10) and never had problems.

At risk of listing again all the stuff you've already tried, these are the thing sthat I found to be important - or at least are the only thing I have had to do after recent rebuilds to get SPDIF sound working.

- Enable the digital audio out in alsamixer (IEC958 as you mentioned, but it might have digital or something after it as well - I seem to think I have a few IECxxx entries on my system) - make sure its the out/playback one you are un-muting!
- Make sure that your master audio output is not muted. I've had a few strange occasions where the master audio out fader drops to zero for no apparent reason (maybe one of the pulse audio bugs? I haven't really looked into this).
- Then in the MythTV front end general setu pages, set your audio device to "SPDIF: default" (I think that's right - its certainly very close to that).
- Select to pass through AC3 etc, and all should be good.

As I say, you've probably tried all of these, but just in case it helps I thought I'd list all that I had to do to get mine up and running.

-FM

---

### Post by larsolav on 2009-02-18
I had a horrible time getting my Realtek ALC880 chip to play digital sound. {My problem discussed [[COLOR="SeaGreen"]here[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=857898")and [[COLOR="SeaGreen"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1051588")}
I now have MythTV Digital sound mostly working. I think I followed the tips in [[COLOR="SeaGreen"]this link[/COLOR]]("http://www.mythtv.org/wiki/Intel_HD_Audio_-_Realtek_ALC88x") to get me going. I maybe did some more stuff, but I will have to check my Mythbox tonight after the kids are in bed....
Good luck!

---

### Post by itlarson on 2009-02-18
I have heard you must select "stereo" for surround over spdif work, which is a bug.

---

### Post by allene222 on 2009-02-18
I put a wiki together for digital sound in myth.  It seems to be helping people.  
[http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto](http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto)

Allen

---

### Post by t_hutch on 2009-02-18
Thank you for all the great replies. However, I still have no luck. I've tried all (and I mean all) the combinations of mythtv sound settings. Not one of them made a difference. I can't even get mplayer or xine or vlc to give sound on their own.

In my alsamixer, I have 3 IEC958 items. The first is just labeled IEC958. It was the one I unmuted, but it doesn't allow me to adjust any volume. The second is IEC958 Playback AC97-SPSA. It allows me adjust volume only. The third is IEC958 Playback Source. It allows me to change between IEC958 In, Analog In, and PCM. I have that set on PCM, as I've read it should.

I'm at a total loss. Should I rebuild this damn thing? Maybe in my rambling attempts to correct the problem, I've actually made it worst. Any other suggestions or things to look at?

Thanks,
Tim

---

### Post by allene222 on 2009-02-18
Did you follow the instructions in my wiki?  You should not be able to adjust the volume with digital sound.  Did I forget to day that in the wiki?  I think I said to turn off adjust sound in myth.

Allen

---

### Post by t_hutch on 2009-02-19
Allen,

When I saw your post originally, I thought you were referring to the to a different wiki on the subject of digital audio passthrough which I already attempted to follow. However, now I see that this is different. I will go through the finer details tonight and see if it makes a difference and I'll report back.

Thanks!
Tim

---

### Post by t_hutch on 2009-02-19
Allen,

Still no success. I had trouble updating ALSA. It seems that the FTP site is currently down (as noted in the log file from the script). However, I'm already at version 1.0.17, so I went ahead and tried your method. No luck. I tried some of your troubleshooting methods with no luck.

I'm about to give up all together....any other suggestions before I give up on Mythbuntu?

Thanks,
Tim

---

### Post by allene222 on 2009-02-19
You said you have 3 IEC958 entries in alsamixer.  From my experience, that must mean you have a HDMI motherboard.  If that is the case, you need to update alsa to 1.0.18 before you give up.  Also, if you have an HDMI MB, you may have to tell the BIOS which output you want to use, in your case it sounds like you want to use the spdif output.  Assuming I am right about this, please make sure you try this for asound.conf:

pcm.!default {
     type plug
     slave.pcm "spdif"
  }

Also, make sure that you have myth audio set up exactly like the wiki:
Audio output device: ALSA:default
Passthrough output device: ALSA:default
Max Audio Channels: Stereo (MUST BE SET IN STEREO as of 2/10/2009 as there is a bug in surround)
Upmix: Passive
Enable AC3 to SPDIF passthrough checked
Enable DTS to SPDIF passthrough checked
Aggressive sound card buffering off
Use internal volume controls off

Those are the highlights.  If you give me more information on your board and setup I might be able to help more.

Allen

---

### Post by fatmonk on 2009-02-20
Just thought of another thing to check...

Does your motherboard have a digital audio out header on it? Is it connected to anything?

I had mine connected to my video card for a while. During that time I had problems getting the S/PDIF out working.

I removed the digital audio connection from teh motherboard to the video card and nevere placed it. Now I don't have any problems with the S/PDIF out on the mtherboard.

Maybe the motherboard detects that there is something connetced to the digital audio header and directs the audio that way and not to the on board S/PDIF out.

Just an idea that might be worth checking (my BIOS settings didn't allow me to select where to output the digital audio).

-FM

---

### Post by t_hutch on 2009-02-20
Hi Guys,

Thanks for your patience with me. I'll keep trying as long as people have suggestions.

I do not have hdmi. I'm using a Foxconn 6150K8MA-8EKRS motherboard. I'm using both the on-board video and audio. I'm using the coax digital out to my receiver. I'll double check the bios settings to be sure no settings are tripping this up, however, this board works just fine in this configuration under WMC (I have a separate partition with WMCE-2005). Before anyone suggests going back to WMC, my reasoning for myth is I love the front end/back end setup. WMC wouldn't let me see videos stored on a shared drive and that drove me nuts!

Allen, I've tried the first two lines for the asound.conf file, but not the one you just suggested. I'll try that tonight as well as try again to update ALSA.

Thanks,
Tim

P.S. Can someone else confirm that the ALSA ftp site is down? Or am I just doing something wrong? I've tried from two locations now.

---

### Post by allene222 on 2009-02-20
What confuses me is why you have 3 iec options in alsamixer.  Could you post the output of your asound -l and also the names on of the 3 iec options on alsamixer?

---

### Post by t_hutch on 2009-02-20
The first is just labeled IEC958. It was the one I unmuted, but it doesn't allow me to adjust any volume. The second is IEC958 Playback AC97-SPSA. It allows me adjust volume only. The third is IEC958 Playback Source. It allows me to change between IEC958 In, Analog In, and PCM. I have that set on PCM, as I've read it should.

That information is from a previous post of mine, but I'm not at home and don't have a VNC connection to my box yet. I'll run asound -l (is that correct or did you mean aplay -l) as soon as I get home and post the output.

---

### Post by allene222 on 2009-02-20
Sorry, yes aplay -l.
I see that the third is a spdif input. You should not be able to adjust the volume when you get this set up correctly. I believe the second one needs to be set to 0.  
Here is some advice from: [http://alsa.opensrc.org/index.php/Realtek_ALC650](http://alsa.opensrc.org/index.php/Realtek_ALC650)

Putting this in your /etc/rc.d/rc.local should fix this:
 amixer set 'IEC958 Playback AC97-SPSA' 0

I would bet this will fix the problem.  I will add this to my wiki.  Hopefully you can confirm success tonight.

Allen

---

### Post by 7bigjohn on 2009-02-20
Are you trying to output sound to a receiver?  If so, the volume control won't work through myth.  You have to set your remote to control the receiver volume.

---

### Post by macogw on 2009-02-20
It could also be a driver bug...

---

### Post by t_hutch on 2009-02-20
Hi everyone,

Still no luck. I've updated my asound.conf file as suggested. I've fixed all my myth settings just as Allen suggested.

Here is the output of aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Here is my asound.conf file:

```
pcm.!default {
type hw
card 0
device 2
}

pcm.!default {
type plug
slave {
pcm "hw:0,2"
format S32_LE
}
}

pcm.!default {
type plug
slave.pcm "spdif"
}
```

I also updated my rc.local file as Allen suggested. The result is driving the volume of the second IEC958 in alsamixer to zero.

Does anyone else have any suggestions? Also, is the alsa ftp site down? I'm still at 1.0.17, not that I think upgrading will help.

Thanks,
Tim

---

### Post by t_hutch on 2009-02-20
One last update...I managed to get the update script to run using a ALSA mirror site. It went through the update, the log indicated success, and I rebooted. However, I when I check the version (cat /proc/asound/version) I still get 1.0.17. Don't know what that is all about...

Tim

---

### Post by allene222 on 2009-02-20
I would think any of your default settings would work but I just want to make sure you only have one of them in there.  If the file really is what you said, I have no idea what would happen.

Try them one at a time.  I don't think updating alsa is important for your board as you do not have hdmi.

Allen

---

### Post by t_hutch on 2009-02-21
I think I may be on the point of a rebuild here. I'm not too deep into setting this thing up, so I won't loose too much. I likely screwed something up while I attempted to fix this sound issue.

If that still doesn't work, I may consider a new mb. Any good suggestions for a sure fire sound chipset? Obviously realtek 850 is not a good choice. Any other suggestions?

Tim

---

### Post by allene222 on 2009-02-21
Before you do that, please confirm that you tried a asound.conf file with nothing more than the following in it:

pcm.!default {
type plug
slave.pcm "spdif"
}

and that .asoundrc did not exist.

And that this was with the second iec slider at 0 and the first one enabled of course.

And that you had myth configured like this:

Audio output device: ALSA:default
Passthrough output device: ALSA:default
Max Audio Channels: Stereo (MUST BE SET IN STEREO as of 2/10/2009 as there is a bug in surround)
Upmix: Passive
Enable AC3 to SPDIF passthrough checked
Enable DTS to SPDIF passthrough checked
Aggressive sound card buffering off
Use internal volume controls off

I would really like to know for sure that you tried this setup and it either did or did not work.

Allen

---

### Post by t_hutch on 2009-02-22
I doubled checked everything you suggested, and updated asound.conf to include that one line with no luck.

Are there any logs generated that could give us a clue to what is going on?

Tim

---

### Post by allene222 on 2009-02-22
/var/log/mythtv/mythfrontend.log

That should be full of myth dealing with sound.  I will post a typical session for your reference below.  Also posted my asound.conf file.

If you are thinking of reinstalling consider this.  Of the 4 mythbuntu systems I have set up, I don't think I have one one in less than 3 re-installs.  If I ever hit the wrong button or enter the wrong thing, I start over.  Recovering is impossible.  So, that might be the next step as you suggested a few posts ago.

Allen

-------------/etc/asound.conf-----------------
pcm.!default {
        type plug
        slave {
                pcm "hw:0,1"
                format S32_LE
        }
}




----------/var/log/mythtv/mythfrontend.log------------------

2009-02-03 09:03:49.650 TV: Attempting to change from None to WatchingPreRecorded
2009-02-03 09:03:49.751 DPMS Deactivated
2009-02-03 09:03:49.923 AFD: Opened codec 0x848e7f0, id(MPEG2VIDEO) type(Video)
2009-02-03 09:03:49.923 AFD: codec AC3 has 6 channels
2009-02-03 09:03:49.924 AFD: Opened codec 0x83554d0, id(AC3) type(Audio)
2009-02-03 09:03:49.924 AFD: codec AC3 has 1 channels
2009-02-03 09:03:49.924 AFD: Opened codec 0x8492430, id(AC3) type(Audio)
2009-02-03 09:03:49.924 AFD: codec AC3 has 6 channels
2009-02-03 09:03:49.925 AFD: Opened codec 0x8354ed0, id(AC3) type(Audio)
2009-02-03 09:03:49.927 Opening audio device 'spdif'. ch 2(2) sr 48000
2009-02-03 09:03:49.927 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2009-02-03 09:03:49.982 Opening audio device 'spdif'. ch 2(2) sr 48000
2009-02-03 09:03:49.982 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2009-02-03 09:03:55.580 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-02-03 09:03:55.719 OSD Theme Dimensions W: 640 H: 480
2009-02-03 09:03:56.155 TV: Changing from None to WatchingPreRecorded
2009-02-03 09:03:56.180 New DB connection, total: 4
2009-02-03 09:03:56.180 Connected to database 'mythconverg' at host: localhost
2009-02-03 09:03:56.192 Realtime priority would require SUID as root.
2009-02-03 09:03:56.250 TV: Attempting to change from WatchingPreRecorded to None
2009-02-03 09:03:56.289 Video sync method can't support double framerate (refresh rate too low for bob deint)
2009-02-03 09:03:56.291 Video timing method: USleep with busy wait
2009-02-03 09:03:56.333 TV: Changing from WatchingPreRecorded to None
2009-02-03 09:03:56.729 DPMS Reactivated.
2009-02-03 09:03:56.865 AFD: Opened codec 0x88c2e50, id(MPEG2VIDEO) type(Video)
2009-02-03 09:03:56.865 AFD: codec AC3 has 6 channels
2009-02-03 09:03:56.865 AFD: Opened codec 0x8492430, id(AC3) type(Audio)
2009-02-03 09:03:56.865 AFD: codec AC3 has 1 channels
2009-02-03 09:03:56.866 AFD: Opened codec 0x83554d0, id(AC3) type(Audio)
2009-02-03 09:03:56.866 AFD: codec AC3 has 6 channels
2009-02-03 09:03:56.866 AFD: Opened codec 0x848e7f0, id(AC3) type(Audio)
2009-02-03 09:03:57.401 AFD: Opened codec 0x848e7f0, id(MPEG2VIDEO) type(Video)
2009-02-03 09:03:57.401 AFD: codec AC3 has 6 channels
2009-02-03 09:03:57.401 AFD: Opened codec 0x83554d0, id(AC3) type(Audio)
2009-02-03 09:03:57.401 AFD: codec AC3 has 1 channels
2009-02-03 09:03:57.402 AFD: Opened codec 0x8492430, id(AC3) type(Audio)
2009-02-03 09:03:57.402 AFD: codec AC3 has 6 channels
2009-02-03 09:03:57.402 AFD: Opened codec 0x88c2e50, id(AC3) type(Audio)
2009-02-03 09:03:58.557 AFD: Opened codec 0x88c2e50, id(MPEG2VIDEO) type(Video)
2009-02-03 09:03:58.557 AFD: codec AC3 has 6 channels
2009-02-03 09:03:58.557 AFD: Opened codec 0x8492430, id(AC3) type(Audio)
2009-02-03 09:03:58.557 AFD: codec AC3 has 1 channels
2009-02-03 09:03:58.558 AFD: Opened codec 0x83554d0, id(AC3) type(Audio)
2009-02-03 09:03:58.558 AFD: codec AC3 has 6 channels
2009-02-03 09:03:58.558 AFD: Opened codec 0x848e7f0, id(AC3) type(Audio)
2009-02-03 09:04:00.815 TV: Attempting to change from None to WatchingPreRecorded

---

### Post by t_hutch on 2009-02-22
interesting....that log doesn't exist on my system.

---

### Post by allene222 on 2009-02-22
/var/log/mythtv/mythfrontend.log

Did I type it wrong?  Here is a cut and paste...

Do a $locate  mythfrontend.log

Allen

---

### Post by t_hutch on 2009-02-23
I tried a locate and that didn't find anything. I did the rebuild last night, so hopefully I'll find out tonight if I can get sound.

Thanks,
Tim

---

### Post by t_hutch on 2009-02-25
OK...finally some progress. I got sound back, but now I can't get the digital to pass to my receiver. The sound is coming through the digital coax, but the dolby doesn't come through. I've tried the first two settings in the wiki for the asound.conf file, but both caused the sound to go away and only deleting the asound.conf file would bring it back.

Any thoughts?

Thanks,
Tim

---

### Post by allene222 on 2009-02-25
If you have the sound devices in Myth set to default and you delete the asound.conf file you should get an awful static sound from your analog outputs and nothing from the digital coax.

I looked at the specs for the foxconn 6150 and it looks like the spdif output is not on the rear panel of the board.  How are you hooking up to the spdif port?

I am a little unclear about a few details and think the best thing is if you write down as much information as you can including the output from the commands below.  

1) All the mythtv sound settings from the sound setup screen. 
2) $ locate .asoundrc
3) $ aplay -l
4) $ cat /etc/asound.conf
5) $ cat /proc/asound/version
6) $ cat /proc/driver/nvidia/version
7) The physical connection from the computer to the sound system including what the sound system is.
8 ) What you hear with the above setup
9) $ tail /var/log/mythtv/mythfrontend.log -n 40

In return I will stick with this until it is solved.

Allen

---

### Post by t_hutch on 2009-02-26
With the settings below, and no asound.conf file, I get audio out of the coax digital. I don't have an easy way to test the analog, but if you feel it will help debug, I'll find a way to test it.

Here's the information you requested:

1)Audio output device: ALSA:default
Passthrough output device: default
Max Audio Channels: Stereo
Upmix: Passive
Enable AC3 to SPDIF Passthrough: Checked
Enable DTS to SPDIF Passthrough: Checked
Aggressive Sound Card Buffering: Unchecked
Use Internal volume controls: Unchecked

2)No output

3)
```
tim@htpc-myth1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

4)
```
tim@htpc-myth1:~$ cat /etc/asound.conf
cat: /etc/asound.conf: No such file or directory

```

5)
```
tim@htpc-myth1:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.17.

```

6)
```
tim@htpc-myth1:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008
GCC version:  gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) 

```

7)The connection from the MB to the back of the case is a digital coax connector to comes off the header on the board. It actually comes with the MB, but I don't think the website shows it. It works fine under windows media center.

8)The sound now works out of the receiver, but it is not coming to the receiver as digital. I've tried the same file (a tv show, xvid) in my MCE build and myth. In MCE, receiver reports Dolby Digital 3/2. When played in myth, I get PCM, 48khz. The receiver is a fairly old (maybe 8 to 10 years) Sony STR DB830 with dolby digital and dts support.

9)
```
tim@htpc-myth1:~$ tail /var/log/mythtv/mythfrontend.log -n 40
tail: cannot open `/var/log/mythtv/mythfrontend.log' for reading: No such file or directory

```

Weird that it can't find this file. Are you running 8.10? Maybe they've moved it since previous versions.

Thanks!
Tim

---

### Post by t_hutch on 2009-02-27
Some more updates...

I get 2 channel sound only now. When I play with the asound.conf file, I get some interesting results. I won't run through all the configurations, but some of the options in Allen's wiki cause no sound at all. Some have the receiver recognizing sound (not digital though), but no sound comes out. The only way to get any sound is no asound.conf file.

I've done a ton of googling on this with many similar problems out there, but no concrete solutions. Some people have said they fixed the problem, but they fell into the solution and details are sketchy at best...

---

### Post by t_hutch on 2009-03-01
Little by little....making progress...

My receiver now recognizes that it is receiving a 5.1 digital input. However, no sound from the speakers. I can get sound with 2 channel audio. I've again gone through all Allen's plug-ins for asound.conf, but every time I do that, something fails. Here is an example from my mythfrontend.log file (which I finally got working, hint: you have to create a /var/log/mythtv directory and make it writable) when I put the formatting plug-in:

```
  pcm.!default {
     type plug
     slave {
        pcm "hw:0,2"
        format S32_LE
     }
  }

```

into my asound.conf file:

```
2009-03-01 22:19:26.804 AFD: Opened codec 0x9fd4560, id(MPEG4) type(Video)
2009-03-01 22:19:26.804 AFD: codec AC3 has 6 channels
2009-03-01 22:19:26.805 AFD: Opened codec 0x9fc4f70, id(AC3) type(Audio)
2009-03-01 22:19:26.809 Opening audio device 'default'. ch 2(2) sr 48000
2009-03-01 22:19:26.809 Opening ALSA audio device 'default'.
ALSA lib pcm_params.c:2135:(snd1_pcm_hw_refine_slave) Slave PCM not usable
2009-03-01 22:19:26.811 AudioOutput Error: Broken configuration for playback; no configurations available: Invalid argument
2009-03-01 22:19:26.811 AudioOutput Error: Unable to set ALSA parameters
2009-03-01 22:19:26.811 NVP: Disabling Audio, reason is: Unable to set ALSA parameters
```

Obviously there is some error occurring, but damn if I know what it means. Hopefully someone can decipher.

---

### Post by allene222 on 2009-03-02
We are learning some good things here.  I have 8.04.  I see you have figured out how to enable the log files so that is good.

I set up my system without asound.conf and to my amazement I also get sound out just as I did when asound.conf was there.  The shows that had dolby digital still had it and I know it was not 2 channel as all I got was center channel output for the part I was listening to.  My decoder showed dolby digital as well.   So, apparently the default configuration of alsa can output digital.  Very interesting.

Here is the asound.conf file that I use.
pcm.!default {
        type plug
        slave {
                pcm "hw:0,1"
                format S32_LE
        }
}

From your asound -l results, you should use hw:0,2 as you are.

Note that I only need the format line for one of my two decoders, the other one works fine either way.

I am a little confused as to where you are with your project here.  The best I can determine, you say you have digital sound output it is 2 channel and not surround as it is when you play it with another program.  Can you explain that a little more.

Also, you say you get different results with various of my configuration files.  Would it be possible to make a little table with the config file and the result you get, sound or no sound, channels, key error messages?

Another possibility is that this sound source you have is 2 channel and the other system was faking it out to surround.  I noticed that when I played another program back, a concert no less, that it was not dolby digital and the processor switched to ProLogic mode and gave me apparent surround but it was not dolby digital.

One more thing.  You say you are getting sound when you hook your spdif coax up to your processor but it is not digital.  I take it you mean that it is not dolby digital as it must be digital if you only have the spdif coax connected.  Can you clarify this?

So, if you have sound out of your processor can you also play a variety of sources and see if any of them indicate dolby digital or digital as you have been saying.  For me, the SoundStage concert was not dolby and the news program, 60 minutes, was dolby digital.  Go figure.

Allen

---

### Post by allene222 on 2009-03-02
I just noticed that your passthrough device is "default" and I would expect it to be "ALSA:default".

That may or may not be significant but it is worth taking a look at.

Allen

---

### Post by t_hutch on 2009-03-02
Allen,

You hit the nail on the head when it comes to what my videos actually had for audio. Turns out some of my video that I thought had AC3 6 channel audio, actually only had 2 channel. Windows must have been transcoding for the sake of consistency. I do now have a video that actually has AC3 6 channel audio confirmed by a video analysis program.

The state of my system is now that I get perfect 2 channel sound (through spdif, so, yes, it is digital) from my videos that only have 2 channel sound. The video clip that is encoded using AC3 DVM codec with 6 channels will not produce sound, but the receiver does see it. Usually the first time I play it, it registers as dolby 2 channel. Subsequent plays will get it to switch to 6 channel dolby digital, but still produces no sound. All that leads me to that formatting plug-in you suggested, but as I stated before, that produced the audio error shown in my mythfrontend.log file. With that plug-in, my receiver sees nothing.

I will work tonight on trying the various plug-ins (at least the ones that make sense) and report the results. 

As for the ALSA:default versus just default....I don't have a ALSA:default option. I'll try just typing in ALSA:default and see where that gets me.

Thanks,
Tim

---

### Post by allene222 on 2009-03-02
You are correct, my mistake, it is "Default"  I will correct the wiki.

I am glad to hear we are making progress.  It does sound like you have the same situation I had before I added the format but my system plays without the asound.conf file with at least the one dolby digital source I tried.  However, as it is a passthrough situation, it could again be dependent on the source and it is possible some of the sources have the format one way and some another so that I might be in the same situation as you without asound.conf.  If you want to clip part of a file and send it I can try playing it both ways.  Or, we could record some of the same shows if you are in the US and getting your programs OTA.

On the format, we might have different versions of alsa and I know there are lots of differences between 8.04 and 8.10 so that could be what is going on here.  In my research on solving my own problem, I did find that the format line I used is used in the spdif configs.

I would have hope that the spdif plugin might work with the only fear being that you system used device 2 instead of 1.  But you should try it.


Allen

---

### Post by t_hutch on 2009-03-02
Good News/Bad News....

I got the asound.conf file to stop error out my setup, but I'm still not getting sound. The key was I needed to capitalize the D in Default. I'm kind of a noobie to Linux, but this should have dawned on me sooner. I've tried all the plug-in's but no luck. They all result in the same output in the log file:

```
2009-03-02 19:38:11.210 AFD: Opened codec 0x86fcdf0, id(MPEG4) type(Video)
2009-03-02 19:38:11.210 AFD: codec AC3 has 6 channels
2009-03-02 19:38:11.211 AFD: Opened codec 0x86fc210, id(AC3) type(Audio)
2009-03-02 19:38:11.215 Opening audio device 'default'. ch 2(2) sr 48000
2009-03-02 19:38:11.215 Opening ALSA audio device 'default'.
2009-03-02 19:38:11.226 Opening audio device 'default'. ch 2(2) sr 48000
2009-03-02 19:38:11.226 Opening ALSA audio device 'default'.
```

They get my receiver to recognize the six channels but no sound. Each one does the same. Any thoughts? Any other plug-ins that may help?

Tim

---

### Post by allene222 on 2009-03-02
What "D" did you capitalize?  

Allen

---

### Post by t_hutch on 2009-03-02
The D in Default.

This is the latest version of asound.conf I've been trying:

```
pcm.!Default {
       type hw
       card 0
       device 2
   }


pcm.!Default {
     type plug
     slave.pcm "spdif"
  }
```

Tim

---

### Post by allene222 on 2009-03-02
I think that needs to be "default" with a small "d" and what you have done is break it so it does the same thing it would do without the file.

Allen

---

### Post by t_hutch on 2009-03-03
You could be right. If so, any thoughts on what is causing the errors? Is there some part of ALSA that those plug-ins use that I don't have installed?

Would there be any hope that 8.04 would be a better build for me, being a long term build and all? I'm grasping at straws at this point, but I'm not apposed to one more build before taking more drastic measure (i.e. trying to buy a known good sound card...)

Tim

---

### Post by allene222 on 2009-03-03
I can't remember if you have updated alsa.  There is a new version, I think 10.0.19.  I don't think that is it but updating might bring in all the files again.  It is an important update for HDMI motherboards.
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

I have 3 systems built on 8.04 and they all work.  One is digital and the other 2 are analog.  I tried to build a 4th using 8.10 and got so frustrated that I decided 3 systems was enough.  I thought it was because of my familiarity with 8.04 but I am in no position to say 8.10 is fine.  I will leave it at that.  

Allen

---

### Post by t_hutch on 2009-03-03
I just recently did the ALSA upgrade as a hail mary. Didn't do much for me. I'll do some poking around tonight to see if there is some obvious ALSA component not installed for some reason. Otherwise, I'll give 8.04 a try.

Thanks,
Tim

---

### Post by allene222 on 2009-03-03
Well, there is no file with "S32_LE" in the name on my system so I don't know what it is.  It sounds like your decoder doesn't like the format of the data.  The other thing to try would be to see if you can find the source for the spdif plug-in and copy it with the change from device 1 to device 2.

I took a look and could not find what I was looking for but I did find someone who liked this for the config file

pcm.!default {
type plug
slave {
pcm "spdif"
rate 48000
format S16_LE
}
}

You might try it and also some of the other ones with just the rate 4800 line.  This is a shot in the dark but easier than reinstalling without knowing it will help.

Allen

---

### Post by t_hutch on 2009-03-03
In your myth settings for audio, is your ALSA:default with a D or a d for default? That's where I was getting my theory about capitalizing the D. Mine is a Capital D.

I'll try the asound.conf file you suggested when I get home. I was playing with the rate plug-in last night with no effect. I also went through xine, vlc, mplayer, etc to see if any of those GUI's provided a toggle that would pass the audio properly. No luck... 

If this new asound doesn't work, I'm at a loss. I think a build at 8.04 might be in order as I can't think of anything else to do. It's a sad day, google has failed me on this one. (Not my quote, paraphrased from someone else with a similar sound issue...)

Tim

---

### Post by allene222 on 2009-03-03
Within the asound.conf files use lower case throughout in everything I have seen. Within myth, there is "ALSA:default", I believe and "Default" for the two settings.  If you have ALSA:Default, then you might be right to use Default within asound.conf as I assume that it will match case sensitive.

If you check and find you have ALSA:Default, I check my system again.

Allen

---

### Post by t_hutch on 2009-03-03
Some different results tonight. Forget what I was on about D vs. d....that was nothing. I was wrong. My setting was ALSA:default.

So, with the following asound.conf file, my receiver recognized a PCM 48000 sound, but not dolby 5.1. Still no sound. At least now it is not erroring in the log. I think it needs the first plug to define what "slave" is. I'm guessing anyway...

```
pcm.!default {
     type plug
     slave.pcm "iec958"
  }

pcm.!default {
type plug
slave {
pcm "iec958"
rate 48000
format S16_LE
}
}
```

I tried a bunch of different variables (iec958 vs. spdif, 16 vs. 32) with similar results.

Still leaning towards a 8.04 build unless you have any last minute suggestions...

Thanks,
Tim

---

### Post by allene222 on 2009-03-04
The only question I have is that you have this time and before shows two configurations when you say what  your file is.  I hope that you are just showing two files and not the content of a single file with two default definitions.  

My file is:
...........start of file..........
  pcm.!default {
     type plug
     slave {
        pcm "hw:0,1"
        format S32_LE
     }
  }
.............end of file............

Now, this file could be written in two parts, the default section what would call out a plug by name and a plug definition.  The way it is written above is just a way to combine those two statements into one by defining the slave right in the call out to the plug.  I have tried it both ways and they both work.
So, the file above would be equivalent to this file:

...........start of file.............
  pcm.!default {
     type plug
     slave allen_plug
}

pcm_slave.allen_plug{
        pcm "hw:0,1"
        format S32_LE
  }
...........end of file................

The only other thing I can suggest is to ask if you have tried playing a CD using this commend?
$ mplayer -cache 500 -cdrom-device /dev/cdrom cdda://

Also, some times it seems like I have to reboot to get the changes to stick in alsa when I would think a restart of X would be enough.  I think it might not be.

Allen

---

### Post by t_hutch on 2009-03-04
I was putting multiples in. I understand these plug-ins better now, thanks. However, it still isn't working. I've tried every combination of S32_LE, S16_LE, rate settings, pcm "iec958", pcm "spdif", pcm "hw:0,2", etc. that I could think of. Every time I put something in the asound.conf file, the receiver doesn't recognize the dolby 5.1 like it does without the asound.conf file.

Most settings don't show an error in the log file, except S32_LE. That errors as such:

```
2009-03-04 19:52:07.760 AFD: Opened codec 0x867b4e0, id(MPEG4) type(Video)
2009-03-04 19:52:07.760 AFD: codec AC3 has 6 channels
2009-03-04 19:52:07.760 AFD: Opened codec 0x867bc50, id(AC3) type(Audio)
2009-03-04 19:52:07.767 Opening audio device 'default'. ch 2(2) sr 48000
2009-03-04 19:52:07.767 Opening ALSA audio device 'default'.
ALSA lib pcm_params.c:2135:(snd1_pcm_hw_refine_slave) Slave PCM not usable
2009-03-04 19:52:07.771 AudioOutput Error: Broken configuration for playback; no configurations available: Invalid argument
2009-03-04 19:52:07.771 AudioOutput Error: Unable to set ALSA parameters
2009-03-04 19:52:07.772 NVP: Disabling Audio, reason is: Unable to set ALSA parameters
```

Only no asound.conf file results in the receiver at least recognizing the 5.1 sound, but producing no sound from the speakers.

At this point, I'm going to go for the 8.04 build. We'll see what happens tonight, if I get enough time to do it...

Tim

---

### Post by t_hutch on 2009-03-04
I officially give up. At least on this hardware. I'm getting the same behavior on 8.04.

One last thought....every plug-in I've seen has card 0, device 1. Why is mine device 2? Is there anyway to change that? Is there some bug that prevents ALSA from properly formatting on a device other than 1?

Finally, can someone suggest a known good sound card with either optical or coaxial output? Just in case I want to beat my head against the wall more...

Allen...thanks for all your help!

Tim

---

### Post by allene222 on 2009-03-05
I have seen others give up and just grab an old soundblaster they had around from a computer 10 years ago and it worked fine.  You are not asking the sound card to do anything except pass the spdif out. Some cards only run at one rate so they might not work.  Others have sung the praise of Turtle Beach cards.

Most spdif cards have analog device 0 and digital device 1.  Yours has your digital on device 2 as per aplay -l

I don't think that is a big deal if you are using a config file as you can specify it.

Sorry to hear it didn't work out.  Please post what happens with the new sound card.

I don't know the card but did notice free shipping on this one right now.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16829118103](http://www.newegg.com/Product/Product.aspx?Item=N82E16829118103)

Allen

---

### Post by t_hutch on 2009-03-15
Finally!!!!! It works....

Installed the card you suggested and disabled the on board sound through the bios. I went through ALSAmixer and unmuted everything and turned up all the volumes. I deleted everything in the asound.conf file.

This is where my experience parts from the wiki your provided went in a different direction. With the settings you suggested, I still got no sound or any response from my receiver. Once I selected ALSA:iec958:{ AES0 0x02 } as the passthrough device, I got full AC3 and dts passthrough. However, I lost 2 channel sound. After some more monkeying around, I selected ALSA:spdif as the output device and now both AC3/dts and 2 channel sound live together!!!

Again, thanks for all the help! While frustrating at times, I did learn alot.

---

### Post by allene222 on 2009-03-15
Glad you got it working.  If you would not mind just clarifying something to help me out here in my understanding.  Are you saying that having the passthrough device set to Default and the audio output device set to ALSA:default and having the following asound.conf:

  pcm.!default {
     type plug
     slave.pcm "spdif"
  }

that this didn't work?  This should be equivalent to the setting you have that worked and will allow firrefox to output digital sound as well.

Allen

---

### Post by t_hutch on 2009-03-16
I stopped as soon as I had success. I just set it up as you suggested and it worked just fine. I will stick with this asound.conf file as you suggested. I think you just saved me more frustration when I get around to trying firefox!

Thanks,
Tim

---

### Post by allene222 on 2009-03-16
Glad to hear it.  You will be happier with it set up this way.

Allen

---

