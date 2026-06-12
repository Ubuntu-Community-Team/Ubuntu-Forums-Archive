---
title: "Opening up my Ubuntu box"
date: 2006-02-06
forum: Networking &amp; Wireless
---

### Post by kennethb on 2006-02-06
I have a home office with 4 Macs (OSX) and one Windows (XP Pro) and one Linux (Ubuntu Breezy 5.0) in place. I can't access by Ubuntu box from the Macs or Windows boxes - which is a good thing! How do I open up a port so my home/internal network can detect my Ubuntu box? I'm very comfortable using the command line in a term session.

---

### Post by dickohead on 2006-02-06
What kind of access do you need? Command line access to the ubunto box, file sharing, web based?

For simple command line access just install ssh-server onto Ubuntu and use an ssh client to connect to the machine using the IP address or domain name.

FOr file sharing between Mac/Linux and Windows you will need to install NFS or Samba, samba is probably easier in a multi-platform environment however.

---

### Post by kennethb on 2006-02-07
I have SSH installed, and I can access my Linux box from my Mac via the command line with no problem. However, the Mac Finder doesn't detect the Linux box.

I can access both my Mac and Windows box from my Linux box, but I can't access my Linux box from my Mac or Windows boxes. 

I was thinking that I may need to open up a port on my Linux box.

---

### Post by dickohead on 2006-02-07
When you say you can't access them, are we still talking ssh? ping? Or have we moved the food chain to file sharing and network browsing?

---

### Post by kennethb on 2006-02-08
I mean file sharing and network browsing. 

From my Linux box:
1. I use SMB to browse my Windows box with the Nautulus file browsing GUI. 
2. I use the cmd line to SSH to connect to my iMac
I'd like to browse my iMac with Nautulus.

From my iMac box:
1. I can use the cmd line to SSH to my Linux Box.
2. I can use the Mac Finder to browse my Windows box.
I'd like to browse my Linux box on my Mac with the Finder.

From my Windows box:
1. I really have no need to access my Linux or iMac boxes from my Windows box. I basically use my Windows box to run Windows apps that I can't run on my Mac or Linux boxes. I use TS Client on my Linux box to access my Windows box mostly.

I hope that clarifies things rather than make them more confusing.

---

