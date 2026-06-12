---
title: "Thin Liquid Film installation problem"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by Leechpool on 2007-12-07
Hi,
I am a newbee beginning to gather enough Ubuntu knowledge to start enjoying myself but still need lots of help so would appreciate it if someone could help me get Thin Liquid Film TLF working and then I'll be dependant on my windows machine for one less thing (ipod).

Ubuntu 7.04
python 2.5.1c1
TLF 1.00

I managed to install TLF using the instructions, but whenever I run it I get the following in the terminal:

earnie@earnie-desktop:~$ sudo thinliquidfilm
Password:
X Error: BadDevice, invalid or uninitialized input device 169
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
[]
ffmpeg supports xvid
ffmpeg supports h264
tab changed
changed to "encode"
/home/earnie/.thinliquidfilm/latest
1.0
Version Check: Update message already shown
Version Check: This is the latest version
tab changed
changed to "encode"


My ipod mounts at /media/IPOD VIDEO and I changed main.py to reflect this as per one post I found but this made no difference.
Any help would be appreciated.
Cheers
Roger

---

### Post by dixelpixel on 2007-12-08
Hi,

I can't install TLF at all actually. When I click on the "install.py" file Terminal just flashes for an instant then nothing more happens. 

I managed to open the program/GUI by double clicking the "thinliquidfilm.py" file. However as I started to convert a file the whole window froze.

Any chance someone could write up a step by step guide for noobs using TLF?

Cheers,

..dp..

---

### Post by dixelpixel on 2007-12-08
Oh, and I'd like to mention another problem. As my screenshot hopefully demonstrates TLF seems unable to recognise my Ipod so I cannot transfer files anyhow.

Perhaps it's connected to my installation problem, or could there be a problem with the Ipod? (6th generation classic 80 Gb)

All help is very much appreciated :-D

Thanks,

..dp..

---

### Post by Leechpool on 2007-12-12
OK I'm obviously every bit the newbie I feared I was. The installation was actually in and working. What confused me was all the errors in the terminal window when I entered "sudo thinliquidfilm" and the fact that so much in the GUI was greyed out. I didn't realise you have to press the large plus sign at the bottom and either enter a file for conversion or upgrade before the GUI bits become ungreyed and you can use them! Transcode and upload to ipod both work. How stupid was I! (don't bother answering)

The only thing now is that the mount point in the GUI always reverts to /media/ipod and mine mounts at /media/IPOD VIDEO    - I assume this causes the errors in the terminal window as the programme starts. I can change it and it works but even though I hit save it doesn't and reverts the next time I start it. If anyone can help with this I would appreciate it. I'll keep looking at it and post again if I get anywhere.

dixelpixel,

You might be suffering from the same pessimism I was. My installation has the ipod button to the bottom right greyed out until I press the files for transfer tab and press the large plus button and add a file. Then the button ungreys and I can press it to transfer (assuming I've entered the correct mount point).

So I must say I managed to follow the installation guide at [http://thinliquidfilm.org/installation.php](http://thinliquidfilm.org/installation.php)

The only thing that threw me for a while was "pygt". In the end I installed python-qt3 and python-qt4 and it seemed to install OK. The install script was pretty good at telling you if something was missing.

Hope this helps
Cheers
Roger

---

