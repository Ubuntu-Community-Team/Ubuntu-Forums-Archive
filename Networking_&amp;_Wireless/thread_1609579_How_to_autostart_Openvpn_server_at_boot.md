---
title: "How to autostart Openvpn server at boot ?"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by Bacaryu on 2010-10-30
Hi 

I configured succesfully openvpn server, but the service won't start at boot !
I thought openvpn automatically starts al the *.conf files in the /etc/openvpn folder ?

on my personal laptop the service automatically starts all the .conf files in the folder. But on my server with server.conf file it won't start at boot. I have to start the service as root

---

### Post by SeijiSensei on 2010-10-31
[Openvpn]("https://answers.launchpad.net/ubuntu/+source/chkconfig/+question/117028") seems to be one of the services now in "no-man's land" since the arrival of the [upstart]("http://upstart.ubuntu.com/") service manager.  A quick test of 10.04 server installation shows that this approach works, though:

```
sudo update-rc.d openvpn enable 2345
```

That will build the symlinks between /etc/init.d/openvpn and the run-level directories /etc/rc*.d/.

You'd think that the developers would have systematically recreated all the existing daemon service scripts to run with upstart by now.  "sudo initctl list" provides a list of all services controlled by upstart; I didn't see openvpn there.

---

