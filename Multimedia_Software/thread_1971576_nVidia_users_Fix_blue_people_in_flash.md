---
title: "*nVidia users* Fix blue people in flash"
date: 2012-05-02
forum: Multimedia Software
---

### Post by jschall1 on 2012-05-02
Adobe Flash sends the red and blue channels to vdpau in the wrong order, causing red things to look blue and blue things to look red. This has been known for a while, but adobe hasn't fixed it.
There's a workaround patch to libvpau posted on the nvnews forums: [http://www.nvnews.net/vbulletin/showthread.php?t=177380](http://www.nvnews.net/vbulletin/showthread.php?t=177380)

STEP 1:
I compiled a package with the patch applied:
[http://www.ecst.csuchico.edu/~jschall/libvdpau1_0.4.1-3ubuntu1_amd64.deb]("http://www.ecst.csuchico.edu/%7Ejschall/libvdpau1_0.4.1-3ubuntu1_amd64.deb")
But don't trust me! Build it yourself:
```
mkdir ~/vdpau
cd ~/vdpau
apt-get source libvdpau1
sudo apt-get install checkinstall build-essential automake debhelper libx11-dev dh-autoreconf x11proto-dri2-dev libxext-dev doxygen-latex graphviz
cd libvdpau-*
wget http://plagman.net/stuff/0001-vdpau_trace-WAR-Flash-quirks.patch
patch -p1 < 0001-vdpau_trace-WAR-Flash-quirks.patch
dpkg-buildpackage -rfakeroot -b
sudo dpkg -i ../libvdpau1_0.4.1-3ubuntu1_amd64.deb

```(note that you'll have to change amd64 to i386 if you're not running 64 bit.)

When you upgrade packages, ubuntu will try to revert the patched package back to the unpatched one. You can stop this by using synaptic (sudo apt-get install synaptic) to force the version.

**In order for the patch to work, you have to run your web browser with the following environment variable set:**
VDPAU_TRACE=1
In order to do this for firefox, you can edit /usr/lib/firefox/firefox.sh and add the line 
```
export VDPAU_TRACE=1 
```near the top. (after the first line "#!/bin/sh" is fine)

---

