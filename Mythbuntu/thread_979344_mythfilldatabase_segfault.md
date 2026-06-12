---
title: "mythfilldatabase segfault?"
date: 2008-11-11
forum: Mythbuntu
---

### Post by jape42 on 2008-11-11
Anyone else seeing this?:

jape@mythbackend:~$ dmesg | grep myth
[ 1064.040033] mythfilldatabas[8586]: segfault at 0816ded0 eip 0816ded0 esp b55d5d2c error 15
[ 9721.308833] mythfilldatabas[11162]: segfault at 08187500 eip 08187500 esp b5564d2c error 15
[13993.659584] mythfilldatabas[11958]: segfault at 0816ded0 eip 0816ded0 esp b5547d2c error 15
[18175.816940] mythfilldatabas[12696]: segfault at 0816ded0 eip 0816ded0 esp b5592d2c error 15
[22373.637538] mythfilldatabas[13426]: segfault at 0816ded0 eip 0816ded0 esp b5582d2c error 15
[26574.593639] mythfilldatabas[14495]: segfault at 0816ded0 eip 0816ded0 esp b562dd2c error 15
[34963.408146] mythfilldatabas[15982]: segfault at 0816ded0 eip 0816ded0 esp b561cd2c error 15
[39165.462668] mythfilldatabas[16727]: segfault at 08197698 eip 08197698 esp b55cad2c error 15
[43523.474436] mythfilldatabas[18752]: segfault at 0816ded0 eip 0816ded0 esp b562bd2c error 15
[51973.336657] mythfilldatabas[20508]: segfault at 0816ded0 eip 0816ded0 esp b556fd2c error 15
[64556.781309] mythfilldatabas[23773]: segfault at 0816ded0 eip 0816ded0 esp b55cad2c error 15
jape@mythbackend:~$  

It's not continuously failing, since I have guide data in the db.

jp

---

### Post by fatmonk on 2008-11-12
Have had mythfilldatabase seg fault on me a few times.

Doing a db repair (through phpmyadmin) seems to sort it for me.

-FM

---

### Post by jape42 on 2008-11-16
I turned on the nightly db optimization/repair, but it didn't seem to help:

