---
title: "Offline auth. with Kerberos and timeouts (pam_krb5.so, pam_ccreds.so)"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by pirx666 on 2009-07-06
Hi,                                                                                                                          

I'm trying to setup authentication with kerberos (Active Directory) for some Ubuntu and Debian Clients.   

This is working fine, except for offline logins (Laptops). In this case I always get an login timeout.
                                                                                                                             
                                                                                                                                                                                                
Some things I found with google:
                                                                                                       
[https://wiki.ubuntu.com/NetworkAuthentication/Client?highlight=(pam\_ccreds.so)#PAM]("https://wiki.ubuntu.com/NetworkAuthentication/Client?highlight=%28pam%5C_ccreds.so%29#PAM")                                            
[http://www.klabs.be/~fpiat/linux/debian/Disconnected_Authentication.html]("http://www.klabs.be/%7Efpiat/linux/debian/Disconnected_Authentication.html")                                                        
                                                                                                                                
my common-auth for pam:

 ```
       
auth [success=done default=ignore] pam_unix.so debug                                                                            
auth [authinfo_unavail=ignore success=1 default=2] pam_krb5.so use_first_pass minimum_uid=1000 debug                            
auth [default=done] pam_ccreds.so action=validate use_first_pass                                                                
auth [default=done] pam_ccreds.so action=store                                                                                  
auth [default=bad] pam_ccreds.so action=update                                                                                  
auth requisite                       pam_deny.so                                                                                
auth required                        pam_permit.so 
 
```With this an offline login always fails with the message "Login timed out after 60 seconds".   


auth.log:                                                                            

 ```
                                                                                                                              
Jul  6 10:42:04 foo login[24712]: pam_unix(login:auth): authentication failure; logname=myuser uid=0 uid=0 tty=tty3 ruser= rhos
Jul  6 10:42:04 foo login[24712]: (pam_krb5): none: pam_sm_authenticate: entry (0x0)                                            
Jul  6 10:42:04 foo login[24712]: (pam_krb5): myuser: attempting authentication as myuser@foobarblub666.net

```Changing the value for the kdc_timeout in krb5.conf didn't change anything.

```
                                                                                                                
[appdefaults]                                                                                                                   
pam = {                                                                                                                         
   debug = true                                                                                                                 
   ticket_lifetime = 36000                                                                                                      
   renew_lifetime = 36000                                                                                                       
   forwardable = true                                                                                                           
   krb4_convert = false                                                                                                         
   kdc_timeout = 5                                                                                                              
   max_retries = 1                                                                                                              
}                          

```Online login with kerberos and pam_ccreds is working fine.                                                                                       
                                                                                                                                
```
                                                                                                                                
Jul  6 10:58:07 foo sshd[26016]: (pam_krb5): myusere: attempting authentication as myusere@foobarblub666.net                    
Jul  6 10:58:07 foo sshd[26016]: (pam_krb5): myusere: pam_sm_authenticate: exit (success)                                       
Jul  6 10:58:07 foo sshd[26016]: (pam_krb5): myusere: pam_sm_acct_mgmt: entry (0x0)                                             
Jul  6 10:58:07 foo sshd[26016]: (pam_krb5): myusere: retrieving principal from cache                                           
Jul  6 10:58:07 foo sshd[26016]: (pam_krb5): myusere: pam_sm_acct_mgmt: exit (success)                                          
Jul  6 10:58:07 foo sshd[26016]: Accepted password for myusere from 192.168.1.254 port 55154 ssh2                               
Jul  6 10:58:07 foo sshd[26016]: (pam_krb5): myusere: pam_sm_setcred: entry (0x2)                                               
Jul  6 10:58:07 foo sshd[26016]: (pam_krb5): myusere: initializing ticket cache FILE:/tmp/krb5cc_1000_LzpSNP                    
Jul  6 10:58:07 foo sshd[26016]: (pam_krb5): myusere: pam_sm_setcred: exit (success)                                            
Jul  6 10:58:07 foo sshd[26016]: (pam_krb5): myusere: pam_sm_setcred: entry (0x2)                                               
Jul  6 10:58:07 foo sshd[26016]: (pam_krb5): myusere: pam_sm_setcred: exit (success)                                            
Jul  6 10:58:07 foo sshd[26016]: pam_unix(sshd:session): session opened for user myusere by (uid=0)                             
Jul  6 10:58:07 foo sshd[26027]: (pam_krb5): myusere: pam_sm_setcred: entry (0x2)                                               
Jul  6 10:58:07 foo sshd[26027]: (pam_krb5): myusere: pam_sm_setcred: exit (success)                                            
 
```Any ideas what to do to not run into the 60 second timeout?

---

### Post by tokarbol on 2010-08-19
I stumbled upon this problem trying to do the exact same thing - offline logons.
The pam_ccreds seems cool to use, but pam_krb5 waits forever.
I found that to be a problem with DNS timeouts.
See [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=315622](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=315622) and [http://krbdev.mit.edu/rt/Ticket/Display.html?id=4114](http://krbdev.mit.edu/rt/Ticket/Display.html?id=4114)

Apparently, this is a bug and seems not to be solved in upstream yet.

I tried to find a workaround for this.
I entered the KDC and realm details to /etc/krb5.conf not to rely on DNS SRV records.
Then, I put the KDCs into my /etc/hosts file.
This shortens the time taken by pam_krb5 ~30s when disconnected.
Thus, I could login when disconnected.

We are using AD here, so I was able to also use pam_ldap.
This one seems to take less time (but still too long when you use DNS names).
You either put IPs to /etc/ldap.conf or to /etc/hosts.
I had to use /etc/hosts, as we are using SSL port 636 which fails when certificate name does not match the server name (in this case, an IP address).

pam_ldap takes much less time, you can get a failed logon in 5s.
However, you loose the kerberos tickets and cannot use SSO.
So I figured out I would put this into /etc/pam.d/common-auth:
```

auth    [success=done default=ignore]   pam_unix.so nullok_secure
auth    [success=ignore default=1] pam_ldap.so use_first_pass
auth    [authinfo_unavail=ignore success=2 default=3] pam_krb5.so use_first_pass minimum_uid=1000
auth    [default=done]  pam_ccreds.so action=validate use_first_pass
auth    [default=done]  pam_ccreds.so action=store
auth    [default=bad]   pam_ccreds.so action=update

```What it does: First, it tries local auth (fast), then tries logging in to LDAP.
If it succeeds, it continues (success=ignore) to Kerberos, using the same password,
which should succeed and get the user a Kerberos ticket and stuff.
On any LDAP error (default=1) it skips the kerberos auth to try the cached credentials.

We are going to give this config a couple of tests.
I would appreciate any suggestions as to the workaround.
I know it is not cool and using winbind offline logon is tempting, but there are even more problems with it.

---

