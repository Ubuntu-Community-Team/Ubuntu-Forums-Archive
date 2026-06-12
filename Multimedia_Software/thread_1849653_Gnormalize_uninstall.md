---
title: "Gnormalize uninstall?"
date: 2011-09-24
forum: Multimedia Software
---

### Post by Ehiesl on 2011-09-24
hi, I'm very new to this whole thing and just discovered Sound Converter which means I no longer need my Gnormalize installation (which sadly wasn't working anyway for whatever reason).  So I'm trying to uninstall my Gnormalize and can't figure it out.  In the Readme, instructions say:

Execute the bash script commands:
                           tar zxvf gnormalize-0.63.tar.gz
               cd gnormalize-0.63/                           
               ./install
as root.

To install only the gnormalize: 'make install'.
To uninstall the gnormalize:    'make uninstall'.

So when I try this I get:

To: command not found
emily@emily-laptop:~$ cd gnormalize-0.63/
bash: cd: gnormalize-0.63/: No such file or directory
emily@emily-laptop:~$ ./install
bash: ./install: No such file or directory
emily@emily-laptop:~$ as root.

Is there a way to uninstall? I'm just concerned that I won't be able to remove other programs not installed with synaptic if I can't somehow figure this.

Thanks!

---

### Post by sammiev on 2011-09-24
You should be able to go into Synaptic Package Manager and do a search under Gnormalize and select to remove it. :)

---

