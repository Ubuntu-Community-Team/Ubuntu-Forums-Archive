---
title: "SCP never stops, generates gigabytes of garbage"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by gnemo on 2009-09-11
Operating system: Ubuntu Jaunty 9.04, from Alternate CD (i386)
Problem: when I use scp to copy a 21 GB folder across the network to the PC running Jaunty, the copy process never ends. Worse, copying that 21 GB folder generated a 309 GB folder on the destination machine before I interrupted the copy! Nautilus shows 309 GB folder size, but when I open the folder, there is no visible data inside it.

Note: copy was done as root because some sub-folders were owned by root. My network connection to the external world was DISCONNECTED while the scp process ran, so running scp as root did not pose a security risk.

Repeatability: Every time. I tried it a second time, and this time the scp process generated 290 GB of invisible data before I killed the process.

Commands executed:
1) Log into Ubuntu Jaunty PC, let's pretend its IP is 192.168.0.5
2) su to root (I set a root password)
3) Try to copy 21 GB /home/gnemo folder from 192.168.0.2 (source PC running Kubuntu 8.04) to Jaunty PC using the command:
 scp -prv root@192.168.0.2:/home/gnemo ./gnemo_full_copy_sep_9_2009

4) Result: scp never terminates, and ./gnemo_full_copy_sep_9_2009 keeps growing endlessly until I manually kill the scp process.

On-screen messages: "kcore" appears periodically, along with an endlessly growing reported copy size. Other messages as shown below ("kcore" lines formatted red for emphasis):
```

gnemo@backupbox:~$ su
Password: 
root@backupbox:/home/gnemo# scp -prv root@192.168.0.2:/home/gnemo ./gnemo_full_copy_sep_9_2009
<BIG SNIP>
.
.
.
.
Sink: T1252438770 0 1252438770 0
Sending file modes: C0200 0 sysrq-trigger
Sink: C0200 0 sysrq-trigger
sysrq-trigger                                 100%    0     0.0KB/s   00:00    
Sink: T1252438770 0 1252438770 0
Sending file modes: C0400 0 vmcore
Sink: C0400 0 vmcore
vmcore                                        100%    0     0.0KB/s   00:00    
Sink: T1252438770 0 1252438770 0
Sending file modes: C0400 281474975666176 kcore
Sink: C0400 281474975666176 kcore
[COLOR="Red"]kcore                                           0%   23GB  11.3MB/s[/COLOR] 6623:46:10 debug1: need rekeying
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.0.2' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: set_newkeys: rekeying
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: set_newkeys: rekeying
debug1: SSH2_MSG_NEWKEYS received
[COLOR="Red"]kcore                                           0%   87GB  11.2MB/s [/COLOR]6648:20:57 debug1: need rekeying
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.0.2' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: set_newkeys: rekeying
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: set_newkeys: rekeying
debug1: SSH2_MSG_NEWKEYS received
[COLOR="Red"]kcore                                           0%  150GB  11.2MB/s[/COLOR] 6634:27:31 debug1: need rekeying
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.0.2' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: set_newkeys: rekeying
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: set_newkeys: rekeying
debug1: SSH2_MSG_NEWKEYS received
[COLOR="Red"]kcore                                           0%  214GB  11.3MB/s [/COLOR]6625:09:49 debug1: SSH2_MSG_KEXINIT received
debug1: SSH2_MSG_KEXINIT sent
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.0.2' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: set_newkeys: rekeying
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: set_newkeys: rekeying
debug1: SSH2_MSG_NEWKEYS received
[COLOR="Red"]kcore                                           0%  278GB  11.3MB/s [/COLOR]6609:08:40 debug1: SSH2_MSG_KEXINIT received
debug1: SSH2_MSG_KEXINIT sent
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.0.2' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: set_newkeys: rekeying
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: set_newkeys: rekeying
debug1: SSH2_MSG_NEWKEYS received
[COLOR="Red"]kcore                                           0%  309GB  10.7MB/s [/COLOR]6974:59:44 ^Cdebug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
debug1: Killed by signal 2.
root@backupbox:/home/gnemo# 

```
This Jaunty box was intended to be my data backup and media server, and it is currently useless for the task if I can't use ssh/scp to transfer my files to it.

