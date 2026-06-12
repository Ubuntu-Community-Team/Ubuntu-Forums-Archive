---
title: "Video capture and editing on Solaris vs Debian vs Ubuntu"
date: 2011-12-28
forum: Multimedia Software
---

### Post by Marcus Aurelius on 2011-12-28
I am interested in doing some heavy  video work.  I have a ADVC 110 Video capture device, which I am using to  capture VHS video tapes, which I will convert on the server to DVD  format and burn to DVD's using DVD production software. I will also take  the captured video file and split it up in parts and convert to other  formats.  
 I will have a need to rip DVD video and encoding.  

My question is for these tasks what setup do you suggest for the following. 

The server that will be doing this work is:

HP Proliant DL-380 G4 
Dual CPU's 3.20 ghz / 800 mhz / 1MB L2
5120 MB RAM
6 hard disks on HP Smart Array 6i controller (36.4 GB Ultra320 SCSI HD each)
RAID set to RAID 5 (5 discs) with one spare (6th disk)
USB, 2 Ethernet ports, 1 ILO port, 1 SCSI port

When it comes to the 6 disk raid I am setting up I was planning to use  RAID-5 on 5 disks using the 6th disk as a spare. Do you think this will  be to slow (due to the parity) since I will be doing so much video  editing?
My other choice was RAID 1+0 (RAID 10).  This would not allow me to have  that extra spare.  Which do you think would be best?  I have at least  50 - 2 hour VHS tapes to capture and DVD's not included.

As far as the operating system I am still considering the one to use.  I   am concerned about security, so I am undecided as to how much   proprietary software I will install on this machine.  Flash etc, make me   a little wary.

I have used Ubuntu on my laptop and have been very satisfied, especially  with the community support.  However I am looking to try something new  and not sure what to expect as far as support and available software  necessary to perform the above requirements (and others not mentioned). 

I am deciding between Debian 6 (squeeze) and Solaris, but will default to Ubuntu if this is a bad idea.  I am probably  going to install Debian on another laptop I have, and was thinking about  Solaris for this server.

The video requirements are one of the major functions this server must  perform, and I do not know to much about Solaris.  What recommendations  do you have concerning the video requirements, and how Solaris will work  on this server hardware.  If it is a poor choice, please tell me what you do recommend.  Thank you.

---

### Post by Marcus Aurelius on 2011-12-28
ttt

---

### Post by 2F4U on 2011-12-29
I don't know too much about Solaris, but unless you get a paid subscription, you won't get updates for it (not even security fixes). Did you already check that the software you need is available for Solaris? Since it is more dedicated towards the more classical server usage, it may not provide the software you need.
Solaris is usually also behind Linux with respect to hardware support, so you might want to look at this before making a decision.
Talking about security and stability, besides the desktop version of Ubuntu there is also a server edition and I would strongly recommend that you use that for a server. The server edition has five years of support (which is even more than Debian provides) for a LTS version (and thats what you will want to get).

---

