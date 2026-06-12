---
title: "Can't connect two computers via SSH or FTP"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by tbrminsanity on 2009-04-09
I have two Ubuntu computers (my common desktop running 8.10 (64bit), any my work laptop running 8.04).  Before I upgraded my desktop to 8.10 I was able to use gFTP using an SSH protocol to transfer files between the two computers.  Now though I'm getting the following warnings:

With gFTP:
Error: Could not read from socket: Connection reset by peer
Disconnecting from site ############
Waiting 30 Seconds until trying to connect again

With SSH:
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
#################################################.
Please contact your system administrator.
Add correct host key in /home/#######/.ssh/known_hosts to get rid of this message.
Offending key in /home/########/.ssh/known_hosts:1
RSA host key for ############ has changed and you have requested strict checking.
Host key verification failed.

How do I fix this?

---

### Post by superprash2003 on 2009-04-09
are both machines able to ping each other.. have you installed firestarter or ufw recently?

---

### Post by jtniehof on 2009-04-09
Apparently the upgrade on your desktop caused it to regenerate the server keys, so your laptop thinks the server has been replaced by another one, possibly by someone with bad intent. Edit the file .ssh/known_hosts in your home directory on the laptop and remove the first line, then try again.

---

### Post by wylfing on 2009-04-09
Probably nothing evil is happening. Most likely there's just a disconnect between the key that is being sent and the key that is expected. I have had this happen from time to time after doing major upgrades as well (e.g., from one release to the next).

The error message tells you which key it's complaining about. As long as both computers are local, and you don't have any reason to suspect them of being compromised, you can just delete the offending key. Go into ~/.ssh/known_hosts and remove it. The next time you connect, it will ask if you trust the other computer, and you can say Yes.

After that you'll be back in business.

---

### Post by mazato on 2009-04-09
jtniehof is right . regenrate new keys and put them where it belongs.
SSH is not letting gftp connect because of the key errors!
good luck!

---

### Post by PreviousN on 2009-04-09
Okay what you need to do is open a terminal in each computer: 

Applications --> accessories --> terminal
You'll have a prompt like this:
previousn@raptop:~$
type: rm ~/.ssh/known_hosts

And that will remove your ssh key, so you can get a new one. This is a security mechanism associated with ssl. Anyways, when you upgraded your computer it changed the ssh key. So now when you connect to the other computer it is using a different key and your host is refusing the connection based on that.

Wow, that was fast, there were no responses when I first started typing my response. But yes, all of the other posts are right. It has to do with the fact that you upgraded your computer and ssh knows it. So regenerate the ssh key. Best of luck to you, though its not needed. You can do it in less than a minute. Quite an easy fix. :-)

---

### Post by tbrminsanity on 2009-04-09
Worked like a charm.  Thanks all.

---

