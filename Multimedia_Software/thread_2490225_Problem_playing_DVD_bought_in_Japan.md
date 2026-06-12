---
title: "Problem playing DVD bought in Japan"
date: 2023-08-27
forum: Multimedia Software
---

### Post by tarastasesa on 2023-08-27
Hello everybody, 

have a problem playing a DVD (movie) bought in Japan with my Acer Aspire V5-571 bought in Italy using both my DVD VERBATIM player (bought in Italy and always working fine) and my DVD LOGITECH LDR-PML8U3CVBK player (just bough in Japan). Videos application starts but the screen remains black and, after a few seconds, the disk stops.
Had just installed Ubuntu 22.04 (ISO on USB pendrive) and updated/upgraded the system. Before the installation, had NVIDIA drivers (GFORCE GT 620M). Wish to install them again. I tried following a few tutorials but Videos application still doesn't work. Downloaded Ubuntu 22.04 ISO from: _[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)_
My purpose is  to install everything needed to play DVDs bought in Japan (where I'm living, now) with at least one of my DVD player. 
A friend of mine, played my Japanese DVD with her APPLE notebook (bought in Italy) using my LOGITECH DVD player and everything went fine, so I'm sure the DVD and the LOGITECH LDR-PML8U3CVBK DVD player are OK.

Many thanks!

---

### Post by Rubi1200 on 2023-08-27
Hi and welcome to the forums :-)

Ubuntu does not ship with certain proprietary codecs out of the box due to legal restrictions unless you checked the box to add third-party applications during installation.

If not, then do the following:

```
sudo apt update
sudo apt install ubuntu-restricted-extras libdvd-pkg
sudo dpkg-reconfigure libdvd-pkg

```

Open a terminal with Ctrl+Alt+T and run each command separately. You will be prompted for your password with the first command. You may also be prompted to agree to certain terms and conditions during the process.

Hopefully, once this all completes you should be able to play your DVDs.

Let us know if there were any errors.

---

### Post by ajgreeny on 2023-08-27
Don't forget that most commercial DVDs have a region limitation built in meaning they may not be playable on all hardware which is itself region limited.

There are apparently workarounds that can remove or change the region setup of hardware but I've never needed or tried that so can't help any more with how to do it.

---

### Post by tarastasesa on 2023-08-27
Thanks Rubi1200!
Unfortunately, I've run commands you suggested but... nothing, Videos application start for a few seconds and, then, the disk stops. Is seems that the DVD is not readable... :(

---

### Post by tarastasesa on 2023-08-27
Interesting Ajgreeny, maybe, I should give it a try: anyone who knows how to change region setup?
Thanks again!

---

### Post by Rubi1200 on 2023-08-27
There is a way to change the region for a DVD drive but be aware there is a limit to how many times you can do it, I think it is 5.

Another thing to try is install vlc, an excellent media player that I highly recommend:

In a terminal:
```
sudo apt install vlc
```

Once installed, open the application and go to Media >> Open Disc >> under DVD check the box No disc menus and then try to run the DVD.

Does this help?

---

