---
title: "No sound on Mythbuntu"
date: 2009-10-10
forum: Multimedia Software
---

### Post by mythuser on 2009-10-10
Hi all,

I recently configured a spare PC for a media center and installed Mythbuntu 9.04. After the install, the sound did not function on the system; though prior to the Mythbuntu install, I had installed Ubuntu and the sound was working, so it's not a hardware issue.



Here is some information on the problem:


 
 ```
    $ aplay -l
**** List of PLAYBACK Hardware Devices **** 
```
 ```
    $ sudo asoundconf list
[sudo] password for user: 
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
CX8801 
```I've also tried purging:
 ```
 sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils 
``` ```
  $ sudo lspci -v
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
    Flags: medium devsel, IRQ 22
    I/O ports at c000 [size=256]
    Capabilities: [c0] Power Management version 2
    Kernel modules: snd-via82xx 
```I've tried countless other methods, but it's really just me guessing and seeing what happens.. not very effective so far. 

Any advice on the issue is appreciated!!!


-Mythbuntu user

---

