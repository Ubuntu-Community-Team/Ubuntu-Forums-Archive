---
title: "Problem with Apt &amp; updates standard stuff no work"
date: 2021-05-26
forum: MINT
---

### Post by covid16 on 2021-05-26
Hello Mr. or Ms. Who Most Likely Know More Than Me,

My basic problem is I can't download software or get updates in Linux Mint Tina when I could before.

I get the apt corrupted line. But the corrections I read about don't appear to work or I am too dense
to be doing it right. 

I did not set a restore point when the laptop was working correctly so yes it was stupid but I was new to Linux
(and still am just started during lockdown).

Below is some info I gathered to get help with or put in a time capsule for future lames. Any help appreciated.

Tried Update Manager 14 April 21 just 1st update on list to simplify:

W: Failed to fetch 
  File has unexpected size (26027 != 9900). Mirror sync in progress? [IP: 209.206.49.21 443]



W: Failed to fetch 
  File has unexpected size (26027 != 82692). Mirror sync in progress? [IP: 209.206.49.21 443


Attempt to refresh list of updates:

```
Failed to fetch [http://archive.ubuntu]("http://archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease")  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)The repository 'http://archive.ubuntu.com/ubuntu bionic-updates InRelease' is no longer signed.Updating from such a repository can't be done securely, and is therefore disabled by default.See apt-secure(8) manpage for repository creation and user configuration details.Failed to fetch [http://archive.ubuntubuntu/dists/bionic-backports/InRelease]("http://archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease")  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)The repository 'http://archive.ubuntu.com/ubuntu bionic-backports InRelease' is no longer signed.
```




TERMINAL try to do update:

```
rand@rand-HP-ProBook-450-G2:~$ apt-get update

Reading package lists... Done
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)
```



```
rand@rand-HP-ProBook-450-G2:~$ sudo apt-get update

sudo password for rand:     
 
Get:1  bionic-security InRelease [26.0 kB]
Err:1 [https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DAF:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://security.ubuntu.com/ubuntu]("https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:03:DF:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://security.ubuntu.com/ubuntu") bionic-security InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:2 [https://n177.network-authh/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:F:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://archive.ubuntu.com/ubuntu]("https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:03:DF:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://archive.ubuntu.com/ubuntu") bionic InRelease [26.0 kB
Err:2 [https://n177.network-aut?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:F:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://archive.ubuntu.com/ubuntu]("https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:03:DF:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://archive.ubuntu.com/ubuntu") bionic InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:3 [https://n177.networlash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:03:DF:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://archive.canonical.com/ubuntu]("https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:03:DF:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://archive.canonical.com/ubuntu") bionic InRelease [26.0 kB
Err:3 [https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:03:DF:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://archive.canonical.com/ubuntu](https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:03:DF:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://archive.canonical.com/ubuntu) bionic InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:4 [https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:03:DF:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://mirrors.evowise.com/linuxmint/packages](https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:03:DF:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://mirrors.evowise.com/linuxmint/packages) tina InRelease [26.0 kB
Err:4 [https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:03:DF:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://mirrors.evowise.com/linuxmint/packages](https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:03:DF:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://mirrors.evowise.com/linuxmint/packages) tina InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:5 [https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:03F:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://archive.ubuntu.com/ubuntu]("https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:03:DF:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://archive.ubuntu.com/ubuntu") bionic-updates InRelease [26.0 kB]
Err:5 [https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:0F:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://archive.ubuntu.com/ubuntu]("https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:03:DF:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://archive.ubuntu.com/ubuntu") bionic-updates InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:6 [https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:F:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://archive.ubuntu.com/ubuntu]("https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:03:DF:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://archive.ubuntu.com/ubuntu") bionic-backports InRelease [26.0 kB]
Err:6 [https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:0F:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://archive.ubuntu.com/ubuntu]("https://n177.network-auth.com/splash/?mac=98:18:88:C7:6E:43&real_ip=10.40.237.61&client_ip=10.40.237.61&client_mac=DA:03:DF:1B:2C:38&vap=0&a=c1dfd96eea8cc2b62785275bca38ac261256e278&b=3657257&auth_version=5&key=b41ed7ee31e8de9b6cc5b32628ec34baa4948013&acl_ver=P10733388V2&continue_url=http://archive.ubuntu.com/ubuntu") bionic-backports InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Reading package lists... Done       
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://security.ubuntu.com/ubuntu bionic-security InRelease' is no longer signed.
E: Failed to fetch [http://security.ubuntuubuntu/dists/bionic-security/InRelease]("http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease")  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' is no longer signed.
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/bionic/InRelease](http://archive.ubuntu.com/ubuntu/dists/bionic/InRelease)  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://archive.canonical.com/ubuntu bionic InRelease' is no longer signed.
E: Failed to fetch [http://archive.canonicalubuntu/dists/bionic/InRelease]("http://archive.canonical.com/ubuntu/dists/bionic/InRelease")  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://mirrors.evowise.com/linuxmint/packages tina InRelease' is no longer signed.
E: Failed to fetch [http://mirrors.evowise.com/linuxmint/packages/dists/tina/InRelease](http://mirrors.evowise.com/linuxmint/packages/dists/tina/InRelease)  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease)  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://archive.ubuntu.com/ubuntu bionic-updates InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease)  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://archive.ubuntu.com/ubuntu bionic-backports InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
rand@rand-HP-ProBook-450-G2:~$
```

---

### Post by jeremy31 on 2021-05-26
Moved to Mint
Open the Software Update program and try changing the mirror

---

### Post by covid16 on 2021-05-29
Thanks for advice. I don't have regular internet access so that is why the wait.

I tried to switch mirrors. I got "Failed to download repository information"

---

