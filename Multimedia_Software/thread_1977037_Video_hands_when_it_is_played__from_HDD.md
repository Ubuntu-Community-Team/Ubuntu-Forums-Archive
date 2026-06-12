---
title: "Video hands when it is played  from HDD"
date: 2012-05-09
forum: Multimedia Software
---

### Post by Inquisitive Alex on 2012-05-09
Hello. I have the following problem: when I try to open a video (ogg, mp4, mkv) from hard disk it freezes for a moment every 10-15 seconds. When video is opened from flash it works well. Sometimes video is played well from hard disk, too. But I can't understand how to get it.
Ubuntu version is 12.04. Please help.

---

### Post by Shadius on 2012-05-09
> **Inquisitive Alex said:**
> Hello. I have the following problem: when I try to open a video (ogg, mp4, mkv) from hard disk it freezes for a moment every 10-15 seconds. When video is opened from flash it works well. Sometimes video is played well from hard disk, too. But I can't understand how to get it.
Ubuntu version is 12.04. Please help.

What is your graphics card?

---

### Post by papibe on 2012-05-09
Hi Inquisitive Alex.

It sounds like your video is HD, and your machine is struggling to reproduce it. 

Depending in your hardware, you just need to install and configure the necessary libraries so you take advantage of video hardware acceleration.

As Shadius requested it, it is important to know your graphic card, because it will end up doing all the decoding.

Could you post the result of these commands so we can learn your graphics?
```
lspci -nn | grep -i VGA

sudo lshw -C display
```
Regards.

---

### Post by Inquisitive Alex on 2012-05-10
Thank you for your reply. I have quite good card. I tried different video formats, both HD and quite simple ones. Sometimes videos play well, sometimes - not.

lspci -nn | grep -i VGA
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT216 [GeForce GT 330M] [10de:0a29] (rev a2)

