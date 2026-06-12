---
title: "Dvd dont play on lubuntu 14.04 fix?"
date: 2014-04-25
forum: Multimedia Software
---

### Post by tomsubt on 2014-04-25
Hi,  I was told to install these but they are not in the software center>>>

open the Software Center and install the packages libdvdcss, libdvdread4, and libdvdnav4 by searching for them (upper-right-hand corner)

How can I get a dvd to play on Lubuntu 14.04?


I have Ubuntu on my desktop and it had the items in the software center but not on 14.04

---

### Post by Dennis N on 2014-04-25
Both packages are in the universe repository.

Install them with [B][FONT=Courier New]sudo apt-get install libdvdread4 libdvdnav4

[/FONT][/B]Then run this command in the terminal

**[FONT=Courier New]sudo /usr/share/doc/libdvdread4/install-css.sh[/FONT]**

---

### Post by tomsubt on 2014-04-25
Ok, When I tried to install >>sudo apt-get install libdvdread4 libdvdnav4

It stated I already had the libdvdnav4

so I went to the next command you gave me>>> sudo /usr/share/doc/libdvdread4/install-css.sh 

and it stated No Such File Or Directory!

Anything else I can try, Thank You

PS:  I noticed I can install the ubuntu software center on Lubuntu wouldnt that give me a way to install these items, my desktop has it and the dvd plays just fine?

---

### Post by Dennis N on 2014-04-25
Those instructions come from here:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

You can check them over. I don't see any error in the post. The same directory and contents exists on Lubuntu 14.04.

---

### Post by tomsubt on 2014-04-25
it does not mention lubuntu 14.04 that I can see and the software center does not have it in there, do you think I should install the ubuntu software center and extract it from there?

---

### Post by Dennis N on 2014-04-25
> it does not mention lubuntu 14.04 that I can see

That's what I was getting at by "The same directory and contents exists on Lubuntu 14.04". It applies also to Lubuntu. If you run the first command, it creates the directory  **/usr/share/doc/libdvdread4/** and the files inside it no matter what Desktop Environment (Unity, LXDE, XFCE) you are using. You could have a typo in the command. Copy and paste if necessary from the page I referred you to. You can also check if the package was installed by the command:

**apt-cache policy livdvdread4**

from the terminal.

If it says  **Installed: (none)** then your install went wrong somehow.

Lubuntu Software Center is a subset of Ubuntu Software Center. I think you can use the latter instead if you want to. Lubuntu Software Center may omit packages not relevant to Lubuntu, but I really can't speak for Lubuntu.

---

### Post by tomsubt on 2014-04-25
I copied and pasted into terminal the commands and it keeps saying libdvdread 4 is not found in the package

---

### Post by tomsubt on 2014-04-25
shouldn't the libdvdread4 be in the get software in lubuntu software center, its not?

---

### Post by Dennis N on 2014-04-25
Lubuntu 14.04 comes with Synaptic Package manager (Menu > System Tools > Synaptic Package Manager). Use that and you will find it. I just did. Just use the Search box on top.

Added comment: I can't find it in Lubuntu Software Center. Doesn't it have a search function? Anyway, I'm not surprised, as it seems to focus on user applications, which I think is appropriate, and not underlying packages.

---

### Post by tomsubt on 2014-04-25
ok I found both the libdvd2 1.2.13.0

and the libdvd read4   Both with a checkmark,

 doesn't that mean they are installed, if so why isn't the terminal finding these and what can I do about it? Thanks

---

### Post by Dennis N on 2014-04-25
> **tomsubt said:**
> ok I found both the libdvd2 1.2.13.0

and the libdvd read4   Both with a checkmark,

 doesn't that mean they are installed, if so why isn't the terminal finding these and what can I do about it? Thanks

Don't put any space in the name. Its all one word: **libdvdread4** and not **libdvd read4** as you wrote. I suggest you copy the command from the page (highlight the text to copy and then Ctrl-C), and paste into the terminal to avoid errors. Shift-Ctrl-V will paste text into the terminal screen. Again, the given command is:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Enter your password, and when complete, that will end this job.

---

### Post by tomsubt on 2014-04-25
ok, here is the results

