---
title: "SuperTux!"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by NewWaves on 2006-09-22
Hi,
SuperTux runs so sloooow on my machine!  I only get about 20FPS and is really making me sick in the stomach trying to play it!

Here's my PC specs:

CPU:
Pentium III (Coppermine)
Running at: 1002.458Mhz

Hdd(s):
/dev/hda = 30GB running at 7200RPM (Primary)
 --1.95GB SWAP

/dev/hdb 13GB running at 5200RPM (Secondary)

Video Card:
0000:00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 03)

Ram:
Total: 385256 kB

Top Output:

```
top - 18:38:59 up 2 days, 18:05,  3 users,  load average: 0.64, 1.01, 1.26
Tasks:  88 total,   1 running,  87 sleeping,   0 stopped,   0 zombie
Cpu(s): 21.3% us,  2.7% sy,  0.0% ni, 74.0% id,  0.0% wa,  1.7% hi,  0.3% si
Mem:    385256k total,   368120k used,    17136k free,     9276k buffers
Swap:  2048248k total,    57580k used,  1990668k free,   172868k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4175 root      15   0  105m  33m  11m S  7.6  8.9 181:49.57 Xorg
14946 josh      15   0 40476  14m 9644 S  6.6  4.0   0:03.86 gnome-terminal
 5494 josh      15   0 68812  17m  11m S  4.0  4.6 102:45.27 gnome-btdownloa
 6182 josh      15   0 68980  20m  11m S  3.3  5.4  75:25.84 gnome-btdownloa
14904 josh      15   0 57700 9340 5892 S  1.0  2.4   0:11.43 xmms
14898 josh      15   0 96616  37m  18m S  0.7 10.0   0:32.47 firefox-bin
 4728 josh      15   0 15784 8656 6604 S  0.3  2.2  63:22.16 metacity
 4746 josh      15   0 30300  10m 8316 S  0.3  2.8   0:30.12 update-notifier
15360 josh      16   0  2196 1096  856 R  0.3  0.3   0:00.03 top
    1 root      16   0  1564  476  444 S  0.0  0.1   0:02.77 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.01 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:01.01 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.20 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid

```

Any Ideas?[-o<

---

### Post by Anonii on 2006-09-22
[I]glxinfo | grep direct
[/I]
gives you?

---

### Post by NewWaves on 2006-09-22
> **Anonii said:**
> [I]glxinfo | grep direct
[/I]
gives you?

```

direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

---

