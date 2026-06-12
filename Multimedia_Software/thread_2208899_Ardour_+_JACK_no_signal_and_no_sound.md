---
title: "Ardour + JACK no signal and no sound"
date: 2014-03-02
forum: Multimedia Software
---

### Post by julipanette on 2014-03-02
Dear people who might help me figure this out:

I can sometimes get sound and sometimes not, and I can't figure out what changes are happening between those sessions.

I am using Ardour and JACK in Ubuntu 12.04 LTS with an external soundcard; an M-Audio MobilePre. It's all nice and connected, the external soundcard is automatically recognized and selected both by JACK and in the general system sound settings, and Ardour is properly connected to System in JACK. Levels from recorded tracks in Ardour projects move when I play but I'm not getting any signal from the external soundcard into Ardour although the signal is processed in the soundcard itself, and no sound from Ardour.

Things I've tried:

Someone on Ardour's irc channel suggested it could be PulseAudio blocking the soundcard. But sometimes I get sound, without having killed PulseAudio. I can't figure out how to kill PulseAudio without logging in as root user and that is too thin ice for me to be on, obviously. People have suggested the command "pasuspender ardour" or "padsp ardour" but they aren't recognized.

When I do get sound it seems to be after changing back and forth aimlessly between selected soundcards - from the ones I know to be incorrect and back to the correct one. Or stopping and starting JACK and stopping and starting Ardour in various combinations, which I seem to have tried all of them any number of times tonight with no luck. I am unable to see what parameters are changing between when it works and when it doesn't and I am deeply grateful for any attempt at helping me understanding this. I'm stumbling in the dark here, as you can see!

Thanks for any suggestions!

---

### Post by julipanette on 2014-03-03
I've now also tried

sudo killall pulseaudio
sudo alsa force-reload

Tried a proper reboot with several seconds powerout afterwards, no result.

Also wondering why in system sound settings M-Audio MobilePre shows up as both Speakers and Digital Output (S/PDIF), and likewise in input devices; i.e. there are both analogue and digital devices for the same soundcard. No combination of toggling these yields any results though. Everything unmuted in Alsamixer and also toggled between letting alsamixer choose the default soundcard and changing it to the external soundcard.

---

