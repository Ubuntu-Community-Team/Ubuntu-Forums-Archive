---
title: "Sigh. Linux sound. Again."
date: 2009-02-16
forum: Multimedia Software
---

### Post by BetterSense on 2009-02-16
I just finally switched over to 64 bit intrepid because I need the memory for photo editing. My sound is broked. Again.

I only care about SPDIF. It's the only audio connection my computer has. I simply want everything to play out of SPDIF, all the time.

*mplayer -ac hwac3 *dvd** works fine and triggers dolby surround on my receiver. There's no hardware problem. But Amarok is silent, even though it says it's playing. Youtube also is dead. No sound.

Alsamixer only has one slider in it. No IEC958 slider this time. Must be that PulseAudio.

OK, so I'm not touching anything. I know there are probably at least 4 separate GUI widgets (sound countrol widget, KDE sound system, Alsamixer, pulseaudio, who knows what else by now) that must be simultaneously set to the right setting in order to get my sound to work. So I'm not touching anything without advice.

Please, what should I do? I so just want my sound to work. I wish it was a simple matter of editing a configuration file, but it's so complicated now that it's simple.

---

### Post by Vico Vicario on 2009-02-17
Sound has become complicated *sigh*. My understanding is that Ubuntu/Gnome would like things to be like this:

[IMG]http://img23.imageshack.us/img23/1170/audioarchru3.png[/IMG]

So to fix my audio problems, I installed all pulse packages, installed all alsa packages, installed all gstreamer packages.

Then to fix Skype install oss-compat, which adds oss compatibility. To fix amarok, open preferences and select pulseaudio output. To fix SDL games and applications install libsdl with pulse backend.

You can control volume at the app, pulse or alsa level. The volume applet controls alsa device.

Bye bye,

V.

---

### Post by Reeman on 2009-02-17
If alsamixer has only one slider in it you are most likely set to use the OSS drivers. You should be able to change it back to alsa and whatever your sound system really is. I am also getting very tired of being borked by pulse and OSS drivers. If you have Audacity installed try to see if something other than OSS is available through preferences. If not then try killing the pulse audio server then access alsamixer (no X) through a terminal to see if there are all the connections present that should be available. I have been borked for the last time by pulse and OSS my Ubuntu Studio install does not include the pulse audio server at all. Been there done that.

---

### Post by BetterSense on 2009-02-17
> You can control volume at the app, pulse or alsa level. The volume applet controls alsa device.

Exactly. WTF. I don't want to conrol it at 4 different places. Most of all, I would like to listen to some music right about now but the only thing that my computer plays is AC3 streams from mplayer'd dvds. The gnome-menu's "Test" buttons don't even work.

---

### Post by Reeman on 2009-02-17
> **Vico Vicario said:**
> Sound has become complicated *sigh*. My understanding is that Ubuntu/Gnome would like things to be like this:

[IMG]http://img23.imageshack.us/img23/1170/audioarchru3.png[/IMG]

So to fix my audio problems, I installed all pulse packages, installed all alsa packages, installed all gstreamer packages.

Then to fix Skype install oss-compat, which adds oss compatibility. To fix amarok, open preferences and select pulseaudio output. To fix SDL games and applications install libsdl with pulse backend.

You can control volume at the app, pulse or alsa level. The volume applet controls alsa device.

Bye bye,

V.
Better solution...audio and vlc <--> alsa <--> sound devices 

OR Audio GUI <--> jackd (with -t option) alsa <--> sound devices.

At least this way you do not have to contend with persistant locks on /dev/dsp!

I am getting totally fed up with Ubuntu and the disregard for a sane audio-video setup. From what I am reading the jump to 64Studio is going to be great in about 2 weeks when 3.0 comes out with a realtime kernel and a sensible audio and video setup!

---

### Post by Vico Vicario on 2009-02-17
Agreed it is a mess. Add another sound card and you can kiss goodbye your sanity.

This post is very useful:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

V.

---

### Post by ByteXP on 2009-02-17
Sounds unreliably working, not working, never worked? After trawling through a zillion responses I believe that I have the answer (possibly) for all flavours of Ubuntu. On my Kubuntu 8.04 PC it was the ACPI function. Disabling ACPI has cured all my sound issues and it worked with Vector Linux too, both with 'out of the box' sound setups.

---

### Post by ByteXP on 2009-02-17
Sorry,I should have mentioned that if you disable ACPI, Ubuntu will no longer power off at shutdown-you'll have to ignore the error messages and press the button. Seemed like a good deal to me after 4 days of struggle and the sound just keeps on working, reliably.

---

### Post by ByteXP on 2009-02-18
I'm, sighing with you now. ACPI turned out to be a false dawn. Sound gone down again. There is more to life than linux sound issues!

---

### Post by silentb on 2009-02-18
Hehe, I can't run several audio applications at all. That's why I only use programs that support JackD. Which Amarok and Flash player don't. *sigh*

---

