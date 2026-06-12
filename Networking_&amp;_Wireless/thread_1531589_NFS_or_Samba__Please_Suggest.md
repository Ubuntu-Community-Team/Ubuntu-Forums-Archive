---
title: "NFS or Samba || Please Suggest"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2010-07-15
Recently I rebuilded my old PC & now I am planning to buy a switch & setup a small home network consisting of my new & old computers.

I connect to the internet using an adsl modem, so thats the other thing that I will connect to the switch.

Both the computers are & will be running Ubuntu.

The old one will run Hardy while the new PC is running Lucid. So there are no (& there will be no) windows PCs.

Now, in that case which file sharing service is most appropriate for me ?

Is it Samba ? or is it NFS ?

Previously I had some experience with Samba but I have never even seen  NFS's interface, don't know what kind of features it offers in comparison to Samba.

So, please help me choose the correct one.

Please reply.

---

### Post by dragin33 on 2010-07-15
Samba may be easier to set up in Ubuntu through the GUI.  You may have to set up NFS through the command line (not sure if it's easily done through the gui.)  That being said NFS is quite fast and you may see some performance improvements using that instead of Samba.

---

### Post by amsterdamharu on 2010-07-15
You could try setting up nfs, I had no trouble with it.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)


It was faster than samba for linux to linux file copying. Windows can support nfs as well but I've never tried it.

---

### Post by linuxyogi on 2010-07-15
> **dragin33 said:**
> Samba may be easier to set up in Ubuntu through the GUI.  You may have to set up NFS through the command line (not sure if it's easily done through the gui.)  That being said NFS is quite fast and you may see some performance improvements using that instead of Samba.

> **amsterdamharu said:**
> You could try setting up nfs, I had no trouble with it.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)


It was faster than samba for linux to linux file copying. Windows can support nfs as well but I've never tried it.

Thanks for your replies.

I guess I will try nfs first once I am able to finish setting up my network.

I use firestarter firewall. Suppose I use nfs, will it be necessary to open  any ports in the firewall?   

If yes, will this make my PC more vulnerable to attacks?
I am asking this because I am using my adsl modem in bridged mode & firestarter is pretty much my only defence against any intrusions.

---

### Post by linuxyogi on 2010-07-15
> **dragin33 said:**
> (not sure if it's easily done through the gui.)  

I visited [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) but there is no mention of any gui here.

Is there any gui for NFS at all or is command line the only option ?

If there is no gui then I will have no other choice but to install Samba.

I hope there is a gui. **[-o<**

---

### Post by amsterdamharu on 2010-07-16
For the server I could not find a gui, for the client you can add stuff in fstab. 

You can copy and paste terminal commands but if it's too much then I guess you're stuck with samba.

---

### Post by linuxyogi on 2010-07-18
> **amsterdamharu said:**
> For the server I could not find a gui, for the client you can add stuff in fstab. 

You can copy and paste terminal commands but if it's too much then I guess you're stuck with samba.

Once I finish setting up my network I will definitely try NFS first. 
In case I don't succeed I will move to Samba. 
I will write back soon.   


Thanks a lot.

---

### Post by linuxyogi on 2010-09-19
> **amsterdamharu said:**
> You could try setting up nfs, I had no trouble with it.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)


It was faster than samba for linux to linux file copying. Windows can support nfs as well but I've never tried it.

Just finished setting up nfs.
And yes, samba is really slow.
Thanks.

---

