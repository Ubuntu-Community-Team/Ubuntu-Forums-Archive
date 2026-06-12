---
title: "Error during XFI driver install."
date: 2008-06-01
forum: Multimedia Software
---

### Post by smsaks2000 on 2008-06-01
All,

   I'm a Linux noob...installed Ubuntu on my Vista PC. Been trying to get some sound thru Ubuntu...downloaded the Creative XFI drivers. While trying to install drivers I got the following error:

Installation is in progress. Please wait...
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful

    Does anyone have any clue what I need to do to get this installed. I need some sound...must listen to music. :)

    Thanks, in advance, for helping this Linux moron.

    Steve

---

### Post by smsaks2000 on 2008-06-02
Bump for help...please

---

### Post by Divide_Overflow on 2008-06-02
I haven't been able to get my Soundblaster X-fi working with 8.04 either.  I'm trying to pay close attention for news of a fix but haven't found anything yet.  OSS provided very basic X-fi sound for the previous version of Ubuntu.

---

### Post by in0v8 on 2008-06-09
smsaks2000 - this looks like you need to run the 'make' command with sudo.  The install is bailing out at the point where it needs to create files and your user doesn't have sufficient permission.  By the look of what you have pasted here, you're at the ./configure stage, but the 'can't create executables' is probably down to permissions.  Run it as 'sudo ./configure', then your next code should be sudo make and if that completes successfully, run sudo make install

---

