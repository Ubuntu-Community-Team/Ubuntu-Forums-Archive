---
title: "Installing nvidia-glx-new from Hardy on Gutsy"
date: 2008-06-16
forum: Multimedia Software
---

### Post by NTolerance on 2008-06-16
I'm having several issues with Hardy such as Firefox/Flash crashes.  

I want to go back to Gutsy, but Gutsy had a major issue with my NVidia 7400 Go.  I had to manually install the NVidia drivers to prevent a crashing/black screen flashing issue that's present in the stock Gutsy nvidia-glx-new package.  This solved the problem but was a continuing issue because the drivers would have to be manually re-installed every time a new kernel update was installed.

My question is this:  Can I take the Hardy nvidia-glx-new DEB and install it on Gutsy?  I'd like to know if this is feasible before I go off reformatting.  Thanks!

---

### Post by NTolerance on 2008-06-17
bump

---

### Post by chrisccoulson on 2008-06-17
No you can't take the nvidia-glx-new package from Hardy and install it on Gutsy. nvidia-glx-new will depend on packages that have a higher version number than those in Gutsy (for example, it will require the newer linux-restricted-modules, which will require the Hardy kernel. It will also require the Hardy libc6, which will completely break a Gutsy system). Adding Hardy repositories to a Gutsy system and installing packages from it will probably cause Hardy libraries to be installed, creating a dependency nightmare. Plenty of people on here have done this and completely broken their systems.

When installing binary pacakges, only use repositories and software sources containing packages compiled for your system.

Source compatibility != Binary compatibilty

If you want the newer NVIDIA drivers, use Envy or install manually from NVIDIA's website.

---

### Post by NTolerance on 2008-06-17
> **chrisccoulson said:**
> No you can't take the nvidia-glx-new package from Hardy and install it on Gutsy. nvidia-glx-new will depend on packages that have a higher version number than those in Gutsy (for example, it will require the newer linux-restricted-modules, which will require the Hardy kernel. It will also require the Hardy libc6, which will completely break a Gutsy system). Adding Hardy repositories to a Gutsy system and installing packages from it will probably cause Hardy libraries to be installed, creating a dependency nightmare. Plenty of people on here have done this and completely broken their systems.

When installing binary pacakges, only use repositories and software sources containing packages compiled for your system.

Source compatibility != Binary compatibilty

If you want the newer NVIDIA drivers, use Envy or install manually from NVIDIA's website.

Thanks for the information.  This saved me from finding out after trying a complete re-install.  

I did the manual install from NVidia's site when running Gutsy, but had to re-do it every time a new kernel update came out.  Is there any sort of way to make the drivers persist when a new kernel is released?  Thanks.

Edit:  I wonder if any kind souls figured out how to make a Gutsy DEB of newer NVidia drivers if it is even possible.  It's a shame that the official repos never introduced any NVidia driver updates for Gutsy.

---

### Post by NTolerance on 2008-06-18
bump

---

### Post by NTolerance on 2008-06-19
bump

---

### Post by chrisccoulson on 2008-06-19
If you install the NVIDIA drivers using a method other than from the official repositories, then you can't avoid having to re-install the drivers for each new running kernel.

The NVIDIA drivers in Gutsy haven't been updated because in general, none of the updates to the NVIDIA driver qualify for a SRU (see [https://wiki.ubuntu.com/StableReleaseUpdates]("https://wiki.ubuntu.com/StableReleaseUpdates")). Being proprietary, it isn't a good idea to introduce a new NVIDIA driver in to a stable release unless absolutely necessary, especially as it affects something as critical as X.Org. Doing this introduces unneccessary risk for a stable release.

Your best bet to get the latest NVIDIA drivers on Gutsy is to use Envy.

---

### Post by NTolerance on 2008-06-19
> **chrisccoulson said:**
> If you install the NVIDIA drivers using a method other than from the official repositories, then you can't avoid having to re-install the drivers for each new running kernel.

