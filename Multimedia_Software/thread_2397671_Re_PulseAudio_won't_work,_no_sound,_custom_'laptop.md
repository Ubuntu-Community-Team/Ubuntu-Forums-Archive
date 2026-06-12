---
title: "Re: PulseAudio won't work, no sound, custom 'laptop' build around MeeGoPad T09"
date: 2018-08-01
forum: Multimedia Software
---

### Post by starhawk2 on 2018-08-01
I do hope my experience here will be more positive than the last time... I do unfortunately have a habit of getting ignored on forums...

...at any rate...

My hardware is a custom homemade laptop-like portable computer (there is no battery, so technically it's not a laptop) built around a MeeGoPad T09 MiniPC. The MeeGoPad has an Intel Atom z8300 CPU, 4gb DDR3L RAM, and a 32gb eMMC solid-state drive. I am using a display controller from eBay (which annoyingly does not support the video mode that the MeeGoPad's UEFI uses) attached to a Dell e6400 LCD panel. Peripherals are accessed through an IOGear GUH304 powered USB hub. Power is supplied to the system first as 120vAC through the intake filter from a disused Commodore 1541 disk drive and the primary power switch (which switches both live and neutral) and then as 12vDC from a power brick that has been removed from its original housing. The power brick is rated for eight amps' current output at the specified voltage. This is connected directly to the LCD driver board by way of a barrel jack; a set of wires soldered to said jack run to a wide-input (~9-30vDC in) 5vDC output regulator that is good for ten amps' load at the specified output voltage. This step-down converter powers the USB hub and the MeeGoPad. Spliced into the *input* to the regulator (it was a convenient location for this) is a 12vDC fan, the stock fan from the Dynatron embedded Pentium-M cooler to which it is attached. That cooler cools the CPU of the MeeGoPad, and is attached with a slightly modified version of its stock bracket (the bracket is intended to permit four mount points; the motherboard only permits two, so the bracket is missing two arms and the cooler is missing two bolt assemblies). The MeeGoPad's original cooling scheme was laughably awful; however, the fan that was part of that, now cools the onboard RAM and is situated next to the CPU cooler. I attempted to bodge on a remote power switch, wiring from the motherboard's existing switch; this has proved an unsuccessful effort that I need to go back in and redo. (I haven't done that yet, because access to the motherboard requires the removal of three screws that can only be accessed through the inside of the lid of the LCD.) All of this is mounted to an IBM Model M13 keyboard (a standard Model M, but black, with an integrated TrackPoint mouse) which provides input to the system.

Software-wise, I am running a nearly brand new, standard install of Xubuntu 18.04, with the exception that (as with most MiniPCs that are sold under various brands, MeeGoPad included), the UEFI for this system is 32bit, even though everything else about it is 64bit. Customizations so far have been limited to appearance and the installation of Audacious, Viewnior, and Google Chrome. I have already reinstalled once to deal with an apparently-uncorrectable PulseAudio issue that was of my own making... I would prefer not to do that again, particularly because eMMC is not nearly as sophisticated or as robust as a true SSD in dealing with things such as wear-leveling algorithms. It's better than a standard SD card, although it borrows the (low-level electronic) interface of one... but it's not better by a whole lot.

I have read the sticky at the top of this subforum. With the first linked troubleshooting guide, I stalled out at Step 17... the given command returns nothing, and thus I am directed to follow a procedure that does not yet exist. With the second, none of the sixteen steps resolve my issue.

I suspect something somewhere is misconfigured; however,  I don't know enough to troubleshoot this on my own.

Attempting to access pavucontrol results in the typical "PulseAudio isn't connecting" message. Attempting manual start results in the claim that the daemon both is running and has been killed. I can verify that /etc/asound.conf does not exist and that I have not manually tampered with /etc/pulse/{client.conf|daemon.conf|default.pa|system.pa}.

**I do not know enough to proceed from here on my own... however, I can try to follow directions as given by forum members.**

Oh right... I want the audio out to be through HDMI, and I neither need nor care about input/capture anything. I just want my tunes to play...

---

### Post by Yellow Pasque on 2018-08-04
Start here:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by starhawk2 on 2018-08-04
FINALLY some help! :D

Uploaded script output as ZIP archive because using TXT exceeded forum limits.

I strongly suspect a misconfiguration somewhere within PulseAudio. I'm getting the usual "you screwed something up, you bozo, so I won't connect up to myself" dialog box...

Isn't it a bit rude to provide one single tantalizing piece of help, and then disappear entirely, abandoning a user to hi/her apparent fate?

---

### Post by Yellow Pasque on 2018-08-05
](*,)

> Isn't it a bit rude to provide one single tantalizing piece of help and then disappear entirely, abandoning a user to hi/her apparent fate? 

