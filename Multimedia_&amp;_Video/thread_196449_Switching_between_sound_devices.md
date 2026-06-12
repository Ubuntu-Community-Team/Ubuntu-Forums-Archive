---
title: "Switching between sound devices?"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by EReckase on 2006-06-14
I have an HP Pavilion dv8225nr (one of the dv8000 series) with on-board ATI IXP sound.  It's definitely not the cleanest audio output, so I purchased a Sound Blaster Live (SB 0490) USB Sound Card, plugged it in, and attempted to get sound from it.  Needless to say, the process is far from straightforward, and it took a lot of fiddling to get it to play anything (some manual editing of the .asoundrc file was required, among other things.)

What I'm truly curious about is how to easily switch between these sound cards.  I don't plan on bringing my external sound card with me when I take my machine to different locations - I only plan on using that card when I'm at home.  What's the easiest way to configure my system to use the USB audio if it's plugged in, otherwise use the onboard audio?  Any advice would be valuable.

Thanks!

---

### Post by Sutekh on 2006-06-14
[quote=EReckase]I have an HP Pavilion dv8225nr (one of the dv8000 series) with on-board ATI IXP sound. It's definitely not the cleanest audio output, so I purchased a Sound Blaster Live (SB 0490) USB Sound Card, plugged it in, and attempted to get sound from it. Needless to say, the process is far from straightforward, and it took a lot of fiddling to get it to play anything (some manual editing of the .asoundrc file was required, among other things.)[/quote] It was probably because the SB card was identified as the second sound card, that you needed to create an .asoundrc file. Probably to map a virtual device to your hardware for the new card. What did you need in the file for the card to work? Something simple like this?
```
pcm.[B]<card_name>
[/B]{
     type hw
     card **<card_number>**
}

ctl.**<card_name>** 
{
     type hw
     card **<card_number>**
}
```  [quote=EReckase]
What I'm truly curious about is how to easily switch between these sound cards. I don't plan on bringing my external sound card with me when I take my machine to different locations - I only plan on using that card when I'm at home. What's the easiest way to configure my system to use the USB audio if it's plugged in, otherwise use the onboard audio? Any advice would be valuable.

Thanks![/quote] Are you using GNOME?
 
 You should be able to change the devices as neccessary from the System -> Preferences -> Sound menu.

---

### Post by EReckase on 2006-06-14
[QUOTE=Sutekh]It was probably because the SB card was identified as the second sound card, that you needed to create an .asoundrc file. Probably to map a virtual device to your hardware for the new card. What did you need in the file for the card to work? Something simple like this?
```
pcm.[B]<card_name>
[/B]{
     type hw
     card **<card_number>**
}

ctl.**<card_name>** 
{
     type hw
     card **<card_number>**
}
```   
[/QUOTE]

OK, here's what was in my .asoundrc file when I started messing around:
```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/xxxx/.asoundrc.asoundconf>

```

In the included file (.asoundrc.asoundconf), I had the following:
```
# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card IXP
defaults.ctl.card IXP
defaults.pcm.device 0
defaults.pcm.subdevice -1

```

If I change the defaults to the external card (as you are recommending, I think), what happens if it's not plugged in?

[QUOTE=Sutekh]
Are you using GNOME?
 
 You should be able to change the devices as neccessary from the System -> Preferences -> Sound menu.[/QUOTE]

I'm using Gnome.  If I don't do anything to my .asoundrc file, then changing the default audio device in Sys->Pref->Sound does not stick once selected (if I close the widget and reopen it, my original sound card is selected again.)

Thanks for your help (and any more you might be able to give.)

---

### Post by rikard_grankvist on 2006-06-18
Same thing for me. Using the gnome applet to select sound card doesn't stick. I wanna use /dev/dsp1, but it switches back to /dev/dsp when I close the window.

---

### Post by neymac on 2006-06-18
The same hapens in my Ubuntu Dapper.

---

