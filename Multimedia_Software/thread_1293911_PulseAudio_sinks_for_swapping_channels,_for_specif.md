---
title: "PulseAudio sinks for swapping channels, for specific programs"
date: 2009-10-17
forum: Multimedia Software
---

### Post by NY00123 on 2009-10-17
[SIZE=4][COLOR=Red]UPDATE (Feb 9th 2012): The guide has been updated again in order to take care of an issue that has been detected. A few more updates have been applied to the latest guide (not the older, pre-11.04 one).[/COLOR][/SIZE]
[SIZE=4][COLOR=Red]
UPDATE (Sep 15th 2011): The originally posted instructions, at least for the sinks, don't seem to work as expected on Ubuntu 11.04. Furthermore, it looks like it's now way easier to enable surround sound. So, I consider the original instructions out of date. See the following text for more up-to-date instructions.
Furthermore, this thread's title has been edited, so it's now more relevant.[/COLOR][/SIZE]

As mentioned in the original post (before any update), if you want to play Doom 3 or Quake 4 with 5.1 sound channels, you'd want to swap between the rear channels and center/lfe ones. This is because the games use a different channel mapping.
If you wonder why, then, at least as a guess, look for "ALSA and surround sound" here: [http://www.volkerschatz.com/noise/alsa.html](http://www.volkerschatz.com/noise/alsa.html)

_**Before you read the instructions:**_ Note that this thread does **NOT** intend to solve any problem in Doom 3 or Quake 4 regarding sound latencies. This is for a different thread. I'll briefly mention two ways which may help, though:
1. One is by using ALSA directly, with pasuspender and an ALSA way of swapping channels (see "ALSA in surround sound" in [http://www.volkerschatz.com/noise/alsa.html](http://www.volkerschatz.com/noise/alsa.html) for a way of configuring channel swaps). A disadvantage of this is that the game would block all other applications from outputting sounds, but it may still be better for some users than the following alternative.
2. Another way is alsa-oss. It has been tested with Doom 3, using its OSS interface. On a 64-bit Ubuntu installation this would be somewhat more tricky (you need a 32-bit libaoss), but it's technically possible. To swap channels, you can simply follow the instructions in this post for PulseAudio. Sound mixing with different applications does work, although a few sound glitches may pop up in the game (e.g. a little sound being heardf after loading a saved game in the very beginning).
I'd add, though, that for the 64-bit case, you may need to apply the following steps (relevant to 11.10):
- Install the 32-bit flavor of alsa-oss (look for getlibs in order to find a way that, sorta, works).
- Create the following symbolic link (assuming doom3 is installed to /usr/local/games/doom3):
```
/usr/local/games/doom3/libalsatoss.so.0 -> /usr/lib32/libalsatoss.so.0
```- Manually preload libaoss.so, rather than using the supplied aoss script:
```
LD_PRELOAD=/usr/lib32/libaoss.so.0 doom3
```- Oh and, of course, tell Doom 3 to use OSS for sound output.

Alright, lets begin.

_** Instructions for surround sound channel swapping****:**_

1. Open /usr/share/pulseaudio/alsa-mixer/profile-sets/default.conf for editing, having root privileges. Here's how it can be done on Ubuntu 11.04 with gedit:
```
gksu gedit /usr/share/pulseaudio/alsa-mixer/profile-sets/default.conf
```2. Now, just a little word of warning: The following step applies to the common 3.5mm audio jacks. It has **not** been tested with HDMI or SPDIF connections.
Look for some text similar to the following:

```

[Mapping analog-surround-51]
device-strings = surround51:%f
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe
paths-output = analog-output analog-output-speaker analog-output-desktop-speaker analog-output-lfe-on-mono
priority = 8
direction = output

[Mapping analog-surround-71]
device-strings = surround71:%f
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right
description = Analog Surround 7.1
paths-output = analog-output analog-output-speaker analog-output-desktop-speaker analog-output-lfe-on-mono
priority = 7
direction = output

```We're going to add a very similar mapping for 5.1 channels, just with a different channel order. Furthermore, we need to give it some description.
Here's the text I've added and tested:

```

[Mapping analog-surround-51-doom3swap]
device-strings = surround51:%f
channel-map = front-left,front-right,front-center,lfe,rear-left,rear-right
description = Analog Surround 5.1 D3 remapping
paths-output = analog-output analog-output-speaker analog-output-desktop-speaker analog-output-lfe-on-mono
priority = 8
direction = output

```3. Before we continue, it is possible that steps 4a and 4b are going to fail, with no new "doom3" profile in sight. You may need to edit a different profile set file in a similar manner.
At least in my case, on a later installation, I've had to edit /usr/share/pulseaudio/alsa-mixer/profile-sets/extra-hdmi.conf.

4a. Now, on to toggling the channel swapping, the GUI way:
You can open the Sound Preferences in the UI, select the "Hardware" tab, pick-up the relevant sound device, and choose the output+input combination that you want.
You should spot a new "Analog Surround 5.1 D3 remapping" for the output, appearing in a few places. This is the same as the original ("Analog Surround 5.1" here), just with the different channel order. You may test it by clicking on "Test Speakers" and then checking, channel by channel.
To restore the original channel order, simply choose the original selection.

4b. The same thing but the command line way:
Type in the following command:
```
pactl list cards
```Now you should see a list of the installed sound cards, along with relevant profiles. If everything works as expected, you should see lines looking like the following ones in the output:
```

Card #1
Name: alsa_card.pci-0000_00_1b.0
.
.
.
        output:analog-surround-51: Analog Surround 5.1 Output (sinks: 1, sources: 0, priority. 800)
        output:analog-surround-51+input:analog-stereo: Analog Surround 5.1 Output + Analog Stereo Input (sinks: 1, sources: 1, priority. 860)
        output:analog-surround-51+input:iec958-stereo: Analog Surround 5.1 Output + Digital Stereo (IEC958) Input (sinks: 1, sources: 1, priority. 855)
        output:analog-surround-51-doom3swap: Analog Surround 5.1 D3 remapping Output (sinks: 1, sources: 0, priority. 800)
        output:analog-surround-51-doom3swap+input:analog-stereo: Analog Surround 5.1 D3 remapping Output + Analog Stereo Input (sinks: 1, sources: 1, priority. 860)
        output:analog-surround-51-doom3swap+input:iec958-stereo: Analog Surround 5.1 D3 remapping Output + Digital Stereo (IEC958) Input (sinks: 1, sources: 1, priority. 855)

```Now we can change to the Doom 3 sound profile. For our example, we'd select the one combining stereo input:
```

pactl set-card-profile alsa_card.pci-0000_00_1b.0 output:analog-surround-51-doom3swap+input:analog-stereo

```Now you can check the channel order from the GUI as before, or from the command line using:
```

speaker-test -c6

```We can restore the profile in a similar manner. In case one wants analog stereo input combined, the following command should do the job:
```

pactl set-card-profile alsa_card.pci-0000_00_1b.0 output:analog-surround-51+input:analog-stereo

```5. The command line way is useful if one wants to temporarily swap the channels for a specific application. Here is a simple example:
```

pactl set-card-profile alsa_card.pci-0000_00_1b.0 output:analog-surround-51-doom3swap+input:analog-stereo
doom3
pactl set-card-profile alsa_card.pci-0000_00_1b.0 output:analog-surround-51+input:analog-stereo

```[SIZE=4][COLOR=Red] Original post (irrelevant to 11.04, please read the above instructions if you're using 11.10; They should be relevant to 11.04, although untested as of these days):[/COLOR][/SIZE]

Hello everybody,

Some of you have probably had channel swap issues. Here's what I had.
Basically, I have 5.1 speakers, working as expected in the 'speaker-test' program using PulseAudio (now that 6 channels are set).
However, the Rear and Center/LFE channels seem to be swapped in the Doom 3 and Quake 4 games, when surround sound is enabled, and sound device is the default or "best".

So, after I couldn't a quick solution by myself, and using a search engine to look for useful information, I finally got something which seems to work.

**Before you read this**, I must say that a few assumptions are made:
1. You've got a single sound card configured.
2. You're using PulseAudio (which is the case if you've got Ubuntu 9.04).
3. When you try testing 5.1 channels output with the 'speaker-test' program, it works as expected.

So here's what should be done, assuming the above assumptions are met, of course.

1. Find the files default.pa and daemon.conf in /etc/pulse, and make a copy of them in the directory ~/.pulse, assuming there isn't one already. The command line way, using a terminal:

```
mkdir ~/.pulse
cp /etc/pulse/default.pa /etc/pulse/daemon.conf ~/.pulse
```2. Now open the file ~/.pulse/daemon.conf for editing. Here's how it can be done in Ubuntu with a GNOME desktop environment, using the command line:

```
gedit ~/.pulse/daemon.conf
```Look for the following line of code:

```
; default-sample-channels = 2
```Basically, you should have this in order to take advantage of 5.1 channels:

```
default-sample-channels = 6
```3. In order to test 5.1 channels output, restart PulseAudio. A safe way to do it is by logging out and then logging in again.
A quicker way, if you feel like doing it, is by typing the following commands:

```
pulseaudio -k
pulseaudio --start --log-target=syslog
```Now you can test it by typing the following command into the terminal:

```
speaker-test -c6
```4. Now open the file ~/.pulse/default.pa for editing in the same way.
Here is where it's important that the above assumptions are met. Start by finding the code section related to detection of devices. Here's how it looks like here:

```
### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect tsched=0
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif
```Right after these lines, add the following lines of code:

```
load-module module-remap-sink sink_name=doom3 master=0 channels=6 master_channel_map=front-left,front-right,rear-left,rear-right,center,lfe channel_map=front-left,front-right,center,lfe,rear-left,rear-right
set-default-sink 0
```Basically, the first command is used to create a new PulseAudio Sink, which is a Remapping Sink, used to change the order of channels. The expression master=0 relates to a Sink already being used, assuming there's one sound card only.
The second command is used to set the usual output Sink you've already got to be the default. Maybe not necessary, but it may avoid issues.

5. Restart PulseAudio. You can see step 3 for details.

6. Now here's how you can make a game use the doom3 sink to swap channels.
As an example, for Doom 3, begin by starting a game with the following command:

```
PULSE_SINK=doom3 doom3
```Note that it's possible you get no sound, even though Doom 3 had sound working with PulseAudio before. It may just be that the game was launched a bit before the sink was changed, so it should be temporary.
Future launches of Doom 3, without setting PULSE_SINK, should now work with the new Remapping Sink. It least it seems to work for me.

Here's a similar example for Quake 4, using the quake4-smp executable:

```
PULSE_SINK=doom3 quake4-smp
```7. If you want to revert back to the original sink for a certain application like doom3, here's a command that can be used to do the job:

```
PULSE_SINK=0 doom3
```

---

### Post by lupusnoctu on 2009-12-16
Thank you for the guide. It ALMOST helped me. lol.  I have it set up with World of Warcraft via WINE, but I still can't get it right. I've explained my issue in detail at [http://forum.winehq.org/viewtopic.php?t=7105](http://forum.winehq.org/viewtopic.php?t=7105) and will be copying this post over to that thread.

Using this guide, I've tried remapping several different ways, but I just can't seem to get it right... Leaving the front/rear-left/right alone, but swapping center/lfe to lfe/center produced the proper change... I was thinking that maybe either WINE or WoW was thinking lfe was rear-center, but they're not, so that's good. I put it back to center/lfe.

I then tried physically unplugging all channels except center/lfe from from the soundcard. Coming out of the center, I heard what was behind me, and LFE was producing lf sound from all directions, as it should. This made me think that maybe WoW thinks there is a rear-center and front-center, and has the two swapped.

I then plugged everything back in and tried the following and there was no change...
```
master_channel_map=front-left,front-right,rear-left,rear-right,center,lfe channel_map=front-left,front-right,rear-left,rear-right,rear-center,lfe
```
and
```
master_channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe channel_map=front-left,front-right,rear-left,rear-right,rear-center,lfe
```

I'm out of ideas. Please help.

EDIT: I also forgot to mention that I tried swapping front/rear-left/right to rear/front-left/right and confirmed that it's just the center channel that's messed up.

Thank you,
LupusNoctu

---

### Post by gumpish on 2010-03-03
I hope this isn't horribly off-topic, but as someone who found this thread while looking for just a way to swap left and right, I found the procedure outlined in this link worked for me (9.04):

[http://pulseaudio.org/wiki/FAQ#HowcanIreversemyleftandrightspeakerchannels](http://pulseaudio.org/wiki/FAQ#HowcanIreversemyleftandrightspeakerchannels)

---

