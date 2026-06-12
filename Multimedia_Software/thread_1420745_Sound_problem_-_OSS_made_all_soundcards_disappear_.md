---
title: "Sound problem - OSS made all soundcards disappear (SB X-Fi Xtreme Audio)"
date: 2010-03-03
forum: Multimedia Software
---

### Post by kidd79 on 2010-03-03
So here is my true, but sad story.

I am new with Ubuntu (first installed Karmic mid-February). So now I'm on dual boot Ubuntu 9.10 Karmic 64-bit / WinXP Home SP3 32-bit.

I noticed that sound is somehow weird when I'm logged in Ubuntu, so I googled a lot and found [this link]("https://help.ubuntu.com/community/OpenSound") on some forum. As poster mentioned, he followed the instructions carefully and hes problem (similar to mine) was completely solved.

I decided to give it a try. I followed all instructions step-by-step. However, I didn't pay too much attention to the note in "Preparation: removing pulseaudio" section of the guide:

> Note: You can't remove alsa-base in Hardy, or it will try and remove gdm.First, I was sure I was on Karmic, not Hardy (and I am still sure, whatever), second, I did not know at that moment what does "gdm" stand for. So when I run the respective commands, it said something about removing 26 packages (including "ubuntu-desktop" or something like that), and I agreed.

So when I came to the step when I needed to do something with my gdm ("Add a new custom application launcher to the panel"), gdm restarted and I found miself in plain console without any GUI. Command-line only - while "cd .." and "ls" were top of my knowlege. I was scared. I was shocked. But, somehow I got a bright idea: I typed "firefox" and it worked! So I googled and re-installed the gdm (even my compiz settings were restored, yay!) However, when I check system -> preferences -> sound -< devices, there is NOTHING.

