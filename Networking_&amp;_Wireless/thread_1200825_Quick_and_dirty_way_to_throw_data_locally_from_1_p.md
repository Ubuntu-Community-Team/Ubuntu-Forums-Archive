---
title: "Quick and dirty way to throw data locally from 1 pc to another."
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-06-30
At work, I run two computers. One is my laptop and a desktop (9.04 only). The desktop is a FOG imaging server, which I use extensively at my desk at work. The laptop is basically a mobile version of the desktop, so I can walk in with my laptop and a 24 port gig switch, hook up a lab, and image them in no time at all.

Thing is, I want my desktop to be the "big guns" for the image storage, however, the desktop and laptop aren't on the network. They have static 192.168.x.x IP addresses.

If I static the desktop @ 192.168.1.100 and the laptop @ 192.168.1.101, is there a way I can throw a crossover in between the two computers and run an rsync script to synchronize the images between the two computers?

---

### Post by jhannah on 2009-06-30
It should just be a matter of plugging in the cable, in fact with most modern NICs you don't even need a cross-over cable- they will simply auto detect it. I'm not sure I am correctly understanding your question however. Neither machine is currently connected to a network? If not, a cross-over cable would probably be your best bet to copy files over quickly and rsync is another good choice to do so. 

Please let me know if I am missing something.

---

### Post by Roasted on 2009-06-30
jhannah - these computers are stand-alone servers, essentially. We use a 10.52 network scheme at work, however, due to this software being "experimental" in our network, I chose to keep it off network. Plus we get much better bandwidth speeds by using a secluded LAN to do imaging lab by lab instead of dealing with shooting images across the main network. Not only that, but we have 7 schools in the district, some as much as 14 miles apart. I can't imagine the downtime to pull a 40 gig photoshop image across those lines...

As a result, I keep two computers running. One is my 80gb laptop which runs Ubuntu/FOG, the other is my desktop, which has substantially more hard drive space. The desktop is at my work bench, which is the main area I do imaging at as far as building images 1 at a time. However, when I transfer them, I put them on an external hard drive and then push them over to my laptop. Due to my laptop's hard drive space, I cannot keep all images there, just a few at a time. So it's handy to just kick an image over that I need in the one middle school library and bam, done, drive over, image them, done.

But my desktop and laptop use 192.168 ip schemes. Based on the nature of this software, I just chose to keep it off the main network, mostly because I am relatively new at my place of work and I am not the network admin, so I wanted things to be done off the network instead of on where I may be accountable.

So in short, I really just need a way to connect a patch/crossover cable to each computer and be able to see each computer's documents. I just want to pull up 2 folders on the desktop. 1 folder being my image directory where the images are stored, the 2nd folder being my laptop. Then just drag/drop and kick an image file over. Then my laptop would be ready to do its mobile job.

Make sense?

---

### Post by 3rdalbum on 2009-07-01
Yep, absolutely. Just install the Samba server on the "remote" computer - that is, the one that you will NOT be sitting at when you drag and drop the image files across.

To configure it, you can run the "shares-admin" command (which is actually a GUI program). Set up a shared folder - this will be either the folder with the images, or the folder that you want the images to go to (depending on which computer you are setting up the server on).

Then under Places > Network you will be able to access your share, and literally drag and drop files across.

---

### Post by mpm on 2009-07-02
Trying the same thing. But I'm having a very basic problem, I cannot get the machines to connect with the crossover cable.  I assume there are no major issues as I had a more complicated samba share set up with the same machines under ubuntu 8.04 (I actually had to connect to a windows share server in order to share).  The ethernet devise attempts to connect, but to no avail.  Any help would be greatly appreciated.
Is it necessary to have static IP addresses?
I'm a noob that just gets lucky, so don't overestimate.

---

