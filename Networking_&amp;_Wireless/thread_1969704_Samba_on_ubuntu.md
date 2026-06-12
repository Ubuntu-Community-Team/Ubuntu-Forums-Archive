---
title: "Samba on ubuntu"
date: 2012-04-30
forum: Networking &amp; Wireless
---

### Post by bfrie on 2012-04-30
I have not been able to get access to a network printer with ubuntu 10.04 or 11.04. I thought I could do it with samba but every time I attempt using samba an error message of some kind comes up and I can not proceed. Therefore, I can not 'see' any other partitions or other work stations on the network.

If samba is the issue, please inform me how to proceed. 

Is a solution to upgrade to 12.04 and all will be corrected?

bfrie

---

### Post by garvinrick4 on 2012-04-30
Are you running all Linux boxes or are you running a combination with some Windows boxes.
Must set your shares (what you want to share) in both Linux or Windows. 
Windows is Windows workgroup. If you want a GUI app to use for your Samba shares:
All else just works out of box in Ubuntu.
```
sudo apt-get install system-config-samba
```

---

### Post by bfrie on 2012-04-30
> **garvinrick4 said:**
> Are you running all Linux boxes or are you running a combination with some Windows boxes.

I am running some with Windows partitions and one workstation is just windows.


Must set your shares (what you want to share) in both Linux or Windows. 
Windows is Windows workgroup. If you want a GUI app to use for your Samba shares:
All else just works out of box in Ubuntu.
```
sudo apt-get install system-config-samba
```

Is the above install a way to set my shares?

When I entered the above it failed.

_ldb.LdbError: (80, 'Failed to load modules from: /usr/lib/samba/ldb\n')
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)

What did I do incorrectly?

bfrie

---

### Post by garvinrick4 on 2012-04-30
Go to ubuntu software center or synaptics and remove anything samba4 should be [COLOR=Red]Version: 2:3.6.3-2ubuntu2 installed.
[COLOR=Black]
system-config-samba is a package where you can go from[COLOR=RoyalBlue] file[/COLOR] to[COLOR=RoyalBlue] add[/COLOR] to[COLOR=RoyalBlue] browse[/COLOR] find what you want to add as share and select.
Is a GUI package instead of editing  [COLOR=RoyalBlue] /etc/samba/smb.conf [/COLOR]manually.

Somehow it looks like you installed Samba4 which is a beta package. 

 


[/COLOR] 

[/COLOR]

---

### Post by garvinrick4 on 2012-04-30
Here is screenshot of correct samba, In new install I just added system-config-samba and it added everything it needed and works fine. Of course I did not have anything samba4 releated installed.

---

### Post by bfrie on 2012-05-01
I have removed the samba4 files using the above instructions.

Will I have to add anything if I now upgrade to ubuntu 12.04?

bfrie

---

### Post by garvinrick4 on 2012-05-01
Anytime you upgrade to new version
will upgrade all packages. Just make sure you upgrade your 11.10 then dist-upgrade to
12.04. Enjoy your Ubuntu Linux.

---

### Post by Gilgen on 2012-12-06
I'm having problems installing as well this is what I get:-


reg@Reg-Netbook:~$ sudo apt-get install system-config-samba
[sudo] password for reg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.



The following information may help to resolve the situation:

The following packages have unmet dependencies.
 system-config-samba : Depends: samba but it is not installable
E: Unable to correct problems, you have held broken packages.
reg@Reg-Netbook:~$ 



I'm running 12.04
Any ideas?

---