jape@mythbackend:~$ dmesg | grep myth
[ 1064.040033] mythfilldatabas[8586]: segfault at 0816ded0 eip 0816ded0 esp b55d5d2c error 15
[ 9721.308833] mythfilldatabas[11162]: segfault at 08187500 eip 08187500 esp b5564d2c error 15
[13993.659584] mythfilldatabas[11958]: segfault at 0816ded0 eip 0816ded0 esp b5547d2c error 15
[18175.816940] mythfilldatabas[12696]: segfault at 0816ded0 eip 0816ded0 esp b5592d2c error 15
[22373.637538] mythfilldatabas[13426]: segfault at 0816ded0 eip 0816ded0 esp b5582d2c error 15
[26574.593639] mythfilldatabas[14495]: segfault at 0816ded0 eip 0816ded0 esp b562dd2c error 15
[34963.408146] mythfilldatabas[15982]: segfault at 0816ded0 eip 0816ded0 esp b561cd2c error 15
[39165.462668] mythfilldatabas[16727]: segfault at 08197698 eip 08197698 esp b55cad2c error 15
[43523.474436] mythfilldatabas[18752]: segfault at 0816ded0 eip 0816ded0 esp b562bd2c error 15
[51973.336657] mythfilldatabas[20508]: segfault at 0816ded0 eip 0816ded0 esp b556fd2c error 15
[64556.781309] mythfilldatabas[23773]: segfault at 0816ded0 eip 0816ded0 esp b55cad2c error 15
[77415.666821] mythfilldatabas[26702]: segfault at b5ad91b0 eip b5ad91b0 esp b5479d2c error 15
[81646.267701] mythfilldatabas[27405]: segfault at 08171a28 eip 08171a28 esp b5416d2c error 15
[85830.287281] mythfilldatabas[28109]: segfault at b5b471b0 eip b5b471b0 esp b54e7d2c error 15
[90027.530084] mythfilldatabas[28816]: segfault at b5a701b0 eip b5a701b0 esp b5410d2c error 15
[111193.473567] mythfilldatabas[1716]: segfault at 0818d610 eip 0818d610 esp b54ebd2c error 15
[119632.221717] mythfilldatabas[3131]: segfault at 08171a20 eip 08171a20 esp b54d0d2c error 15
[123826.640027] mythfilldatabas[4328]: segfault at 0818cad0 eip 0818cad0 esp b54e5d2c error 15
[140621.315712] mythfilldatabas[7873]: segfault at 0818d610 eip 0818d610 esp b54b2d2c error 15
[161686.225369] mythfilldatabas[11970]: segfault at 0818d618 eip 0818d618 esp b54f9d2c error 15
[165867.733236] mythfilldatabas[12659]: segfault at 0819d160 eip 0819d160 esp b54abd2c error 15
[178635.216152] mythfilldatabas[15405]: segfault at b5adb1b0 eip b5adb1b0 esp b547bd2c error 15
[187062.099700] mythfilldatabas[16859]: segfault at 08174058 eip 08174058 esp b543cd2c error 15
[195481.336930] mythfilldatabas[19901]: segfault at 08171a28 eip 08171a28 esp b549ed2c error 15
[203895.110168] mythfilldatabas[21448]: segfault at 0818d618 eip 0818d618 esp b550dd2c error 15
[208279.283023] mythfilldatabas[22425]: segfault at 0818d618 eip 0818d618 esp b54f0d2c error 15
[212670.755297] mythfilldatabas[23876]: segfault at b5ada1b0 eip b5ada1b0 esp b547ad2c error 15
[216866.046233] mythfilldatabas[24573]: segfault at 08171a28 eip 08171a28 esp b5432d2c error 15
[221053.085401] mythfilldatabas[25278]: segfault at 08171a28 eip 08171a28 esp b548bd2c error 15
jape@mythbackend:~$ uptime

---

### Post by Joe Jarvis on 2008-11-25
> **jape42 said:**
> Anyone else seeing this?

I have the same problem.  If you find a solution, please post it.  Thanks.

---

### Post by DCMarkie on 2008-11-30
I'm having the same problem.
Running Ibex,
MythTV Version   : 18722
MythTV Branch    : branches/release-0-21-fixes
Library API      : 0.21.20080304-1
Network Protocol : 40
Options compiled in:
 linux profile using_oss using_alsa using_arts using_jack using_backend using_dbox2 using_dvb using_firewire using_frontend using_hdhomerun using_iptv using_ivtv using_joystick_menu using_libfftw3 using_lirc using_opengl_vsync using_opengl_video using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmcw using_xvmc_vld using_glx_proc_addr_arb using_bindings_perl using_bindings_python using_opengl using_ffmpeg_threads using_libavc_5_3 using_live

Error:
[88112.196937] mythfilldatabas[7910]: segfault at 16d80b0 ip 00000000016d80b0 sp 000000004111bdd8 error 15
[231014.312464] mythfilldatabas[20717]: segfault at 1627110 ip 0000000001627110 sp 00000000421cadd8 error 15
[374795.629279] mythfilldatabas[29489]: segfault at 16490b0 ip 00000000016490b0 sp 00000000419bbdd8 error 15
[398793.333265] mythfilldatabas[16052]: segfault at 2778100 ip 0000000002778100 sp 0000000040c1add8 error 15

---

### Post by buntunub on 2008-12-10
Same problem, same error give or take. Doing the db repair via mythbackend works for a week or two and then it happens again. This has only started happening since the last kernel update. I have regressed to the last kernel on Hardy (2.6.24-21-generic) and so far no issues. I never had any issues when running on that kernel, so well see.

---

