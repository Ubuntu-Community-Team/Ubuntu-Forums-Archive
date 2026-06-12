---
title: "samba"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by X-313 on 2009-09-01
I am new to Ubuntu and would like join my Ubuntu desktop to Windows domain and share files and printers. But I have another machine (running on FreeBSD) samba installed on. Do I need to install samba on my Ubuntu to achive above-mentioned or I can configure existing samba on FreeBSD to share files and printers in Windows AD?

---

### Post by shredder12 on 2009-09-01
In order to connect to a windows machine and access its shared folder you jst need to install the samba client on your machine  i.e. sambfs but if you want your files and folders to be shared on a network as well then you will have to install samba server on your machine..

I don't have much information about enabling printer sharing on networks but probably CUPS can be configured to do so..

So, if you want to install samba server on your system you can follow this tutorial
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Hope that helps..

---

### Post by X-313 on 2009-09-01
So you suggest that I have to install samba on each *nix machine in order to share its files/folders on it? Won't installation of samba just one of the *nix machine achieve that (to share files/folders on other machines as well)?

---

### Post by X-313 on 2009-09-01
I think I have to install one samba server and samba clients on others... but can I browse through all *nix clients then?

---

### Post by w00ly on 2009-09-01
> **X-313 said:**
> So you suggest that I have to install samba on each *nix machine in order to share its files/folders on it? Won't installation of samba just one of the *nix machine achieve that (to share files/folders on other machines as well)?

no because you have no way of getting the files off the ubuntu system. You need to install samba
thankfully it's easy. Load up synaptic or kpackagekit and install samba, smbclient and smbfs (i think smbclient or smbfs will install the other but just to be sure..)
or simply
sudo apt-get install samba smbclient smbfs
in terminal

---

### Post by X-313 on 2009-09-02
nobody answered to my question. I am not asking about just installing samba, but the way of using samba let's say for a bunch of (10) linux/unix desktops or servers in windows network. Should I install samba server just on one of linux/unix systems or to all of them to share files with windows?

---

### Post by shredder12 on 2009-09-02
Look.. if you want to jst access the windows server share from ubuntu..
you jst need to install samba client on your system.
but if you are planning to share files and folders from your ubuntu system to be accessed by windows machines as well.. then you need to create servers on those machines.. 
yes, then you will have to install samba server on every machine ...

---

### Post by X-313 on 2009-09-02
OK. Thank you. Got it.

---

