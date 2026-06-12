---
title: "Mythbuntu 9.10 channel scanning with DVB-C card not working"
date: 2009-11-04
forum: Mythbuntu
---

### Post by davetibbs on 2009-11-04
Hi All

Hopefully someone can help me with this - I have been successfully running a Mythbuntu 9.04 install for a while and decided to upgrade to Mythbuntu 9.10.  Since I wanted to fiddle about with partitions I decided to do a clean install (after a DB backup) which went fine.

The DVB-C card wasn't loaded according to dmesg as dvb-ttpci01.fw didn't exist in /lib/firmware.  Once I put that in there, the card was detected and I was able to scan channels using the "scan" command line app but mythtv doesn't find anything with "signal timeout".

I then decided to put 9.04 back on there, scan all channels in Myth (which worked) and then upgrade to 9.10, but I found that after the upgrade it won't boot into X and just shows the login prompt rapidly flashing on the screen.

I think a clean install is the way to go on this, but does anyone know how any tips for getting the channel scanning working?

Thanks

Dave

---

### Post by mookie60 on 2009-11-06
mr. tibbs,

sorry to say, but i have no answers, just a similar problem.   9.04 works fine, 9.10 doesn't.   i have a hauppauge 1600.  installation proceeds normally until it's time to scan.  i haven't tried the commandline scan yet (just heard about it), been using the one in the setup/config.   the 1600 analog tuner stops abruptly at channel 16 and won't continue (these channels can at least be viewed thru myth).   the digital tuner just gets those "signal timed out" msgs as you mentioned.  

i've given up and gone back to 9.04 and all is well again.

i'll watch your thread and hope for some answers.

john

---

### Post by davetibbs on 2009-11-06
I've found the problem - I was using a plugin, the mentioning of which is probably frowned upon over on these forums, and it won't work under the kernel that ships with Mythbuntu 9.10 (2.6.31).  I've gone back to 9.04 and an earlier kernel and all is well again!

---

### Post by sawbuck on 2009-11-06
I'm having an upgrade issue with my HVR 1600 not being recognized -  fine in 9,04 b\ut dead in 9.10 - and I'm sure I have the latest kernel.  What is the "plug-in"?  I did have some edits I made to xorg.conf and menu.lst in 9.04 that I responded to "keep" during the upgrade.

I guess the question here is how do you go back to the old kernel if it has been over deleted by upgrading to 9.10?

---

### Post by davetibbs on 2009-11-06
The plugin is open-sasc-ng.  I'm just guessing when I say mentioning it is frowned upon.

I tried installing an official ubuntu 2.6.30 linux-image and linux-headers .deb packages and then changing GRUB to boot to that kernel, but for some reason I lost sound doing that, hence going back to 9.04.

---

### Post by zingo on 2009-11-10
#58 in theire bug database handles compiling for kernel 2.6.31 but it is not completly solved yet, but please check it out.

I also lost sound when I switch to 2.6.30, did you manage to solve that problem? 

And there is leagal ways to use the SW like with a cardreader with a subscription card (and maybe outside US I don't know if this goes under some strange copyright act) so I don't see why it needs to be "frowned upon" but I have seen that it has before and not just on this forum. It would be nice if someone compiled together a cardreader only version that could be included in distibutions and discussed without problem.

---

### Post by zingo on 2009-11-17
Here is a solution for the device if you want to use the 2.6.30 kernel
[http://ubuntuforums.org/showthread.php?t=1322019](http://ubuntuforums.org/showthread.php?t=1322019)

---

