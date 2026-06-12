---
title: "Mouse and remote not working after kernel security fix install"
date: 2009-10-04
forum: Mythbuntu
---

### Post by ffaker on 2009-10-04
OK: so I've have my box running MythTV on Jaunty working for a while now ([see my guide]("http://www.winstanleys.org/tech/mythtv/")).

Unfortunately, today there was a kernel security patch pushed to my Jaunty box. I installed it (along with a bunch of other updates) and now my remote is not working.

Now normally, when I have a security update to the kernel, I recompile and reinstall the drivers I had to install to get my remote working in the first place ([see this thread]("http://ubuntuforums.org/showthread.php?p=7247731#post7247731")).

However, this time it's not working for some reason. I have also tried downloading the newest version and compiling and installing that: all to no avail.

The weird thing is that the "input: IR-receiver inside an USB DVB receiver..." is still there when I run dmesg. So it seems not to be a problem with the drivers. But it seems something else is stopping the remote from working (no response when I run the irw command either, so it's not a problem with my lircrc).

I've checked the batteries and it's not that.

Another weird symptom, is that" when I run the MythTV frontend, my mouse is frozen. When I close the frontend, the mouse works again. Very odd, not sure if it's connected to the remote issue or not.

Any ideas?!? I miss my MythTV remote :(

---

### Post by ffaker on 2009-10-07
BUMP.

Any ideas?

---

