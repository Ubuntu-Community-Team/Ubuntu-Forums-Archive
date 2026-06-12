---
title: "USB Headset in ALSA with X-Fi"
date: 2009-08-29
forum: Multimedia Software
---

### Post by Atrixium on 2009-08-29
Okay, so I have a fairly interesting problem which I'm hoping is caused by my own neophyte ignorance of this wonderful system. I'm currently Running Linux Mint 7 Gloria (Jaunty Based) with a Creative X-Fi and a Dynex USB Headset.

The purpose of the USB headset is to run in tandem with Diablo 2 and Teamspeak where the game audio is output through the X-Fi and Teamspeak is output to, and recieves input from, the headset.

Here's the situation:

While updating Wine to the newest dev release for some testing, I somehow managed to stuff up my X-Fi, this bothered me since I had just spent a number of days and had gotten it working politely with some new drivers. I looked around and found this article --> [Creative X-fi Linux [Update] | Rants from a Scottish geek]("http://www.moobash.com/Blog/?p=815")

This seemed like a great idea so I followed all the directions except for removing Pulseaudio and modifying the modules file. Everything worked perfectly, in fact with the ALSA snapshot driver my X-Fi finally had proper 5.1! I was super excited and willing to write off my having stuffed it up in the first place as serendipity.

Then I tried to run Teamspeak, this is where it all fell apart. Testing under Teamspeak revealed that my previously working USB Headset was no longer working. I went into "gnome-sound-properties" and found that my USB device was now listed as "USB Device 0Xd8C:0X0C USB Audio (OSS) Not Connected" 

I checked and it was most definately physically connected. I changed ports but it had no effect. I also ran "lsusb" and found that is was listed as "Bus 001 Device 005: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter"

I ran "alsaconf" and it only showed me the X-Fi and the HDA-Intel, no USB audio.

This made me curious so I ran "cat /proc/asound/cards" and it gave me the following:

 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xdffec000 irq 7
 1 [XFi            ]: SB-XFi - Creative X-Fi
                      Creative X-Fi 20K1 Unknown

Now unless I'm crazy, there is no USB audio device listed there which prompted me to check Google since by this point I was well, well outside of my element. One result suggested I change "options snd-usb-audio index=-2" in alsa-base.conf to index=-1, this resulted in me losing sound altogether so I changed it back.

Another result suggested commenting out that same line but the result was the same. Out of my own curiosity I changed it to 3 but nothing happened that I noticed.

I've tried rebooting with the device unplugged and then plugging it back in when Mint is fully loaded but that didn't help either.

I've exhausted my rather limited knowledge of Linux and now I've come to beg for the help of a resident guru! First one with a solution gets a cookie and my eternal gratitude! :)

---

### Post by Atrixium on 2009-08-30
I hate to bump this thread but I'm running out of hair to pullout :confused:

---

### Post by Atrixium on 2009-09-05
Bump number 2, for great justice!

---

### Post by Atrixium on 2009-10-21
Still no luck with this one myself, bump!

---

