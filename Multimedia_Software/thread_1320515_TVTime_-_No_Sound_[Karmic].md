---
title: "TVTime - No Sound [Karmic]"
date: 2009-11-09
forum: Multimedia Software
---

### Post by Uncle Spellbinder on 2009-11-09
I'm getting no sound from TVTime. Channels scanned properly, great picture quality but no sound at all. Did a forum search and 
found no answers. I have a Hauppauge video card working perfectly in Win 7 (dual-booting). All my other sound is fine in Karmic.

Anyone have any ideas?

---

### Post by megamania on 2009-11-09
> **Uncle Spellbinder said:**
> I'm getting no sound from TVTime. Channels scanned properly, great picture quality but no sound at all. Did a forum search and 
found no answers. I have a Hauppauge video card working perfectly in Win 7 (dual-booting). All my other sound is fine in Karmic.

Anyone have any ideas?
What card model do you have? Did sound work with 9.04?

---

### Post by Uncle Spellbinder on 2009-11-09
> **megamania said:**
> What card model do you have? Did sound work with 9.04?
TV tuner card is in my signature, no previous issues  with sound at all in Karmic. Worked in Jaunty. And this is a clean install of Karmic, not an upgrade.

---

### Post by testazio on 2009-11-09
Hi,
I have tha same problem.
TVTIME worked perfectly with 8.04LTS.
Now with karmic tvtime gets no sound at all, but the soud card with pulse audio is ok with all other applications.
here a piece of dmesg:
root@ubuntu-box:~# dmesg | grep bttv
[    9.284528] bttv: driver version 0.9.18 loaded
[    9.284533] bttv: using 8 buffers with 2080k (520 pages) each for capture
[    9.284578] bttv: Bt8xx card found (0).
[    9.284592] bttv 0000:00:0b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.284601] bttv0: Bt848 (rev 18) at 0000:00:0b.0, irq: 16, latency: 64, mmio: 0xf7f00000
[    9.286095] bttv0: using: MIRO PCTV pro [card=11,insmod option]
[    9.286100] IRQ 16/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.286130] bttv0: gpio: en=00000000, out=00000000 in=00ff33ff [init]
[    9.289901] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[    9.290464] bttv0: miro: id=12 tuner=5 radio=no stereo=no
[    9.290467] bttv0: tuner type=5
[    9.675813] bttv0: audio absent, no audio device found!
[   11.047979] bttv0: registered device video1
[   11.048017] bttv0: registered device vbi0
[ 6300.198719] bttv0: unloading
[ 6432.924650] bttv: driver version 0.9.18 loaded
[ 6432.924654] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 6432.924702] bttv: Bt8xx card found (0).
[ 6432.924715] bttv0: Bt848 (rev 18) at 0000:00:0b.0, irq: 16, latency: 64, mmio: 0xf7f00000
[ 6432.925841] bttv0: using: MIRO PCTV pro [card=11,insmod option]
[ 6432.925845] IRQ 16/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[ 6432.925875] bttv0: gpio: en=00000000, out=00000000 in=00ff33ff [init]
[ 6432.930449] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[ 6432.931013] bttv0: miro: id=12 tuner=5 radio=no stereo=no
[ 6432.931016] bttv0: tuner type=5
[ 6432.955726] bttv0: audio absent, no audio device found!
[ 6432.974090] bttv0: registered device video1
[ 6432.974117] bttv0: registered device vbi0
[ 6454.282220] bttv0: unloading
[ 6461.000792] bttv: driver version 0.9.18 loaded
[ 6461.000796] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 6461.000847] bttv: Bt8xx card found (0).
[ 6461.000859] bttv0: Bt848 (rev 18) at 0000:00:0b.0, irq: 16, latency: 64, mmio: 0xf7f00000
[ 6461.002166] bttv0: using: MIRO PCTV pro [card=11,insmod option]
[ 6461.002171] IRQ 16/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[ 6461.002202] bttv0: gpio: en=00000000, out=00000000 in=00ff33ff [init]
[ 6461.017582] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[ 6461.018148] bttv0: miro: id=12 tuner=5 radio=no stereo=no
[ 6461.018151] bttv0: tuner type=5
[ 6461.036914] bttv0: audio absent, no audio device found!
[ 6461.057984] bttv0: registered device video1
[ 6461.058011] bttv0: registered device vbi0
[ 6502.194177] bttv0: unloading
[ 6507.477309] bttv: driver version 0.9.18 loaded
[ 6507.477314] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 6507.477362] bttv: Bt8xx card found (0).
[ 6507.477375] bttv0: Bt848 (rev 18) at 0000:00:0b.0, irq: 16, latency: 64, mmio: 0xf7f00000
[ 6507.481450] bttv0: using: MIRO PCTV pro [card=11,insmod option]
[ 6507.481455] IRQ 16/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[ 6507.481487] bttv0: gpio: en=00000000, out=00000000 in=00ff33ff [init]
[ 6507.493622] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[ 6507.494188] bttv0: miro: id=12 tuner=5 radio=no stereo=no
[ 6507.494191] bttv0: tuner type=5
[ 6507.517130] bttv0: audio absent, no audio device found!
[ 6507.534213] bttv0: registered device video1
[ 6507.534237] bttv0: registered device vbi0

Note that is saying: [ 6507.517130] bttv0: audio absent, no audio device found!
What does it mean?
I tried all possible combination of alsamixer but no luck.
Thank you for the answers.

---

### Post by imaca on 2009-11-10
This might be a silly answer but have you got ALSAmixer installed and its master volume turned up?
In my system (old Athlon Nforce2 Mboard) all my sound outputs through SPDIF EXCEPT Tvtime. Tvtime comes out over analogue (this was the case in Hardy also) but now I have to turn up the ALSAmixer master volume after every reboot to hear it (it seems to be completely disconnected from the Pulse audio volume control)

---

### Post by Uncle Spellbinder on 2009-11-10
Master in alsamixer is always up for me. type in *alsamixer* in terminal and I get this, Master is always fine.:

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/alsamixer-1.png[/IMG]

Still, no sound at all in TVTime. 




Come to think of it, I don't even see a volime bar anymore with TVTime. 

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/TVTime.png[/IMG]

