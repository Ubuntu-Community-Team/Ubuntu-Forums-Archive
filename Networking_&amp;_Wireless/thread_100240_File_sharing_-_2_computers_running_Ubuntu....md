---
title: "File sharing - 2 computers running Ubuntu..."
date: 2005-12-07
forum: Networking &amp; Wireless
---

### Post by Reaped In Half on 2005-12-07
As easy as possible. What's the best way? I have 2 computers both running behind a router - 1 wired, 1 wireless (laptop).  I just want to be able to swap files preferably with a gui.

---

### Post by Pablo_Escobar on 2005-12-07
One of the following options :
1. Network Share - perfect solution
2. Send files via Gaim or some other IM supporting DCC

---

### Post by steevc on 2005-12-07
I've used the IM option to transfer files between Ubuntu (Kopete) and Windows 98 (Psi).

I can map drives using LinNeighborhood, but that's more hassle for the odd file. One of these days I'll figure out how to network them properly.

---

### Post by Corvillus on 2005-12-07
You could also set up an SSH server on the 2 computers and then use sftp for file transfer, you'd also get the bonus of being able to remotely adminster them through shells and X tunnels.

---

### Post by frodon on 2005-12-07
I would use NFS if i was in your case because it's easy to use, reliable and you can mount the shared drives on startup.
[http://www.rhce2b.com/clublinux/RHCE-24.shtml](http://www.rhce2b.com/clublinux/RHCE-24.shtml)

When i want to share files between computer with different OS i always use ftp because it eat few CPU power.

---

### Post by Mathboy on 2005-12-09
I'm a fan of sshfs :)

(quote from [here]("http://ubuntuforums.org/showthread.php?p=547477#post547477"))

[QUOTE=Mathboy]
Things don't get much easier than sshfs!

On the server (which stores the files):
just install ssh :)

On the client:
install sshfs

Then to share the /jeremy/music folder on "myserver" just go:
sshfs myserver:/jeremy/music /jeremy/music

That's it! :)

Check out [this]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/") page for some more info.[/QUOTE]

---

