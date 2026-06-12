---
title: "Firefox 3, flash, sound device"
date: 2008-04-28
forum: Multimedia Software
---

### Post by sparks88 on 2008-04-28
I'm currently running Hardy Heron.  I have installed flashplugin-nonfree. Flash videos play, but only through my speakers, I would prefer my headset. All other sound plays through my headset. I have tried disabling motherboard sound in my bios, at which point flash just produces no sound.

---

### Post by jonah1980 on 2009-03-13
> **sparks88 said:**
> I'm currently running Hardy Heron.  I have installed flashplugin-nonfree. Flash videos play, but only through my speakers, I would prefer my headset. All other sound plays through my headset. I have tried disabling motherboard sound in my bios, at which point flash just produces no sound.

yeah i've got kubuntu 8.10 and use a pair of usb speakers (samson studio dock) and i can set the default sounds to them and vlc/videos etc, music, but not firefox. so myspace, youtube and any flash stuff just comes out of lcd screen speakers which sounds naff...

flash or firefox should have a prefs tab to set the order of priority then if your usbs aren't plugged in it drops to other but if they are it pumps through them!

---

### Post by km0ti0n on 2009-05-27
BUMP!

I too have this problem.

So far no one's mentioned the version of ubuntu, I'm using 9.04 Jaunty Jackalope.

This is on 3 seperate machines, An old Single Core Intel P4, an AMD64 (using the 64bit flash workaround) and an Intel Core2 Duo.  All behave in the same manor.

The sound works perfectly in the headset if I use Skype, I'm able to select the Headset as the Output and Capture device, in skype's preferences.  

If I use System -> Preferences -> Sound and set all of the options to my Logitec Headset, mplayer and any other media player I test use the Headset, just as you would expect.  

But if I open firefox and a flash player has sound it comes out of Intel's onboard chip/card.

I tried a number of mods such as : 

[PHP]:~$ asoundconf list
Names of available sound cards:
Intel
Headset
:~$ asoundconf set-default-card Headset[/PHP]

And re-opening Firefox, even rebooted.  It doesn't change the source of the sound, it still come out of the onboard Intel and not the headset. 

Some people in versions pre 9.04 have suggested that the pavucontrol isn't installed, well this is my 3rd machine I've installed this week and it's deffo got pavucontrol installed by default. 

Using pavucontrol, you can clearly see that the Intel Chip is being used as the output card/device.

Another person has suggested using asoundconf-gtk, to me this is the same as using the [FONT="Courier New"]asoundconf set-default-card Headset[/FONT] As I have above.  Although I did try it on one of the machines, and it's no different.  

Another fix ([off these forums]("http://ubuntuforums.org/showthread.php?t=18926&highlight=mips")) was to mod the /etc/modprobe.d/alsa-base.conf and add an option that would stop The On board Intel chip from being set as the default (via setting it's index to anything but 0).  

ATM it's showing : 

[PHP]:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_audio[/PHP]

So I modded /etc/modprobe.d/alsa-base.conf and added the line : 

[PHP]options snd_hda_intel index=-2[/PHP]

And again, after a reboot it's still not playing the audio out of the headset.  

Although running : cat /proc/asound/modules again it looked no different; snd_hda_intel was still set to index=0.  So maybe I've not added the correct content to the alsa-base.conf.

As you can see I've been searching up and down to find a fix for this but not had any luck so far.  Looks like I'll be booting a windows box this eve. so I can watch BBC's iPlayer w/o waking the rest of the family.

Has ANYONE managed to get Flash to play audio via a USB headset?

Any help would be GREAT, I really hope I can fix this soon.  I'm so close to removing windows off all my machines.

Big thanks

Andy

---

### Post by km0ti0n on 2009-05-29
I just noticed that if I use the sound controls on the conputer the Gnome icon indicates the change in volume but the flash player doesn't change, the only way I'm able to change the volume of the flash player when it playing is via the PCM bar in the Volume Control, the master makes no difference.

It's as if Flash is by-passing the sound settings that are in gnome and using the hardware directally.

Any help would be fab.

---

### Post by realn on 2009-10-28
I managed to get USB output for flash.But now I DON'T.

 Here is how I did:

sudo rmmod snd_hda_intel
sudo rmmod snd_usb_audio

 Then make sure you have in /etc/modprobe.d/alsa-base 

options snd-usb-audio index=0

Then you do a sudo modprobe snd_usb_audio, and you end up with :

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Device [USB Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/cards
 0 [Device         ]: USB-Audio - USB Audio Device
                      Elite Silicon USB Audio Device at usb-0000:00:13.0-2, full speed

But, i really don't understand what changed, as I don't have any longer audio output in firefox/flash. I can output sound to the USB speakers in mplayer, in xmms, whatever, but no sound in Firefox/Flash.

 PLEASE HELP ---> EXTREMELY FRUSTRATED

 Thanks a lot!

---

### Post by realn on 2009-10-29
Bump, please help !

---

### Post by realn on 2009-10-30
It seems this is a SERIOUS issue, I found so many other posts with the same thing: every other application works OK with USB audio device, except for FF + flash. What is really frustrating, is that this thing worked for meuntil I did something. If I come to think about it, I might have uninstalled a package (it might have been libflashsupport because FF was crashing a lot).
 Don't know what to do, is there a way to track down this problem?

---

### Post by realn on 2009-10-30
I confirm that on a live usb stick kubuntu HH, on which i install firefox + adobe flashplugin 10 and on which I leave as soundcard only the USB one, it work PERFECTLY.

 Getting more and more confused. Please help !!

---

### Post by realn on 2009-12-03
Please, could someone help, I still have this issue.

---

