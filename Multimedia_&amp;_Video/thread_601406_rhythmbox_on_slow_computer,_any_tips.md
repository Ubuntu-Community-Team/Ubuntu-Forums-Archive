---
title: "rhythmbox on slow computer, any tips?"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by ssam on 2007-11-03
I have a via epia MII with a 600MHz Eden Samuel 2 processor, 512Mb Ram. the processor have a very small cache (64 KB).

i am using it as a network jukebox. i ssh in from my main machine and run rhythmbox using X forwarding. i have installed the bare minimum of packages on top of a minimal install.

rhythmbox, gstreamer codecs, openssh-server, xauth (needed for forwarding), avahi, gtk clearlooks theme (so that rhythmbox looks right when displayed on my desktop).

to start with when playing music (mp3 and ogg) rhythmbox would be at 80-100% CPU all the time. a couple of times an hour it would stutter a bit and then carry on.

I found a few mentions of audioresample being a big bottle neck in gstreamer. my music is in 44kHz (its all from CDs), and alsa needs 48kHz to mix streams. as i only need one process to play sound i switched rhythmbox to use oss, by setting the gconf key /system/gstreamer/0.10/default/audiosink to osssink (note 3 's's). this reduces CPU usage to about 30% but i still get stuttering.

so far i have also tried switching to a realtime kernel. i though as that what the audio people use maybe it would help. this did not seem to make a difference.

does anyone have any other ideas or methods to diagnose this?

thanks

---

### Post by bingoUV on 2007-11-03
Does your slow computer plays sounds, or streams to your main computer?

If it plays itself, you might like some command line player. Running an X server, and gnome libraries might be too much to expect from your slow computer.

---

### Post by ssam on 2007-11-03
> **bingoUV said:**
> Does your slow computer plays sounds, or streams to your main computer?

If it plays itself, you might like some command line player. Running an X server, and gnome libraries might be too much to expect from your slow computer.

it plays the sound it self. the only thing going across the network is the GUI tunneled through the ssh connection.

the small computer is not running X, it is just the single window being forwarded.

```
ssh -XC flute.local rhythmbox
```
(where flute is then name of the jukebox computer)

i have tried with and without C compression.

here is a list of all the processes that are running

