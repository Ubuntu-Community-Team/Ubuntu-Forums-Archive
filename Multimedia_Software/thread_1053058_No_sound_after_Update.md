---
title: "No sound after Update"
date: 2009-01-28
forum: Multimedia Software
---

### Post by timmil on 2009-01-28
Well let me begin by saying thank you to everyone here in the forums as I have always been able to find the solution in the previous posts. However, now I am stumped.

This morning I was notified that updates were available, I reviewed the updates and noticed that many were to PulseAudio. I didn't think anything about it and went ahead and applied the updates. Upon completion it called for a reboot, which I did and now no sound.  I checked all the standard things, lsmod shows the driver is loaded, aplay -l shows the card as available, volume is set to 100%, but still nothing. I have no idea where to turn on this one being it was working before the update.

Did anyone else get these updates today? Did you have problems as well?

Thanks for you help!
-Tim

---

### Post by maxmingus on 2009-01-28
I have the same problem. My system has a built in Intel sound card and an added Creative labs Audigy 2 sound card. When I originally installed Kubuntu, I had a similar problem and the solution turned out to be installing "asoundconf-gtk", which allowed me to set the Audigy 2 as the default sound card. This time, no luck. I have checked and volume on all the PCM settings is on 100%

Max

---

### Post by timmil on 2009-01-28
THat is the same exact setup that I have. Intel on-board (disabled in bios) and snd_via82xx is blacklisted, and nothing. Dead silence. Not sure where to turn or what to do next.

- Tim

---

### Post by rigelstar on 2009-01-28
I did the same update and my sound is gone - My card is a Audigy 2 ZS and I have never had sound problems before.  Something introduced in the last update had killed sound for this card.  The kernel was updated as well in the latest series of updates.  I will boot into the older kernel and let you know if I have sound.

---

### Post by rigelstar on 2009-01-28
I reverted to the previous kernel and my sound is back.  The problem is with the kernel upgrade not the pulse audio upgrade.

---

### Post by timmil on 2009-01-28
That works for me to. So kernel 2.6.27-11 has sound issues.

---

### Post by maxmingus on 2009-01-28
Same thing. Rebooted with kernel 2.6.27-9 and my sound is back. 

Thanks rigelstar.

---

### Post by sickenmcsluggets on 2009-01-28
> **rigelstar said:**
> I did the same update and my sound is gone - My card is a Audigy 2 ZS and I have never had sound problems before.  Something introduced in the last update had killed sound for this card.  The kernel was updated as well in the latest series of updates.  I will boot into the older kernel and let you know if I have sound.

I have the same card and the same problem. Guess I'll boot from the earlier kernel.

---

### Post by mc4man on 2009-01-28
Atm I'm not inclined to upgrade the kernel (have audigy 2 Zs) though curiosity will probably get the better of me.

I noticed one line in the upgrade
 > ALSA: emu10k1 - Add more invert_shared_spdif flag to Audigy models

