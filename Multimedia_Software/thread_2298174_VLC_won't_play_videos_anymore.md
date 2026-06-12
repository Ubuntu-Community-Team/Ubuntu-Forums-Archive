---
title: "VLC won't play videos anymore"
date: 2015-10-09
forum: Multimedia Software
---

### Post by corneliuss2 on 2015-10-09
Suddenly, VLC will not play any video. Audio files and streams work fine however.

No matter what video source I use (file, stream, capture device) VLC crashes before starting playback. This is the error message:

```
Inconsistency detected by ld.so: ../sysdeps/i386/dl-machine.h: 607: elf_machine_rel_relative: Assertion `((reloc->r_info) & 0xff) == 8' failed!
```

I failed to find relevant information about this error except this forum: [http://www.linuxforums.org/forum/gentoo-linux/170115-solved-inconsistency-detected-ld-so.html](http://www.linuxforums.org/forum/gentoo-linux/170115-solved-inconsistency-detected-ld-so.html)

So far, I have reinstalled VLC, I have deleted configuration files and I tried changing video output. None changes anything.

Running ```
ldd /usr/bin/vlc
``` gives the following output:

```
linux-gate.so.1 =>  (0xb7781000)    libvlc.so.5 => /usr/lib/libvlc.so.5 (0xb7736000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xb7719000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb7713000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb7558000)
    libvlccore.so.8 => /usr/lib/libvlccore.so.8 (0xb743a000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xb73ed000)
    /lib/ld-linux.so.2 (0xb7782000)
    librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xb73e4000)
    libidn.so.11 => /usr/lib/i386-linux-gnu/libidn.so.11 (0xb73b0000)
    libdbus-1.so.3 => /lib/i386-linux-gnu/libdbus-1.so.3 (0xb7359000)
```

Using Ubuntu 15.04 x86, NVIDIA GeForce 8600 GT graphics card with repo `nvidia-340` driver.

---

### Post by mc4man on 2015-10-09
reboot a few times, see if better. If not run a full memtest.
(a ldd on vlc isn't useful as it's plugin based, the plugins have most of the linked shared objects.

---

### Post by corneliuss2 on 2015-10-10
Thanks for your reply. I rebooted three times and run Memtest. No errors found by memtest. VLC still crashes.

---

### Post by corneliuss2 on 2015-10-10
I have fixed it. I reinstalled the video driver with

```
sudo apt-get update && sudo apt-get install --reinstall nvidia-340 nvidia-settings && sudo reboot now
```

Now it works.

---

### Post by fortworthtechs on 2015-10-10
The API key is to be generated on Google Developer in order to use Minitube on Antergos. You have to follow the simple steps:


1)      Go to [http://console.developers.google.com]("http://console.developers.google.com/") and you need to sign in with your Google Account.
2)      Click on the blue button marked with Create Project which is at the top left hand corner of the screen. 
3)      The project is to be given a name doesn’t matter what it is just click on create button.
4)      You have to wait until the project is created and you will directly taken to the dashboard. The list of option is seen on the left hand side. Click on the APIs and Auth and then click on the credentials.
5)      Click on Create New Key
6)      Click on Browser Key.
7)      Just left the text field empty, and click on the create.
8)      API string key is generated and then it is copied to the clipboard.
9)      The mini tube is to be installed and if you already have not and then open it once to generate the next file you will need. 
10)   file /etc/profile.d/minitube.sh as root is to opened in your text editor. Just type sudo leafpad /etc/profile.d/minitube.sh is to be typed as this is easy to do in this terminal. 
11)   In there you will see APP_GOOGLE_API_KEY=””. Paste that generated API key in between the speech marks, save and close.
12)   Now Reboot your machine.

---

### Post by corneliuss2 on 2015-10-10
> **fortworthtechs said:**
> The API key is to be generated on Google Developer in order to use Minitube on Antergos. You have to follow the simple steps:


1)      Go to [http://console.developers.google.com]("http://console.developers.google.com/") and you need to sign in with your Google Account.
2)      Click on the blue button marked with Create Project which is at the top left hand corner of the screen. 
3)      The project is to be given a name doesn’t matter what it is just click on create button.
4)      You have to wait until the project is created and you will directly taken to the dashboard. The list of option is seen on the left hand side. Click on the APIs and Auth and then click on the credentials.
5)      Click on Create New Key
6)      Click on Browser Key.
7)      Just left the text field empty, and click on the create.
8)      API string key is generated and then it is copied to the clipboard.
9)      The mini tube is to be installed and if you already have not and then open it once to generate the next file you will need. 
10)   file /etc/profile.d/minitube.sh as root is to opened in your text editor. Just type sudo leafpad /etc/profile.d/minitube.sh is to be typed as this is easy to do in this terminal. 
11)   In there you will see APP_GOOGLE_API_KEY=””. Paste that generated API key in between the speech marks, save and close.
12)   Now Reboot your machine.
Are you sure you didn't post in the wrong thread?

---

