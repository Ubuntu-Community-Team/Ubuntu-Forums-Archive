---
title: "I just want 2 ubuntu machines to talk to each other!"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by morganpatrick on 2009-08-31
I can't find any reliable, current documentation on this. Samba is working, but what's the point if i'm running two linux machines? I just want NFS to be running, and be able to either map network drives or have a mount point, and be able to do this graphically if at all possible.

I only see a windows-network connecting my two ubuntu machines. I have the nfs packages installed.

It's 2009 and this very basic feature still eludes Ubuntu. Or maybe it doesn't and I just don't know what I'm doing.

I'm trying to sync my files with Grsync but it can't find a path to my other computer because those folders don't appear to be mounted anywhere.

---

### Post by Jimlas53 on 2009-08-31
You can connect your two machines with NFS, and it is fairly painless.  Yes, you will need to edit a couple of files on each machine, but it's not so bad.  Basically you need to export the shared folder on each machine, or one one machine if only one folder is needed.  I have 4 machines connected to a main machine with a common folder that everyone can read and write.  The folder is automatically mounted when each client starts up.  It is completely transparent.

Hope this helps!

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by morganpatrick on 2009-08-31
but does that mean, then, that you have to share though one folder? If I'm trying to rsync my folders together so that I have the same files in both my home folders, this wouldn't work if theres only one 'shares' folder.

---

### Post by dmizer on 2009-08-31
> **morganpatrick said:**
> but does that mean, then, that you have to share though one folder? If I'm trying to rsync my folders together so that I have the same files in both my home folders, this wouldn't work if theres only one 'shares' folder.

I think you might be looking for unison: [https://help.ubuntu.com/community/Unison](https://help.ubuntu.com/community/Unison)

---

### Post by morganpatrick on 2009-08-31
How does Unison help though? I still can't connect to the other computer through it.

---

### Post by morganpatrick on 2009-08-31
I managed to connect both computers through ssh, which will at least let me bookmark the connection. I still don't know where the mount point is, which means I can't use Grsync, but I can use Unison.

SSH is half as fast as Samba, though. I wonder why, if Linux is the choice for IT people, networking wouldn't be a lot easier than this.

---

### Post by dmizer on 2009-08-31
> **morganpatrick said:**
> I managed to connect both computers through ssh, which will at least let me bookmark the connection. I still don't know where the mount point is, which means I can't use Grsync, but I can use Unison.

SSH is half as fast as Samba, though. I wonder why, if Linux is the choice for IT people, networking wouldn't be a lot easier than this.

Simple file sharing is indeed easy to accomplish in Ubuntu, but you are not trying to do simple file sharing.

SSH may be a bit slower than samba because SSH is an encrypted protocol. It should not be noticeably slower though unless you have a very low powered computer. There may be something interfering with the connection like a local firewall (for example).

---

### Post by morganpatrick on 2009-09-01
I guess when I think of 'simple file sharing' I think of what I'm used to, in Windows: you go to network, you see a network, you doubleclick it, you see another computer, you doubleclick it, you see shared folders on that computer. and if you want you can right-click > 'map network drive' and give it a drive letter.

maybe this isn't simple file sharing after all, and i just always thought it was. In any case, it doesn't look to me like ubuntu has anything like this, except for samba, which is designed to make linux machines talk to windows machines, and not to each other (although this will work too).

If i'm wrong, and there's something like nfs that has this functionality, i'd rather use linux-based networking. if i'm right, and only samba can do this kind of 'simple' networking, then i'll stick with samba.

---

### Post by dmizer on 2009-09-01
> **morganpatrick said:**
> I guess when I think of 'simple file sharing' I think of what I'm used to, in Windows: you go to network, you see a network, you doubleclick it, you see another computer, you doubleclick it, you see shared folders on that computer. and if you want you can right-click > 'map network drive' and give it a drive letter.

Linux is not Windows. So you should expect to do things differently than you did in Windows. Linux is not a free version of Windows, it's a completely different OS and it does lots of things differently, including networking.

Also, you didn't mention anything about synchronizing folders in your Windows scenario. This is what makes it more complex. If you don't need to synchronize your folders, then Ubuntu file sharing is just as simple as Windows file sharing. Right click -> sharing options -> check all three boxes. To mount the share, just click places -> connect to server.

It doesn't really matter if the protocol used is Samba or NFS as long as it gets the job done. Both do equally well, and Samba provides the added benefit of allowing interoperability with Windows machines. And, since Samba is a completely open source project, it's not like you're using an "evil Microsoft" tool.

Again, for MOST situations, you'll not need the CLI in order to configure simple file sharing. Once you start mapping drives, it's not simple file sharing anymore, and (in Linux) you have to step beyond the bounds of the GUI.

If you need to create a physical mount point, you can either follow this howto: [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877) or you can follow the 2nd link in my sig.

Or if you're not averse to using CLI tools, the 4th link in my sig provides a thorough and simple howto for configuring NFS. There are no GUI tools for NFS (that I am aware of) because NFS is designed for use between Linux/Unix servers which have no GUI to begin with.

---