Interestingly, I had the same problem (scp would never end, and the copied data size kept growing indefinitely) on a Mepis Linux box several years ago. That makes me suspect that ssh/scp in Debian-based distributions has a long-standing bug.

-Gnemo

---

### Post by lloyd_b on 2009-09-11
I'm not that familiar with scp, but two facts make me suspicious:
1.  scp *will* follow symlinks
2.  The file /proc/kcore is constantly changing while the system is running.

So if that "kcore" is a link to /proc/kcore, scp may be constantly aborting and restarting the transmission because the file is changing...

Lloyd B.

---

### Post by gnemo on 2009-09-11
Thank you for your reply, and the thought you put into it.

I ran "kfind" and searched for anything named kcore within the /home/gnemo folder and subfolders. Kfind found nothing.

Then I Googled for a command-line way to search specifically for symlinks, and found this:
[http://www.linuxquestions.org/questions/linux-software-2/how-to-find-symlink-565475/](http://www.linuxquestions.org/questions/linux-software-2/how-to-find-symlink-565475/)

I used the shell script suggested in post #6 of that thread to hunt for all symlinks inside /home/gnemo.  The script found one single symlink, pointing to the Internet Explorer 6 binary (I installed IEs4linux a while ago). Nothing named kcore was found. 

Suggestions, anyone?

-Gnemo

---

### Post by lloyd_b on 2009-09-11
Okay, now I'm confused.  From your original message:> Sink: T1252438770 0 1252438770 0
Sending file modes: C0200 0 sysrq-trigger
Sink: C0200 0 sysrq-trigger
sysrq-trigger                                 100%    0     0.0KB/s   00:00    
Sink: T1252438770 0 1252438770 0
Sending file modes: C0400 0 vmcore
Sink: C0400 0 vmcore
vmcore                                        100%    0     0.0KB/s   00:00    
Sink: T1252438770 0 1252438770 0
Sending file modes: C0400 281474975666176 kcore
Sink: C0400 281474975666176 kcorelooks like it's sending the files "sysreq-trigger", "vmcore", and then "kcore".  All of these files are located in the /proc filesystem (and all are files that you should *not* be backing up, as they are dynamically generated by the system).

Please double check exactly what it is you're trying to send (the contents of that /home/gnemo folder, if I'm understanding that command line correctly).

Lloyd B.

---

### Post by gnemo on 2009-09-12
> **lloyd_b said:**
> looks like it's sending the files "sysreq-trigger", "vmcore", and then "kcore". 
<snip>
Please double check exactly what it is you're trying to send (the contents of that /home/gnemo folder, if I'm understanding that command line correctly).

Lloyd B.
Yes, /home/gnemo is what is being sent (from the Hardy 8.04 box) to be received by the Jaunty 9.04 box.

That folder is a typical user directory, with the usual photos, documents, email, and so on. I have already verified that there is only one symlink inside the /home/gnemo folder and its sub-folders, that one symlink pointing to the Internet Explorer 6 binary. Nothing pointing to /proc.

I think your observation that "sysreq-trigger", "vmcore", and "kcore" are files related to /proc might prove very useful. However, there seems to be no logical reason WHY the secure copy (scp) command is copying files from the /proc tree.

