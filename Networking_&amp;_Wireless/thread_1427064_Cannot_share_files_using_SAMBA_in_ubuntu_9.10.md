---
title: "Cannot share files using SAMBA in ubuntu 9.10"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by Shadyabhi on 2010-03-11
When I try to share a folder using Nautilus by right clicking on the Folder & then "Sharing Options", I get the following error..

```
Samba's testparm returned error 1: Loaded smb config files from --parameter-name=usershare allow guests
lp_load: refreshing parameters from --parameter-name=usershare allow guests
params.c:OpenConfFile() - Unable to open configuration file "--parameter-name=usershare allow guests":
	No such file or directory
Error loading services.

```
[IMG]http://docs.google.com/uc?id=0Bz5PTCmbPL4aYzIyMTY3MmEtYWNiNS00ZjVhLTg2N2YtYzg5YzJhZTUyMTdh&hl=en[/IMG]
I have the followng packages installed..

```
shadyabhi@shadyabhi-desktop:~$ dpkg --get-selections samba*
samba                                           install
samba-common                                    install
samba-common-bin                                install
samba4-common-bin                               install
shadyabhi@shadyabhi-desktop:~$

```

---

