---
title: "emacs through ssh through ssh"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by Rkgoboom on 2010-03-04
I am working on a cluster for a molecular dynamics class and I have to edit my FORTRAN code (only the newest and best for me!). In order to get through to the cluster I have to ssh in. The network on which the cluster resides is behind a firewall, so I have to ssh through the firewall into the network first.

Me-------ssh--->Host 1------ssh----->cluster

this is fine, I can login and move files and folders as needed, including sftp-ing into host 1, then into the cluster so I can transfer files from cluster to host and then host to me. This gets rather tiresome, so it would be nice to edit the files in place.

The problem is that when I access my code with emacs it launches the emacs client on Host 1, with no mouse support. I know the purists will howl about how I should be using keyboard shortcuts, but I am a chemist and not a programmer, so the mouse is very nice for me.

Is there any way I can perhaps mount the cluster using sshfs so that when I open my code it launches a local instance of emacs?

Sorry if this is the wrong forum, but I thought it was network related.

---

### Post by Iowan on 2010-03-04
Interesting problem - unfortunately, about all I can offer for help is [this]("https://help.ubuntu.com/community/SSHFS") link for SSHFS -  and you probably already know how to do that...

---

### Post by r939ick on 2010-03-05
The FAQ on sourceforge makes it look like sshfs supports a -p switch, so you might be able to use port redirection to accomplish what you want, e.g. (NOTE: untested):

me$ ssh -L2222:cluster:22 username@Host1
me$ sshfs -p 2222 localhost:/remote/mount/point /local/mount/point

If that doesn't work, you could try mounting cluster onto Host1 via sshfs and then accessing that mount point from emacs via tramp:

C-x C-f /username@host1:/mount/point/on/host1

---

### Post by jpkotta on 2010-03-07
Make sure you're using xterm-mouse-mode or something similar.

This looks like how I ssh in to my workstation at work.  The IT guy set this up; I think this is all that's needed but I'm not 100% sure.

On the local machine ("Me"), I have this in my ~/.ssh/config:
```

Host cluster
HostName cluster.example.com
ProxyCommand ssh -q host1.example.com "nc -q 1 %h %p"

```

On host1, netcat (nc) is installed, and I don't think any special configuration is necessary.

With this configuration, sshfs works and so do mouse clicks in a terminal.

---

