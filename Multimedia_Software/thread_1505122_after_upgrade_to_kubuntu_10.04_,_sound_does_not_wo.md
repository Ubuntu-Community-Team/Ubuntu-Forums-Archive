---
title: "after upgrade to kubuntu 10.04 , sound does not work"
date: 2010-06-08
forum: Multimedia Software
---

### Post by awsffa71 on 2010-06-08
On kubuntu 9.10 my sound was working fine. less than a week ago i upgraded to kubuntu 10.04.  After the upgrade the sound did not work at all.  i made sure that my volume was turned up and that my volume was not on mute. so far i have gotten no sound on 10.04

I upgraded through the update manager.  Dont know where to start please help.

:confused:

---

### Post by Yellow Pasque on 2010-06-08
First, let's make sure you're using the corrrect kernel and that the sound driver is loading. Post output of these commands:
```
aplay -l
uname -a
```

---

### Post by Algot Runeman on 2010-06-26
same lack of sound on Asus netbook 1101 HAB

chaunce@roadshow-asus:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chaunce@roadshow-asus:~$ uname -a
Linux roadshow-asus 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
chaunce@roadshow-asus:~$ 

Thanks for any suggestions
--Algot

---

### Post by lidex on 2010-06-26
*algot* try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 kdesudo kate /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=lifebook  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by Algot Runeman on 2010-06-27
lidex, Thank you for your clear directions.

I set the speakers to 100% in alsamixer (wasn't sure if needed)

After restart of computer, sound is working.

Where should this information go from here, so that a Kubuntu upgrade will fix the problem generically? It would seem that the hardware recognition system during installation needs to be modified so that the proper options line is added to the configuration file. As noted before, sound was working before upgrade to 10.04 which suggests something slipped out of the process. Although, maybe it was an upgrade vs. install issue. I installed Kubuntu 9.10 initially and did the upgrade to 10.04.

Do you know if there is an appropriate bug report that can be referred to this thread for guidance toward a fix?

In any event, MY problems are fixed. Thanks again.
--Algot

---

