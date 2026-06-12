---
title: "How to install Steam in Linux Mint?"
date: 2019-04-01
forum: MINT
---

### Post by drpeppercan on 2019-04-01
I'm using Linux Mint 19.1 (Tessa), based on Ubuntu.
So far the only lead I have is a couple of Nvidia driver installation errors. However, other than the Steam issue, and the Nvidia settings app not showing up, the driver seems to be used by the system successfully. I was able to output a movie file with Blender. I ran OBS too. But ultimately, Steam won't run (although it seems installed)
Here is some relevant data:


    ```
sudo apt install steam
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    The following packages were automatically installed and are no longer required:
      libnvidia-common-390 libnvidia-common-396 libnvidia-common-410
      libnvidia-common-415 libwayland-client0:i386 libwayland-server0:i386
      screen-resolution-extra
    Use 'sudo apt autoremove' to remove them.
    Suggested packages:
      steam-devices:i386
    Recommended packages:
      libxss1:i386 nvidia-driver-libs-i386:i386
    The following NEW packages will be installed:
      steam:i386
    0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
    Need to get 0 B/1,311 kB of archives.
    After this operation, 4,106 kB of additional disk space will be used.
    Preconfiguring packages ...
    Selecting previously unselected package steam:i386.
    (Reading database ... 289208 files and directories currently installed.)
    Preparing to unpack .../steam_1%3a1.0.0.54+repack-5ubuntu1_i386.deb ...
    Unpacking steam:i386 (1:1.0.0.54+repack-5ubuntu1) ...
    Processing triggers for mime-support (3.60ubuntu1) ...
    Processing triggers for desktop-file-utils (0.23+linuxmint4) ...
    Setting up steam:i386 (1:1.0.0.54+repack-5ubuntu1) ...
    Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
    Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
    Processing triggers for hicolor-icon-theme (0.17-2) ...
    drpeppercan@Nitro:~$ steam
    ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
    [2019-03-31 16:02:27] Startup - updater built Nov 23 2016 01:05:42
    libGL error: No matching fbConfigs or visuals found
    libGL error: failed to load driver: swrast
    SteamUpdateUI: An X Error occurred
    X Error of failed request:  BadValue (integer parameter out of range for operation)


```-----------------------------------------------

    ```
inxi -v2
    System:    Host: Nitro Kernel: 4.15.0-46-generic x86_64 bits: 64 Desktop: Cinnamon 4.0.10 
               Distro: Linux Mint 19.1 Tessa 
    Machine:   Type: Desktop Mobo: Acer model: Nitro N50-600 v: V:1.1 serial: <root required> 
               UEFI: American Megatrends v: R01-A3 date: 05/16/2018 
    CPU:       6-Core: Intel Core i7-8700 type: MT MCP speed: 800 MHz min/max: 800/4600 MHz 

```
-----------------------------------------------

    ```
glxinfo | grep renderer
    OpenGL renderer string: GeForce GTX 1060 6GB/PCIe/SSE2
    drpeppercan@Nitro:~/Documents$ glxinfo | grep OpenGL
    OpenGL vendor string: NVIDIA Corporation
    OpenGL renderer string: GeForce GTX 1060 6GB/PCIe/SSE2
    OpenGL core profile version string: 4.6.0 NVIDIA 418.56
    OpenGL core profile shading language version string: 4.60 NVIDIA
    OpenGL core profile context flags: (none)
    OpenGL core profile profile mask: core profile
    OpenGL core profile extensions:
    OpenGL version string: 4.6.0 NVIDIA 418.56
    OpenGL shading language version string: 4.60 NVIDIA
    OpenGL context flags: (none)
    OpenGL profile mask: (none)
    OpenGL extensions:
    OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 418.56
    OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
    OpenGL ES profile extensions:
    drpeppercan@Nitro:~/Documents$ nvidia-smi
    Sun Mar 31 20:30:15 2019       
    +-----------------------------------------------------------------------------+
    | NVIDIA-SMI 418.56       Driver Version: 418.56       CUDA Version: 10.1     |
    |-------------------------------+----------------------+----------------------+
    | GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
    | Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
    |===============================+======================+======================|
    |   0  GeForce GTX 106...  Off  | 00000000:01:00.0  On |                  N/A |
    | 40%   39C    P0    27W / 120W |    395MiB /  6075MiB |      0%      Default |
    +-------------------------------+----------------------+----------------------+
                                                                                   
    +-----------------------------------------------------------------------------+
    | Processes:                                                       GPU Memory |
    |  GPU       PID   Type   Process name                             Usage      |
    |=============================================================================|
    |    0      1298      G   /usr/lib/xorg/Xorg                           158MiB |
    |    0      1797      G   cinnamon                                      73MiB |
    |    0     13428      G   bin/shotcut                                   16MiB |
    |    0     16868      G   /usr/lib/nemo-preview/nemo-preview-start       8MiB |
    |    0     17241      G   ...quest-channel-token=6126019085776133848   136MiB |
    +-----------------------------------------------------------------------------+


```-----------------------------------------------

    ```
drpeppercan@Nitro:~/Documents$ sudo nvidia-settings
    [sudo] password for drpeppercan:         
    sudo: nvidia-settings: command not found

```
-----------------------------------------------

    ```
apt search nvidia-driver
    p   nvidia-driver-390                      - NVIDIA driver metapackage                        
    p   nvidia-driver-390:i386                 - NVIDIA driver metapackage                        
    p   nvidia-driver-396                      - NVIDIA driver metapackage                        
    p   nvidia-driver-396:i386                 - NVIDIA driver metapackage                        
    p   nvidia-driver-410                      - NVIDIA driver metapackage                        
    p   nvidia-driver-410:i386                 - NVIDIA driver metapackage                        
    p   nvidia-driver-415                      - NVIDIA driver metapackage                        
    p   nvidia-driver-415:i386                 - NVIDIA driver metapackage                        
    i   nvidia-driver-418                      - NVIDIA driver metapackage                        
    v   nvidia-driver-binary                   -                                                  
    v   nvidia-driver-binary:i386 

```
-----------------------------------------------

    ```
apt-cache search nvidia-driver
    nvidia-304 - NVIDIA legacy binary driver - version 304.137
    nvidia-340 - NVIDIA binary driver - version 340.107
    nvidia-384-dev - Transitional package for nvidia-driver-390
    nvidia-384 - Transitional package for nvidia-driver-390
    nvidia-387-dev - Transitional package for nvidia-driver-390
    nvidia-387 - Transitional package for nvidia-driver-390
    nvidia-390-dev - Transitional package for nvidia-driver-390
    nvidia-390 - Transitional package for nvidia-driver-390
    nvidia-driver-390 - NVIDIA driver metapackage
    xserver-xorg-video-nvidia-390 - NVIDIA binary Xorg driver
    nvidia-driver-396 - NVIDIA driver metapackage
    xserver-xorg-video-nvidia-396 - NVIDIA binary Xorg driver
    nvidia-headless-390 - NVIDIA headless metapackage
    nvidia-headless-no-dkms-390 - NVIDIA headless metapackage - no DKMS
    nvidia-headless-396 - NVIDIA headless metapackage
    nvidia-headless-no-dkms-396 - NVIDIA headless metapackage - no DKMS
    nvidia-driver-410 - NVIDIA driver metapackage
    nvidia-headless-410 - NVIDIA headless metapackage
    nvidia-headless-no-dkms-410 - NVIDIA headless metapackage - no DKMS
    xserver-xorg-video-nvidia-410 - NVIDIA binary Xorg driver
    nvidia-driver-415 - NVIDIA driver metapackage
    nvidia-headless-415 - NVIDIA headless metapackage
    nvidia-headless-no-dkms-415 - NVIDIA headless metapackage - no DKMS
    xserver-xorg-video-nvidia-415 - NVIDIA binary Xorg driver
    nvidia-driver-418 - NVIDIA driver metapackage
    nvidia-headless-418 - NVIDIA headless metapackage
    nvidia-headless-no-dkms-418 - NVIDIA headless metapackage - no DKMS
    xserver-xorg-video-nvidia-418 - NVIDIA binary Xorg driver
```

---

### Post by QIII on 2019-04-01
Moved to MINT.

---

