---
title: "How-To on CUPS+SAMBA (network printing) on Ubuntu server"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by mathewfer on 2009-07-18
Hi All,

Can someone give a link to a good "How-To" for network printer setup on Ubuntu server (6.06 LTS)?

I have setup the CUPS & SAMBA. So far, I can get the CUPS admin page on a remote XP PC & send a TEST page to printer (on Ubuntu server) successfully but printing from a remote XP PC is NOT working.

I get the below error in SAMBA log.

[2009/07/18 12:57:43, 1] rpc_client/cli_pipe.c:cli_rpc_pipe_open(2197)
  cli_rpc_pipe_open: cli_nt_create failed on pipe \spoolss to machine XP-PC.  Error was NT_STATUS_ACCESS_DENIED


Even if someone can reply with a working "cupsd.conf" & "smb.conf" files for network printing, I will be able to use that for testing in my box.

Thanks in advance for your replies.

Mathew

---

### Post by wojox on 2009-07-18
Did you go into control panel > printers > add netwrk printer
Browse for server computer. Should see list of printers.
Install printer. 
Test.

---

### Post by mathewfer on 2009-07-18
Hi,

Yes, I did in Windows XP PCs & it looks all good on windows side but printer does not print any pages. No errors on Windows XP PCs.

If you have your setup working, I would like to see the config files, if you like to share

Mathew

---

