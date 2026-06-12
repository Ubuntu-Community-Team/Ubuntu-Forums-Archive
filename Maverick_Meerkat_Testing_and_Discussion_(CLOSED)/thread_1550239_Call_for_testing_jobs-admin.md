---
title: "Call for testing: jobs-admin"
date: 2010-08-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jpeddicord on 2010-08-10
Hello all,

Google Summer of Code ends this week, which indirectly means that jobs-admin is now ready for testing! Interested testers need only to add [a PPA]("https://launchpad.net/~jpeddicord/+archive/jobs") and install a package to begin. Within a few days the packages will be available in maverick universe.

```
sudo add-apt-repository ppa:jpeddicord/jobs
sudo apt-get install jobs-admin
```

Essentially, jobs-admin is a replacement for services-admin. Upstart support has been added, along with the ability to change settings on individual services. For example, you can tweak simple firewall settings or enable and disable Apport.

jobs-admin may be launched from the terminal, or can be found under **System > Administration > System Jobs**. We've hidden most jobs/services that are essential to your system, so ideally you shouldn't be able to break anything even if you wanted to. With that in mind, feel free to give it all a stress test. Shut off jobs you don't want, and change the settings of others. By testing this you'll also be testing jobservice, the daemon which powers it all. Think of jobservice as a "PackageKit" for system services: it's a generic backend to manage jobs no matter whether a system is running Upstart or a basic System V setup.

Bugs can be reported on Launchpad:
    [http://bugs.launchpad.net/jobsadmin](http://bugs.launchpad.net/jobsadmin)

We're also open for translating:

[LIST]
[*][https://translations.launchpad.net/jobsadmin](https://translations.launchpad.net/jobsadmin) - for most UI elements
[*][https://translations.launchpad.net/jobservice](https://translations.launchpad.net/jobservice) - for job settings
[/LIST]

Any and all feedback is welcome. We'll have a bugfix release in the next few weeks. I won't be responding to reports or feedback until August 16 (Monday), however.

For Maverick, you'll be able to install jobs-admin and have easy access to your system's services. The PPA will be maintained so Lucid users aren't left out. We're hoping to make this the de-facto utility (and framework) for managing services and jobs, and hopefully you'll see this in-place as the replacement for the missed services-admin in 11.04. I'll be working on getting these packages into Debian as well.

Thanks for your attention!

---

### Post by castrojo on 2010-08-10
Can you link to your proposal? I'd like to read an overview of what you're trying to accomplish, thanks!

---

### Post by jpeddicord on 2010-08-11
> **whiprush said:**
> Can you link to your proposal? I'd like to read an overview of what you're trying to accomplish, thanks!

Yeah, I realize I didn't make it too clear at first. Updated the first post, as well as the post on Planet.

[https://wiki.ubuntu.com/GSoC/2010/JacobPeddicord](https://wiki.ubuntu.com/GSoC/2010/JacobPeddicord)

Basically, this is a replacement of the previous services-admin with Upstart capabilities and the ability to tweak settings on individual services.

This varies in a few ways: it *is* separate from services-admin; using projects named jobs-admin and jobservice.

Other deviations were made with regards to implementation, and choice of small features.

---

