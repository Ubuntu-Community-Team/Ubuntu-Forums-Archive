---
title: "Only Windows network appears"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by billburt on 2010-05-19
Good Day everyone. This is my first post and I am pretty much a newbie.

Using Ubuntu 10.04 on a dual boot desktop that also has WIN 7. Connected to the same router are the following devices:

- 6 mo. old quad processor desktop dual boot listed above (10.04 and WIN7)
- old laptop reformatted with only Ubuntu 10.04
- 2 year old netbook with only Ubuntu 8.01
- 4 year old laptop with only XP Pro

Places/Network lists only Windows Network/MSHOME and Workgroup. MSHOME shows only the laptop with XP. WORKGROUP lists unable to mount.

My question/need for help is **how do I display the Ubuntu devices that are connected to this router** (3 of the 4 devices) in Places/Network?

System/Admin/Network Tools lists only the device I'm on as a Loopback interface - ethernet interface is a selectable choice.

I would like to be able to connect to each device running Ubuntu to send/receive files .

I am able to print to a network connected printer from each of the 3 devices running Ubuntu so I know there is some connection there.

Many thanks.

---

### Post by therieb on 2010-07-19
I'm experiencing the same thing.  I have two netbooks running 10.04 Netbook Remix, and I've activated System--> Preferences --> Personal File Sharing and set my downloads folder to share on both netbooks in System--> Administration--> Shared Folders.  Matters are made slightly more complicated because Netbook Remix lacks a "Places" menu, but I assume the Go--> Network in Nautilus is the same thing.  When I go to that directory, however, all I see is an icon that says windows network.  One of my machines sees itself as a server, but I can't see the shared folders on either machine from the other.  I do not have Samba installed and would like to avoid it if possible.  I am looking for a GUI solution because my wife isn't interested in the command line.  I can ping each box from the other.  Any help appreciated.

---

### Post by dtl on 2010-07-23
Hi. I've had the same issue i believe and got it resolved like this.
On my Mint 9 desktop went into control center-other-file sharing.Ticked file sharing and than moved the wanted files into the shared folder in my home folder. Now I see everything on my other computers.
Hope this helps.

---

