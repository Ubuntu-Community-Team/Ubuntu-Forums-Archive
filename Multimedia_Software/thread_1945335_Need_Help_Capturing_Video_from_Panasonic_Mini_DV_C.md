---
title: "Need Help Capturing Video from Panasonic Mini DV Camcorder"
date: 2012-03-23
forum: Multimedia Software
---

### Post by jcdeighan on 2012-03-23
Hi all!

New to posting on the forum, though I frequent them often.

I need to capture some video off a Panasonic PV-GS250 Mini DV Camcorder.  I have an iLink-Firewire400 Cable plugged into the 3.5" Bay on the front of my computer that has 2 USB and 1 Firewire400 ports. I know the USB ports work but so far am unable to determine if the Firewire port is the reason why I can't recognize this camera on the PC.

I've read numerous posts and threads and nothing so far has worked. I first tried Kino but will use any software that will allow me to capture the video off these tapes.

Let me know where to begin or what information you need and I'll be happy to post away!

Also, I'm fairly new to Ubuntu but understand things like running commands in a terminal and whatnot.

Thanks ahead of time!

Ubuntu 11.10

---

### Post by Bhodi223 on 2012-03-26
I'm in the same situation.. It seems the Panasonic MiniDV camcorder drivers are only for WinXP. So, I switched to Ubuntu, rather than buy a new camcorder.

If you make any headway, please post your results. As a last resort, you may have to use a driver wrapper in Ubuntu, and use the panasonic drivers for XP. I was thinking that as a last resort..

Please keep this running..

Bhodi223

---

### Post by Steeperton on 2012-03-26
I used to use Kino a long, long time ago, and I recall that I had to run it as root ("sudo kino") in order to get it to read correctly. 

Otherwise, run kino normally, connect the camcorder, and see if any error messages are shown in the status bar at the bottom of kino. If so, post it here.

---

### Post by rhk on 2012-09-02
I'm trying to solve similar problem with TRV-900 and Ubuntu 12.04 and can't make it recognize the camera. There seem to be many people fighting with the same problems and it seems that some of it started after the old FW stack was dropped (in Natty? Can't remember).

So please let us know if you ever solved this, it'll propably help others looking for solutions.

---

### Post by rfrome on 2012-09-22
I am using Panasonic Camcorder and JVC with Kununtu 12.04 with FW

Here is what I am doing to make it work:
1. Switch on camcorder. Set it to **play mode** ;), not PC mode
2. connect it to the PC
3. start Kino
4. Open the capture sub menu
5. Press the AV/C Button, this actually connects the camcorder
6. Use the <<, <, play, rec, > >> buttons as expected

I hope that might help.
May be it is your FW400? So may try the USB connection of the Panasonic, but I did not tried that. 
):P

---

