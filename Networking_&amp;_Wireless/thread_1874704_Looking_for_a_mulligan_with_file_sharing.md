---
title: "Looking for a mulligan with file sharing"
date: 2011-11-03
forum: Networking &amp; Wireless
---

### Post by jabema on 2011-11-03
Okay, here's my dilemma:  I have (1) laptop running Mint Ldxe 11 (1) desktop running Ubuntu 11.04 and (1) desktop running windows XP.  I tried very unsuccessfully to use Samba to share files across all three machines.  After much google-ing and many forum reads, I'm throwing in the towel on the windows machine.  

If I can get the linux laptop and desktop to share files and a printer, I'll be extremely happy.  I have tried to reconfigure samba with the linux computers but I seem to still be a part of the Windows Network, and I am still having permission issues.  I basically have a mess going on here atm.

How can I start this whole process over from a clean slate?  How can I create a new network for use by the two linux machines without any microsoft involvement.  I am the only user on my computers and all I'd like to do is share files between my two linux machines and share a printer.  Also, once I do, would it be better to go with SSH or give samba another shot?   

I appreciate any tips, advice, or suggestions.

---

### Post by WasMeHere on 2011-11-03
Welcome to the Ubuntu Forums, jabema,

I would suggest ssh, because I think it is easier to configure and more secure (against intrusion). Install a ssh server daemon, ***sshd***, on your main computer (I suggest your ubuntu desktop).

Then you can reach it from the other computers with ***ssh*** (login and run programs remotely) and ***sftp*** (file sharing) which is called 'ssh' in the file browser Nautilus. There is also free software for Windows so that you can run ssh and sftp.

But before starting a server, I suggest that you read the following thread, where we try to make a [[COLOR="RoyalBlue"]_wiki or how-to about security for newbies_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1873643")

Have fun finding out :-)
Olle

---

### Post by jabema on 2011-11-03
Thanks Olle.  

When I install ssh will that supersede the samba mess I currently have or do I need to do any prep work before the install?  

I appreciate the thread link as well.  I have zero experience networking, getting my router set up and my wireless printer up and running is about the extent of my home networking resume.

---

### Post by WasMeHere on 2011-11-03
I suggest that you delete your 'samba mess'. It is easy if you remember what you installed. Then reverse it with the command
```
sudo apt-get purge xxx
```
where xxx is what you installed earlier. That might not delete all configuration files, but it is a minor problem. It might be an idea to keep or reinstall ***smbclient***

See the following post to find out what samba programs you have.
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11416478&postcount=4_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11416478&postcount=4")
The server daemon is ***smbd***, which should not be running.

Read the manual **man smbd**

To shut down a user´s smbd process it is recommended that SIGKILL (-9)
NOT be used, except as a last resort, as this may leave the shared
memory area in an inconsistent state. The safe way to terminate an smbd
is to send it a SIGTERM (-15) signal and wait for it to die on its own.

And of course, when the program is removed, it will not be started again.

---

### Post by jabema on 2011-11-03
Good deal, looks like I have my work cut out for me this evening.  Once I finish reading up on ssh and cleaning out samba, I'll give it a go.  I'll post again once I get it working or if I run in to any problems.

Thanks again.

---

### Post by WasMeHere on 2011-11-03
You should always run apt-get with superuser privileges
```
sudo apt-get purge xxx
``` Sorry that I forgot that in my previous post.

---

### Post by jabema on 2011-11-03
Everything went smooth with the install and setup.  Thanks again to Olle

Just trying to get permissions squared away so I can access my external hard drive.  It auto mounts in /media and for some reason when i try to access it I get a permission denied error.  

Aside from that one small hiccup everything else seems to be working.

---

### Post by WasMeHere on 2011-11-03
What file system(s) is it on you external disk? And what is the content of /etc/mtab? It should show how the drive is mounted.

---

### Post by jabema on 2011-11-04
Sorry about the delayed reply.  Long day at work.

Every thing is up and sharing now.  The external was just a permission issue, got it all sorted out.

Thanks again for the pointers, it was a big help.

---

