---
title: "MythBuntu LXC template?"
date: 2016-03-23
forum: Mythbuntu
---

### Post by mattlach on 2016-03-23
Hi all,

Does anyone know if there is a MythBuntu LXC template?

I currently have my MythBuntu backend running as a VMWare ESXi Guest, but I am - for a variety of reasons - planning to migrate to to ProxMox.

My virtualized server is always bumping up against its RAM capacity, so I figured this migration would be an excellent opportunity to convert all of my Linux based guests to containers using LXC instead of just converting them to KVM VM's.

While my server is a home server, it is a home production server of sorts serving as - among other things - my router, firewall, and sole source of TV through MythTV (people in house get unhappy if the TV and internet go down at the same time) so I don't currently have a play environment to learn from.   Once the server goes down for migration, I am under the gun to get everything back up again.

So, my questions are as follows:

[LIST=1]
[*]Typically when creating a container one chooses from provided templates that are downloaded and installed.   The Ubuntu template allows you to specify specific sub-versions of Ubuntu to be installed.   Is MythBuntu one of them?

[*]Is anyone aware of a way to either convert an install ISO to an LXC template, or otherwise install an install ISO into an LXC container?

[*]If not, and I instead just create a basic 64bit Ubuntu 14,04 LTS server install, is there a good guide that can walk me through installing and configuring everything that makes MythBuntu MythBuntu, starting with a blank slate server install?  It would have to include getting the desktop environment up and running, installing the MythBuntu Control Center, mythbuntu itself, etc. etc.

[*]There are many guides on blogs out there speaking to converting both bare metal and VM Guest installs into LXC containers.  They all involve manually copying the root file system into a container, excluding system mounts (what these are vary from guide to guide, but IO assume like /proc and /boot are among them) and then uninstalling unneeded packages afterwards.  Problem is these guides don't agree among themselves, and none of them have a comprehensive list of which packages wind up being unneeded in an LXC container.  I would go down this route, but it just isn't giving me the warm fuzzies right now.
[/LIST]

I'd appreciate any thoughts anyone might have on this subject of getting a MythBuntu-like experience inside an LXC container.

Much obliged,
Matt

---

### Post by mattlach on 2016-03-24
So,

After some further research, I am partway to a solution.   First let me clarify that this is for a dedicated headless backend.  All video playback will occur on dedicated frontends.

It looks like I should be able to set up a working desktop environment in a 64bit 14.04 server install using xvfb and vnc4server.   I'm not entirely clear how to do this yet. Apparently xvfb replaces the xserver, and only renders in memory, and doesn't try to output to a screen.  Then I can remotely manage it using VNC, or tunnel X through SSH.  

It is unclear to me how I would use apt to do this though.  I'd imagine that if I try to install LXDE or XFCE using apt, this will pull in the x server as one of its dependencies.  How can I tell it to not do this, and install xvfb instead?

Either way, once I have a working xvfb based desktop environment managed remotely via VNC, I gather [from the mythbuntu webpage](http://www.mythbuntu.org/existing-ubuntu) that all I need to do is install mythbuntu-control-centre, and it pulls in all of the MythTV stuff as configured by the MythBuntu project.    Is this accurate?

Any thoughts at all on this would be greatly appreciated.

Thanks,
Matt

---

