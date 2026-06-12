---
title: "No Sound With Players, please help"
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by MetalPrincess on 2008-04-02
I'm using Ubuntu 7.10 on a AMD Sempron 3000+ with a USB Hi-Fi Link (All sound goes through my stereo) on my machine. I have a problem playing mp3 or any audio files on all player except the Totem Movie Player. This plays the mp3 tracks, but I would prefer to use a different player. The default Rhythm box does not work either. Just the movie player works. I currently do not get any sound at all through the other players. 

Also when I shut the PC down I get an error message sorta like this:

> Could not get system Bus, Make Sure Bus Daemon Is Running.

That is the basic gist of the message, it flashes so quickly that I cannot read it all adn I have no idea how to pause it. Is this maybe the problem or am I looking at a 2 fold problem here that are totally unrelated to each other?

TIA!

---

### Post by xc3RnbFO8P on 2008-04-02
In terminal:
> rhythmbox
and play mp3
Show output.

---

### Post by MetalPrincess on 2008-04-02
Ok I played a mp3 whle I had the rythmn box open after putting that in the terminal and there is no output. what output do you mean? I'm kinda lost. The terminal did not come up with anything at all.

---

### Post by xc3RnbFO8P on 2008-04-02
I'm sorry, you open the terminal and type rhythmbox > return
then you play mp3

---

### Post by MetalPrincess on 2008-04-02
> **Ringi said:**
> I'm sorry, you open the terminal and type rhythmbox > return
then you play mp3

Erm yeah that's exactly what I did. When it opened the program I played a mp3 while keeping the terminal open. There was no message in the terminal at all during or after.

---

### Post by xc3RnbFO8P on 2008-04-02
I cant find any solution on internet, only this bug: [https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/152045]("https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/152045")
What is the output **lsusb** in terminal?

---

### Post by MetalPrincess on 2008-04-02
I get this:

> Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 09ef:0101 Xitel MD-Port DG2 MiniDisc Interface
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by xc3RnbFO8P on 2008-04-03
In Synaptic Package Manager search: **jack**
see if you got **libasound-plugins** and **libjack0** installed.

---

### Post by MetalPrincess on 2008-04-03
They were not installed. I will test it when my sister is awake later to see if that solved the problem and post back here.

---

### Post by MetalPrincess on 2008-04-06
Nope nada no go. Did not work :( Is there anything I can do at all to get sound to work in a regular audio player on here?

---

### Post by xc3RnbFO8P on 2008-04-06
Xmms
Amarok
Banshee
Listen
Exaile
Gimmix
Aqualung
All players are in Add/Remove (All Available Application)
You just have to try them out, I can not find any solution to this problem, sorry.

---

### Post by MetalPrincess on 2008-04-06
Thanks for trying. :( I already have a few of those installed and did try it out on them with nothing happening. However I think what I might do is install my soundcard in the motherboard because I'm using the built in sound on the board right now. So I will add a soundcard to the board and see if that helps any at all :D

---

### Post by xc3RnbFO8P on 2008-04-06
Yes maybe thats best, looking at others peoples problem with this issue, you are lucky to get a sound :)

---

