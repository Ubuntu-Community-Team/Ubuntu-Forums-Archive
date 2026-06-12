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

### Post by crucian on 2006-04-15
Hi Folks,

There's more information:

I forgot to mention that I can print from the Linux Server with no problem. 

I tried to print again this morning then looked in the following logs:

/var/log/samba/log.nmbd
This only stated that Ubuntu is now the local master browser

/var/log/cups/error_log - these entries are from yesterday... nothing for this morning.
E [14/Apr/2006:22:21:27 -0700] get_printer_attrs: resource name '/printers/r200.bat' no good!
E [14/Apr/2006:22:21:28 -0700] get_printer_attrs: resource name '/printers/r200.cmd' no good!
E [14/Apr/2006:22:21:28 -0700] get_printer_attrs: resource name '/printers/r200.exe' no good!
E [14/Apr/2006:22:21:28 -0700] get_printer_attrs: resource name '/printers/r200.com' no good!
E [14/Apr/2006:22:21:28 -0700] get_printer_attrs: resource name '/printers/r200.pif' no good!
E [14/Apr/2006:22:21:28 -0700] get_printer_attrs: resource name '/printers/r200.lnk' no good!

/var/log/samba/log.smbd  - I don't know what bad magic is, but I assume it's not good. I have pages of this.
[2006/04/15 06:38:09, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/cache/samba/printing/R200.tdb): rec_read bad magic 0xd9fee666 at offset=28072
[2006/04/15 06:38:10, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/cache/samba/printing/R200.tdb): rec_read bad magic 0xd9fee666 at offset=28072
[2006/04/15 06:38:42, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/cache/samba/printing/R200.tdb): rec_read bad magic 0xd9fee666 at offset=28072
[2006/04/15 06:38:42, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/cache/samba/printing/R200.tdb): rec_read bad magic 0xd9fee666 at offset=28072
[2006/04/15 06:39:03, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/cache/samba/printing/R200.tdb): rec_free_read bad magic 0x42424242 at offset=28296
[2006/04/15 06:39:03, 0] tdb/tdbutil.c:tdb_log(725)
  tdb(/var/cache/samba/printing/R200.tdb): rec_free_read bad magic 0x42424242 at offset=28296

I'm still checking other sites and trying to creatively google the problem, but so far no love. Any assistance would be much appreciated.

Thanks,

crucian

---

### Post by petermarkab on 2007-07-18
just wondering if you managed to solve this problem as I have a very similar one. Will read up onm CUPS in the meantime as I suspect there's a problem there.

---

