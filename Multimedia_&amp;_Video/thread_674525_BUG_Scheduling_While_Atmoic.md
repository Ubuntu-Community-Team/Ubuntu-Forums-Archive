---
title: "BUG: Scheduling While Atmoic"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by jenic on 2008-01-21
I am somewhat reluctant to start a new thread on this but I think that resurrecting those '05 posts  would be messier than starting a fresh one. They were not the exact problem in any case.

Exact Error:
```
Jan 21 14:48:03 Akatosh kernel: [  141.181732] BUG: scheduling while atomic: swapper/0x00000100/0
Jan 21 14:48:03 Akatosh kernel: [  141.181736] 
Jan 21 14:48:03 Akatosh kernel: [  141.181737] Call Trace:
Jan 21 14:48:03 Akatosh kernel: [  141.181752]  [thread_return+542/1737] thread_return+0x21e/0x6c9
Jan 21 14:48:03 Akatosh kernel: [  141.181757]  [kernel_thread+129/222] kernel_thread+0x81/0xde
Jan 21 14:48:03 Akatosh kernel: [  141.181764]  [default_idle+0/64] default_idle+0x0/0x40
Jan 21 14:48:03 Akatosh kernel: [  141.181769]  [cpu_idle+141/192] cpu_idle+0x8d/0xc0
Jan 21 14:48:03 Akatosh kernel: [  141.181774]  [start_kernel+645/784] start_kernel+0x285/0x310
Jan 21 14:48:03 Akatosh kernel: [  141.181778]  [x86_64_start_kernel+286/352] _sinittext+0x11e/0x160
```uname -a :
```
Linux Akatosh 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64 GNU/Linux
```I am convinced it has something to do with my nVidia card (nvidia GeForce 6600 GT) and/or drivers (I have tried both nvidia-glx-new and am currently running on 169.07) as the issue occurs when I am:[LIST]
[*]Using Accelerated Graphics
[*]Updating/Installing nvidia drivers
[*](Oddly Enough) Viewing */var/log/kern.log*[/LIST]Also note that Compiz runs fine, as does its graphical effects such as The Cube. Even Games such as chess work. **However**, Tetris causes the error, as does all graphically intense games like Eve Online.

The error will only occur when viewing *kern.log*. Not ones no longer being written to such as* kern.log.2.gz*.

If it helps, here is the relevant xorg.conf:
```
Section "Device"
        Identifier      "nVidia Corporation NV43 [GeForce 6600 GT]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "CPD-L181"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV43 [GeForce 6600 GT]"
        Monitor         "CPD-L181"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"     "1024x768"      "800x600"      "720x400"        "640x480"
        EndSubSection
        Option          "AddARGBGLXVisuals"     "True"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "Enable"
EndSection
```When this error occurs I can notice it immediately as GkrellM shows 99% cpu usage by system while System Monitor says average 24% usage. It is then that things begin to slow down (I am assuming it is I/O Wait from the flood of the above error writing to kern.log) until it is unusably slow. If I attempt a shutdown or reboot it will stall after shutting down most processes and hang on a blank screen showing my background wallpaper. At that point I invoke the life saving magic SysReq which usually works. More often than not it is fine after that reboot until the next occurrence, sometimes however I need to hard reboot it as a last resort.

I thank everyone in advance for any help you can provide me.

---

### Post by jenic on 2008-02-03
**New Developments**

Since the last post I have encountered new instances of the bug in other locations:[LIST]
[*]Startup when loading PS/2 mouse
[*]Startup when loading GDM
[*]Immediately after logging in
[*]Restarting Compiz engine[/LIST]My original thought was that it must have something to do with the interaction between nvidia drivers and the kernel but now I think it is some issue inherent in the kernel itself. I have found many other instances of the exact same error plaguing people on other forums and mailing lists but have yet to find one explaining what is happening or even more important, how to fix it. 

Btw: this is my cleverly disguised bump >.>

---

