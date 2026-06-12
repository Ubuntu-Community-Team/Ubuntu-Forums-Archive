---
title: "remove (broken) nVidia and revert to nouveau"
date: 2010-10-17
forum: Multimedia Software
---

### Post by mamthor on 2010-10-17
Yesterday I got out of a frightening situation, after installing the non-open nVidia drivers the day after installing 10.04.1 64 bit on my new work computer.  After installing the nVidia drivers I could no longer boot into any usable video environment.  The computer went straight from a blinking cursor after grub to a blank screen and stayed there.  I had the same result when booting into recovery mode.  Booting into the previous kernel, which also shows up as an option in the grub list, gave me only a BusyBox terminal, which is unfortunately useless for someone with my low level of skill in linux.

I got access to my system using the live version from the USB stick from which I installed Ubuntu in the first place and tried a few things (based on ideas from the forums) to try to get it back up and running.  Finally the solution that worked was just deleting my xorg.conf file entirely.  Now, I imagine that I will need to use that file at some point in the future, and am not sure where to go from here to get back where I was before installing the proprietary drivers.

After reading a lot on these forums, I have come to the conclusion that I was previously running with nouveau drivers, since I understand that they are the default for lucid.  I would like to go back to those if possible, but I am now very paranoid about doing any kind of guesswork on my own, hence this post.  Is it as simple as going into Synaptic Package manager and uninstalling anything starting with "nvidia-" or putting something like 

```
sudo apt-get --purge remove nvidia-*
```into a terminal?

Once I do that, how can I be sure that the nouveau drivers will take over again?  I know they don't provide any 3D acceleration, but I don't need it for my purposes.  And they do at least allow some of the desktop effects, which are nice to have.  Also, I do assume that it's better to have an xorg.conf file to be able to customize settings there, rather than running in whatever default mode I am in currently.

Thanks a lot for the help!

---

