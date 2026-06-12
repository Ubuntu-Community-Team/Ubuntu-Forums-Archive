---
title: "Mythbuntu 11.04 Hard drive always accessing"
date: 2011-10-01
forum: Mythbuntu
---

### Post by sqeelurgle on 2011-10-01
I have a brand new 11.04 installation that is straight (no additions).  The hard drive access light is now on literally all the time.  Not something I am used to with earlier versions.  Is this normal?  If not then what can I do to start finding out the problem?

Thanks

---

### Post by thatguruguy on 2011-10-01
How much memory does your computer have?

What is the myth backend log telling you?

---

### Post by sqeelurgle on 2011-10-01
I have 1GB of RAM, which has always been sufficient in the past (mythbuntu 9.10 and 10.04).  The backend log has errors about missing files (some idiot forgot to plug the antenna into the tuner and it recorded a whole bunch of nothing) and also errors about sudo not working for the shutdown sequence for setting wakeup time for ACPI wakeup.  I need to look into that, because the script is definitely set to NOPASSWD in sudoers.

---

### Post by sqeelurgle on 2011-10-01
Woops.  Think I know what was going on.  The drive LED seems to be always lit a little, but gets brighter again when the drive is being accessed.  That behaviour is new, but seems OK.  Just different.  Now to sort out that sudo problem with shutdown.

---

### Post by Tim L on 2011-10-02
A few weeks ago I installed a new 2TB hard disk and found that after a few hours the disk activity light came on permanently. On rebooting it would work properly for a few hours and then the LED would come on permanently. Having no idea what to do I updated the Mother Board Bias and the problem was solved.

---

