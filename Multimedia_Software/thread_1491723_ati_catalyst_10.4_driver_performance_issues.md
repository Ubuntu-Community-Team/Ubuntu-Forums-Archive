---
title: "ati catalyst 10.4 driver performance issues?"
date: 2010-05-23
forum: Multimedia Software
---

### Post by Schroeder on 2010-05-23
I am running an ATI Mobility Radeon 4570.

I recently upgraded to Lucid and also installed the latest version of the ATI Catalyst drivers from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&#9001;=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English").

After restarting Lucid, everything runs painfully slow. Dragging any window it looks like the screen is updated at a very slow rate, scrolling in Firefox is the same. I can see the screen redrawing and the dragged window leaves a trace until I stop dragging and it updates.

Is this a known issue? :confused:

Thanks!

Chris

---

### Post by apuglisi on 2010-06-01
I had the same issue this last weekend. I had to install Catalyst a second time but then I was carefull to read all instructions available onscreen. The problem got solved this way:
Just after installing Catalyst, I had to run the command "aticonfig --initial -f" (without quotes) and the config utility will autosetup the new driver. This fixed my problem at least.

Hope you can solve it too. Good luck!

---

