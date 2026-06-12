---
title: "[SOLVED] cant update using terminal"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by monkey186 on 2009-01-06
hello, i have a little problem in xubuntu 8.10 - i cannot connect to internet through terminal.

i'm behind proxy, so in synaptic package manager/preferences/network i entered proxy details, and both synaptic and update manager connect to internet and work fine.

but not the terminal for some reason. for example when sudo apt-get update i get:
```
 
Err http://ppa.launchpad.net hardy Release.gpg                                 
  Could not connect to ppa.launchpad.net:80 (91.189.90.217), connection timed out
Err http://ppa.launchpad.net hardy/main Translation-en_US                      
  Unable to connect to ppa.launchpad.net http:
Err http://archive.canonical.com intrepid Release.gpg                          
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err http://archive.canonical.com intrepid/partner Translation-en_US            
  Unable to connect to archive.canonical.com http:
Err http://security.ubuntu.com intrepid-security Release.gpg                   
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err http://security.ubuntu.com intrepid-security/restricted Translation-en_US  
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/main Translation-en_US        
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/multiverse Translation-en_US  
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/universe Translation-en_US    
  Unable to connect to security.ubuntu.com http:
Err http://archive.ubuntu.com intrepid Release.gpg                             
  Could not connect to archive.ubuntu.com:80 (91.189.88.46), connection timed out [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com intrepid/main Translation-en_US
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com intrepid/restricted Translation-en_US
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com intrepid/universe Translation-en_US
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com intrepid/multiverse Translation-en_US
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.46 80]
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg  Could not connect to archive.ubuntu.com:80 (91.189.88.46), connection timed out [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_US.bz2  Unable to connect to archive.canonical.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://ppa.launchpad.net/c-korn/ubuntu/dists/hardy/Release.gpg  Could not connect to ppa.launchpad.net:80 (91.189.90.217), connection timed out

W: Failed to fetch http://ppa.launchpad.net/c-korn/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Unable to connect to ppa.launchpad.net http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

is there anywhere else i have to enter the proxy details, assuming the problem is because of the proxy?

thanks!

---

### Post by monkey186 on 2009-01-07
bump.?

---

### Post by scorp123 on 2009-01-07
The proxy settings in "synaptic" have no effect on the terminal. You can set proxy settings manually for the shell you're in and you could place the same lines into e.g. ~/.bashrc so that these commands are auto-executed whenever you open a shell. The commands:
```
export http_proxy=http://your.proxy.server.here:12345/
export ftp_proxy=http://your.proxy.server.here:12345/
```

Of course ... you'd have to set the correct port above.

When executing the commands above manually they will only take effect for the open terminal session into which these commands were typed in!

---

### Post by monkey186 on 2009-01-07
got it thanks, now all works =D>

---

