---
title: "SSH if the /home directory is shared"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by bilboe on 2009-11-13
Hello, i have 2 computers that share the /home over nfs, and i want to be able to ssh without a password between the two (to run mpich). I have gotten this to work with seperate home directories, but not when they share them. Any ideas?


Thanks!


-Bilbo

---

### Post by theshibboleth on 2009-11-15
I'm trying to do the same thing, following [https://help.ubuntu.com/community/MpichCluster](https://help.ubuntu.com/community/MpichCluster). I've succesfully got 2 out of 3 of the computers in my network configured properly, but I'm at a loss as to why the third one isn't working since it uses the same home directory as the other two computers. I almost think it might be better to run mpich without sharing the home directory, but I'm not sure how to implement this.

---

### Post by theshibboleth on 2009-11-16
I had success using separate folders once I decided to give all the computers only one hostname each in /etc/hosts. This might help in your case too. (So just use the ordinary hostnames of the computers within mpd.hosts This said, if your computers have different architectures, you might consider using separate folders anyway (as the binaries in the shared folder might not work for all the computers).

---

### Post by Lars Noodén on 2009-11-17
> **bilboe said:**
> Hello, i have 2 computers that share the /home over nfs, and i want to be able to ssh without a password between the two (to run mpich). I have gotten this to work with seperate home directories, but not when they share them. Any ideas?


Host-based authentication might be what you are looking for.  The client machine authenticates to the server and then the server allows all (or some) of the users to connect without further process.  

Three files on the server or target host must be modified to get host-based authentication working:
[list]
[*]/etc/shosts.equiv	- same syntax as rhosts.equiv, can point to netgroups
[*]/etc/ssh/ssh_known_hosts	- hold the identities of the clients
[*]/etc/ssh/sshd_config	 - turn on host-based authentication
[/list]

**shosts.equiv** on the server should have the hostnames and/or ip numbers of the other machines.  Don't try to manage users or anything tricky here.  

**ssh_known_hosts** on the server should have the public key(s) from the other machines.  Each machine can have more than one key, if you set it up that way.  So you can use a special key for host-based authentication.

**sshd_config** on the server should be set to allow host-based authentication, for at least one group containing at least one user. e.g. put them into the group **mpichcluster**:

```

Match Group **mpichcluster**
   HostbasedAuthentication **yes**

```

Each machine will need legitimate A,AAAA,or CNAME plus PTR entries in DNS.  If that is not possible then you may have to fiddle and kludge a bit with dnsmasq or something.  Or try skipping that requirement:

```

HostbasedUsesNameFromPacketOnly **yes**

Match Group **mpichcluster**
   HostbasedAuthentication **yes**

```


YMMV

---

### Post by Lars Noodén on 2009-11-17
> **bilboe said:**
> i want to be able to ssh without a password between the two (to run mpich)

I'm not familiar with how mpich is managed.  Are you talking about logging in for the purpose of starting a single program?

If so, then forget the host-based noise I wrote above and use key-based authentication plus sudo, if you need sudo.  Can you show the exact method you use to start mpich ?

---

### Post by i.r.id10t on 2009-11-17
Or you could use passwordless SSH keys...

---

### Post by bilboe on 2009-11-18
> **Lars Noodén said:**
> I'm not familiar with how mpich is managed.  Are you talking about logging in for the purpose of starting a single program?

If so, then forget the host-based noise I wrote above and use key-based authentication plus sudo, if you need sudo.  Can you show the exact method you use to start mpich ?


I start mpich with *mpdboot -n 8 -f .mpd.conf*

Is keybased authentication with the keys in the .ssh directory and noted in the .allowed_keys file? That is what i do and it works without nfs, but when i want to ssh when sharing the home directory, it means that they have the same .ssh directory too, so it will not work. Is there a way to change the location of the ssh directory to outside of the shared home and onto the local machine?

Thank you!

---

### Post by bilboe on 2009-11-18
Ok everyone, i figured it out! In /etc/ssh/ssh_config, there is a line that specifies the location of the identity file. I have changed this to a new directory on each node...(i.e. .ssh_node1/identity, .ssh_node2/identity.pub and so on...) 

And now i expect it will work, but i have not tried it.


Thank you!!

-Bilbo

---

