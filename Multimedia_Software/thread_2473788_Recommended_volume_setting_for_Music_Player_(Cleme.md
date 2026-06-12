---
title: "Recommended volume setting for Music Player (Clementine)"
date: 2022-04-14
forum: Multimedia Software
---

### Post by lister171254 on 2022-04-14
I've posted the following in the Clementine Google Group, but had so far no response.

I'm using Clementine 1.4 on the latest Ubuntu Desktop.

I have the digitial output go via a Musicial Fidelity DAC with Digital Pre-Amp (DPA) Mode turned off and feeding into a Yamaha Amp.

I found that if I turn the volume on the Clementine player higher than 50, the output sometimes gets distorted. The distortian is most audible on something like a Ballad where the 's' sounds more and more like a hiss the higher you turn the Clementine Volume.

All my Music is in Flac.

Not sure which libraries Clementine uses under the hood to play the audio, but a friend of mine is a sound engineer and he can't find a reason why the Volume on the player should have any impact on the sound quality.

---

### Post by TheFu on 2022-04-14
"latest Ubuntu Desktop" is ambiguous.
[LIST]
[*]Are you using the version **you should be using**, 20.04?  I will assume this.
[*]Or are you using a non-LTS release 21.10?
[*]Or are you running beta soon-to-be-released, but not yet released, 22.04?
[/LIST]
"Latest" isn't useful. What is the release number ... **lsb_release -d** is the command to get it.

So ... only general answers are possible.
PulseAudio is the sound subsystem on 20.04. It controls gain, output channels, etc.  There are many different "volume" sliders that can be tweaked - some are system-wide. These should be set and never touched again.  Then there are volume sliders for each application.  This can be controlled both inside the Pulse Audio control tool or with the volume controls in each application.

The way to setup pulse audio is to run pavucontrol (install it if it isn't already installed), then work from the right-most tab towards the left, ensuring the devices are setup in the way you want that actually still works.  I like to disable any devices in the first tab, to prevent other programs from being confused.
Move left 1 tab at a time, modifying the settings for the device as needed.
When you are finally at the far left tab (Playback), that's were you can pick the running applications that are connected to the pulse server and manage the volume control for that specific application.  Be 100% certain that you've already set the gain in the "Output devices" tab. This is where the distortion is likely originating.  I have mine set to 100% there and use the Playback volume sliders to make the speakers louder or softer.  I haven't touched the "output devices" slider in about 2 yrs. 

Once these things are set, you'll likely be able to control the undistorted volume in each application - including clementine.

If you use a microphone, the steps are the same ... start in the "Configuration" tab and move left.  The microphone gain is set to 100% in the 'input devices' tab, and the microphone _volume_ (I lack a better term), is set in the  "Recording" tab.

---

### Post by Yellow Pasque on 2022-04-14
It may be an issue with the whole pulseaudio "flat volumes" thing (google for more info)
```
echo "flat-volumes=no" >> ~/.config/pulse/daemon.conf
pulseaudio -k
```

---

### Post by lister171254 on 2022-05-12
Sorry for the late response, but thread emails seem to only work occasionally.

I also upgraded.

I'm now on Ubuntu 22.04 LTS

Attached are the sound settings. 

I have tried the "flat volumes" thing, but that makes no difference.

Also to clarify what I mean by "distortion"; it is with songs/recordings/ballads with "S" in the lyrics. The "S" is (sometimes) accentuated and I have no explanation for this. It doesn't happen with all the songs, but I have quite a few examples where it does.

It's not the recording as the songs play fine on a standard analogue output.

I have tried different DACs with the same result, so somewhat at a loss.

---

### Post by TheFu on 2022-05-12
Enable one 1 of the output devices. Disable all the others. This is in the far-right tab. See if that helps.
There's gain and there's volume.  When there is distortion, it is usually the gain that is too high.

I think
[LIST]
[*]Output Devices - gain
[*]Playback - volume
[/LIST]

If the gain is too high, reduce it. Once set for your hardware, just use the volume controls.

Just my guessing.

---

### Post by lister171254 on 2022-05-12
After reading a bit more on pulseaudio and that it's being replaced by PipeWire I followed these instructions [https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/]("https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/") to install PipeWire and the hissing is gone. :-)

---

