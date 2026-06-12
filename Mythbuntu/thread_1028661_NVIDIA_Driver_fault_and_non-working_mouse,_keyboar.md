---
title: "NVIDIA Driver fault and non-working mouse, keyboard or remote"
date: 2009-01-02
forum: Mythbuntu
---

### Post by doveman on 2009-01-02
I've installed MythTV on top of Ubuntu 8.10 and that's working OK, except for the remote for my Nova-T 500 which I haven't worked out how to set up yet.

I thought I'd try Mythbuntu to see if it would save me some effort but I've not had much luck so far. Firstly, when the install starts, the windows are too big for the screen so I couldn't see the parts where I needed to click. I cancelled the install and installed the Nvidia 173 driver from the Live desktop and then I could increase the resolution and see everything.

Once the install finished, it doesn't detect my Nova-T 500 in the setup so I rebooted but it came up with the following error:
Ubuntu is running in low graphics mode
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module
(EE) NVIDIA(0): Aborting
(EE) Screen(s) found but none have usable configuration

and the mouse and keyboard weren't working in the graphical screen. I changed the xorg.conf to use the NV driver and rebooted and got the Mythbuntu main menu but the mouse and keyboard were still not working.

I've attached the xorg files for the NVIDIA driver boot. Obviously I need to go back and setup MythTV with my Nova-T (I recall that even under Ubuntu it didn't detect it until after a reboot), but I don't think that will sort out the NVIDIA driver problems or the non-working mouse, keyboard or remote. Please let me know if I can supply any other log files that will help identify what's causing these problems.

EDIT: Sorry, I didn't realise the files hadn't uploaded.

---

### Post by doveman on 2009-01-03
Just a couple of pieces of further info. I've got an FX5600 graphics card, a PS2 mouse and keyboard and the Mythbuntu version number is as below. I haven't found a way to run the backend setup yet as the mouse and keyboard are still not working. Is there a backend config file that I can copy from my working Ubuntu/MythTV system to the Mythbuntu one?

$ apt-cache policy mythtv-common
mythtv-common:
  Installed: 0.21.0+fixes18722-0ubuntu1
  Candidate: 0.21.0+fixes18722-0ubuntu1
  Version table:
 *** 0.21.0+fixes18722-0ubuntu1 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages
        100 /var/lib/dpkg/status

---

