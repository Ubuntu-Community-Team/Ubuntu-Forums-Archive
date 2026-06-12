---
title: "[SOLVED] nvidia driver causing freezing"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by jtprince on 2007-02-06
On occassion (once or twice per day), whenever I'm doing somethings graphics intensive (e.g., viewing a webpage with video on it, or playing a game) my system will 'freeze' up.  It doesn't lock up absolutely, it just slows down to the point that it is effectively locked up and I have to hard reboot (power button for 4 seconds).  This doesn't happen when I use 'nv' in my xorg.conf, but then I can't do all that much without using the nvidia driver.  

Is there some setting in my xorg.conf that I'm missing?  Attached are my xorg.conf and the Xorg log files I copied directly after a reboot from one of these freezes.

Any help on this would be greatly appreciated.  I just switched to Ubuntu exclusively on my laptop and this is my biggest problem.

Thanks,
John

---

### Post by ingo on 2007-02-19
Which NVIDIA driver are you using and how did you install it? Also, could you post the output of "lshw" just for info please. Thanks

---

### Post by jtprince on 2007-02-19
I installed the 'nvidia-glx' package with synaptic or aptitude.  I have installed version 1.0.8776+2.6.17.7-11.1 of that package.

The output of uname -a is "Linux altius 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux" just in case.  I've attached the output of lshw.  

Thanks for looking at this.  I appreciate it very much.  Any tips, hints or tricks are greatly appreciated.

---

### Post by ingo on 2007-02-20
Right, you've go a GeForce FX Go5200 card, mine is a GeForce FX 5200 - doesn't sound too different...

However, the way I install my direct rendering and 3D capabilities is quite different (and I've never had a problem). Before you start, however, a word of caution: First deinstall your current glx package. Also, the method below will fail to start X after a kernel-update. You will have to go through the same procedure again - for me a welcome reminder to update my NVIDIA driver. Here goes:[LIST=1]
[*]**download **- I download the latest linux driver from the [nvidia website]("http://www.nvidia.com/object/unix.html")
[*]**logout **- I logout of X (KDE in my case since I'm on Kubuntu), change to a different terminal by pressing CTRL + ALT + F2
[*]**login **- login on the console and stop X altogether by typing sudo ```
/etc/init.d/kdm stop
```or if you are using Ubuntu with gnome ```
/etc/init.d/gdm stop
```
[*]**install **- ready for installation. First you have to make the downloaded driver executable. Change to the directory your file is in and type ```
sudo chmod +x name_of_your_file
```Now run it ```
sudo ./name_of_your_file
```or ```
sudo sh name_of_your_file
```I don't remember which and follow the instructions. Say yes to installation, yes to backup and yes to everything.
[*]**bingo **- your screen should come up. Reboot if in doubt.[/LIST]As I said this has never failed for me. If you don't like it there are about a hundred howtos in the tips & tricks section of this forum. 

HTH

---

### Post by tseliot on 2007-02-20
Try Envy and follow the instructions on my website:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by andyp11 on 2007-02-20
Actually this happens to me except it, or at least the screen, freezes solid. Even followed the Envy route and different methods on tseliot's site and I try it now and again, with kernal upgrades etc. So i keep reverting to the bog standard NV driver and then all works perfectly.

Same Geforce FX5200 as well. Any thoughts??

---

### Post by ingo on 2007-02-20
Well andyp11, thanks for your post. It just goes to show that good old fashioned installation works best :)

---

### Post by andyp11 on 2007-02-20
Seems like it. I think I'll try your method and report back

---

### Post by jtprince on 2007-12-04
much time and several Ubuntu release's later... and I'm pretty sure **I finally have this figured out (at least the problem)**.  I did a fresh install with Gutsy and I didn't have any freezes, EVER (this is with enabling the restricted drivers they offer which is using nvidia-glx-new to my understanding).  In any case, I wanted to get hibernation going on my laptop and I enabled the option in xorg.conf: NvAGP "1".  And boom, the freeze again.  So, I removed the line from my xorg.conf and no freezes again for as long as I had the option removed.  So, the problem is with the NvAGP "1" option.

Here's a more detailed description of the problem and some more suggested solutions:
[http://xlife.zuavra.net/index.php/41/](http://xlife.zuavra.net/index.php/41/)

Since I still wanted to hibernate and suspend (and this option seems vital to them both [I even tried suspend2 to no avail]) I tried some of these options.  NvAGP "2" still froze on me and NvAGP "0" (which is probably the same as not having the option??) didn't hibernate/suspend and didn't freeze.  

Digging a little deeper I discovered this site: 
[http://en.opensuse.org/index.php?title=NVidia_Suspend_HOWTO](http://en.opensuse.org/index.php?title=NVidia_Suspend_HOWTO)

I did this:
1. like normal, add the line NvAGP "1" to appropriate place in xorg.conf
2. add the phrase 'agp=off' to your /boot/grub/menu.lst file (yes, the line is preceded with a pound key).  The line now looks like this:
# kopt=root=UUID=e4d79a31-027c-4f2f-abbb-604bab112a1c agp=off ro
3. notice that 'lsmod | grep agp' gives the intel_agp module and agpgart.  Go into /etc/modprobe.d/blacklist and add the line:
blacklist intel_agp
and then restart the machine

So far so good.  I have not had any freezes and I can hibernate and suspend.  I will reply to this post if I have any issues with this.

---

### Post by jtprince on 2008-05-02
It is slightly simpler to disable the agpgart in the blacklist instead of at boot time (and apparently it is loaded as a module) as described here: [http://ubuntuforums.org/showthread.php?t=589794](http://ubuntuforums.org/showthread.php?t=589794)

The short summary:
_To */etc/modprobe.d/blacklist* add the following:_
[B]blacklist intel_agp
blacklist agpgart[/B]

_In the *device* section of */etc/X11/xorg.conf* add the line:_
**Option "NvAGP" "1"**

_Then **reboot**!_

_Then check to make sure you have the nvidia agp driver loaded:_
*cat /proc/driver/nvidia/agp/status*

which gives me:
Status: 	 Enabled
Driver: 	 NVIDIA
AGP Rate: 	 4x
Fast Writes: 	 Disabled
SBA: 		 Disabled

This works for me on Hardy Heron and I can suspend and hibernate.

---

