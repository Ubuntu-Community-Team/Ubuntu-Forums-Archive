---
title: "repository added - but no WICD"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by mookie60 on 2009-04-25
background:
I've been using (dual boot) 8.10 since it's release and had no problems with network manager.   A recent infection in on XP forced me to wipe and start over, this time trying 8.10 (super ubuntu) as the main OS and XP running in virtualbox.

I'm not sure what may have changed with network manager, but it's intermittent at best (wired works fine).  So I decided to try Wicd.

the problem:
I've added the repository and key as stated on the wicd site - pretty simple as I've added similar repositories before.  Other websites and forums basically quote from Wicd's instructions.   But when I enter wicd in Synatptic's search, it doesn't find it.  When I "reload", there are no errors about needing a keyfile.

Any ideas why it's not found in Synaptic?


Thanks for any assistance,
John

---

### Post by snowpine on 2009-04-25
Try the following from the terminal:

```
sudo apt-get update
sudo apt-get install wicd
```

There is a bug with the Synaptic search feature: [http://ubuntuforums.org/showthread.php?t=1134850](http://ubuntuforums.org/showthread.php?t=1134850)

---

### Post by mookie60 on 2009-04-25
Thanks, it was there afterall.   It also seems to be working much better than network manager.

Thanks again,

John

---

### Post by speedwell68 on 2009-04-25
Just to say really, Wicd is included in the default repositories in 9.04.

---

