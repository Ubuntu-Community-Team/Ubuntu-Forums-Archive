---
title: "Samba shares are accessible, but not from Windows Explorer"
date: 2013-06-10
forum: Networking &amp; Wireless
---

### Post by PL04Mgt on 2013-06-10
I have a samba share on a Ubuntu server. The share uses a domain authentication (Domain controller is somewhere else). Everything works almost fine: I can access this share from Windows using command line, Total Commander, even Firefox or any other program that can open files and read directories. All access rights are properly negotiated, files can be read/written if a user have proper permissions.

However, when a user tries to open a network share path in a file browser called Windows Explorer (don't mix it up with Internet Explorer, Windows Explorer is what shows you folders content in Windows, most Windows users use it, however don't know how it is called) it says that the user doesn't have permissions to access the correspondent folder.

In samba log I see this:
```
[2013/06/09 21:09:17.754432, 10] smbd/open.c:2717(open_directory)
  open_directory: smbd_check_open_rights on file dirname failed with NT_STATUS_ACCESS_DENIED
[2013/06/09 21:09:17.754466, 10] smbd/open.c:3423(create_file_unixpath)
  create_file_unixpath: NT_STATUS_ACCESS_DENIED
[2013/06/09 21:09:17.754496, 10] smbd/open.c:3696(create_file_default)
  create_file: NT_STATUS_ACCESS_DENIED
[2013/06/09 21:09:17.754526,  3] smbd/error.c:81(error_packet_set)
  error packet at smbd/error.c(161) cmd=162 (SMBntcreateX) NT_STATUS_ACCESS_DENIED

```

---

### Post by PL04Mgt on 2013-06-14
Since google search and this forum failed to help with this issue, I  downloaded the source code of samba (with "apt-get source samba") and  compiled it with debug symbols in a hope to debug the problem with gdb.  To my utter surprise the compiled version works just fine! "apt-get  source" supposedly has to provide me the same sources that were used to  produce the binaries I installed with "apt-get install", doesn't it? Why  the behavior is different?

---

### Post by bab1 on 2013-06-14
> **Nox Metus said:**
> Since google search and this forum failed to help with this issue, I  downloaded the source code of samba (with "apt-get source samba") and  compiled it with debug symbols in a hope to debug the problem with gdb.  To my utter surprise the compiled version works just fine! "apt-get  source" supposedly has to provide me the same sources that were used to  produce the binaries I installed with "apt-get install", doesn't it? Why  the behavior is different?

The source code is the same.  The packager maintainer did not have to use the same make file defaults as you.

---

### Post by PL04Mgt on 2013-06-14
Is there any chance to check what build options were used by the package maintainer? I guess I should file a bug.

---

### Post by bab1 on 2013-06-14
> **Nox Metus said:**
> Is there any chance to check what build options were used by the package maintainer? I guess I should file a bug.

I would ask the maintainer.  Pick the proper Ubuntu version [**[COLOR="#FF8C00"]here[/COLOR]**]("http://packages.ubuntu.com/search?keywords=samba"). Why would you file a bug report?  Did you try and diagnose the problem?  My guess is it is a configuration parameter.  Everything Samba3 is configured at smb.conf. No one could set up the defaults that will satisfy all users.  Have you posted this *problem* at the samba.org mailing list?

---

### Post by PL04Mgt on 2013-06-16
> **bab1 said:**
> Why would you file a bug report?  Did you try and diagnose the problem?It depends on what you mean by “diagnose”. I see the problem, I can reproduce it at least on 2 client PCs in my company. I failed to debug it though, since the debug version I compiled myself works fine.

> **bab1 said:**
> My guess is it is a configuration parameter.   Everything Samba3 is configured at smb.conf. No one could set up the  defaults that will satisfy all users.This smb.cong works fine with the debug version. And the version deployed with OS has problems only with Windows Explorer. So I doubt it's configuration.

> **bab1 said:**
> Have you posted this *problem* at the samba.org mailing list?I haven't. I'll try. Thank you for the advice.

---