I believe you understood the scp command correctly. However, if you wish, there is a short writeup on the scp command here:
[http://kb.iu.edu/data/agye.html](http://kb.iu.edu/data/agye.html)

I'm using the "-prv" options to [1](p)reserve modification and access times of all copied files, [2](r)ecursively copy sub-folders and files, and [3]produce (v)erbose output.

I've used this command (scp -prv user@remotehost:/path/to/remote/file localfilename) hundreds of times in the past to make backups over the network. I have encountered the never-ending scp at least once before, though, in an old version of Mepis linux IIRC.

-Gnemo

---

### Post by Yannick Le Saint kyncani on 2009-09-12
Ssh will indeed follow symlinks.

You should use "rsync -avxH -e ssh" instead, which will preserve symlinks (and other things as well, man rsync for details).

---

### Post by gnemo on 2009-09-12
> **Yannick Le Saint kyncani said:**
> Ssh will indeed follow symlinks.

You should use "rsync -avxH -e ssh" instead, which will preserve symlinks (and other things as well, man rsync for details).

Thanks for the alternative (rsync); I'll try that.

However: there is as yet no evidence that the original problem originates from a symlink in the folder being copied.

If you look at the original post, I was copying a 21 GB folder; the first appearance of "kcore" in the scp output showed 23 GB had already been copied. It seems likely that the scp process had in fact already copied the entire contents of my 21 GB folder before it went nuts and then started copying random garbage data, possibly from /proc.

After that first occurence of "kcore", if you look at the output I posted, no other file names appear - all you see is ssh debug messages, and the periodic re-appearance of "kcore", along with an ever-increasing copied data size.

-Gnemo

---

### Post by Yannick Le Saint kyncani on 2009-09-12
> **gnemo said:**
> However: there is as yet no evidence that the original problem originates from a symlink in the folder being copied.

Well, where is kcore coming from then ?

"sudo find $HOME -type l" will show you symbolic links in your $HOME.

---

### Post by gnemo on 2009-09-12
> **Yannick Le Saint kyncani said:**
> Well, where is kcore coming from then ?
That, precisely, is the mystery. :)
> **Yannick Le Saint kyncani said:**
> 
"sudo find $HOME -type l" will show you symbolic links in your $HOME.
I already ran a check for symlinks earlier (mentioned in a previous post on this thread), but no matter, I went ahead and ran the command you suggested, on the source machine, the one I'm trying to back up to the new Jaunty box. In other words, I checked the $HOME folder that is causing the problems when I use scp to copy it to the new machine.

The results of the "find" command are attached below (unedited except for replacing my real username with "gnemo" and a couple of bittorrent file names with generic names). As you can see, there is no /proc and no kcore anywhere to be seen:
```

gnemo@Blacktower64:~$ sudo find $HOME -type l
/home/gnemo/.DCOPserver_Blacktower64_:0
/home/gnemo/.wine/dosdevices/g::
/home/gnemo/.wine/dosdevices/c:
/home/gnemo/.wine/dosdevices/h:
/home/gnemo/.wine/dosdevices/e::
/home/gnemo/.wine/dosdevices/f::
/home/gnemo/.wine/dosdevices/d::
/home/gnemo/.wine/dosdevices/z:
/home/gnemo/.wine/dosdevices/h::
/home/gnemo/.wine/drive_c/windows/profiles/gnemo/My Music
/home/gnemo/.wine/drive_c/windows/profiles/gnemo/Desktop
/home/gnemo/.wine/drive_c/windows/profiles/gnemo/My Videos
/home/gnemo/.wine/drive_c/windows/profiles/gnemo/My Pictures
/home/gnemo/.wine/drive_c/windows/profiles/gnemo/My Documents
/home/gnemo/.mozilla/firefox/2ow8n13e.default/lock
/home/gnemo/.ies4linux/ie6/dosdevices/c:
/home/gnemo/.ies4linux/ie6/dosdevices/z:
/home/gnemo/.ies4linux/ie6/drive_c/windows/system
/home/gnemo/.ies4linux/ie6/drive_c/users/gnemo/My Music
/home/gnemo/.ies4linux/ie6/drive_c/users/gnemo/Desktop
/home/gnemo/.ies4linux/ie6/drive_c/users/gnemo/My Videos
/home/gnemo/.ies4linux/ie6/drive_c/users/gnemo/My Pictures
/home/gnemo/.ies4linux/ie6/drive_c/users/gnemo/My Documents
/home/gnemo/.openoffice.org2/user/config/arrowhd_en-GB.soe
/home/gnemo/.openoffice.org2/user/config/classic_en-US_en-ZA.sog
/home/gnemo/.openoffice.org2/user/config/styles_en-US_en-ZA.sod
/home/gnemo/.openoffice.org2/user/config/palette_en-US_en-ZA.soc
/home/gnemo/.openoffice.org2/user/config/classic_en-GB.sog
/home/gnemo/.openoffice.org2/user/config/hatching_en-GB.soh
/home/gnemo/.openoffice.org2/user/config/hatching_en-US_en-ZA.soh
/home/gnemo/.openoffice.org2/user/config/palette_en-GB.soc
/home/gnemo/.openoffice.org2/user/config/modern_en-GB.sog
/home/gnemo/.openoffice.org2/user/config/arrowhd_en-US_en-ZA.soe
/home/gnemo/.openoffice.org2/user/config/modern_en-US_en-ZA.sog
/home/gnemo/.openoffice.org2/user/config/styles_en-GB.sod
/home/gnemo/.googleearth/instance-running-lock
/home/gnemo/bin/ie6
/home/gnemo/.thunderbird/tri6cxav.default/lock
/home/gnemo/.adobe/Acrobat/8.0/Cert/curl-ca-bundle.crt
/home/gnemo/.kde/tmp-Blacktower64
/home/gnemo/.kde/cache-Blacktower64
/home/gnemo/.kde/share/apps/ktorrent/tor0/cache/filename1
/home/gnemo/.kde/share/apps/ktorrent/tor0/cache/filename2
/home/gnemo/.kde/share/apps/ktorrent/tor0/cache/filename3
/home/gnemo/.kde/share/apps/ktorrent/tor0/cache/filename4
/home/gnemo/.kde/share/apps/ktorrent/tor0/cache/filename5
/home/gnemo/.kde/share/apps/ktorrent/tor0/cache/filename6
/home/gnemo/.kde/share/apps/ktorrent/tor0/cache/filename7
/home/gnemo/.kde/socket-Blacktower64
gnemo@Blacktower64:~$         

```
I also ran the results of the find command through grep, hunting first for kcore, then proc, then sys (looking for that "sysrq-trigger" file), and came up empty:
```

gnemo@Blacktower64:~$ sudo find $HOME -type l | grep kcore
gnemo@Blacktower64:~$ sudo find $HOME -type l | grep proc
gnemo@Blacktower64:~$ sudo find $HOME -type l | grep sys
/home/john/.ies4linux/ie6/drive_c/windows/system

```
(Well, the "grep sys" found something, but not what I was looking for, only the Wine fake Windows drive.)
-Gnemo

