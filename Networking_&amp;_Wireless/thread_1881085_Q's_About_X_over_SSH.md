---
title: "Q's About X over SSH"
date: 2011-11-14
forum: Networking &amp; Wireless
---

### Post by fullmoonguru on 2011-11-14
I would like to be able to login & start a remote desktop session over SSH.  I don't want to take over the existing session, I want a seperate one for the remote session.  The client is gnome 2 & the host is Xfce.  I set up the SSH server & client & was able to start the remote session, but it took over my local desktop.  It seemed to be a mix of the local & remote desktop and the colors & everything changed to what's on the host computer.  I even ended up with the hosts desktop image on the client.  Is there a simple command that will make this more of a captured experience?  I've used noMachine and that worked well, but if it ever quit working because I changed something on one of the computers, I could never seem to get it working again.  I also feel like if I could just do it through the terminal that would be the simple thing.

---

### Post by cybergalvez on 2011-11-14
Not exactly sure what you want to do. if you want the full desktop experience then something like nomachine or x2go is the way to go, but if you only want to run a couple of apps then x over ssh is the simplest way to get run a couple of programs from the command line. if your using Xfce then you don't need any composting and I would personally use x2go, very simple to install and get working.

---

