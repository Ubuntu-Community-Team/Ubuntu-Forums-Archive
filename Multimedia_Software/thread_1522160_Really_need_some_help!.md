---
title: "Really need some help!"
date: 2010-07-01
forum: Multimedia Software
---

### Post by JThompson118 on 2010-07-01
I've made this post nearly identically twice now, and I still can't get an answer. While trying to set up a dual screen with my television, and following some steps taking from some forums, I restarted my computer after applying said changes, and I got an alert that said "Ubuntu is running in low-graphics mode". I went to check my NVidia to double check if anything was wrong, and got this> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. After seeing that, I logged in as root. I then ran 'nvidia-xconfig' and got this: > Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

Figuring that this must have fixed my problem, I restarted my computer (for whatever reasons, "Ctrl+Alt+ Backspace" doesn't restart my X Server), and upon reaching the log-in screen, got the same exact error message. I logged in, checked Nvidia, and got the same message as before. I could only think that I'm going to dig deep and change some codes, and as I'm a newbie at this, I'd like some help. :P. If you need any information, just let me know. :)

---

### Post by abra13b on 2010-07-01
Try this for starters:

sudo apt-get install --reinstall dkms

then reboot.

---

### Post by -humanaut- on 2010-07-01
Have you updated the kernel recently? It broke my X when I upgraded to 2.6.32-23 (on a different system)
try this

sudo nano /etc/default/grub

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

**GRUB_DEFAULT=2**
GRUB_HIDDEN_TIMEOUT=0

The bold part should be 0 try changing it to 2 and it should boot into your last good kernel with the Nvidia modules already built in.

---

### Post by JThompson118 on 2010-07-01
Abra13b: I entered it, installed whatever that was, and restarted. No apparent changes. I'm off to try humanaut's suggestion now.

---

### Post by JThompson118 on 2010-07-01
humanaut: It's at zero as you thought, but I can't save my changes. it says ^X- Exit, but I enter that in, and it won't exit. And it won't let me tab to it and hit enter. If I exit out, it doesn't save my changes. How do I save it and exit?

---

### Post by fwhall on 2010-07-01
> **-humanaut- said:**
> Have you updated the kernel recently? It broke my X when I upgraded to 2.6.32-23 (on a different system)
try this

sudo nano /etc/default/grub

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

**GRUB_DEFAULT=2**
GRUB_HIDDEN_TIMEOUT=0

The bold part should be 0 try changing it to 2 and it should boot into your last good kernel with the Nvidia modules already built in.


Yes, update manager upgraded my kernal this morning on my desktop machine and it did whack X.  I was going to post this and see if anyone else had it happen.  I'm  running gnome, will the grub modification fix this?

---

### Post by JThompson118 on 2010-07-01
Humanaut: I figured it out! :P. I altered 'grub' as directed, and it changed something, but Ubuntu is still in low-graphics mode, and still won't open NVidia properly.

---

### Post by -humanaut- on 2010-07-01
> **JThompson118 said:**
> Humanaut: I figured it out! :P. I altered 'grub' as directed, and it changed something, but Ubuntu is still in low-graphics mode, and still won't open NVidia properly.

Did you run sudo update-grub? if so try this

sudo update-grub

then 

sudo update-initramfs -k -u 2.6.23-22-generic

then

sudo shutdown -r now

also try this
**GRUB_DEFAULT=5**
**GRUB_HIDDEN_TIMEOUT=10**
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10

hit escape when its at the blank screen and select your last kernel you knew had the nvidia modules.

---

### Post by -humanaut- on 2010-07-01
last thing if all else fails try this 

sudo apt-get install nvidia-kernel-common             <------TRY THIS FIRST!


and the very last thing I can think of is *_``````````LAST RESORT!!`````````_*

sudo apt-get install nouveau-firmware

then

sudo nano /etc/modprobe.d/blacklist-framebuffer.conf

blacklist nvidiafb

then

sudo nano /etc/modprobe.d/blacklist.conf

blacklist nvidia
blacklist nvidia-kernel
blacklist nvidia-current

then

sudo update-initramfs -u && sudo update-grub

then

sudo shutdown -r now

then pray haha

---

### Post by JThompson118 on 2010-07-01
Tried your second to last suggestion. Nothing. So I'm doing > sudo apt-get install nvidia-kernel-common

---

### Post by JThompson118 on 2010-07-01
Lol. If I do something wrong in the "last resort", will it ruin my computer? :P. Nothing else is working. :(

---

### Post by -humanaut- on 2010-07-02
It won't ruin your computer but it will install the nouveau firmware which should block the proprietary nvidia drivers and you should be able to reinstall them after nouveau's installed but there is a substantial risk that it could kill X and you might have to reinstall make sure you back everything up first before using my "LAST RESORT"

---

