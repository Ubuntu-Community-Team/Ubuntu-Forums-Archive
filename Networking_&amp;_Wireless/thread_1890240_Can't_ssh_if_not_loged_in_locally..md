---
title: "Can't ssh if not loged in locally."
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by Ceiber Boy on 2011-12-03
I have two ubuntu machines 10.04 desktops, (for purpose of explanation I'll call one server and one client).

Server
Installed openssh

Client
Generated authentication key, copied .pub part of the key to server.

Server
Disallowed password authentication, restarted ssh deamon.

Now I can only login remotly if the server has been loged into locally. If I restart the server remotely I can't log back in remotely untill someone else has logged in locally.

How am I able to restart the server remotely and then log back in with out having to have someone to log in locally for me to login remotely? 

Thanks you

---

### Post by dandnsmith on 2011-12-03
As someone who hasn't set up and used ssh, can I ask why you disallow pwd authentication on the server - after all, when you attempt to do the remote login via ssh you need to allow authentication, or otherwise somehow bypass it for a particular user on that remote machine (no password?)

---

### Post by Ceiber Boy on 2011-12-03
Ah, I have an encrypted home directory so the suggested solution is given here:

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

But ssh dose not ask me for a Password as suggested, but stated 'key based authentication'.

Also if someone was able to add their public key to the authorised keys file (because it's outside of the encrypted home folder) would they not then be able to gain access to my encrypted home folder?

---

### Post by Ceiber Boy on 2011-12-03
> **dandnsmith said:**
> As someone who hasn't set up and used ssh, can I ask why you disallow pwd authentication on the server - after all, when you attempt to do the remote login via ssh you need to allow authentication, or otherwise somehow bypass it for a particular user on that remote machine (no password?)

Security, plane and simple. The like in the previous post gives a very good explanation / reasoning for this

---

### Post by dandnsmith on 2011-12-03
I've read the link posting - thanks for that.
I see your problem - the suggested route for implementation is giving you problems, which means either that there is a flaw in the implementation, a flaw in the server installation, or you have misunderstood sufficiently to get your setup wrong.
I can only suggest you try some experiments, probably with a dummy username/pwd on the server, to see if you can get the correct results in the case where the user on the server doesn't have an encrypted home directory.

Good luck

---

### Post by Ceiber Boy on 2011-12-03
> **dandnsmith said:**
> I've read the link posting - thanks for that.
I see your problem - the suggested route for implementation is giving you problems, which means either that there is a flaw in the implementation, a flaw in the server installation, or you have misunderstood sufficiently to get your setup wrong.
I can only suggest you try some experiments, probably with a dummy username/pwd on the server, to see if you can get the correct results in the case where the user on the server doesn't have an encrypted home directory.

Good luck

I need to do some experimenting; I'll post my findings.

---

### Post by Ceiber Boy on 2011-12-14
> **Ceiber Boy said:**
> Ah, I have an encrypted home directory so the suggested solution is given here:

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

But ssh dose not ask me for a Password as suggested, but stated 'key based authentication'.

Also if someone was able to add their public key to the authorised keys file (because it's outside of the encrypted home folder) would they not then be able to gain access to my encrypted home folder?

ok..have found some time to do some testing, Following the instructions at

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

under the heading 'Encrypted Home Directory', dose work in that in allows you to ssh into the home directory of your user, however it dose not decrypt the home directory!

I then assume that the encrypted folders would then have to be mounted separately.

as mounting a encrypted home directory is a bit of a potch to say the least, I don't think I'll be doing that.

---

### Post by Ceiber Boy on 2011-12-14
It is possable to manually place a public key in the /etc/ssh/<username>/authorized_keys2 folder and then use that to ssh into the machine, but that dose not afford one any more access than when they were sitting in front of the machine manually placing their public key in the 'authorized_keys2' file. Unless the attacker ssh into the machine whalst the user was using the machine and had logged in, thus decrypting the home directory, but i don't know weather that would allow access for the attacker into the encrypted home directories! And I don't have the time to try this out.

so in short, (in my opinion as a user for what its worth), keep your authroized keys file inside your encrypted home directory as this is the most secure method. What this dose mean is that you have to live with the niggle that you can't ssh into it until you have phoned someone at the machines location to authenticate the user on the machine, (log in). Then you can SSH into it. Just tell them to lock the screen or something. 

Any other thoughts comments technical solutions I'd be happy to hear.

---

