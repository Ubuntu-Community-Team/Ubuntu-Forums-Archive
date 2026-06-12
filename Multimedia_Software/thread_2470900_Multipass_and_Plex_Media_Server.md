---
title: "Multipass and Plex Media Server"
date: 2022-01-15
forum: Multimedia Software
---

### Post by linuxtech32 on 2022-01-15
I had Plex Media Server running on a previous version of Ubuntu server, but due to some unforseen hardware issues, I had to re-install everything from scratch. I'm now running Ubuntu server 20.04.03 LTS. I also just installed the newest version of Plex Media Server through the Multipass option today. Per the documentation, multipass launch appliance:plexmediaserver, but from there, nothing is connecting.

Server address: 192.168.86.92
Multipass instance: 10.202.150.196

Plex used to run on the old server, but I didn't have multipass installed then. I am using UFW. I have another linux computer (Linux Mint) that I use for communicating with the server and a Roku TV that used to reach the Plex server. Now, I can't get them to connect to the instance. I haven't been able to find clear directions on how to connect to it. Do I have to install Plex again on the Multipass instance? Is there something special I have to do with UFW? There aren't any good guides on this part. Everyone has a different idea and all kind of drop off after the first few "Step 1:", "Step 2", "Step 3" ...step 4 kind of drops off into more or less yammering.

---

### Post by linuxtech32 on 2022-01-15
Disregard. I finally found the answer. For anyone who struggles with this, disable UFW and work with just IPtables.

The basic steps for the whole process
installed Multipass
Installed Multipass plexmediaserver instance
start the instance and note the IP address

IP tables
sudo iptables -t nat -I PREROUTING 1 -1 <main adapter...such as eno1> -p tcp --deport 32400 -j DNAT --to-destination <instance ip address>:32400
sudo iptables -I FORWARD -p tcp -d <instance ip address> --deport 32400 -j ACCEPT

Once I finally found that, everything is working the way it should. I finally found the UFW actually blocks the Multipass instances...you would think that would be right in the main Multipass documentation.

---

### Post by noisea on 2022-02-21
> **linuxtech32 said:**
> Disregard. I finally found the answer. For anyone who struggles with this, disable UFW and work with just IPtables.

The basic steps for the whole process
installed Multipass
Installed Multipass plexmediaserver instance
start the instance and note the IP address

IP tables
sudo iptables -t nat -I PREROUTING 1 -1 <main adapter...such as eno1> -p tcp --deport 32400 -j DNAT --to-destination <instance ip address>:32400
sudo iptables -I FORWARD -p tcp -d <instance ip address> --deport 32400 -j ACCEPT

Once I finally found that, everything is working the way it should. I finally found the UFW actually blocks the Multipass instances...you would think that would be right in the main Multipass documentation.

I think your post was very helpful in identifying the problem I was having. However, your iptables commands are confusing. Specifically, -1, --to-destination, & --deport are not iptables commands listed under iptables --h. Am I misunderstanding your instructions? I have only been using linux for a very short time so there's probably something obvious that I am missing.

---

