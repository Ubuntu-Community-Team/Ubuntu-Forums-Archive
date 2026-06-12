---
title: "USB sound card?"
date: 2011-04-10
forum: Multimedia Software
---

### Post by hopkinskong on 2011-04-10
Hello,
 
I just bought a usb sound card, and but there is no sound...
 
In System->Preferences->Sound->Hardware Tab, no device!
 
dmesg | grep -i usb, have my usb sound card,
 
cat /proc/asound/cards
```

1[Set]: USB-Audio - USB Headphone Set
            USB Headphone Set at usb-msm-hsusb-1.4, full speed

```
 
cat /proc/asound/modules
```

1 snd_usb_audio

```
 
i found my sound card in aplay -l, but in /etc/modprobe.d/alsa-base, it was BLANK!
 
Any solution to fix?
 
Thanks

---

### Post by Yellow Pasque on 2011-04-10
> but in /etc/modprobe.d/alsa-base, it was BLANK!
..that's because it's named alsa-base.conf !!!!11

Run alsa-info script: [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

---

### Post by hopkinskong on 2011-04-11
lol.. i'll try later, do that script need root?

thx

---

### Post by hopkinskong on 2011-04-11
Lol, i don't know what happened, after i ran your script, without root, it comes out few error, then it told me to replace sth or what, then i pressed CTRL+C to abort the program...
 
After that, i rebooted, the usb sound card appeared in my System->Perferences->Sound->Hardware!
 
Sound tested, ok, but mic seems not work! Any solution?
 
 
Do i need still to run that script with root again?
 
[color=red]UPDATE: Still no sound output, just sometimes have sound, some times doesn't have, when i playing a music, it have sound about 5-10 sec, then sound muted(i mean no sound, not i muted)[/color]
 
Thanks

---

### Post by hopkinskong on 2011-04-11
Any fix????

---

### Post by hopkinskong on 2011-04-12
Any help?

---

### Post by hopkinskong on 2011-04-13
hmm, no help?

---

### Post by hopkinskong on 2011-04-16
I found that system sound were working, justs only i can't using the music player to play music, the first 1,2 second have sound, and then no sound, even the whole song have no sound...
 
While i was playing the mp3, the system sound still work!
 
Some music player also can't detect my hardware!
 
Who can help me???
 
Thanks!

---

### Post by Yellow Pasque on 2011-04-16
You should still run the alsa-info script..

---

### Post by hopkinskong on 2011-04-17
> **Temüjin said:**
> You should still run the alsa-info script..
 
Already ran, with root user, it tolds me it will overwrite the original alsa-info.sh, press Ctrl+C to cancel, then i pressed enter.
 
Then the script turned nothing!(0.00KB)

---

### Post by hopkinskong on 2011-04-26
Can someone help me to finish this?

---

### Post by lidex on 2011-04-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by hopkinskong on 2011-04-30
Here is the output:

> 
--2011-04-30 16:51:04--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80](www.alsa-project.org|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2011-04-30 16:51:16--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [    <=>                                ] 27,247      25.6K/s   in 1.0s    

2011-04-30 16:51:23 (25.6 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.
pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.
pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.
pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.
Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=0977ba7b7cfe07aed5a9385792459f60aba3c3e0](http://www.alsa-project.org/db/?f=0977ba7b7cfe07aed5a9385792459f60aba3c3e0)

Please inform the person helping you.


Thanks!

---

### Post by lidex on 2011-04-30
Is it because of your processor you have such an odd kernel?
Try this:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo update-grub
```
**Reboot**
Now re-install alsa. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by hopkinskong on 2011-05-01
> **lidex said:**
> Is it because of your processor you have such an odd kernel?
Try this:
```
sudo apt-get update
``````
sudo apt-get upgrade
``````
sudo update-grub
```**Reboot**
Now re-install alsa. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```**Reboot.**
 
For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```
 
 
Wait... i will not upgrade my kernel! My kernel was a custom kernel, and it was ONLY specially designed for my device, if i upgrade it, my cpu, display, everything will not work!
 
I can re-install my alsa, but i think i can't touch anything about the kernel...
 
I may run:
sudo apt-get update
sudo apt-get -s upgrade
sudo apt-get upgrade
sudo apt-get install aptitude
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils libasound2
 
uname -r:
```

2.6.32.9-38182-g6ad7e77

```
 
uname -v:
```

#26 PREEMPT Sun Dec 26 00:12:43 CET 2010

```
 
 
Thanks!

---

### Post by hopkinskong on 2011-05-02
Ok. reinstalled, now, Music player STILL NOT WORK
 
System sound work!
Something weird, i installed this:
 
[http://appnr.com/package/gamix](http://appnr.com/package/gamix)
 
i tested my mic playback+recoding, when i talk, i can hear i am talking, so the usb sound card was work on playback, and the speaker was work...
 
 
[s]I'll try my mic using skype later[/s] Skype don't support my device...
 
PS. i am using Rhythmbox Music Player
 
 
[COLOR=red]Now, i got some good news, my GNOME MPlayer worked! there have sound, but only the sound of the left output was too softly..[/COLOR]
[COLOR=red]But still, Rhythmbox not work, quark, quod libet, and more music palyer not work! [s]Now let me try to install GStreamer first[/s](Installed, but nothing)...[/COLOR]
[COLOR=#ff0000]And one more thing, when i play my music (MPlayer or other no-sound player), my sound card light still flash![/COLOR]
 
Any fix? Thanks.

---

### Post by hopkinskong on 2011-05-03
Any help???

---

### Post by lidex on 2011-05-04
This is a tricky one. Can you post an updated alsa-info please?

---

### Post by hopkinskong on 2011-05-04
> **lidex said:**
> This is a tricky one. Can you post an updated alsa-info please?
 
Ok, but i get stucked!
 
Stucked at:
pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.
 
Just entered the next line, but nothing came out, the script still running...
 
[color=red]
May be that was the network problem? idk, trying uisng a faster conn speed
[/color]
 
Any fix? Thanks

---

### Post by hopkinskong on 2011-05-05
Here it is:
> 
--2011-05-05 17:12:57--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80](www.alsa-project.org|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2011-05-05 17:13:01--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [   <=>                                 ] 27,247      31.7K/s   in 0.8s    

2011-05-05 17:13:03 (31.7 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.
pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.
pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.
pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.
Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=af0e0cad09fc9d04cf9134b56842a6c75c02cb55](http://www.alsa-project.org/db/?f=af0e0cad09fc9d04cf9134b56842a6c75c02cb55)

Please inform the person helping you.

Thanks

---

### Post by hopkinskong on 2011-05-06
Pls help!
 
thx

---

### Post by hopkinskong on 2011-05-07
Any ones help?
 
Thanks a lot!

---

### Post by hopkinskong on 2011-05-07
Now, i tried VLC Player, and it works! Using Default output, but other player still didn't work, any solution?
 
PS I will try other output tomorrow...

---

### Post by hopkinskong on 2011-05-09
any help?

thanks

---

### Post by hopkinskong on 2011-05-09
> **talk-visa said:**
> you can install sound card but usb sound cards i think they are not soo much likeley to be used..other wise search on internet and install its ubunto driver for this device
 
[uk leading immigration specialist]("http://www.talk-visa.com/") , [leading immigration specialist]("http://www.talk-visa.com/") , [uk immigration specialist]("http://www.talk-visa.com/") , [uk visa management]("http://www.talk-visa.com/") , [studying in the uk ]("http://www.talk-visa.com/"), [uk work permit ]("http://www.talk-visa.com/"), [uk visa information]("http://www.talk-visa.com/") , [uk immigration experts]("http://www.talk-visa.com/") , [united kingdom immigration]("http://www.talk-visa.com/") , [immigrating to the uk]("http://www.talk-visa.com/"), [immigration service]("http://www.talk-visa.com/") , [immigration service in uk]("http://www.talk-visa.com/") , [immigration services in uk]("http://www.talk-visa.com/") , [immigration advice uk]("http://www.talk-visa.com/") , [uk immigration advice ]("http://www.talk-visa.com/")
 
There is no driver for this sound card, ALSA is enough
 
And NO ADVERTISEMNT!(What is your tags?)

---

### Post by hopkinskong on 2011-05-12
Any help? I have no sound for my computer now!

---

### Post by Yellow Pasque on 2011-05-12
Is VLC still working?
> And NO ADVERTISEMNT!(What is your tags?)
Don't respond to the spambots. Talking to a wall is more fulfilling.

---

### Post by lidex on 2011-05-12
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

Have you tried increasing speaker level in alsamixer?

---

### Post by hopkinskong on 2011-05-12
ALSA Mixer are not already removed in newer version in ALSA?
 
I just use the GUI version of mixer downloaded from the internet...
 
I used it to increasing my volume! I opened that thing and the music player at the same time and i pulled the volume to highest, but no help...
 
I'll try your command later...
 
Thanks

---

### Post by hopkinskong on 2011-05-13
Yes, VLC was work before..
 
/home/[username]/.asound* : No such file or dir
also /etc/asound.conf
 
Now rebooting...

---

### Post by hopkinskong on 2011-05-13
Yes, VLC was work before..
 
/home/[username]/.asound* : No such file or dir
also /etc/asound.conf
 
Now rebooting...
 
Rebooted!
 
All same!!! Nothing change!
 
And i want to add something, before(and after) i run that command(del pluseaudio conf), the VLC Volume Control was not working! This was very interesting! Even i mute in VLC, there was still output, but GNOME MPlayer's Volume control can control the volume...
 
Now going to install padevchooser...
 
[b]
Installed!
I used a non-working meida player, the sound card still flash, but the Volume Contol(Pluse video padevchooser)'s volume meter didn't raise... VLC, GNOME raise!
[/b]

---

### Post by lidex on 2011-05-13
What are your gstreamer settings. Set to auto:
```
gstreamer-properties
```

---

### Post by hopkinskong on 2011-05-14
> **lidex said:**
> What are your gstreamer settings. Set to auto:
```
gstreamer-properties
```
 
My GStreamer settings:
 
**Audio:**
Default Output:
Plugin: Autodetect
Device: Unsupported <=== This one was disabled(truned grey)
Pipeline: autoaudiosink <=== This one was disabled(truned grey), TEST FAILED, NO SOUND
 
Default Input:
Plugin: Custom
Device: None <=== This one was disabled(truned grey)
Pipeline: audiotestsrc <=== TEST FAILED, NO SOUND
 
[color=red]
I tried all Plugin, All device, all no sound!
[/color]

---

### Post by lidex on 2011-05-14
> **hopkinskong said:**
> My GStreamer settings:
 
**Audio:**
Default Output:
Plugin: Autodetect
Device: Unsupported <=== This one was disabled(truned grey)
Pipeline: autoaudiosink <=== This one was disabled(truned grey), TEST FAILED, NO SOUND
 
Default Input:
Plugin: Custom
Device: None <=== This one was disabled(truned grey)
Pipeline: audiotestsrc <=== TEST FAILED, NO SOUND
 
[color=red]
I tried all Plugin, All device, all no sound!
[/color]

Leave them both set to pulse audio.

---

### Post by hopkinskong on 2011-05-14
> **lidex said:**
> Leave them both set to pulse audio.
 
So plugin was pluse audio
 
I tried device as Default and Unknown, both still no sound...(I mean when i press the Test button)

---

### Post by lidex on 2011-05-14
Have you installed medibuntu and restricted extras?
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by hopkinskong on 2011-05-15
> **lidex said:**
> Have you installed medibuntu and restricted extras?
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
 No... I didn't install those...
 
I am only simply play a MP3 File using other player and no sound...
 
Should i install them?

---

### Post by lidex on 2011-05-15
> **hopkinskong said:**
> No... I didn't install those...
 
I am only simply play a MP3 File using other player and no sound...
 
Should i install them?

Yes.

---

### Post by hopkinskong on 2011-05-15
> **lidex said:**
> Yes.
 
Ok, i will install later.
 
In GStreamer Properties, Default Output, I used ALSA and Device as Default, the test works!
 
But in Input, i used ALSA, still no sound...

---

### Post by hopkinskong on 2011-05-16
Ok,
 
I got error when i install Mediubuntu, I added the source manually, and ran:
```

**wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update**

```
 
> 
W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/Release](http://packages.medibuntu.org/dists/karmic/Release) Unable to find expected entry free/binary-armel/Packages in Meta-index file (malformed Release file?)
 
W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/Release](http://packages.medibuntu.org/dists/maverick/Release) Unable to find expected entry free/binary-armel/Packages in Meta-index file (malformed Release file?)
 
E: Some index files failed to download, they have been ignored, or old ones used instead.

 
May be it does not support my cpu...
 
Next, i have ran:
```

**sudo apt-get install faac faad lame non-free-codecs ubuntu-restricted-extras**

```
Error:
> 
E: Unable to locate package non-free-codecs

 
Then, i ran:
```

**sudo apt-get install faac faad lame ubuntu-restricted-extras**

```
And it started to install...

---

### Post by hopkinskong on 2011-05-16
Hmm..
 
Now VLC seems something wrong, GNOME MPlayer still fine, VLC the sound suck, like some scratching sound(i can still heard it was playing the MP3)...
 
And other player... Not work!
 
In gstreamer-properties, Plugin=ALSA, Device=Default, test work <= in INPUT
 
Output use same setting still not work...
 
And i found that everytime i use a non-work player to play MP3, my pluseaudio(process) went very high and make my CPU full in-use(I was just a 998Mhz cpu)[THIS CASE EXCEPT RHYMBOX(this use totem(process) highly)]. Although my pulseaudio(process) still have some change when i use GNOME MPlayer, it was just about half of my cpu, not FULL!

---

### Post by hopkinskong on 2011-05-17
Any help?
thanks

---

### Post by lidex on 2011-05-17
This thread is way too long and I have lost the the point. Can you summarize what we are trying to accomplish now please? 
What is the problem now as it seems to have changed? And I know it's not your fault, but your wording is a little hard for me to understand.
What is the other player that doesn't work?

A little house-keeping:
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
* Ignore any 'No such file or directory' errors*
Now re-install pulse:
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
```
```
sudo apt-get install pulseaudio gstreamer0.10-pulseaudio
```
**Reboot.**
Next these outputs please:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

### Post by hopkinskong on 2011-05-19
> **lidex said:**
> This thread is way too long and I have lost the the point. Can you summarize what we are trying to accomplish now please? 
What is the problem now as it seems to have changed? And I know it's not your fault, but your wording is a little hard for me to understand.
What is the other player that doesn't work?
 
A little house-keeping:
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```*Ignore any 'No such file or directory' errors*
Now re-install pulse:
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
``````
sudo apt-get install pulseaudio gstreamer0.10-pulseaudio
```**Reboot.**
Next these outputs please:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
``````
pkill pulseaudio; sleep 2; pulseaudio -vv
```
 
Just rebooted, now trying sound, then try your command...
 
Seems worst(then before reinstall)...
 
> 
GSTREAMER-PROPERTIES:
Default Output:
Plugin: ALSA
Device: Default
Test:WORK! (CPU usage ~50%-60%)
 
Default Input:
Plugin ALSA
Device USB Audio
Test: Didn't work! (CPU usage ~100%)
> 
GNOME MPlayer: Work great, CPU usage: ~50%-90%, volume control work, sound not best(there will be some "jit" sound when playing)
KMPlayer: Work best, CPU usage ~50%-70%, volume control NOT WORK
VLC:
Work but worst, CPU usage ~90-100%, sound worst, volume control NOT WORK
 
Quark:
No sound, cpu usage no change
 
Quod Libet:
In first test, no sound, computer nearly stop working, CPU ~95%-100%
In second, third, forth test, sound work!
 
Rhythbox:
In first test, it was no sound, computer nearly stop working, CPU ~97%-100%
In second test, sound work! Cpu still high! Sound sometimes stop!
The "pulseaudio" process usage(when playing MP3):
> 
GNOME MPlayer: 15-20%(gnome-mplayer: 4%-5%)
KMPlayer: 20%-24% (mplayer:10-13%)
VLC: 0%(vlc: 40-60%)
Quark: 0%(quark:0%, strange-quark: 0%)
Quod Libet:18%-20%(/usr/bin/quodli: 22%) [WHEN SOUND WORK]
Quod Libet:18%-20%(/usr/bin/quodli: 70-80%) [WHEN SOUND NOTWORK]
Rhythmbox: 12-22%(totem: 11%)
I just want to make the CPU usage lower, fix the sound quality, and i want all player can use my sound card!
 
 
```

sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*

```Output:
```

                     USER        PID ACCESS COMMAND
/dev/snd/controlC1:  htc-linux   2914 F.... pulseaudio

``````

pkill pulseaudio; sleep 2; pulseaudio -vv

```Output(I can't copy all! There still have text before "D: alsa-mixer.c: Probing path 'analog-output-headphones'"): [COLOR=#ff0000]After this command, process went to 100%, even i can't open the system monitor![/COLOR]
```

D: alsa-mixer.c: Probing path 'analog-output-headphones'
D: alsa-mixer.c: Probe of element 'Headphone' failed.
D: alsa-mixer.c: Probing path 'analog-output-headphones'
D: alsa-mixer.c: Probe of element 'Headphone2' failed.
D: alsa-mixer.c: Probing path 'analog-output-mono'
D: alsa-mixer.c: Probe of element 'Master Mono' failed.
D: alsa-mixer.c: Probing path 'analog-output-lfe-on-mono'
D: alsa-mixer.c: Probe of element 'Master Mono' failed.
D: alsa-mixer.c: Some paths of the device lack hardware volume control, disabling hardware control altogether.
D: alsa-sink.c: Probed mixer paths:
D: alsa-mixer.c: Path Set 0x35bb0, direction=1, probed=yes
D: alsa-mixer.c: Path analog-output (Analog Output), direction=1, priority=99, probed=yes, supported=yes, has_mute=yes, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=0, max_dB=0
D: alsa-mixer.c: Element Speaker, direction=1, switch=1, volume=2, enumeration=0, required=0, required_absent=0, mask=0xbfaeb851eb851ebe, n_channels=2, override_map=no
D: alsa-mixer.c: Path analog-output-speaker (Analog Speakers), direction=1, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=no, has_dB=yes, min_volume=0, max_volume=38, min_dB=-28.37, max_dB=0
D: alsa-mixer.c: Element Speaker, direction=1, switch=1, volume=1, enumeration=0, required=4, required_absent=0, mask=0xbfaff851eb851ffe, n_channels=2, override_map=yes
D: alsa-mixer.c: Added 2 ports
I: sink.c: Created sink 0 "alsa_output.usb-0c76_USB_Headphone_Set-00-Set.analog-stereo" with sample spec s16le 2ch 48000Hz and channel map front-left,front-right
I: sink.c:     alsa.resolution_bits = "16"
I: sink.c:     device.api = "alsa"
I: sink.c:     device.class = "sound"
I: sink.c:     alsa.class = "generic"
I: sink.c:     alsa.subclass = "generic-mix"
I: sink.c:     alsa.name = "USB Audio"
I: sink.c:     alsa.id = "USB Audio"
I: sink.c:     alsa.subdevice = "0"
I: sink.c:     alsa.subdevice_name = "subdevice #0"
I: sink.c:     alsa.device = "0"
I: sink.c:     alsa.card = "1"
I: sink.c:     alsa.card_name = "USB Headphone Set"
I: sink.c:     alsa.long_card_name = "USB Headphone Set at usb-msm_hsusb-1.4, full speed"
I: sink.c:     alsa.driver_name = "snd_usb_audio"
I: sink.c:     device.bus_path = "platform-msm_hsusb-usb-0:1.4:1.0"
I: sink.c:     sysfs.path = "/devices/platform/msm_hsusb/usb1/1-1/1-1.4/1-1.4:1.0/sound/card1"
I: sink.c:     udev.id = "usb-0c76_USB_Headphone_Set-00-Set"
I: sink.c:     device.bus = "usb"
I: sink.c:     device.vendor.id = "0c76"
I: sink.c:     device.vendor.name = "JMTek, LLC."
I: sink.c:     device.product.id = "1607"
I: sink.c:     device.product.name = "audio controller"
I: sink.c:     device.serial = "0c76_USB_Headphone_Set"
I: sink.c:     device.form_factor = "headphone"
I: sink.c:     device.string = "front:1"
I: sink.c:     device.buffering.buffer_size = "384000"
I: sink.c:     device.buffering.fragment_size = "192000"
I: sink.c:     device.access_mode = "mmap+timer"
I: sink.c:     device.profile.name = "analog-stereo"
I: sink.c:     device.profile.description = "Analog Stereo"
I: sink.c:     device.description = "audio controller Analog Stereo"
I: sink.c:     alsa.mixer_name = "USB Mixer"
I: sink.c:     alsa.components = "USB0c76:1607"
I: sink.c:     module-udev-detect.discovered = "1"
I: sink.c:     device.icon_name = "audio-headphones-usb"
D: core-subscribe.c: Dropped redundant event due to change event.
I: source.c: Created source 0 "alsa_output.usb-0c76_USB_Headphone_Set-00-Set.analog-stereo.monitor" with sample spec s16le 2ch 48000Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of audio controller Analog Stereo"
I: source.c:     device.class = "monitor"
I: source.c:     alsa.card = "1"
I: source.c:     alsa.card_name = "USB Headphone Set"
I: source.c:     alsa.long_card_name = "USB Headphone Set at usb-msm_hsusb-1.4, full speed"
I: source.c:     alsa.driver_name = "snd_usb_audio"
I: source.c:     device.bus_path = "platform-msm_hsusb-usb-0:1.4:1.0"
I: source.c:     sysfs.path = "/devices/platform/msm_hsusb/usb1/1-1/1-1.4/1-1.4:1.0/sound/card1"
I: source.c:     udev.id = "usb-0c76_USB_Headphone_Set-00-Set"
I: source.c:     device.bus = "usb"
I: source.c:     device.vendor.id = "0c76"
I: source.c:     device.vendor.name = "JMTek, LLC."
I: source.c:     device.product.id = "1607"
I: source.c:     device.product.name = "audio controller"
I: source.c:     device.serial = "0c76_USB_Headphone_Set"
I: source.c:     device.form_factor = "headphone"
I: source.c:     device.string = "1"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-headphones-usb"
I: alsa-sink.c: Using 2.0 fragments of size 192000 bytes (1000.00ms), buffer size is 384000 bytes (2000.00ms)
I: alsa-sink.c: Time scheduling watermark is 20.00ms
D: alsa-sink.c: hwbuf_unused=0
D: alsa-sink.c: setting avail_min=95041
D: alsa-mixer.c: Activating path analog-output-speaker
D: alsa-mixer.c: Path analog-output-speaker (Analog Speakers), direction=1, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=no, has_dB=yes, min_volume=0, max_volume=38, min_dB=-28.37, max_dB=0
D: alsa-mixer.c: Element Speaker, direction=1, switch=1, volume=1, enumeration=0, required=4, required_absent=0, mask=0xbfaff851eb851ffe, n_channels=2, override_map=yes
I: alsa-sink.c: Driver does not support hardware volume control, falling back to software volume control.
I: alsa-sink.c: Using hardware mute control.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Hardware PCM card 1 'USB Headphone Set' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 48000
D: alsa-util.c:   exact rate   : 48000 (48000/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 96000
D: alsa-util.c:   period_size  : 48000
D: alsa-util.c:   period_time  : 1000000
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 95041
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1572864000
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1572864000
D: alsa-util.c:   appl_ptr     : 0
D: alsa-util.c:   hw_ptr       : 0
D: alsa-sink.c: Thread starting up
D: core-util.c: SCHED_RR|SCHED_RESET_ON_FORK worked.
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: alsa-sink.c: Starting playback.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:1
D: alsa-util.c: Maximum hw buffer size is 10922 ms
D: alsa-util.c: Set buffer size first (to 96000 samples), period size second (to 96000 samples).
I: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
I: alsa-source.c: Successfully opened device hw:1.
I: alsa-source.c: Selected mapping 'Analog Mono' (analog-mono).
I: alsa-source.c: Successfully enabled mmap() mode.
I: alsa-source.c: Successfully enabled timer-based scheduling mode.
I: alsa-mixer.c: Successfully attached to mixer 'hw:1'
D: alsa-mixer.c: Probing path 'analog-input'
D: alsa-mixer.c: Probe of element 'Capture' failed.
D: alsa-mixer.c: Probing path 'analog-input-microphone'
D: alsa-mixer.c: Probing path 'analog-input-linein'
D: alsa-mixer.c: Probe of element 'Line' failed.
D: alsa-mixer.c: Probing path 'analog-input'
D: alsa-mixer.c: Probe of element 'Aux' failed.
D: alsa-mixer.c: Probing path 'analog-input-video'
D: alsa-mixer.c: Probe of element 'Video' failed.
D: alsa-mixer.c: Probing path 'analog-input-video'
D: alsa-mixer.c: Probe of element 'TV Tuner' failed.
D: alsa-mixer.c: Probing path 'analog-input-radio'
D: alsa-mixer.c: Probe of element 'FM' failed.
D: alsa-mixer.c: Probing path 'analog-input'
D: alsa-mixer.c: Probe of element 'Mic/Line' failed.
D: alsa-source.c: Probed mixer paths:
D: alsa-mixer.c: Path Set 0x4ee28, direction=2, probed=yes
D: alsa-mixer.c: Path analog-input-microphone (Analog Microphone), direction=2, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=16, min_dB=0, max_dB=23.81
D: alsa-mixer.c: Element Mic, direction=2, switch=1, volume=1, enumeration=0, required=4, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: core-subscribe.c: Dropped redundant event due to change event.
I: source.c: Created source 1 "alsa_input.usb-0c76_USB_Headphone_Set-00-Set.analog-mono" with sample spec s16le 1ch 48000Hz and channel map mono
I: source.c:     alsa.resolution_bits = "16"
I: source.c:     device.api = "alsa"
I: source.c:     device.class = "sound"
I: source.c:     alsa.class = "generic"
I: source.c:     alsa.subclass = "generic-mix"
I: source.c:     alsa.name = "USB Audio"
I: source.c:     alsa.id = "USB Audio"
I: source.c:     alsa.subdevice = "0"
I: source.c:     alsa.subdevice_name = "subdevice #0"
I: source.c:     alsa.device = "0"
I: source.c:     alsa.card = "1"
I: source.c:     alsa.card_name = "USB Headphone Set"
I: source.c:     alsa.long_card_name = "USB Headphone Set at usb-msm_hsusb-1.4, full speed"
I: source.c:     alsa.driver_name = "snd_usb_audio"
I: source.c:     device.bus_path = "platform-msm_hsusb-usb-0:1.4:1.0"
I: source.c:     sysfs.path = "/devices/platform/msm_hsusb/usb1/1-1/1-1.4/1-1.4:1.0/sound/card1"
I: source.c:     udev.id = "usb-0c76_USB_Headphone_Set-00-Set"
I: source.c:     device.bus = "usb"
I: source.c:     device.vendor.id = "0c76"
I: source.c:     device.vendor.name = "JMTek, LLC."
I: source.c:     device.product.id = "1607"
I: source.c:     device.product.name = "audio controller"
I: source.c:     device.serial = "0c76_USB_Headphone_Set"
I: source.c:     device.form_factor = "headphone"
I: source.c:     device.string = "hw:1"
I: source.c:     device.buffering.buffer_size = "192000"
I: source.c:     device.buffering.fragment_size = "96000"
I: source.c:     device.access_mode = "mmap+timer"
I: source.c:     device.profile.name = "analog-mono"
I: source.c:     device.profile.description = "Analog Mono"
I: source.c:     device.description = "audio controller Analog Mono"
I: source.c:     alsa.mixer_name = "USB Mixer"
I: source.c:     alsa.components = "USB0c76:1607"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-headphones-usb"
I: alsa-source.c: Using 2.0 fragments of size 96000 bytes (1000.00ms), buffer size is 192000 bytes (2000.00ms)
I: alsa-source.c: Time scheduling watermark is 20.00ms
D: alsa-source.c: hwbuf_unused=0
D: alsa-source.c: setting avail_min=95041
D: alsa-mixer.c: Activating path analog-input-microphone
D: alsa-mixer.c: Path analog-input-microphone (Analog Microphone), direction=2, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=16, min_dB=0, max_dB=23.81
D: alsa-mixer.c: Element Mic, direction=2, switch=1, volume=1, enumeration=0, required=4, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
I: alsa-source.c: Hardware volume ranges from 0.00 dB to 23.81 dB.
I: alsa-source.c: Fixing base volume to -23.81 dB
I: alsa-source.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-source.c: Using hardware mute control.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Hardware PCM card 1 'USB Headphone Set' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 1
D: alsa-util.c:   rate         : 48000
D: alsa-util.c:   exact rate   : 48000 (48000/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 96000
D: alsa-util.c:   period_size  : 48000
D: alsa-util.c:   period_time  : 1000000
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 95041
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1572864000
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1572864000
D: alsa-util.c:   appl_ptr     : 0
D: alsa-util.c:   hw_ptr       : 0
D: alsa-source.c: Read hardware volume: 0: 100%
D: alsa-source.c: Thread starting up
D: core-util.c: SCHED_RR|SCHED_RESET_ON_FORK worked.
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: alsa-source.c: Starting capture.
I: (alsa-lib)pcm_hw.c: SNDRV_PCM_IOCTL_START failed (-32)
I: module.c: Loaded "module-alsa-card" (index: #4; argument: "device_id="1" name="usb-0c76_USB_Headphone_Set-00-Set" card_name="alsa_card.usb-0c76_USB_Headphone_Set-00-Set" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"").
I: module-udev-detect.c: Card /devices/platform/msm_hsusb/usb1/1-1/1-1.4/1-1.4:1.0/sound/card1 (alsa_card.usb-0c76_USB_Headphone_Set-00-Set) module loaded.
I: module-udev-detect.c: Found 1 cards.
I: module.c: Loaded "module-udev-detect" (index: #5; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-bluetooth-discover.so': failure
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #6; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #8; argument: "").
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
I: module.c: Loaded "module-always-sink" (index: #11; argument: "").
I: module.c: Loaded "module-intended-roles" (index: #12; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.usb-0c76_USB_Headphone_Set-00-Set.analog-stereo becomes idle, timeout in 5 seconds.
D: module-suspend-on-idle.c: Source alsa_input.usb-0c76_USB_Headphone_Set-00-Set.analog-mono becomes idle, timeout in 5 seconds.
I: module.c: Loaded "module-suspend-on-idle" (index: #13; argument: "").
D: dbus-util.c: Successfully connected to D-Bus system bus f711713aa3f09920de8588aa00000025 as :1.66
I: module.c: Loaded "module-console-kit" (index: #14; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #15; argument: "").
D: main.c: Got org.pulseaudio.Server!
I: main.c: Daemon startup complete.
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-device-restore.c: Storing volume/mute/port for device sink:alsa_output.usb-0c76_USB_Headphone_Set-00-Set.analog-stereo.
I: module-device-restore.c: Storing volume/mute/port for device source:alsa_output.usb-0c76_USB_Headphone_Set-00-Set.analog-stereo.monitor.
I: module-device-restore.c: Storing volume/mute/port for device source:alsa_input.usb-0c76_USB_Headphone_Set-00-Set.analog-mono.
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
I: module-suspend-on-idle.c: Source alsa_input.usb-0c76_USB_Headphone_Set-00-Set.analog-mono idle for too long, suspending ...
D: source.c: Suspend cause of source alsa_input.usb-0c76_USB_Headphone_Set-00-Set.analog-mono is 0x0004, suspending
I: alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.usb-0c76_USB_Headphone_Set-00-Set.analog-stereo idle for too long, suspending ...
D: sink.c: Suspend cause of sink alsa_output.usb-0c76_USB_Headphone_Set-00-Set.analog-stereo is 0x0004, suspending
I: alsa-sink.c: Device suspended...
D: reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio1 changed: not busy
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: core-subscribe.c: Dropped redundant event due to change event.
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
I: module-device-restore.c: Synced.
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes

```Thanks for help

---

### Post by lidex on 2011-05-19
I'm beginning to think your usb card is not supported, at least not with this kernel. I can't help you further.

---

### Post by hopkinskong on 2011-05-21
So anyone else can help me?
 
Thanks

---

