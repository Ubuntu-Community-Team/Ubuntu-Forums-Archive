---
title: "upgrade from mythbuntu 10.04 to 12.04, backend now not auto-starting"
date: 2014-03-07
forum: Mythbuntu
---

### Post by wayover13 on 2014-03-07
I decided finally to take the plunge today and upgrade my 10.04 mythbuntu to 12.04. It did not go hitch-free: I resolved a couple of more minor issues but one that I've been unable to analyze persists. Namely, the backend on this combination FE/BE machine will not auto-start when I reboot the machine.

My issue is a little like the one described in this thread: [http://ubuntuforums.org/showthread.php?t=2106554](http://ubuntuforums.org/showthread.php?t=2106554) . That is to say that, after the machine boots and brings up the FE, and I get the complaint about the FE being unable to connect to the BE, if I ssh in and manually run sudo mythbackend, the BE starts and the system runs hunky dory, just as it has been for the last couple of years. But somehow the BE won't start itself on boot and I'm not sure why.

Can anyone help me troubleshoot and resolve this issue? I've got a workaround for now, but I want to get this system back into GWO. Thanks

---

### Post by wayover13 on 2014-03-07
I think I may have resolved this--at least on the last reboot I did not get the "could not connect to the backend" error message. In my continued searching on the issue I ran across a post on these forums (see [http://ubuntuforums.org/showthread.php?t=2202457](http://ubuntuforums.org/showthread.php?t=2202457) ) that mentioned upstart scripts and a sample on the mythtv wiki. Then I came upon this page [http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration) which does, indeed, give a sample. I found the directions on the wiki a bit confusing, but what I ended up doing was moving /etc/init/mythtv-backend.conf to /etc/init/mythtv-backend.conf-old. Then I created a new /etc/init/mythtv-backend.conf and pasted into it the content of the sample file given on the wiki (didn't do any symlinking, as they instruct). Once I rebooted, the machine has come up with no complaints from the FE about not being able to connect to the BE. So, fingers crossed, this step may have resolved the problem.

---

