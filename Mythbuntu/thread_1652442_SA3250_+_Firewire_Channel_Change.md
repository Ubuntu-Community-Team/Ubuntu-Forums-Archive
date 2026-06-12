---
title: "SA3250 + Firewire Channel Change?"
date: 2010-12-24
forum: Mythbuntu
---

### Post by zepfan on 2010-12-24
Hi all,
I've recently gotten a SA3250 and it works perfectly except for one thing. I can't change channels via firewire! Recording works fine, viewing works fine, but I have to change the channel on the box to the channel I want. 

My box is on node 1, and my mythtv setting is 3250, set to 4250 ( I've tried them all though). I've tried the 3250 script, doesn't work. I've tried mythprime, doesn't work. I've tired mythchanger, doesn't work. 

Any one else have this problem? Everything works except the channel changing. I've tried my IR transmitter, but the one that came with my remote doesn't seem to work at all, so that's not any help. 

Any advice?

---

### Post by LowSky on 2010-12-25
mythchanger works just fine for me but i found the instructions they include to be backwards

i use the following to get it to work

```
mythchanger -f 4 -c xxx
```

4 is my cable box, for your try 1 or 2
xxx is the channel you wish to tune to

try from terminal it should work from there too.

dont forget to enter it in the mythbackend and leave out the channel portion
looks like this 
```
mythchanger -f 1 -c
```

---

### Post by zepfan on 2010-12-25
Thanks, I tried that. It still won't change channels. Sucks too because everything else works. I just have to change the channel on the STB to the channel I want to tune.

---

### Post by zepfan on 2010-12-25
Ok I've tried two 3250 boxes (we have 3 in the house) and it still doesn't work. Firewire issue maybe?

---

### Post by zepfan on 2010-12-25
Ok I've tried two different Pc's with different firewire brands, and two different 3250's. Am I doing something wrong? I hooked up the firewire to the back and to the mobo. I get results from everything except channel change.

---

### Post by LowSky on 2010-12-25
did you install the dependencies of mychanger?
 * build-essential

 * libraw1394-dev

 * libiec61883-dev

 * libavc1394-dev

---

### Post by zepfan on 2010-12-25
> **LowSky said:**
> did you install the dependencies of mychanger?
 * build-essential

 * libraw1394-dev

 * libiec61883-dev

 * libavc1394-dev

Yup. Theyre all installed.

---

### Post by zepfan on 2010-12-25
Here's my output from mythchanger.

```
 peter@HTPC:~/Documents/changer$ mythchanger -f 1 -c 004 -v

mythchanger .10f beta

Acquiring firewire handle... OK.
1 port(s) found

Acquiring handle on port 0... 1 devices detected.
STB Vendor ID: 0x1692 Model ID: 0x0be0, Scientific Atlanta Model SA3250HD

(Using user selected channel changer #1)

Skipping empty node 1
1 STB(s) found:
-------------
STB 1: port=0, node=0, changer=1, GUID=0x0016921249f20000

```

Output from SA3250CH
```

peter@HTPC:~/Documents/3250$ sudo sa3250ch -v 055node 0: vendor_id = 0x00001692 model_id = 0x00000be0
AV/C Command: 055 = cmd0=0x00487ce7 cmd2=0x04353530 cmd3=0xff000000
AV/C Command: 055 = cmd0=0x00487c67 cmd2=0x04303535 cmd3=0xff000000

```

---

### Post by LowSky on 2010-12-26
It does look like its working. I get nearly the same output for my setup
```
john@jpc-desktop:~$ mythchanger -f 4 -c 0002 -v

mythchanger .10f beta

Acquiring firewire handle... OK.
1 port(s) found

Acquiring handle on port 0... 1 devices detected.
Skipping empty node 0
STB Vendor ID: 0x1cea Model ID: 0x10cc, Scientific Atlanta Model SA4250HDC

(Using user selected channel changer #4)

1 STB(s) found:
-------------
STB 1: port=0, node=1, changer=4, GUID=0x001cea1b2ab40000


```


what is the output of this command?

```
plugreport
```

and try this:

 ```
 mythchanger -f 2 -c 0002 -v
```

---

### Post by zepfan on 2010-12-26
```
plugreport
```

Here's my output

```

root@HTPC:/home/peter/Documents/changer# plugreport
Host Adapter 0
==============

Node 0 GUID 0x0010dc00016b32b6
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Node 1 GUID 0x0016921249f20000
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=1
	channel=0, data_rate=2, overhead_id=0, payload=146
iMPR n_plugs=0, data_rate=2

```


```
 mythchanger -f 2 -c 0002 -v
```

Here's my output

```

root@HTPC:/home/peter/Documents/changer#  mythchanger -f 2 -c 0002 -v

mythchanger .10f beta

Acquiring firewire handle... OK.
1 port(s) found

Acquiring handle on port 0... 1 devices detected.
Skipping empty node 0
STB Vendor ID: 0x1692 Model ID: 0x0be0, Scientific Atlanta Model SA3250HD

(Using user selected channel changer #2)

1 STB(s) found:
-------------
STB 1: port=0, node=1, changer=2, GUID=0x0016921249f20000

```

Still does the same thing. Still shows the channel tuned, but it doesn't change. In mythtvfrontend, if I change the channel, it shows the channel changed on the OSD, but it still shows the same show from the same previous channel.

---

### Post by LowSky on 2010-12-26
Reboot the cable box, and dont just turn it off unplug it from the wall. and try again.

---

### Post by zepfan on 2010-12-26
> **LowSky said:**
> Reboot the cable box, and dont just turn it off unplug it from the wall. and try again.

Then press power or leave it off(so that time is showing)?
Nevermind, couldn't get a lock with it off, so had to turn it on. Same issue, same output from the codes, just node 0 now.

---

### Post by LowSky on 2010-12-26
try restting the connection on the PC

```
mythchanger -R 
```

---

### Post by zepfan on 2010-12-26
Just gives me the man page. Is that normal?

Ran the same commands, no dice.

---

### Post by zepfan on 2010-12-27
Any other thoughts?

---

### Post by zepfan on 2010-12-31
I installed mythdora to test. Still wouldn't work. I'm using mythbuntu 10.10, is it too new for firewire control? I saw on mythwiki that libraw1394 had to be < 1.2.1 . Any other thoughts? Anyone?

---

### Post by LowSky on 2011-01-01
Sorry I'm out of ideas... Works for me with 10.10 just fine.

---

### Post by zepfan on 2011-01-01
> **LowSky said:**
> Sorry I'm out of ideas... Works for me with 10.10 just fine.

Well thanks for trying! I'll just buy an IR blaster (more money!)

---

