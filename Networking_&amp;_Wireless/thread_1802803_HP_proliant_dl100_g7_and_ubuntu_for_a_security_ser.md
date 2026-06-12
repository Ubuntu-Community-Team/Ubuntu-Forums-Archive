---
title: "HP proliant dl100 g7 and ubuntu for a security server need help"
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by jewfromdahood on 2011-07-12
I am trying to set up in a few days when the servers come in. A Linux security server. This server will act as the gateway, router, and firewall. I need to know where I can find the documentation to help me in setting up the following list
1) router as it will have an intel 4 port server NID connected VoIP, and windows server enterprise, PoE switches and a wireless router will be behind this
2) firewall and anti-virus to scan every packet going in and out if possible
3) DNS cache server
4) we will have an air band T3 and roadrunner business fused together in case the satellite for the T3 goes down
5) RAID 5 with hot spare via 3ware 9750
6) SSH or other way to remote access this server

Now here is another issue that I can not convince the people who are hiring me to change their minds about. They want a GUI. Which I think is ridiculous on a server. The reason is the techs are not familiar with Linux and I am still quite noobbish but quite familiar with Linux (been using it for about 6 years at this point) and used to the terminal. And I think a gui on a server is ridiculous. But it took me a week to convince them windows is the worst OS for a security server. The other servers must be windows as this if for a dental office being upgraded, and the software they use is windows only.

---

### Post by jewfromdahood on 2011-07-12
anti-virus will be Eset Nod32 as I have great success with it on windows, and they have a linux, and mac version.
 as for the other stuff... BUMP!

---

### Post by jewfromdahood on 2011-07-13
bump

---

### Post by jewfromdahood on 2011-07-13
I know I already posted this but no one would help me so this is a repost. but how do I fuse two internet connections together and make it a wired router as well. 
I found a lot but I still 
I am trying to set up in a few days when the servers come in. A Linux security server. This server will act as the gateway, router, and firewall. I need to know where I can find the documentation to help me in setting up the following list
1) router as it will have an intel 4 port server NID connected VoIP, and windows server enterprise, PoE switches and a wireless router will be behind this
2) firewall and Eset Nod32 anti-virus to scan every packet going in and out if possible
3) DNS cache server
4) we will have an air band T3 and roadrunner business fused together in case the satellite for the T3 goes down
5) RAID 5 with hot spare via 3ware 9750
6) SSH or other way to remote access this server
7) block all use to youtube and other recreational sites, as well as any .exe files downloaded.

Now here is another issue that I can not convince the people who are hiring me to change their minds about. They want a GUI. Which I think is ridiculous on a server. The reason is the techs are not familiar with Linux and I am still quite noobbish but quite familiar with Linux (been using it for about 6 years at this point) and used to the terminal. And I think a gui on a server is ridiculous. But it took me a week to convince them windows is the worst OS for a security server. The other servers must be windows as this if for a dental office being upgraded, and the software they use is windows only.

---

### Post by karlson on 2011-07-13
> **jewfromdahood said:**
> 

1) router as it will have an intel 4 port server NID connected VoIP, and windows server enterprise, PoE switches and a wireless router will be behind this
2) firewall and anti-virus to scan every packet going in and out if possible


[IPTables HOWTO](https://help.ubuntu.com/community/IptablesHowTo) will cover the set up of the server.


> 
3) DNS cache server


[BIND 9](https://help.ubuntu.com/community/BIND9ServerHowto) documentation.

> 
4) we will have an air band T3 and roadrunner business fused together in case the satellite for the T3 goes down


I don't think this is a Linux Question.

> 
6) SSH or other way to remote access this server


SSH but you want to configure it to listen on the internal interface only.

> 
Now here is another issue that I can not convince the people who are hiring me to change their minds about. They want a GUI. Which I think is ridiculous on a server. The reason is the techs are not familiar with Linux and I am still quite noobbish but quite familiar with Linux (been using it for about 6 years at this point) and used to the terminal. And I think a gui on a server is ridiculous. But it took me a week to convince them windows is the worst OS for a security server. The other servers must be windows as this if for a dental office being upgraded, and the software they use is windows only.

GUI on a firewall server is a bad idea because it could open ports on the server, which you want to have closed.

You also might want to take a look at [Linux Router](https://help.ubuntu.com/community/Router) documentation.

---

### Post by jamesden_ip on 2011-07-13
Check out Zentyal community edition. It provides most if not all those features.

---

### Post by uRock on 2011-07-13
Duplicate threads merged. Please do not create multiple threads on the same subject.

Thanks,
uRock

---

### Post by jewfromdahood on 2011-07-13
I don't think this is a Linux Question.

Yes it is I am asking because I want to know how do you merge two different internet connections together?

---

