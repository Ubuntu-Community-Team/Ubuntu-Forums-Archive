---
title: "Best way?"
date: 2008-07-06
forum: Mythbuntu
---

### Post by jensk on 2008-07-06
I am looking for the best way to combine my present two server setup into to one.

I have an e-smith server as mail and web server with PhpFusion as CMS. I have a Knoppmyth server with Myth 0.20 as master backend in mI am looking for the best way to combine my present two server setup down to one.

I have an e-smith server as mail and web server with PhpFusion as CMS. I have a Knoppmyth server with Myth 0.20 as master backend in my mythsetup (PVR-500 analog input) with a couple of frontends. My diskstorage is a Qnap 409pro with 1.4 tByte configured i raid 6. Both servers uses NFS against the NAS as data store. No myth frontend is running on the master backend.

I would like to combine theese two server down to one. A Ubuntu server with Mythbuntu on, Apache, cms etcy mythsetup (PVR-500 analog input) with a couple of frontends. My diskstorage is a Qnap 409pro with 1.4 tByte configured as raid 6. Both servers uses NFS against the NAS as data store. 

No myth frontend is running on the master backend server.

I would like to combine theese two server down to one. A Ubuntu server with Mythbuntu on, Apache, PhpFusion cms, mailserver, Horde webmail, spamfiltering etc.

I am no newbie but is not skilled enough in Linux. I am able to read howtos, steal a littele here and there to get things working. I am not able to write script og command files.

My question is therefore what is the easiest way to achiewe this?

- do i install ubuntu server, an ubuntu desktop on top of that and then myth backend through synaptic?

- Do i install mythbuntu and then configure all the services apache2, virtual webservers, mail, horde etc. on top of that.

It would be great if i was able to use the diskless frontend server part and PXE booting my frontends from the same server.

I would like the server to have webmin, myth backend, mail with spamfiletring, several virtual webservers/hosts, horde webmail and mysql. This way it would be the only server in the house. It is going to be used by several users as their webmail server with several websites and mail domain names on it.

The hardware it self is a P4 2.8 Ghz, 1 gbyte ram with Gbit network connection and 400Gbyte mirrored sata disk. The server it self is stored away in the basement and SSH'ed into - occationally VNC if the gui is loaded.

Any input would be welcome as this should be my summer holliday projekt.
/jk

---

### Post by ian dobson on 2008-07-06
Hi,

Sounds alot like my setup. I'm running Myth-backend, Apache, xmail (mail server) on my main server. I'm running ubuntu server on it.

If your happy working from the command line, go server, you don't need X to run all the services.

If you really want a graphical frontend then just install Mythbuntu.

Hope this helps abit.

Regards
Ian Dobson

---

