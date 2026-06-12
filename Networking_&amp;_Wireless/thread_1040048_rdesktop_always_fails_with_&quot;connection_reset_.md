---
title: "rdesktop always fails with &quot;connection reset by peer&quot;"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by LinuxRocks713 on 2009-01-15
> 
$ rdesktop xx.xx.xx.xx:5000 -r clipboard:CLIPBOARD -r sound:local
ERROR: send: Connection reset by peer
ERROR: Connection closed


Is there a way to ignore this and allow rdesktop to continue?

---

### Post by movingover on 2009-01-15
An explanation from the [microsoft website]("http://www.microsoft.com/technet/prodtechnol/windows2000serv/reskit/w2000Msgs/5055.mspx?mfr=true") might help:
> This normally results from a loss of the connection on the remote socket due to a timeout or a restart... This reset could be generated locally by the network system when it detects a connection failure, or it might be received from the remote host.

One of the most common problems is that windows remote desktop only allows one connection at a time to any given machine if it's not a windows server variant. That error probably means you at least got through to the machine, but can no longer connect. Try making sure you can ping the machine?

At any rate, that's a fatal error, so it's not something that can be "ignored." If you still have problems using remote desktop, maybe [VNC]("http://www.tightvnc.com/") will work better.

Hope this helps!

---

### Post by pdtpatrick on 2009-01-15
is remote desktop on your windows machine set to allow connection? also make sure port 3389 (if i remember right, thats RDC protocol) is open. 

Check your windows firewall.

---

### Post by 2phar on 2010-02-24
Hi.. I was having the same problem:
rdesktop dies with RECV Connection reset by peer  just after the remote desktop window opens momentarily.

Then I discovered it worked when running under root, and you can see in an strace that there is a permission denied when trying to access the .rdesktop hidden dir within your home directory, when not running as root.

When rdesktop fails to access the RDP license file in your .rdesktop dir, the remote Windows terminal server terminates the connection because of an invalid license (hence the reset by peer).

If this is the cause in your case, try the following in the terminal to fix it, and then retry rdesktop:

sudo chown -R $USER.$USER ~/.rdesktop

---

### Post by thefish123 on 2010-05-09
> **LinuxRocks713 said:**
> Is there a way to ignore this and allow rdesktop to continue?Is the server you are connecting to configured to use SSL security with RDP?  I do not think that rdesktop can connect to an SSL encrypted RDP.

There may be a way to establish the SSL connection with stunnel and then use rdesktop.  I am not 100% clear on how to use stunnel...

The Fish

---

### Post by landtuna on 2010-06-17
I was able to fix this problem by going to the Remote tab in System Properties on my Win7 Pro machine. Select "Allow connections from computers running any version of Remote Desktop (less secure)".

---

### Post by _UsUrPeR_ on 2011-06-09
I am using Windows 2008 R2 with RDS CALS (Remote Desktop Services Client Access Licenses), and was having the same problem. I was able to fix it by changing the Security Layer accepted by Windows 2008.

Here's how to do that:


Open your server manager. That can be done as follows:

Start > Administrative Tools > Server Manager

Once in there, go to:

Roles > Remote Destkop Services > RD Session Host Configuration: <YOUR SERVER NAME>

In there, under the connections window, find your connection name. I am working in a testing environment, and only have one connection, called "RDS".

Right-click on the connection name (RDS for me) and click properties.

In the properties window, click on the "General" tab. In the general tab, under the Security section, inside the "Security Layer" drop-down menu, change the selection from "SSL (TLS 1.0)" to "RDP Security Layer".

After doing that, I was able to connect to the server.

---