I don't think that's the issue though, as far too many people are having issues with TVTime and no sound.

---

### Post by Uncle Spellbinder on 2009-11-10
For those interested, or suffering the same issue, there is a bug filed at Launchpad: [**NO Audio in Tv Time using Ubuntu Karmic**](https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/472770?comments=all)

---

### Post by HoboJ on 2009-11-10
I'm curious, does your tuners' audio go out the back of your card and into your sound via a line in/mic port? Mine does and I had similar problems until I installed alsamixer and unmuted the mic port in the back.

---

### Post by Uncle Spellbinder on 2009-11-11
I have no idea how my tuner's audio works. It's the card listed in my signature, default config that has worked in Windows Vista and 7 as well as Ubuntu Intrepid and Jaunty. 

As far as Alsamixer, see image above. I also tried unmuting everything in that image. Still no sound.

:(

---

### Post by ricsi-pontaz on 2009-11-17
I have got the same thing here, no audio in TvTime.:(

---

### Post by xc3RnbFO8P on 2009-11-17
Read this:
[http://ubuntuforums.org/showthread.php?t=1319646]("http://ubuntuforums.org/showthread.php?t=1319646")

---

### Post by ricsi-pontaz on 2009-11-17
> **Ringi said:**
> Read this:
[http://ubuntuforums.org/showthread.php?t=1319646]("http://ubuntuforums.org/showthread.php?t=1319646")

It didn't work for me. :(

---

### Post by Uncle Spellbinder on 2009-11-17
Checked that thread. Still no help. No "AUX" to uncheck and that terminal input was of no help.


This is getting so annoying. All was fine in clean installs of Intrepid and Jaunty. All of a sudden, Karmic and TVTime seem not work together at all.

---

### Post by xc3RnbFO8P on 2009-11-17
Try this:
> arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
<return>
exit
<return>
To turn it off  you have to Log Out or Restart the computer.

---

### Post by Uncle Spellbinder on 2009-11-17
> **Ringi said:**
> Try this:



Did 
```
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
<return>
```

Hitting return (enter) and terminal closed. Tried TV Time, still no sound. It then froze and went to blue screen. Became extremely slow. Restarted CPU, back to normal (no sound).

Appreciate the help though. For now, I think I'll just keep an eye on this thread and the [bug filed at Launchpad](https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/472770?comments=all).

Quite frustrating.

---

### Post by Uncle Spellbinder on 2009-11-17
Ohhhh.  


You meant in terminal with TVTime on. 

I just tried that and got the following...

```
$ arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
[1] 2259
$ ALSA lib pcm_hw.c:1433:(_snd_pcm_hw_open) Invalid value for card
arecord: main:608: audio open error: No such file or directory
The program 'play' is currently not installed.  You can install it by typing:
sudo apt-get install sox
play: command not found

```

---

### Post by xc3RnbFO8P on 2009-11-17
> **Uncle Spellbinder said:**
> Ohhhh.  


You meant in terminal with TVTime on. 

I just tried that and got the following...

```
$ arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
[1] 2259
$ ALSA lib pcm_hw.c:1433:(_snd_pcm_hw_open) Invalid value for card
arecord: main:608: audio open error: No such file or directory
The program 'play' is currently not installed.  You can install it by typing:
sudo apt-get install sox
play: command not found

```

Yes I forgot this sox thing
> sudo apt-get install sox
Then try this:
> tvtime -M | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -Dplug:surround51

---

### Post by Uncle Spellbinder on 2009-11-17
Damn. Still no sound. I now get this...

```
wombat@Wombat:~$ arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav - &
[1] 2211
wombat@Wombat:~$ ALSA lib pcm_hw.c:1433:(_snd_pcm_hw_open) Invalid value for card
arecord: main:608: audio open error: No such file or directory
play: invalid option -- w
play: SoX v14.3.0

play FAIL sox: invalid option

Usage summary: [gopts] [[fopts] infile]... [fopts] [effect [effopts]]...

SPECIAL FILENAMES (infile, outfile):
-                        Pipe/redirect input/output (stdin/stdout); may need -t
-d, --default-device     Use the default audio device (where available)
-n, --null               Use the `null' file handler; e.g. with synth effect
-p, --sox-pipe           Alias for `-t sox -'

SPECIAL FILENAMES (infile only):
"|program [options] ..." Pipe input from external program (where supported)
http://server/file       Use the given URL as input file (where supported)

GLOBAL OPTIONS (gopts) (can be specified at any point before the first effect):
--buffer BYTES           Set the size of all processing buffers (default 8192)
--clobber                Don't prompt to overwrite output file (default)
--combine concatenate    Concatenate multiple input files (default for sox, rec)
--combine sequence       Sequence multiple input files (default for play)
-D, --no-dither          Don't dither automatically
--effects-file FILENAME  File containing effects and options
-G, --guard              Use temporary files to guard against clipping
-h, --help               Display version number and usage information
--help-effect NAME       Show usage of effect NAME, or NAME=all for all
--help-format NAME       Show info on format NAME, or NAME=all for all
--i, --info              Behave as soxi(1)
--input-buffer BYTES     Override the input buffer size (default: as --buffer)
--no-clobber             Prompt to overwrite output file
-m, --combine mix        Mix multiple input files (instead of concatenating)
-M, --combine merge      Merge multiple input files (instead of concatenating)
--magic                  Use `magic' file-type detection
--norm                   Guard (see --guard) & normalise
--play-rate-arg ARG      Default `rate' argument for auto-resample with `play'
--plot gnuplot|octave    Generate script to plot response of filter effect
-q, --no-show-progress   Run in quiet mode; opposite of -S
--replay-gain track|album|off  Default: off (sox, rec), track (play)
-R                       Use default random numbers (same on each run of SoX)
-S, --show-progress      Display progress while processing audio data
--single-threaded        Disable parallel effects channels processing
--temp DIRECTORY         Specify the directory to use for temporary files
--version                Display version number of SoX and exit
-V[LEVEL]                Increment or set verbosity level (default 2); levels:
                           1: failure messages
                           2: warnings
                           3: details of processing
                           4-6: increasing levels of debug messages
FORMAT OPTIONS (fopts):
Input file format options need only be supplied for files that are headerless.
Output files will have the same format as the input file where possible and not
overriden by any of various means including providing output format options.

-v|--volume FACTOR       Input file volume adjustment factor (real number)
--ignore-length          Ignore input file length given in header; read to EOF
-t|--type FILETYPE       File type of audio
-s/-u/-f/-U/-A/-i/-a/-g  Encoding type=signed-integer/unsigned-integer/floating-
                         point/mu-law/a-law/ima-adpcm/ms-adpcm/gsm-full-rate
-e|--encoding ENCODING   Set encoding (ENCODING in above list)
-b|--bits BITS           Encoded sample size in bits
-1/-2/-3/-4/-8           Encoded sample size in bytes
-N|--reverse-nibbles     Encoded nibble-order
-X|--reverse-bits        Encoded bit-order
--endian little|big|swap Encoded byte-order; swap means opposite to default
-L/-B/-x                 Short options for the above
-c|--channels CHANNELS   Number of channels of audio data; e.g. 2 = stereo
-r|--rate RATE           Sample rate of audio
-C|--compression FACTOR  Compression factor for output format
--add-comment TEXT       Append output file comment
--comment TEXT           Specify comment text for the output file
--comment-file FILENAME  File containing comment text for the output file
--no-glob                Don't `glob' wildcard match the following filename

AUDIO FILE FORMATS: 8svx aif aifc aiff aiffc al amb au avr caf cdda cdr cvs cvsd cvu dat dvms f32 f4 f64 f8 fap flac fssd gsm hcom htk ima ircam la lpc lpc10 lu mat mat4 mat5 maud nist ogg paf prc pvf raw s1 s16 s2 s24 s3 s32 s4 s8 sb sd2 sds sf sl smp snd sndfile sndr sndt sou sox sph sw txw u1 u16 u2 u24 u3 u32 u4 u8 ub ul uw vms voc vorbis vox w64 wav wavpcm wv wve xa xi
PLAYLIST FORMATS: m3u pls
AUDIO DEVICE DRIVERS: alsa

EFFECTS: allpass band bandpass bandreject bass bend biquad chorus channels compand contrast crop+ dcshift deemph delay dither divide+ earwax echo echos equalizer fade filter* fir firfit+ flanger gain highpass input# key* ladspa loudness lowpass mcompand mixer noiseprof noisered norm oops output# overdrive pad pan* phaser pitch polyphase* rabbit* rate remix repeat resample* reverb reverse riaa silence sinc spectrogram speed splice stat stats stretch swap synth tempo treble tremolo trim vad vol
  * Deprecated effect    + Experimental effect    # LibSoX-only effect
EFFECT OPTIONS (effopts): effect dependent; see --help-effect

```


Also, for **tvtime -M | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -Dplug:surround51 **...

```
wombat@Wombat:~$ tvtime -M | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -Dplug:surround51 
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/wombat/.tvtime/tvtime.xml
ALSA lib pcm_hw.c:1433:(_snd_pcm_hw_open) Invalid value for card
arecord: main:608: audio open error: No such file or directory
aplay: playback:2297: read error
Thank you for using tvtime.

```

---

### Post by xc3RnbFO8P on 2009-11-17
See is this helps:
[http://ubuntuforums.org/showthread.php?t=1284056]("http://ubuntuforums.org/showthread.php?t=1284056")
> Ok update, i was able to get to get audio working with tvtime and wintv 950q using jack via the qjackctl. All i did was go into the setup and set the wintv's audio input hw:1,0 and leave output as default. I started jack and connected the system input to outputs.
Or you try to  change **hw:1,0** to
hw:1,1 hw:1,2

---

### Post by Uncle Spellbinder on 2009-11-17
I have no idea what jack and/or qjackctl are. No clue how to "go into the setup and set the wintv's audio input hw:1,0 and leave output as default." No idea what "started jack and connected the system input to outputs" even means.

Seems complicated to get something to work that has worked without issue in the 2 previous versions of Ubuntu. 

While I truly appreciate your help. This may be out of my league to achieve. 

Off to work now, I have this thread and the Launchpad bug bookmarked.

Again, thanks for your help.

---

### Post by petsam on 2009-11-17
I' m having the same problem with PCTV Rave PCI.
No sound, no Aux control in alsamixer, no app running in Sound Settings.
I have a cable for the card sound output going to Line in of the onboard sound card and tried also the Mic in, but still nothing.
I believe it is a bug as it is stated already.
Hope it is solved soon!

---

### Post by Elv13 on 2009-11-18
I have similar problem with my saa7130 card. I have audio out wired into my sound card line in. Sox worked in the past, but now say that "-w" does not exist as many pointed earlier.  

I also get that:

lepagee@lepagee-mediaserver:~$ arecord -D hw:0,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000  -t wav 
play: SoX v14.3.0

play FAIL sox: missing filename




To get the sound, I can unmute the channel in alsamixer, but it is of no use to me as I can't record or use any advanced tv program because buffering cause massive audio delay. I am looking for a solution, I will post one if I find one.

---

### Post by jamesm113 on 2009-11-19
Mine only works if i do:
tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -

I have a wintv-950q

---

### Post by Elv13 on 2009-11-19
Well, downgrading to ubuntu 8.10 (intrepid) sox version helped, I now enjoy MythTV!

---

### Post by Uncle Spellbinder on 2009-11-20
Well, after installing Jaunty and Intrepid and trying TVTime on these versions, I can only come to the conclusion that either Karmic breaks TVTime or TVTime breaks Karmic. In any event, it works in the 2 previous Ubuntu versions on this computer. So something has drastically changed to cause this mess.

---

### Post by ububaba on 2009-11-20
I'm not trying to bump. My Koala has been behaving alright. However, from yesterday every time
I start anything on Youtube, BBC News etc it starts perfectly but after a second the sound disappears
without a trace. 

As I said I have had no problems of this nature earlier. I can play CD's, music files etc which are
already on the machine. The performance is perfect. 

Any clue?

---

### Post by Uncle Spellbinder on 2009-11-21
> **ububaba said:**
> ...Any clue?

Your issue has NOTHING to do with the topic of this thread, Nothing at all.

---

### Post by testazio on 2009-11-21
Hi guys,
same problem, here my dmesg.

[    9.762856] bttv0: audio absent, no audio device found!

No audio with tvtime on 9.10.
It worked delightful on 8.04.

Any news?


root@ubuntu-box:/home/ignazio/src# dmesg | grep bttv
[    9.671372] bttv: driver version 0.9.18 loaded
[    9.671376] bttv: using 8 buffers with 2080k (520 pages) each for capture
[    9.671422] bttv: Bt8xx card found (0).
[    9.671436] bttv 0000:00:0b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.671446] bttv0: Bt848 (rev 18) at 0000:00:0b.0, irq: 16, latency: 64, mmio: 0xf7f00000
[    9.671486] bttv0: using: MIRO PCTV pro [card=11,insmod option]
[    9.671489] IRQ 16/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.671518] bttv0: gpio: en=00000000, out=00000000 in=00ff33ff [init]
[    9.675415] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[    9.675978] bttv0: miro: id=12 tuner=5 radio=no stereo=no
[    9.675981] bttv0: tuner type=5
[    9.762856] bttv0: audio absent, no audio device found!
[    9.963973] bttv0: registered device video1
[    9.963996] bttv0: registered device vbi0

---

### Post by Uncle Spellbinder on 2009-11-21
> **testazio said:**
> ...Any news?...

Well, there is a bug filed. I'm keeping an eye on it in the hopes of a fix soon.

[https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/472770](https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/472770)

---

### Post by jamesm113 on 2009-11-23
Per the latest comments on the bug report,

add this line to /etc/pulse/default.pa :
load-module module-loopback

---

### Post by Uncle Spellbinder on 2009-11-23
Tried *pactl load-module module-loopback* in terminal. Didn't work. Added *pactl load-module module-loopback* to /etc/pulse/default.pa, didn't work. Then tried *load-module module-loopback*. Still nothing.

---

### Post by adymitruk on 2009-11-24
I've have this problem as well. But what makes it more interesting is that I had the same WinTV (10 yr old hauppauge) working on Ubuntu 9.10 on 7 yr old MB, RAM, HD, snd-card, etc.

Then the motherboard got zapped. I get new hardware and now I don't get sound in TVTime or mythtv. Both worked just fine on the old hardware.

New hardware has network, sound, display, usb on the MB. The only card I have is the PCI wintv. There is sound that comes out of the jack on the back of the card, but I didn't need to pass this into the soundcard input before, why should I now?

in dmesg I get the same thing the others get: no audio found for the wintv card in the bttv0 entries.

Any help is appreciated. I'm going to try to down grade the kernal until it works or this is solved.

---

### Post by petsam on 2009-11-26
OK. If it' s true that tvtime will most probably work fine with a previous release, should I do that and witch release is more certain to work fine with TV?

---

### Post by Uncle Spellbinder on 2009-11-26
> **petsam said:**
> OK. If it' s true that tvtime will most probably work fine with a previous release, should I do that and witch release is more certain to work fine with TV?
Jaunty and Intrepid worked fine for me on three different computers. Those same computers cannot run TVTime on Karmic. Seriously considering reverting to Jaunty myself. Or 6.06 LTS Dapper Drake, which also had no issues.

---

### Post by 1i1g on 2009-12-02
I just installed an HVR1100 and had no sound in tvtime. Then I found the solution with aplay and arecord below which resulted in choppy sound followed by no sound a couple of seconds later leaving only video.
Combined with the loopback module like this
```
pactl load-module module-loopback
```followed by
```
tvtime | arecord -D hw:1,0 -f S16_LE -c2 -r32000 | aplay -
```worked for me.
Now I have full sound and video with my HVR 1100 in karmic.

---

### Post by Uncle Spellbinder on 2009-12-02
> **1i1g said:**
> I just installed an HVR1100 and had no sound in tvtime. Then I found the solution with aplay and arecord below which resulted in choppy sound followed by no sound a couple of seconds later leaving only video.
Combined with the loopback module like this
```
pactl load-module module-loopback
```followed by
```
tvtime | arecord -D hw:1,0 -f S16_LE -c2 -r32000 | aplay -
```worked for me.
Now I have full sound and video with my HVR 1100 in karmic.

Still no luck here. Following above, I get...

```
wombat@Wombat:~$ pactl load-module module-loopback
19
wombat@Wombat:~$ tvtime | arecord -D hw:1,0 -f S16_LE -c2 -r32000 | aplay -
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/wombat/.tvtime/tvtime.xml
ALSA lib pcm_hw.c:1433:(_snd_pcm_hw_open) Invalid value for card
arecord: main:608: audio open error: No such file or directory
```

---

### Post by 1i1g on 2009-12-03
I also get that error if I set hw incorrectly.
Try
```
alsamixer -c #
```where # is an integer from 0...7 and find out which number is your TV card and which is your sound card.
Then use those numbers in
```
tvtime | arecord -D **hw:1,0** -f S16_LE -c2 -r32000 | aplay -
```

hth

---

### Post by Fitch on 2009-12-04
With a PCTV Rave PCI card, karmic installed, all I have ever been able to get is continual hiss.
Did the pactl load-module module-loopback etc.  it hissed at me.

Using alsamixer -c 0  the mixer controls come up, stating it's a Realtec ALC65 Rev 1.
With tvtime | arecord -D hw:1,0 -f S16_LE  -c 0 -r 32000 | aplay -
I get hiss.

I have tried PAL I (the correct one), PAL B-G, etc,: hiss.

Grepping bttv gives:

[   25.562830] bttv0: Bt878 (rev 17) at 0000:04:08.0, irq: 17, latency: 16, mmio: 0xfdaff000
[   25.563044] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[   25.563048] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,autodetected]
[   25.563051] IRQ 17/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   25.563103] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   25.568149] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   25.568766] bttv0: pinnacle/mt: id=1 info="PAL / mono" radio=no
[   25.568769] bttv0: tuner type=33
**[   25.981208] bttv0: audio absent, no audio device found!**
[   27.375933] bttv0: registered device video0
[   27.375960] bttv0: registered device vbi0
[   27.375981] bttv0: PLL: 28636363 => 35468950 .. ok
[39935.535900] bttv0: unloading

But if I don't have an audio device, why am I getting hiss? (and what are my speakers plugged into?)

---

### Post by yvanovitch on 2009-12-20
I've just run alsamixer , turned all gains at 100%... worked for me.

---

### Post by Fitch on 2009-12-21
Did that, now the hiss is even louder, needless to say, no actual TV audio.

---

### Post by Fitch on 2009-12-21
I did see an old thread relating to Mandrake which suggested adding "options tda9887 pal=i" in /etc/modprobe.d/bttv.conf. 
This led to "unrecognised pal" and "unable to tune" errors in dmesg.  But the speakers were wonderfully silent (I was getting fed up with the hiss), so the problem's definitely around there.


Previously, when I did the pactl stuff and put that line into /etc/pulse/default.pa I lost the loudspeaker icon on the top bar and the speakers gave four rapid clicks, pause, 4 rapid clicks, pause, ad infinitum.
The "pactl load-module module-loopback" gave an anwser back of "19" when I had the line in, and "17" when I didn't.

What does that all mean?

---

### Post by Fitch on 2009-12-22
Anyway, Alsa is now 1.0.22 and it still hisses.

How can I tell the computer I have a TDA9887 for a tuner? as this is the heart of the problem

---

### Post by sgwebb on 2009-12-27
The code suggested earlier in the thread resolved the issue for me


shane@ubuntu:~$ pactl load-module module-loopback
20
shane@ubuntu:~$ tvtime | arecord -D hw:1,0 -f S16_LE -c2 -r32000 | aplay -
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/shane/.tvtime/tvtime.xml
Recording WAVE 'stdin' : Signed 16 bit Little Endian, Rate 32000 Hz, Stereo
Warning: rate is not accurate (requested = 32000Hz, got = 48000Hz)
         please, try the plug plugin 
Playing WAVE 'stdin' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo

---

### Post by sgwebb on 2009-12-27
I have noticed if I close the terminal window where I have ran the commands, to get the sound, the sound goes away.. is there a way to run these when tvtime starts?, or add it to a config file?

```
$ pactl load-module module-loopback

```
and 

```
tvtime | arecord -D hw:1,0 -f S16_LE -c2 -r32000 | aplay -
```

---

### Post by Uncle Spellbinder on 2009-12-27
Still not working for me. When Trying
```
pactl load-module module-loopback
tvtime | arecord -D hw:1,0 -f S16_LE -c2 -r32000 | aplay -
```

I get the following...
```
wombat@Wombat:~$ pactl load-module module-loopback
20
wombat@Wombat:~$ tvtime | arecord -D hw:1,0 -f S16_LE -c2 -r32000 | aplay -
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/wombat/.tvtime/tvtime.xml
ALSA lib pcm_hw.c:1433:(_snd_pcm_hw_open) Invalid value for card
arecord: main:608: audio open error: No such file or directory
aplay: playback:2297: read error
```


NTSC TV tuner, over-the-air ATSC high-definition Digital TV tuner, and FM tuner
[Hauppauge WinTV HVR-1800 (Model 78xxx, Combo ATSC/QAM)]

---

### Post by Fitch on 2009-12-27
Same here!
brafferton@Office:~$ pactl load-module module-loopback
20
brafferton@Office:~$ tvtime | arecord -D hw:1,0 -f S16_LE -c2 -r32000 | aplay -
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
aplay: main:608: Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/brafferton/.tvtime/tvtime.xml
Recording WAVE 'stdin' : Signed 16 bit Little Endian, Rate 32000 Hz, Stereo
audio open error: Device or resource busy
arecord: pcm_read:1629: read error: Input/output error

PAL PCTV Rave
Oh! and it still hisses like mad.  It's the tuner...

---

### Post by Uncle Spellbinder on 2009-12-30
Anyone with this issue having any luck? Still nothing working for me.

---

### Post by madjinji on 2010-01-06
when I use 

dmesg | grep bttv

these the output for it ....

[   13.618490] bttv: driver version 0.9.18 loaded
[   13.618497] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   13.618583] bttv: Bt8xx card found (0).
[   13.618627] bttv 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.618642] bttv0: Bt878 (rev 17) at 0000:00:07.0, irq: 19, latency: 32, mmio: 0xe7001000
[   13.621114] bttv0: using: Prolink Pixelview PV-BT878P+ (Rev.4C,8E) [card=70,insmod option]
[   13.621121] bttv0: gpio config override: mask=0x3f, mux=0x21,0x20,0x23,0x23
[   13.621130] IRQ 19/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   13.621205] bttv0: gpio: en=00000000, out=00000000 in=00ffc0ff [init]
[   13.624514] bttv0: tuner type=38
**[   14.045027] bttv0: audio absent, no audio device found!**
[   14.350989] bttv0: registered device video0
[   14.351050] bttv0: registered device vbi0
[   14.351104] bttv0: registered device radio0
[   14.351125] bttv0: PLL: 28636363 => 35468950 .. ok
[   14.380812] input: bttv IR (card=70) as /devices/pci0000:00/0000:00:07.0/input/input5
[  310.272223] bttv0: PLL can sleep, using XTAL (28636363).
[  446.244355] bttv0: PLL: 28636363 => 35468950 .. ok

but when  I add **options bttv card=70 tuner=38 radio=1 gpiomask=0x3F audiomux=33,32,35,35,40** to** /etc/modprobe.d/bttv** the the sound work just fine it's still give the message **[   14.045027] bttv0: audio absent, no audio device found! **but what ever its working now

---

### Post by Fitch on 2010-01-07
Don't worry about the "audio absent, no audio device found" 'cos that card doesn't have "audio".  It's shipped with a little cable to go to your audio card, or on the card itself, there is a CD connector.  Since yours works, you must have one of them plugged in correctly.

Anyway,  this message is mainly for Uncle Spellbinder, who I'm hoping is an old b*gg*r - or at least an experienced one ( - in Linux that is ;) ), but anyone who knows a little bit about bash scripting please feel free to read on....

I trawled the web far and wide and found a script or 3 for cycling through the tuners one by one using xawtv.

Of course, it doesn't work as Linux has changed since this baby was born.... but it's close!

The original script was done by Yves Glodt in 2001, so I've added the newer cards and tuners to the script, but that's as far as it goes. (I've e-mailed him, but I don't know if his addy still exists yet)

I've got the errors down to just a couple now, pity one is still fatal, but there you go!

Who would like to have a try at this:

Anybody interested in looking at it, and if so, what's the best way to do it? I don't have a blog or anything like that and my web site actually belongs to the guest house I own, so I'd better not use that....

---

### Post by Blaspheme on 2010-01-10
> **jamesm113 said:**
> Mine only works if i do:
tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -

I have a wintv-950q

ON **Karmic Koala**,

This  worked for my saa7134, and mute 'Front Mic' to avoid interference.

:glee:

Volume level managed through: Sound Preferences>Input  [use the *Output Volume* bar on top, let me know if you find a shortcut to handle this job]

Tag, you're IT! :popcorn:

---

### Post by Fitch on 2010-01-10
I see there are no takers oh well. pity.

The script gives an error of:
WARNING: No DGA direct video mode for this display.
WARNING: couldn't find framebuffer base address, try manual  configuration ("v4l-conf -a <addr>")
v4l2: WARNING: framebuffer base address mismatch
v4l2: me=(nil) v4l=(nil)
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct

which is a shame, but I reckon all it is, is a syntax problem with the new kernel.

Yves Glodt did get back to me, but since it is 9 years since he did it, I think he's out of the loop now.

A lot of threads mentioned "pal=i" which, looking at other threads is now pll=? where ? is a number from 0 to whatever.

---

### Post by Fitch on 2010-01-10
Just a quick question to confuse things..
I know I/we use card=39 tuner=33, Well, tuner=33 is the MT2050
Looking at /lib/modules/2.6.31-17-generic/kernel/drivers, there is a ko file for MT20xx, but there's also a file for the TDA9887.  Is that the card=39 bit?

In dmesg it clearly states:
 39.591319] bttv0: tuner type=33
[   39.603861] bttv0: audio absent, no audio device found!
[   39.610907] tuner 2-0043: chip found @ 0x86 (bt878 #0 [sw])
[   39.610996] tda9887 2-0043: creating new instance
[   39.610998] tda9887 2-0043: tda988[5/6/7] found
[   39.616601] Chip ID is not zero. It is not a TEA5767
[   39.616690] tuner 2-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   39.619775] mt20xx 2-0060: microtune: companycode=3cbf part=42 rev=22
[   39.621182] mt20xx 2-0060: microtune MT2050 found, OK

---

### Post by DeMartini on 2010-01-13
> **1i1g said:**
> I just installed an HVR1100 and had no sound in tvtime. Then I found the solution with aplay and arecord below which resulted in choppy sound followed by no sound a couple of seconds later leaving only video.
Combined with the loopback module like this
```
pactl load-module module-loopback
```followed by
```
tvtime | arecord -D hw:1,0 -f S16_LE -c2 -r32000 | aplay -
```worked for me.
Now I have full sound and video with my HVR 1100 in karmic.
This just worked for me thanks, all I needed was the first line of code, running Karmic W/ Hauppauge 9500 usb wintv-hvr, however the left/right arrow for default volume control still doesn't work, I have use my laptop volume control, I can live w/ that....thanks again!

---

### Post by alekkova on 2010-01-13
#!/bin/bash
sudo su &                                                                        # -- Use admin writes
your_password                                                                    # -- Enter password
sox -q -c 2 -s -2 -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -2 -r 32000 /dev/dsp &  # -- Start sox process
/usr/bin/kdetv                                                                   # -- Start KDETV
                                                                                 # -- If stop KDETV
p=$( ps -ef | grep "[s]ox.*3200" | awk '{ print $2 }' )                          # -- Search sox process
kill -9 ${p} || ferror "Command kill -9 ${p}";                                   # -- Kill sox process
[ ${?} -eq 0 ] || ferror "echo Error COMMAND : stop sox"                         # -- Exit display on error

---

### Post by Fitch on 2010-01-14
I've tried a lot in the last few weeks, and now seem to have gotten a bit confused, and ended up with an overcrowded dmesg.

My bttv.conf now looks like:

# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv card=39 tuner=33 radio=0 pll=11 adc_crush=0
options tda9887 debug=2
options BROOKTREE_SYSTEM_DEFAULT=BROOKTREE_PAL

This gives: (amongst other things)
[ 1169.131033] tda9887 2-0043: configure for: PAL-BGHN
[ 1169.131045] tda9887 2-0043: writing: b=0xd0 c=0x70 e=0x49
[ 1169.131051] tda9887 2-0043: write: byte B 0xd0
[ 1169.131056] tda9887 2-0043:   B0   video mode      : sound trap
[ 1169.131061] tda9887 2-0043:   B1   auto mute fm    : no
[ 1169.131066] tda9887 2-0043:   B2   carrier mode    : Intercarrier
[ 1169.131071] tda9887 2-0043:   B3-4 tv sound/radio  : FM/TV
[ 1169.131076] tda9887 2-0043:   B5   force mute audio: no
[ 1169.131081] tda9887 2-0043:   B6   output port 1   : high (inactive)
[ 1169.131086] tda9887 2-0043:   B7   output port 2   : high (inactive)
[ 1169.131091] tda9887 2-0043: write: byte C 0x70
[ 1169.131096] tda9887 2-0043:   C0-4 top adjustment  : 0 dB
[ 1169.131101] tda9887 2-0043:   C5-6 de-emphasis     : 50
[ 1169.131106] tda9887 2-0043:   C7   audio gain      : 0
[ 1169.131110] tda9887 2-0043: write: byte E 0x49
[ 1169.131115] tda9887 2-0043:   E0-1 sound carrier   : 5.5 MHz
[ 1169.131120] tda9887 2-0043:   E6   l pll gating   : 36
[ 1169.131125] tda9887 2-0043:   E2-4 video if        : 38.9 MHz
[ 1169.131129] tda9887 2-0043:   E5   tuner gain      : normal
[ 1169.131134] tda9887 2-0043:   E7   vif agc output  : pin3+pin22 port
[ 1169.131139] tda9887 2-0043: --
[ 1169.133917] tda9887 2-0043: configure for: PAL-BGHN
[ 1169.133923] tda9887 2-0043: writing: b=0xd0 c=0x70 e=0x49
[ 1169.133928] tda9887 2-0043: write: byte B 0xd0
[ 1169.133933] tda9887 2-0043:   B0   video mode      : sound trap
[ 1169.133938] tda9887 2-0043:   B1   auto mute fm    : no
[ 1169.133942] tda9887 2-0043:   B2   carrier mode    : Intercarrier
[ 1169.133947] tda9887 2-0043:   B3-4 tv sound/radio  : FM/TV
[ 1169.133952] tda9887 2-0043:   B5   force mute audio: no
[ 1169.133957] tda9887 2-0043:   B6   output port 1   : high (inactive)
[ 1169.133962] tda9887 2-0043:   B7   output port 2   : high (inactive)
[ 1169.133967] tda9887 2-0043: write: byte C 0x70
[ 1169.133972] tda9887 2-0043:   C0-4 top adjustment  : 0 dB
[ 1169.133977] tda9887 2-0043:   C5-6 de-emphasis     : 50
[ 1169.133982] tda9887 2-0043:   C7   audio gain      : 0
[ 1169.133986] tda9887 2-0043: write: byte E 0x49
[ 1169.133991] tda9887 2-0043:   E0-1 sound carrier   : 5.5 MHz
[ 1169.133996] tda9887 2-0043:   E6   l pll gating   : 36
[ 1169.134001] tda9887 2-0043:   E2-4 video if        : 38.9 MHz
[ 1169.134006] tda9887 2-0043:   E5   tuner gain      : normal
[ 1169.134010] tda9887 2-0043:   E7   vif agc output  : pin3+pin22 port
[ 1169.134015] tda9887 2-0043: --
[ 1169.136021] tda9887 2-0043: configure for: PAL-BGHN
[ 1169.136027] tda9887 2-0043: writing: b=0xd0 c=0x70 e=0x49
[ 1169.136032] tda9887 2-0043: write: byte B 0xd0
[ 1169.136037] tda9887 2-0043:   B0   video mode      : sound trap
[ 1169.136042] tda9887 2-0043:   B1   auto mute fm    : no
[ 1169.136047] tda9887 2-0043:   B2   carrier mode    : Intercarrier
[ 1169.136052] tda9887 2-0043:   B3-4 tv sound/radio  : FM/TV
[ 1169.136056] tda9887 2-0043:   B5   force mute audio: no
[ 1169.136061] tda9887 2-0043:   B6   output port 1   : high (inactive)
[ 1169.136067] tda9887 2-0043:   B7   output port 2   : high (inactive)
[ 1169.136072] tda9887 2-0043: write: byte C 0x70
[ 1169.136076] tda9887 2-0043:   C0-4 top adjustment  : 0 dB
[ 1169.136081] tda9887 2-0043:   C5-6 de-emphasis     : 50
[ 1169.136086] tda9887 2-0043:   C7   audio gain      : 0
[ 1169.136091] tda9887 2-0043: write: byte E 0x49
[ 1169.136095] tda9887 2-0043:   E0-1 sound carrier   : 5.5 MHz
[ 1169.136100] tda9887 2-0043:   E6   l pll gating   : 36
[ 1169.136105] tda9887 2-0043:   E2-4 video if        : 38.9 MHz
[ 1169.136110] tda9887 2-0043:   E5   tuner gain      : normal
[ 1169.136115] tda9887 2-0043:   E7   vif agc output  : pin3+pin22 port
[ 1169.136119] tda9887 2-0043: --

A bit much.
Nowhere does it mention PAL I
Anyone know how I can clean it up a bit?

---

### Post by Fitch on 2010-01-18
BTW:  PAL I sound carrier is 6.0MHz
so the 5.5MHz shown in dmesg is no good.  I just need someone to tell me how to change that one bit.

---

### Post by Fitch on 2010-01-21
Someone please give me a clue! ](*,)

---

### Post by Vitoid on 2010-01-29
Hi all, First off I'm pretty new to all this, but, i managed to get the sound working. This is how:

1. in terminal run: pactl load-module module-loopback

2. Start tvtime with: tvtime | arecord -D hw:1,0 -f S16_LE -c2 -r32000 | aplay -

3. Start (install) QT Jack Control interface, setup input device as hw:1,0 and output as default, start the service, for me it produced a server error, cancel out of the error, and close all by right clicking on icon in tray. At this point the audio kicks in

I don't understand why, but this procedure ALWAYS gives me audio. Maybe someone more knowledgeable can see a fix in all this. Standing by, hoping :)

This is on Karmic with a wintv hvr 950Q.

---

### Post by Uncle Spellbinder on 2010-01-29
All these workarounds have not worked for me at all. I just hope this gets fixed in time for Lucid.

---

### Post by Fitch on 2010-01-29
Thanks Vitoid, but as Uncle says, been there, done that, got the t shirt, eat the stew...
There are two problems in this thread.,
a. those with no sound at all
b. those with white noise coming out of their speakers

a. The "pactl load-module module-loopback" thing might actually work if there is no sound because alsa mixer hasn't seen the bttv module correctly.

b. no-one seems to know how to set the MT2050 or TDA9887 or whatever to PAL I or whatever which is a bummer.

---

### Post by charliefdom on 2010-02-02
Hi there,
Has anyone been able to get sound in Tvtime using a Terratec Cinergy XS (em28xx)???
So far, I've tried all the options presented above and nothing has happend.
Any help would be appreciated.
Bye...

---

### Post by Fitch on 2010-02-02
Have you been to [http://kuparinen.org/martti/comp/ubuntu/en/terratec.html](http://kuparinen.org/martti/comp/ubuntu/en/terratec.html)
This chap is not very complementary about that card.

---

### Post by yorgos1 on 2010-02-05
Hi fellas,
I had the same problem just now after installing 9.10.(from 8.04)
Problem solved after  I installed alsamixer and there i un-muted the "line" and sliding up the volume. so simple.

Ubuntuforums saved me ones more, thanks!


```
[   14.823854] Linux video capture interface: v2.00
[   14.877968] bttv: driver version 0.9.18 loaded
[   14.877974] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   14.878046] bttv: Bt8xx card found (0).
[   14.878065]   alloc irq_desc for 17 on node -1
[   14.878069]   alloc kstat_irqs on node -1
[   14.878080] bttv 0000:02:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.878093] bttv0: Bt878 (rev 17) at 0000:02:05.0, irq: 17, latency: 32, mmio: 0xf3100000
[   14.892786] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   14.892793] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   14.892798] IRQ 17/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   14.892844] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   14.895328] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   14.929107] tveeprom 0-0050: Hauppauge model 44354, rev B121, serial# 2133549
[   14.929114] tveeprom 0-0050: tuner model is Philips FM1216 (idx 21, type 5)
[   14.929119] tveeprom 0-0050: TV standards PAL(B/G) (eeprom 0x04)
[   14.929124] tveeprom 0-0050: audio processor is MSP3415 (idx 6)
[   14.929128] tveeprom 0-0050: has radio
[   14.929132] bttv0: Hauppauge eeprom indicates model#44354
[   14.929136] bttv0: tuner type=5
[   14.937965] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
[   14.960449] msp3400 0-0040: MSP3415D-B3 found @ 0x80 (bt878 #0 [sw])
[   14.960455] msp3400 0-0040: msp3400 supports nicam, mode is autodetect
[   14.970896] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   14.984603] tuner-simple 0-0061: creating new instance
[   14.984609] tuner-simple 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   14.985308] bttv0: registered device video0
[   14.985351] bttv0: registered device vbi0
[   14.985392] bttv0: registered device radio0
[   14.995424] bttv0: PLL: 28636363 => 35468950 .. ok
[   15.028768] flexcop-pci: will use the HW PID filter.
[   15.028779] flexcop-pci: card revision 1
[   15.028800] b2c2_flexcop_pci 0000:02:0a.0: PCI INT A -> GSI 18 (level, low) -
.............
.............
```

---

### Post by Fitch on 2010-02-05
Hi Yorgos1 

If only it were that simple..

I believe the problem with the hiss is the default to PAL BD blah blah and PAL I uses a completely different IF,  But if it is a problem with no sound at all, then perhaps that will help someone.

Cheers for keeping this thread alive.

---

### Post by Uncle Spellbinder on 2010-02-27
Installed TVTime in Ubuntu 10.04 Alpha 3, still no sound. Really disappointed here. Worked so well on the same computer with Jaunty and previous versions.

:(

---

### Post by Roughmouth on 2010-03-20
I have a *Hauppauge *WinTV-HVR-950Q
great picture using tvtime but i cant seem to get sound either. I would love for someone out in the ubuntu world to help me fix this. If i could get this fixed i would probly never use win 7 again. help!!!

---

### Post by sgwebb on 2010-04-18
Has anyone tried this in 10.04? 

I am currently using the following workaround.. and I am bit afraid upgrading because I have it at least working this way..

pactl load-module module-loopback
tvtime | arecord -D hw:1,0 -f S16_LE -c2 -r48000 | aplay -

---

### Post by sgwebb on 2010-04-19
> **Roughmouth said:**
> I have a *Hauppauge *WinTV-HVR-950Q
great picture using tvtime but i cant seem to get sound either. I would love for someone out in the ubuntu world to help me fix this. If i could get this fixed i would probly never use win 7 again. help!!!

I have an WinTV-HVR-850, and this works for me

I created a file with this:

pactl load-module module-loopback
tvtime | arecord -D hw:1,0 -f S16_LE -c2 -r48000 | aplay - 

Then execute that file, I hope it works for you as well..
I had to adjust the r48000 to match my signal rate

---

### Post by Merel 469 on 2010-04-22
Installation of Gnome ALSA MIXER worked for me.
TVtime can now produce sound.
Adjust the audio level in the mixer (VIDEO channel) !

---

### Post by sgwebb on 2010-04-30
I have upgraded to 10.04 and this is FIXED for me!!

---

### Post by testazio on 2010-06-17
Still no sound with 10.04

ignazio@ubuntu-box:~$ dmesg | grep bttv
[   28.461738] bttv: driver version 0.9.18 loaded
[   28.461742] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   28.462267] bttv: Bt8xx card found (0).
[   28.462282] bttv 0000:00:0b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.462292] bttv0: Bt848 (rev 18) at 0000:00:0b.0, irq: 16, latency: 64, mmio: 0xf7f00000
[   28.462310] bttv0: using: MIRO PCTV pro [card=11,insmod option]
[   28.462313] IRQ 16/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   28.462341] bttv0: gpio: en=00000000, out=00000000 in=00ff33ff [init]
[   28.462441] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   28.464330] bttv0: miro: id=12 tuner=5 radio=no stereo=no
[   28.464334] bttv0: tuner type=5
**[   28.725233] bttv0: audio absent, no audio device found!**
[   28.810320] bttv0: registered device video1
[   28.810345] bttv0: registered device vbi0

---

### Post by SirPecanGum on 2010-07-25
I installed alsamixer and gnome gui and the audio in TVTime now works! Almost an hour just to watch an old video - Mr. Jolly lives next door...

---

### Post by davis68nf on 2013-02-05
SOLVED!


 I had trouble with my tvtime too. HVR-850 sent a video, but there was no audio. The volume was set at 0 and would not move.


 The solution I found was here:
[http://kimbriggs.com/computers/computer-notes/linux-notes/tvtime-volume-notes.file](http://kimbriggs.com/computers/computer-notes/linux-notes/tvtime-volume-notes.file)
 ---------------------------------------
 In a nutshell, type:
  sudo gedit /etc/tvtime/tvtime.xml

and change the line:
  <option name="MixerDevice" value="/dev/mixer:vol"/>


 So, my tvtime.xml now reads:
  <option name="MixerDevice" value="HVR850:vol"/>


 The OLD code used to read:
  <option name="MixerDevice" value="default/Line"/>

---

### Post by wildmanne39 on 2013-02-05
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

