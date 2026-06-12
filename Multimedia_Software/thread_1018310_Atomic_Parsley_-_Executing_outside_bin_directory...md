---
title: "Atomic Parsley - Executing outside bin directory.."
date: 2008-12-22
forum: Multimedia Software
---

### Post by ibexcentral on 2008-12-22
Hi,

I am new to linux and learning......is it possible to run an executable outside the /bin directory?

The reason I ask is that my ISP/Host will not allow any apps to be installed in /bin

I want to run atomic parsley, a command line application from within my web folders on the server is this possible or do executables only work in a bin directory.

Thanks

Paul

---

### Post by andrewc6l on 2008-12-22
Executables can live anywhere. However, the files have to be marked executable. If you build something by compiling it, it should automatically be marked executable. However, if you've just uploaded a binary, odds are good that you'll need to:

chmod u+x my-binary

to get it to execute. After that, you will have to run it with the full pathname /home/my-user/my-binary (or just ./my-binary if your current directory is the directory that contains the file). You could also modify your PATH environment variable to include your home directory (usually not recommended).

---

