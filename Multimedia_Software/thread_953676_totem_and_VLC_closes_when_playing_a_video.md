---
title: "totem and VLC closes when playing a video"
date: 2008-10-20
forum: Multimedia Software
---

### Post by madsc89 on 2008-10-20
If I try to open a video using Totem or VLC, it just closes. I might be able to glimpse one frame...

In totem using the YouTube plugin, I get this from terminal:

```
 totem
** (totem:8768): DEBUG: Init of Python module
** (totem:8768): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:8768): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:8768): DEBUG: Creating Python plugin instance
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 54 error_code 2 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

It worked fine yesterday.

Earlier today, these automatic upgrades were installed:

```
Upgraded the following packages:
gstreamer0.10-tools (0.10.18-4ubuntu1) to 0.10.18-4ubuntu2
libexif12 (0.6.16-2.1) to 0.6.16-2.1ubuntu0.1
libgstreamer0.10-0 (0.10.18-4ubuntu1) to 0.10.18-4ubuntu2
tzdata (2008g-0ubuntu0.8.04) to 2008h-0ubuntu0.8.04
tzdata-java (2008g-0ubuntu0.8.04) to 2008h-0ubuntu0.8.04
```

How do I fix this? 

Thank you

Mads

---

### Post by aeiah on 2008-10-20
does this happen with all videos or just youtube ones?

it could be related to libgstreamer. you could try removing it from synaptic and installing an older version although make sure you find out how to install an older version first before removing the new one

---

### Post by madsc89 on 2008-10-20
> **aeiah said:**
> does this happen with all videos or just youtube ones?

it could be related to libgstreamer. you could try removing it from synaptic and installing an older version although make sure you find out how to install an older version first before removing the new one

Sorry, I wasn't quite clear on that. It happens with 3gp files as well.

I forced libgstreamer0.10.18-4ubuntu2 to be downgraded to  libgstreamer0.10.18-4ubuntu1.
And this resolved the problem. (It might be restarting the computer, I only tried logging in again earlier.)

_To do this:_
Open Synaptic, highlight libgstreamer0.10.18-4ubuntu2, press ctrl + E.

Should this be reported as a bug or something like that?

---

### Post by hesjnet on 2008-11-07
Im running 8.10 and it is not possible to do CTRL E on that file anymore. Any idea what to do?

---

### Post by scoobymad555 on 2008-11-07
I've had similar problems on my system too, most noteably it's usually video playback within firefox though.

I usually have amorak docked at the same time and killing that off can make a difference sometimes but not always.

I didn't have the problem before i cranked compiz up to full effects though and i suspect if i disabled it or reduced the things it was doing that it might solve the problem on my system .... i like my pretty desktop though so i live with the problem lol! have found that re-opening the page or video (sometimes several attempts) usually yields a successful result though.

If you're running compiz on yours then perhaps 'tweaking' it's settings may help? :)

---

### Post by madsc89 on 2008-11-09
It doesn't work ofr me.
Compiz is at no desktop effects.
It seems that everytime I upgrade or reinstall anything related, it works after one restart, but then is back to not working.

---

### Post by madsc89 on 2008-11-26
It works again:s

---

### Post by vpa2013 on 2011-07-24
Hello,
I have the same problem, and I think it may be a shared memory issue due to a Xorg memory leak

My symptoms: after running ubuntu 11.04 for a while, when I open a video with totem it crashes immediately with this in the standard output: 
```
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 96 error_code 2 request_code 133 minor_code 19)
```When I try to play with VLC, the sounds plays but the screen remains black.
If I log off and then log in again, everything works!

I noticed that sometimes, closing everything that consumes RAM (like firefox...) was enough to be able to play a video again.

Now I had a look at my memory usage before and after logging off:
Before logging off, even though I closed everything I sill had a big memory consumption.
This is my top before loggof, ordered by RES desc:
```
top.a - 19:54:01 up  9:20,  1 user,  load average: 0.37, 0.36, 0.23
Tasks: 183 total,   2 running, 180 sleeping,   0 stopped,   1 zombie
Cpu(s): 15.1%us,  5.7%sy,  0.2%ni, 75.6%id,  2.7%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:   8190800k total,  7029080k used,  1161720k free,    75788k buffers
Swap:  3664892k total,    18264k used,  3646628k free,  3766776k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1191 root      20   0 1478m 982m 342m S   41 12.3  68:26.09 Xorg               
25133 pascal    20   0  584m 111m  39m S   25  1.4   0:30.47 compiz             
 1646 pascal    20   0  720m  57m  19m S    0  0.7   0:57.21 nautilus           
 2097 pascal    20   0  295m  41m 7048 S    0  0.5   1:06.19 ubuntuone-syncd    
