---
title: "Hulu Desktop just stopped working in 11.10."
date: 2012-04-10
forum: Multimedia Software
---

### Post by Stray Wolf on 2012-04-10
When I try to start hulu desktop I get this: ```
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
```
I'm on a Dell Inspiron 1564 with Intel HD graphics. Don't know why I'd need a Nvidia.so. This started after the last flash update. But usually I just have to update the .huludesktop script in the home folder with the new flash location. I don't know what to do for this issue. Any suggestions?

---

### Post by lovinglinux on 2012-04-10
I don't have access to Hulu and it is weird to see an nVidia vdpau error, but I suppose it could be fixed by disabling hardware acceleration.

See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by RJARRRPCGP on 2012-04-10
Looks like a missing library.

---

### Post by Stray Wolf on 2012-04-10
> **lovinglinux said:**
> I don't have access to Hulu and it is weird to see an nVidia vdpau error, but I suppose it could be fixed by disabling hardware acceleration.

See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

Unfortunately that context menu hasn't worked for me in quite a while. I can right-click to show it, but I can't interact with it. I tried going to the global settings but there is no option to enable/disable there.

---

### Post by Stray Wolf on 2012-04-10
> **RJARRRPCGP said:**
> Looks like a missing library.

I'm not sure if that library was ever there. I'm not on a system that has never used Nvidia. Plus, Hulu works fine through FF and XBMC. But using those two apps requires more time and more steps. Hulu Desktop was a lot quicker and easier and the interface was really intuitive to me.

---

### Post by lovinglinux on 2012-04-10
> **Stray Wolf said:**
> Unfortunately that context menu hasn't worked for me in quite a while. I can right-click to show it, but I can't interact with it. I tried going to the global settings but there is no option to enable/disable there.

That issue is also explained in the tutorial. Open a video, enter fullscreen mode then access the Settings dialog.

---

### Post by Stray Wolf on 2012-04-11
> **lovinglinux said:**
> That issue is also explained in the tutorial. Open a video, enter fullscreen mode then access the Settings dialog.
I apologize for overlooking that explanation. Just as before Hulu Desktop opens a window with the correctly themed borders and all, but in the window is still a black screen. The only difference after turning off flash's hardware acceleration is that the whole system bogs down and the terminal just has a flashing cursor instead of the output in my original post. Weird that Hulu works fine from XBMC and FF.

---

### Post by lovinglinux on 2012-04-11
After some research, I have found that this error occurs when the default output is set to nVidia. Perhaps you could try to change the output from "Autodetect" to XV in gstreamer-properties.

---

### Post by Stray Wolf on 2012-04-11
> **lovinglinux said:**
> After some research, I have found that this error occurs when the default output is set to nVidia. Perhaps you could try to change the output from "Autodetect" to XV in gstreamer-properties.
Done. Still no worky. I also tried: ```
sudo apt-get install vdpau-va-driver libvdpau1
``` which didn't work. Someone directed me to do: ```
sudo touch /usr/lib/libvdpau_nvidia.so
``` and ```
sudo ln -s /usr/lib/libvdpau_nvidia.so /usr/lib32
``` which I did before your gstreamer suggestion. The only thing I on top of your suggestion was to select the device option too which was "Intel(R) Textured Video". Anyway, Hulu now outputs: ```
Failed to open VDPAU backend /usr/lib/libvdpau_nvidia.so: file too short
```

I haven't undone or know how to undo these tweaks people have suggested so I hope don't mess anything up. But if so reinstalling is easy enough.

---

### Post by lovinglinux on 2012-04-11
> **Stray Wolf said:**
> Done. Still no worky. I also tried: ```
sudo apt-get install vdpau-va-driver libvdpau1
``` which didn't work. Someone directed me to do: ```
sudo touch /usr/lib/libvdpau_nvidia.so
``` and ```
sudo ln -s /usr/lib/libvdpau_nvidia.so /usr/lib32
``` which I did before your gstreamer suggestion. The only thing I on top of your suggestion was to select the device option too which was "Intel(R) Textured Video". Anyway, Hulu now outputs: ```
Failed to open VDPAU backend /usr/lib/libvdpau_nvidia.so: file too short
```

I haven't undone or know how to undo these tweaks people have suggested so I hope don't mess anything up. But if so reinstalling is easy enough.

I wouldn't be worried about the tweaks so far.

---

### Post by Stray Wolf on 2012-04-12
So I did find and remove all Nvidia stuffs by running ```
sudo apt-get -s remove nvidia-*
``` This just output what needed to be removed then I got rid of them by running ```
sudo apt-get remove nvidia-common vdpau-va-driver
``` I also got rid of the dummy file /usr/lib/libvdpau_nvidia.so and the link /usr/lib/libvdpau /usr/lib32. I noticed that WITH libvdpau1 installed huludesktop outputs:  ```
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared  object file: No such file
``` WITHOUT libvdpau1 the output is just a  blinking cursor. While the cursor just blinks Hulu Desktop has a window with proper border themes. But inside the window is black. And the mouse gets choppy.

---

### Post by mastermindg on 2012-04-19
The solution that worked for me was to download a previous version of Flash from Adobe's archived versions, in particular this one:

[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.62_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.62_archive.zip)

from this page:

[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

Simply extract and drill down until you find your distro (for me 11_1r102_62_64bit/flashplayer11_1r102_62_linux.x86_64) and copy the libflashplayer.so to /usr/lib/mozilla/plugins and then point Hulu there in ~.huludesktop.

Good luck and Good watching!

---

### Post by lovinglinux on 2012-04-19
> **mastermindg said:**
> The solution that worked for me was to download a previous version of Flash from Adobe's archived versions, in particular this one:

[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.62_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.62_archive.zip)

from this page:

[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

Simply extract and drill down until you find your distro (for me 11_1r102_62_64bit/flashplayer11_1r102_62_linux.x86_64) and copy the libflashplayer.so to /usr/lib/mozilla/plugins and then point Hulu there in ~.huludesktop.

Good luck and Good watching!


You don't need to download the huge package. See direct links at [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by Stray Wolf on 2012-04-26
Could I install an older version of flash in a way that only Hulu desktop would use and still have everything else use the newest version?

---

### Post by lovinglinux on 2012-04-26
> **Stray Wolf said:**
> Could I install an older version of flash in a way that only Hulu desktop would use and still have everything else use the newest version?

Possibly, but since I don't live in the US, I can't try to figure it out.

---

### Post by Stray Wolf on 2012-04-28
> **lovinglinux said:**
> Possibly, but since I don't live in the US, I can't try to figure it out.
Either way - you're awesome! Thanks for all the help!

---

### Post by lovinglinux on 2012-04-28
> **Stray Wolf said:**
> Either way - you're awesome! Thanks for all the help!

You are welcome and thanks for your kind words.

---

