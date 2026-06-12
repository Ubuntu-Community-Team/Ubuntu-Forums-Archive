---
title: "fileserver+media server (HTPC) hardware and software"
date: 2011-09-29
forum: Multimedia Software
---

### Post by jebus_beler on 2011-09-29
Hi,

I'm trying to build an ubuntu-based fileserver that might (eventually) double as a media server/HTPC.  The primary purpose is to act as a server (mostly files but maybe ldap and other such stuff) and its supposed to be cheap, inconspicuous, silent and tasteful looking :-)  I think I have the basics specs for this system down but I'm still undecided about whether to get a dedicated HTPC case with an LCD/VFD and remote control or just get a more server-friendly case and then try to use a smart-phone to act as a remote control.

I don't know much about HTPC software but from what I can gather XBMS seems to be the primary (open source) option.  So I have a few questions:

- How well does this run in a virtualized environment?
- Is it better to get a dedicated hardware remote and display or are their good software based options if I have an old smartphone lying around (I do :-) ).

Ideally the HTPC software and interface will run in a VM on the server and a fileserver such as samba would run in another server.  The HTPC software would actually access the media files over the network (even if this just loops back to the local machine) and would have read-only access.  This is for my own peace of mind as I want the fileserver to be a locked down machine and not to have to run HTPC software.

So would it make sense, e.g., to run something like Mythbuntu on a VM on my server or just to run some software like XBMS on a standard ubuntu install?  I'm afraid I'm quite ignorant of this side of things.

If a dedicated HTPC case would be preferably can anyone make recommendations?  I've seen a few nice, but expensive offerings:

- Antec Fusion Micro, Remote and Max
- Sivlerstone GD01MX or GD02MX (expensive)

Any other recommendations?  One preference would be to support at least 4+ internal HDs. Oh, and space is also a concern as it would be great if I could slip this into a cabinet (not so with the Lian-Li mentioned below unfortunately).

I somehow think it would be nicer to "roll my own" and control things via a smartphone but don't know if e.g. XBMS has such a interface.

Just for reference here's my putative build:

Lian-Li PC-Q08 case
Asus P8H61-I
 Be Quiet! 300W Pure Power L7 PSU
Pentium G620 
2 GB DDR3-1333 RAM
WD Green 2TB

An advantage of this build is the ability to upgrade to the ram, add HDs and even upgrade to a more serious processor if needed.

Sorry for the long-winded post....

---

### Post by WasMeHere on 2011-09-29
I would not build a combined ubuntu-based fileserver and media server/HTPC, because I think that the tasks are rather different and demand different hardware.

Have you considered a NAS (network-attached storage) server? A simple software solution for a media center pc might be to use [_GeeXboX_]("http://www.geexbox.org")? It is a live mediaplayer using xbmc with USB persistent user data storage.

---

### Post by jebus_beler on 2011-09-30
Thanks for the reply Olle.  The point is this is mostly going to be a file server and that was my initial goal in building it.  But it occurred to me that down the line it might well double as a media server as I might have an extra screen lying around and it would be nice to have something that works like a traditional tv/video (i.e. from the couch with a remote rather than watching something of my computer screen).  As a media server i don't expect to play games or do anything intense on it.  I'm guessing the HW I mentioned below can support 1080p decoding, etc... and the only issues I can see with making it a media server are:

- Desire for a remote control and LCD/VFS style display (which a smart-phone can maybe replace).
- The desire to sandbox the media software in a VM.

So my question is just whether there's an issue doing the two above.  While I love building boxes its not particularly efficient, cost-wise, environment-wise, and space-wise to have a dedicated box for each digital service.

---

### Post by WasMeHere on 2011-10-02
> **jebus_beler said:**
> ... I'm guessing the HW I mentioned below can support 1080p decoding, etc... and the only issues I can see with making it a media server are:

- Desire for a remote control and LCD/VFS style display (which a smart-phone can maybe replace).
- The desire to sandbox the media software in a VM.

So my question is just whether there's an issue doing the two above.  While I love building boxes its not particularly efficient, cost-wise, environment-wise, and space-wise to have a dedicated box for each digital service.
I see your points and I think you know enough to succeed.

*Plan A.*
I am not sure if it would be efficient enough to run the media software in a VM. My experience is that it will be faster to run directly in a physical machine. *Try it* :-) Playback of high definition video may suffer. But in that case try

*Plan B.*
- install your multimedia software directly into your server system or
*Plan C.*
- install dual boot (boot as server or boot as htpc) if it would be OK to shut down your server, or
-  boot GeeXbox off a usb flash drive!

Good luck and have fun
Olle

---

