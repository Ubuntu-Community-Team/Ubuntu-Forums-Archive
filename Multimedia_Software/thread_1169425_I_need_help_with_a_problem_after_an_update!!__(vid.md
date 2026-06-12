---
title: "I need help with a problem after an update!!  (video included)"
date: 2009-05-25
forum: Multimedia Software
---

### Post by akd_inc on 2009-05-25
not sure what the problem is exactly. something to do with the video. i have restored xorg.conf from a few different backups already.. any other suggestions???

[http://ubuntuforums.org/showthread.php?p=7340990#post7340990](http://ubuntuforums.org/showthread.php?p=7340990#post7340990)

---

### Post by pastalavista on 2009-05-25
OK, I understand you're new here but you really shouldn't double post. Your first post would have been answered shortly.. weekends are the worse. At the first screen where it gives the option, press escape to show the grub menu and select. There you'll see all the kernels installed on your system. Choose the recovery mode (top one, lower ones are older kernels) and select 'fix x' or something like that and reboot. If you still have the problem, reboot, escape to grub and boot from the previous kernel. If that doesn't work, the only fix would be to boot from the live CD and see if you can repair the system, one of the options below the main list.. otherwise a reinstall may be in order and this time cancel the kernel update.

---

### Post by akd_inc on 2009-05-25
ok, im sorry about the double post. wasnt sure if i had put it in the right spot or not. wanted to make sure. 
i tried all those options previously without success. tried 3 different kernals with recovery running fix x
 there is no apt command to remove recent updates? like a rollback.
i know aptitude remove. but i dont know all the package names

i will start to download another copy of a live cd. hopefully that works.
a system reinstall will lose alot of work and custom settings.

any other suggestions in the mean time?

---

### Post by pastalavista on 2009-05-25
I feel your pain. I've done many reinstalls myself and love evey minute of it because Ubuntu allows you the freedom to do whatever you want and sometimes that's a bad thing but mostly it's a good thing.

In the root terminal you could try a few things:
```
sudo apt-get remove xserver-xorg --purge
```
the --purge will remove all configs. then:
```
sudo apt-get install xserver-xorg
```

but if you don't want to have to worry about driver issues, I'd recommend downloading, burning (and keeping a copy this time) an older version of Ubuntu, probably Hardy Heron 8.04 because it has long term support.

---

### Post by akd_inc on 2009-05-25
ok thank you, i will try that. I do have a habit of misplacing my dvd's countless copys have been made.This system is II but i will try HH and when i have it setup how i want it, i will turn off the updates. I really only did it for security reasons, dont want to miss an important patch. i guess i shouldnt be lazy and actually read the update info.  lol

never had these updaters and package installers in the 90's when i started using *nix, never had these problems.... although it did take hours sometimes days just to set up the xserver (for me anyways) i have a bald patch on my head from my bsd days too. so i really appreciate the Ubuntu project and all the support

---

### Post by akd_inc on 2009-05-25
THANK you VERY much. that did the trick. had to reboot in between in order to have access to my network adapter. but it worked perfectly! i am in your debt

---

### Post by pastalavista on 2009-05-25
I'm glad I could help. If you do a full reinstall (after you've gotten everything backed up, of course ;) there are some better ways to install. When you partition, create a seperate /home partition, large enough for all your personal data and settings. You could do well to keep the / directory about 10 gigs. That way, reinstalls are quicker because you only have to reformat 10 gigs and all your saved files are left alone (make sure you don't format them too! format /home box is UNchecked).. you can even experiment with different distros and not lose your stuff.. :D

---

