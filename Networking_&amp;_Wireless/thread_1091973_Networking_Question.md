---
title: "Networking Question"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by marsdend on 2009-03-09
Hi all,

I need some advice on a networking issue.

_Scenario_
I am looking at creating a home network where files and setting follow you. I am a fairly new Linux user using Ubuntu for just over 1 year so i do not know much to do with terminal just the apt-get really. I am looking for a method of doing this through the GDE. I have an 1TB external Network HD if this could help in any way.

Any ideas or advice would be appreciated.

Note... I have 1 PC, 2 Laptops & Wireless Broadband Router

Dan

---

### Post by pytheas22 on 2009-03-10
One way to do this is to keep one /home directory (the place where all user-specific settings and files are stored) on one of your machines, and mount it over the network as /home for the other computers.  You might see a performance decrease, because reading and writing of users' files will take place over the network rather than directly to disk, but on a local network, it shouldn't be much of a problem.

There are three basic steps:

1. configure the central computer (i.e., the one with the main /home directory) to share its /home directory over the network.  You could use ssh (for which there's a guide [here]("http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/")), NFS (documentation [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo#Installation")) or samba as the protocol for the share, although NFS would probably be the easiest way to go.

2. edit /etc/fstab on the client machines so that they use the remote /home directory as /home, instead of a local directory.

3. make sure that all the computers in your house have the same user accounts installed, with the same passwords for each account, etc.  You could set this up manually, or just copy the same /etc/passwd file onto all the machines.

Unfortunately, you're going to need to use the command-line to do this.  But if you follow instructions, it should be possible to accomplish even if you don't have much Linux experience.

I'm sorry not to give more detailed instructions--I don't have time right now--but if you're willing to do some research, this should get you started.  Feel free to ask for more clarification if necessary.

EDIT: also note that if you move the laptops out of your house, this would cause problems, because they wouldn't be able to mount /home.  I don't know if this poses a problem for you.

---

