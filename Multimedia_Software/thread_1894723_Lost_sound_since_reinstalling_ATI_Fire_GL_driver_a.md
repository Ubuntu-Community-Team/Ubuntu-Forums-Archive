---
title: "Lost sound since reinstalling ATI Fire GL driver and 'aticonfig --initial'"
date: 2011-12-13
forum: Multimedia Software
---

### Post by Dáire Fagan on 2011-12-13
I installed my new card a few days ago and everything has been fine sound wise, but I received an error in WINE so thought I'd try reinstalling the driver.

I first uninstalled it and attempted to restart but just saw lots of white text that eventually stalled so I hard reset. I got into Ubuntu recovery mode and started in failsafe graphics mode where I reactivated the driver.

After a reboot I did an 'aticonfig --initial' in terminal and restarted again to discover I had no sound.

Notably my sound in Windows XP has also stopped working which I initially feared meant the sound had a hardware failure but I'm now hoping it has somehow just gotten mixed up.

My new HD Radeon 4650 has sound capability but only in HDMI mode, and I use the VGA port. Perhaps somehow the sound is trying to go through HDMI?
```


[LIST=1]
[*]dusf@banshee:~$ sudo aplay -l
[*][sudo] password for dusf:
[*]**** List of PLAYBACK Hardware Devices ****
[*]card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
[*]  Subdevices: 1/1
[*]  Subdevice #0: subdevice #0
[*]card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
[*]  Subdevices: 1/1
[*]  Subdevice #0: subdevice #0
[/LIST]

```Already tried a cold restart.

Any suggestions?

Xubuntu 11.04
x86
Xfce
Dell E520

---

### Post by Dáire Fagan on 2011-12-13
I installed my new card a few days ago and everything has been fine  sound wise, but I received an error in WINE so thought I'd try  reinstalling the driver.

I first uninstalled it and attempted to restart but just saw lots of  white text that eventually stalled so I hard reset. I got into Ubuntu  recovery mode and started in failsafe graphics mode where I reactivated  the driver.

After a reboot I did an 'aticonfig --initial' in terminal and restarted again to discover I had no sound.

Notably my sound in Windows XP has also stopped working which I  initially feared meant the sound had a hardware failure but I'm now  hoping it has somehow just gotten mixed up.

My new HD Radeon 4650 has sound capability but only in HDMI mode, and I  use the VGA port. Perhaps somehow the sound is trying to go through  HDMI?
```


[LIST=1]
[*]dusf@banshee:~$ sudo aplay -l
[*][sudo] password for dusf:
[*]**** List of PLAYBACK Hardware Devices ****
[*]card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
[*]  Subdevices: 1/1
[*]  Subdevice #0: subdevice #0
[*]card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
[*]  Subdevices: 1/1
[*]  Subdevice #0: subdevice #0
[/LIST]
 
```Already tried a cold restart.

Any suggestions?

Xubuntu 11.04
x86
Xfce
Dell E520

---

### Post by Dáire Fagan on 2011-12-13
Xubuntu 11.04
  x86
  Xfce
  Dell E520
  
I installed my new card a few days ago and everything has been fine  sound wise, but I received an error in WINE so thought I'd try  reinstalling the driver.
 
 I first uninstalled it and attempted to restart but just saw lots of  white text that eventually stalled so I hard reset. I got into Ubuntu  recovery mode and started in failsafe graphics mode where I reactivated  the driver.
 
 After a reboot I did an 'aticonfig --initial' in terminal and restarted again to discover I had no sound.
 
 Notably my sound in Windows XP has also stopped working which I  initially feared meant the sound had a hardware failure but I'm now  hoping it has somehow just gotten mixed up.
 
 My new HD Radeon 4650 has sound capability but only in HDMI mode, and I  use the VGA port. Perhaps somehow the sound is trying to go through  HDMI?
 ```

 
[LIST=1]
[*]dusf@banshee:~$ sudo aplay -l
[*][sudo] password for dusf:
[*]**** List of PLAYBACK Hardware Devices ****
[*]card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
[*]  Subdevices: 1/1
[*]  Subdevice #0: subdevice #0
[*]card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
[*]  Subdevices: 1/1
[*]  Subdevice #0: subdevice #0
[/LIST]
  
``` Already tried a cold restart.
 
 Any suggestions?
 
 Xubuntu 11.04
 x86
 Xfce
 Dell 520

---

### Post by Dáire Fagan on 2011-12-13
Xubuntu 11.04
    x86
    Xfce
    Dell 520
    
 I installed my new card a few days ago and everything has been fine  sound wise, but I received an error in WINE so thought I'd try  reinstalling the driver.
   
   I first uninstalled it and attempted to restart but just saw lots of  white text that eventually stalled so I hard reset. I got into Ubuntu  recovery mode and started in failsafe graphics mode where I reactivated  the driver.
   
   After a reboot I did an 'aticonfig --initial' in terminal and restarted again to discover I had no sound.
   
   Notably my sound in Windows XP has also stopped working which I  initially feared meant the sound had a hardware failure but I'm now  hoping it has somehow just gotten mixed up.
   
   My new HD Radeon 4650 has sound capability but only in HDMI mode, and I  use the VGA port. Perhaps somehow the sound is trying to go through  HDMI?
   ```

   
[LIST=1]
[*]dusf@banshee:~$ sudo aplay -l
[*][sudo] password for dusf: 
[*]**** List of PLAYBACK Hardware Devices ****
[*]card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
[*]  Subdevices: 1/1
[*]  Subdevice #0: subdevice #0
[*]card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
[*]  Subdevices: 1/1
[*]  Subdevice #0: subdevice #0
[/LIST]
    
```
   
   Already tried a cold restart.
   
   Any suggestions?
   
   Xubuntu 11.04
   x86
   Xfce
   Dell E520

---

### Post by overdrank on 2011-12-13
Hi and please do not create multiple threads on the same issue. Threads merged.

---

### Post by Dáire Fagan on 2011-12-13
Resolved: selected the Sigmatel Onboard sound in Windows XP Control Panel (Audio Tab), and did the same in Xubuntu's alsamixer making sure 'PCM' was at 100%.

Somehow the IRQ order got changed and the Onboard sound was moved down priority.

---

### Post by Dáire Fagan on 2011-12-13
Resolved: selected the Sigmatel Onboard sound in Windows XP Control  Panel (Audio Tab), and did the same in Xubuntu's alsamixer making sure  'PCM' was at 100%.

Somehow the IRQ order got changed and the Onboard sound was moved down priority.

---