The NVIDIA drivers in Gutsy haven't been updated because in general, none of the updates to the NVIDIA driver qualify for a SRU (see [https://wiki.ubuntu.com/StableReleaseUpdates]("https://wiki.ubuntu.com/StableReleaseUpdates")). Being proprietary, it isn't a good idea to introduce a new NVIDIA driver in to a stable release unless absolutely necessary, especially as it affects something as critical as X.Org. Doing this introduces unneccessary risk for a stable release.

Your best bet to get the latest NVIDIA drivers on Gutsy is to use Envy.

I'd argue that lockups and constant black screen flashing is a severe regression:

> Bugs which represent severe regressions from the previous release of Ubuntu. This includes packages which are totally unusable, like being uninstallable or crashing on startup.

Over time it appears that anyone using a Geforce 7300/7400 Go on their laptop was affected.  

But I guess that the whole binary-only thing is, of course, taboo.  This is the nature of things and I understand that.  

Anyways, I guess my final question before I put this whole thing to bed is this:  is there a technical reason that prevents a third party from building a DEB file of updated NVidia drivers?  Wouldn't a working DEB prevent the whole kernel update issue?

Thanks again for helping to answer my questions.

---

### Post by chrisccoulson on 2008-06-19
There is nothing preventing a third party from creating a DEB package, but that is exactly what Envy does. But you would still need a DEB package specific to the running kernel, which means building and installing a new DEB for each new kernel. When you get a kernel update in Ubuntu, you also get a new linux-restricted-modules package for that kernel automatically, which contains the NVIDIA kernel module built for that kernel. This happens transparently, which is why you don't notice it.

Is there a bug report for your problem? Your type of problem might qualify for a SRU if there are enough people with that problem.

Note that the situation in Hardy is improved somewhat for the NVIDIA drivers. Envy is in the repository now and when you install the latest drivers using it, it works as transparently as the official nvidia-glx-* packages with regards to kernel updates (I think). This means that people can choose to use the latest drivers if they want to, without Ubuntu having to update the nvidia-glx-* packages.

Hope that helps

---

### Post by NTolerance on 2008-06-19
> **chrisccoulson said:**
> There is nothing preventing a third party from creating a DEB package, but that is exactly what Envy does. But you would still need a DEB package specific to the running kernel, which means building and installing a new DEB for each new kernel. When you get a kernel update in Ubuntu, you also get a new linux-restricted-modules package for that kernel automatically, which contains the NVIDIA kernel module built for that kernel. This happens transparently, which is why you don't notice it.

Is there a bug report for your problem? Your type of problem might qualify for a SRU if there are enough people with that problem.

Note that the situation in Hardy is improved somewhat for the NVIDIA drivers. Envy is in the repository now and when you install the latest drivers using it, it works as transparently as the official nvidia-glx-* packages with regards to kernel updates (I think). This means that people can choose to use the latest drivers if they want to, without Ubuntu having to update the nvidia-glx-* packages.

Hope that helps

Ah yes, the linux-restricted-modules update always coming alongside linux-image makes total sense now.  

Here's the [Launchpad report](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/156470) for the problem (there might be others but this is the first one I found).  Most of the discourse about this problem is found [here](http://ubuntuforums.org/showthread.php?t=398821) and [here](http://www.nvnews.net/vbulletin/showthread.php?t=96673).  

I recall one of the Ubuntu developers stating that the bug couldn't be fixed due to reliance on NVidia and whatnot.  This may have prevented the Launchpad report from gaining any interest and as such, workarounds became the solution.  Both workarounds are less than desirable - the worst being turn off GPU power management!  My laptop is white-hot as it is!

You are right about Hardy, the NVidia bug doesn't even occur for me there and the updated Envy you speak of sounds quite nice.  But if I can't browse Youtube without Firefox frequently bombing out I can't use the OS.  I have followed the popular "Pulseaudio fixes" thread to no avail.

---

### Post by NTolerance on 2008-06-20
So last night I worked up the patience to boot into Ubuntu.  Previously I was using Firefox 2.  I installed Firefox 3 final from the repos and it seems my crashing issue doesn't occur any longer.  \\:D/

---

