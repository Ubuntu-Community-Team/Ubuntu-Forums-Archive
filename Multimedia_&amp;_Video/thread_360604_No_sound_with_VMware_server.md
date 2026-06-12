---
title: "No sound with VMware server"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by cybrkup on 2007-02-13
I'm on Xubuntu. Sound works fine for me until I open my winxp virtualization on Vmware server. I get the error msg below.

> Failed to open sound device /dev/dsp: Device or resource busy
Failed to connect virtual device sound.

Any ideas on how to fix this? I haven't an idea where to start. Thanks.

CybrKup

---

### Post by veloce on 2007-02-13
In the setting for the vm sound do you have it set to "auto" or did you select the interface manually?

---

### Post by cybrkup on 2007-02-13
> **veloce said:**
> In the setting for the vm sound do you have it set to "auto" or did you select the interface manually?

Good question. I set it to Auto.

---

### Post by veloce on 2007-02-13
No solution there then, I was hoping you had manually selected one that wasn't working.

I assume that sound is working outisde vm server?  
Do you have anything running that is using sound as you start? If yes try turning it off, if no, try turning something on!

---

### Post by GoingDown on 2007-02-14
Try to kill esd sound server before starting vmware. I don't have any idea if it is actually running on Xubuntu, but at least it is on stock Ubuntu.

```

killall esd
vmware

```

---

### Post by Fungyo on 2007-02-14
Can't say this will solve your problem but it got sound working with my vmware xp pro inside edgy.

Check this thread:

[http://ubuntuforums.org/showthread.php?t=305306&highlight=vmware]("http://ubuntuforums.org/showthread.php?t=305306&highlight=vmware")

---

### Post by cybrkup on 2007-02-14
Yes, sound does work fine outside of VMWare. 

I tried killing ESD, but it wasn't running at the time. I have subsequently installed it per another troubleshooting thread, but that hasn't made a difference. 


> **Fungyo said:**
> Can't say this will solve your problem but it got sound working with my vmware xp pro inside edgy.

Check this thread:

[http://ubuntuforums.org/showthread.php?t=305306&highlight=vmware]("http://ubuntuforums.org/showthread.php?t=305306&highlight=vmware")

Tried these suggestions as well. No luck. 

The sound is turned up in vmware windows emulation, but I don't suppose that matters since I still get the error msg. 

Other ideas?

---

### Post by coldvodka on 2007-11-25
It didn't work for my virtual XP on VMWare Server when I had it set on Auto. I switched it to use the actual /dev/dsp and worked fine. Trying to set it up the same way on my server2k3 vm.....

---

### Post by hamid.nyc on 2008-03-24
Before trying anything exotic like replacing libraries, etc, it might prove useful to try to add a sound device directly in VMWare Server under VM\Settings\Options and by clicking on the Add button before powering on your Virtual Machine. You won't be able to do this after the VM is powered and up and running. There are several "Devices" that are offered, all Virtual of course...

---

