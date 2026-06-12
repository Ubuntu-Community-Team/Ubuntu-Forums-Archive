---
title: "Unable to authenticate to Win2k8 R2 DC"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by rawdeal888 on 2011-04-19
All,

Since upgrading to Win2k8 R2 servers I am getting below mentioned errors. I can see all the domain members in wbinfo but I am getting this error when doing ntlm_auth check and smbclient check. This is was finewhen we were using win2k3 servers. I have attached smb.conf as well

sudo smbclient -U Administrator -L 127.0.0.1
session setup failed: NT_STATUS_PIPE_DISCONNECTED

zen@c3netmon01:~$ sudo ntlm_auth --diagnostics --username=abc.xyz
password:
Named pipe dicconnected (0xc00000b0)
[2011/04/15 21:19:22,  1] utils/ntlm_auth_diagnostics.c:600(diagnose_ntlm_auth)
  Test LM failed!
Named pipe dicconnected (0xc00000b0)
[2011/04/15 21:19:22,  1] utils/ntlm_auth_diagnostics.c:600(diagnose_ntlm_auth)
  Test LM and NTLM failed!
Named pipe dicconnected (0xc00000b0)
[2011/04/15 21:19:22,  1] utils/ntlm_auth_diagnostics.c:600(diagnose_ntlm_auth)
  Test NTLM failed!
Named pipe dicconnected (0xc00000b0)
[2011/04/15 21:19:22,  1] utils/ntlm_auth_diagnostics.c:600(diagnose_ntlm_auth)

I would appreciate any help in this regard.

---