Possibly the output has been switched to spdif or the Audigy Analog/Digitial output Jack has switched. (On my card it needs to be on for sound.
It can be found in the full alsamixer as Audigy A (00 is on) or in 'switches' (d. left click on speaker icon -> preferences and add the switch, then in 'switches' check or uncheck depending on audigy card


To get full alsamixer if not available
to find card #, usually 0
```
cat /proc/asound/cards
``` 

```
alsamixer -c [COLOR="Red"]0[/COLOR]
```

---

### Post by S0m3th1ngw13rd on 2009-01-28
After update this morning I had same problem.  I used the directions on the following thread and upon reboot sound was restored. Don't know if it will be your solution also, it worked here though.

Did this first:        [http://ubuntuforums.org/showthread.php?t=870001&highlight=creative+drivers](http://ubuntuforums.org/showthread.php?t=870001&highlight=creative+drivers)

after this sound in rythmbox was scratchy.  So I did this:

[http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+issues](http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+issues)

---

### Post by mc4man on 2009-01-28
Can confirm that with an audigy 2 Zs the kernel update does kill the sound.

Sound was restored by resetting the 'Analog/Digitial Output Jack' switch to off.
Previous to update it needed to be on, so it's use has been 'inverted' as per the update info.

---

### Post by rigelstar on 2009-01-28
> **mc4man said:**
> Can confirm that with an audigy 2 Zs the kernel update does kill the sound.

Sound was restored by resetting the 'Analog/Digitial Output Jack' switch to off.
Previous to update it needed to be on, so it's use has been 'inverted' as per the update info.

I confirm that this resolves the problem as well.

---

### Post by sickenmcsluggets on 2009-01-28
> **mc4man said:**
> Can confirm that with an audigy 2 Zs the kernel update does kill the sound.

Sound was restored by resetting the 'Analog/Digitial Output Jack' switch to off.
Previous to update it needed to be on, so it's use has been 'inverted' as per the update info.
So, how does one reset this Analog/Digital Output Jack switch?

---

### Post by mc4man on 2009-01-28
I sorta described in post #9
2 ways, either open the full alsamixer and with the arrow key scroll to the setting, m on your keyboard enables or disables. (Audigy A
Or add the 'switch' to what you see when you d. left click on the speaker icon next to the date.

Take a look in that post for how on both ways

screen of alsamixer at spot

---

### Post by sickenmcsluggets on 2009-01-29
Thanks, was having trouble finding the right spot in alsamixer. Sounds back.

---

### Post by earlyberd on 2009-01-29
I updated this morning, and it appears that I have sound in all of my media players, like Rhythmbox and VLC, but the Flash player and system sounds are broken. Furthermore, booting into previous kernels does not help.

I think it's a pulseaudio issue, but I haven't the slightest clue how to revert back to the previous version I had installed.

---

### Post by a-musing amazon on 2009-01-29
The whole business seems very odd. 

When I updated my system sounds and my flash sound worked OK but Rhythmbox just froze when I tried to play tracks (otherwise it was responding OK). Gxine also froze when I tried to play an Ogg in Nautilus. I have a onboard Realtek ALC889A.

I rebooted into the prevous kernel and that worked OK (though my atheros network drivers no longer worked: I usually have to recompile some modules when I change a kernel, but I would have expected them to work OK once I had done that). So that wasn't much use. 

Rebooted again into the new kernel version and everything was working again.

---

### Post by walom on 2009-01-30
Lost sound with the previous updates but unchecking the previously checked Analog/Digital output jack solved it. Thanks.

---

### Post by TNFa on 2009-01-30
It may be silly registering just to say thanks, but hell yeah this little checkbox solved my sound issues with the new kernel as well!

---

### Post by GrfyGrumpyBear on 2009-01-30
There's no need to use alsamixer. If you're using Gnome, you can use the Gnome Volume Control interface. Just right click on the speaker icon in the system tray, click "Open Volume Control," then making sure that your card is selected in the "Device" section, click "Switches." If "Audigy Analog/Digital Output Jack" is selected, just de-select it, done.

If you don't see that switch, then hit "Preferences" and just choose it in the window that comes up.

---

### Post by terryscott on 2009-01-30
Hi, 
Same problems, same card,creative soundblaster audigy 2 on Intrepid (8.10) following kernel update from 2.6.27-9 to 2.6.27-11. Following this thread, also resolved by resetting the 'Analog/Digitial Output Jack' switch to off.
Thanks 

Could this by any chance have resolved an identical problem I had in Hardy (8.04), again following a kernel update, from 2.6.24-19 to 2.6.24-21. Intrepid followed soon after so went for that instead to resolve the problem.

---

### Post by SirBismuth on 2009-01-30
Thanks for recommending resetting the 'Analog/Digitial Output Jack' switch to off.  All is well on the sound front now! :D

:popcorn:

B

---

### Post by firewings on 2009-01-30
I have the same problem described by earlyberd after the last update: sound correct in rhythmbox, totem but no sound from firefox with flash plugin or system sounds. I also tried the proposed workaround (Analog Audigy checkbox), but nothing; my soundcard is an Audigy2. Thanks to all

---

### Post by blfgomes on 2009-01-31
> **SirBismuth said:**
> Thanks for recommending resetting the 'Analog/Digitial Output Jack' switch to off.  All is well on the sound front now! :D

:popcorn:

B
That solved it for me too! Thanks for posting the solution here, it made my life a lot easier!

---

### Post by SegaBoy0 on 2009-02-01
> **blfgomes said:**
> That solved it for me too! Thanks for posting the solution here, it made my life a lot easier!

Fixed it for me too!  Thanks everyone...these forums are priceless :D

---

### Post by nickby on 2009-02-01
> **GrfyGrumpyBear said:**
> There's no need to use alsamixer. If you're using Gnome, you can use the Gnome Volume Control interface. Just right click on the speaker icon in the system tray, click "Open Volume Control," then making sure that your card is selected in the "Device" section, click "Switches." If "Audigy Analog/Digital Output Jack" is selected, just de-select it, done.

If you don't see that switch, then hit "Preferences" and just choose it in the window that comes up.

Thanx it worked for me too

---

### Post by Chachee on 2009-02-02
Confirm fix with switch back to analog out from digital.

Thanks.

JT

---

### Post by Ameneon on 2009-02-03
Ok now I feel stupid but for meeeeeeeee toooooo (couldn't help it) toggling the analog switch did the trick (another Audigy 2 ZS here). Thanks a ton!

---

### Post by phenix. on 2009-02-14
hello all

i just want to say thankx to every one involved in the forms. i am new to ubuntu and i love the whole thing so far. i do need help with some thing thoe. i know zilch about how to program and how ubuntu works and i am having the same problem as the rest of you but it is more complex for me i dont know where to look to find this switch. i am running ubuntu studio with the latest kernel update.

cheers :confused:

---

### Post by forestwalkerjoe on 2009-02-14
I tried a lot of things to FIX this problem too.. the minute i got the UPDATE .. all my sounds when out.. i was able to get system sounds back.. then play music on my system.. but NO FLASH.. 
here is the solves that worked for me. 
[URL="http://ubuntuforums.org/showthread.php?t=1068574&highlight=sound+flash"]
SOLVES[/URL]

Go slowly.. dont skip anything on the 3erd solve.. it really SHOULD work.. if the 3erd one doesnt do it.. try ONE or TWO.. these will work on some systems. 
GOOD LUCK. 

FWJ

---

### Post by jfrancl on 2009-02-22
I have had sound after the updates a couple of weeks ago, but it suddenly disappeared yesterday in the middle of what I was doing. I get the bongos at login, but that is it for system sounds. I can hear quicktime videos and play mp3's. I de-installed and re-installed Flash in the latest kernel(as that seemed to be my major hangup), but to no avail. Previous kernels don't restore my sound, but a bunch of error messages fly by during bootup. This doesn't happen in the latest kernel. I've read the other posts and threads, but haven't tried them yet. I thought I'd post this as additional information. I have a Creative Audigy 2 sound card, Gigabyte motherboard and 3.2GHz Intel processor(all 5 years old). I'm on Intrepid Ibex. My usual problem after some updates is that GoogleEarth quits working, but it always comes back after a few days, so I'm sure the sound problem will be fixed soon.

---

### Post by jfrancl on 2009-02-22
Addendum to previous post. I unchecked the analog/digital setting and lost what little sound I had. I rebooted and same thing. I rechecked the analog/digital switch, and now have full sound again. But I also noticed there was a switch for external amplifier (which I have), so I checked that as well. Hope this helps someone. It seems that all computers do not act the same way...

---

