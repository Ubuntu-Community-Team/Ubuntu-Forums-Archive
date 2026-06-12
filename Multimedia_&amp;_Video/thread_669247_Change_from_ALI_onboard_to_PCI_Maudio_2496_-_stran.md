---
title: "Change from ALI onboard to PCI Maudio 2496 - strange effects!! Reconfigure ALSA?"
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by perixx on 2008-01-16
I've just switched off my onboard sound-chip (ALI) in favour of my old PCI-card Maudio Delta Audiophile 2496...

Now I've got the problem of certain games not working correctly (obviously OpenAL and SDL games), also the Alsa 'master control' isn't found (no faders in the audio mixer gui availible, only 'alsamixer' works). 
Strange effects occur: 
- UT2004 will produce really low-sampled + low-speed sounds like when turning vinyls at very low speeds (using OpenAL)!
- freedroidRPG won't have no sound at all (using SDL).
- Doom3 has good sound from what I can tell, but some Menu sounds are missing. 
- playing CD's/videos with Mplayer (using Alsa) is okay.
- I've got no mixer-faders availible in 'xfce4-mixer' and system-mixer (only 'alsamixer' is working)...

Steps I took trying to get the card working:
```
uninstalled ice1712 soundmodule with 'sudo modconf' + reinstalled it with:
sudo modprobe snd-ice1712
```

From what I can tell, there might still be the old (deactivated) ALI chip in use by the system - error-ouput of '.xsession-errors': 
> alsa: error: master control not found. I even tried to guess wildly, but to no avail.
alsa: info: developer information follows: (send E-Mail to Developer with that)
alsa: * IEC958,0
alsa: * IEC958 Multi,0
alsa: * IEC958 Multi,1
alsa: * IEC958,1
alsa: * ADC,0  <--- hint hint
alsa: * ADC,1  <--- hint hint
alsa: * DAC,0  <--- hint hint
alsa: * DAC,1  <--- hint hint
alsa: * Deemphasis,0
alsa: * H/W,0
alsa: * H/W,1
alsa: * H/W Multi,0
alsa: * H/W Multi,1
alsa: * Multi,0  <--- hint hint
alsa: * Multi,1  <--- hint hint
alsa: * Multi,2  <--- hint hint
alsa: * Multi,3  <--- hint hint
alsa: * Multi,4  <--- hint hint
alsa: * Multi,5  <--- hint hint
alsa: * Multi,6  <--- hint hint
alsa: * Multi,7  <--- hint hint
alsa: * Multi,8  <--- hint hint
alsa: * Multi,9  <--- hint hint
alsa: * Multi Track Internal Clock,0
alsa: * Multi Track Internal Clock Default,0
alsa: * Multi Track Peak,0  <--- hint hint
alsa: * Multi Track Rate Locking,0
alsa: * Multi Track Rate Reset,0
alsa: * Multi Track Volume Rate,0  <--- hint hint
alsa: info: end of developer information 

SDL-game-error:
> ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
SDL just reported a problem.
The error string from SDL_GetError was: No available audio device 
The error string from the SDL mixer subsystem was: No available audio device 

