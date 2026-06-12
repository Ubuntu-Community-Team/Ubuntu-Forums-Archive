---
title: "No sound from S/PDIF from desktop"
date: 2016-12-30
forum: Multimedia Software
---

### Post by Adam_Jacobs on 2016-12-30
I have an Ubuntu 14.04 system with MythTV, and S/PDIF connected to a 5.1 surround sound speaker system.

From my MythTV frontend, those speakers work just fine. However, from the Ubuntu desktop, they don't work (though I can still get sound via HDMI). If I go to my sound settings and choose the S/PDIF output and go to "test sound", it just gives me a choice of "left" and "right", so presumably it thinks I have stereo speakers rather than 5.1. I've just discovered that the sound from the MythTV frontend only works if the box marked "upscale stereo to 5.1" is ticked, so I'm guessing there is a similar issue here and that I somehow need to tell the system that the speaker configuration is 5.1 rather than stereo.

In looking for a solution, I came across this page, which I thought looked like it might help:

[https://help.ubuntu.com/community/DigitalAC-3Pulseaudio](https://help.ubuntu.com/community/DigitalAC-3Pulseaudio)

I tried running the automated installer script, but almost all steps failed. So I'm not quite sure what my next move is. Is it worth figuring out how to get the installer script to work by troubleshooting each failed step one by one, or is this not actually the right way to get my surround sound speakers to work anyway?

The first step that fails is this one:

```
sudo apt-get build-dep libasound2-plugins
```

The output I get when I try to run that is 

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'alsa-plugins' as source package instead of 'libasound2-plugins'
The following packages have unmet dependencies.
 libjack-dev : Depends: libjack0 (= 1:0.121.3+20120418git75e3e20b-2.1ubuntu1) but it is not going to be installed
E: Build-dependencies for libasound2-plugins could not be satisfied.



```

All suggestions gratefully received!

---

### Post by Adam_Jacobs on 2017-04-08
I've been playing with this some more, and making a small amount of progress. I can now get sound from my S/PDIF connection (turned out it was muted in alsamixer), but it's still only in stereo.

I'm assuming that this has a good chance of being solved if I can install the a52 plugin as per the link I gave above, but I can't.

I have got a little further now (I don't think I've done anything different, but maybe something has been fixed in a recent update), but still not very far.

The line 

```
sudo apt-get build-dep libasound2-plugins
```

doesn't give an error now, though it does give the following output:

> Picking 'alsa-plugins' as source package instead of 'libasound2-plugins'


I don't know if that's a problem or not. But the next line in the set of instructions, namely
```

sudo apt-get install libavcodec-dev libavformat-dev
```

 still fails. It seems to have unmet dependencies that it can't fix. This is the output I get:
> 
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 libavcodec-dev : Depends: libavutil-dev (= 6:9.20-0ubuntu0.14.04.1) but it is not going to be installed
 libavformat-dev : Depends: libavformat54 (= 6:9.20-0ubuntu0.14.04.1) but it is not going to be installed
                   Depends: libavutil-dev (= 6:9.20-0ubuntu0.14.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



I'm a little stuck here. Does anyone know how I can fix these problems? Or is is a bit of a red herring anyway and there's another reason why the surround sound isn't working?

---