Out-of-the-box I have had 2 sound cards - X-Fi (not working) and HDA (working). Now both are gone and I have no sound in video or audio players (It may sound weird, but flash objects like youtube videos sometimes still play sound - but sometimes they don't.)

I googled for 4 days but can't find anything helping, so you all guys are my last hope.

---

### Post by Yellow Pasque on 2010-03-03
> However, when I check system -> preferences -> sound -< devices, there is NOTHING.
That's an app checking for pulseaudio devices. If you're using OSS4, the app shouldn't even start. This leads me to believe you still have cruft from Pulseaudio hanging around on your system.

> what does "gdm" stand for.
GNOME Display Manager. It's the screen you see when you log in.

> Out-of-the-box I have had 2 sound cards - X-Fi (not working) and HDA (working).
Disable the onboard audio in the BIOS and restart. Fire up a terminal and:
```
sudo soundoff
sudo ossdetect -Lv
sudo soundon
```

If that doesn't work, post the output of 
```
ossinfo -v3
```

---

### Post by kidd79 on 2010-03-05
Thank you so much. Well, let's see..

> **Temüjin said:**
> That's an app checking for pulseaudio devices. If you're using OSS4, the app shouldn't even start. This leads me to believe you still have cruft from Pulseaudio hanging around on your system.Maybe it is so. However, I don't know how to check this out for sure, :(

> **Temüjin said:**
> GNOME Display Manager. It's the screen you see when you log in.Well, NOW I know it very well :)

> **Temüjin said:**
>  Disable the onboard audio in the BIOS and restart. Fire up a terminal and:
```
sudo soundoff
sudo ossdetect -Lv
sudo soundon
```Done, still no luck. Sound is present in embedded flash-objects, like, youtube or flash games, but not in audio- or video-players or games. Here's what I see when I try to run your commands:

```
kidd79@karmic:~$ sudo soundoff
kidd79@karmic:~$ sudo ossdetect -Lv
v/etc/devices.list: No such file or directory
kidd79@karmic:~$ sudo soundon
************************************************************
* NOTE! You are using trial version of Open Sound System   *
************************************************************
kidd79@karmic:~$
```> **Temüjin said:**
>  If that doesn't work, post the output of 
```
ossinfo -v3
```Well, it's quite long, but whatever:

```
kidd79@karmic:~$ ossinfo -v3
Version info: OSS 4.2 (b 2002/200911060720) (0x00040100) TRIAL
Platform: Linux/x86_64 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 (karmic)

Number of audio devices:    4
Number of audio engines:    8
Number of MIDI devices:        0
Number of mixer devices:    1

Device objects
 0: osscore0 OSS core services
 1: oss_audigyls0 AudigyLS
 2: oss_usb0 USB audio core services

MIDI devices (/dev/midi*)

Mixer devices
 0: AudigyLS Mixer (Mixer 0 of device object 1)
    Device file /dev/oss/oss_audigyls0/mix0, Legacy device /dev/mixer0
    Priority: 1
    Caps: 
    Device handle: PCI10131102-0000:01:07.0-mx01
    Device priority: 1

Audio devices
AudigyLS front                    /dev/oss/oss_audigyls0/pcm0  (device index 0)
    Legacy device /dev/dsp0
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Engine      1: 0/AudigyLS front
                     Available for use 
      Engine      2: 4/AudigyLS front (vmix)
                     Available for use 
      Engine      3: 5/AudigyLS front (vmix)
                     Available for use 
      Engine      4: 6/AudigyLS front (vmix)
                     Available for use 
      Engine      5: 7/AudigyLS front (vmix)
                     Available for use 
    Input formats (0x00000410):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_AC3        - AC3 (Dolby Digital) encoded audio
    Output formats (0x00000410):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_AC3        - AC3 (Dolby Digital) encoded audio
    Device handle: PCI10131102-0000:01:07.0-au01
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 1 - 2
    Native sample rates (min - max): 48000 - 48000
    HW Type: Not indicated.
    Minimum latency: Not indicated

AudigyLS center/lfe               /dev/oss/oss_audigyls0/pcm1  (device index 1)
    Legacy device /dev/dsp1
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 1/AudigyLS center/lfe
                     Available for use 
    Input formats (0x00000410):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_AC3        - AC3 (Dolby Digital) encoded audio
    Output formats (0x00000410):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_AC3        - AC3 (Dolby Digital) encoded audio
    Device handle: PCI10131102-0000:01:07.0-au02
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 1 - 2
    Native sample rates (min - max): 48000 - 48000
    HW Type: Not indicated.
    Minimum latency: Not indicated

AudigyLS surround                 /dev/oss/oss_audigyls0/pcm2  (device index 2)
    Legacy device /dev/dsp2
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 2/AudigyLS surround
                     Available for use 
    Input formats (0x00000410):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_AC3        - AC3 (Dolby Digital) encoded audio
    Output formats (0x00000410):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_AC3        - AC3 (Dolby Digital) encoded audio
    Device handle: PCI10131102-0000:01:07.0-au03
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 1 - 2
    Native sample rates (min - max): 48000 - 48000
    HW Type: Not indicated.
    Minimum latency: Not indicated

AudigyLS 5.1 output               /dev/oss/oss_audigyls0/pcm3  (device index 3)
    Legacy device /dev/dsp3
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 3/AudigyLS 5.1 output
                     Available for use 
    Input formats (0x00000010):
      AFMT_S16_LE    - 16 bit signed little endian
    Output formats (0x00000010):
      AFMT_S16_LE    - 16 bit signed little endian
    Device handle: PCI10131102-0000:01:07.0-au04
    Related mixer dev: -1
    Sample rate source: 0
    Preferred channel configuration: MULTICH
    Supported number of channels (min - max): 2 - 6
    Native sample rates (min - max): 48000 - 48000
    HW Type: Not indicated.
    Minimum latency: Not indicated

Nodes
  /dev/dsp -> /dev/oss/oss_audigyls0/pcm0
  /dev/dsp_in -> /dev/oss/oss_audigyls0/pcm0
  /dev/dsp_out -> /dev/oss/oss_audigyls0/pcm0
  /dev/dsp_ac3 -> /dev/oss/oss_audigyls0/pcm0
  /dev/dsp_mmap -> /dev/oss/oss_audigyls0/pcm0
  /dev/dsp_multich -> /dev/oss/oss_audigyls0/pcm3
kidd79@karmic:~$ 

```

I hope this makes some sense for you&#1073; because for me it does not :(

---

### Post by Yellow Pasque on 2010-03-05
If you're getting sound, then the drivers work. Maybe you just need to configure apps to use OSS output: [http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)
Can you give examples of applications that aren't working?

---

### Post by kidd79 on 2010-03-07
> **Temüjin said:**
> If you're getting sound, then the drivers work. Maybe you just need to configure apps to use OSS output: [http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)
Thank you for the link, I will try it and reply if this will work.

> **Temüjin said:**
> Can you give examples of applications that aren't working? vlc, Rhytmbox, Totem, gxine, Audacious2, system sounds, Urban Terror, Hedgewars.

---

### Post by kidd79 on 2010-03-09
Now this gets really funny.

Well, I downloaded and installed *gnome-sound-properies* package. When I first ran it, all setting were set on "Autodetect". I changed setting randomly, did "sudo reboot", and it played system sound on logon!!! BUT still NO sound in apps (players and games).

I ran *gnome-sound-properties* once again, and it looks now like that on picture (see attached). My Ubuntu is Russian, so I will translate a little here.

As you can see, the only difference between settings for "Sound Events" and "Music and Movies" is the word "&#1044;&#1088;&#1091;&#1075;&#1086;&#1081;" (means "Other one" in Russian). Now I suppose that if I could have same settings for "Music and Movies" as I have for "Sound Events", my troubles will go away. But when I open the drop-down menu in "Music and Movies" section, there is no such option as above in "Sound Events" section. There is only "OSS4 - AudigyLS 5.1 output", without the word "&#1044;&#1088;&#1091;&#1075;&#1086;&#1081;", as above (while the "Sound Events" section has BOTH options - with and without that word).

Moreover, when I press the "Test" button in "Sound Event", I can hear sound, but if I press the "Test" button in "Music and Movies", ther is no test sound, and the following appears in console:

```
kidd79@karmic:~$ gnome-sound-properties 
(gnome-sound-properties:3373): sound-properties-DEBUG: setting theme ubuntu
sound-properties-Message: Error running pipeline 'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music': &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100;/&#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1080;&#1090;&#1100; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1099; &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1072;. [oss4-audio.c(611): gst_oss4_audio_set_format (): /GstPipeline:pipeline0/GstGConfAudioSink:gconfaudiosink0/GstBin:bin0/GstOss4Sink:oss4sink1:
Format actually configured wasn't the one we requested. This is probably either a bug in the driver or in the format probing code.]

```The Russian part here says "Failed to get/define resources propertis" or something like this.

I tried other options in "Music and Movies" section. "ALSA" and "OSS4 - AudigyLS front" cause the "Test" button make sound (but still no sound in any app), while all other options (including "Autodetect") do nothing at all - no sound in apps, no test sound, no error messages in console.

Still trying further.

----------------------

UPDATE

Some packages like libcanberra and similar auto-updated right two minutes ago. Now If I set "OSS4 - AudigyLS front" in "Music and Movies", I have sound in Rhythmbox music player and all games listed abouve, while other music and video players (totem, gxine, audacious) remain silent. This is just ridiculous (I hope I spelled it correctly).

---

### Post by Yellow Pasque on 2010-03-09
Why do you have the mixer set to Pulseaudio? Why do you still have pulseaudio stuff on your system?

---

### Post by kidd79 on 2010-04-08
The problem is solved in some unusual way :-\

My motherboard malfunctioned, so I had to replace it, as well as cp. After that, I formatted the drive, re-installed and updated Ubuntu, and the sound was OK in all apps, so I decided to not try to install OSS again.

Thank you for your assistance very much again.

---

### Post by cbilljones on 2010-06-03
For future reference:
User most likely needed to run "gstreamer-properties" and set to oss, also some apps(like vlc) you will need to set OSS in its options.

---

