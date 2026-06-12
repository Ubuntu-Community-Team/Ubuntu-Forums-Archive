---
title: "System not going to sleep"
date: 2008-10-06
forum: Mythbuntu
---

### Post by eddypolak on 2008-10-06
I have had sleep/wake working perfectly but now the machine won't go to sleep reliably. I am using the setting in the Mythbackend with the command 'sudo shutdown -h -P now'. This command works if I type it into a terminal so I suppose there is something active I am not aware of that is interfering with the countdown.

Perhaps it was as I explored and installed some other apps (since uninstalled) that I've left something behind that's keeping the machine busy. I know of 'top' for looking at active processes but do not have the knowledge to interpret the output or how to copy it into this post.

Any help would be appreciated. Please note that my Linux skills are minimal...

---

### Post by eddypolak on 2008-10-08
I have done some tests. Going to sleep with the timout set to 120 or 300 seconds seems to work every time. Set the timout to 600 seconds and the system never goes to sleep, (although it used to). With timout set at 300 secs I have set a recording of 10 mins and it went to sleep correctly after that. In other words its not as if setting a short timout simply works because some interfering process has not yet started.

If anyone would find it useful I can now post the output that lists the processes running on my machine.

A short timout would be OK if I could stop the machine sleeping while I am doing other stuff on it. I read in the tutoral that logging onto a ssh session would stop it sleeping. I am afraid I dont know how to do that, being a Linux novice. Could someone tell me please or perhaps suggest a more elegant way to achieve this.

The final issue relating to sleep is how to stop the Mythbuntu machine going to sleep whilst it is serving recordings via upnp to by PS3. The system is very good as it is but making upnp truly practical would be the icing on the cake.

Thanks in advance for any help that might be offered.

---