tom@tom-Aspire-3100:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
[sudo] password for tom: 
--2014-04-25 17:47:02--  [http://download.videolan.org/pub/debian/stable//Packages](http://download.videolan.org/pub/debian/stable//Packages)
Resolving download.videolan.org (download.videolan.org)... 88.191.250.9, 2a01:e0d:1:3:58bf:fa02:0:2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3520 (3.4K) [text/plain]
Saving to: &#8216;/tmp/dvdcss-w7PZet/Packages&#8217;

100%[======================================>] 3,520       --.-K/s   in 0.1s    

2014-04-25 17:47:03 (24.3 KB/s) - &#8216;/tmp/dvdcss-w7PZet/Packages&#8217; saved [3520/3520]

--2014-04-25 17:47:03--  [http://download.videolan.org/pub/debian/stable/stable/libdvdcss2_1.2.13-0_i386.deb](http://download.videolan.org/pub/debian/stable/stable/libdvdcss2_1.2.13-0_i386.deb)
Resolving download.videolan.org (download.videolan.org)... 88.191.250.9, 2a01:e0d:1:3:58bf:fa02:0:2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44316 (43K) [application/octet-stream]
Saving to: &#8216;/tmp/dvdcss-w7PZet/libdvdcss.deb&#8217;

100%[======================================>] 44,316      73.9KB/s   in 0.6s   

2014-04-25 17:47:04 (73.9 KB/s) - &#8216;/tmp/dvdcss-w7PZet/libdvdcss.deb&#8217; saved [44316/44316]

dpkg: error: dpkg status database is locked by another process
Dynamic fetch failed; Falling back to static fetch
--2014-04-25 17:47:04--  [http://download.videolan.org/pub/debian/stable/libdvdcss2_1.2.13-0_i386.deb](http://download.videolan.org/pub/debian/stable/libdvdcss2_1.2.13-0_i386.deb)
Resolving download.videolan.org (download.videolan.org)... 88.191.250.9, 2a01:e0d:1:3:58bf:fa02:0:2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44316 (43K) [application/octet-stream]
Saving to: &#8216;/tmp/dvdcss-w7PZet/libdvdcss.deb&#8217;

100%[======================================>] 44,316      74.2KB/s   in 0.6s   

2014-04-25 17:47:05 (74.2 KB/s) - &#8216;/tmp/dvdcss-w7PZet/libdvdcss.deb&#8217; saved [44316/44316]

dpkg: error: dpkg status database is locked by another process
tom@tom-Aspire-3100:~$

---

### Post by Yellow Pasque on 2014-04-25
> dpkg: error: dpkg status database is locked by another process
Try it again. This time, make sure Synaptic, Software Center, or any other package manager is not open/running. ;)

---

### Post by tomsubt on 2014-04-26
Ok,  I made sure nothing was open and here are the results, can I play the dvd now or is there other instructions first? Thanks>>

tom@tom-Aspire-3100:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
[sudo] password for tom: 
--2014-04-26 09:56:58--  [http://download.videolan.org/pub/debian/stable//Packages](http://download.videolan.org/pub/debian/stable//Packages)
Resolving download.videolan.org (download.videolan.org)... 88.191.250.9, 2a01:e0d:1:3:58bf:fa02:0:2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3520 (3.4K) [text/plain]
Saving to: &#8216;/tmp/dvdcss-rg1Rne/Packages&#8217;

100%[======================================>] 3,520       22.5KB/s   in 0.2s   

2014-04-26 09:57:03 (22.5 KB/s) - &#8216;/tmp/dvdcss-rg1Rne/Packages&#8217; saved [3520/3520]

--2014-04-26 09:57:03--  [http://download.videolan.org/pub/debian/stable/stable/libdvdcss2_1.2.13-0_i386.deb](http://download.videolan.org/pub/debian/stable/stable/libdvdcss2_1.2.13-0_i386.deb)
Resolving download.videolan.org (download.videolan.org)... 88.191.250.9, 2a01:e0d:1:3:58bf:fa02:0:2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44316 (43K) [application/octet-stream]
Saving to: &#8216;/tmp/dvdcss-rg1Rne/libdvdcss.deb&#8217;

100%[======================================>] 44,316      52.5KB/s   in 0.8s   

2014-04-26 09:57:05 (52.5 KB/s) - &#8216;/tmp/dvdcss-rg1Rne/libdvdcss.deb&#8217; saved [44316/44316]

(Reading database ... 202314 files and directories currently installed.)
Preparing to unpack .../dvdcss-rg1Rne/libdvdcss.deb ...
Unpacking libdvdcss2 (1.2.13-0) over (1.2.13-0) ...
Setting up libdvdcss2 (1.2.13-0) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...

PS: I just tried to play a dvd and still getting the MRL error

---

### Post by Yellow Pasque on 2014-04-26
> I just tried to play a dvd and still getting the MRL error

What MRL error? What player are you trying to use and what happens when you start it from the terminal and try to play a disc (copy/paste the output).

I find VLC is good for logging errors.
```
vlc --file-logging
```

---

### Post by tomsubt on 2014-04-26
Here is the error from the vlc screen>>>>>

Playback failure:
DVDRead could not open the disc "/dev/dvd1".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/dvd1'. Check the log for details.

 Thanks I could not get the log to come up got this instead>>

tom@tom-Aspire-3100:~$ vlc --file-logging
VLC media player 2.1.2 Rincewind (revision 2.1.2-0-ga4c4876)
[0x980ae90] logger interface: using logger.

---

### Post by Yellow Pasque on 2014-04-26
Okay, so the next step is to check whether you have a /dev/dvd1 device or VLC is looking at the wrong device name. It's very possible that your device is actually named /dev/sr0

> Thanks I could not get the log to come up got this instead>>
Heh, that's what you want. The point is to copy/paste or attach the log file (but don't do that right now because it won't be helpful until you get the correct /dev device).
The default location for the log file is ~/.config/vlc-log.txt

---

### Post by tomsubt on 2014-04-26
You said the next step is to check whether you have a /dev/dvd1 device or VLC is looking at the wrong device name. It's very possible that your device is actually named /dev/sr0
 
How do I check this out? Thanks

---

### Post by tomsubt on 2014-04-26
You said the next step is to check whether you have a /dev/dvd1 device or VLC is looking at the wrong device name. It's very possible that your device is actually named /dev/sr0
 
How do I check this out? Thanks

---

### Post by Yellow Pasque on 2014-04-26
```
cd /dev
ls -la
```

---

### Post by tomsubt on 2014-04-26
here is what i got, hope i did it right>>>

tom@tom-Aspire-3100:~$ cd /dev ls -la
tom@tom-Aspire-3100:/dev$

---

### Post by tomsubt on 2014-04-26
when i put ls la  by itself I got this

tom@tom-Aspire-3100:~$ ls -la
total 132
drwxr-xr-x 23 tom  tom  4096 Apr 26 14:27 .
drwxr-xr-x  3 root root 4096 Apr 12 09:41 ..
drwx------  3 tom  tom  4096 Apr 13 10:54 .adobe
-rw-------  1 tom  tom  3021 Apr 26 14:53 .bash_history
-rw-r--r--  1 tom  tom   220 Apr 12 09:41 .bash_logout
-rw-r--r--  1 tom  tom  3637 Apr 12 09:41 .bashrc
drwx------ 12 tom  tom  4096 Apr 26 14:27 .cache
drwx------ 23 tom  tom  4096 Apr 23 16:17 .config
drwxr-xr-x  2 tom  tom  4096 Apr 23 11:16 Desktop
-rw-r--r--  1 tom  tom    26 Apr 23 12:03 .dmrc
drwxr-xr-x  2 tom  tom  4096 Apr 12 09:50 Documents
drwxr-xr-x  2 tom  tom  4096 Apr 26 11:06 Downloads
drwx------  3 tom  tom  4096 Apr 26 14:54 .gconf
-rw-r-----  1 tom  tom     0 Apr 12 10:02 .gksu.lock
drwx------  4 tom  tom  4096 Apr 23 15:25 .gnome2
drwx------  2 tom  tom  4096 Apr 23 15:25 .gnome2_private
drwxr-xr-x  2 tom  tom  4096 Apr 24 09:47 .gstreamer-0.10
drwxr-xr-x  3 tom  tom  4096 Apr 12 09:50 .local
drwx------  3 tom  tom  4096 Apr 13 10:54 .macromedia
drwx------  4 tom  tom  4096 Apr 12 09:51 .mozilla
drwxr-xr-x  2 tom  tom  4096 Apr 13 04:29 .mplayer
drwxr-xr-x  2 tom  tom  4096 Apr 12 09:50 Music
drwxr-xr-x  2 tom  tom  4096 Apr 12 09:50 Pictures
-rw-r--r--  1 tom  tom   675 Apr 12 09:41 .profile
drwxr-xr-x  2 tom  tom  4096 Apr 12 09:50 Public
drwx------  6 tom  tom  4096 Apr 24 12:38 .purple
drwxr-xr-x  2 tom  tom  4096 Apr 12 09:50 Templates
drwx------  4 tom  tom  4096 Apr 13 04:23 .thumbnails
drwxr-xr-x  2 tom  tom  4096 Apr 12 09:50 Videos
-rw-rw-r--  1 tom  tom   536 Apr 26 10:49 vlc-log.txt
-rw-------  1 tom  tom    60 Apr 26 14:27 .Xauthority
-rw-r--r--  1 tom  tom    14 Apr 25  2013 .xscreensaver
-rw-------  1 tom  tom   108 Apr 26 14:27 .xsession-errors
-rw-------  1 tom  tom   212 Apr 26 11:57 .xsession-errors.old

---

### Post by tomsubt on 2014-04-26
Sorry about the duplicate reply

---

### Post by Yellow Pasque on 2014-04-26
*sigh*
I'm not sure what you're doing but, you really screwed that up. Try it again. Here it is in one command.
```
cd /dev; ls -la
```

---

### Post by tomsubt on 2014-04-26
ok, I copied and pasted the command and here are the results

tom@tom-Aspire-3100:~$ cd /dev; ls -la
total 4
drwxr-xr-x  14 root root        4040 Apr 26 14:27 .
drwxr-xr-x  22 root root        4096 Apr 22 17:03 ..
crw-------   1 root root     10, 235 Apr 26 14:27 autofs
drwxr-xr-x   2 root root         640 Apr 26 14:27 block
drwxr-xr-x   2 root root          80 Apr 26 14:27 bsg
crw-------   1 root root     10, 234 Apr 26 14:27 btrfs-control
drwxr-xr-x   3 root root          60 Apr 26 14:26 bus
lrwxrwxrwx   1 root root           3 Apr 26 14:27 cdrom -> sr0
drwxr-xr-x   2 root root        3560 Apr 26 14:27 char
crw-------   1 root root      5,   1 Apr 26 14:27 console
lrwxrwxrwx   1 root root          11 Apr 26 14:27 core -> /proc/kcore
crw-------   1 root root     10,  60 Apr 26 14:27 cpu_dma_latency
crw-------   1 root root     10, 203 Apr 26 14:27 cuse
drwxr-xr-x   5 root root         100 Apr 26 14:27 disk
drwxr-xr-x   2 root root          80 Apr 26 14:27 dri
crw-------   1 root root     10,  61 Apr 26 14:27 ecryptfs
crw-rw----   1 root video    29,   0 Apr 26 14:27 fb0
lrwxrwxrwx   1 root root          13 Apr 26 14:27 fd -> /proc/self/fd
crw-rw-rw-   1 root root      1,   7 Apr 26 14:27 full
crw-rw-rw-   1 root root     10, 229 Apr 26 14:27 fuse
crw-------   1 root root    251,   0 Apr 26 14:27 hidraw0
crw-------   1 root root     10, 228 Apr 26 14:27 hpet
lrwxrwxrwx   1 root root          14 Apr 26 14:27 .initramfs -> /run/initramfs
drwxr-xr-x   4 root root         340 Apr 26 14:27 input
crw-r--r--   1 root root      1,  11 Apr 26 14:27 kmsg
srw-rw-rw-   1 root root           0 Apr 26 14:27 log
brw-rw----   1 root disk      7,   0 Apr 26 14:27 loop0
brw-rw----   1 root disk      7,   1 Apr 26 14:27 loop1
brw-rw----   1 root disk      7,   2 Apr 26 14:27 loop2
brw-rw----   1 root disk      7,   3 Apr 26 14:27 loop3
brw-rw----   1 root disk      7,   4 Apr 26 14:27 loop4
brw-rw----   1 root disk      7,   5 Apr 26 14:27 loop5
brw-rw----   1 root disk      7,   6 Apr 26 14:27 loop6
brw-rw----   1 root disk      7,   7 Apr 26 14:27 loop7
crw-------   1 root root     10, 237 Apr 26 14:27 loop-control
drwxr-xr-x   2 root root          60 Apr 26 14:26 mapper
crw-------   1 root root     10, 227 Apr 26 14:27 mcelog
crw-r-----   1 root kmem      1,   1 Apr 26 14:27 mem
drwxr-xr-x   2 root root          60 Apr 26 14:26 net
crw-------   1 root root     10,  59 Apr 26 14:27 network_latency
crw-------   1 root root     10,  58 Apr 26 14:27 network_throughput
crw-rw-rw-   1 root root      1,   3 Apr 26 14:27 null
crw-r-----   1 root kmem      1,   4 Apr 26 14:27 port
crw-------   1 root root    108,   0 Apr 26 14:27 ppp
crw-------   1 root root     10,   1 Apr 26 14:27 psaux
crw-rw-rw-   1 root tty       5,   2 Apr 26 16:06 ptmx
drwxr-xr-x   2 root root           0 Apr 26 14:26 pts
brw-rw----   1 root disk      1,   0 Apr 26 14:27 ram0
brw-rw----   1 root disk      1,   1 Apr 26 14:27 ram1
brw-rw----   1 root disk      1,  10 Apr 26 14:27 ram10
brw-rw----   1 root disk      1,  11 Apr 26 14:27 ram11
brw-rw----   1 root disk      1,  12 Apr 26 14:27 ram12
brw-rw----   1 root disk      1,  13 Apr 26 14:27 ram13
brw-rw----   1 root disk      1,  14 Apr 26 14:27 ram14
brw-rw----   1 root disk      1,  15 Apr 26 14:27 ram15
brw-rw----   1 root disk      1,   2 Apr 26 14:27 ram2
brw-rw----   1 root disk      1,   3 Apr 26 14:27 ram3
brw-rw----   1 root disk      1,   4 Apr 26 14:27 ram4
brw-rw----   1 root disk      1,   5 Apr 26 14:27 ram5
brw-rw----   1 root disk      1,   6 Apr 26 14:27 ram6
brw-rw----   1 root disk      1,   7 Apr 26 14:27 ram7
brw-rw----   1 root disk      1,   8 Apr 26 14:27 ram8
brw-rw----   1 root disk      1,   9 Apr 26 14:27 ram9
crw-rw-rw-   1 root root      1,   8 Apr 26 14:27 random
crw-r--r--   1 root root     10,  62 Apr 26 14:27 rfkill
lrwxrwxrwx   1 root root           4 Apr 26 14:27 rtc -> rtc0
crw-------   1 root root    254,   0 Apr 26 14:27 rtc0
brw-rw----   1 root disk      8,   0 Apr 26 14:27 sda
brw-rw----   1 root disk      8,   1 Apr 26 14:27 sda1
brw-rw----   1 root disk      8,   2 Apr 26 14:27 sda2
brw-rw----   1 root disk      8,   5 Apr 26 14:27 sda5
crw-rw----   1 root disk     21,   0 Apr 26 14:27 sg0
crw-rw----+  1 root cdrom    21,   1 Apr 26 14:27 sg1
lrwxrwxrwx   1 root root           8 Apr 26 14:27 shm -> /run/shm
crw-------   1 root root     10, 231 Apr 26 14:27 snapshot
drwxr-xr-x   3 root root         240 Apr 26 14:27 snd
brw-rw----+  1 root cdrom    11,   0 Apr 26 14:27 sr0
lrwxrwxrwx   1 root root          15 Apr 26 14:27 stderr -> /proc/self/fd/2
lrwxrwxrwx   1 root root          15 Apr 26 14:27 stdin -> /proc/self/fd/0
lrwxrwxrwx   1 root root          15 Apr 26 14:27 stdout -> /proc/self/fd/1
crw-rw-rw-   1 root tty       5,   0 Apr 26 14:27 tty
crw--w----   1 root tty       4,   0 Apr 26 14:27 tty0
crw-rw----   1 root tty       4,   1 Apr 26 14:27 tty1
crw--w----   1 root tty       4,  10 Apr 26 14:27 tty10
crw--w----   1 root tty       4,  11 Apr 26 14:27 tty11
crw--w----   1 root tty       4,  12 Apr 26 14:27 tty12
crw--w----   1 root tty       4,  13 Apr 26 14:27 tty13
crw--w----   1 root tty       4,  14 Apr 26 14:27 tty14
crw--w----   1 root tty       4,  15 Apr 26 14:27 tty15
crw--w----   1 root tty       4,  16 Apr 26 14:27 tty16
crw--w----   1 root tty       4,  17 Apr 26 14:27 tty17
crw--w----   1 root tty       4,  18 Apr 26 14:27 tty18
crw--w----   1 root tty       4,  19 Apr 26 14:27 tty19
crw-rw----   1 root tty       4,   2 Apr 26 14:27 tty2
crw--w----   1 root tty       4,  20 Apr 26 14:27 tty20
crw--w----   1 root tty       4,  21 Apr 26 14:27 tty21
crw--w----   1 root tty       4,  22 Apr 26 14:27 tty22
crw--w----   1 root tty       4,  23 Apr 26 14:27 tty23
crw--w----   1 root tty       4,  24 Apr 26 14:27 tty24
crw--w----   1 root tty       4,  25 Apr 26 14:27 tty25
crw--w----   1 root tty       4,  26 Apr 26 14:27 tty26
crw--w----   1 root tty       4,  27 Apr 26 14:27 tty27
crw--w----   1 root tty       4,  28 Apr 26 14:27 tty28
crw--w----   1 root tty       4,  29 Apr 26 14:27 tty29
crw-rw----   1 root tty       4,   3 Apr 26 14:27 tty3
crw--w----   1 root tty       4,  30 Apr 26 14:27 tty30
crw--w----   1 root tty       4,  31 Apr 26 14:27 tty31
crw--w----   1 root tty       4,  32 Apr 26 14:27 tty32
crw--w----   1 root tty       4,  33 Apr 26 14:27 tty33
crw--w----   1 root tty       4,  34 Apr 26 14:27 tty34
crw--w----   1 root tty       4,  35 Apr 26 14:27 tty35
crw--w----   1 root tty       4,  36 Apr 26 14:27 tty36
crw--w----   1 root tty       4,  37 Apr 26 14:27 tty37
crw--w----   1 root tty       4,  38 Apr 26 14:27 tty38
crw--w----   1 root tty       4,  39 Apr 26 14:27 tty39
crw-rw----   1 root tty       4,   4 Apr 26 14:27 tty4
crw--w----   1 root tty       4,  40 Apr 26 14:27 tty40
crw--w----   1 root tty       4,  41 Apr 26 14:27 tty41
crw--w----   1 root tty       4,  42 Apr 26 14:27 tty42
crw--w----   1 root tty       4,  43 Apr 26 14:27 tty43
crw--w----   1 root tty       4,  44 Apr 26 14:27 tty44
crw--w----   1 root tty       4,  45 Apr 26 14:27 tty45
crw--w----   1 root tty       4,  46 Apr 26 14:27 tty46
crw--w----   1 root tty       4,  47 Apr 26 14:27 tty47
crw--w----   1 root tty       4,  48 Apr 26 14:27 tty48
crw--w----   1 root tty       4,  49 Apr 26 14:27 tty49
crw-rw----   1 root tty       4,   5 Apr 26 14:27 tty5
crw--w----   1 root tty       4,  50 Apr 26 14:27 tty50
crw--w----   1 root tty       4,  51 Apr 26 14:27 tty51
crw--w----   1 root tty       4,  52 Apr 26 14:27 tty52
crw--w----   1 root tty       4,  53 Apr 26 14:27 tty53
crw--w----   1 root tty       4,  54 Apr 26 14:27 tty54
crw--w----   1 root tty       4,  55 Apr 26 14:27 tty55
crw--w----   1 root tty       4,  56 Apr 26 14:27 tty56
crw--w----   1 root tty       4,  57 Apr 26 14:27 tty57
crw--w----   1 root tty       4,  58 Apr 26 14:27 tty58
crw--w----   1 root tty       4,  59 Apr 26 14:27 tty59
crw-rw----   1 root tty       4,   6 Apr 26 14:27 tty6
crw--w----   1 root tty       4,  60 Apr 26 14:27 tty60
crw--w----   1 root tty       4,  61 Apr 26 14:27 tty61
crw--w----   1 root tty       4,  62 Apr 26 14:27 tty62
crw--w----   1 root tty       4,  63 Apr 26 14:27 tty63
crw--w----   1 root tty       4,   7 Apr 26 14:27 tty7
crw--w----   1 root tty       4,   8 Apr 26 14:27 tty8
crw--w----   1 root tty       4,   9 Apr 26 14:27 tty9
crw-------   1 root root      5,   3 Apr 26 14:27 ttyprintk
crw-rw----   1 root dialout   4,  64 Apr 26 14:27 ttyS0
crw-rw----   1 root dialout   4,  65 Apr 26 14:27 ttyS1
crw-rw----   1 root dialout   4,  74 Apr 26 14:27 ttyS10
crw-rw----   1 root dialout   4,  75 Apr 26 14:27 ttyS11
crw-rw----   1 root dialout   4,  76 Apr 26 14:27 ttyS12
crw-rw----   1 root dialout   4,  77 Apr 26 14:27 ttyS13
crw-rw----   1 root dialout   4,  78 Apr 26 14:27 ttyS14
crw-rw----   1 root dialout   4,  79 Apr 26 14:27 ttyS15
crw-rw----   1 root dialout   4,  80 Apr 26 14:27 ttyS16
crw-rw----   1 root dialout   4,  81 Apr 26 14:27 ttyS17
crw-rw----   1 root dialout   4,  82 Apr 26 14:27 ttyS18
crw-rw----   1 root dialout   4,  83 Apr 26 14:27 ttyS19
crw-rw----   1 root dialout   4,  66 Apr 26 14:27 ttyS2
crw-rw----   1 root dialout   4,  84 Apr 26 14:27 ttyS20
crw-rw----   1 root dialout   4,  85 Apr 26 14:27 ttyS21
crw-rw----   1 root dialout   4,  86 Apr 26 14:27 ttyS22
crw-rw----   1 root dialout   4,  87 Apr 26 14:27 ttyS23
crw-rw----   1 root dialout   4,  88 Apr 26 14:27 ttyS24
crw-rw----   1 root dialout   4,  89 Apr 26 14:27 ttyS25
crw-rw----   1 root dialout   4,  90 Apr 26 14:27 ttyS26
crw-rw----   1 root dialout   4,  91 Apr 26 14:27 ttyS27
crw-rw----   1 root dialout   4,  92 Apr 26 14:27 ttyS28
crw-rw----   1 root dialout   4,  93 Apr 26 14:27 ttyS29
crw-rw----   1 root dialout   4,  67 Apr 26 14:27 ttyS3
crw-rw----   1 root dialout   4,  94 Apr 26 14:27 ttyS30
crw-rw----   1 root dialout   4,  95 Apr 26 14:27 ttyS31
crw-rw----   1 root dialout   4,  68 Apr 26 14:27 ttyS4
crw-rw----   1 root dialout   4,  69 Apr 26 14:27 ttyS5
crw-rw----   1 root dialout   4,  70 Apr 26 14:27 ttyS6
crw-rw----   1 root dialout   4,  71 Apr 26 14:27 ttyS7
crw-rw----   1 root dialout   4,  72 Apr 26 14:27 ttyS8
crw-rw----   1 root dialout   4,  73 Apr 26 14:27 ttyS9
drwxr-xr-x   3 root root          60 Apr 26 14:27 .udev
crw-------   1 root root     10, 239 Apr 26 14:27 uhid
crw-------   1 root root     10, 223 Apr 26 14:27 uinput
crw-rw-rw-   1 root root      1,   9 Apr 26 14:27 urandom
crw-rw----   1 root tty       7,   0 Apr 26 14:27 vcs
crw-rw----   1 root tty       7,   1 Apr 26 14:27 vcs1
crw-rw----   1 root tty       7,   2 Apr 26 14:27 vcs2
crw-rw----   1 root tty       7,   3 Apr 26 14:27 vcs3
crw-rw----   1 root tty       7,   4 Apr 26 14:27 vcs4
crw-rw----   1 root tty       7,   5 Apr 26 14:27 vcs5
crw-rw----   1 root tty       7,   6 Apr 26 14:27 vcs6
crw-rw----   1 root tty       7,   7 Apr 26 14:27 vcs7
crw-rw----   1 root tty       7, 128 Apr 26 14:27 vcsa
crw-rw----   1 root tty       7, 129 Apr 26 14:27 vcsa1
crw-rw----   1 root tty       7, 130 Apr 26 14:27 vcsa2
crw-rw----   1 root tty       7, 131 Apr 26 14:27 vcsa3
crw-rw----   1 root tty       7, 132 Apr 26 14:27 vcsa4
crw-rw----   1 root tty       7, 133 Apr 26 14:27 vcsa5
crw-rw----   1 root tty       7, 134 Apr 26 14:27 vcsa6
crw-rw----   1 root tty       7, 135 Apr 26 14:27 vcsa7
crw-------   1 root root     10,  63 Apr 26 14:27 vga_arbiter
crw-------   1 root root     10, 238 Apr 26 14:27 vhost-net
crw-rw-rw-   1 root root      1,   5 Apr 26 14:27 zero
brw-rw----   1 root disk    251,   0 Apr 26 14:27 zram0
tom@tom-Aspire-3100:/dev$

---

### Post by Yellow Pasque on 2014-04-26
The device is /dev/sr0
So if you try to use VLC, then you need to enter /dev/sr0 when you select Media -> Open Disc

---

### Post by tomsubt on 2014-04-27
I did as you instructed but still get this different error message, please see here>>

Playback failure:
DVDRead could not open the disc "/dev/sr0".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.

Also entered this to get the log to come up but all i got was the vlc player on the screen>>

tom@tom-Aspire-3100:~$ vlc --file-logging
VLC media player 2.1.2 Rincewind (revision 2.1.2-0-ga4c4876)
[0x88d6e90] logger interface: using logger.
tom@tom-Aspire-3100:~$

---

### Post by Yellow Pasque on 2014-04-27
The log is just a text file. You have to open it with a text editor. Assuming leafpad is still the default Lubuntu text editor, this command should do it.
```
leafpad ~/.config/vlc-log.txt
```

---

### Post by tomsubt on 2014-04-27
after pasting this in the terminal to see the log file, it was empty leafpad ~/.config/vlc-log.txt <<< No log

---

### Post by tomsubt on 2014-04-28
Temüjin:  Since dvd's play on my desktop that has Ubuntu software center on it, would it do any good to install Ubuntu software center on the laptop along with Lubuntu software center.
Would it play a dvd then with the right codes? Thanks

---

### Post by tomsubt on 2014-04-28
Temüjin:  Since dvd's play on my desktop that has Ubuntu software center on it, would it do any good to install Ubuntu software center on the laptop along with Lubuntu software center.
Would it play a dvd then with the right codes? Thanks

---

### Post by temporos on 2014-05-04
I'm having issues, too, with playing DVDs on Lubuntu 14.04. I'm using GNOME Mplayer instead of VLC, but that shouldn't really make a difference, since I know Mplayer can play DVDs.

I have the *ubuntu-restricted-extras* package installed, and already installed css from the command line. I also set the default optical device to */dev/sr0* (my DVD drive's mount location) in Mplayer, but it still won't play the DVD. When I try to open the DVD (File > Disc > Open DVD with menus), it tries to load for about half a second, then it simply stops and plays nothing.

The codecs are there, because if I open the largest VOB file directly from PCManFM, the file will play fine in Mplayer. But that one VOB file isn't the whole DVD; it's just a part of it.

Any idea what's going on? I'm not sure how to dump logging into into a file from MPlayer.

---

### Post by tomsubt on 2014-05-05
I tried the terminal again and after typing in "sudo apt-get install libdvdread4"  it states the I have the newest version, but when I typed in "sudo/usr/share/doc/libdvdread4/install-css.sh".  It states No such file or directory!

How can I add this file or directory? Thanks

---

### Post by temporos on 2014-05-05
There should be a space between "sudo" and "/usr" in that string. Try this (copy and paste it into a terminal window; don't retype it).

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by Yellow Pasque on 2014-05-06
@temporos: the OP already has installed css with the script. I'm not sure why he is trying to do it again.

> Since dvd's play on my desktop that has Ubuntu software center on it, would it do any good to install Ubuntu software center on the laptop along with Lubuntu software center.
No, it will not make a difference. They're all pulling packages from the same place, just with different interfaces.

Try this:
```
vlc --file-logging --verbose=2 --logfile /home/tom/log.txt
```
Then try to play the DVD (changing to /dev/sr0), and when it fails, exit vlc and attach or pastebin the /home/tom/log.txt file

---

### Post by tomsubt on 2014-05-06
ok, This is what I got now, hope it was done correctly>>>          m@tom-Aspire-3100:~$ vlc --file-logging --verbose=2 --logfile /home/tom/log.txt
VLC media player 2.1.2 Rincewind (revision 2.1.2-0-ga4c4876)
[0x93c3910] main libvlc debug: VLC media player - 2.1.2 Rincewind
[0x93c3910] main libvlc debug: Copyright © 1996-2013 the VideoLAN team
[0x93c3910] main libvlc debug: revision 2.1.2-0-ga4c4876
[0x93c3910] main libvlc debug: configured with ./configure  '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--localstatedir=/var' '--libdir=${prefix}/lib/i386-linux-gnu' '--libexecdir=${prefix}/lib/i386-linux-gnu' '--disable-dependency-tracking' '--build=i686-linux-gnu' 'CPPFLAGS=-D_FORTIFY_SOURCE=2' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' '--config-cache' '--disable-maintainer-mode' '--disable-silent-rules' '--disable-update-check' '--enable-fast-install' '--prefix=/usr' '--docdir=/usr/share/doc/vlc-nox' '--libdir=/usr/lib' '--sysconfdir=/etc' '--with-binary-version=2build2' '--enable-a52' '--enable-aa' '--enable-bluray' '--enable-bonjour' '--enable-caca' '--enable-chromaprint' '--enable-dbus' '--enable-dca' '--enable-dirac' '--enable-directfb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad' '--enable-flac' '--enable-fluidsynth' '--enable-freetype' '--enable-fribidi' '--enable-gnutls' '--enable-jack' '--enable-kate' '--enable-libass' '--enable-libfreerdp' '--enable-libmpeg2' '--enable-libxml2' '--enable-lirc' '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod' '--enable-mpc' '--enable-mtp' '--enable-mux_ogg' '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-opus' '--enable-oss' '--enable-pulse' '--enable-qt' '--enable-realrtsp' '--enable-samplerate' '--enable-schroedinger' '--enable-sdl' '--enable-sftp' '--enable-shout' '--enable-skins2' '--enable-smbclient' '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-theora' '--enable-twolame' '--enable-upnp' '--enable-vcd' '--enable-vcdx' '--enable-vorbis' '--enable-x264' '--enable-zvbi' '--with-kde-solid=/usr/share/kde4/apps/solid/actions/' '--disable-decklink' '--disable-dxva2' '--disable-fdkaac' '--disable-gnomevfs' '--disable-goom' '--disable-libvnc' '--disable-opencv' '--disable-projectm' '--disable-quicksync' '--disable-sndio' '--disable-telx' '--disable-vsxu' '--disable-wasapi' '--enable-alsa' '--enable-atmo' '--enable-dc1394' '--enable-dv1394' '--enable-linsys' '--enable-omxil' '--enable-udev' '--enable-libva' '--enable-v4l2' '--enable-crystalhd' '--enable-mmx' '--enable-sse' '--disable-neon' '--disable-altivec' 'CFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security' 'CXXFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security' 'build_alias=i686-linux-gnu'
[0x93c3910] main libvlc debug: searching plug-in modules
[0x93c3910] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins.dat
[0x93c3910] main libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0x93c3910] main libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins.dat
[0x93c3910] main libvlc debug: plug-ins loaded: 426 modules
[0x93c3910] main libvlc debug: opening config file (/home/tom/.config/vlc/vlcrc)
[0x93c3910] main libvlc debug: translation test: code is "C"
[0x93c3910] main libvlc debug: CPU has capabilities MMX MMXEXT SSE SSE2 SSE3 3DNow! FPU 
[0x93d2eb8] main interface debug: looking for interface module matching "logger,none": 19 candidates
[0x93d2eb8] logger interface: using logger.
[0x93d2eb8] logger interface debug: opening logfile `/home/tom/log.txt'
libdvdnav: Using dvdnav version 4.2.1
libdvdread: Can't stat /dev/sr0
No such file or directory
libdvdread: Could not open /dev/sr0
libdvdnav: vm: failed to open/read the DVD
libdvdread: Can't stat /dev/sr0
No such file or directory
libdvdread: Could not open /dev/sr0
Twoum + Twoum...

---

### Post by tomsubt on 2014-05-06
ok I see where I did not attach    exit vlc and attach or pastebin the /home/tom/log.txt file  how do I get to the log.text file?

---

### Post by tomsubt on 2014-05-06
tom@tom-Aspire-3100:~$ vlc --file-logging
VLC media player 2.1.2 Rincewind (revision 2.1.2-0-ga4c4876)
[0x980ee90] logger interface: using logger.
libdvdnav: Using dvdnav version 4.2.1
libdvdread: Can't stat /dev/sr0
No such file or directory
libdvdread: Could not open /dev/sr0
libdvdnav: vm: failed to open/read the DVD
libdvdread: Can't stat /dev/sr0
No such file or directory
libdvdread: Could not open /dev/sr0
tom@tom-Aspire-3100:~$ vlc --file-logging
VLC media player 2.1.2 Rincewind (revision 2.1.2-0-ga4c4876)

---

### Post by Yellow Pasque on 2014-05-07
> libdvdread: Can't stat /dev/sr0 No such file or directory

^That's odd because your earlier /dev listing showed sr0:
```
brw-rw----+ 1 root cdrom 11, 0 Apr 26 14:27 sr0
```

Please run these commands and show output:
```
sudo apt-get install lshw
sudo lshw -C disk -sanitize
cat /etc/group | grep cdrom
```

---

### Post by tomsubt on 2014-05-07
Ok, This is what came up>>>> tom@tom-Aspire-3100:~$ sudo apt-get install lshw
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lshw is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
tom@tom-Aspire-3100:~$ sudo lshw -C disk -sanitize
  *-disk                  
       description: ATA Disk
       product: ST98823AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.06
       serial: [REMOVED]
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=00014109
tom@tom-Aspire-3100:~$ cat /etc/group | grep cdrom
cdrom:x:24:tom

---

### Post by Yellow Pasque on 2014-05-07
lshw doesn't even see the drive. Is it connected to the motherboard correctly? Have you tried other operating systems or discs?

Anything in dmesg?
```
dmesg | grep -i cd
```

---

### Post by tomsubt on 2014-05-07
Results heretom@tom-Aspire-3100:~$ dmesg | grep -i cd
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=fcd6aecc-ef94-4dd0-8000-f69b0e50e5b9 ro quiet splash vt.handoff=7
[    0.275033] system 00:07: [io  0x0cd4-0x0cd5] has been reserved
[    0.275037] system 00:07: [io  0x0cd6-0x0cd7] has been reserved
[    0.275041] system 00:07: [io  0x0cd8-0x0cdf] has been reserved
[    1.432328] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.520236] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    1.520619] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.607961] usb usb2: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    1.664135] usb usb3: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    1.664403] uhci_hcd: USB Universal Host Controller Interface driver
[    2.050327] 8139too 0000:06:01.0 eth0: RealTek RTL8139 at 0x0001a000, 00:16:d4:cd:60:e2, IRQ 21
[   20.391677] [drm]     LCD1: INTERNAL_LVDS
 
I forgot that the old owner of this laptop somehow removed the cd drive but I was using a external cd drive which worked on my desktop pc using ubuntu ok
Shouldn't work on the laptop as well? I installed lubuntu on laptop with it?

---

### Post by Yellow Pasque on 2014-05-07
Is it a USB drive? Do you know it's model number?

---

### Post by tomsubt on 2014-05-07
> **Temüjin said:**
> Is it a USB drive? Do you know it's model number?

Yes, Its a USB CDRom Drive, but I cannot see a model # anywhere!

---

### Post by Yellow Pasque on 2014-05-07
Okay, check if lsusb recognizes it.
Unplug the drive and plug it back in. Then show output of:
```
lsusb
dmesg | tail -n 10
```

---

### Post by tomsubt on 2014-05-07
Here is what came up>>>  tom@tom-Aspire-3100:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 192f:0916 Avago Technologies, Pte. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
tom@tom-Aspire-3100:~$ dmesg | tail -n 10
[   38.815400] ath5k 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   38.815407] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   38.815411] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   38.816283] wlan0: associate with 0c:d5:02:38:95:15 (try 1/3)
[   38.818304] wlan0: RX AssocResp from 0c:d5:02:38:95:15 (capab=0x411 status=0 aid=2)
[   38.818626] wlan0: associated
[   52.787582] audit_printk_skb: 105 callbacks suppressed
[   52.787590] type=1400 audit(1399487241.779:47): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1589 comm="apparmor_parser"
[   52.787603] type=1400 audit(1399487241.779:48): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1589 comm="apparmor_parser"
[   52.788793] type=1400 audit(1399487241.783:49): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1589 comm="apparmor_parser"

---

### Post by Yellow Pasque on 2014-05-07
There's no mention of it (Avago is your mouse). The drive is not being recognized at all. Have you tried different USB ports? (If that doesn't work, I'm out of ideas..)

---

### Post by tomsubt on 2014-05-07
ok I tried a different port is this better?>>>>   tom@tom-Aspire-3100:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 192f:0916 Avago Technologies, Pte. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
tom@tom-Aspire-3100:~$ dmesg | tail -n 10
[   38.815400] ath5k 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   38.815407] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   38.815411] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   38.816283] wlan0: associate with 0c:d5:02:38:95:15 (try 1/3)
[   38.818304] wlan0: RX AssocResp from 0c:d5:02:38:95:15 (capab=0x411 status=0 aid=2)
[   38.818626] wlan0: associated
[   52.787582] audit_printk_skb: 105 callbacks suppressed
[   52.787590] type=1400 audit(1399487241.779:47): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1589 comm="apparmor_parser"
[   52.787603] type=1400 audit(1399487241.779:48): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1589 comm="apparmor_parser"
[   52.788793] type=1400 audit(1399487241.783:49): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1589 comm="apparmor_parser"

---

### Post by Yellow Pasque on 2014-05-07
Still not recognizing the drive...

---

### Post by tomsubt on 2014-05-07
Dont understand it, it recognized the drive when I installed ubuntu 13.10 then upgraded to 
14.04 can the usb ports go bad, my mouse works ok in them, i even took the mouse out and plugged in the cdrom and still no dvd play?
Is there anything else i can try?

---

### Post by tomsubt on 2014-05-08
I think I know what happened and why I was able to install Lubuntu. its because I was using windows to install it with the external cdrom and windows recognized it, but after Lubuntu was installed, lubuntu could not find the cdrom drive located originally on the laptop and for some reason you cannot use a external cdrom drive using lubuntu. Thats the best I can figure, and why I cannot get Lubuntu to recognize the external drive I dont know. So I guess I will never be able to use it now. Is anyone else able to use a external cdrom on Lubuntu, please let me know?  Thank You

---

### Post by pwolters on 2014-07-24
I see this behaviour on multiple installs of mine. It has nothing to do with hardware as this has functioned OK, even when I boot up Ubuntu 13.10 DVD works fine. So must have something to do with 14.04 doing strange things.

lshw -C disk states following:
[FONT=courier new]  *-cdrom[/FONT]
[FONT=courier new]       description: DVD-RAM writer[/FONT]
[FONT=courier new]       product: CDDVDW SH-S202J[/FONT]
[FONT=courier new]       vendor: TSSTcorp[/FONT]
[FONT=courier new]       physical id: 0.0.0[/FONT]
[FONT=courier new]       bus info: scsi@4:0.0.0[/FONT]
[FONT=courier new]       logical name: /dev/cdrom[/FONT]
[FONT=courier new]       logical name: /dev/sr0[/FONT]
[FONT=courier new]       version: SB01[/FONT]
[FONT=courier new]       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram[/FONT]
[FONT=courier new]       configuration: ansiversion=5 status=nodisc[/FONT]

Where the drive really is loaded, or having disc.


An ls on sr0, where DVD resides looks to give me all the right impressions:
[FONT=courier new]ls -l /dev/sr0 [/FONT]
[FONT=courier new]brw-rw----+ 1 root cdrom 11, 0 jul 24 11:52 /dev/sr0[/FONT]



Even root cannot mount the DVD so this cannot be a rights problem.

---

### Post by tomsubt on 2014-07-24
Yeah  Your right,  I had no problem with 13.10 either,  I might have to go back to it. 
Wish they could fix it though lubuntu is nice and fast for my laptop, Ok, Thanks for the Reply

---

### Post by avdiel1946 on 2014-08-03
after running sudo apt-get install libdvdcssread4, that and libdvdnav4 are installed. After running the install procedure, libdvdcss is still not installed. How do I fix this?

---

