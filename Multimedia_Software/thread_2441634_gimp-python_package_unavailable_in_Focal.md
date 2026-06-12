---
title: "gimp-python package unavailable in Focal"
date: 2020-04-25
forum: Multimedia Software
---

### Post by ehdee on 2020-04-25
Hi,

I'm seeing errors as per the following upon launching gimp 2.10.18 (with gimp-plugin-registry installed) in 20.04, :

```

Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/plugin-uncrop.py", line 46, in <module>
    from gimpfu import *
ImportError: No module named gimpfu
gimp: LibGimpBase-WARNING: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/plugin-resynth-sharpen.py", line 32, in <module>
    from gimpfu import *
ImportError: No module named gimpfu
gimp: LibGimpBase-WARNING: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/plugin-resynth-fill-pattern.py", line 33, in <module>
    from gimpfu import *

```

In previous releases this could be addressed by installing the [gimp-python]("https://packages.ubuntu.com/search?keywords=gimp-python") package, however this is not available for Focal. Are there plans to make this package available in Focal Fossa?

Eddie

---

### Post by mc4man on 2020-04-25
Most likely no chance you'll see those packages..
You could try the snap version, it's constructed with python2.7 support so maybe it'll work for you.
Additional plugins can be put in ~/snap/gimp/252/.config/GIMP/2.10/plug-ins. If they are compiled then maybe use 18.04 versions for glibc compatibility 
Also if  any shebangs use python2 they would need to be edited to just python

Or acquire the eoan packages gimp-python_2.10.8-2_amd64.deb & python-gtk2_2.24.0-6_amd64.deb, they'll install ok as a pair with apt.
Also install the focal python-is-python2 package
Then see how the .deb gimp is.

---

### Post by ehdee on 2020-04-25
Thanks for the response. I made a backup of the plugins deployed by gimp-plugin-registry and stuck them over a snap install.

This has got me a step further! I can launch the app without the Python errors now and can even get as far as getting the dialogs up for Python-based plugins, but they fail with other errors that I'll need to investigate at a later date. I've not tried using the old debs yet. It might be a quicker solution for me to revert to Bionic, and only update again once a GIMP with Python 3 support is out (with the hopes that the Python plugins should be easy enough to port).

I guess I should also figure out how to file a suggestion for Python-based plugins to be removed from the 'gimp-plugin-registry', as the fact that they are still being shipped is going to trip up others in the future too.

---

