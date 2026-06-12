---
title: "X crash with ssh"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by laurentp on 2007-06-14
Hi,

I've recently installed Ubuntu for my work computer and I have been very satisfied. I have Gentoo on my others computer and first of all I must congratulate you for the job you've all done on this distro. Now let's get to the problem. I use Comsol (simulation software) on a remote server that I connect throught ssh and I forward X to my ubuntu. When the software try to show a lot of mesh ( graphical info) X crash and I don't know why. I can't find anything in logs or dmesg. I've tried using Xfce and I have still the same problem.  I've tried also the radeon driver with no luck. I have a Ati radeon 7500 mobility. I'm now running the same setup with Fedora Core on university's comp with no problem. Any help would be appreciated,

Larry

---

### Post by dannyboy79 on 2007-06-14
have you checked out the /var/log/Xorg.log file? otherwise I am not sure what to tell ya? how does that comsol software work? so you're saying that you're sitting in front of Ubuntu, you ssh into a box and forward the X display of the machine that is running the Comsol?? Is comsol like a vncserver, or like X11vnc?

---

### Post by laurentp on 2007-06-15
Yes I just start ssh with -X and I run my software. So the window appears on my desktop but it is running on the server. This bug is new and if I can recall corectly there was an X update recently. I checked my log file and no signs of the crash ... Maybe I could start X in gdb to have a backtrace or something. Thanks for your time,

Larry

---

### Post by laurentp on 2007-06-18
Nobody have an idea ? Is it possible to downgrade the version of X ? Or maybe to install a more recent version  ? Maybe it's the video driver ?

Larry

---

