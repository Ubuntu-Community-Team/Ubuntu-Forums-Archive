---
title: "Steps to replace intel graphics with nvidia on desktop?"
date: 2009-11-13
forum: Multimedia Software
---

### Post by david.karr on 2009-11-13
I'm trying to get 9.10 working on a desktop with intel graphics.  I'm about to give up on this, as the box only runs for about 20 minutes before freezing (only the mouse pointer moves, nothing else responds), requiring a reboot.  I've upgraded to the latest intel Xorg driver, even the PPA version, with no change.

I've concluded that there's a good chance that replacing the intel graphics card with an appropriate NVidia graphics card might fix this.  I have a few issues with this.  First, I have to figure out which card to get for optimal Ubuntu support, but I also have to figure out the procedure for doing the upgrade, mostly with respect to Ubuntu.  If I just restart with the new card, what exactly will happen?  Will it go into a primitive "safe mode" that will allow me into Ubuntu to make sure I have the latest nvidia driver installed?

How do I get the latest nvidia driver at that point?

---

### Post by falconindy on 2009-11-13
Don't despair! Intel graphics work great with the latest Xorg, given a little massaging. You'll need to enable KMS (kernel modesetting) in order for it to work.

As I'm not 100% familiar with the process under Ubuntu (I'm an Archer), I'll point you to the [wiki article](https://wiki.ubuntu.com/X/KernelModeSetting).

---

### Post by david.karr on 2009-11-13
Ok, that's promising.

As the process says to verify that I'm using a particular version of the intel driver, can you tell me how I determine that?

I can see that my first expedition into Grub2 (or even Grub) will take some research.  It would be nice if this article was updated for Grub2.

---

### Post by RavanH on 2009-11-13
Very interesting... What graphics card are you using now? Please let me know if you make it work with the KMS wiki!

I have had the same issues since 9.04 on a laptop with Intel i855GM graphics using the i915 driver. It became impossible as soon as I installed a fresh 9.10 . See [http://ubuntuforums.org/showthread.php?t=1238658](http://ubuntuforums.org/showthread.php?t=1238658) where I conclude that only switchin OFF (!) modeset (=KMS) and reverting to the default vesa driver (loosing Desktop Effects in Ubuntu but with Xubuntu I stil have transparency/shading) worked for me. The original solution was posted on [http://blog.cyril-ravat.fr/post/2009/10/25/Ubuntu-karmic-freeze-on-Asus-M2n](http://blog.cyril-ravat.fr/post/2009/10/25/Ubuntu-karmic-freeze-on-Asus-M2n) 

So if pushing forward to force KMS does not work, try reverting to vesa as done in the link above. Good luck!

---

### Post by david.karr on 2009-11-14
I've been struggling trying to figure out how to follow these directions, when I noticed the bold text at the top of the instructions for enabling KMS:

"Since kernel 2.6.30-10.12 KMS is enabled by default."

The report from "uname -r" says I have "2.6.31-14-generic", so it seems to me that trying to turn on KMS is a waste of time.  Would you agree?

---

### Post by david.karr on 2009-11-14
Again, assuming that KMS page is correct, since my kernel version is "2.6.31-14-generic", I should have KMS enabled already.

This morning I looked in the "kern.log" for events that occurred just before long gaps.  I saw the following after I rebooted the box this morning (as usual):

----------------
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752046] INFO: task i915/0:227 blocked for more than 120 seconds.
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752054] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752059] i915/0        D c08145c0     0   227      2 0x00000000
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752068]  f6a61f04 00000046 f6a40cbc c08145c0 f6a40f28 c08145c0 7af12304 00000125
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752080]  c08145c0 c08145c0 f6a40f28 c08145c0 7af100e8 00000125 c08145c0 f5f0e000
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752090]  f6a40c90 f6872c14 f6872c18 ffffffff f6a61f30 c056f776 c0748e80 f6872c1c
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752101] Call Trace:
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752119]  [<c056f776>] __mutex_lock_slowpath+0xc6/0x130
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752125]  [<c056f690>] mutex_lock+0x20/0x40
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752171]  [<f822bc0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752184]  [<c0157a7e>] run_workqueue+0x6e/0x140
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752207]  [<f822bbe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752216]  [<c0157bd8>] worker_thread+0x88/0xe0
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752225]  [<c015c280>] ? autoremove_wake_function+0x0/0x40
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752231]  [<c0157b50>] ? worker_thread+0x0/0xe0
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752237]  [<c015bf8c>] kthread+0x7c/0x90
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752243]  [<c015bf10>] ? kthread+0x0/0x90
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752251]  [<c0104007>] kernel_thread_helper+0x7/0x10
----------------

Looking further back in the log, I saw this event several times in the houre before this.  This event was the last event in the log until I rebooted, several hours later.

