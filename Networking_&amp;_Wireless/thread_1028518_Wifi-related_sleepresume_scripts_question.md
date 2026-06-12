---
title: "Wifi-related sleep/resume scripts question"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by eugenia_loli on 2009-01-02
I have an Aspire One and I use the latest madwifi ath_pci driver (that works better than the ath5k default driver, for me). This driver needs to be unloaded before closing the lid of the laptop to go to suspend-to-RAM mode (laptop sleep). If I don't do that, then the driver is not able to scan for networks anymore, until I cold-boot the laptop. So basically, my questions are:

1. Which script do I edit exactly (somewhere in /etc/acpi, I would assume) to run the "madwifi-unload ath_pci" command just before the laptop goes to sleep by closing its lid?

2. Which script do I edit exactly, to run the "modprobe ath_pci" command after the laptop awakes from sleep (please note that this laptop requires to press a button to come back to life, a simple opening of the lid won't awake it).

Thank you for your suggestions.

---

### Post by mpokrywka on 2009-01-02
You could try installing "hibernate" package that "smartly puts your computer to sleep (suspend to RAM or disk) ... Hibernate can take care of loading and unloading modules, provides various hacks..."
I used it successfully with tuxonice, config files in /etc/hibernate are well commented, for unloading modules see /etc/hibernate/blacklisted-modules

---

### Post by eugenia_loli on 2009-01-03
Thank you for the reply. Unfortunately, from what I read on Synaptic, the "hibernate" scripts replace the Ubuntu "suspend-scripts" package, and this is not something I want to be doing. For forward compatibility reasons I would like to keep the ubuntu packages installed, especially the system-related ones.

So I am still on square one as to which files to edit to achieve the above stated targets.

---

### Post by mpokrywka on 2009-01-03
That "replaces: suspend-script" is artifact of debian packaging - first version of this package was called (suprise!) "suspend-script", and that was changed to "hibernate" in second package upload in july 2004.
I think you can use this package safely, it integrates well with system suspend infrastructure.

---

### Post by eugenia_loli on 2009-01-03
Sorry, this did not work. I installed what you said, I blacklisted in that script the ath_pci module, but it wouldn't unload it upon sleep, causing my wifi hardware to go berzerk again. I really don't like that hibernate package and the companion utility it installed as dependency, as it's one added layer where it shouldn't there be any. So I uninstalled it, I am just not interested in it, and I REALLY hope I didn't damage my system by installing uspswup (or whatever the heck that dependency package was called) because it took a LONG TIME to configure itself, obviously it wasn't just a drop-in script.

So, ALL I need is the information about which scripts to edit on /etc/acpi/ to do what I need as I stated in my first post above. Does ANYONE know? Anyone!?! Please don't give me answers that I didn't ask for. My questions were on purpose straightforward with all the info someone would need to provide me with an also straightforward answer. And given how many modules are crapped up on Linux as they have poor ACPI integration, my questions should be considered common, so I am very surprised why no one provided me with an answer yet.

---

### Post by mpokrywka on 2009-01-04
Maybe check: /etc/default/acpi-support

---

### Post by eugenia_loli on 2009-01-04
This didn't work correctly either. I added the "ath_pci ath_hal" modules in that script to be removed/reloaded, but while it seems that the script did remove them while on sleep, when the laptop came back wifi didn't work again -- even if the modules got reloaded.

I believe that the reason for this is because the ath_pci family of modules need to be removed using the supplied "madwifi-unload" command rather than with a straight "rrmod" that generic scripts use. So I guess the question still stands:
1. What acpi script do I edit to run the actual command "madwifi-unload ath_pci" just before going to sleep?
2. What acpi script do I edit to run "modprobe ath_pci" when the laptop comes back from sleep?

---

### Post by mpokrywka on 2009-01-04
You said that hibernate package didn't work, so I investigated further. In fact, it looks like support for this script was removed - it won't be invoked during suspend/hibernate. Under new kernel my laptop suspends without additional hacks, so I didn't notice that hibernate script doesn't work anymore.
<how this works>
When going to sleep /etc/acpi/sleep.sh script is invoked (when suspending to disk /etc/acpi/hibernate.sh). This script calls /etc/acpi/prepare.sh before suspend and /etc/acpi/resume.sh after.
/etc/acpi/prepare.sh runs all scripts in /etc/acpi/suspend.d directory
/etc/acpi/resume.sh runs all scripts in /etc/acpi/resume.d directory
</how this works>
**SOLUTION:**
Put shell script you want to run before suspend into /etc/acpi/suspend.d directory. Similar, put your resume script into /etc/acpi/resume.d

---

### Post by eugenia_loli on 2009-01-04
> Put shell script you want to run before suspend into /etc/acpi/suspend.d directory. Similar, put your resume script into /etc/acpi/resume.d

What you say makes sense. Here's what I did:
eugenia@AspireOne:/etc/acpi/suspend.d$ ls -l
total 68
-rwxr-xr-x 1 root root   90 2008-10-14 20:31 05-acpi-lock.sh
-rwxr-xr-x 1 root root   34 2009-01-04 06:59 10-madwifi.sh
[...]

Inside that 10-madwifi.sh script, there is the following commands:
#!/bin/sh
madwifi-unload ath_pci

The permissions of the file seem to be correct, it's executable and all. I also tried the filenames 00-madwifi.sh and 05-madwifi.sh (to make sure I run it early enough in the game).

However, no cake! ACPI does *not* run that script at all when it's going to sleep! When I come back from sleep the modules are still loaded with the previous instance, which means that connection/scanning is dead. I have to again manually unload and reload the module from the command line or cold-boot to get wifi back.

My similar 99-madwifi.sh under /etc/acpi/resume.d/ that modprobes back the ath_pci module doesn't seem to run either! What gives? I even rebooted to make sure that the acpi service hadn't cached its scripts, but still nothing. This is a mystery!

Thank you for replying over and again btw!

---

### Post by eugenia_loli on 2009-01-04
I found the solution!!!!!

This situation is so crapped up that I can't even move the muscles of my lips to laugh at it.

So, here's the problem. Normally, we would do what we both were suggesting, which is creating executable scripts on the /etc/acpi/ sub-folders. In fact, this is how it's *supposed* to work. However, when Gnome-Power-Manager is running -- its daemon, I suppose --, then NOTHING gets executed in these acpi folders! Why? I don't freaking know! That's what I read on a forum thread online, and that's what it seems to be happening indeed!

Thankfully, I finally found another way to suspend modules before sleep:
```
cd /etc/pm/config.d/
sudo nano config
```
And inside that "config" file you just created, you type:
```
SUSPEND_MODULES="$SUSPEND_MODULES ath_pci"
```
Save, and test it! It works.

It works, until the next "big thing" that replaces pm-tools comes to Linux and breaks that solution too, that is. Not having /etc/acpi/ running was unpleasantly unexpected. Every time I take this Acer netbook with me, or when I use my other ubuntu laptop (please note that I use Linux on/off for 10+ years now) I would stumble into such situations all the time. It never works as expected (and I am not talking just about wifi here). I think that new Macbook or DELL Mini12 with Vista is closer than before in my purchasing future.

I am not trying to bitch here, it's just that this whole GNU/Linux usability/bugs/utils-being-moving-targets situation is frustrating as hell. All I wanted is to have a lightweight laptop with me these two weeks that I currently vacate in Europe. All I ended up doing is stay 4 days without internet before I found out how to fix the wifi problem manually, and one more week of hair-pulling frustration trying to automate that "fix" (which is not even a fix, it's just a workaround).

