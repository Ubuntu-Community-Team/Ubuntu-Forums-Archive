---
title: "Optimus using Bumblebee, VDPAU errors"
date: 2014-01-25
forum: Multimedia Software
---

### Post by Amorget on 2014-01-25
Hi, 
I purchased a new laptop that has a Optimus setup in it.  The Nvidia card is the 765M and the Intel is the 4600.  Unfortunately it seems like all the modern laptops with Nvidia cards have Optimus except the hard core gaming laptops.

I followed these instructions:  [http://www.muktware.com/2013/12/install-nvidia-331-bumblebee-optimus-cards/18271](http://www.muktware.com/2013/12/install-nvidia-331-bumblebee-optimus-cards/18271)  to setup Bumblebee with the Nvidia 331 drivers as I needed them for the 765M.  The 304s don't support it, as I have read and learned after some troubleshooting.  The only problem that I ran into during installing is that nvidia-settings-331 doesn't seem to exist in the ppa.  However, I wouldn't think that would cause any issues.

Now that I have it so optirun works I want to get VDPAU working.  I launch Firefox using the command "optirun firefox" and then attempt to view a youtube video.  This error shows up in the console:

```
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
```

I googled around and found this:

[https://ask.fedoraproject.org/en/question/29138/failed-to-open-vdpau-backend-libvdpau_nvidiaso-cannot-open-shared-object-file-no-such-file-or-directory/](https://ask.fedoraproject.org/en/question/29138/failed-to-open-vdpau-backend-libvdpau_nvidiaso-cannot-open-shared-object-file-no-such-file-or-directory/)

However, some of the folders the reference (like /usr/lib64) doesn't exist on my machine, just lib and lib32.  However, I can't find the file libvdpau_nvidia.so anywhere on my machine.

I also found this and tried creating the symbolic link, however it didn't help, same error:

[http://askubuntu.com/questions/164785/how-to-configure-bumblebee-in-ubuntu-12-04](http://askubuntu.com/questions/164785/how-to-configure-bumblebee-in-ubuntu-12-04)

Anyone have any ideas on how to fix this?

Thanks,
Douglas

---

### Post by Yellow Pasque on 2014-01-26
Install catfish search, which will easily let you search for the file in question.

I'm using Debian, but for me, the libvdpau_nvidia.so.331.38 file is under /usr/lib/x86-64-linux-gnu/vdpau, and there is a libvdpau_nvidia.so.1 symlink in the same directory pointing to it.

---

### Post by Amorget on 2014-01-26
Using catfish it says no files found, it looks like that file doesn't exist on my system but I have no idea why.

Thanks for the hint on catfish, though.  I've missed a file search program like that.

Thanks,
Douglas

---

### Post by Yellow Pasque on 2014-01-26
Check the repo's (in Synaptic or Software Center or whatever you use for packages with 'vdpau' in the name. On Debina, there's a separate package for nvidia-vdpau driver, but I'm not sure how xorg-edgers does their packages.

---

### Post by Amorget on 2014-01-26
The only thing that returns for vdpau is the 173 nvidia drivers and a codec pack

Thanks,
Douglas

---

### Post by Yellow Pasque on 2014-01-26
Check this dir:

```
cd /usr/lib/nvidia-331/vdpau/
ls
```

If you see the 331.38 file, make a symlink and check vdpauinfo:
```
sudo ln -s /usr/lib/nvidia-331/vdpau/libvdpau_nvidia.so.331.38 /usr/lib/nvidia-331/vdpau/libvdpau_nvidia.so
sudo ldconfig
sudo apt-get install vdpauinfo
vdpauinfo
```

---

### Post by Amorget on 2014-01-26
The files exist at that location!  However, when I tried to create the symbolic link, it says the file already exists.

```
amorget@amorgetlp:/usr/lib/x86_64-linux-gnu$ cd /usr/lib/nvidia-331/vdpau/
amorget@amorgetlp:/usr/lib/nvidia-331/vdpau$ ls
[COLOR="#40E0D0"]libvdpau_nvidia.so  libvdpau_nvidia.so.1[/COLOR]  libvdpau_nvidia.so.331.38

amorget@amorgetlp:/usr/lib/nvidia-331/vdpau$ sudo ln -s /usr/lib/nvidia-331/vdpau/libvdpau_nvidia.so.331.38 /usr/lib/nvidia-331/vdpau/libvdpau_nvidia.so
ln: failed to create symbolic link &#8216;/usr/lib/nvidia-331/vdpau/libvdpau_nvidia.so&#8217;: File exists

```

---

### Post by Yellow Pasque on 2014-01-26
Check vdpauinfo command. It should tell us whether it's a system-wide issue or just Flash/youtube.

---

### Post by Amorget on 2014-01-26
Same output as inside of FF:

```
amorget@amorgetlp:/usr/lib/nvidia-331/vdpau$ vdpauinfo
display: :0   screen: 0
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Error creating VDPAU device: 1

```

Same error if I run optirun vdpauinfo

Thanks,
Douglas

---

### Post by Amorget on 2014-01-27
Anyone have any thoughts on this?  Thanks, Douglas

---

### Post by monkeybrain20122 on 2014-01-27
I don't think bumblebee supports vdpau, so better do some googling before wasting your time.

---

### Post by Amorget on 2014-01-28
Things like this lead me to saying yes:

[http://askubuntu.com/questions/164785/how-to-configure-bumblebee-in-ubuntu-12-04](http://askubuntu.com/questions/164785/how-to-configure-bumblebee-in-ubuntu-12-04)

---

### Post by monkeybrain20122 on 2014-01-28
You may be right. I checked the bumblebee mailing list but that was 2012 [https://github.com/Bumblebee-Project/Bumblebee/issues/36](https://github.com/Bumblebee-Project/Bumblebee/issues/36)

---

### Post by pok1yoyo on 2014-03-20
Hi.
I took some time to configure my setup, and here is what it worked for me. 
Symlink nvidia's libvdpau (may be neccesary to replace nvidia-current with your driver)
```
ln -s /usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so /usr/lib/libvdpau_nvidia.so
```
That may already work, but for me, I got (when running mplayer):
```

Xlib:  extension "NV-GLX" missing on display ":0".
Xlib:  extension "NV-GLX" missing on display ":0".
[vdpau] Error when calling vdp_device_create_x11: 1

```
So I tried to run mplayer with --display=:8 or maybe try 
```
DISPLAY=:8 & optirun mplayer
```
It works for me, but I see no video. After some reading, it seems that :8 display is not shown, so I had to use WinDump.
So I built windump, then run mplayer on display :8, replaced the window manager and ran windump. You may want to replace gnome-shell with compiz or metacity, if you don't use it. I used three tabs, one for each command.
```
optirun mplayer &
gnome-shell --replace --display=:8
./windump :8 :0

```

Now I see video, it works with vdpau, but the size is wrong, and I can't go fullscreen. It is worth said, that there are people who managed to make it work.
More info:
[http://askubuntu.com/questions/100786/watching-videos-with-hardware-acceleration-enabled-gives-me-sound-but-no-image/100812#100812](http://askubuntu.com/questions/100786/watching-videos-with-hardware-acceleration-enabled-gives-me-sound-but-no-image/100812#100812)

---

