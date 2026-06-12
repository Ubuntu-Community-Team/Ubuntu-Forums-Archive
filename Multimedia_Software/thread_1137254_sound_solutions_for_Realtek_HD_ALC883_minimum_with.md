---
title: "sound solutions for Realtek HD ALC883 minimum with sound apps bug notes"
date: 2009-04-25
forum: Multimedia Software
---

### Post by planetLars on 2009-04-25
Hello,

having had identical issues with Ubuntu 8.04 Hardy Heron and 9.04 Jaunty
Jackalope with my Laptops soundchip and getting it to work after a while,
and experiencing obvious faulty behaviour in Ubuntus audio applications,
I decided to write this walkthrough.

Here's the sound system details to which this walk-through applies at
least:

**Realtek HD Audio chip ALC883 with ATi Technologies Inc IXP SB4x0 Hi** chips
bound to be used by the hda-intel driver.

Initially on displaying the login screen for the first time after fresh
installation the welcome sound could be heard. This was the only sound
from then on until my solution.

[B]Neither PulseAudio, ALSA, OSS, chip (OSS), chip (ALSA) nor Automatic
Detection in the sound settings let any sound output.[/B] Some settings even
displayed error mesages about device or files being in use (the chip
(ALSA) settings) which I can't repeat now because I got it to work ..

The first step you may try, which I always did last and thus don't know
whether that's all that's needed, is **enabling the Surround channel**
in the mixer and setting it's output level such high that you would hear
something if everything worked. This enabled audio through the built-in
speakers of my laptop. At that point after my steps, headphone output
always worked but I never knew until I accidentally tried once!

I assume you know what are and how to use standard Ubuntu tools such as
the Synaptic-Package-Manager or the sound-volume-applet (hint: look in
the System menu and the top task bar).


**First step:** get the Realtek HD audio driver for Unix (Linux) from
[www.realtek.com.tw](www.realtek.com.tw).

**Second step:** find and apply the following packages: patch xmlto gettext
build-essential and their suggested dependancies.

[COLOR="Green"](This is what is needed with Realteks driver 5.11 and Ubuntu 9.04.)[/COLOR]

**Third step:** Decompress the downloaded driver file.

**Fourth step:** Decompress the driver, utils and lib file which you got from
decompressed downloaded driver file.

**Fifth step:** On the command-line, enter the lib directory.

[COLOR="Red"]sudo ./configure, sudo make, sudo make install.[/COLOR]

**Sixth step:** likewise enter the utils directory.

[COLOR="#ff0000"]sudo ./configure, sudo make, sudo make install.[/COLOR]

**Seventh step:** .. enter the driver directory.

[COLOR="#ff0000"]sudo ./configure, sudo make, sudo make install.[/COLOR]

**Eigth step:** sudo alsaconf. Your chip should be detected. If not, this
driver isn't for you. Select it via the arrow keys on your keyboard,
**remember the name of the driver next to it**, and press enter.
Answer yes to adding information to conf files.

**Ninth step:** open command line. cd .. up to /. sudo gedit etc/modules.
Enter the following lines:

*driver name*
# ALSA portion
alias char-major-116 snd
alias snd-card-0 *driver name*     
# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

**Tenth step:** reboot and open sound volume applet (mixer) and unmute
everything and set the volume levels high. That's it.


[SIZE="5"]Bug notes:[/SIZE]

**Video-Player:** max. Volume not settable: When reaching max volume by
sliding via the mouse, the knob sets itself to zero
(if(MixerObject.translate(slider.getValue()) > Constants.MAX_AUDIO_VOLUME)
MixerObject.setVolume(0) always true ?????).

**Volume-Manager:** disabling PCM and enabling PCM leads to cracking sounds
only coming out of the speakers for about two minutes. Reentering volume-manager after enabling PCM has PCM slider value set at 0 though it wasn't
0 before. Muted microphone sliders are unmuted on each entering of volume-manager. Unmuted RecordX sliders are muted on each entering of the
applet. Applet update of state is slow needing close and open to show all
options at times and sliders feel inprecise.

(Translated application names from German).


[B][COLOR="DarkOrange"][SIZE="4"]Hope it helps, mixer issues should be sorted out, comments welcome.

Best Regards![/SIZE][/COLOR][/B]


Lars

---

### Post by Wistful on 2009-04-25
What should I put in etc/modules "driver name" ?
How can I know what is the driver name  ?

---

### Post by planetLars on 2009-04-25
when you run sudo alsaconf, alsaconf detects your soundchips and tells you the driver name for each sound chip. In my specific case snd-hda-intel.

---

