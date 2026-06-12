---
title: "Help! VPN setup"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by Crispygb on 2009-05-07
Hello

I'm trying to set Ubuntu up (Jaunty) so that I can remote desktop into my office computer (running Windows XP).  I'm supposed to install the Cisco AnyConnect client which my employer (a university) has made available on their website.  It won't allow me to do a web installation, so I have to downnload a file called vpnsetup.sh.  I cannot get this to install at all.  
Any ideas?

I'm also having problems getting wireless to work.  I've installed the relevant drivers so the wifi light is on, but it just will not connect to my wifi box (supplied by O2).

Thanks
Crispy

---

### Post by FBoeckle on 2009-05-07
Hi,

I also need a vpn connection to my university. With Linux I use vpnc (available from repository) instead of the Cisco version. It is compatible, when using windows, I go over cisco, so I guess your vpn should also work over vpnc.


I had to configure a file in /etc/vpnc: 

> 
Interface name tun0
IKE DH Group dh2
Perfect Forward Secrecy nopfs
IPSec gateway <vpn.adress.org>
IPSec ID <ID>
IPSec secret <IPSec-code>
Xauth username <user>This file was saved as default.conf

I'm not sure the 3 first lines are global or specifically needed for my university...

Then I needed a samba-client, which you also find on repositories.

At last, when I connect I run the following script (from terminal) : 

name : vpnconnect.sh
> #!/bin/bash

sudo vpnc
smbclient -U <usergrour/user> -L <servername>
sudo mount -t smbfs -o username=<user> //<servername>/<directory> /<local>/<path>

exit 0hope this helps you a bit further.

Florian

---

### Post by Crispygb on 2009-05-08
> **FBoeckle said:**
> Hi,

I also need a vpn connection to my university. With Linux I use vpnc (available from repository) instead of the Cisco version. It is compatible, when using windows, I go over cisco, so I guess your vpn should also work over vpnc.


I had to configure a file in /etc/vpnc: 

This file was saved as default.conf

I'm not sure the 3 first lines are global or specifically needed for my university...

Then I needed a samba-client, which you also find on repositories.

At last, when I connect I run the following script (from terminal) : 

name : vpnconnect.sh
hope this helps you a bit further.

Florian

Hi Florian

Many thanks for this.  I'm a bit new to all of this so it needs explaining to me like I'm a 3 year old!

Do I just need to cut and paste your instructions into a terminal window?  I've installed vnpc in the repository, but haven't got it to work yet.

Any help gratefully received!

---

### Post by FBoeckle on 2009-05-14
To make vpnc work, you have to use the correct configuration file. It depends from school to school.

Here's an example of the configuration file from my school ( Filepath /etc/vpnc/default.conf  )

>   Interface name tun0
  IKE DH Group dh2
  Perfect Forward Secrecy nopfs
  IPSec gateway vpn.zhaw.ch
  IPSec ID ZHW
  IPSec secret **GROUP-PASSWORD**
  Xauth username **USERNAME**

Maybe you can use this as example, but for further infos you should ask ppl from your school, maybe the IT department.

Hope it helps

---

### Post by dwayne.hale on 2009-06-02
@crispygb 
There should have been a web setup option on the AnyConnect homepage of the univeristy. You will need to download the vpnsetup.sh file from the site. Click AnyConnect, let it do its web detection thing then it will prompt you with a link "Linuxi386" Click that link to download the vpnsetup.sh file.
Download it to your desktop. Right click the file once downloaded and go to the permissions tabs and click "Allow Executing File as a program". After you close that menu, open a terminal from Applications>Applications>Terminal. Type in "cd ./Desktop" and hit enter.
Type "sudo sh ./vpnsetup.sh" you will be prompted for your password and then everything should install fine.
The VPN Client should be under the Internet tab on the Applications page.
Happy Ubunting!
This is assuming you have the 32 bit version which is most commonly used and that the university has a active directory and terminal server set up in order to remote desktop into Windows XP.

---

### Post by dwayne.hale on 2009-06-02
> **dwayne.hale said:**
> @crispygb 
There should have been a web setup option on the AnyConnect homepage of the univeristy. You will need to download the vpnsetup.sh file from the site. Click AnyConnect, let it do its web detection thing then it will prompt you with a link "Linuxi386" Click that link to download the vpnsetup.sh file.
Download it to your desktop. Right click the file once downloaded and go to the permissions tabs and click "Allow Executing File as a program". After you close that menu, open a terminal from Applications>Applications>Terminal. Type in "cd ./Desktop" and hit enter.
Type "sudo sh ./vpnsetup.sh" you will be prompted for your password and then everything should install fine.
The VPN Client should be under the Internet tab on the Applications page.
Happy Ubunting!

Sorry should have been "Applications>Accessories>Terminal

---

### Post by nusigmaforce on 2009-07-05
Thank you dwayne.hale. 

Now, how do I have the Cisco Anyconnect VPN service start at boot?

I need to install the vpnsetup.sh every time I boot. If not, I get the following error messages:
"VPN Service not available"
"Failed to initialize VPN API, aborting"

---

### Post by dwayne.hale on 2009-08-12
hmmm. sounds like it may be a problem with your install, I've never had to re-install it every time I wanted to run it, and this was on both 64bit and 32bit of 9.04. Try "sudo apt-get autoremove" , after it has removed whatever orphaned files are on your machine then try re-installing the VPN service, that is unless of course your company uses products like DeepFreeze to wipe it back to original anytime the machine is turned off or logged out of.

---

### Post by State on 2009-10-31
hey ... old thread ... but if someone has the same problem ( "VPN Service not available" )

the setup starts vpnagentd but it does not start while booting ...

Solution:
```
sudo /etc/init.d/vpnagentd_init start
```

or better

```
sudo su
cd /etc/rc4.d/
ln -s ../init.d/vpnagentd_init S99vpnagentd
cp S99vpnagentd ../rc3.d/
cp S99vpnagentd ../rc2.d/
cp S99vpnagentd ../rc5.d/
cp S99vpnagentd ../rc6.d/K99vpnagentd
reboot
```

---

### Post by nusigmaforce on 2009-12-02
Awesome. It worked!!!
Thanks!

---

