---
title: "Nvidia drivers cause system crash"
date: 2015-07-30
forum: Multimedia Software
---

### Post by alan64 on 2015-07-30
When I install Nvidia 331.113 drivers, my single-boot Macbook Pro 5,2 works perfectly but crashes after 1 to 2 minutes and has to be switched on again.

Graphics card: [COLOR=#008000]NVIDIA Corporation G96M [GeForce 9600M GT] (rev a1)[/COLOR]

I have identified various bits of text in /var/log/syslog that may indicate what is causing these crashes:

Exhibit A:
[COLOR=#008000]Jul 30 09:33:43 i kernel: [    4.255718] nvidia: module license 'NVIDIA' taints kernel.
Jul 30 09:33:43 i kernel: [    4.255720] Disabling lock debugging due to kernel taint
Jul 30 09:33:43 i kernel: [    4.283894] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
Jul 30 09:33:43 i kernel: [    4.293191] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 20
Jul 30 09:33:43 i kernel: [    4.293211] nvidia: probe of 0000:00:03.5 failed with error -1[/COLOR]

Exhibit B:
[COLOR=#008000]Jul 30 09:33:44 i kernel: [    6.321417] ACPI Warning: \_SB_.PCI0.RP01.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)[/COLOR]

This earlier bit might mean something as well. It must have been generated just as Nvidia driver install was finishing, but before restart:
[COLOR=#008000]Jul 30 09:26:16 i nvidia-persistenced: Failed to query NVIDIA devices. Please ensure that the NVIDIA device files (/dev/nvidia*) exist, and that user 117 has read and write permissions for those files.
Jul 30 09:26:16 i nvidia-persistenced: The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced
Jul 30 09:26:16 i nvidia-persistenced: Shutdown (17145)
Jul 30 09:26:16 i kernel: [ 1851.487956] init: nvidia-persistenced main process (17145) terminated with status 1[/COLOR]

Without Nvidia drivers, I have serious problems with Googlemaps, playback of video files and resume from suspend.

---

### Post by SeijiSensei on 2015-08-03
Did you install the drivers from the Ubuntu repositories?  From the xorg-edgers PPA?  Or from the NVIDIA site?  That should always be your last resort.

If you installed the drivers from the NVIDIA site, try reversing what you did, then run
```

sudo apt-get update
sudo apt-get install nvidia-331

```

---

### Post by alan64 on 2015-08-03
Usually I install Nvidia drivers from the Gnome GUI marked "additional  drivers." Both 331.113 and 304 give the same result: video playback  works perfectly, suspend/resume works perfectly, but my computer  completely shuts off after one or two minutes. Today I also tried  Nvidia-340 using terminal commands similar to the ones you posted. Same  result. I have also tried to install the 173 "legacy" drivers, but the  GUI can't even get them to download.

In order to avoid an OS  reinstall, it is necessary to start my computer and, as quickly as  possible before it crashes, enter the following 2 commands: **sudo mount -o remount,rw /** and then **sudo apt-get purge Nvidia***  Today, however, it crashed before the second command had finished  executing, so my install was broken beyond repair (no mouse, no  keyboard). If I could just get some version of the Nvidia drivers  running, my computer would work more or less perfectly.

---

### Post by Yellow Pasque on 2015-08-04
[http://gizmodo.com/5107277/do-the-new-macbook-pros-have-faulty-nvidia-graphics-cards](http://gizmodo.com/5107277/do-the-new-macbook-pros-have-faulty-nvidia-graphics-cards)

---

### Post by NathanRodriguez on 2015-08-05
My card was behaving badly due to temperature issues: the fan was stopping from times to times. A dust cleanup and lubrication solved the issue.

---

### Post by alan64 on 2015-08-06
You might be onto something, Temüjin. Under Mac OS, this machine also didn't work that well. Video playback was good, but resume from suspend always caused an instant crash. Crashes were also common during boot. Installing Ubuntu and wiping out Mac OS made it a bit more stable, and at first even video playback was good, but resume from suspend never worked except with Nvidia drivers, which brought back the sudden crashing problem.

Oh well, I just tried Debian, but that didn't work, so I'll go back to Ubuntu, with its lagging video and resume to black screen. This machine still sometimes crashes during boot, so it really would be nice to solve this Nvidia problem, as Nvidia drivers are the only way I know of to fix suspend/resume and avoid booting up all the time....

---

