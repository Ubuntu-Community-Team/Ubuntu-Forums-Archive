---
title: "Intermittent Connectivity with Windows 7 PC's"
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by Bubbasheeko on 2011-02-17
We are sharing a networked accounting file through 8 computers.  We recently upgraded and are temporarily running the programs side by side on the Windows 7 and XP PC's.  That gives us 16 connections to our XP Pro machine and with it's limit on 10, it now became something we could not use.  I then installed Linux, got all the shares set up with Samba and all the PC's on the network can see them and have them mapped.

The problem?  Apparent intermittent connectivity issues.  This seems incorrect as ifconfig shows no dropped connections.  The mapped drives stay connected, but the errors from the network application running on the Windows systems indicate a dropped connection.  Access to the data file was terminated.  Then all the staff need to close out of the applications in order to log back in.  So I obviously need to find a solution to this quickly.

4 systems running Windows 7 and 4 systems running Windows XP pro.  The system hosting the files is dual booted with Windows XP Pro and Ubuntu 10.10.  No problems with network when in XP - except when we hit our connection limit.  This only happens when the PC hosting the shared files is running Ubuntu.

I should add that this issue has not replicated on any of the XP machines.

I have tried setting up access to the file with both TCP/IP and NetBIOS on the Windows PC's.  All updates have been completed in Ubuntu 10.10.

Any suggestions??

---

### Post by Bubbasheeko on 2011-02-17
Just in case it is Windows not keeping the persistent connection I did this on the windows 7 pcs:

> net config server /autodisconnect:-1

This would prevent the connection from timing out - in case that was it.  Low and behold, as I was updating this post, one of the system users told me that the connection was terminated.

I also installed firestarter - and did not start the firewall.  I just wanted to ensure that the connections remained persistent.

Any other thoughts out there in Ubuntu world?

---

