---
title: "Audio Playback for wav audio files"
date: 2011-03-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Buschbarber on 2011-03-21
My PC has a Realtek audio adapter on my P5Q Asus motherboard. Since I have a 5.1 Surround Sound speaker system, I choose Internal Audio Analog Surround 5.1 Output and Analog Stereo Input.

My problem is that I have a WAV file, that I recorded, that I assign to gm-notify, to announce when I have new email. I have used this file an numerous previous versions of Ubuntu, with good success, but in 11.04, it plays with an annoying "tick, tick, tick," as long as the audio plays.

It does not, however, do this at the Login screen drum roll or when the Desktop opens.

Is there a way I can adjust the Audio Settings to stop this from happening? I am using the default Audio Player, Banshee.

---

### Post by r-senior on 2011-03-21
If you right-click on the file in Nautilus, go to Properties on the menu, then the Audio tab in the properties window, what does it say for codec, channels, sample rate and bitrate?

Does it play OK if you right-click on it and "Open with Movie Player"?

---

### Post by Buschbarber on 2011-03-21
Codec - uncompressed 32bit PCM Audio
Chanel - mono
Sample Rate - 22050
BitRate - N/A

Other Windows wav files seem to play without the tic.

I recorded another audio email alert, with Sound Recorder. It saved in the ogg format. I am not familiar with that format. I tried to use the Mic in my Microsoft LifeCam Cinema web cam, but it had a tin can sound. I connected a cheap Mic to the Front Mic Port on my PC and played with the Input Volume and Distance from me to the Mic until I got a smooth sound.

The previous wav file played the same, with the tics, whether I opened it  with Movie Player or Banshee.

Any recommendations on a good quality Mic for recordings on a PC?

---

### Post by Buschbarber on 2011-03-22
When I realized I could not play Midi music, I used Synaptic to install Timidity. I had to launch it from Terminal. When I tried to play a Midi file, I believe I was prompted to install gstreamer something. The Midi file plays fine, but Banshee and Movie Player disappeared as if they were Uninstalled. I reinstalled Banshee, but I could not find the installer for Movie Player, in Synaptic.

I have a number of tracks from audio CD's I own that I ripped to MP3's. I have had no problems playing them on my iPod 3, Droid cell phone, W7, and other versions of Ubuntu. When I click on them in 11.04, I get an error that I need an app to play them.

What am I missing?

---

### Post by Buschbarber on 2011-03-22
It appears that when I tried to play the Midi file, I was prompted to search for the proper Codec. Once it was installed, the Midi file played properly. It appears the same was true for the MP3. I was prompted to search for the proper Codecs and it found more Gstreamer files. The MP3's now play.

Do you know if Banshee will play DVD's?

---

### Post by r-senior on 2011-03-22
> **Buschbarber said:**
> Codec - uncompressed 32bit PCM Audio
Chanel - mono
Sample Rate - 22050
BitRate - N/A
I think it should play OK, but this is a slightly odd format for a WAV file. A CD quality WAV is typically 16bit with a sample rate of 44100. Think of yours as being very high resolution in the height of the waveform (32 bit vs 16 bit) but a comparatively low resolution in the width of the waveform (22050 vs 44100).

When making WAVs 16 bit/44100 is a good standard to aim for.

> Any recommendations on a good quality Mic for recordings on a PC?
Depends what you are recording. I don't use any mics that go directly into a PC. Condenser mics generally give the best frequency response and therefore clarity.

I suspect your other problems, as you are finding, are down to codecs.

There's a help page here, although it seems slightly out of date:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

The general solution to this is to install the ubuntu-restricted-extras package, e.g. from Synaptic. You need to add the "multiverse" repositories to your software sources first. See screenshots.

I loaded up a DVD and Banshee didn't recognise it. I don't know whether it can or not. Totem, the movie player, works well for DVDs.

The Ubuntu startup sound, by the way is OGG. Audacity is a good piece of software for resampling/converting/checking audio files.

---

### Post by Buschbarber on 2011-03-22
Thanks!! I have installed Ubuntu Extras in the past, I was just not sure what was compatible with 11.04. I have used Audacity before. It worked great for creating Ringtones, for my cell phone. I may have even used it to record the wav file I mentioned.

This Unity is quite a bit different than the ones I have used on other versions of Ubuntu. I cannot seem to find Software Sources. I have used it before, to add Repositories in other versions of Ubuntu, but I cannot seem to find it using Unity.

---

### Post by Buschbarber on 2011-03-22
While doing a Google Search, I saw a post that says Software Sources is not available in 11.04 until it is released.

How do I add Repositories in A3?

---

### Post by r-senior on 2011-03-22
Three ways I know of:

1. From Synaptic, choose Settings->Repositories
2. From Ubuntu Software Centre choose Edit->Software Sources.
3. From Update Manager, choose the Settings button on the first tab

It's all the same beast.

---

### Post by Buschbarber on 2011-03-22
Thanks!! I found that easily enough. The Multiverse tab is checked. Is there anything else I need to do?

---

### Post by r-senior on 2011-03-22
Just do a search in Synaptic for restricted-extras, tick the little box next to ubuntu-restricted-extras (assuming you are using Ubuntu and not Kubuntu, etc), then hit the Apply button in the toolbar.

Or, if you prefer a terminal version:

```

$ sudo apt-get update
$ sudo apt-get install ubuntu-restricted-extras

```

---

### Post by Buschbarber on 2011-03-22
I had no problems installing unrestricted extras. My question was do I need to add the Multiverse Repository. The checkbox, for Multiverse, on the Software Sources page, is checked.

---

### Post by r-senior on 2011-03-22
No, there's no need to do anything else to add it. It's either on or off. All the update programs - apt-get, synaptic, update manager, software centre - will look in multiverse now for updates and new software.

---

### Post by Buschbarber on 2011-03-22
Thank you!! I dual boot between W7 and Ubuntu. Each is on a separate HDD. When the newest version of Ubuntu comes out, I test it out to see how well it does the things I need it to do. When the Ubuntu Ultimate Edition comes out, I install that on another HDD. When the next version of Ubuntu comes out, I install it over the previous version. I am constantly recycling, with one stable version of W7 64bit Pro, on stable version of UE, and the latest Ubuntu.

I am retired from Kodak, but I spent many years in IT there. I attended the unveiling of Windows, in NYC, when it first came out and I have mainly been a Windows or Mac support person. I did not get into Linux until Ubuntu showed up.

I can do pretty much anything in Ubuntu that I can do in Windows, except run my Flight Simulator. I fly Radio Controlled RC aircraft and I spend the winters flying on my 50" HDTV. There is no hint of them porting it to Linux any time soon.

---

