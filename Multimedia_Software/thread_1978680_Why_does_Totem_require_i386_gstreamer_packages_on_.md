---
title: "Why does Totem require i386 gstreamer packages on amd64 system?"
date: 2012-05-12
forum: Multimedia Software
---

### Post by peterdm on 2012-05-12
Whenever I click on an MKV file, Totem opens and complains that the required packages are not installed. It wants to install "gstreamer0.10-plugins-base (i386)". I wonder why though, I have "gstreamer0.10-plugins-base" installed. The amd64 version that is. There should be no need to install the i386 version, right?

It is my understanding that i386 packages on an amd64 system should only be there for exceptional cases, like flashplugin, acroread, or vmware or some other i386-only binary distro. Totem hardly qualifies as an exceptional case, the gstreamer base plugins are also no exceptional case. I could understand this maybe for the "ugly" or "bad" gstreamer plugins, but not for "base"...

Can someone explain what is going on here?

---

### Post by peterdm on 2012-05-12
And when I do allow installation of the i386 package, Totem still fails with "Required plugin could not be found

Python (v2.7) requires to install plugins to support the following multimedia feature: GStreamer element uridecodebin".

---

### Post by mc4man on 2012-05-12
It would appear that if totem(gstreamer) can't decode, or thinks it can't decode a file, then on 64 bit it falls back to the nonsense about installing the i386 packages (which ultimately fail anyway

Maybe? your 'problem' files fall under this current bug - [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014)

If so, (or anyway) you can try this for 64 bit,
```
sudo mv /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak

```
Otherwise maybe install mediainfo-gui & open your .mkv in it & identify the encoding ect.

Edit - the other thing you can try is to delete ~/.gstreamer-0.10/registry.x86_64.bin

---

### Post by peterdm on 2012-05-12
Thanks for the tip mc4man. I tried uninstalling plugins-bad, but it didn't help. As you point out, the problem is not at all amd64/i386 related, it's that gstreamer is broken.

---

