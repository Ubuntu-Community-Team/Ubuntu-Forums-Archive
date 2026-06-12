---
title: "Samba has to be re-installed everytime I want to stream to my Xbox"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by Fenris_rising on 2009-05-29
Hi all

I have a slight problem which has only started in the last 2 weeks. I have been running Ubuntu for 12 months now and as part of my network my Xbox original has been hardwired to the network, since the beginning, so that I can stream my music and media to it.

This has, till now, worked flawlessly. Last month I updated to 8.10 with out issue BTW.

Symptoms are; From the xbox the error message 'could not find network'

On the PC if I try and share folders it says smbd may not be active.

The only thing I have been able to do is uninstall samba and reinstall to get the sharing options to work. Then the xbox can find the shares and it's all systems go. That is until the next time.

My smb.conf file appears intact so what else do I need to address please.

regards

Fenris (1st anniversary of Linux :) )

---

### Post by superprash2003 on 2009-05-30
when you have trouble , in your terminal type smbtree and post output

---

### Post by Fenris_rising on 2009-05-30
Hi there, thanks for looking. Here's what I get at the moment. The Xbox is on but can't be pinged and it can't find the network as before. The Amanda-PC is my wifes laptop which normally is an 'enter password' connection so I'm not surprised it failed. But no Xbox entry.

```

fenris@Odhinn:~$ smbtree
Password: 
TOTSVILLE
	\\AMANDA-PC      		
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine AMANDA-PC.  Error was NT_STATUS_ACCESS_DENIED
```

Here is the output when I have rejigged samba. Which is now communicating with the Xbox. I can ping the Xbox and the xbox now has access to the shared files of the PC.

```
fenris@Odhinn:~$ smbtree
Password: 
TOTSVILLE
	\\ODHINN         		
		\\ODHINN\my music       	
		\\ODHINN\electronics and mags	
		\\ODHINN\films          	
		\\ODHINN\windows share  	
		\\ODHINN\IPC$           	IPC Service (Odhinn server (Samba, Ubuntu))
		\\ODHINN\print$         	Printer Drivers
	\\AMANDA-PC      		
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine AMANDA-PC.  Error was NT_STATUS_ACCESS_DENIED
```

Now the only thing I do wonder is if the smb.conf file is corrupt? It doesn't get removed when I uninstall samba to fix the main problem.

regards

Fenris

---

### Post by dmizer on 2009-05-30
When you have problems, try this:
```
sudo /etc/init.d/samba restart
```
See if that corrects your problem, or gives you errors.

---

### Post by Fenris_rising on 2009-05-30
Ah thanks for that, I have copy/pasted that to my list of 'tools'.
I will try on the next reboot as this seems to reset the system to 'cockup' mode :D

regards

Fenris

---

### Post by MartyBuntu on 2009-05-30
This is a known bug, where Samba services are not started on boot.

I have seen a workaround script. I can't for the life of me remember where I saw it, but if I remember, I'll post it.

I have the exact same problem, but I just restart Samba:

**sudo /etc/init.d/samba restart**

---

### Post by dmizer on 2009-05-30
If this is a known bug, please post a linj to the bug report.

---

### Post by MartyBuntu on 2009-05-30
Here is one bug report with the same problem I and the OP seem to be having:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/125687](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/125687)

---

### Post by Fenris_rising on 2009-05-30
interesting! That bug report does seem to be what I am having trouble with. Now my Ubuntu 8.04 has worked flawlessly with the Xbox link and so did 8.10 update up until 2 weeks after the upgrade.

A thing to notice, at least for me, Is that the sleep script used by some of you to fix the problem is not a good fix for my setup. By this I mean that if you are delaying the startup of samba so that all network points are up and present when it then runs.

My Xbox may not be switched on anyway as I may not be using it until much later in the day so the startup will have happened anyway and already seen the absents of the Xbox which then won't pickup.

Prior to this I have been able to turn the Xbox on whenever and it picks up and runs no problem. Now the network connection is recognised when the Xbox is turned on but won't function until a play with samba (I will be using the samba restart code now of course if needs be)

The only other change to my setup that may be of relevance is the change of router. I have gone from a belkin with the IP address of
```

192.168.**2**.1
```

To a netgear with the IP address of

```
192.168.**0**.1  
```

my Xbox **had** the static IP

```
192.168.**0**.10
```

The PC NIC to which it was attached was

```
192.168.**0**.1
```

So to avoid a DHCP clash of IP's of connected PC's and laptops which will get an IP based on the;

```
192.168.0.1
```

format I changed the static IP's of the Xbox and the PC's NIC to a
```

192.168.**1**.1
```

format.

Would anything have gone awry with this fundamental change in IP addressing?

regards

Fenris

---

### Post by Fenris_rising on 2009-06-01
Hi Guys

Well I had to use the

```
sudo /etc/init.d/samba restart
```

As 

```
smbtree
```

Showed nothing after the reboot. All that happened after entering my password was the command prompt came backup.

Unfortunately after using the restart code I still have nothing so I guess I have to uninstall samba to re-install it to get it working for the duration of the session. Here is the result of using the restart code, Hopefully it contains a clue that greater minds than mine can use to help.

EDIT: Scratch that, I must have been to hot off the mark, I just tried the smbtree again and samba is up. So in light of that what can be done to get it to automate itself again?

```
fenris@Odhinn:~$ sudo /etc/init.d/samba restart
[sudo] password for fenris: 
 * Stopping Samba daemons    start-stop-daemon: warning: failed to kill 5084: No such process
                                                                         [ OK ]
 * Starting Samba daemons                                                [ OK ] 
```

regards

Fenris

---

### Post by dmizer on 2009-06-01
Make sure that the Samba service (I think it's called file sharing) is set to start automatically under: system > administration > services

---

### Post by Fenris_rising on 2009-06-02
Initially couldn't find the services :confused: But it turned out they were not turned on in the menu list options. I know that has nothing to do with whether it's running though. So got it up on the menu and file sharing was ticked for action.

I don't know if the following is of use but heres the properties window with the run levels and settings for file sharing. Is anything awry here?

Thanks for your interest thus far :)

regards

Fenris

---

### Post by Fenris_rising on 2009-06-03
Hi all

I now presume that the 'start delay' script as posted in the bug report would actually automate the start of the samba system? If I understand better now it doesn't matter whether my Xbox is on or off when samba starts.

Because Samba is primarily to do with making shared files available on the network from the PC. So any one who gets onto the network has instant access to the shares.

regards

Fenris

---

### Post by dmizer on 2009-06-03
You can try this:

Edit /etc/rc.local
```
gksudo gedit /etc/rc.local
```
and add the mount -a command to the file (above exit 0) so it looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

mount -a
exit 0
```

Save the file, and reboot. See if things work correctly then.

---

