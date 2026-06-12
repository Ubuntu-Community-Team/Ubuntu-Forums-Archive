---
title: "Another No Sound Thread, ATI HDA SB450, Toshiba Laptop"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by fidibidabah on 2008-02-23
Hi. Just to get this out of the way first. Yes my laptop has a physical volume control, it has been turned all the way up during my troubleshooting process. Yes, I know what alsamixer is and how to make sure my speakers aren't muted.

Here are the appropriate specs. Ubuntu 7.10, fresh install, on a Toshiba a105-s2011 laptop. All updates are current, downloaded, and installed with no errors. Soundcard is built in, speakers are internal. Soundcard is ATI HDA SB450 ALC861 (possibly ALC861VD), I have read through, and tried in every possible manner, all of the suggestions in the official sound troubleshooting guides.

Here's what I know my problem ISN'T:
Speakers aren't muted.
My sound card SEEMS to be supported according to ALSA (ATI HDA SB450 ALC861(VD))
DSDT, I have ruled out DSDT incompatibility because if I pass acpi=off on boot, it doesn't restore my sound. I've also decompiled my DSDT and found none of the common problems associated with Toshibas (like the l30 or l35). Please call me out on this if it's faulty reasoning.
I've recompiled and reinstalled new ALSA drivers in every way imaginable.

Things my problem COULD BE:
I may need to custom install my ALSA drivers with a certain patch. I've played with a few things but I'm not familiar enough with ALSA to really understand how to mess with stuff, I've just followed others suggestions.
I made need to add something to alsa-base or a similar file. I've tried many things, but all of the "options snd-hda-intel model=" commands always error out when i modprobe snd-hda-intel. It seems to ignore those lines I've added because of something or other.
My problem could also be something I haven't thought of yet, because I'm not very intelligent. That's why I'm asking you genius people.

Sorry if I sound at all arrogant, I'm just very frustrated. I'm spoken to a zillion people and read atleast 4 or 5 dozen threads.

I'll take any and all suggestions. If you need any values of any specific commands or hardware info, just let me know what it is and how to find it. Thank you very very much.

---

### Post by hotmonkeyluv on 2008-02-23
I had the exact same problem, and got around it by installing debian on another partition (the sound worked with debian - go figure) and then copying the /etc/modprobe.d directory from debian straight to the ubuntu /etc/modprobe.d. Don't forget to make a backup! If your wireless isn't working, then copy the backup file: /etc/modprobe.d.backup/ipw3945 to /etc/modprobe.d and overwrite the one that was there (if there was one there).

---

### Post by mix1080 on 2008-02-23
Hi,
I recently spent a little time troubleshooting a similar problem; Seems my system selects earphone output as a default. 
I've yet to diagnose between a hardware fault in the earphone socket and the driver configuration. 
I'm currently happy to plug and unplug the earphones when I need speaker output 
as I am working through Firewire (Behringer FCA202) connection problems with Rosegarden. 
Using Sony laptop, Core duo T7100 processor, 2 GB ram, ATI mobility Radeon 2300 graphics, Ubuntu 7.10 (NOT Vista).....freebob, qjackctl, jack, rosegarden.

---

### Post by fidibidabah on 2008-02-23
> **hotmonkeyluv said:**
> I had the exact same problem, and got around it by installing debian on another partition (the sound worked with debian - go figure) and then copying the /etc/modprobe.d directory from debian straight to the ubuntu /etc/modprobe.d. Don't forget to make a backup! If your wireless isn't working, then copy the backup file: /etc/modprobe.d.backup/ipw3945 to /etc/modprobe.d and overwrite the one that was there (if there was one there).

Well that sounds interesting. Is there any way you could get me a tar of that directory possibly? I only ask because installing debain would be relatively uncomfortable in my current situation, although possible. I only ask, when you say "exact same problem", do you have similar or identical specs?

---

### Post by fpscott on 2008-02-23
What worked for me with my HP Pavilion DV9700 laptop, and also for a friend with a Dell laptop with the same problem, was to open terminal and type the following line. You'll be asked for your root password. After this finishes installing, reboot your computer, and you should have sound. Good luck!

sudo apt-get install linux-backports-modules-generic

Frank

---

### Post by hotmonkeyluv on 2008-02-24
I have a toshiba a105, and I think I have the same soundcard as you said. I don't know how to make a .tar of anything, so if you tell me, I'll make one and upload it for ya. (unless fpscott's idea works)

---

### Post by knattlhuber on 2008-02-24
> **fpscott said:**
> What worked for me with my HP Pavilion DV9700 laptop, and also for a friend with a Dell laptop with the same problem, was to open terminal and type the following line. You'll be asked for your root password. After this finishes installing, reboot your computer, and you should have sound. Good luck!

sudo apt-get install linux-backports-modules-generic

Frank

Thanks, man! That tip also worked for me on my HP DV9748.

---

### Post by stedevil on 2008-03-06
I have fully working sound on my 
Toshiba Equium L30-149 (PSL35E-002002N5) with the ATI SB450 (ACL861VD) soundchip

Read more here
[http://ubuntuforums.org/showthread.php?p=4462175#post4462175](http://ubuntuforums.org/showthread.php?p=4462175#post4462175)

---

