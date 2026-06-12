---
title: "Cups: client-error-forbidden"
date: 2013-04-22
forum: Networking &amp; Wireless
---

### Post by unbekannt on 2013-04-22
Hello,

I am new to this forum, so sorry if I put this into the wrong thread.

At my new working place a print server is set up. But when trying to access it with "system-config-printer" and I enter the print server name I get the following error message:
>CUPS server error
>There was an error during the CUPS operation: 'client-error-forbidden'.

The print server is within a local network and I am able to ping it. Has anybody an idea what I am doing wrong?

My system is:
 E325 Lenovo
Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-40-generic
GNOME 3.4.2
(I updated this morning)

Thanks,
Thomas

---

### Post by tgalati4 on 2013-04-22
Open the print server's webpage:  [http://yourprintserver:631](http://yourprintserver:631)

Look for your printer and its status.  You won't be able to perform any admin funtions from the web page (without allowing remote admin).

If this is a Windows shared printer, then there may be another issue.  On your machine, look in /var/log/cups for errors.

Under the "Help" tab of system-config-printer there is a troubleshooting guide, did you go through it?

You also mentioned that you performed an update.  Did you do a reboot afterward?  Sometimes CUPS needs to be restarted with a clean boot after kernel or other updates.

---

### Post by unbekannt on 2013-04-23
Hello tgalati4,

thanks for your answer.

> **tgalati4 said:**
> Open the print server's webpage:  [http://yourprintserver:631](http://yourprintserver:631)

Look for your printer and its status.  You won't be able to perform any admin funtions from the web page (without allowing remote admin).

I did that and I get 403 Forbidden error. I should have said that I am not the admin of the print server.

> 
If this is a Windows shared printer, then there may be another issue.  On your machine, look in /var/log/cups for errors.

I have not found an error log.



> 
Under the "Help" tab of system-config-printer there is a troubleshooting guide, did you go through it?

I did it now: First I get these error messages in the shell:
```
Traceback:
File "/usr/share/system-config-printer/troubleshoot/__init__.py", line 314, in _collect_answer
    answer = question.collect_answer ()
File "/usr/share/system-config-printer/troubleshoot/Welcome.py", line 64, in collect_answer
    '_authenticated_connection': self.op.run () }
File "/usr/share/system-config-printer/timedops.py", line 208, in run
    return self.thread.collect_result ()
File "/usr/share/system-config-printer/timedops.py", line 161, in collect_result
    raise self.exception
RuntimeError: failed to connect to server

```
After a while the trouble shooter returns this result:
```
The Cups print spooler does not appear to be running. To correct this, choose System->Administration->Services from the main menue and look for the 'cups' service 

```
I looked for this menue but I was not able to find it.


> 
You also mentioned that you performed an update.  Did you do a reboot afterward?  Sometimes CUPS needs to be restarted with a clean boot after kernel or other updates.
I did reboot after the update. But as my first atempt to print was after the update I am not able to say if the update changed anything.


Another thing which I have overseen before is that if I start ```
system-config-printer
``` from the command line I get the following warning:
```
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-TPSLek/pkcs11: No such file or directory
```


Cheers,
Thomas

---

### Post by bobblex on 2013-04-23
Do you have a firewall like UFW running on you Linux system?  

I ran into this problem earlier this week when I was trying to set up access to a printer attached to an MS W7 system. The MS W7 serves as the print server.  It turned out that I needed to check my Samba ports in UFW. When I got those configured correctly, the error message went away and printing operations were enabled.

---

### Post by unbekannt on 2013-04-23
> **bobblex said:**
> Do you have a firewall like UFW running on you Linux system?  

I ran into this problem earlier this week when I was trying to set up access to a printer attached to an MS W7 system. The MS W7 serves as the print server.  It turned out that I needed to check my Samba ports in UFW. When I got those configured correctly, the error message went away and printing operations were enabled.

I personally have not installed one. So if Lubuntu does not come with one installed by default there should be no firewall. 

UFW is installed but it seems to be inactive:
```

sudo ufw status
Status: inactive
```

Is there a different place where I could check if a firewall is active?

---

### Post by bobblex on 2013-04-23
It looks like you may have a different problem. 

The following link, although not specific for Ubuntu, might give you some ideas.

[https://wiki.archlinux.org/index.php/CUPS#CUPS_permission_errors](https://wiki.archlinux.org/index.php/CUPS#CUPS_permission_errors)

---

### Post by tgalati4 on 2013-04-23
Is cups running on your machine?

```
ps -ef | grep cups
```

It should look like:

tgalati4@Mint14-Extensa ~ $ ps -ef | grep cups
root       748     1  0 Apr19 ?        00:00:00 /usr/sbin/cupsd -F
tgalati4 17654 11049  0 18:47 pts/0    00:00:00 grep --colour=auto cups

If cups is not running then start it:

```
sudo service cups start
```

Open [http://localhost:631](http://localhost:631)

---

### Post by unbekannt on 2013-04-23
I have done it and cups is running:
```
ps -ef | grep cups
root      3882     1  0 18:46 ?        00:00:00 /usr/sbin/cupsd -F
thomas    4357  2275  0 19:30 pts/1    00:00:00 grep --color=auto cups

```

I can also do:
```
http://localhost:631/


```

---

### Post by tgalati4 on 2013-04-25
If you can see CUPS through [http://localhost:631](http://localhost:631), try setting up a printer on your machine.  The key is getting the correct URL to put in the dialog box.  Your IT department should be able to help you with that.  Sometimes you can search the network and the printer will automatically show up--(like on a Mac).  Other times it won't and you will have to explicitly put in the printer server details.  It's possible that the printer server has an Access Conrol List (ACL) that only accepts print requests from a list of IP addresses.  Since you are the new guy, they are just messing with you.

---

### Post by bobblex on 2013-05-18
unbekannt, 

Did you ever get a solution to your problem of adding and activating network printers?

I was running into the same issue today after making some system changes.  After searching for a while I found that smbclient hadn't been installed after my updates and changes.  Once I got smbclient installed through Synaptic all began working again.

---

