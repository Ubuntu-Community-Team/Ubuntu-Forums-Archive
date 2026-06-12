---
title: "Hardy NVidia Drivers"
date: 2009-01-24
forum: Mythbuntu
---

### Post by uncle hammy on 2009-01-24
Are there any plans to have Hardy be able to install the NVidia drivers beyond 169.12 direct from the repositories?

Thanks,
Scott

---

### Post by txcrackers on 2009-01-24
I installed the nvidia-glx-new-envy on my wife's Hardy installation (without using envy, by the way), so it it possible...

---

### Post by uncle hammy on 2009-01-24
Did you have to do anyting other than selecting and installing it from synaptic?

---

### Post by uncle hammy on 2009-01-26
OK, I ended up installing envyng-gtk, and using it to try to install the more current drivers (173 at this point).  However, it cerated an absolute mess that I was never able to get myself out of.

I ended up doing a fresh install, not selecting the NVidia drivers during the installation.  I then did all available updates, and THEN installed envy and tried installing the 173 drivers.  It worked like a charm, so I know envy works.

Here's my catch.  I want to install envy / 1732 drivers on my backend/frontend machine as well (it solves a tearing issue I was having), which already has the 169 drivers installed via the restricted drivers manager.  However, after the fiasco I had testing this out on my frontend machine, I am a little afraid.

Anyone want to tell me the best apporach to install envy -> use it to install drivers, when the NVidia drivers have already been installed via the restricted drivers managers?

Thanks,
Scott

---

### Post by uncle hammy on 2009-01-26
OK, I have tracked down the issue that cause my problems trying to install the drivers with envy on my other system.  I started trying to get the drivers installed on my other machine, by manually removing nvidia-glx-new first.  My machines are AMD64, and they are 64bit installaitons....nvidia-glx-new cannot be removed!  

Trying to remove it leads to an error....

dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx-new (--remove):
 subprocess post-removal script returned error exit status 2


Here's the thing though, the file 100% exists.  In the system I am currently working on, it is a symlink to /usr/lib32/libGL.so.169.12 which also exists.  I am am really at a loss, all the "fixes" I have found with this issue revolve around creating simlinks to /usr/lib/libGL.so.1 however, that obvisouly doens't work, because the simlink I am trying to create exists.

Anyone have any ideas?

Thanks,
Scott

---

### Post by uncle hammy on 2009-01-28
bump

---