### Post by tarastasesa on 2023-08-27
Just installed VLC. 
I got this message, when I play the Japanese DVD:

 [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/sr0".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR]p, li { white-space: pre-wrap; }

---

### Post by #&amp;thj^% on 2023-08-27
If you go this route, please NOTE:
```
regionset /dev/sr0
Current drive parameters for /dev/sr0:
  RPC Type: Phase II (Hardware)
  RPC Status: no region code set (bitmask=0xFF)
  [B][U][COLOR="#FF0000"]Vendor may reset the RPC 4 times
  User is allowed change the region setting 5 times[/COLOR][/U][/B]
Would you like to change the region setting for this drive? [y/n]: 


```
I'm not of your region so this one is up to you.
And you will need to install "regionset" 
Good Luck

---

### Post by Holger_Gehrke on 2023-08-27
I don't think it is the region code since Europe and Japan are in the same region (Region Code 2).

Holger

---

### Post by #&amp;thj^% on 2023-08-27
Possibly not the region code, but this is concerning:
> A friend of mine, played my Japanese DVD with her APPLE notebook (bought in Italy) using my LOGITECH DVD player and everything went fine, so I'm sure the DVD and the LOGITECH LDR-PML8U3CVBK DVD player are OK.
So I guess it would be good to know if the DVD in question is encoded (Scrambled CSS)
More on that:
```
apt policy libdvdcss2
libdvdcss2:
  Installed: 1.4.3-1~local
  Candidate: 1.4.3-1~local
  Version table:
 *** 1.4.3-1~local 100
        100 /var/lib/dpkg/status

```

---

### Post by tarastasesa on 2023-08-27
Thanks 1falleen, I got the same as you:

libdvdcss2:
  Installed: 1.4.3-1~local
  Candidate: 1.4.3-1~local
  Version table:
 *** 1.4.3-1~local 100
        100 /var/lib/dpkg/status

On the DVD cover, there is the usual globe symbol with NTSC2 on it, but under the symbol I read, in Japanese: "Japan nation".
So, it seems that NTSC is not the same everywhere. In this sense, Wikipedia:
[https://en.wikipedia.org/wiki/NTSC](https://en.wikipedia.org/wiki/NTSC)

Any ideas?

---

### Post by #&amp;thj^% on 2023-08-27
Insert your DVD in question and then run:
```
regionset
```
Mine looks:
```
regionset /dev/sr0
Current drive parameters for /dev/sr0:
  RPC Type: Phase II (Hardware)
  RPC Status: no region code set (bitmask=0xFF)

```
I'm not sure I'm familiar with  "Japan nation".
And i assume your friends laptop was bought in Japan? Correct me if I'm wrong

---

### Post by tarastasesa on 2023-08-27
My friens' laptop? Bought in Italy...

---

### Post by #&amp;thj^% on 2023-08-27
I can't in good faith recommend any change to the regionset then.

---

### Post by Rubi1200 on 2023-08-27
Is it just this one specific DVD that is causing issues? Can you play other DVDs? Is it an internal player or plug and play?

---

### Post by tarastasesa on 2023-08-29
Hello 1fallen, run your command and got this:

:~$ regionset
Command 'regionset' not found, but can be installed with:
sudo apt install regionset

So, I run:

XXXXX:~$ sudo apt install regionset
[sudo] password for XXXXX: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  regionset
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 11.0 kB of archives.
After this operation, 41.0 kB of additional disk space will be used.
Get:1 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy/universe amd64 regionset amd64 0.1-3.1 [11.0 kB]
Fetched 11.0 kB in 1s (7,904 B/s)                        
Selecting previously unselected package regionset.
(Reading database ... 208165 files and directories currently installed.)
Preparing to unpack .../regionset_0.1-3.1_amd64.deb ...
Unpacking regionset (0.1-3.1) ...
Setting up regionset (0.1-3.1) ...
Processing triggers for man-db (2.10.2-1) ...

And then, with the DVD inserted in my DVD player (both, the one bought  in Italy, and the second one bought in Japan, nothing changes):

XXXXX:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.

Tried with another DVD (non the Japanese one), with both my DVD player,  the one bought in Italy and the other one bought in Japan, VLC gives me  always the same message:

Playback failure:
DVDRead could not open the disc "/dev/sr0".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.
 
Please note that, before the last Ubuntu 22.04 installation, this last DVD didn't give me any problem. 

Question: could be my proprietary NVIDIA G620 drivers? I cannot find  them on the tab Additional Drivers of Software And Updates  application...

---

### Post by #&amp;thj^% on 2023-08-29
Not sure here, but the failure to find this:
> VLC is unable to open the MRL 'dvd:///dev/sr0'
My Nvidia install just works:
```
 nvidia-smi | grep Driver
| NVIDIA-SMI 535.104.05             Driver Version: 535.104.05   CUDA Version: 12.2     |

```
The only thing I can think of off the top of my head is to link it ie:
```
sudo ln -s /dev/sr0 /dev/dvd
```
Try again any better?
BTW I DID NOT say run regionset , >>my last post to you is>>**"I can't in good faith recommend any change to the regionset then. "**

---

### Post by #&amp;thj^% on 2023-08-30
> **tarastasesa said:**
> Hello 1fallen, run your command and got this:

Question: could be my proprietary NVIDIA G620 drivers? I cannot find  them on the tab Additional Drivers of Software And Updates  application...
I still don't think so but show us this please:
```
*ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.1/0000:01:00.0 ==
modalias : pci:v000010DEd00001F95sv000017AAsd00003A3Ebc03sc00i00
vendor   : NVIDIA Corporation
model    : TU117M [GeForce GTX 1650 Ti Mobile]
driver   : nvidia-driver-525 - distro non-free
driver   : nvidia-driver-535-open - distro non-free
driver   : nvidia-driver-535-server-open - distro non-free
**[COLOR="#FF0000"]driver   : nvidia-driver-535 - distro non-free recommended[/COLOR]**
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-525-server - distro non-free
driver   : nvidia-driver-535-server - distro non-free
driver   : nvidia-driver-525-open - distro non-free
driver   : nvidia-driver-470-server - distro non-free
driver   : nvidia-driver-470 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

```
Highlighted in red is the one I use, and if I'm not mistaken yours will use "nvidia-driver-470 "

---

### Post by tarastasesa on 2023-09-02
Run the command:

```
:~$ ubuntu-drivers devices
```

and got:

```
:~$
```

Of course, on Software and Updates, using the GUI, my PC do not find proprietary drivers at all.
So, tried to install my NVIDA drivers (NVIDIA-Linux_x86_64-390.157.run), downloaded from the NVIDIA page, but for one reason or another, the installation fails. 
Read a few of tutorials, but they didn't help. 
Read also this, which looks very well-done:

[https://www.if-not-true-then-false.com/2021/debian-ubuntu-linux-mint-nvidia-guide/](https://www.if-not-true-then-false.com/2021/debian-ubuntu-linux-mint-nvidia-guide/)

Unfortunately, when arrive to 2.8.2 (Run NVIDIA Binary) and run:

```
./NVIDIA-Linux_x86_64-390.157.run
```

I always get this:
```

./NVIDIA-Linux_x86_64-390.157.run: No such file or directory
```
 
The .run file has the same name with which I downloaded it from NVIDIA page and is located in Download folder.

Of course, had already made the file executable as program.

Please help...

---

### Post by tarastasesa on 2023-09-02
PS: the command:

```
:~$  nvidia-smi | grep Driver
```

gives me this:

```
:~$  
```

while, the command:

```
:~$ sudo ln -s /dev/sr0 /dev/dvd
```

gives me this:

```
ln: failed to create symbolic link '/dev/dvd': File exists
```

---

### Post by #&amp;thj^% on 2023-09-02
I keep saying here, that I do not think Nvidia has anything to do with your "Non playing dvd"
And it's not recommended using the .run file from Nvidia's site. (I strongly suggest that you change back everything to stock)
But i would as a last effort to help you need to see this:
```
groups
```
Check if "cdrom" is listed, like below:
```
me adm cdrom sudo dip plugdev lpadmin sambashare libvirt
```
And please include:
```
inxi -G
```

---