---

### Post by RoundSparrow on 2009-01-19
Thanks for posting this!  I was trying to reset my mouse drivers on 2.6.28-4 with eee pc and couldn't figure out why the acpi scripts were not working.  Your solution resolved my issue.

---

### Post by kevdog on 2009-01-20
Ok, happy for your solution but where does the resume script go?

---

### Post by pastalavista on 2009-01-20
I was going to recommend exactly that script. Had the same problem and found the solution on launchpad. This is why Ubuntu rocks.

---

### Post by hyperboloid on 2009-01-31
> **eugenia_loli said:**
>  
I am not trying to bitch here, it's just that this whole GNU/Linux usability/bugs/utils-being-moving-targets situation is frustrating as hell. All I wanted is to have a lightweight laptop with me these two weeks that I currently vacate in Europe. All I ended up doing is stay 4 days without internet before I found out how to fix the wifi problem manually, and one more week of hair-pulling frustration trying to automate that "fix" (which is not even a fix, it's just a workaround).

+1 to that!

If developers are going to change standard things (like /etc/acpi for suspend scripts) around randomly, first I say: WHY? and second, PLEASE REMOVE THE OLD LEGACY FILES SO THAT FOLKS IN USERLAND HAVE A CLUE WHAT IS GOING ON!!!

And some documentation - SOMEWHERE - might be nice.

---

### Post by vtdstein95 on 2009-04-01
Confirming this resolved the same issue on a Thinkpad T42 with integrated A/B/G Wireless using the ath_pci driver.

---

### Post by Tlynyrd on 2010-02-03
Can I try this script on my HP DV6700 as well? Having problem with wifi when coming out of standby, or opening lid...

---

