---
title: "Connect frontend with backend: “No UPnP backends found”"
date: 2009-11-05
forum: Mythbuntu
---

### Post by koyaanisqatsi on 2009-11-05
Hello, everybody!

I want to set up an all-in-one media pc and tried the live-CD Mythbuntu 9.10. But I could not start the frontend.

When I click on the symbol on the desktop and start with default values, the message “No UPnP backends found” appears. After two more steps (both with default values, too) I get “Cannot login to Database” and the configuration fails.

I really tried a lot and read many sites, but I don’t get it. I’ve been using Linux for years, but have no experience with MythTV or SQL.

The problem should be reproducable really simply – just start the live-CD. Can anyone please help me?

Hoping ;-)

koy

---

### Post by SiHa on 2009-11-05
Hi

MythTV is a client / server or Frontend / Backend system.

Unfortunately a Mythbuntu LiveCD can only be used as a frontend to an existing MythTV network. If you want to try it out properly, the only way is to actually install Mythbuntu, and run through the backend setup. You should be able to accept all defaults and at leat get a system that will let you play your media files.

---

### Post by koyaanisqatsi on 2009-11-06
Yes, that’s it, thanks!

Sorry for asking, it was too simple ](*,)
There was even a message on the desktop, but unfortunately only in English. I just couldn’t imagine that a hard drive installation is necessary.

Bye

koy

---

### Post by Datdarndot on 2010-03-14
Although I am very experienced using Windows and familar with setting up networks, I am completely new to Linux. I recently bought a HomeRun network HDTV tuner, which I understand is ideally suited to using with MythTV. I opted to go with the Mythbuntu LiveCD distro, as it was described as a straightforward introduction to Linux with MythTV built-in and which could variously be run entirely from the CD, installed within Windows, or installed on a dedicated partition. I have tried the first two methods, both of which confront me during installation with questions about frontend, backend, SQL server, passwords, localhost, etc. — all of which is rather mystifying. I'm unclear whether these refer to the HomeRun device itself, to the PC on which I am installing MythBuntu, the PC I intend to use as a server to store video files — or something else entirely. Many posts I read suggest the necessary password can be found on the Mythbuntu partition in the MythTV folder. This seems perverse, as I have not yet completed installing Ubuntu, much less have I configured MythTV. In any case, no matter what I guessed to be the right answers, the frontend-backend communication test failed.
 
A previous post suggests the frontend-backend issues are more clearly addressed only if one opts to actually install Mythbuntu to a dedicated partition. I decided to proceed down this path, as I have deleted all files from the NTFS partition which is known to Windows as Logical Drive D, and I am willing to dedicate it to Mythbuntu. But instead of allowing me to specify where to install Mythbuntu, the installer looked for a physical drive which did not already contain an OS. It decided upon my 1T external eSATA drive, which is not what I had in mind. Leery of where this might lead, I elected to abort the installation.
 
Nowhere have I managed to find a plain-English step-by-step explanation of how to configure the frontend-backend step of the installation process, nor intructions on how to insure I have complete control over where the Mythbuntu OS will be installed. Can anyone help?

---