```

sam@flute:~$ top -b -n 1
top - 15:59:15 up  3:28,  2 users,  load average: 1.55, 1.47, 1.52
Tasks:  62 total,   1 running,  61 sleeping,   0 stopped,   0 zombie
Cpu(s): 50.5%us,  1.7%sy,  0.0%ni, 46.2%id,  0.2%wa,  1.3%hi,  0.1%si,  0.0%st
Mem:    482864k total,   473204k used,     9660k free,    17532k buffers
Swap:        0k total,        0k used,        0k free,   402832k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                  
 5612 sam       10  -5  139m  35m  16m S 51.8  7.6  26:02.25 rhythmbox                
 5774 sam       15   0  2256  980  760 R  5.8  0.2   0:00.04 top                      
    1 root      15   0  2860 1844  528 S  0.0  0.4   0:04.91 init                     
    2 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                 
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0              
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0              
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0               
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                 
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper                  
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 kblockd/0                
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                   
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify             
  108 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                  
  125 root      16   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                  
  126 root      15   0     0    0    0 S  0.0  0.0   0:00.88 pdflush                  
  127 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                  
  179 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                    
 1877 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                 
 1879 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0              
 1882 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd            
 1883 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                    
 2098 root      10  -5     0    0    0 S  0.0  0.0   0:01.08 ata/0                    
 2099 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                  
 2277 root      12  -5     0    0    0 S  0.0  0.0   0:00.16 kjournald                
 2469 root      11  -4  2348  704  400 S  0.0  0.1   0:01.72 udevd                    
 3286 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 pccardd                  
 3287 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 pccardd                  
 3551 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                
 3780 root      11  -5     0    0    0 S  0.0  0.0   0:01.86 kjournald                
 3781 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                
 3782 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                
 3783 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                
 4085 root      18   0  1604  504  440 S  0.0  0.1   0:00.00 getty                    
 4086 root      18   0  1604  504  440 S  0.0  0.1   0:00.00 getty                    
 4092 root      18   0  1600  500  440 S  0.0  0.1   0:00.00 getty                    
 4095 root      18   0  1604  508  440 S  0.0  0.1   0:00.00 getty                    
 4098 root      18   0  1604  508  440 S  0.0  0.1   0:00.00 getty                    
 4099 root      18   0  1604  504  440 S  0.0  0.1   0:00.00 getty                    
 4135 syslog    23   0  1808  684  548 S  0.0  0.1   0:00.14 syslogd                  
 4154 root      18   0  1740  512  424 S  0.0  0.1   0:00.11 dd                       
 4156 klog      18   0  2396 1380  396 S  0.0  0.3   0:00.46 klogd                    
 4174 messageb  15   0  2664  900  720 S  0.0  0.2   0:00.09 dbus-daemon              
 4194 root      15   0  5216  984  648 S  0.0  0.2   0:00.03 sshd                     
 4232 avahi     15   0  2628 1364 1160 S  0.0  0.3   0:00.06 avahi-daemon             
 4233 avahi     25   0  2628  452  280 S  0.0  0.1   0:00.00 avahi-daemon             
 4247 daemon    15   0  1856  428  312 S  0.0  0.1   0:00.00 atd                      
 4258 root      18   0  2232  784  632 S  0.0  0.2   0:00.04 cron                     
 4286 root      21   0  7972 2380 1936 S  0.0  0.5   0:00.52 sshd                     
 4288 sam       16   0  8452 1968 1080 S  0.0  0.4   0:31.07 sshd                     
 4294 sam       18   0  5204 2492 1840 S  0.0  0.5   0:01.07 gconfd-2                 
 4298 sam       25   0  2816  328  160 S  0.0  0.1   0:00.00 dbus-launch              
 4299 sam       15   0  2800 1024  764 S  0.0  0.2   0:02.12 dbus-daemon              
 4301 sam       15   0  8480 3296 2796 S  0.0  0.7   0:00.08 gnome-vfs-daemo          
 4557 root      17   0  7972 2420 1972 S  0.0  0.5   0:00.49 sshd                     
 4559 sam       15   0  8260 1832 1120 S  0.0  0.4   0:06.32 sshd                     
 4560 sam       15   0  5356 2816 1416 S  0.0  0.6   0:00.89 bash                     
 4588 sam       15   0  2260 1092  848 S  0.0  0.2   1:09.86 top                      
 5558 root      15   0  7972 2424 1972 S  0.0  0.5   0:00.52 sshd                     
 5560 sam       15   0  8120 1516 1044 S  0.0  0.3   0:01.16 sshd                     
 5561 sam       16   0  5356 2844 1440 S  0.0  0.6   0:01.10 bash                     
 5609 root      17   0  7972 2376 1936 S  0.0  0.5   0:01.40 sshd                     
 5611 sam       15   0  8372 2120 1424 S  0.0  0.4   0:07.08 sshd

```

---

### Post by bingoUV on 2007-11-03
Oh, cool. I didn't know it was possible to run X applications without whole X server running. Thanks.

---

### Post by bom28 on 2007-11-05
Are you sure you want to use rhythmbox ?
There is a lot of other players, in particular you might be interested in mpd, a music player with a  server - client model, so only the server runs on your slow computer and you can control it through a variety of gui that runs on other computers.
Also there is my favorite, gmusicbrowser, which can use mpg321/ogg123 or mplayer instead of gstreamer.  So if your slow computer can play mp3 fine with mpg321, it's probable that gmusicbrowser will play them fine too.

---

### Post by Wiebelhaus on 2007-11-05
[VLC]("http://www.videolan.org/vlc/")

---

