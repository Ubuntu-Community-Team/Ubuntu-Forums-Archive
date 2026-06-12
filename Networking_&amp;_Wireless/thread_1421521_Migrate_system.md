---
title: "Migrate system"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by leg on 2010-03-04
How do I migrate a system from one machine to another. By this I mean install a new system on a new machine then have a copy of all the settings etc from the old one copied to the new one.

---

### Post by leg on 2010-03-09
Sorry to bump but I want to give this one more go. I want to be able to install a new system and them migrate all my installed programs over etc. I thought there was a command I could use to export which programs were installed.

---

### Post by dannyboy79 on 2010-03-09
> **leg said:**
> Sorry to bump but I want to give this one more go. I want to be able to install a new system and them migrate all my installed programs over etc. I thought there was a command I could use to export which programs were installed.

looking into backing up your /home/username directory. also, aptoncd from synaptic. there's literally hundreds of answers to this question in google and ubuntuforums. just try different search statements.

---

### Post by leg on 2010-03-12
thanks

---

### Post by srs5694 on 2010-03-12
There are a lot of ways to do this. If you're only interested in your personal files, and if you have lots of free disk space on both systems, this may be the easiest way:


[list=1]
[*]Use tar to create a local backup of /home: As root, type "tar cvzf /home/name.tgz /home/name", where "name" is your directory name. You could also create the tarball somewhere else, which might be necessary if you've got free disk space one place but not another.
[*]Use your favorite network protocol to transfer /home/name.tgz. If you've got an SSH server on the new system, typing "scp /home/name.tgz newsystem:/home/" as root should do the trick (although some configurations block root access to the SSH server, which will complicate this). FTP, a Web server on the original computer, Samba, and NFS are all other options that will work. Which is easiest depends on which, if any, you've got running and on which computer.
[*]If it's not already set up, create a new account on the new computer. Use the same username you used on the original.
[*]On the new system, untar the tarball you've copied. Assuming the tarball is in /home, typing "tar xvzf name.tgz" should do this. Note that this will untar the tarball using the original name and username.
[/list]


There are ways to combine some of these steps. For instance, if you've got NFS or Samba set up, you can create the tarball directly on the new system, or even forego creation of a tarball altogether. For instance, if you want to copy /home/fred, and if the new system's /home directory is mounted at /mnt/newsystem/home, you could type this:

```

cd /home
tar cpf - ./fred | (cd /mnt/newsystem/home; tar xvpf -)

```

That'll copy the entire /home/fred directory to /home/fred on the new system in one go; but this will only work with a file-sharing server such as NFS or Samba set up. There could also be ownership or permissions glitches, depending on whether these features are properly configured.

In fact, it's possible to transfer an entire installed system in a similar way, using an emergency disc, thus obviating the need to use the installer on the new system. This will also copy over the system configuration options (stored in /etc), all the installed packages, etc.

---

### Post by leg on 2010-03-13
I think what I need is a mixture of the two things suggested so far. I was pretty sure there was a way of exporting a list of installed programs from apt that could be fed into another (new) systems apt so that the same programs are installed. Then I could make sure all the configs are copied in the way suggested.

---

