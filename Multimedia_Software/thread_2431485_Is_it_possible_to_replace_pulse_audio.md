---
title: "Is it possible to replace pulse audio?"
date: 2019-11-17
forum: Multimedia Software
---

### Post by casey-earnshaw on 2019-11-17
Hi everyone.

I am currently running 2 computers, one with Ubuntu 18.04 and one with Linux Mint 14.2. Occasionally I have found on both that when a sound changes, I.E. the next video on a youtube playlist plays or if I pause my music player then restart it while running something else that makes noise like a game then the audio becomes really crackily. It happens on both but it seems to be a lot more frequent on Ubuntu. 

I found a workaround for this...I'm not really sure how I think its just that the more I've been using Linux the more personally intuitive I've found it and I can fix it by opening a terminal and typing 
$pulseaudio -k

This fixes it but it upsets the applications that are currently playing music :(

VLC needs to be closed and reopened in order to play anything.
Youtube will need refreshing because it will be unable to load the video
The only game I really play is factorio and I like to play it with an audio book but killing pulse audio will drop the FPS from around 60 to around 2 or 3 which means the game needs reloading.

This is all bearable because there are work arounds but there's obviously something wrong. I was just wondering if there's a different audio system I could try out? I'm guessing if I just uninstall pulse audio then I'm going to have no sound at all right? I've heard of a different program called alsa but I'm not really sure how this works. Is alsa completely separate or does it require something like pulse audio to sit on top of it? Like how Gnome has to sit on top of x.org.

Thank you for your time

---

### Post by CatKiller on 2019-11-17
The crackling issue sounds like sample-mismatch: the new audio stream has a different bitrate to the old one, but it's being played at the old bitrate. There are a bunch of options around how streams are resampled or otherwise manipulated that you can play with in PulseAudio.

pulseaudio -k kills and restarts PulseAudio, which is a sledgehammer solution to getting the sample rate to change. It will have significant consequences for any software that expects the sound server to not disappear, as you've already found. 

ALSA provides the interface between the hardware and some kind of mixer for applications to use. It used to come with its own suite of software bits but they had significant limitations, which was why PulseAudio was invented. Taking out PulseAudio and replacing it with the old software stack will likely make your resampling issue worse, not better. 

Adjusting PulseAudio's configuration so that it better matches your hardware is the best approach to fixing your issue.

---

### Post by casey-earnshaw on 2019-11-19
Hi thanks for the reply

Unfortunately when it comes to audio configuration I'm completely ignorant. I don't have a musical bone in my body and configuring something as complex as an audio system is seriously out of my depth. I did find the config files in /etc/pulse however I'm still kinda new to editing config files and I am worried I'll make it worse. I suppose I could make back ups but I'd be tinkering in the dark.

Is there only one thing out there like pulse audio or are there other competing programs? I'm wondering if maybe installing a different one might help if I can get lucky with its defaults.

---

### Post by CatKiller on 2019-11-19
> **casey-earnshaw said:**
>  configuring something as complex as an audio system is seriously out of my depth. 
On the contrary, PulseAudio is really straightforward for the configuration changes that you're interested in; it's all option-value pairs. By contrast configuring ALSA, which you were originally hankering to do, is a complete nightmare with an exotic and opaque structure. 

> I did find the config files in /etc/pulse  
Perfect. 

>  however I'm still kinda new to editing config files and I am worried I'll make it worse.  
The config files are well-commented, the format is straightforward, and the man pages are informative. There is also extensive supplemental information online that explains what everything does, for example the [Arch Wiki](https://wiki.archlinux.org/index.php/PulseAudio#Configuration). 

>  I suppose I could make back ups but I'd be tinkering in the dark. 
Yep, that's the sensible way to edit configuration files: copy the original to *whatever.name*.backup and then, if it all goes pear-shaped, just copy it back again. Bonus points: you can easily do that from the command line or from a live environment if it's all gone *really* pear-shaped. 

>  Is there only one thing out there like pulse audio or are there other competing programs? I'm wondering if maybe installing a different one might help if I can get lucky with its defaults.
I *really* don't understand why you're so fixated on using something else. The defaults come from what's sensible in the majority of cases, and based on ALSA's best guess about the specific hardware it's running on. That's always going to be the same, whichever audio stack you're using.

To answer the question, ALSA's old software stack was *much* harder to configure and had significant limitations; JACK is a completely different paradigm, is harder to configure than ALSA, and it's main benefit - extremely low latency - is only useful to a specific subset of a specific subset of users and needs you to be running a specifically-modified kernel; PulseAudio's eventual replacement, PipeWire, is still in the design stage.

Now switching to any of those seems much harder than changing a value or two in a text file, but maybe that's just me.

As an example, I use an external USB sound card. It natively uses 24-bit audio at whatever sample rate is needed, but the signal over the wire is actually 32-bit. Ubuntu has always handled it perfectly, but games run through Proton would sometimes get very confused and would garble their audio requests, which gave exactly the kind of crackling you've described that you're having. Finding the *default-sample-format* entry and setting it to s32le (signed, 32-bit, little-endian) sorted it all out. Perhaps it's a different value that you'll need to change, or perhaps you'll need to adjust the resampling method - I know nothing about your hardware or the streams you're trying to use - but all the options are straightforward.

---

### Post by SeijiSensei on 2019-11-19
If you have multiple audio channels, say the normal headphone/speaker jack and also sound via an HDMI cable, you might want to install the utility pavucontrol:

```
sudo apt install pavucontrol
```

It gives you a nice interface to mark which channel you want to use by default, and how you want to set it up.

[img]https://www.politicsbythenumbers.org/images/pavucontrol.png[/img]

---

### Post by nik.charles on 2019-11-23
> **casey-earnshaw said:**
> I did find the config files in /etc/pulse however I'm still kinda new to editing config files and I am worried I'll make it worse. I suppose I could make back ups but I'd be tinkering in the dark.

no need to edit files in etc/pulse/

copy 3 main configuration files to home folder:
```
cp /etc/pulse/default.pa ~/.config/pulse/default.pa
cp /etc/pulse/daemon.conf ~/.config/pulse/daemon.conf
cp /etc/pulse/client.conf ~/.config/pulse/client.conf
```

edit new files in home folder only (no sudo required)

restart pulseaudio to load new home folder configuration
```
systemctl --user restart pulseaudio
```

if anything goes wrong delete new configuration file(s) and restart pulseaudio to revert to system default

see 'man pulse-daemon.conf' and 'man pulse-cli-syntax' for more information about these configuration files

---

### Post by Skaperen on 2019-11-23
i sometimes hear that crackling sound, too, so i am reading with curiosity.  i have dabbled on it and found that turning the volume down for a few seconds in pavucontrol reduces or eliminates the crackling.  if i stays down for a few seconds, it sometimes is gone by the time i turn it back up.  other times i leave it alone and the crackling often goes away.  i have paused the player a few times and that usually makes it go away.  often, the crackly sound seems to be slightly related to the intended sound, but more often it's like it's getting clipped random bytes.

i have looked around for possible replacements for this reason and for others.  "jack" seems to be the best choice but i need to research this more.  i run pulseaudio in system mode so that i can continue to hear the music as i switch around to different userids (i do this a lot).  i don't know, yet, if "jack", or any other, can do this.  in the research i have done, i discovered that pulseaudio uses a buffer sharing method to reduce sound latency for gaming.  while that is not a big concern of mine, it could be for others.  and i can understand that effect on videos, having worked in broadcast TV for a few years.  i enjoy many online videos and don't want to ruin that.

for those who might recall my reference to "hearing impairment" in other posts describing why i do not have any kind of phone, i cannot hear in the one ear i can hold a phone to, but i can hear computer audio well in the other.  and, no, i don't want a speaker phone.  i have become accustomed to other ways to communicate.

---

