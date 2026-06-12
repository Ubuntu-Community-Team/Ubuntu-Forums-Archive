---
title: "Making sound work on GIGABYTE GA-MA785GM-US2H with Realtek ALC889A audio chipset"
date: 2009-10-26
forum: Multimedia Software
---

### Post by Isthan on 2009-10-26
Hello all!

I just wanted to give my contribution to this community which helps so many people daily.  When I installed Ubuntu 9.10 recently with a host of brand new hardware, I was not able to get the audio to work correctly right off the bat.  I wanted to make this post for anyone else having problems with the same hardware.

Here is my hardware:
GIGABYTE GA-MA785GM-US2H
AMD Sempron 140 "Sargas"
Seagate Barracuda 500gb
Crucial DDR2 800mhz 2gb
Rosewill 400W PSU
CD-RW

Initially the sound was horrible.  To describe it, it was extremely low fidelity.  I began to tinker with the sound settings thinking the settings I was using by default werent set up for the earbuds I was using to test with.

I played with the settings and thought there were differences between the settings so I found the "least sucky" setting, as it still sounded horrible.  I tried this with other audio sources and found it to be intolerable.  I played with the settings some more and eventually got to a point where there was NO sound no matter what I changed.

I logged out, thinking it was going to be a problem local to the session.  Upon logging back in, still no sound.  Frantically I tried to get sound back.  In my System prefs under sound, I had two hardware profiles.  The motherboard has "HD audio" and "Internal Audio" hardware profile that appears.  I thought to disable the HD audio since I had no intention on using that in the near future anyway.  After I disabled the HD audio profile, my sound returned and in the proper fidelity!

I hope this experience helps you along your paths.  If you have the same hardware and similar or different problems, send me a private message and i'll be glad to help any way I can!

---

### Post by MaindotC on 2009-10-28
After you disable HDA ATI HDMI audio, the other option should be "Internal Audio" right?  And of that category, which Profile did you choose?  My audio is fine but I can't get my microphone jack to work!  I used the AC97 audio connection from my case, not the HD audio.

---

### Post by Isthan on 2009-10-29
Yes on "Internal Audio" i'm using the profile of "Analog Stereo Output."  Since this is a secondary computer I have it hooked up to a two-speaker stereo, so it seemed like the best choice.

I am curious to try my microphone now though, thats one aspect I had not considered.  I will try to test it but when I look into the "Input" tab, I dont see any devices.  Does this only show up after I have plugged in a microphone to the jack?  Do I also need to switch profiles by chance?

---

### Post by MaindotC on 2009-10-29
I'm still not getting anything on my mic :(  I re-opened the machine and made sure I had the sound jacks on the front panel properly connected, using the AC97 instead of the HD Audio connection.  I'm following the [Sound Troubleshooting Guide](https://help.ubuntu.com/community/SoundTroubleshooting) and I'm at the point where I can edit/configure the /etc/modprobe.d/alsa-base.conf file but I'm not sure if this is really necessary or what options to try.  *confused*

---

### Post by Dr. Freeman on 2009-11-01
Gigabyte GA-MA78GM-US2H Ubuntu 9.10 Disabled the RS780 Azalia controller (Profile: off) and set the Internal Audio Profile: Anolog Stereo Output and audio started working immediately!  Didn't even have to reboot or log in/out

Thanks for the quick tip and fix!!!

---

### Post by MaindotC on 2009-11-01
I got it working by installing the linux-backports-modules-alsa-karmic package.

---

### Post by lifeform23 on 2009-11-02
I would really like to minimize the number of cables that I'm running from this same MB.  I was hoping to be able to run the HDMI cable only for sound and video.  Judging by the posts here that won't be possible. Am I wrong?
I also noticed that the optical output doesn't seem to work.  Has anyone else found that to be the case?
Its great that there is a work around using the analog sound but it kind of defeats the purpose of having a board with all of these sweet outputs.

On a non-audio note...the HDMI video output with the proprietary ATI drivers is pure sweetness

---

### Post by lifeform23 on 2009-11-02
digital sound works great.  You have to set digital output in both the hardware and output profiles. Oops.
I guess I just assumed selecting digital in one area would automatically change the other

---

### Post by agentsmith23 on 2009-11-08
Which digital out are you using? Optical or HDMI? I can't get HDMI to work no matter what I do and I haven't tried optical yet.

---

### Post by MaindotC on 2009-11-19
I'm back to square one.  Mic not working :(

---

### Post by souta95 on 2009-11-19
I'm having similar problems.  I'm not getting sound input to work with the internal audio, I'm working on getting my video capture card set up.

I have a PCChips motherboard with the nVidia MCP61 HD audio integrated (I believe its actually a Realtek chipset, though).  The audio configuration only lists one device, so its not anything to do with my video card as far as I know.

I've read that there are several issues with these chips in Linux, but most of that news was from around 2007.

Output works fine, although I can't set it to anything but 2-channel (stereo).  The Windows drivers support 5.1 surround (6-channel) from it.

I'm not going to mess with it all that much, I'm just going to throw in a PCI sound card (either a C-Media, or an old SB Live! Value) and disable the integrated sound, but I would like to know if a solution presents itself.

FWIW, lspci gives the following (one is the integrated sound, the other is my video capture card):

```
lspci | grep -i audio
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
```

---

