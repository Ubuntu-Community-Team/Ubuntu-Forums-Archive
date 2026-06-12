---
title: "update manager behind proxy not working in 10.10"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by John.Gateley on 2010-12-10
Hi,

I was having trouble getting update-manager to work behind a proxy (without authentication). I tried everything I could find in my search, including setting http_proxy environment variable, setting the System->Preferences->Network Proxy and setting the Synaptic package manager proxy settings. Nothing seemed to work.

It turns out that the problem was that the System->Preferences->Network Proxy allows "automatic" proxy (pac file), and I had used that. update-manager doesn't do anything with this setting I guess. I changed from the automatic setting to a host/port manual setting and it began working.

I suspect this qualifies as a bug. update-manager should do something more reasonable than quietly fail if the settings are for automatic - it would be really nice if it worked, and if not then an error message.

Hope this helps someone else

John

---

### Post by pilap82 on 2011-01-12
Hi,

if that can help, I had the same issue.

It turns out that what I put in the "Network Proxy" was not properly applied in the /etc/apt/apt.conf file.

there was a line to setup the proxy, but it didn't get the authentication bit.

so i edited the proxy lines as follow:
Acquire::http::proxy "http://username:password@proxy:port/";
(username without the domain if you have one) and it worked.

the bad news is if you have special characters in your password, it will screw up everything :)

hth
Pierre

---

### Post by BasDoot on 2011-01-17
I had the same problem as the OP in my Ubuntu 10.10: I had to use proxy (without authentication), but UM didn't work. Web and Synaptic worked fine. I had previously used automatic proxy config script in Preferences -> Network Proxy, but I had disabled it and used manual configuration instead. 

The thing that worked for me was enabling the autoconfig script, emptying the text field for the address, applying system-wide, then enabling the manual config and again applying system-wide. It seems that for some reason the autoconfig was (unsuccessfully) used, even though it was disabled.

I hope this helps someone else with the same problem.

---

### Post by benoliver999 on 2011-02-05
BasDoot you just solved an two-week old problem. You are a lifesaver.

If only it weren't so simple then I wouldn't feel so stupid...

---

### Post by xlearner on 2011-02-25
Basdoot & benoliver999

I am facing the same problem with update-manager. But I am not clear about the solution suggested by Basdoot. Can you please explain how to access the autoconf script and make the necessary changes? It will greatly help me.

Thanks a lot for your help!

---

### Post by bronkman on 2011-03-17
Go to Applications > Accessories > Terminal
Type: sudo gedit /etc/apt/apt.conf
You may be prompted for password.
Modify the following accordingly with your details:
```
Acquire::http::proxy "http://username:password@proxy:port/";
```

---

