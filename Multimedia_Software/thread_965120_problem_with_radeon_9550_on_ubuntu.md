---
title: "problem with radeon 9550 on ubuntu"
date: 2008-10-31
forum: Multimedia Software
---

### Post by aparadektos on 2008-10-31
first of all i am a complitly newbie, so please help!!

like i said i have the graphics card radeon 9550 and i have installed the drivers that ubuntu suggested me from the hardwer drivers...

the problem that i noticed is that i have a very bad graphic analysis when i watch a movie (the quality of the movies is good for sure!!!).the programs that i have used is vlc and the movie player that ubuntu has.

i wrote some commands to the terminal that might help you understand my problem!

this is the message i get after "fglrxinfo"

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 2.1.7412 Release


and this is the message i get after "dmesg | grep glrx"

[   39.811747] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   40.159274] [fglrx] Maximum main memory to use for locked dma buffers: 1172 MBytes.
[   40.159324] [fglrx] ASYNCIO init succeed!
[   40.159454] [fglrx] PAT is enabled successfully!
[   40.184197] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   56.688006] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   56.688018] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   56.688023] [fglrx] AGP detected, AgpState   = 0x1f000207 (hardware caps of chipset)
[   56.689677] [fglrx] AGP enabled,  AgpCommand = 0x1f000304 (selected caps)
[   56.694841] [fglrx] GART Table is not in FRAME_BUFFER range
[   56.694856] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   56.694859] [fglrx] Reserve Block - 1 offset =  0Xffff000 length = 0X1000
[   56.842044] [fglrx] interrupt source 20008000 successfully enabled
[   56.842055] [fglrx] enable ID = 0x00000004
[   56.842526] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   56.842853] [fglrx] interrupt source 10000000 successfully enabled
[   56.842858] [fglrx] enable ID = 0x00000005
[   56.843206] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000


thank you for your time people!!!

---

### Post by vinnie on 2008-10-31
There seems to be a bug in the driver that affects that model.
You can read the details [here]("http://www.ubuntu.com/getubuntu/releasenotes/810") and [here]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408")

---

