---
title: "Lubuntu not recognising sound card on startup"
date: 2015-05-20
forum: Multimedia Software
---

### Post by rgard37 on 2015-05-20
Probably the 10,000th version of this question so apologies if people are tired of answering it. 

Running Lubuntu 14.04.2 on an old Toshiba Satellite Pro A120 laptop. 

- If I boot to my desktop, there is no sound and if I open pavucontrol immediately, there is no sound card recognised or able to be selected. Only dummy outputs.

- If I refer to the Sound Troubleshooting Procedure; [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) and run the massive command in Step 4 in my terminal and then open pavucontrol the sound card is recognised and able to be selected.

- This laptop only has a single, integrated sound card installed so there's nothing else for the system to be able to detect. Information on it according to the output from the previously mentioned command used in the Sound Troubleshooting Procedure is as follows;
       description: Audio device
       product: NM10/ICH7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:27 memory:40080000-40083fff

- I don't know if it's relevant but I am running the machine with the Universal Firewall program enabled. I read on one possible fix for the problem that this could cause issues but if I disable the firewall, reboot and run the Step 4 command again the command no longer fixes the issue. If I re-enable the firewall, reboot and run the command, the issue is resolved. 

This is my first foray into Linux. I kind of understand the issue here but have no idea how to go about resolving it. The fact that the only thing so far that has resolved it is a long chain of commands is making it very difficult for me to understand the exact nature of the problem or how I should go about resolving it. I'd appreciate any and all input!

---

### Post by Vladlenin5000 on 2015-05-20
Hi and welcome.

Did it work in the live session?

---

### Post by rgard37 on 2015-05-20
I didn't run a live session, just wiped the computer and installed Lubuntu as it was basically a throwaway with Windows on it. Now it's working like a champ so I'm going to keep it. 

It did work the first time I installed Lubuntu, but I'm not sure how many re-boots afterwards it stopped working as I don't use it for music every time I power it up.

I still have the bootable USB that I used to install it, so I will boot to a live session from it later tonight and report back.

---

### Post by rgard37 on 2015-05-21
OK, if I boot to a live session the sound works 100% from the boot, no need to do or change anything.

First reboot after the live session; sound did not work and the Troubleshoot command did not fix the issue.

Reboot a second time, sound does not work as usual and the Troubleshoot command did fix the issue.

---