### Post by Explodinglemur on 2008-12-26
I'm seeing this problem as well.  If I run mythfilldatabase manually from the command line, it doesn't segfault, but it seems to always segfault when run automatically.

Dec  8 03:46:58 mythtv kernel: [6605237.850633] mythfilldatabas[1577]: segfault at 790d20 rip 790d20 rsp 41923a58 error 15
Dec  8 16:30:25 mythtv kernel: [6651019.063674] mythfilldatabas[2143]: segfault at 790d00 rip 790d00 rsp 40d19a58 error 15
Dec  9 10:24:00 mythtv kernel: [6715398.501232] mythfilldatabas[2977]: segfault at 790d00 rip 790d00 rsp 40ae8a58 error 15
Dec 10 13:01:22 mythtv kernel: [6811187.411665] mythfilldatabas[4059]: segfault at 790d00 rip 790d00 rsp 423a4a58 error 15
Dec 11 16:30:51 mythtv kernel: [6910102.404116] mythfilldatabas[5257]: segfault at 790d00 rip 790d00 rsp 42192a58 error 15
Dec 12 20:11:32 mythtv kernel: [7009688.577881] mythfilldatabas[6469]: segfault at 790d30 rip 790d30 rsp 40a95a58 error 15
Dec 13 20:18:42 mythtv kernel: [7096470.307782] mythfilldatabas[8343]: segfault at 790d00 rip 790d00 rsp 40beaa58 error 15
Dec 14 20:15:19 mythtv kernel: [7182619.886739] mythfilldatabas[9627]: segfault at 790d00 rip 790d00 rsp 41875a58 error 15
Dec 15 06:43:13 mythtv kernel: [7220272.849872] mythfilldatabas[10143]: segfault at 790d30 rip 790d30 rsp 41acea58 error 15
Dec 16 14:08:56 mythtv kernel: [7333353.361440] mythfilldatabas[11399]: segfault at 790d30 rip 790d30 rsp 415c1a58 error 15
Dec 17 07:57:12 mythtv kernel: [7397414.502111] mythfilldatabas[12234]: segfault at 790d30 rip 790d30 rsp 41179a58 error 15
Dec 18 12:53:32 mythtv kernel: [7501537.012665] mythfilldatabas[13398]: segfault at 790d00 rip 790d00 rsp 42533a58 error 15
Dec 19 14:01:29 mythtv kernel: [7591963.917847] mythfilldatabas[14422]: segfault at 790d00 rip 790d00 rsp 422a2a58 error 15
Dec 20 16:17:18 mythtv kernel: [15838.087682] mythfilldatabas[7629]: segfault at 799fd0 rip 799fd0 rsp 414f7af8 error 15
Dec 21 03:34:54 mythtv kernel: [56471.950712] mythfilldatabas[14482]: segfault at 788f50 rip 788f50 rsp 41388af8 error 15


These errors appear every day for as far back as my logs go (November 23rd is the earliest I have stored right now).

---

### Post by ian dobson on 2008-12-26
Hi,

I've seen a few seg faults when mythfilldatabase runs. Not every time but usually it's caused by bad XMLTV data (tags not closed etc).

Regards
Ian Dobson

---

### Post by Da_Teach on 2008-12-28
Mine segfaults, not that often though:

[223847.820264] mythfilldatabas[29546]: segfault at 21d38e0 ip 00000000021d38e0 sp 0000000041343e08 error 15
[317338.012487] mythfilldatabas[25129]: segfault at d4f8e0 ip 0000000000d4f8e0 sp 0000000041b35e08 error 15
[401402.672138] mythfilldatabas[17304]: segfault at 22e78e0 ip 00000000022e78e0 sp 0000000041d1be08 error 15

Also had the backend crash on me once:
[641991.718278] mythbackend[11982]: segfault at 100000000 ip 0000000000427578 sp 00007fff74d40ba0 error 4 in mythbackend[400000+111000]

(well actually that happened more but only once in he last 7 days)

---

