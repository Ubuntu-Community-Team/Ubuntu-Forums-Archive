---
title: "Configuring Samba Shares"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by TehKivin on 2010-03-14
Hi all,

My samba daemon is currently configured adequately to give me access to folder **~**.
I wish to have a share available which routes to **/var/www** for web sharing.

However, I have having issues with authentication.
When I choose the 'kivin-root' share from my Windows Networking screen, I'm prompted for a user/pass.  Entering 'root' & my su password gains me admittance here.

For the purposes of /var/www, I have included the following in my samba.conf:

```
[www]
comment = www directory
path = /var/www
public = yes
writable = yes
valid users = kivin
create mask = 0771
directory mask = 0771
force user = kivin
force group = www-users
```And I have performed the following commands on the terminal:

```
sudo addgroup www-users
sudo adduser kivin www-users

sudo chown -R root:www-users /var/www
sudo chmod -R 771 /var/www
```When I select the www share from Windows, I enter 'kivin' as the user and my ubuntu sign on password.

The response is:

```
\\KIVIN-LAPTOP\www is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions
```

edit:

My user 'kivin' does not seem to have permissions to view /var/www and attempts to visit this folder in Nautilus fail.  Could this be why?

---