```

 lshw -C display
```
  *-display               
       description: VGA compatible controller
       product: GT216 [GeForce GT 330M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:e2000000-e2ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:d000(size=128) memory:e3000000-e307ffff

```

---

### Post by papibe on 2012-05-10
OK, thanks.

First, let's check you have the proprietary Nvidia driver installed.

If you run this:
```
apt-cache policy nvidia-current
```
The output should be something like this:
```
  **Installed: 195.36.24-0ubuntu1~10.04.2**
  Candidate: 195.36.24-0ubuntu1~10.04.2
  Version table:
 *** 195.36.24-0ubuntu1~10.04.2 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid-updates/restricted Packages
        500 http://mirror.anl.gov/pub/ubuntu/ lucid-security/restricted Packages
        100 /var/lib/dpkg/status
     195.36.15-0ubuntu2 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/restricted Packages

```
Then make sure you are using it. Run this:
```
lsmod | grep nvidia
```
It should print something similar to this:
```
nvidia               9962720  56 
agpgart                31788  2 nvidia,intel_agp

```
And this:
```
lsmod | grep nouveau
```
should return nothing.

Now to the acceleration library (VDPAU). To check if is installed:
```
 apt-cache policy libvdpau1
```
If libvdpau1 is installed, you should be able to run acceleration on SMplayer setting it up [this]("http://ubuntuforums.org/showpost.php?p=11721778&postcount=6") way.

VLC won't use VDPAU directly so if you like to use VLC, you need to install another library:
```
sudo apt-get install vdpau-va-driver libva1 vainfo
```

and set VLC -> Tools -> Preferences -> Inputs & Codecs -> Use GPU acceleration.

You can check if the VAAPI libraries are installed correctly by running:
```
vainfo
```
That should show a list of codecs and no error.

I hope that help, and tell us how it goes.
Regards.

---

### Post by Inquisitive Alex on 2012-05-11
Yes, I use proprietary Nvidia driver (295.40-0ubuntu1). There is no nouveau module loaded. I have vdpau-va-driver and GPU acceleration is on. 
Here is my vainfo output:
```
libva: VA-API version 0.32.0
libva: User requested driver 'vdpau'
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/vdpau_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems VDPAU backend for VA-API - 0.7.3
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileMPEG4Simple            :	VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```

Actually I don't think that this is video card problem. I think this is hard disk problem. And I noticed (but I'm not sure) that problem exists only in first ~ 20 minutes after system start. After that, video plays fine. Maybe there is some system process which uses hard disk very intensively?

---

### Post by papibe on 2012-05-11
> **Inquisitive Alex said:**
> Actually I don't think that this is video card problem. I think this is hard disk problem. And I noticed (but I'm not sure) that problem exists only in first ~ 20 minutes after system start. After that, video plays fine. Maybe there is some system process which uses hard disk very intensively?

Check your 'Startup Applications' to see if there's something unusual launching there.

Also, use either 'System Monitor', or 'top' (terminal) in those 20 minutes to look for something that would take away your performance.

Any backup or sync that you can think of?

Just some thoughts.
Regards.

---

### Post by Inquisitive Alex on 2012-05-12
Here is top command output. Nothing suspicious... 
```
 1071 root      20   0  157m  41m  18m S    2  1.1   0:11.32 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none                                                             
 1798 alex      20   0 1378m 130m  47m S    1  3.4   0:11.33 /usr/bin/gnome-shell                                                                                                                                    
 1950 alex      20   0  638m  87m  33m S    1  2.2   0:14.41 /usr/lib/firefox/firefox                                                                                                                                
 2133 alex      20   0 17332 1336  968 R    1  0.0   0:00.08 top                                                                                                                                                     
   19 root      20   0     0    0    0 S    0  0.0   0:00.01 [ksoftirqd/3]                                                                                                                                           
   58 root      20   0     0    0    0 S    0  0.0   0:00.15 [kworker/u:3]                                                                                                                                           
  705 root      20   0     0    0    0 S    0  0.0   0:00.15 [kworker/0:2]                                                                                                                                           
 1037 root      20   0 15972  688  512 S    0  0.0   0:00.06 /usr/sbin/irqbalance                                                                                                                                    
 2071 alex      20   0  576m  18m  11m S    0  0.5   0:01.11 gnome-terminal                                                                                                                                          
    1 root      20   0 24456 2408 1348 S    0  0.1   0:01.27 /sbin/init                                                                                                                                              
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 [kthreadd]                                                                                                                                              
    3 root      20   0     0    0    0 S    0  0.0   0:00.09 [ksoftirqd/0]                                                                                                                                           
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 [migration/0]                                                                                                                                           
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 [watchdog/0]                                                                                                                                            
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 [migration/1]                                                                                                                                           
    9 root      20   0     0    0    0 S    0  0.0   0:00.12 [kworker/1:0]                                                                                                                                           
   10 root      20   0     0    0    0 S    0  0.0   0:00.00 [ksoftirqd/1]                                                                                                                                           
   11 root      20   0     0    0    0 S    0  0.0   0:00.25 [kworker/0:1]                                                                                                                                           
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 [watchdog/1]                                                                                                                                            
   13 root      RT   0     0    0    0 S    0  0.0   0:00.00 [migration/2]                                                                                                                                           
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 [ksoftirqd/2]                                                                                                                                           
   16 root      RT   0     0    0    0 S    0  0.0   0:00.00 [watchdog/2]                                                                                                                                            
   17 root      RT   0     0    0    0 S    0  0.0   0:00.00 [migration/3]                                                                                                                                           
   18 root      20   0     0    0    0 S    0  0.0   0:00.00 [kworker/3:0]                                                                                                                                           
   20 root      RT   0     0    0    0 S    0  0.0   0:00.00 [watchdog/3]                                                                                                                                            
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 [cpuset]                                                                                                                                                
   22 root       0 -20     0    0    0 S    0  0.0   0:00.00 [khelper]                                                                                                                                               
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 [kdevtmpfs]                                                                                                                                             
   24 root       0 -20     0    0    0 S    0  0.0   0:00.00 [netns]                                                                                                                                                 
   26 root      20   0     0    0    0 S    0  0.0   0:00.00 [sync_supers]                                                                                                                                           
   27 root      20   0     0    0    0 S    0  0.0   0:00.00 [bdi-default]                                                                                                                                           
   28 root       0 -20     0    0    0 S    0  0.0   0:00.00 [kintegrityd]                                                                                                                                           
   29 root       0 -20     0    0    0 S    0  0.0   0:00.00 [kblockd]                                                                                                                                               
   30 root       0 -20     0    0    0 S    0  0.0   0:00.00 [ata_sff]                                                                                                                                               
   31 root      20   0     0    0    0 S    0  0.0   0:00.00 [khubd]                                                                                                                                                 
   32 root       0 -20     0    0    0 S    0  0.0   0:00.00 [md]                                                                                                                                                    
   34 root      20   0     0    0    0 S    0  0.0   0:00.00 [khungtaskd]                                                                                                                                            
   35 root      20   0     0    0    0 S    0  0.0   0:00.00 [kswapd0]                                                                                                                                               
   36 root      25   5     0    0    0 S    0  0.0   0:00.00 [ksmd]                                                                                                                                                  
   37 root      39  19     0    0    0 S    0  0.0   0:00.00 [khugepaged]                                                                                                                                            
   38 root      20   0     0    0    0 S    0  0.0   0:00.00 [fsnotify_mark]                                                                                                                                         
   39 root      20   0     0    0    0 S    0  0.0   0:00.00 [ecryptfs-kthrea]                                                                                                                                       
   40 root       0 -20     0    0    0 S    0  0.0   0:00.00 [crypto]                                                                                                                                                
   48 root       0 -20     0    0    0 S    0  0.0   0:00.00 [kthrotld]                                                                                                                                              
   50 root      20   0     0    0    0 S    0  0.0   0:00.17 [kworker/2:1]                                                                                                                                           
   51 root      20   0     0    0    0 S    0  0.0   0:00.00 [scsi_eh_0]                                                                                                                                             
   52 root      20   0     0    0    0 S    0  0.0   0:00.00 [scsi_eh_1]                                                                                                                                             
   53 root      20   0     0    0    0 S    0  0.0   0:00.00 [scsi_eh_2]	
```

---

