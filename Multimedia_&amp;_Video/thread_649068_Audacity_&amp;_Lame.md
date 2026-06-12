---
title: "Audacity &amp; Lame"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by OBI_Ron on 2007-12-24
Hello Everyone,

I am having trouble trying to use Audacity to convert files to mp3.  I have searched, and following previous posts, I installed Lame using synaptic.  However, as root, the following search finds nothing:

find / -name 'libmp3*'

According to previous posts, Audacity is looking for libmp3lame.so.0 or libmp3lame.so.  In either case, find / -name 'libmp3*' should find the file.

I have also verified Lame installation using apt:

# sudo apt-get install lame
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lame is already the newest version.
The following packages were automatically installed and are no longer required:
  libxcb-xv0 libxcb1 libxcb-shape0 libxvmc1 libpulse0 libxcb-shm0 libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I also re-booted just in case.

Can anyone offer any suggestions?

Thanks in advance!!!

---

### Post by jdiz on 2007-12-24
I have the exact same problem :confused:

---

### Post by OBI_Ron on 2007-12-25
jdiz,

I got a little help from a guy on the Blender forums - you need to install the liblame0 package.  I used synaptic, and was able to install and use it with Audacity with no problems - no searching for the library.

Hope this works for you!

---

