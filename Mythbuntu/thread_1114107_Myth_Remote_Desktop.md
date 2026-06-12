---
title: "Myth Remote Desktop"
date: 2009-04-02
forum: Mythbuntu
---

### Post by DonMegel on 2009-04-02
This is my, fourth thread I think, and its a testament of how helpful the community is that I've been able to move from one problem to the next. This is the last hurdle. I am loving the whole thing, way beyond my expectations. Very very pleased.

Now I need to be able to remote into it. I saw a myriad of options for remoting in using Ubuntu but Mythbuntu, which I used, is slightly different. I also don't know which option is best.

I use Windows on all my other PCs and have a wired/wireless network.

I need to be able to control and install programs on my mythbutntu box. What is my best option and how do I install it?

---

### Post by David Grigor on 2009-04-02
I recently went through this being a newbie this was the easiest I found to do. 

Download and install xming application to your windows environemnt to be able to use the linux gui. Use the xming launch wizard, select one window, put in your ip address of the backend, and select to connect using xdmcp.  Just be sure to turn the xdmcp capability on with the checkbox on the mythbuntu control-centre first. 

Putty.exe to be the easiest for just a terminal mode ( which I use more often ).

---

### Post by DonMegel on 2009-04-02
Just checking the box means I can log onto the mythbox?

---

### Post by Chris Musampa on 2009-04-02
Freenx gets my vote for most purposes, way more responsive than vnc IMO, there is a windows client as well.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by AboveTheLogic on 2009-04-02
> **Chris Musampa said:**
> Freenx gets my vote for most purposes, way more responsive than vnc IMO, there is a windows client as well.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

I second this.... this is what I use to log into a remote session on my mythbox while the main (mythfronend) session remains undisturbed (with the exception of the log in/out sounds).

If you need to log into the same (console) session as the mythfronend, VNC is a good way to go... I'm not sure there are any other choices.

---

### Post by AlecJ on 2009-04-02
I use RealVNC in windows, cos it's free

[http://www.realvnc.com/products/free/4.1/index.html](http://www.realvnc.com/products/free/4.1/index.html)

I have vnc turned on in mythbuntu control center and a password set.
I run realvnc from the windows box using the ip adddress and vnc password for the mythbox, then i have full control.

---

### Post by nickrout on 2009-04-02
> **AlecJ said:**
> I use RealVNC in windows, cos it's free

[http://www.realvnc.com/products/free/4.1/index.html](http://www.realvnc.com/products/free/4.1/index.html)

I have vnc turned on in mythbuntu control center and a password set.
I run realvnc from the windows box using the ip adddress and vnc password for the mythbox, then i have full control.

indeed vnc is already there in mythbuntu, just use it!

but real geeks use the command line, use putty to ssh in and there you are!

---

### Post by DonMegel on 2009-04-03
Well I set up FreeNX and it works perfectly. I am just shocked an amazed at how wonderfuly this is working. The PC is just a XP2100 with 1gig of RAM and it does things that only my Quad Core windows box can do.

I am just thrilled. 

Thank you guys.

---

### Post by newlinux on 2009-04-03
freeNX when I'm tunneling in from work (like I am now so they don't monitor my web browsing :)). Putty if I just need to do some commandline config VNC mostly when I'm at home (don't need to better compression and responsiveness on my LAN). But since most of my PCs at home run Linux, I usually just tunnel X over SSH.

Glad FreeNX worked for you. It's been great for me.

---

### Post by AboveTheLogic on 2009-04-04
I prefer tunnelier over putty.

---

