---
title: "Problems joining ADS Domain , Cross Domain Autentication, likewise"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by mreggiardo on 2009-09-01
hello all, make someone can help me, I'll make a post of the problem as we put in another place.
 
This is the history
 
I cant join an Ubuntu 9.04 machine to a domain. 
Details are: 
* I am trying to join a domain that is not the root of the forest. 
* I am using an account that is from another domain in the same forest. 
* The account I am using does not have rights to create a computer account, but the account was already created by an administrator an delegated to me rights to join it. 
* I try joining another domain (where I am Domain Admin) and it work ok. The big difference was that I am domain admin of this other domain and that this domain is the root and the only one in the forest. 
The command I am trying to use is:  domainjoin-cli --loglevel verbose join --ou >  
Servers/Sales/UK FOO.DOMAIN.NET [EMAIL="MYACCOUNT@DUMMY.DOMAIN.NET"][COLOR=#083e61]MYACCOUNT@DUMMY.DOMAIN.NET[/COLOR][/EMAIL] 
The log output near the error is: 
[2009/08/30 00:54:53, 3] libads/sasl.c:ads_sasl_spnego_bind(787) 
ads_sasl_spnego_bind: got server principal name = domcont1$@FOO.DOMAIN.NET 
[2009/08/30 00:54:53, 3] libsmb/clikrb5.c:ads_krb5_mk_req(657) 
ads_krb5_mk_req: krb5_cc_get_principal failed (No credentials cache found) 
[2009/08/30 00:54:53, 10] libads/sasl.c:ads_sasl_spnego_bind(808) 
ads_sasl_spnego_krb5_bind failed with: No credentials cache found, calling kinit 
[2009/08/30 00:54:53, 10] libads/kerberos.c:kerberos_kinit_password_ext(217) 
kerberos_kinit_password: as [EMAIL="MYACCOUNT@DUMMY.DOMAIN.NET"][COLOR=#083e61]MYACCOUNT@DUMMY.DOMAIN.NET[/COLOR][/EMAIL] using [MEMORY:net_ads] as ccache and config [/var/lib/likewise-open/smb_krb5/krb5.conf.WORKGROUP] 
[2009/08/30 00:54:53, 1] libsmb/clikrb5.c:ads_krb5_mk_req(666) 
ads_krb5_mk_req: krb5_get_credentials failed for domcont1$@FOO.DOMAIN.NET (Server not found in Kerberos database) 
[2009/08/30 00:54:53, 0] libads/sasl.c:ads_sasl_spnego_bind(817) 
kinit succeeded but ads_sasl_spnego_krb5_bind failed: Server not found in Kerberos database 
[2009/08/30 00:54:53, 1] utils/net_ads.c:net_ads_join(1791) 
error on ads_startup: Server not found in Kerberos database 
[2009/08/30 00:54:53, 10] intl/lang_tdb.c:lang_tdb_init(134) 
lang_tdb_init: /usr/lib/likewise-open/en_US.UTF-8.msg: No such file or directory 
[2009/08/30 00:54:53, 2] utils/net.c:main(1178) 
return code = -1 

 
 
Tried upgrading to the last release from likewise-open… 
Now the error is… 
```
 
Joining to AD Domain:  MYDOMAIN.MYORG.NET 
With Computer DNS Name: hostname.mydomain.myorg.net 
[EMAIL="MYUSER@MYOTHERDOMAIN.MYORG.NET"]MYUSER@MYOTHERDOMAIN.MYORG.NET[/EMAIL]’s password: 
Error: Lsass Error [code 0x00080047] 
0x3B - Bad font file format 

```
BTW: I still can join to domain where I am Domain Admin. 
 
In this last case… there are syslog entries related to the problem: 
```
 
Aug 30 16:47:37 sidd00206138 lwiod[3191]: GSS-API error calling gss_init_sec_context: -1765328377 (Server not found in Kerberos database) 
Aug 30 16:47:43 sidd00206138 lwiod[3191]: GSS-API error calling gss_init_sec_context: 851968 (Unspecified GSS failure.  Minor code may provide more information) 
Aug 30 16:47:43 sidd00206138 lwiod[3191]: GSS-API error calling gss_init_sec_context: -1765328377 (Server not found in Kerberos database) 
Aug 30 16:47:48 sidd00206138 lwiod[3191]: GSS-API error calling gss_init_sec_context: 851968 (Unspecified GSS failure.  Minor code may provide more information) 
Aug 30 16:47:48 sidd00206138 lwiod[3191]: GSS-API error calling gss_init_sec_context: -1765328377 (Server not found in Kerberos database) 
Aug 30 16:47:50 sidd00206138 lwiod[3191]: GSS-API error calling gss_init_sec_context: 851968 (Unspecified GSS failure.  Minor code may provide more information) 
Aug 30 16:47:50 sidd00206138 lwiod[3191]: GSS-API error calling gss_init_sec_context: -1765328377 (Server not found in Kerberos database) 

```
 
This happens while trying to join to the domain. 
 
It seems the recurring error is always Server not found in Kerberos database
 
 
I Added capaths to krb5.conf and now I get this error: 
```
 
20090831234618:ERROR:Lsass Error [CENTERROR_DOMAINJOIN_LSASS_ERROR] 
0x5 - Input/output error 
Stack Trace: 
main.c:885 
main.c:455 
djmodule.c:319 
djauthinfo.c:752 
djauthinfo.c:1082 
Any idea what does it mean? 

```
Please if any have a clue what can be wrong… i would appreciate any suggestion.

---

### Post by mreggiardo on 2009-09-05
Well finally we do it, installing the unstable branch likewise open 5.3 , and works fine
But now i've another problem..
We are autenticating apache2 with pam serving a svn repository. and the acces is really 
slow.
Every time i acces the svn repository , apache start authenticating the user and the lsassd start consuming about 20% of the CPU and the operation take around 5 seconds.

Do anyone have any idea how to speed up the likewise authentication. is a very big domain and is really painfull accesing the repository.

thanks in advance

---

