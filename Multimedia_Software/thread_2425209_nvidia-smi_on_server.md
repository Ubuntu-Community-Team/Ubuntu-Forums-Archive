---
title: "nvidia-smi on server"
date: 2019-08-22
forum: Multimedia Software
---

### Post by ray-nok on 2019-08-22
Hello :)
hope this wont be duplicate post. But I tried every post i found on internet and it didnt help me. So here i bother YOU ;)

Summary:
Ubuntu 16.04 Server without GUI
GeForce GTS 250

```

ray@ubuntuServer:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce GTS 250] (rev a2)
ray@ubuntuServer:~$ nvidia-smi
modprobe: ERROR: could not insert 'nvidia': No such device
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

```

Installed:
cuda-repo-ubuntu1604_10.0.130-1_amd64.deb
NVIDIA-Linux-x86_64-340.107.run

then for some reason:
```

oot@ubuntuServer:~# nvidia-settings

ERROR: The control display is undefined; please run `nvidia-settings --help`
       for usage information.

```

originaly just want to run mining on my graphic, but now im irritated that i cant :(
please please help :) Does anyone know wheres the problem?
thank you all ;)

---

