---
title: "Samba &amp; File serving for windows clients"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by Skippy_X on 2009-04-15
Hello, all!

First I will apologize in advance for the length of this post. I'll try to be as brief as possible, but given the magnitude of the problem I'm dealing with I think this will be a long post. I also hope you'll be forgiving if my use of terminology is incorrect. I'm a networking neophyte and I'm pretty sure I'll use the wrong term - likely several times.

I work as a PC Tech at a nonprofit organization that does charitable work in the community. To fund this work the organization operates a number of retail outlet selling donated second hand stuff. Over the years the organization noticed that they were getting a significant amount of IT gear donated and that it simply gathered dust in a corner. The employees at those stores didn't have a clue about the equipment and consequently couldn't provide any service to the customers.

As a result of this the organization decided to open a store dedicated to the recycling, refurbishing and sale of IT gear. My function is to test components and refurbish computers. We take in a tremendous amount of material and I use what we get to assemble computers for sale to the public. The proceeds from these sales get turned around to do charitable work in the community. Those items that are too old or are broken beyond repair are broken down to their component pieces and recycled - which is another profit center for the organization.

Essentially, I'm the kid that works in the candy store.

I only have access to donated equipment, so things can get a bit interesting at times. I'm thinking that a year from now I will have been exposed to just about every hardware problem that a computer can develop, but I digress.

Most of the machines we turn out are Windows XP boxes. I do the occasional Mac, and I try to keep a Linux box out on the sales floor at all times (but they don't sell well). We use the existing Win XP license sticker on the box to handle the activation required by MS. When building the systems I install a package of open source applications (Open Office, Firefox, Thunderbird, InfraRecorder, etc.) and some freeware security apps (AVG, Win Defender, A-Squared, CCleaner) so the customer has a working machine set up and running to do most things they'd care to do w/out having to go out and buy apps to accomplish the most common tasks.

We keep everything legal. The company has a reputation for a high standard of integrity and I'm proud to be affiliated with them.

The problem I'm having is that the installation process (both OS & applications) are extremely time consuming. I could easily quadruple production if I had the ability to do unattended OS & app installs. I searched the web and found two apps that should handle that problem nicely for me, [Unattended]("http://unattended.sourceforge.net/installers.php") & [WPKG]("http://wpkg.org/").

I've started w/ WPKG to do the application installs, which are the most time-consuming. My goal is to eventually use Unattended to install WinXP, SP3 and the updates to SP3, along w/ all the apps we handle. If I wind up using Unattended to do the OS installs and WPKG to do the app installs, that's fine by me. It will still save me a tremendous amount of time running up & down a line of PCs clicking "OK", "Install", "Next". That time could be better used testing hardware to get machines ready for install.

I've built an Ubuntu box to use as the file server and I've installed Samba. I can use Nautilus to browse the other systems on the network - all of which are in the workgroup "WORKGROUP". However, I can't get any of the Windows system on the network to "see" my Ubuntu server.

Does anyone know how I can accomplish this?

Thank you in advance for your help, and - again - my apologies for the length of the post.

---

### Post by Iowan on 2009-04-16
The short version...> **Skippy_X said:**
> I've built an Ubuntu box to use as the file server and I've installed Samba. I can use Nautilus to browse the other systems on the network - all of which are in the workgroup "WORKGROUP". However, I can't get any of the Windows system on the network to "see" my Ubuntu server.


I presume the Samba server is in the same workgroup (or it probably wouldn't see the Windows boxes).  Is Ubuntu box firewalled?

---

### Post by Skippy_X on 2009-04-17
> **Iowan said:**
> The short version...


I presume the Samba server is in the same workgroup (or it probably wouldn't see the Windows boxes).  Is Ubuntu box firewalled?

No, it's not.

I've messed about w/ the smb.conf file and tried some variations that I've found online. At this point the windows boxen can see the server but can't access the server.

---

