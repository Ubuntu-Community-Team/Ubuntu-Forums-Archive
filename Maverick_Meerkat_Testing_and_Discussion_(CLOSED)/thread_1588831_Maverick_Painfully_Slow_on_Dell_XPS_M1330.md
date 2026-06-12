---
title: "Maverick Painfully Slow on Dell XPS M1330"
date: 2010-10-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by supertedster on 2010-10-05
I just installed the Meerkat (32-bit) on my Dell XPS M1330 (Core 2 Duo 2,5 GHz, 4 GB RAM). Install was very slow (~40 minutes), and the wireless connection is very unstable. I performed

```
sudo apt-get update
sudo apt-get upgrade
```This took at least 20 minutes. I then rebooted, didn't help. System Monitor reports itself using ~90% CPU. Starting Firefox takes approx. 30 seconds and uses 96% CPU according to system monitor. 

Basically, my system runs like syrup. System Monitor doesn't report any obvious memory leaks.

Any ideas on where to begin finding the problem?

---

### Post by cariboo on 2010-10-05
Either start top in a terminal, or click the processes tab in system monitor to see what is using all your resources.

Top will give you a better reading of system usage, as System Monitor adds it's own overhead.

Currently my desktop system is using between 2 and 4% cpu, with chromium and deluge, plus a couple of terminals open, while my netbook is using approx 2% with just a terminal open.

---

### Post by TBABill on 2010-10-05
When I ran the upgrade from 10.04 to 10.10 I could not even get into Chromium and Firefox was slow. I removed the iced tea plugin (which was reinstalled with 10.10) and all was well again. It was like the system was just in slow motion until I removed it. I think it conflicted with Sun Java.

---

### Post by supertedster on 2010-10-05
top reports Xorg using 5%, top using 4%, gnome-terminal using 3% CPU. No memory hogs whatsoever, and no other apps using any significant CPU power.

But my system is still running like syrup.

---

### Post by NightwishFan on 2010-10-05
Open top while the system is slow, and post an average value of **%wa**. It is above the process list on the CPU(s) line.

---

### Post by supertedster on 2010-10-05
%wa is 0.0%. Have yet to see an increase after 1 minute observation.

Attempting to remove iced tea, it's taking forever.

---

### Post by NightwishFan on 2010-10-05
So.. The machine has little to no cpu usage, no i/o wait and tons of spare ram and it is still slow?

---

### Post by supertedster on 2010-10-05
Well, synaptic took 97% CPU when running, and I had to do killall synaptic. Basically, at "rest" there is no CPU load but as soon as I do anything, the load goes up to ~100%. Firefox uses 1% when idle, but almost 100% when loading a page (which is really slow). The same for synaptic, the same for navigating files and folders, etc.

Edit: I just realized my WiFi indicator is flashing intermittently, which it normally never does. I disabled the wireless network, doesn't seem to help at all with system performance.

---

### Post by NightwishFan on 2010-10-05
Most programs should use 100% cpu, that is normal. Question is if that is what is the problem or not. This might actually be Xorg related. Could you install a program called gtkperf, and run it and post the final time?

---

### Post by supertedster on 2010-10-05
> **NightwishFan said:**
> Could you install a program called gtkperf, and run it and post the final time?
Total time: 182,00

---

### Post by NightwishFan on 2010-10-05
With default setting of 100? A normal time is around 10 seconds. This is obviously graphics related. Could you post information about your GPU? If you do not know anything post the output of:
```
sudo lshw -C display
```

---

### Post by supertedster on 2010-10-05
The M1330 comes with an nVidia 8400M card. The proprietary drivers weren't activated, trying that now, but again it's painfully slow.

---

### Post by NightwishFan on 2010-10-05
Maverick has known issues with Nvidia drivers. Is it still slow with proprietary installed? Remember to reboot. GTKperf is a good place to test. Though I believe that nouveau should not perform that badly under normal circumstances.

---

### Post by supertedster on 2010-10-05
Problem persists with the recommended nVidia driver. Opening the "Additional Drivers" app took almost a minute. It confirms the "version current" is activated and in use.

---

### Post by lamb123 on 2010-10-05
[http://www.omgubuntu.co.uk/2010/09/nvidia-graphics-laggy-ubuntu-fix/](http://www.omgubuntu.co.uk/2010/09/nvidia-graphics-laggy-ubuntu-fix/)

helped me

---

### Post by NightwishFan on 2010-10-05
Try this for me in a terminal. If it says "file not found" I am at a loss to what to do, however at least we lowered it down to a graphics issue.

First:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.nwbackup
```
Then run:
```
sudo dpkg-reconfigure nvidia-current
```
Finally:
```
sudo apt-get -f install
```

Reboot, if graphic performance is bad, I will do some digging. Edit: That version of Nvidia Driver is already in Maverick I believe.

---

### Post by supertedster on 2010-10-05
> **NightwishFan said:**
> Try this for me in a terminal. If it says "file not found" I am at a loss to what to do, however at least we lowered it down to a graphics issue.

First:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.nwbackup
```Then run:
```
sudo dpkg-reconfigure nvidia-current
```Finally:
```
sudo apt-get -f install
```Reboot, if graphic performance is bad, I will do some digging. Edit: That version of Nvidia Driver is already in Maverick I believe.
That seems to have done the trick! GtkPerf now clocks in at 6,97 total time, and the system is fast and responsive. Thanks a lot! Is there anything I can do to help get this issue fixed before final release?

---

### Post by NightwishFan on 2010-10-05
You must have had a lingering xorg conf file that did not play well with the new driver. Unless there is still a rash amount of these issues, I think it will be fine. Glad I could help. :)

---

### Post by cariboo on 2010-10-05
Too slow.

---