Does that provide any useful information to anyone?

Another ironic piece of information:  I may have found a workaround for the problem.  It's not really a practical workaround, but I discovered something that I can do before I leave the computer that in a couple of cases has let it live for several hours.  I had been trying to get advice on this from the #ubuntu IRC channel.  Normally when I leave the computer I don't leave anything actively running, but one day I left the IRC channel running, which continually updates with new messages.  Somehow, when I came back several hours later, it was still alive.  Up to that point, that was the ONLY time it had ever ran for that long without freezing.

---

### Post by david.karr on 2009-11-14
@Ravanh: What would be the impact of using the VESA driver exactly?

I'd like to pursue this, but I frankly don't understand the instructions.  There's too much noise.  For one, I don't see a "xorg.conf" file in "/etc/X11".

---

### Post by RavanH on 2009-11-16
> **david.karr said:**
> @Ravanh: What would be the impact of using the VESA driver exactly?

The impact on my laptop was that I finally had a stable system but without fancy Desktop Effets (compiz) in Ubuntu/Gnome. However, if you decide to use Xubuntu/XFCE (install xubuntu-desktop in Synaptic) instead of Gnome, you will be able to use basic transparency and drop-shadows around windows and such. Enough eye-candy for me ;)

> **david.karr said:**
> I'd like to pursue this, but I frankly don't understand the instructions.  There's too much noise.  For one, I don't see a "xorg.conf" file in "/etc/X11".

There is no xorg.conf file in Karmic. You have to create one to make your system use the vesa driver. The instructions on [http://blog.cyril-ravat.fr/post/2009/10/25/Ubuntu-karmic-freeze-on-Asus-M2n](http://blog.cyril-ravat.fr/post/2009/10/25/Ubuntu-karmic-freeze-on-Asus-M2n) were not writen for newbies so here is a basic step-by-step for those that did a fresh install (meaning you have GRUB2 instead of legacy GRUB after an upgrade):

**1. Boot with acpi=off**
* At boot hit the **Esc**-key to make the gub menu abort its normal process. Select the boot kernel you want to use (usually the one that is already selected) and hit the **e**-key. 
* Now you will see a new screen with all kinds of mysterious things ;) but just direct the cursor to the second to last line where you should read some basic kernel options like "... ro quiet splash ...". Type the extra kernel option ```
acpi=off
``` there so it looks something like "... ro acpi=off quiet splash ...".
* Continue the boot process with **Ctrl+x**

**2. Change default boot options**
* Log in to an account with sudo (administrative) rights, usually the account with the credentials you have specified during installation. (NOTE: You might notice there is no sound anymore and power management features are missing now, but this is temporary)
* Hit **Alt+F2** ant type (when in Ubunutu/Gnome) ```
gksudo gedit /etc/default/grub
``` (use mousepad in Xubuntu or kate in Kubuntu instead of gedit), hit **Enter** and type your password.
* In the file that has now opened in your editor, find the line that starts with GRUB_CMDLINE_LINUX_DEFAULT and edit the value (usually something like "quiet splash") behind it to include ```
nolapic nomodeset
```. The line might now look like "quiet splash nolapic nomodeset".
* Hit **Save** and close the editor.
* Hit **Alt+F2** again and enter ```
gksudo update-grub
``` (NOTE: this is important! Else the changes will not propagate to the boot menu until the next kernel update...)

**3. Create a xorg.conf with vesa driver**
* Hit **Alt+F2** and type ```
gksudo gedit /etc/X11/xorg.conf
``` (again, use mousepad or kate if on Xubuntu or Kubuntu) and fill the new blank file with ```
Section "Device"
  Identifier      "Configured Video Device"
  Driver 	  "vesa"
EndSection

Section "Monitor"
  Identifier      "Configured Monitor"
EndSection

Section "Screen"
  Identifier      "Default Screen"
  Monitor         "Configured Monitor"
  Device          "Configured Video Device"
EndSection
```
* Hit **Save** en close the editor.
* You might want to disable **Desktop Effects** before the next step to avoid problems after the next login: Go to Preferences > Appearance and choose the tab Visual Effects. Select the option "None" to switch them off.

**4. Reboot**

This time, your system will be using the vesa driver. Test if the freezes have gone and if you are happy with it... You might try to enable the visual effects again but most likely that will not work. If you will settle for fast system with only basic visual effects (basic transparency and drop-down shadows) you might want to try out XFCE: ```
sudo aptitude update && sudo aptitude install xubuntu-desktop
``` Then log out and at the login screen choose XFCE as your new Window Manager... If you are not happy with the XFCE desktop, you can use ```
sudo aptitude remove xubuntu-desktop
``` to remove all packages that where installed with the previous command (note the use of aptitude both times and not apt-get).

Hope this helps and good luck!

---