```And this is just after logging in again:
```
top.a - 20:28:26 up  9:54,  2 users,  load average: 0.18, 0.18, 0.14
Tasks: 179 total,   1 running, 177 sleeping,   0 stopped,   1 zombie
Cpu(s): 15.2%us,  5.8%sy,  0.2%ni, 75.5%id,  2.6%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:   8190800k total,  5110836k used,  3079964k free,    93376k buffers
Swap:  3664892k total,    17828k used,  3647064k free,  4111588k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                   
27790 pascal    20   0  609m 100m  38m S    0  1.3   0:02.60 compiz                                                                                                    
28082 pascal    20   0  295m  46m  11m S    0  0.6   0:01.11 ubuntuone-syncd                                                                                           
27794 pascal    20   0  637m  43m  22m S    0  0.5   0:01.07 nautilus                                                                                                  
27633 root      20   0  273m  40m  28m S    2  0.5   0:05.21 Xorg
```As you can see, the consumption of the Xorg process is indecent : almost 1GB RES and 1.4GB virtual (compared to 100MB - 600MB at startup)
I should say that I have 8GB of memory, so it's plenty enough to play videos still.

This is why I believe there is a shared memory segment somewhere with a limited amount, and once Xorg is too big, it's using all of the shared segments. 
I'll try to find out about the shared segments next time it happens
Someone knows an equivalent of the ipc command on ubuntu? 

Incidentely I have my /tmp FS mounted in RAM but I don't think that would be the issue.
/etc/ftab:
```
tmpfs /tmp tmpfs rw,size=512m 0 0
```BTW there is a workaround that has worked for me at least once: play around with the output options in VLC, and use "X11 (XCB)" as video output. However I find the quality is quite bad and i'd rather logg of and log in.


Thanks

---

### Post by vpa2013 on 2011-07-24
Maybe I should add details about my configuration: 
Like I said I use ubuntu 11.04 natty. 
My mainboard is Gigabyte GA-890GPA-UD3H (AMD 890GX) with HD 4290 embedded
However I recently installed a "HD 5670" (had to reinstall all the fglrx part). I think the issue wasn't occuring with the HD 4290 embedded.
I have the ATI catalyst proprietary driver: 

fglrxinfo
```
display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5670
OpenGL version string: 4.1.10665 Compatibility Profile Context

```lspci -v
```

...
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5670] (prog-if 00 [VGA controller])
        Subsystem: PC Partner Limited Device e166
        Flags: bus master, fast devsel, latency 0, IRQ 49
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fdec0000 (64-bit, non-prefetchable) [size=128K]
        I/O ports at de00 [size=256]
        [virtual] Expansion ROM at fde00000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Legacy Endpoint, MSI 00
        Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Capabilities: [150] Advanced Error Reporting
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx, radeon
...

```/etc/X11/xorg.conf
```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

```oups... that's ugly; I used to have much more in the xorg.conf... maybe that the issue. I will try some tuning on this file and let you know... everyone who has the issue could you post your xorg.conf? 

Thanks

---

### Post by vpa2013 on 2011-07-24
Put in place a more catholic /etc/X11/xorg.conf, using
aticonfig --initial
and adding the result of 
cvt -v 1920 1080 60Hz
(cvt -v <width> <heigth> <frequency>)
in the Section "Monitor" part

Still have the same garble when lauching VLC:

```
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0xe63120] main libvlc: Lancement de vlc avec l'interface par défaut. Utilisez « cvlc » pour démarrer VLC sans interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1310991561)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:2390): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Blocked: call to setlocale(6, "")

```Videos work for now, will post if the issue happens again.

---

### Post by vpa2013 on 2011-10-12
Hi guys.
I was able to find the process that was leaking memory thanks to xrestop: it's gtk-window-decorator
From there I found an open bug: 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/740258](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/740258)

Workaround by [Lukáš Chmela (lukaschmela)]("https://launchpad.net/%7Elukaschmela")             
> a workaround is to replace gtk-window-decorator with unity-window-decorator.
 You can do it simply by pressing ALT+F2 and typing "gconf-editor", then navigating into "/apps/compiz-1/plugins/decor/screen0/options/" and changing the "command" key to "unity-window-decorator --replace".
 Another way, however, non-persistent, is pressing ALT+F2 and typing directly "unity-window-decorator --replace &".
This way, the unity-window decorator would be replaced by the gtk one  once Compiz is reloaded meaning that you would need to run this command  on every login.


Enjoy

---

