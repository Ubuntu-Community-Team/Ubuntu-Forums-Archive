---
title: "[SOLVED] Skype sound problems"
date: 2008-08-05
forum: Multimedia Software
---

### Post by grashdur on 2008-08-05
It looks like most people using VOIP on Ubuntu are using Skype. Has anybody found a way to solve the various sound problems? 

To be specific, on Hardy Heron I hear no ring on incoming calls. (The relevant ring file is there; and when I start Skype I hear the usual "swoosh" sound signifying startup.) I do not have this problem on my laptop, which still uses Gutsy Gibbon.

There is no way to adjust sound levels, which is frustrating. The master control for Ubuntu has no effect on Skype, and Skype has no volume control of its own.

I hear sound only on one side of my USB headset. (Realistic Gigaware)

---

### Post by grashdur on 2008-08-06
I seem to have fixed the ringing issue -- now it seems to ring just fine. I went into Options > Sound Devices and changed the Ring setting to something else. (But I know I tried all these settings before; I don't know why it worked just now.)

But still no way to adjust volume levels during a call. Anybody found a solution to this?

---

### Post by grashdur on 2008-08-06
The solution was hiding under my nose the whole time: Just right-click on the speaker icon on the system tray, and select “Open Volume Control,” then in this menu go into File > Change Device and select the device (USB headset). At this point, it's possible to change the volume! This menu must be new in Hardy Heron, because I think I already tried to do this in GG. 

I hope this posting is helpful to someone, as it's really not obvious how to do this.

---

### Post by oooh on 2008-09-04
Try to read this: [http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html)

I can currently hear & speak, but CAN NOT SIMULTANEOUSLY use Skype with any other device trying to access the audio system.

My advice: enable the mic tab (capture tab) in the control volume of hardy heron. That IS VERY IMPORTANT thing to do, the first, in fact ! Check your mic volume in ubunty volumen control.

In addition, you can test your mic using the Aplications-sound-sound recorder, or System-preferences-sound... where there is a tab dedicated to test all your sound system

---

### Post by grashdur on 2008-09-05
Thank you very much for the info. I just bookmarked the Skype page you suggested. This is all a bit technical for me; I'll try coming back to it some time this weekend. 

So far I've found that I can switch to my USB headset in the HH master volume control panel, but whenever I try to touch the sound levels to change them, they suddenly drop to zero and don't want to turn on again -- which of course is annoying if I just want to adjust sound level during a conversation.

Obviously there's plenty more for me to explore here. Thanks for your input.

---

### Post by grashdur on 2008-09-07
I too have found that Skype tends to conflict with other programs on sound output. I was able to solve most of these problems by going into System > Preferences > Sound, and under "Default Mixer Tracks" at the bottom I switched to an OSS option. But today I noticed that I still have a problem of no inbound sound on Skype if I use Sound Preferences to switch my music output over to my USB headset (which Skype also uses). So I have to switch back to my earlier setting, then restart Skype and the music player, before I can get the sound on Skype and the music player to stop conflicting.

I studied that sound options page on the Skype website (link above from ooh), but it doesn't seem to relate to Ubuntu Linux as I see it on my computer, so I couldn't make heads or tails of their suggestions.

---

### Post by zerubbabel on 2008-09-10
I am trying to use a bluetooth headset with Skype, and the test call worked the first time I tried it, but then when I tried to make an actual SkypeOut call, immediately a window popped up saying "conference call ended" (and I wasn't even trying to make a conference call). After that, I tried the test call again, which failed in the same manner. After a reboot, and trying the test call, it now reports every time, "Conference call, 1 participant", and I'm STILL not trying to make a conference call. In fact, I've never tried to make a conference call. Does anyone know what is going on?

---

### Post by grashdur on 2008-09-11
Totally stumped on that one. But can you still call normally, even though it's called a conference call instead of a phonecall?

---

### Post by zerubbabel on 2008-09-11
No, it doesn't actually dial the call, or at least, I hear and see no evidence of it.

---

### Post by waffen on 2008-09-17
I dont know if you try this before, but for me resolve all the problems then I read before:

Start first Skype!

before other program when the login are finished... #-o

---

### Post by grashdur on 2008-09-17
Won't work for me, Mario, as I have Skype set to start automatically at login. Hopefully it will help somebody though. At this point I don't have many sound problems with Skype: It's just hard to adjust sound during a call, and Skype has no sound while Totem Movie Player is playing (though it's fine now with Rhythmbox). Plus, of course, the fact that incoming sound only works on one side of the headset -- but I seem to be getting used to that already.

One thing to keep in mind, for anyone else with continuing Skype sound problems: Skype is not yet compatible with ALSA, so switching settings to OSS does solve some of my problems. (Although ALSA apparently does have some sort of OSS emulation available.)

---

### Post by grashdur on 2008-09-20
For anyone else still having these problems, I'd like to summarize what's working for me so far: I've fiddled around a lot with Skype on Linux in the past couple months. I've read that Skype for Linux is not yet compatible with ALSA, only with OSS (although ALSA may have some OSS emulation).

What's working best for me now (whether it makes any logical sense or not):
[IMG]http://scott2.airpost.net/Sound%20Preferences%20that%20work%2008-08.png[/IMG]

And, important sound settings for the headset (and for OSS) can be found in [master volume control icon] > [right-click:] Open Volume Control > File > Change Device – keep in mind that this control box can *mute* sound, particularly *on the one side of the stereo headset with which Skype works*. So if you're getting no sound on Skype, definitely look at this little control panel.

And in Skype's Options, you can fiddle with Sound Devices, though that seems to help less in my case.

The problems I still have are: Inability to easily change volume levels *during* a call, and sound only one one side of my USB headset. Basically, I'm able to live with these problems for now. Also, Skype incoming sound is disabled while playing Totem Movie Player, or while playing Rhythmbox with sound routed to my USB headset.

---

### Post by eye208 on 2008-09-20
> **grashdur said:**
> One thing to keep in mind, for anyone else with continuing Skype sound problems: Skype is not yet compatible with ALSA
This is not true.

The Linux sound setup help page on the Skype website is totally out of date and needs to be updated. In fact Skype uses **only** ALSA, at least since Skype 2.0. It's pretty obvious if you look at the sound options page of the program. There you can choose between ALSA's "default" device and one or more "hw" and "plughw" devices provided by ALSA depending on the soundcards in your computer. All OSS devices such as "/dev/dsp" have disappeared from the menu.

The problem is that since Ubuntu 8.04 all sound is routed through PulseAudio first, i.e. Skype "thinks" it is talking to ALSA but in fact it is not. This is very likely to be the cause of your Skype sound problems. Remove PulseAudio (as described [here](http://ubuntuforums.org/showthread.php?t=885437)), and all these troubles will go away instantly.

---

### Post by grashdur on 2008-09-23
I can vouch for eye208's fix, as I just tried it and it worked. Click the link to his how-to in his posting just above (it's very clear and simple to follow). 

The only problems I still have remaining now, which are pretty minor: 
* Skype sound is disabled if I get an incoming call while my music sound output is rerouted to my headset.
* Sound from Flash (for playing YouTube videos on Firefox, for example) still goes only to my speakers, and cannot be routed to my headset.
* With Skype I have sound only on one side (though this is an extremely minor issue and I don't really care about this any more).

---

### Post by swoody on 2008-09-23
Wow, good post :) Just solved one of my problems.

---

### Post by rainwalker on 2008-09-23
Sound (usually) works fine for me, although it stutters a little. I know it's because it's going through PulseAudio, but I refuse to remove Pulse because I like it too much.

Any idea when Skype will work properly with PulseAudio? Is it even planned?

---

### Post by fh_scott on 2008-09-24
> **grashdur said:**
> 
* Skype sound is disabled if I get an incoming call while my music sound output is rerouted to my headset.


I think that's an ALSA issue.  Only one app can have the device at a time.  I finally went to a bluetooth headset because of this (and your other reason).


> **grashdur said:**
> 
* With Skype I have sound only on one side (though this is an extremely minor issue and I don't really care about this any more).

Because of the above issue, I initially installed a pair of USB speakers to be my "skype speakers" so they wouldn't be blocked if something else was playing audio on the main soundcard, but for the life of me I could only get sound out of the left speaker with skype.  Bluetooth headset dedicated to skype (and nuking pulse audio) solved those problems (and created one or two new ones).

-scott

---

### Post by eye208 on 2008-09-25
> **fh_scott said:**
> I think that's an ALSA issue.  Only one app can have the device at a time.
It's an ALSA **configuration** issue. Any ALSA device can be configured to accept multiple clients.

---

### Post by markbuntu on 2008-09-25
You can use skype with pulseaudio, or I can at least. It makes it very easy to switch mics and speakers/headset around.

 I wrote a guide here:


[http://ubuntuforums.org/showthread.php?t=937323](http://ubuntuforums.org/showthread.php?t=937323)

---

### Post by waffen on 2008-10-14
> **waffen said:**
> I dont know if you try this before, but for me resolve all the problems then I read before:

Start first Skype!

before other program when the login are finished... #-o
Hello,

My last post have a problem.. only works some times and when other devices use the sound Skype dont work again.

But.. I reinstall my Ubuntu, fresh install (for another reason) and I have the default params, I use ALSA and Open Skype and click the S icon bottom left>Options>Soound Devices. Setup the default options for all and the sound and micro works again, well in all cases.

I use a Dell Latitude D630 Core 2 Duo, 2GB RAM, my lspci command is:

mario@mario-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 135M (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

---

### Post by detroit/zero on 2008-10-14
I've never been able to get Ubuntu Skype to capture my microphone. Between that and the fact that Skype on Ubuntu is rather plain and option-free compared to the current version for Windows, adds up to one of the very few reasons I even keep Vista on my computer.

---

### Post by swissz on 2010-08-11
Hi!
I have Karmic Koala and I had no ringing in and other notification sounds in Skype. I found out, that their volume was set to zero in the system settings.
So, the solution is to go System-> Preferences-> Sound preferences -> Sound effects and set the "Alert volume" from zero to something higher. Thats it. Now it is working!
The alert volume was probably set to zero when the login sound of Ubuntu was deactivated.

---

