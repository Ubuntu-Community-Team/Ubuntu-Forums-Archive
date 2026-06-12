---
title: "Installing Amarok and VLC on XUBUNTU"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by martinkun167 on 2008-03-31
Hi, i'm a beginner at this...I've installed Xubuntu on my laptop, and am pleased with this operating system since it does not make my laptop so loud (i guess because it doesn't use as much resources).

Anyway, I realised that Xubuntu seems to have less software in comparison to Ubuntu, which is why I'm having trouble finding programs that could play mp3s (for which i used Amarok) and videos (which used to be VlC player for me). I've tried typing the following in the terminal:

$ sudo apt-get install amarok

But it gives me this message after:

[B]Package amarok is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package amarok has no installation candidate[/B]

In the case of VLC, it tells me this:

[B]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.8.6.release.c-0ubuntu5) but it is not going to be installed
       Depends: libcaca0 (>= 0.99.beta11-1) but it is not installable
       Depends: libcdio6 but it is not installable
       Depends: libcucul0 (>= 0.99.beta11-1) but it is not installable
       Depends: libiso9660-4 but it is not going to be installed
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
       Depends: libvcdinfo0 (> 0.7.23) but it is not going to be installed
E: Broken packages
[/B]
It's causing me a little headache...Could anyone please give me clear suggestions on how to fix this, or if there are any other effective programs similar to there that i can use.

Thank you.

---

### Post by Prefix100 on 2008-03-31
This isn't really about your posted problem,

but if your laptop is noisy you should open it up and get a can of compressed air and clear out the dust. It will preform much quieter then.

---

### Post by edm1 on 2008-03-31
you must enable the appropriate repositories in Synaptic>Settings>Repositories then press reload, then try again.

EDIT: the appropriate repos being the universe, restricted and multiverse.

---

### Post by martinkun167 on 2008-03-31
edm1, i tried what you told me, but I get the exact same messages.

---

### Post by Aztek on 2008-04-01
Have you tried using Synaptic?

---

