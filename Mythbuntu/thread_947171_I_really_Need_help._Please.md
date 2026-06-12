---
title: "I really Need help. Please"
date: 2008-10-14
forum: Mythbuntu
---

### Post by dvbspider on 2008-10-14
I was runing mythbuntu 8.04 ,

when I install frist time everthing was fine ecxept Sound NO Sound, I post here so many time and never get help,..

Well anyways I decide to re-install 8.04 , for my luck this time won'T boot now.

this is unbelivable I have been try so many time same problem show u.

I am getting this:

Loading please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/f80b80ed-1cb3-449f-b7e5-363fc8bf2217)=sda5(8.5)
kinit: trying to resume from /dev/disk/by-uuid/f80b80ed-449f-b7e5-363fc8bf2217
kinit: No resume image, doing normal boot...

Ubuntu 8.04.1 space-desktop tty1

space-desktop login:


I have this AMD 2 core board UG7-HT PRO
AMD 64 Dual Core 690G chip set
Nvida G720

Please need help

---

### Post by ahood on 2008-10-14
Maybe the link below will lead to an acceptable solution..

[https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148)

At the last prompt message above, type any of the following key combinations and see if it boots...

enter

or

ctrl + alt + delete

Other solutions are reported at the link above.

Hope this helps.

---

### Post by dvbspider on 2008-10-14
but, one of the quesion I do my self, is...?

how can be possible after working the frist time and boot normaly work fine,, and ofcourse with out AUDIO, is the reason , 

I re-install aging to latest version..

Also I did a Test with the old dvd 8.04 and same problem. :(

---

### Post by netmanny on 2008-10-14
I had a similar problem once before...... mi solution was to get in to the bios and reset to default.... For some reason the bios was change some how .
I was able to boot just fine after that.
I hope that helped.

---

### Post by dvbspider on 2008-10-15
I dont, now I have been try so many possible solution, and nothing..

eider the mythbuntu developer post nothing here..

I don't understand how come this is possible..

when i install fristime boot and fast, 

Now the dam error show up

Loading please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/f80b80ed-1cb3-449f-b7e5-363fc8bf2217)=sda5(8.5)
kinit: trying to resume from /dev/disk/by-uuid/f80b80ed-449f-b7e5-363fc8bf2217
kinit: No resume image, doing normal boot...


Where I can get help???

I dont now,, but I think when the Installation is in process is getting update from the Internet,, if that is the issue, Is possible the BUG is coming from the net,..

I will try out with out Lan cable conected.

---

### Post by SiHa on 2008-10-16
It sounds to me like you have a hardware fault. Have you tried the obvious - unplug and reseat everything that plugs into your motherboard. Perhaps you have a faulty stick of RAM? If you have two sticks, try taking one out and booting. If the problem persists, try with the other one.

From the LiveCD, there is a 'Run Memtest' option in the install menu, if you can get the system to boot from that CD, try that.

You can run Mythbuntu from the LiveCD as a diskless client, have you tried to do that? If that boots succesfully, it mught suggest your HDD is up the spout.

If your HDD is a Maxtor, you could try the PowerMax windows utility (assuming you have a Windows PC to try it on) to see if the HDD is faulty. I expect other manufacturers have their own utils available too.

Have you got any spare RAM you can swap in from a known good PC?

Have you got an old HDD lying around to try the install on?

Sorry that's all a bit disjointed, it's a bit of a brain dump. The above is a list of the things I would try (in roughly that order) to diagnose the fault.

HTH

Simon

---