### Post by Wistful on 2009-04-25
I don't know if this works cause I've stopped at the 'driver name' and tried other solution from this thread 
-> [http://ubuntuforums.org/showthread.php?p=7146245&posted=1#post7146245](http://ubuntuforums.org/showthread.php?p=7146245&posted=1#post7146245) posted by user [COLOR="Red"]gkgarg24[/COLOR] that worked 100%

---

### Post by planetLars on 2009-04-26
most excellent that you found a solution! When you write "that worked
100%": was there a step which resulted in an error or which didn't work
or which gave any other impression that made you doubt it succeeded?
([SIZE="1"]had you read **everything** properly until you stopped, you
would have gathered that just 4 lines above that place the driver name is
pointed at.[/SIZE]
I gather from your other threads post that you have an ALC889. Maybe this
chip can be added here. On the other hand, this walk-through is for first
time getting sound to work. You had just lost the sound after an upgrade.
:) HAND or rest-weekend. (Have A Nice Day)

---

### Post by aatu_kanifani on 2009-07-12
Also remember after the reboot:
1) In "Volume Control", go to "Switches"-tab
2) Enable the "IEC958" (or whatever number you have)

This made the optical output come alive in my system (Gigabyte 965G-DS3, Ubuntu 9.04).


BTW: In the alsaconf: after the autodetect it asks you to choose between different chips/cards ("hda-intel" and "legacy" in my case), but in the next popup it talks about "snd-hda-intel", and that's the one I used when gediting the modules-file...

---

### Post by planetLars on 2009-07-13
I have got an optical SP/DIF out which never worked under Ubuntu although it works under Vista and despite having chosen the correct model. See here [http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt) for audio-models, i.e. wheter 3-jack laptop output or 1 jack all in one audio in/output. Also read here [http://www.kernel.org/doc/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.kernel.org/doc/Documentation/sound/alsa/ALSA-Configuration.txt). I just don't know anymore where to put the audio model line (perhaps in a boot script).

My graphical volume control (mixer) does have no IEC958 switch and there is not an option in its settings (right-click the mixer-applet-icon in the top "appbar") to enable one.

Console alsamixer neither has an IEC switch or if it had it always was disabled and could not be enabled.

And yes, you are right: snd-had-intel is the driver name on the second page and not where you choose the legacy (old) or high-definition (hd) type of driver. 8-[

 
But there's a far better solution: Use OSS4 !

It's FOSS, light-weight, small, fast, fully-featured, easily highly configurable graphically and everything works. Skype in the OSS-version completely works finally. VirtualBox becomes usable with audio enabled and so on.

[http://www.4front-tech.com/](http://www.4front-tech.com/)

The current version is 4.1 as of writing this. Download the deb (x86 or x64) from here [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi). Just run the deb and click install and reboot! You're done. There's a list of applets in the accompanying pdf (whose link I don't find anymore) (use ossxmix for the graphical mixer). The deb is a 6 month trial in fact but you can get the sources and compile it yourself if you want it as FOSS. (vlc media player needs the path set in the advanced settings of the audio device to use sound, use pcm4 as headphone output if you want all channels through your laptops audio out).

 
Best

Lars

---

### Post by aatu_kanifani on 2009-07-19
> **planetLars said:**
> 
My graphical volume control (mixer) does have no IEC958 switch and there is not an option in its settings (right-click the mixer-applet-icon in the top "appbar") to enable one.

Console alsamixer neither has an IEC switch or if it had it always was disabled and could not be enabled.


Hmm, try this:

Right click the taskbar icon => "Open Volume Control" => Make sure "Device" is set as "HDA Intel (Alsa mixer)", then click "Preferences"

There should be (at the end of the list) few options marked as "Switches": I've checked "IEC958" and "IEC958 Default PCM". Also check "PCM" from the beginning of the list (marked as Playback), if it isn't already.

It seems the "PCM" in Playback-tab, and "IEC958" in Switches-tab are the ones that make the difference for me.

Note to people trying this: In 8.10 (and 8.04) this made the optical output work without the ten steps, but in 9.04 you probably have to do the steps first. Well, I think it worked also in 9.04 at first, but then got broken after some update...


After note: If someone Mutes the "PCM" from Playback-tab, it sometimes doesn't come back on with only Unmute-button. In this case you additionally have to move the slider a little bit lower and then back to max.

---

### Post by planetLars on 2009-07-19
I installed OSS4. This apparently removed ALSA. I only have the OSS driver available now for my ALC883.
I'll take note of this setting though if I use ALSA anytime again.
Thanks!

---

### Post by jpt266 on 2009-07-19
Can someone explain "step 2" please? Just what am I to look for and then apply?

Thanks,

---

### Post by planetLars on 2009-07-20
> **jpt266 said:**
> Can someone explain "step 2" please? Just what am I to look for and then apply?

Thanks,

Hi, you have to open Synaptic Package Manager from the System menu and search for the listed packages individually (using the search button, not the quicksearch).

Lars

---

