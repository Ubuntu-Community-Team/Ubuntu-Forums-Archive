---
title: "virtual appliance"
date: 2009-06-29
forum: Mythbuntu
---

### Post by jd896 on 2009-06-29
Hi, I’m new to myth tv and mythbuntu. I was wanting to run the myth backend on my hp prol ml115 g5 under esxi4, with a HD homerun tuner, so not to have pci issues as I haven’t yet played with the pci pass-through on esxi4. But I seem have display problems with the GUI backend setup as all I get is different sized pink boxes and no way to select and navigate. The strange thing is that I have installed virtually under VMware workstation and it displays fine I have even converted the workstation vim with the stand alone converter client to my server, and I run into the same display problem does anybody have any ideas or has anybody managed to get this working as a esxi 4 vim

---

### Post by tgm4883 on 2009-06-29
You could ssh in with 

```
ssh backendip -X -Y
```
 
and then do 

```
mythtv-setup
```

---

### Post by jd896 on 2009-07-01
if I’m honest its not the setting up of it that concerns me as I could set up the backend in workstation then simply transfer it to my esxi  server. My problem is if it has display problems with the setup windows, will it be able to encode and record properly or will I possibly run into problems there also.  My thinking is that seen as my proliant ml115 uses old matrox onboard graphics could this be my problem and should I upgrade the server display card, which would benefit my vm, huh may have just answered my own question there.

---

### Post by larsolav on 2009-07-01
For the recordings the HD Homerun captures the digital signals and sends them to your computer where they are saved to your disk. No encoding is occuring as the signal is already in digital format.

---

### Post by ian dobson on 2009-07-02
Hi,

If don't want to watch TV on your backend server you don't need a "good" graphic card. I run my backend almost "headless" (No Display, Keyboard/Mouse).

Regards
Ian Dobson

---

### Post by jd896 on 2009-07-02
yeah the server is headless its remote managed through vmware's management software just had a thought tho would remote desktop work better

---

### Post by divbo on 2009-10-11
Hi,
Did you get this working in the end?

Mythtv seems to be the only app that doesn't work in Ubuntu under vmware.

See attachment for what the myth backend setup GUI looks like.

Thanks

Dave

---

### Post by Bungo71 on 2009-12-21
Looks like what I get.  (posted in another thread on this too from jd896)

I think it's related to the direct rendering manager, but don't know how to get mythtv-setup to work without it.

cheers

Bungo

---

### Post by Bungo71 on 2009-12-21
Additionally, running it from a VNC connection yeild's the same thing.

cheers

Bungo

---

### Post by jd896 on 2009-12-21
sorry bout the lack of attention to this thread my proliant had to be used to fill in for a faulty production server i'll try setting up the backend with a nvidia PCIe card in the server and try to alocate more video mem to it seen as the server as the old matrox chip in it i'll let eveeryone know later tonight 
 
p.s. anybody know esxi 4's support for host graphics cards lol

---

### Post by divbo on 2009-12-21
Hey guys,

I found two ways around this issue.

Run from a terminal session from another ubuntu box with a working video card and some form of X installed:

```

ssh -X mythtvbackendserverIP
mythtv-setup

```

mythtvbackendserverIP = IP of your backend server
I run this from my front end box.

The other option is to use mythbuntu 9.10 which includes Mythtv 0.22 RC.
This version of mythtv must use a different direct rendering method as it works perfectly with ESXi 4.0 :)

---

### Post by Bungo71 on 2009-12-22
I just tested the 9.10 solution and it does indeed work, but I see you found this out already.  I've a few people I know with many issues with 9.10 compared to 9.04 that prevents them from using it.

Might be my only option here tho...

cheers

Bungo

---

### Post by newlinux on 2009-12-22
maybe using freenx or nxserver remotely would work. This is how I remotely administer some of my machines. Install freenx on the VM and then run a remote X session (not X forwarding) using nxclient.

---

