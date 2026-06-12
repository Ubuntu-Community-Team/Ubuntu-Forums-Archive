---
title: "Connecting via SSL-VPN using Sonic Wall Net Extender"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by celtica on 2010-03-11
We connect to work via Net Extender SSL-VPN page.  Works fine in Windows, cannot get it working in Ubuntu.

Here is what I get:

> 
--- SonicWALL NetExtender 3.5.632 Installer ---
Checking library dependencies...
  Missing library: libssl.so.4
  Found likely compatible version: /lib/libssl.so.0.9.8
  Attempt auto-repair [Y/n]? y

  Missing library: libcrypto.so.4
  Found likely compatible version: /lib/libcrypto.so.0.9.8
  Attempt auto-repair [Y/n]? y

Checking pppd...
Copying files...
/usr/sbin/netExtender: error while loading shared libraries: libssl.so.4: cannot open shared object file: No such file or directory

------------------------ INSTALLATION SUCCESSFUL -----------------------

Type 'netExtenderGui' to launch NetExtender.
Look in /usr/share/netExtender for a desktop shortcut and icon files.
It says that the installation was successful, but I cannot connect. When I run netExtenderGui command I get:

> Ther ewas a problem loading the netexnder jni library. Please reinstall NetExtender and make sure you have a compatible version of java installed. SonicWall recommends Sun Java 1.4 or higherIf I run just netextender I get:

> 
netExtender: error while loading shared libraries: libssl.so.4: cannot open shared object file: No such file or directory
So it created the link from libssl.so.0.9.8 to libssl.so.4, but I am thinking 0.9.8 is not good - how do I upgrade/install libssl.so.4 - or am I completely off base?

Any ideas?

EDIT:  Looked in Synaptic and it says I have Java 6 JRE,, and default Java Runtime (jre) 1.6.30

---

### Post by PingMetal on 2010-03-23
I, myself too, is in the same situation and looking for an answer. If someone knows what is the solution to the problem, please post. That would be greatly appreciated.

---

### Post by bbdimitriu on 2010-03-25
That's what I also see if I try to install the application on Ubuntu Karmic 64-bit. It works fine under the 32-bit version though.

---

### Post by bbdimitriu on 2010-03-25
I have in fact managed to get it running in 9.10 Karmic 64-bit.
I did the following:
```

sudo ln -s /usr/lib32/libssl.so.0.9.8 /usr/lib32/libssl.so.4
sudo ln -s /usr/lib32/libcrypto.so.0.9.8 /usr/lib32/libcrypto.so.4

```
After that go to the directory where you installed the VPN client and run:
```

sudo ./netExtender

```
This should work, although the linux VPN client seems to disconnect quite often (this is a problem with the 32-bit version as well).

---

