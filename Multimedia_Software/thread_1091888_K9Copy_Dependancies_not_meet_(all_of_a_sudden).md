---
title: "K9Copy Dependancies not meet (all of a sudden)"
date: 2009-03-09
forum: Multimedia Software
---

### Post by timZZ on 2009-03-09
Hi,

I was a happy k9copy user but after shortly installing it less then a month ago it has disappeared out of my applications > sound & video.

I tried reinstalling and I get this from the terminal

#Blanked#@#Blanked#:~$ sudo apt-get install k9copy
[sudo] password for #Blanked#:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
k9copy: Depends: kdebase-runtime (>= 4:4.0.66) but it is not going to be installed
Depends: kdelibs5 (>= 4:4.0.98a) but it is not going to be installed
Depends: libphonon4 (> 4:4.2~) but it is not going to be installed
Depends: libqt4-dbus (>= 4.4.0) but it is not installable
Depends: libqt4-opengl (>= 4.4.0) but it is not installable
Depends: libqt4-qt3support (>= 4.4.0) but it is not going to be installed
Depends: libqt4-xml (>= 4.4.0) but it is not installable
Depends: libqtcore4 (>= 4.4.0) but it is not installable
Depends: libqtgui4 (>= 4.4.0) but it is not installable
Depends: phonon (> 4:4.2~) but it is not installable
Depends: mencoder but it is not going to be installed
E: Broken packages

---

### Post by hansdown on 2009-03-09
Hi timZZ.

You can fix broken packages in synaptic.

Click system> administation> synaptic package manager.

In the left Bottom corner click custom filters. Then click broken in the top left corner. Any broken packages should appear, and click fix broken packages.

---

### Post by timZZ on 2009-03-09
My broken list is empty.

---

### Post by timZZ on 2009-03-09
I think my problem lies in the fact i have Hardy instead of Intrepid (Which is what the k9copy in my synaptic package manager is for) I tried forcing versions I got errors as well

---

### Post by timZZ on 2009-03-09
So everyone knows I uninstalled the package and trying to get it back. (with 100% failure)

---

### Post by timZZ on 2009-03-09
This is the synaptic GUI output

k9copy:
 Depends: kdebase-runtime but it is not going to be installed
 Depends: kdelibs5 but it is not going to be installed
 Depends: libphonon4 but it is not going to be installed
 Depends: libqt4-dbus (>=4.4.0) but it is not installable
 Depends: libqt4-opengl (>=4.4.0) but it is not installable
 Depends: libqt4-qt3support but it is not going to be installed
 Depends: libqt4-xml (>=4.4.0) but it is not installable
 Depends: libqtcore4 (>=4.4.0) but it is not installable
 Depends: libqtgui4 (>=4.4.0) but it is not installable
 Depends: phonon (>4:4.2~) but it is not installable
 Depends: mencoder but it is not going to be installed

---

### Post by mc4man on 2009-03-09
Did you add a repo to your sources to enable installing the intrepid(?) version of k9? If so disable it.

The dep's your showing aren't for the hardy version so some source is enabled that shouldn't be.

---

### Post by timZZ on 2009-03-09
That is weird
I found intrepid repos.  I have converted them to hardy.

Will keep updated

---

### Post by timZZ on 2009-03-09
OK thank you. That was the problem right there.

---

### Post by mc4man on 2009-03-09
Just for info - all k9 versions 2.x.x are kde4 versions which would be difficult at best to install on hardy. (maybe if you added some packages and built, installing a 2.x.x on hardy from a .deb would require adding intrepid repo's and would probably break some other things

The latest 1.x.x (for hardy) is 1.2.4 so your 1.2.3 isn't that dated (and if desired you could build 1.2.4 on hardy

---

