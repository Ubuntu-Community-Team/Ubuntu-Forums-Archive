---
title: "Several problems about Likewise Open and AD domain."
date: 2013-05-25
forum: Networking &amp; Wireless
---

### Post by macarthor on 2013-05-25
Hi all,

I don't know if the post is suitable for this forum, but I cannot find the Likewise Open project support or forum or mailing list...

Recently I'm working with Likewise Open and Windows Server 2008 R2 AD domain. Here's problems I met. Any help would be appreciated!

1. I use 2 PC installing ubuntu 12.04, with the same hostname "ubuntu". On both PCs, I join to an AD domain "nps.test" with command "sudo domainjoin-cli join nps.test npsadmin some_password", and both joined OK. But when I get machine passwords, the passwords are different on these PCs: "sudo lw-lsa ad-get-machine password nps.test". The output are:
```

Machine Password Info:
  DNS Domain Name: NPS.TEST
  NetBIOS Domain Name: NPS
  Domain SID: S-1-5-21-3509232304-4000530708-2500345567
  SAM Account Name: UBUNTU$
  FQDN: ubuntu.nps.test
  Account Flags: 0x00000001 (1)
  Key Version: 1
  Last Change Time: 130139344070000000
  Password: /92NG'd11r8;t()( 

```

```

Machine Password Info:
  DNS Domain Name: NPS.TEST
  NetBIOS Domain Name: NPS
  Domain SID: S-1-5-21-3509232304-4000530708-2500345567
  SAM Account Name: UBUNTU$
  FQDN: ubuntu.nps.test
  Account Flags: 0x00000001 (1)
  Key Version: 2
  Last Change Time: 130139323780000000
  Password: -xt7Ui8P(%12=ixv 

```
Note, "Key Version" field is different. When I use these password for 802.1x authentication for respective PCs, the previously joined PC failed to authenticate, and the later joined PC succeeded to authenticate. That is, the later join action generates new machine password at AD domain. BUT, the first PC also gets older password. So, can Likewise Open clear machine password cache and re-get new password from AD domain?

2. For AD domain, one computer account ("ubuntu.nps.test") has various key version numbers, and one key version number seems to be bind to MAC address of joined machine - it's different for every join action. Any further information about AD domain and key version number?

---

