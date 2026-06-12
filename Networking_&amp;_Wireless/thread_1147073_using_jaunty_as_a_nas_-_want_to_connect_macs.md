---
title: "using jaunty as a nas - want to connect macs"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by pedrogent on 2009-05-03
Hello. What I want to do is set up Ubuntu 9.04 AMD64 as a file server. I have a MacBook. I have Jaunty installed on the machine I want to use as the server. I don't need anything special. It'll be a JBOD NAS. It'd be nice (but not essential) if XP machines could also be served up from the Ubuntu NAS.

From my Mac I can easily see & write to XP & Vista partitions. I'm struggling to see partitions in Linux tho'.

I get the feeling that I should be using NFS to achieve my goal (but perhaps I should be using Samba or something else).

I've checked around teh interwebs but I can't find a guide I can understand.

Can anyone point me in the right direction?

Thanks in advance.

---

### Post by jowilkin on 2009-05-03
You should use Samba to allow Windows and Mac to connect, not NFS.  I would also recommend using Ubuntu 8.04 LTS server edition for a server since it should be more stable than 9.04.  It doesn't come with a GUI, but you can install one (i.e. with the "sudo aptitude install ubuntu-desktop" command).

This page may be useful: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by pedrogent on 2009-05-03
Well, seeing as I already have 9.04 installed I can't be bothered putting on the server version you mentioned. I also like GUIs on servers.

In any case, I used [this guide]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/") with good results. In a nutshell it involves compiling netatalk and editing some .conf files.

Could be easier...

---

