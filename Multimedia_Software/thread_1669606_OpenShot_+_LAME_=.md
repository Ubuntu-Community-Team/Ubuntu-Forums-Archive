---
title: "OpenShot + LAME = ???"
date: 2011-01-18
forum: Multimedia Software
---

### Post by helios16v on 2011-01-18
I've been using OpenShot before with no problems at all, I then formatted and Dual booted Windows 7 and Ubuntu 10.10 and now I have a little problem..

I've downloaded and installed OpenShot 1.2 via Software Center and installed LAME Mp3 codec via Terminal 
```
sudo apt-get install lame
```

Everytime I try to export a video I've created in OpenShot I get this message.
"The following formats/codecs are missing from your system:

libmp3lame

You will not be able to use the selected export profile.  You will need to install the missing formats/codecs or choose a different export profile."

I checked the codec in OpenShot and it's missing, I opened Synaptic to search "lame" and sure enough, it's installed version 3.98 so I tried reinstalling lame mp3 via Synaptic and still no audio codec is there in OpenShot when I click Refresh Codec.

I have now tried reinstalling OpenShot with the codec already installed and still nothing, as well as uninstalling both, restarting the computer, and then installing codec then OpenShot and vice versa for installation and STILL nothing is happening. I googled OpenShot LAME Mp3 codec problems and I can't find a single thing..

OpenShot was working flawless before I dual booted and now it wont work at all, every single video format I can use, it's telling me I need the codec for it, which I have but OpenShot tells me I don't..

Any idea's ?! ..I'm stumped
-Ben

---

### Post by helios16v on 2011-01-18
Well I figured it out, I just had to install "ubuntu-restricted-extras" with Synaptic and now it works fine.

Maybe this will help someone else out there with the same problem I had :P
-Ben

---

