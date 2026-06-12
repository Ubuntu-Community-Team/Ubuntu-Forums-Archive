---
title: "Need help installing the NVidia Driver"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by fedora-refugee on 2007-06-01
What I have is a Ubuntu 7.04 and a Geforce4 MX 440 APG 8X. 

Here is what I've done so far:  I first installed Ubuntu, then installed 'Easy Ubuntu' then checked the official driver and the legacy driver for download.  Once this was completed and I restarted, Gnome would no longer run.  So I went ahead and reinstalled Ubuntu.  This time I downloaded the driver manually ( NVIDIA-Linux-x86_64-1.0-9755-pkg2.run ).  When I tried to run this, I got an error message stating this driver didn't support my out-of-date graphics card.  So I go ahead and download the legacy driver (NVIDIA-Linux-x86_64-1.0-9631-pkg2.run) and run this.  This seems to install ok, but then I can't load Gnome.  I'm only able to recover gnome by restoring the backup xorg.conf file.  This time I install 'Envy' which I've heard so much about from googling.   Envy starts ok by starting to download NVIDIA-Linux-x86_64-1.0-9631-pkg2.run from nvidia.com.  The problem is that at around 2-3% it says 'connection timed out' and everything dies.  I retry this multiple times and the download never seems to get above 4%.  Now I do have a 26k modem which is pretty slow, so I decide to download NVIDIA-Linux-x86_64-1.0-9631-pkg2.run manually and put it into /usr/share/envy/nvidia-graphics-drivers.  Now when I run envy it does notice this package but gives me a MD5 checksum error.  So I try to go back to downloading and running the driver from Envy but I still get the timeouts.  I search for some setting that sets the timeout (I suspect Envy or the application it is using is not used to slow dialups, so is a bit overzealous when it comes to declaring timeouts).  But I can not find any setting that increases the timeout size.

Anybody have any ideas on how I get this driver installed on my machine?  Any help would be appreciated!

---

### Post by Nythain on 2007-06-01
sudo apt-get install nvidia-glx-legacy     ???

---

### Post by fedora-refugee on 2007-06-02
I did:

sudo apt-get install nvidia-glx-legacy

...and everything seemed to install ok.  I then click on the desktop effects and it has me install another download before anything can work.  I then get a prompt telling me I need to restart my computer for my changes to take  effect.

I do this and X won't load and gives me the following error message:

Error:  API Mismatch: The NVIDIA kernel module has the version 1.0-7184, but this x module has the version 1.0-9631. Please make sure that the kernel module and all NVIDIA driver components have the same version.

Any help would be appreciated!

---

### Post by tseliot on 2007-06-02
> **fedora-refugee said:**
> I did:

sudo apt-get install nvidia-glx-legacy

...and everything seemed to install ok.  I then click on the desktop effects and it has me install another download before anything can work.  I then get a prompt telling me I need to restart my computer for my changes to take  effect.

I do this and X won't load and gives me the following error message:

Error:  API Mismatch: The NVIDIA kernel module has the version 1.0-7184, but this x module has the version 1.0-9631. Please make sure that the kernel module and all NVIDIA driver components have the same version.

Any help would be appreciated!

Type:
```
sudo apt-get --purge remove nvidia-glx-legacy
```

```
sudo apt-get install nvidia-glx
```

---

### Post by fedora-refugee on 2007-06-03
I tried that and I still get the same error on when trying to load Gnome.

---

### Post by n3ur0m4n on 2007-06-04
I have the same problem with my GeForce 2 Mx with the new kernel (2.6.20-16-generic)... if I install the nvidia-glx-legacy X gives me the "API Mismatch" message... (with the nvidia-glx, the X server has the version 1.0-9755 and Nvidia kernel 1.0-9631).

Some problem if I use Envy (with driver version 1.0-9631 and 1.0-7185).

I tried the nvidia-glx-new (version 1.0.9755) and X start (I see the Nvidia logo) but... it's ok for my old GeForce 2???

---