DOOM3-soundinitialization:
> ------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.13
opened Alsa PCM device default for playback
device buffer size: 5644 frames ( 22576 bytes )
allocated a mix buffer of 16384 bytes
.
.
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.13
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5644 frames ( 22576 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
missed 1 sound updates
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
------ OSS Sound Initialization ------
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, don't bother./dev/dsp - bit rate: 16, channels: 2, frequency: 44100
allocated a mix buffer of 16384 bytes
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe
--------------------------------------
missed 6 sound updates
Shutting down sound hardware
------ OSS Sound Shutdown ------
close sound device
--------------------------------
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.13
opened Alsa PCM device default for playback
device buffer size: 5644 frames ( 22576 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
missed 1 sound updates
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.13
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5644 frames ( 22576 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
missed 1 sound updates
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
.
.
----------------------------------------
sound: found efxs/delta1.efx
-----------------------------------
 38845 msec to load game/delta1
idRenderWorld::GenerateAllInteractions, msec = 46, staticAllocCount = 0.
interactionTable size: 7209552 bytes
43366 interaction take 4856992 bytes
------------- Warnings ---------------
during game/delta1...
WARNING: Couldn't load sound 'guisounds.wav' using default
WARNING: Non-portable: path contains uppercase characters: base/dds/makeIntensity/lights
WARNING: Non-portable: path contains uppercase characters: base/models/mapobjects/tables/Udesk
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
4 warnings
idAudioHardwareALSA::Write: 336 frames overflowed and dropped
.
.
idAudioHardwareALSA::Write: 336 frames overflowed and dropped
.
.
WARNING: Couldn't load sound 'guisounds.wav' using default
.
.
idAudioHardwareALSA::Write: 336 frames overflowed and dropped
idAudioHardwareALSA::Write: 336 frames overflowed and dropped
idAudioHardwareALSA::Write: 336 frames overflowed and dropped
idAudioHardwareALSA::Write: 336 frames overflowed and dropped
idAudioHardwareALSA::Write: 336 frames overflowed and dropped
--------- Game Map Shutdown ----------
--------------------------------------
idAudioHardwareALSA::Write: 336 frames overflowed and dropped
--------- Game Map Shutdown ----------
--------------------------------------
snd_pcm_writei 1276 frames failed: Broken pipe
missed 1 sound updates
idAudioHardwareALSA::Write: 1276 frames overflowed and dropped
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output

What can be done? Do I have to reconfigure Alsa somehow?

---

### Post by perixx on 2008-01-16
*bumpthis*

---

### Post by perixx on 2008-01-16
I was able to get back to my onboard-sound meanwhile (whew). Still, I couldn't get my (supposedly much better) PCI card working - it was playing nicely on Feisty in another mainboard before!

When both soundchips were enabled, none would've functioned, so the idea was to try them separately - but only the onboard chip would play. 

I wonder how I can get this going...

perixx

---

### Post by perixx on 2008-01-17
Nobody got an idea how to manually install the (already availible) alsa driver correctly? 
I've been following the 'comprehensive audio problem solving'-thread, but that didn't fix my problem...

perixx

---

### Post by mutecity on 2008-01-23
I bought an audiophile 2496 the other day and I am having similar problems with alsa. 

The only way i'm able to play music without any issues is through jack!

---

### Post by perixx on 2008-01-24
Thanks for the hint, mutecity!

I've been running Feisty on another mobo but with the same card some time ago, and I can't remember having such problems back then; I think that the old (onboard) sound drivers are still in the way / conflicting....

How do you enable Jack sound support?

perixx

---

### Post by mutecity on 2008-01-24
I'm pretty sure I installed the packages qjackctl and jackd. Its been a difficult one, lots of trial and error really.

---

### Post by perixx on 2008-01-25
Thank you, I'll eventually shall give it a try sometime....

perixx

---

### Post by Yellow Pasque on 2008-01-25
M-audio hired a company called 4front Tech (which developed the now deprecated OSS/Free) to write drivers for their cards. That company is now an open source project and has come out with a modern version of OSS, OSSv4. Try following the procedure in my sig. My M-Audio Revolution works much better with OSS4 than it did with ALSA 1.0.15 (and I don't see any changes for it in the latest release of ALSA). I have a feeling your Audiophile will behave similarly.

---

### Post by perixx on 2008-01-26
Hello, Temüjin!

Thank you for your help... unfortunately, things didn't went that good for me so far:

I tried to install the .deb file from oss' website the way you've described it. I got only error messages about an 'snd-sth-intel' driver still being in use and that files/folder under /usr/lib/oss... couldn't be opened/created....

Then I realized that I forgot to reboot after alsa-deinstallation and booting into safe console. So I did that and tried again - same result. 

Now, I'm stuck to that I even cannot remove the 'oss-linux' package anymore! Not in the safe console, not with apt-get or dpkg and not with Synaptic!! :confused:

Message-output under Synaptic, while trying to remove OSS, reads like this:> ...
sh: Can't Open Sound System
Starting Sound System
/usr/sbin/soundon: 27: cannot create /usr/lib/oss/logs/soundon.log
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 28 - 45: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent 
No /usr/lib/oss/etc/installed_drivers - cannot continue
Error while processing: oss-linux
^AE: Sub-process /urs/bin/dpkg returned an error code (1)
....
Sub-process pre-removal script returned the error code (2)

I got errors about OSS not being able to create folders during installation as well and tried to 'help' the installer by manually creating the folders/empty files, which resulted in getting a little further every time. A bogus victory in the end - it seems the installer simply cannot write to the filesystem!?
Maybe due to the wrong .deb architecture/sudo permission system? 

Anyway, I'd like to compile from source and try again, but HOW in the world, can I GET RID of the broken .deb package again??

Btw: the /usr/lib/oss folder isn't created during installation and I've done a rm -f to make sure it's deleted, after removing the package would fail. Now, I suppose, only the binary oss-files in /bin are left, in addition to the man pages. But the package is still listed in Synaptic and can't be removed and surely will cause trouble when trying to re-install oss from source or even with alsa, who knows...
 
perixx

---

### Post by Yellow Pasque on 2008-01-26
How to recover form a failed installation
[http://www.4front-tech.com/forum/viewtopic.php?t=2054](http://www.4front-tech.com/forum/viewtopic.php?t=2054)

---

### Post by perixx on 2008-01-27
Hello Temüjin.

In the meantime, I downloaded the .tar.bz2 archive and copied it's contents to the appropriate places by hand and did 'sudo soundon'. Everything seemed to work well and I also created a button for the Envy mixer GUI. Thing is, there's no sound-output. 

Then I read about your suggestion how to remove oss, but I was able to use Synaptic meanwhile, to remove the broken installation. The archive-files still remain on the system, 'soundon' is working and so is the mixer. But no sound...

perixx

---

### Post by seawright on 2008-01-28
Check all ossxmixer sliders are at maximum then run osstest.
Does osstest show any errors?
Do you hear any music playing during the tests from either loudspeakers or headphones.
If not (and this is a long shot) plug headphones into microphone socket, run osstest again and listen for music.

Regards,
Clive

---

### Post by perixx on 2008-01-28
Hy seawright!

As told, I manually fitted all files in place and oss-'soundon' is loaded and executed at bootup. When doing 'osstest', I'll have correct playback (though a little distorted due to high-volume clipping, as usual |¬P ) on oss-engine pcm0 and spdout 1.
While playing, the respective peak meters will display the volume level. I can even adjust it with the faders out1/2 and spdout1/2, with 'route' set to 'MON'. For 'DMA', only spdout is adjustable.

Currently, my ATI driver's accelleration is down, and I can't play videos or games other than 'freedroid' for sound testing - and it doesn't work. 

Doing a manual 'aplay somefile.wav' will return > ********************   WARNING   *******************************
Warning! aplay uses ALSA emulation instead of the native OSS API
****************************************************************
aplay: main:550: Fehler beim Öffnen des Audiogerätes: Invalid argument Maybe I'm getting this wrong, but perhaps  most apps / games just use alsa? I've read about some alsa2oss link... how could/should I set this up?
On the other hand, SMPlayer wouldn't give any sound, even when set to 'oss'. So I guess there must be sth. wrong with oss' applications-interface, or this interface is hooked by some other sound driver (maybe still the snd_intel driver?)... :confused: 
What could be wrong?

perixx

---

### Post by seawright on 2008-01-28
Ok so osstest works.
Try ossplay somefile.wav,
aplay won't work due to a problem with libsalsa.

If ossplay doesn't work run:

sudo soundoff
sudo ossdetect -V
sudo soundon

and try ossplay again.
While the file is being played, in another terminal:
cat /dev/sndstat
Note which Audio devices number is being opened OUT by ossplay. If not zero change "masterdev=0" in the sed command below to the correct number.
If it works now the problem is vmix. Run:

sudo soundoff
sudo ossdetect
sudo sed -i 's.#vmix1_masterdev=-1.vmix1_masterdev=0.' /usr/lib/oss/conf/vmix.conf
sudo soundon

ossplay should now work.
Most audio applications should be configurable to use oss.

Regards,
Clive

---

### Post by perixx on 2008-01-28
Here's the 'sndstat' output:
> cat /dev/sndstat
OSS 4.0 (b1012/200801022314)  (C) 4Front Technologies 1996-2007

**** UNREGISTERED VERSION ****

This OSS version will expire after:  Jul 2008

Audio devices:
0: M Audio Audiophile 2496 out1/2 (OUTPUT)
1: M Audio Audiophile 2496 S/PDIF out  (OUTPUT)
2: M Audio Audiophile 2496 in1/2 (INPUT)
3: (Undefined or removed device)
4: M Audio Audiophile 2496 input from mon. mixer  (INPUT)
5: M Audio Audiophile 2496 (all outputs) (OUTPUT)
6: M Audio Audiophile 2496 (all inputs) (INPUT)
7: High Definition Audio front (OUTPUT)
   Opened OUT by ossplay/8867 @ 22050/22050 Hz Fragment: 1024/88200 (11.6 msec)
   Song name: WhiteNoise.wav
8: High Definition Audio rear (OUTPUT)
9: High Definition Audio center/LFE (OUTPUT)
10: High Definition Audio spdif-out (OUTPUT)
11: High Definition Audio rec (INPUT)

Mixers:
0: M Audio Audiophile 2496
1: High Definition Audio AD1986A


WARNING! Legacy device numbering in /dev/sndstat is different from actual device numbering
I then entered all commands that you stated - still no workie..! I can hear a very soft crackling sound every time soundon is being started.

From what I can make out of this, the sound is being 'played' back on the onboard HD Audio sound chip (front). I want to have out1/2 respectively monitor-mixer out of the M-Audio card instead, though. But I cannot quite decipher what you mean by > If not zero change "masterdev=0" in the sed command below to the correct number. :?

Btw., what about those games/apps that don't have a choice to select OSS? Isn't there any kind of soundmapper from alsa to oss, or a possibility to have the sound re-mapped by the system automatically? 

perixx

---

### Post by perixx on 2008-01-29
FGLRX is BACK now!
Applications tried that use: OpenAL, SDL, Alsa, OSS -- none works!

perixx

---

### Post by perixx on 2008-01-30
Can you suggest something, seawright?

perixx

---

### Post by perixx on 2008-02-01
I've managed to return to Alsa savely, finally. 
```
sudo sh /usr/lib/oss/scripts/restore_drv.sh
sudo sh /usr/lib/oss/scripts/removeoss.sh
```
Perhaps you should add those commands to your 'recover from oss' section...

Thanks for your help,

perixx

---

### Post by Yellow Pasque on 2008-02-01
> **perixx said:**
> I've managed to return to Alsa savely, finally. 
```
sudo sh /usr/lib/oss/scripts/restore_drv.sh
sudo sh /usr/lib/oss/scripts/removeoss.sh
```
Perhaps you should add those commands to your 'recover from oss' section...

Thanks for your help,

perixx
Noted. Thank you.

---

### Post by seawright on 2008-02-02
Sorry for delay in replying and that oss did not work for you.
I am surprised as Maudio 2496 is well supported by oss but not having this card myself I am unable to reproduce the problems you were having.
Perhaps the presence of the hdaudio controller was causing a problem.

If you are not happy with Alsa and want to try oss again you could disable hdaudio in the bios setup before booting into Ubuntu or with the oss drivers installed.
Run:
sudo soundoff
Check that the command completes successfully.
Edit: /usr/lib/oss/etc/installed_drivers & remove the line starting with "hdaudio".
Save changes then run:
sudo soundon
cat /dev/sndstat
should then only show M Audio Audiophile 2496 (not  High Definition Audio) in the audio devices and mixers sections.

Kind regards,
Clive

---

### Post by perixx on 2008-02-02
Thank you for response, Clive!

In the long run, I guess I'll try OSS again - I'm convinced that my Audiophile 2496 is much better than my 'HD Audio' oboard chip from ADI, especially when it comes to A/D conversion.

I suppose, I'll give it another shot as soon as I make the switch to Hardy in a couple of weeks. I Just wonder, did you want me to use this command exactly as you stated, or is there something to change in it: ```
sudo sed -i 's.#vmix1_masterdev=-1.vmix1_masterdev=0.' /usr/lib/oss/conf/vmix.conf
``` 

I guess that a key to my problems is this message here (and similar ones): > WARNING! Legacy device numbering in /dev/sndstat is different from actual device numbering Somehow it seems that OSS is working and the apps are likewise - there's but a link missing inbetween...

perixx

---

### Post by seawright on 2008-02-02
Extract from your cat /dev/sndstat/> cat /dev/sndstat
OSS 4.0 (b1012/200801022314) (C) 4Front Technologies 1996-2007

**** UNREGISTERED VERSION ****

This OSS version will expire after: Jul 2008

Audio devices:
0: M Audio Audiophile 2496 out1/2 (OUTPUT)
1: M Audio Audiophile 2496 S/PDIF out (OUTPUT)
2: M Audio Audiophile 2496 in1/2 (INPUT)
3: (Undefined or removed device)
4: M Audio Audiophile 2496 input from mon. mixer (INPUT)
The "Undefined or removed device" is the probable reason for the "WARNING! "
Run:
sudo ossdevlinks
then try
cat /dev/sndstat
again
if "Undefined or removed device" still occurs run:
sudo ossdevlinks -r

```
sudo sed -i 's.#vmix1_masterdev=-1.vmix1_masterdev=0.' /usr/lib/oss/conf/vmix.conf
``` is correct command if output is:
0: M Audio Audiophile 2496 out1/2 (OUTPUT)
If desired output is S/PDIF
1: M Audio Audiophile 2496 S/PDIF out (OUTPUT)
command would be:
```
sudo sed -i 's.#vmix1_masterdev=-1.vmix1_masterdev=1.' /usr/lib/oss/conf/vmix.conf
```

Does that make it any clearer?

kind regards,
Clive

---

### Post by perixx on 2008-02-03
Hello Clive...

I'll try OSS again anytime soon, with the suggestions you've come up with.
> sudo sed -i 's.#vmix1_masterdev=-1.vmix1_masterdev=0.' /usr/lib/oss/conf/vmix.conf

is correct command if output is:
0: M Audio Audiophile 2496 out1/2 (OUTPUT) Well, then I was right when assuming it to be the correct command for my default output (analog RCA out connectors), so this wasn't the problem.

perixx

---