---

### Post by Yannick Le Saint kyncani on 2009-09-12
The command I gave you listed symlinks but did not follow them, it was intended. If you want to see where these links are pointing :

sudo find $HOME -type l -print0 | sudo xargs -0 ls -l

And if you want to find your kcore following symlinks (which may be a bad idea) :

sudo find -L $HOME -name kcore

Also, ~/.wine/dosdevices are symlinks to various locations. I'd bet one of them is pointing to /

> **gnemo said:**
> That, precisely, is the mystery. :)

And there is no mystery, I'm pretty sure your kcore comes from a symlink in your $HOME ;)
I was just showing you the door and I hope this post will help you walk through it.

---

### Post by gnemo on 2009-09-13
> **Yannick Le Saint kyncani said:**
> 
Also, ~/.wine/dosdevices are symlinks to various locations. I'd bet one of them is pointing to /

We have a winner! :)

I ran the "find $HOME -type l -print0 | xargs -0 ls -l" command you suggested, and buried in the output was the following:
```

lrwxrwxrwx 1 gnemo gnemo   1 2009-06-12 13:55 /home/gnemo/.ies4linux/ie6/dosdevices/z: -> /
lrwxrwxrwx 1 gnemo gnemo   1 2008-08-16 11:41 /home/gnemo/.wine/dosdevices/z: -> /

```
So, you're absolutely right, Yannick. Wine created links to /, and the scp command followed those. If I'd left it going it would presumably have copied the entire / tree, including /home/gnemo, and then found those same symlinks inside it...endless recursive file copying, anyone? :eek:

What I've learned from this: if you use Wine and let it set up its fake Windows drives in your user directory, you then cannot use scp -prv to backup your home directory.

I'll go ahead and mark the thread "solved". Thanks to everyone who chimed in.

-Flieslikeabeagle

---

