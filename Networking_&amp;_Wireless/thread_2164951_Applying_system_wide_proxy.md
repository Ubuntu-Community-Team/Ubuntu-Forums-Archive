---
title: "Applying system wide proxy"
date: 2013-08-02
forum: Networking &amp; Wireless
---

### Post by vicke4 on 2013-08-02
Hi all,
I am using my college's wlan connection for browsing and downloading but for updating and installing new packages using software center I have a problem while configuring network proxy to apply system wide proxy.I followed the below links but both of them are not working for me......
What should I do to fix this problem???? 
[URL="http://askubuntu.com/questions/3807/how-to-check-if-network-proxy-is-really-applied"]
http://askubuntu.com/questions/3807/how-to-check-if-network-proxy-is-really-applied[/URL]

[http://askubuntu.com/questions/82880/how-do-i-set-a-system-wide-proxy-with-a-username-and-password](http://askubuntu.com/questions/82880/how-do-i-set-a-system-wide-proxy-with-a-username-and-password)

---

### Post by bapoumba on 2013-08-02
Please see here : [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)
What kind of proxy is it ? Some are trickier than others, such as ISA proxies : [http://ubuntuforums.org/showthread.php?t=1802306](http://ubuntuforums.org/showthread.php?t=1802306)
You may have to ask your network admin what kind of proxy they use.

---

### Post by vicke4 on 2013-08-03
I followed all the procedures (step 10) in the following guide....
[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

Still I couldn't fix the problem.In our college they are using SonicWALL-Net Security Appliance......
And the following is the output when I try to install firefox........

```
vicky@Vicky-HP-ProBook-4520s:~$ sudo apt-get install firefox[sudo] password for vicky: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox-globalmenu
Suggested packages:
  ttf-lyx firefox-gnome-support
The following NEW packages will be installed:
  firefox firefox-globalmenu
0 upgraded, 2 newly installed, 0 to remove and 358 not upgraded.
Need to get 26.5 MB of archives.
After this operation, 55.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  firefox firefox-globalmenu
Install these packages without verification [y/N]? y
Err http://in.archive.ubuntu.com/ubuntu/ precise-updates/main firefox i386 22.0+build2-0ubuntu0.12.04.2
  Something wicked happened resolving '<172.16.16.16>:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com/ubuntu/ precise-security/main firefox i386 22.0+build2-0ubuntu0.12.04.2
  Something wicked happened resolving '<172.16.16.16>:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com/ubuntu/ precise-security/main firefox-globalmenu i386 22.0+build2-0ubuntu0.12.04.2
  Something wicked happened resolving '<172.16.16.16>:http' (-5 - No address associated with hostname)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_22.0+build2-0ubuntu0.12.04.2_i386.deb  Something wicked happened resolving '<172.16.16.16>:http' (-5 - No address associated with hostname)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_22.0+build2-0ubuntu0.12.04.2_i386.deb  Something wicked happened resolving '<172.16.16.16>:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



```

Thanks for the Reply.

---

### Post by bapoumba on 2013-08-03
May be here ?
[http://ubuntuforums.org/showthread.php?t=2070530](http://ubuntuforums.org/showthread.php?t=2070530)

---

### Post by vicke4 on 2013-08-03
I've edited the IPV4 settings and changed the DNS severs still the problem persists...
I think my college's firewall is refusing such connections(system update,apt-get,software center)......

---

### Post by bapoumba on 2013-08-03
Hmm, may be.. At my univ, they still have the old proxy up and running that works. I cannot use the new auto-woodoo one they set up a couple years ago. Asked them not to drop the old one, and so far they have no intension to..

---

### Post by vicke4 on 2013-08-03
So there is no way ah????

---

### Post by bapoumba on 2013-08-03
May be you should ask your network admins what kind of proxy they use (that is why I asked in the first place). With some proxy types, there are some workarounds.

---

### Post by vicke4 on 2013-08-03
Okay thank you I'll try to retrieve the required infos soon....

---

### Post by bapoumba on 2013-08-03
This is what I used long ago, still working: [https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)
On the newer proxy (with login/passwd and other things I did not understand in details), it has never worked. Sysadmins here are using Linux, so that helped :)

---

### Post by vicke4 on 2013-08-07
> **bapoumba said:**
> This is what I used long ago, still working: [https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)
On the newer proxy (with login/passwd and other things I did not understand in details), it has never worked. Sysadmins here are using Linux, so that helped :)

That guide also not worked........:(

---

### Post by vicke4 on 2013-08-15
Finally,I asked the lab technician for solution.He asked me to add proper proxy setting to /etc/apt/apt.conf.Now my problem is fixed...:p

---

### Post by bapoumba on 2013-08-15
> **vicke4 said:**
> Finally,I asked the lab technician for solution.He asked me to add proper proxy setting to /etc/apt/apt.conf.Now my problem is fixed...:p
Good, happy you got it to work (and yes, I had to talk to the sysadmins here too, they ended up just keeping the old proxy around. I suspect they use it too).

---