It's more than a bit rude and impatient to assume that someone "abandoned" you in less than 24 hours on a volunteer forum. Statements like this don't encourage people to help you (quite the opposite). If you want to bump it once a day or whatever, that's great, but I'd suggest not including statements like that even if you're frustrated. Anyway...

All I did was ask for more detailed information. That's not a tantalizing piece of help and it may not be helpful at all, though it could be. I actually skimmed through your log yesterday. I didn't have a ton of time to get deep into it (It may surprise you, but I have other things to do with my weekend.) and it doesn't help that the CherryTrail SoC has 250 mixer controls. It doesn't make for light reading. Looking through the log, nothing jumped out at me other than pulseaudio not running, but I don't claim to be an expert, especially when it comes to Intel SoC audio devices. If it was me, this is the first thing I would try:
[https://bugs.freedesktop.org/show_bug.cgi?id=100488#c39](https://bugs.freedesktop.org/show_bug.cgi?id=100488#c39)
Note that even if it stops pulseaudio from crashing, audio may not work perfectly. Google "chtrt5645 alsa" or "chtrt5645 pulseaudio" and you'll see some other issues with devices using this chipset.

---

### Post by starhawk2 on 2018-08-05
Apologies for the irritation. I just want this fixed... and I'm more used to forum response times measured in hours rather than days...

Let me look at what's at the other end of that link, and I'll report back after attempting its proposed fix.

Setting "realtime scheduling = no" did not fix the issue. I'm going to try a Git compile of PulseAudio, since I've done compiling before and this one looks relatively easy. Again, I'll report back after I'm done.

OK, it's official, I'm a dumb-butt. I somehow didn't realize that the ; in /etc/pulse/daemon.conf meant "commented out" and didn't remove it. Removed it, after that compile, and it magically started working. I probably didn't need the compile.

I feel stupid now!

...alas, audio through HDMI is not going to happen. ALSAMixer reports no controls for that card, and pavucontrol refuses to admit it even exists.

At least this thing has a headphone jack. I can modify the system configuration to pipe audio from there, rather easily, I think... I'll do that.

...well...

The headphone jack doesn't implement autodetect, and manually trying to enforce it through the various files in **/usr/share/pulseaudio/alsa-mixer/paths/** doesn't seem to work. Neither does commenting or uncommenting anything in **/etc/pulse/defaults.pa**.

I *have* blundered my way into enabling the HDMI output -- but it doesn't work either. Files play overly fast and no actual sound output occurs. Mind you, I don't get any output through the headphone jack, either, but at least files play at the proper speed...

...so I guess I hit "solved" a little too quickly. That'll teach me to go by what things look like, rather than what they actually are!

---

### Post by Yellow Pasque on 2018-08-05
I don't have any other suggestions at this moment, other than maybe trying a LiveUSB of something bleeding edge to see if that works any better.

---

### Post by starhawk2 on 2018-08-06
I'll try Mint in the morning, it's my other go-to distro. The problem with Mint, historically, is that these things have a 32-bit UEFI despite being 64-bit in every other respect -- Mint's installer sees that, says "woah, howdy, what's this here awful mess all about?" and promptly curls up and dies. Ubuntu's installer doesn't have that behavior.

I'd report the issue to the Mint devs, but since their forum got hacked that one time, they've implemented a massively horrendous password-requirements scheme (see [https://xkcd.com/936/](https://xkcd.com/936/)) and I refuse to be bothered with such stupidly draconian things that don't actually work as advertised and make remembering the dang thing dang near impossible. Oh, and of course, they've fixed things so that the forum is the absolutely only way to report issues like that...

I guess they just don't want to be contacted.

Mint 19 has the same issues and behavior -- at least, it does from the LiveUSB I made. Did not install.

---

### Post by Yellow Pasque on 2018-08-06
> **starhawk2 said:**
> Mint 19 has the same issues and behavior -- at least, it does from the LiveUSB I made. Did not install.

Mint 19 has the same versions of most packages as Ubuntu 18.04. When I said bleeding edge, I had something like Antergos 18.8 or Fedora Rawhide in mind, though I have no idea how well those work with 32-bit EFI.
In other words, I was thinking of something that uses kernel 4.17.x, pulseaudio 12.x, and hopefully alsa-lib 1.1.6

---

### Post by starhawk2 on 2018-08-06
A valid point, although (a) this is the first of these MiniPCs that I've found willing to run anything newer than Ubuntu 16.04 (!) -- there's something about the display manager that got changed in 16.10 and later, because those systems all freeze at the "just brought up the wallpaper" stage, before cursor, icons, or taskbar/tray appears; and (b) although I've of course heard of Fedora, I've not heard of the other one you mention... for reasons I genuinely cannot explain, I tend to veer away from non-DEB-based distros... for the life of me I don't know why I have that preference, but I do.

EDIT (an hour later) -- it occurs to me that the problem isn't *actually* PulseAudio itself -- the problem is in hardware. The freakin' jack doesn't have a switch in it, because it's a cheap stereo jack. If I could convince the system that there was something constantly plugged into that jack, I'd be completely fine...

---

### Post by Yellow Pasque on 2018-08-06
Nvm

---

### Post by starhawk2 on 2018-08-06
Pretty much what it says in the [Edit] -- if I could convince the machine to assume something **is** plugged in (inverting the default behavior of assuming something **isn't** plugged in) when jack detect fails, then we could quite well hang the "Mission Accomplished" banner up on the battleship and actually mean it this time (lol) because we'd be done with this problem.

Trouble is, I can't seem to get the machine to do that.

---

### Post by starhawk2 on 2018-08-08
'nother bump.

---

### Post by starhawk2 on 2018-08-09
...Beuller? Beuller? Beuller?

Bump number three...

---

### Post by Gstrazds on 2018-08-09
I have this problem too! As soon as I uninstall Pulseaudio my sound comes back.  

I installed Audacity then PulseAudio; which worked correctly in the session. after re-booting my sound icon disappeared with symptoms everybody is describing. 

So I would say as a workaround - After your audacity session - uninstall PulseAudio. then reinstall it the next time you need it. till this bug is fixed.
If your using Audacity all the time I'd volunteer; just leave it on.

Thanks

---

### Post by starhawk2 on 2018-08-09
Since PulseAudio comes with Ubuntu, I suspect your problem is more a clash between the from-Ubuntu PulseAudio and the second version you installed separately. Mine is a hardware issue -- the jack does not physically support plug detection, and the computer refuses to route audio to a jack that it does not know for sure has a plug in it.

Could be wrong about your issue, though... especially since I haven't installed Audacity.

---

### Post by starhawk2 on 2018-08-09
@Temüjin -- you know this forum better than I do... would I be well advised to start another thread in the Hardware subforum and link back to this one? After all, the issue I have now *is* rooted in hardware...

---

### Post by Yellow Pasque on 2018-08-10
> **starhawk2 said:**
> @Temüjin -- you know this forum better than I do... would I be well advised to start another thread in the Hardware subforum and link back to this one? After all, the issue I have now *is* rooted in hardware...

You can request that a mod/admin move it, though I don't think it would make a difference in terms of who sees it. To me, something like this is a "hardware" issue anyway, unless you are having difficulties with a specific audio/video program.

> If I could convince the system that there was something constantly plugged into that jack, I'd be completely fine... 

I'm still trying to figure out how you arrived at this conclusion.

---

### Post by starhawk2 on 2018-08-10
Re plug detection. The reason I'd be all set if the behavior were inverted goes something like this...

If there is no plug present, the audio stream basically goes nowhere anyways. It's effectively write-only memory, because there's nothing connected. No harm there, just a big pile of silence.

If there *is* a plug present, then the audio stream goes to whatever's plugged into the jack... rock on!

Given that line of reasoning, the *current* behavior doesn't make sense to *me* -- why actively block an audio stream when sending it to an empty socket is completely harmless anyways?

---

### Post by Gstrazds on 2018-08-10
> **starhawk2 said:**
> Since PulseAudio comes with Ubuntu, I suspect your problem is more a clash between the from-Ubuntu PulseAudio and the second version you installed separately. Mine is a hardware issue -- the jack does not physically support plug detection, and the computer refuses to route audio to a jack that it does not know for sure has a plug in it.

Could be wrong about your issue, though... especially since I haven't installed Audacity.

I read this - reinstalled the PulseAudio Volume Control; photo enclosed;

Then Tested, by clicking on the input device section of "Pulse volume control" selecting, internal microphone = unplugged; in this case; the video feed routed through to Audacity; it worked! then restarted - where the sound icon showed up, which it did not do yesterday. If it was broken; it is not broken now.

Audacity did not cause the sound problem - fussing with the sound card choices in Audacity; setting them to pulse needs to be done.

thanks for the help Adding the second instance of Pulse Audio should not have done anything except overwrite the first instance; Don't know. Alls well it works.

---

### Post by starhawk2 on 2018-08-10
PulseAudio notes on their website that installing a second instance of PulseAudio does exactly that -- it overwrites nothing, but the manual install takes operational precedence over the distro-installed version.

---

### Post by starhawk2 on 2018-08-11
Bump for great justice...

...I really just don't know what to do here.

---

### Post by starhawk2 on 2018-08-11
You know what? I'm tired of fighting this. I wanted the internal audio to work, but that's apparently not going to happen, and I have a Plantronics USB DSP v2 audio dongle (aka a USB sound card). **** it, I'm using brute force here -- namely, that dongle.

/thread

---

