---
title: "Troubleshooting printing"
date: 2006-04-15
forum: Networking &amp; Wireless
---

### Post by crucian on 2006-04-15
Hi folks,

My printing setup is typical. Ubuntu is print server using Samba to allow my Windows XP clients to print. This has been working reliably for many months. Today none of the clients can print.

Here are my symptoms:

When I attempt to print from the client the Windows printer queue shows the file and for an instant the status is spooling then quickly changes to error.

I see a file in /var/spool/samba. The time stamp corresponds to when I initiated the test print. Though the file size is zero. I assume this means that it can connect to the Samba print spooler.

What I don't see is a file with a similar time stamp in /var/spool/cups or /var/spool/cups/tmp. I assume this to mean that Samba isn't feeding the cups print queue, but I don't know how to troubleshoot any further than this.

One thing that has always bothered me in the past has to do with the initial setup of printing. I configured the Ubuntu server to provide the Windows print driver during a client's initial connection. For some reason it provides two print queues which appear in the printer and faxes folder on the Windows box. One is labeled Auto R200 on Chy. R200 is the printer and Chy is the server. The local port is \\chy\R200. The other queue is R200 on Chy and it's local port is Samba printer port. When all is right in the world and printing is working you can open both printer queues on the Windows client then initiate a print job. You'll see the print job go from the Auto R200 on Chy queue to the R200 on Chy queue before the printer does its thing.

Can anyone provide next step troubleshooting? I've exhausted the information I was able to find on the net. There isn't much material that discusses the flow of the various queues, and what to check. Most of the information is for print problems encountered during initial setup.

All suggestions will be appreciated.

Crucian...

---

