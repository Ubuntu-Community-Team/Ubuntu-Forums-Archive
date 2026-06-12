---
title: "ATI catalyst drivers broke"
date: 2010-02-04
forum: Multimedia Software
---

### Post by AnthIste on 2010-02-04
Sigh I feel a bit retarded tbh, but I have somehow managed to break my system's graphics. Most of my specs are in my sig.

To start from the beginning, I realised that I have no audio, so I tried a couple of fixes that I found online. Upon rebooting, all my graphics were very choppy (moving windows, scrolling etc). The sound is working though. I dont understand how fixing sound can mess with the graphics but hey it isnt working and thats what matters.

I have an installer for the ATI drivers downloaded from ati.amd.com. when I had a clean install of Ubuntu 9.10 and installed these drivers everything worked 100% without any problems. Running the installer now doesnt seem to work. The log in /usr/share/ati/fglrx-install.log reports:
```

Errors during DKMS module removal
Errors during DKMS module removal

Creating symlink /var/lib/dkms/fglrx/8.681/source ->
                 /usr/src/fglrx-8.681

DKMS: add Completed.
You can use the --kernelsourcedir option to tell DKMS where it's located.
[Error] Kernel Module : Failed to build fglrx-8.681 with DKMS
[Error] Kernel Module : Removing fglrx-8.681 from DKMS

```
Im not exactly pro at fixing things so this doesnt help me very much.
```

uname -r

```
reports "2.6.31-17-generic"

Im not really sure how to go about fixing this. I've tried purging fglrx completely but there always seem to be come traces left. The default drivers work fine but ofc theres no acceleration.

Please help

---

### Post by AnthIste on 2010-02-04
Ok I've fixed it.
```

sudo apt-get install envyng-core envyng-qt
sudo envyng -k

```

Choose the recommended option. Reboot and there you go.

---

