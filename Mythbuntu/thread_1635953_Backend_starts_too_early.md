---
title: "Backend starts too early?"
date: 2010-12-02
forum: Mythbuntu
---

### Post by koma77 on 2010-12-02
I've got a problem with my freshly installed mythbuntu.

(Almost) every time after a reboot the backend fails to access the tuner (Hauppage 1900). In the log I can see a "pemission denied" for /dev/video0

However, restarting the backend resolves the issue.

I don't know why this is happening but a theory is that maybe the backend gets started too early by upstart. And maybe the hauppage module is not done initializing the tuner and downloading its firmware?

What do you think, could that be possible?

If so, how can I delay the upstart of the backend a little? Ideally it would be triggered by mysql and the tuner driver being started OK...

---

### Post by ian dobson on 2010-12-02
Hi,

It could happen that the backend starts before the tuners are setup. I just use a pre-start delay script :-

pre-start script
        sleep 5;
end script

in my /etc/init/mythtv-backend.conf or maybe just change your start line for mythbackend to include udev finish

start on (local-filesystems and net-device-up IFACE=lo and **started udev-finish**)

Regards
Ian Dobson

---

### Post by koma77 on 2010-12-02
The upstart script already is:

start on (local-filesystems and net-device-up IFACE=lo and started udev-finish)

from the start, so that not do the trick.

I'll see if a pre-start script works better.

Thanks for your ideas!

---

### Post by CoolDreamZ on 2011-02-18
I am having a similar problem with the Nebula DigiTV card. These two bug reports may also be relevant to your situation:

[https://bugs.edge.launchpad.net/ubuntu/+source/mythtv/+bug/556204]("https://bugs.edge.launchpad.net/ubuntu/+source/mythtv/+bug/556204")

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/368215]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/368215")

---

