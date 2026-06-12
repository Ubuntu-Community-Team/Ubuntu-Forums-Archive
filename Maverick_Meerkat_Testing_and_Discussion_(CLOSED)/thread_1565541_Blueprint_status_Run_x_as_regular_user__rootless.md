---
title: "Blueprint status? Run x as regular user / rootless"
date: 2010-09-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by krazyd on 2010-09-01
here's the blueprint: 
[https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-maverick-rootless-x](https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-maverick-rootless-x)

Has anyone heard recently how this is going?

---

### Post by scorptig on 2010-09-09
OK I read

[https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-maverick-rootless-x]("https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-maverick-rootless-x")

[https://wiki.ubuntu.com/X/Rootless]("https://wiki.ubuntu.com/X/Rootless")

From what I gather, it's all in the way Graphic drivers are installed as user instead of root and more.

Should we switch to rootless-X for Maverick? was the Question, my answer is No. Let's have a POLL, and see what other Ubuntu users think.

I see no point in going this path, certain methods we have all grown familiar with is about to be changed, with no real benefits, the coding hours could be directed in to making Gnome work faster, by reducing clutter in the code, and debugging current release till there no bugs. yes aiming for zero bugs, why not.

If anything, having / root as administrator is a safety layer between user and root, removing this could bring some issues down the road such as security.

If we want more people to use Linux & Ubuntu, we need manufacturers to install OEM the system. We need the Retail PC stores to offer Linux.

Of course I convert people to Linux by installing it correctly for them, and one by one I have gained converts. And if the system was rootless it would make zero difference to their end user experience. Bottom line.

The thing one should realize is 95% of the people out there using a computer cannot install Windows, let alone installing Linux. 
These people need an OS pre-installed or a friend or relative that is a technical resource.

So I realize at this point and time, making Ubuntu and Linux easier for newbies, is a pointless venture. 
We the 1% of the world that use Linux realize installation is easier than ever, however note I use the alternate install, never the desktop version.

I've had people on their own try and install Linux from Desktop, they could not, their hard drive did not have sufficient space. Partitions to many is a new method of doing things, and they do not understand the fundamentals.

The whole thing boils down to Learning, taking time to read, test, and that takes X-Time, Months, Years. Not everyone using a computer is prepared to do that.

However I have no regrets that I did. ):P

---

### Post by Funnnny on 2010-09-09
I stopped tracking  this for a while, but the last time I read it, the developer thinks it's pointless.
Yes, run X as non-root is a feature for advance people, until there's a real benefit for everyone, they will not implement it

---

### Post by ranch hand on 2010-09-10
I think that you are not giving the "average user" (who ever that is) quite enough credit.  95% seems a high, harsh, figure.  I think it is more in the 75 to 80% range.  You could, unfortunately, be right.

I am on the fence on this X as user idea.  There is something that just makes me nervous about it but I can not think of a way that it would really be downgrading security even if it does "feel" that way.

It would make the istallation of drivers a little easier.

The idea that this may be the top of a slippery slope I had not considered.  This I heartily agree with you on being a bad thing.

---

### Post by VMC on 2010-09-10
> **scorptig said:**
> ...
The thing one should realize is 95% of the people out there using a computer cannot install Windows, let alone installing Linux. 
These people need an OS pre-installed or a friend or relative that is a technical resource.

...
More and more I'm beginning to realize this. You give a reply that is slightly bent toward technical - open terminal and type such&such. Either no response - deer caught in headlights, or what's a terminal. I'm over simplifying it, but I run into this time and again.

 When we stick with more advance users we tend to think, everyone is proficient. 

When 90% of computers run Windows, and Windows comes pre-installed. what do you expect.

On the other hand , I admire brick layers....

---

### Post by seeker5528 on 2010-09-10
> **Funnnny said:**
> Yes, run X as non-root is a feature for advance people, until there's a real benefit for everyone, they will not implement it

Rootless X is not a feature, it is a design decision.

The upstream worked a long time to reduce the amount of X stuff that requires root privileges, that was one of the big motivators for moving the DRM stuff into the kernel. With DRM handled by the kernel the amount of X that required elevated privileges was reduced significantly.

With the kernel part of the drivers gaining mode switching support, I believe that was one of the last big barriers, and rootless X seems like the next natural step, the less stuff running with root privileges, the better the security.

> **scorptig said:**
> From what I gather, it's all in the way Graphic drivers are installed as user instead of root and more.

The part that requires bare metal access will remain in the kernel, if that can be done in a way that eliminates the requirement for the part the remains in X to be run as root, that's just a refinement of what's already been done.

> If anything, having / root as administrator is a safety layer between user and root, removing this could bring some issues down the road such as security.

That's not relevant to whether X runs as root or not and with the possible exception of smaller form factor, single user devices, root isn't going anywhere as far as I can see.

Later, Seeker

---

