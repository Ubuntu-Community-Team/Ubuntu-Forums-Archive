---
title: "Updating from RC2 to final release without downloading the entire ISO"
date: 2008-09-27
forum: Mandriva/Mageia
---

### Post by shuttleworthwannabe on 2008-09-27
Hi There,

I have heavy bandwidth restrictions; I could not resist downloading the new RC2 just announced. What I would like to know how I could just roll-over to the final release without actually downloading the final ISO (whole 600MB worth of data). I read somewhere that if I do not do this, I will keep receiving test version updates, is this correct?

Many thanks,
S

---

### Post by Antman on 2008-09-27
Once Mandriva 2009 is released, I think you just need to change your repos and just use urpmi to update any changes to final.
[http://wiki.mandriva.com/en/Tools/urpmi#Upgrade_to_the_latest_Mandriva_version_using_urpmi]("http://wiki.mandriva.com/en/Tools/urpmi#Upgrade_to_the_latest_Mandriva_version_using_urpmi")

---

### Post by AdamWill on 2008-09-27
Right. Once 2009 goes final, you need to remove your repositories (which will be Cooker repositories) and add 2009 stable repositories. You can't do this with the standard tool inside MDV, because your install will still consider itself to be Cooker, and give you Cooker repos. You can just use Easy URPMI:

[http://easyurpmi.zarb.org/](http://easyurpmi.zarb.org/)

Once the final release is out, soon afterwards, that site will start showing 2009 as an available version. Just tell it you're using 2009 and click the big shiny button. :) That'll get you 2009 repos.

Then you just need to run 'urpmi --auto-select' as root to update all the packages to 2009 final state, and you're good from then on.

---

### Post by shuttleworthwannabe on 2008-09-27
Thanks Adam. So far 2009 RC2 GNOME is looking good. Resuming from suspend is still sticky though.

---

### Post by pelle.k on 2008-09-27
> Resuming from suspend is still sticky though.
please, do tell. maybe we can help?

---

### Post by shuttleworthwannabe on 2008-09-28
HI there

Test Hardware: Acer travelmate 6292 notebook; 2G RAM, Intel C2D 2Ghz, built-in mic and webcam, bluetooth; Wireless card intel PRO/Wireless 4965; Ethernet Broadcom BCM5787M Gigabit; GPU is a native intel chipset with 1280x800 max res

What works out of the box: almost all of the hardware is detected; all LED lights are on on boot up (WI-FI--in fact it behave just like in Vista, i.e. blinks when there is data transfer, bluetooth); all shortcut keys (internet, mail and P) all configured to launch firefox, evolution, and a program of choice); only acer&#347; e not work. Keyboard and mouse all work. Screen is configured to native res and 3-D works out of the box (have not tried it much, I personally do not like 3-D, makes me dizzy).
Resume from sleep is temparamental: goes to sleep ok, but when resuming it goes to screensave login screen, and enter password, the screen hangs; I got out of this by ctrl-alt-backspace and relogged in. Sometimes it works without a glitch. I am not able to reproduce it though. 3-D is off when this happens.

What does not work properly: Sound: login sound is muffled and crackly. flash e.g. youtube or cnet videos have not sound at all, but a constant pinging tone. Sound settings are set to ALSA by default. I am not an expert at this, but I had problem with Ubuntu Hardy and Linux Mint 5 as well; and it was related to Pulse Audio thingy or something.
Gripe1: Baterry life in less than in Vista (Vista give me 6H15 min on this 9 cell baterry on powersave mode; Ubuntu Hardy, Mint 5 and now MDV2009 gives me only 4H15). How can I tweak power consumption in any of these linux flavors?

Gripe2: No built files searching tool. No deskbar or tracker? any suggestion how to install these or better tool? I desperately need this to index my chaotic filing system.

Success with installation of third party apps: Zimbra Desktop; Adobe reader just download from host website and install. beautiful.

Overall I am happy, it if fast and responsive and clean and neat; but would have preferred attention to my gripes and sound.

Let me know if these are just idiosynchratic or that I should be submitting bugs.

Thanks
S

---

### Post by pelle.k on 2008-09-28
> but when resuming it goes to screensave login screen, and enter password, the screen hangs
Sounds like it may be a pam, consolekit or gdm issue. Check .xsession-errors when it happens.

> login sound is muffled and crackly. flash e.g. youtube or cnet videos have not sound at all, but a constant pinging tone.
Maybe you have to supply a model id when loading the sound driver?
Try adding 'options snd-hda-intel model=3stack' to /etc/modprobe.conf
You could always try OSS instaed of alsa, if that doesn't work out for you.

> Vista give me 6H15 min on this 9 cell baterry on powersave mode; Ubuntu Hardy, Mint 5 and now MDV2009 gives me only 4H15
Check that you have some type of utility running to reduce CPU speed when it's not needed. cpufreq/powernow/kpowersave etc.
You can check the current state with 'cat /proc/cpuinfo'.
Maybe vista does spin down (HD) more agressively? I don't know. It could just be that the ACPI support are a bit messed up (read: they wrote it for vista).

---

### Post by shuttleworthwannabe on 2008-09-28
Most recent update on RC2

It left notebook unattended for 15 min and it chose to go to sleep on its own--I think it may have done a hibernation; funny thing is the machine completely powered down. There was no way to power it on except that to push the power button; when it cam up it went thru GRUB menu--noticed that GRUB menu did not have my Vista line; it went straight to MDV boot screen (splash) and hung. I had to hard power down once more.
When I rebooted MDV, I had to reinstall GRUB to pick up my Vista partition and load GRUB on hda (MBR) so I could boot into Vista.

Thanks, I will try your suggestion once I get to home,
S

---

### Post by AdamWill on 2008-09-28
You can install and run the 'powertop' utility and it'll give you an indication of what processes are causing power to be consumed. If you see any obvious offenders, post here and we'll see what we can do.

For sound, you can disable PulseAudio from the 'draksound' tool (run it directly or find it in the Control Center). See if that helps.

Both Tracker and deskbar (which isn't an indexer in itself, btw, it just acts as an interface to Tracker or Beagle if they're present) are in the repos. You do need to add the repos first, though.

---

### Post by AdamWill on 2008-09-28
You can install and run the 'powertop' utility and it'll give you an indication of what processes are causing power to be consumed. If you see any obvious offenders, post here and we'll see what we can do.

For sound, you can disable PulseAudio from the 'draksound' tool (run it directly or find it in the Control Center). See if that helps.

Both Tracker and deskbar (which isn't an indexer in itself, btw, it just acts as an interface to Tracker or Beagle if they're present) are in the repos. You do need to add the repos first, though.

---

### Post by shuttleworthwannabe on 2008-10-05
Right, powertop seems to work by identifying processes that consume most power on battery; it also made suggestion, which I followed (SATA settings..I am assuming thi is for spinning thte hd??).
Now I am getting close to 5:36min (much better than 3:24min).
**EDIT: so how do I make powertop run automatically when I switch to battery power, noting by previous selections?**

Thanks
S

---

### Post by AdamWill on 2008-10-05
Powertop is a diagnostic tool, it's not capable of automating any changes or anything. All it can do is look at what's eating power (and give suggestions). You have to deal with implementing the suggestions manually.

What were the suggestions it made, exactly? If I know what they are, I can see about applying them automatically.

---

### Post by shuttleworthwannabe on 2008-10-05
> Power usage (ACPI estimate): 13.5W (6.2 hours)

Top causes for wakeups:
  59.8% (211.6)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  15.0% ( 53.0)              Xorg : schedule_timeout (process_timeout) 
   4.2% ( 14.9)       <interrupt> : extra timer interrupt 
   3.6% ( 12.8)           firefox : futex_wait (hrtimer_wakeup) 
   3.6% ( 12.6)       <interrupt> : iwlagn 
   2.8% ( 10.0)     <kernel core> : scan_async (ehci_watchdog) 

Suggestion: Disable or remove 'gnome-power-manager' from your system.
Older versions of gnome-power-manager wake up far more often than
needed costing you some power.
 Q - Quit   R - Refresh   K - kill gnome-power-manager 

> Power usage (ACPI estimate): 14.6W (5.7 hours)

Top causes for wakeups:
  57.6% (224.8)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  12.7% ( 49.4)              Xorg : schedule_timeout (process_timeout) 
   4.9% ( 19.0)       <interrupt> : extra timer interrupt 
   4.8% ( 18.7)      <kernel IPI> : Rescheduling interrupts 
   4.6% ( 18.0)           firefox : futex_wait (hrtimer_wakeup) 
   3.4% ( 13.2)       <interrupt> : iwlagn 

Suggestion: Enable USB autosuspend by pressing the U key or adding
usbcore.autosuspend=1 to the kernel command line in the grub config

 Q - Quit   R - Refresh   U - Enable USB suspend 


> Power usage (ACPI estimate): 13.4W (6.2 hours)

Top causes for wakeups:
  19.1% ( 23.0)           firefox : futex_wait (hrtimer_wakeup) 
  13.7% ( 16.5)       <interrupt> : extra timer interrupt 
  11.6% ( 14.0)              hald : schedule_timeout (process_timeout) 
  10.4% ( 12.5)       <interrupt> : iwlagn 
  10.0% ( 12.0)      <kernel IPI> : Rescheduling interrupts 
   8.7% ( 10.5)   gnome-power-man : schedule_timeout (process_timeout) 

Suggestion: Enable SATA ALPM link power management via:
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.
 Q - Quit   R - Refresh   S - SATA Link Power Management 


> Power usage (ACPI estimate): 12.9W (6.4 hours)

Top causes for wakeups:
  25.1% ( 21.0)           firefox : futex_wait (hrtimer_wakeup) 
  16.8% ( 14.0)       <interrupt> : iwlagn 
  15.0% ( 12.5)      <kernel IPI> : Rescheduling interrupts 
  12.6% ( 10.5)       <interrupt> : extra timer interrupt 
  12.0% ( 10.0)   gnome-power-man : schedule_timeout (process_timeout) 
   5.4% (  4.5)      <kernel IPI> : function call interrupts

Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
This wakes the disk up less frequenty for background VM activity
 Q - Quit   R - Refresh   W - Increase Writeback time 


> Power usage (ACPI estimate): 12.5W (6.6 hours) (long term: 19.1W,/4.3h)

Top causes for wakeups:
  54.0% (121.9)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  14.5% ( 32.7)              Xorg : schedule_timeout (process_timeout) 
   6.8% ( 15.3)       <interrupt> : extra timer interrupt 
   5.8% ( 13.1)       <interrupt> : iwlagn 
   5.7% ( 12.9)           firefox : futex_wait (hrtimer_wakeup) 
   4.4% (  9.9)       <interrupt> : ahci

 Q - Quit   R - Refresh 


NOTE: how the battery stamina increases with each accepted suggestion. I am impressed. 

Thanks Adam, for the help,
S

---

### Post by AdamWill on 2008-10-06
OK, let's see.

I'm not so sure about the gnome-power-manager message. I suspect it may be bogus. It was introduced quite a long time ago and the bug it refers to in g-p-m was fixed, like, a year ago, I'm fairly sure. I'd suggest you fix all the others first, then after doing that, test with and without g-p-m running and see if it really affects the battery life.

I thought USB suspend was meant to be on in our kernel by default, but - you can just do as it says:

"adding usbcore.autosuspend=1 to the kernel command line in the grub config"

i.e., set 'usbcore.autosuspend=1' as a boot parameter. You can edit /boot/grub/menu.lst directly, or use the Mandriva graphical boot config tool (which is in MCC) - it can let you add kernel parameters.

For SATA ALPM link power management, just add the command it recommends to the file /etc/rc.local :

echo min_power > /sys/class/scsi_host/host0/link_power_management_policy

anything in /etc/rc.local is run automatically at each boot.

You can do exactly the same thing for the final recommendation. Add that command to /etc/rc.local, too:

echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

---

### Post by AdamWill on 2008-10-06
Oh, finally, I'd also recommend you actually test the battery life. The remaining power estimate of anything is, always, only an estimate. The only way to be sure is simply to run the battery down in normal use, and see how long it actually takes.

---

### Post by shuttleworthwannabe on 2008-10-06
thanks, Adam. Will do.

---

