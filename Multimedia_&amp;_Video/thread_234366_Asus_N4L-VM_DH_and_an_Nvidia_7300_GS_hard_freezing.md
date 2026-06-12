---
title: "Asus N4L-VM DH and an Nvidia 7300 GS hard freezing"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by supradave on 2006-08-11
I just purchased a wide-screen monitor and found that the N4L-VM DH's i945gm graphics chipset was a little unclear so I purchased an Nvidia 7300 GS PCIe card.

Through the various lock ups, I have tried to keep track of what was going on at the time.  Most of the time, I'm in KDE with Firefox and Thunderbird and a couple of other apps running.  Other times, I'm watching a movie.  Other times, just sitting at the login screen.  Today, I decided to try something different, I stopped KDM so I could at least ssh into the box.  I started vncserver and less than 5 minutes later, the machine froze.

Unfortunately when it locks, I don't get any log entries.  I will attempt to update the BIOS this weekend and see if that helps.

Any other ideas on how to diagnose this problem?

I'm running Dapper with the latest updates and upgrades.

Thanks,
Dave

---

### Post by tseliot on 2006-08-11
Try this guide:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

---

### Post by supradave on 2006-08-11
Should this work with PCIe cards too?

---

### Post by tseliot on 2006-08-11
> **supradave said:**
> Should this work with PCIe cards too?

I think it could work.

The main problem is the integrated card.

---

### Post by supradave on 2006-08-29
Make sure to update the bios to the 702 version.  Seems to have fixed the problem.

If you need help updating the bios, in the manual, there's a page about ezbios setup that explains that you burn the bios to a CD or write to a floppy with a specific name and the updating process is fairly painless.

Now to figure out the problem of touching a slightly static charged USB cable to a PC that causes it to reboot.  

Thanks for the help.

---

