---
title: "Default sound play through wrong card."
date: 2009-03-29
forum: Multimedia Software
---

### Post by chris_andrew on 2009-03-29
Hi, all.

I have two sound cards, one built-in and one PCI Soundblaster.

I'm using xfce as a desktop, and when I play avi files or music, I don't get any sound.  I've used xfmixer to ensure the master volume is selected for my preferred sound device (Soundblaster), but I'm guessing that the sound output in these applications is being sent to the "default" card, which I'm guessing is my built-in one.  Can anyone tell me how to change this permanently, ideally system wide, not just for my own account?

Many thanks,

Chris.

---

### Post by thirdspace on 2012-01-30
How to set the default sound device in Xubuntu Oneiric (11.10).

This assumes you are using PulseAudio, which is normal for Xubuntu.
This should work for any recent Ubuntu flavor, but if it breaks,
you get to keep both pieces.

First, make sure you have the pactl command-line tool installed.
Open a terminal window.

  $ pactl info

This will show some nice information including the Pulse names of
the current Default Sink (sound output) and Default Source
(sound input).

  $ pactl list short sinks

This will show all the Sinks that Pulse knows about in what would
be a nice table if only your terminal window were wide enough that
it did not have to wrap each line around to make two lines. Anyway
the first item for each card is an index and the next is the name
of the Sink, and the rest is not interesting.

  0	alsa_output.pci-0000_00_1b.0.analog-stereo blah blah blah
  1	alsa_output.pci-0000_02_00.0.analog-stereo blah blah blah

At this point you can probably figure out which Sink you want to
set as your default, or at least what names are worth trying.

So now you are ready to risk causing your computer to catch fire,
by editing an Important System File, namely, '/etc/pulse/default.pa'.

  $ gksudo leafpad /etc/pulse/default.pa

Go to the end of the file and add a line like:

  set-default-sink alsa_output.pci-0000_02_00.0.analog-stereo

but with no leading spaces, and with your chosen Sink name instead of
mine.

Save the file and try it out. After saving the default.pa file, you
probably should kill the pulseaudio daemon and maybe even restart
any sound-producing programs you are running.

  $ pulseaudio -k
  $ pactl info

On my system, something starts a new pulseaudio daemon instance as
soon as I kill the existing one, saving me the trouble.

If you got this far, you can probably figure out how to change the
Default Source too, if you want to.

---

