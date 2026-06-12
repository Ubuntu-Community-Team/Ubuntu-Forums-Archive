---
title: "PXE for Office Network - Pre-Deployment HELP!"
date: 2011-12-31
forum: Networking &amp; Wireless
---

### Post by RockOut on 2011-12-31
I am moving to a new larger office. As such, we need to add 6 computers to support them. So, I want a PXE server or a "Preboot eXecution Environment" which is an environment to boot computers using a network interface independently of data storage devices (like hard disks) or installed operating systems.

Here's my idea:

Why a PXE sounds good to me:
[LIST]
[*]Shared Storage - No need to buy 6 new individual HDDs, which are pricey right now
[*]Only need to maintain ONE install, instead of manage 12
[*]Backup only ONE resource regularly, instead of 12
[*]Everyone's on the same platform
[/LIST]

I found this: [https://help.ubuntu.com/community/PXEInstallServer]("https://help.ubuntu.com/community/PXEInstallServer")

Additional things I want to provide:
[LIST]
[*]Network printing
[*]Network SCANNING - we have Brother MFC printer/scanners
[*]FTP Scanning of documents
[/LIST]


I have never before installed a PXE. This is a bit of a stretch to my skillset, but it doesn't look insurmountable. 

With a bit of help I am more than willing to use them and recreate a guide for others who may find themselves in this spot.

Specific Questions:
Does anyone have suggestions to help me manage this setup? 
What kinds of resources should I have before building the PXE server?
Are there additional resources that I am overlooking?

To be sure, I do have some financial resources to buy new computers/servers/processors/etc that are necessary. So, if there's a particular piece of equipment that helps, let me know. Any/all help is appreciated!

---

### Post by SteveDee on 2012-01-02
> **RockOut said:**
> ...let me know. Any/all help is appreciated!

It sounds like you are looking for a Server/Thin Client set-up, where the clients are light-weight computers and all the processing and data is on the server.

The Thin Clients could be booted from a minimal operating system located on small drives (e.g. HDD, CDROM or whatever) on each client, or you can Pixie boot from a TFTP server over the network.

Having a locally installed Client operating system is quite simple to setup and maintain, as you could use the same Linux "disk image" on all Clients.

I suggest you start by taking a look at the ThinStation site: [http://thinstation.org/](http://thinstation.org/)
I've deployed ThinStation for RDP access to a Windows 2008 server, and it works very well, as long as you can find the right network driver for your Client hardware (I understand the new v2.5beta has much better support). This site should also have info on PXE and TFTP, so would be a good place to start. They also have a very helpful forum.

Also see: [http://ubuntuforums.org/showthread.php?t=1866992&highlight=thin](http://ubuntuforums.org/showthread.php?t=1866992&highlight=thin)

I hope some of this helps.

---

### Post by RockOut on 2012-01-03
I'm looking more into LTSP.  Really, the goal is to stay away from Windows as much as possible -- With Windows, there's no stability or manageable consistency,  given the price of the software. The goal is as we scale larger, for there to be less per-station maintenance.

Right now an LTSP setup looks like the way to go for this project. I'm setting up the first server/thinclient terminal paring now. It's a bit tricky getting the server settings just right though.

---

