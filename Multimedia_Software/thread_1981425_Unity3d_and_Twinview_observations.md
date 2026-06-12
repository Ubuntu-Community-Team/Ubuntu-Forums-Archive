---
title: "Unity3d and Twinview observations"
date: 2012-05-16
forum: Multimedia Software
---

### Post by fbicknel on 2012-05-16
First the formalities:
> $ lsb_release -rd
Description:    Ubuntu 12.04 LTS
Release:    12.04
$ Purchased a second video card thinking I could use Twinview and have twice the screen real estate.

Wrong.  To use Twinview, I find, both monitors have to be connected to the same video card, i.e. one that supports two outputs.  My setup has the Twinview option in nvidia-settings grayed out.

Ok.  So there's another option called Xinerama that does seem to work.  I'll try that.

First off, you don't get a single screen, you get two screens with the ability to move things between the screens easily using the mouse.  But that's minor.

Turns out that Unity 3d does not work with this setup.  If I switch to this and restart X (logout/login), I wind up in Unity 2d.  If I run* /usr/lib/nux/unity_support_test -p*, it fails.

Switch back to a single screen and Unity 3d works again.

Beware.

Thought I might help someone trying to do the same thing.

---

