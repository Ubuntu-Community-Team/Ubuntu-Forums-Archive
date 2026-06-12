---
title: "Network file sharing with windows half works"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by darkwalt on 2009-09-06
Ok, let me start off by saying that i've been working on this problem for about three days straight now, and i've been working off of the forums, so I have read a bunch of HOWTO's and other threads.

Now, i've been wanting to share files between my ubuntu laptop and my win 7 pc with several external HD's attached via USB.  I've gone about installing Samba on the laptop, installing Bonjour on the desktop, configuring the laptop with WINS information, and a few other things from other various threads.  

The half progress i've made is that now my PC can see and has full permissions to my /home folder, which is the way I want it.  On the network tab in Nautilus, it can see my PC, but every time I double click on it, I get "**Unable to mount location** Failed to retrieve share list from server".  

Summary: Windows can access shared resources from ubuntu, ubuntu can not access shared resources from Windows.   

Any clues on what could be causing the hold up?

---

### Post by LinuxRules1 on 2009-09-06
It seems that the file sharing service on your win 7 system isn't running. I have got that error before trying to connect to my server and every time it was because the service wasn't running.

Hope this helps.

---

### Post by darkwalt on 2009-09-06
Should have specified on that issue.  I can connect to my win 7 pc from other windows pc using the "WORKGROUP" in networks.

---

### Post by LinuxRules1 on 2009-09-07
Try connecting to the win 7 system by its ip address. on your ubuntu system go to the file manager and in the location bar type this in.

```

smb://(ip address of system)

```

If that doesn't work then the firewall on the win 7 system is probably blocking it out.

---

### Post by mapes12 on 2009-09-07
I only have experience of XP and this might be stating the obvious:

1. On the windoze PC enable file and print sharing - Control Panel
2. For the folder you want to share right click and enable sharing
3. The user account who owns the folder you want to share must have full Admin rights and not be a Limited account.

I took me 3 days to work out point 3. I had the same unable to mount response until I gave the windoze account full Admin rights. Security issue = yes but that's a MS problem.

---

### Post by darkwalt on 2009-09-07
[img]http://img.photobucket.com/albums/v441/llDarkll/neterror.png[/img]

Also, I completely turned off my firewall, and still had no joy. Any more ideas?

---

### Post by LinuxRules1 on 2009-09-09
Are you using a program to share the files or are you using the windows utilities? I tried to connect to a win7 system with my ubuntu desktop and I successfully connected to it.

---

### Post by darkwalt on 2009-09-09
I am using a program called tversity to share media files with my xbox, and I am using windows utils to make backups to a shared network drive connected to the desktop pc.  Two win7 laptops are making backups to my shared drive.  Nearly all devices on my network have static IP's except for one laptop and my xbox 360.

---

### Post by darkwalt on 2009-09-10
*bump*
Just wanted to keep relevant.

---

### Post by LinuxRules1 on 2009-09-10
Try using the windows utils to share the files instead of tversity.

---

### Post by darkwalt on 2009-09-10
I am.  I right clicked on the file and chose share with everyone.  Could this have anything to do with me running 9.10?

---

### Post by LinuxRules1 on 2009-09-13
It is ubuntu 9.10. i tried to connect to my win 7 system with ubuntu 9.10 and i got the same error

---

### Post by darkwalt on 2009-09-13
FML.  Guess this goes under solved by crappy reason.

So, summary here.

Ubuntu 9.10 cannot connect to a windows share, but windows 7 can connect to a ubuntu share if ubuntu is configured in the same workgroup, which is by default, WORKGROUP.

---

### Post by zman58 on 2009-09-13
> **darkwalt said:**
> [img]http://img.photobucket.com/albums/v441/llDarkll/neterror.png[/img]

Also, I completely turned off my firewall, and still had no joy. Any more ideas?

Set up the Windows box with a simple guest fileshare that does not require a password--as a test. Then on the Ubuntu box use Places -> Connect To Server
Select "Windows Share" from the pull-down combo-box. Provide the server name or ip address and provide the sharename. It should connect.

Then add specific user to the Windows share and try connecting from Ubuntu the same way as above providing the necessary user credentials. It should work. The user credentials are credentials for the user account on the Windows system (user, password).

---

### Post by darkwalt on 2009-09-14
@zman58 

Def tried that.  Not working out at all.  I think that we have a bug in 9.10 that is preventing it from connecting.

---

### Post by Anubis on 2009-09-30
This is definitely a 9.10 issue as this does not occur with 9.04. I have 2 Mint 9.04 boxes, a Windows 7 box, and my two 9.10 boxes. Both 9.10 boxes are sharing via smb. Findsmb shows all PCs sharing on the same network obviously, but none are able to see anything in their respective file browsers.:confused:

---

### Post by darkwalt on 2009-10-10
K, as of kernel 2.6.31-13 samba sharing is still an issue.  Does anybody know if this is a confirmed bug in the bug lists?

[img]http://img.photobucket.com/albums/v441/llDarkll/stillbroken.png[/img]

EDIT: Look at those super-spiffy system tray icons!  :P

---

