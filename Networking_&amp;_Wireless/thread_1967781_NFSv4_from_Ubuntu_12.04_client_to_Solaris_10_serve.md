---
title: "NFSv4 from Ubuntu 12.04 client to Solaris 10 server"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by korb on 2012-04-28
Hello,

I just upgraded from 10.04 LTS to 12.04 LTS, and I'm having a problem with NFS-mounted home directories.

In 10.04, the NFS client automatically defaulted to mounting from our Solaris 10 server using NFSv3, and all was (more or less) well. With the upgrade to 12.04, all files are owned by nobody:nogroup. If I mount the filesystems with vers=3, then the ownerships are correct.

While using v3 is a possible work-around, I would prefer to use v4 so as to have access to v4 ACLs, etc. We do not run Kerberos, so at this point, that is not an option.

Note that from Solaris server to Solaris client, this all works as it should with v4.

I looked at the [SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo") page, but this appears to assume Linux as both client and server.

Does anyone have the Linux NFSv4 client working with anything other than a v4 server? Is there any documentation or other resource that can help me figure this out?

Thanks,
Bill

---

