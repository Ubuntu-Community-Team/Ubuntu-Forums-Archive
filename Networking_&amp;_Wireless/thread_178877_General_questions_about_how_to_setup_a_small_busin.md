---
title: "General questions about how to setup a small business network"
date: 2006-05-18
forum: Networking &amp; Wireless
---

### Post by Tauceti38 on 2006-05-18
I apologize in advance for the extremely long post, but I figure that its always easier to help answer questions when the whole situation and all of my assumptions are explained upfront. Most of these questions are about networking in general, not something related to ubuntu. I bolded the actual questions to make it easier to skip all of the background unless you need to read it.

My father has a small business with a network consisting of 10 computers and 2 network cameras. All of the computers run Windows XP Pro and are connected by a simple switch and router. He's begun to notice several problems with the network, mainly just computers being randomly dropped, but has had a few more destructive errors, including files being erased because someone was unable to save a file stored on another computer. Because of these recent problems, he wants to set up a proper network here, including a computer to route the traffic act as a file server. I don't have any real network experience before, so I'm a bit leary of setting it all up myself since it's a fairly expensive and important step. I've done quite a bit of research and figured I finally know enough to come here and ask some questions.

I'm thinking of using Ipcop for its firewall and for network routing capabilities. The documentation seems detailed and the web managment abilities will prove very useful since I'll be able to manage it when I'm at college. I've seen a bit about Smoothwall, but it seems to do basically the same thing. **Are there any major advantages or disadvantages to either Ipcop or Smoothwall? Should I even use something like them?**

My understanding of the way the network will be setup if Ipcop is used is that the computer running Ipcop has 4 nic's, one connected to the cable modem, one to a wireless router, one to a computer for web/email servers, and one that connects to the main network. **It seems to me that the cable connected to the switch which connects to the rest of the network should go into the same port the modem is connected to know. Would that make sense? or is a different sort of switch needed? It seems like the file server plugs into the switch just like any other computer. Does that make sense, or am I missing something there? **

The file server is mainly going to be used to store data from three programs, along with general documents. One of the main programs used was developed specifically for the company using Alpha5, a database program similar to Microsoft Access. The second program actually was developed using Access, and the third is an accounting program. I doubt we'll ever be using much more than 20 gigs of memory. All of the programs will still be installed on and run from the users computers, not the server. **What sort of hardware would you recommend to increase the speed and reliability of the file server? It seems to me that decreasing the read speed would speed up the programs, so fast hard drives and a RAID setup would be more useful than a brand new processor, but what about RAM? Is RAM more important like the hard drive speed, or less important like the processor? Am I even right to assume that hard drive speed is important and the processor speed isn't? Also, what type of RAID setup would work best here? I'm thinking either RAID 1 or RAID 5 seem best, but RAID 0 or RAID 3 might work too.**

The other question about the file server is what sort of Operating system to install. My personal preference is Ubuntu, since that's what I use on my home computer. I really like the package system from debian based systems, and Dapper looks pretty promising to me, but I don't think you'd really need all of that for a file server. If I'm going to use something like ipcop, most other types of servers would have to be hosted on a different machine, since they have to be in a different network. I found a distro called openfiler which seemed to be specifically designed for a file server. Unfortuantly, there are hardly and posts here which even mention it, much less tell how it works and I couldn't find much on the web either, although what I did find looked good. **Is openfiler something which would be useful for such a small network?** It did appear to be possible to manage it over the web, which would be very nice, but not crucial. I doubt we'll ever be using much more than 20 gigs of space. **Would it be better to go with a more general system like Dapper? Or consider something like CentOS?**

Thanks for any advice you might have or any documents you know of that could be of help.

---

### Post by hkgonra on 2006-10-24
I just ran across this post and BOY you do have a lot of questions. ;) 
First off, IPcop for your firewall is a great choice. I use it at home and work and love it. 

As for as a file server I think you would be good using Ubnutu server or openfiler. 

Server specs, a good hardware Raid Controller and LOTS of Ram are your major priorities.

---

