---
title: "Proxy Settings on 10.04: No way to enter authentication details"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by udippel on 2010-05-06
[Out of all those wireless problems ... ;)  )
Here is a 'wired' problem: I need to enter credentials for a system wide proxy, on a fresh install of Kubuntu 10.04. Everything hunky dory, but: Network Settings->Proxy->Authorization has 'username:' and 'password' grayed out all the time; even at 'Manually specify ...'. The only 'alternative' (not to chose from) is 'Prompt as needed'. But I don't get any prompt, and so I'm out of luck. 
To me, this looks like a bug. Because one should be able to enter a username and a password there, for good.

Uwe

---

### Post by gg234 on 2010-05-07
try this [http://www.ubuntugeek.com/how-to-configure-ubuntu-desktop-to-use-your-proxy-server.html](http://www.ubuntugeek.com/how-to-configure-ubuntu-desktop-to-use-your-proxy-server.html)


> **udippel said:**
> [Out of all those wireless problems ... ;)  )
Here is a 'wired' problem: I need to enter credentials for a system wide proxy, on a fresh install of Kubuntu 10.04. Everything hunky dory, but: Network Settings->Proxy->Authorization has 'username:' and 'password' grayed out all the time; even at 'Manually specify ...'. The only 'alternative' (not to chose from) is 'Prompt as needed'. But I don't get any prompt, and so I'm out of luck. 
To me, this looks like a bug. Because one should be able to enter a username and a password there, for good.

Uwe

---

### Post by udippel on 2010-05-11
> **gg234 said:**
> try this [http://www.ubuntugeek.com/how-to-configure-ubuntu-desktop-to-use-your-proxy-server.html](http://www.ubuntugeek.com/how-to-configure-ubuntu-desktop-to-use-your-proxy-server.html)

No, firstly I am on KDE. Secondly, I tried on Gnome (netbook remix 10.04) and there it also doesn't work. Promised.
The Network Proxy Preferences are on the proxy, with 'Apply System-Wide ...", but wget -d [http://abc.def.com](http://abc.def.com) does not get the data; and there is no mention in the debug context ("-d") of any proxy.

---

### Post by d4y on 2010-05-15
Same problem. Kubuntu 10.04, proxy with authentication, no way to enter login & password and KDE doesn't request them when I try to connect to internet in Konqueror or KPackageKit (haven't tested other KDE apps but think there will be same problem).

---

### Post by Zorael on 2010-05-17
This sounds like it warrants a bug report. Remember, unreported bugs can only be fixed by accident.

[bugs.kde.org](http://bugs.kde.org)

---

### Post by d4y on 2010-05-25
> **Zorael said:**
> This sounds like it warrants a bug report. Remember, unreported bugs can only be fixed by accident.

[bugs.kde.org]("http://bugs.kde.org[/url")

Thanks for advice, I've reported this bug today -- [https://bugs.kde.org/show_bug.cgi?id=238759](https://bugs.kde.org/show_bug.cgi?id=238759)

---

### Post by d4y on 2010-05-27
If somebody has the same problem as described in this thread -- please confirm bug [https://bugs.kde.org/show_bug.cgi?id=232626](https://bugs.kde.org/show_bug.cgi?id=232626) and maybe vote for it. Bug is opened since 2010-03-29  and still no progress, still state UNCONFIRMED. 

I think this bug is critical. Now (as I understand) it is impossible to access internet from KDE apps in any organisation which use auth proxy, and most do so.

---

### Post by sjoerd.vanderveen on 2010-05-31
[EDITED]

Experiencing same issue un Kubuntu 10.04.
Even more strange: when trying to by-pass KDE and set the proxy in a terminal, the definition of the environment variable http_proxy does not seem to be used:

export http_proxy=http://<username>:<password>@<proxyIP>:<port>

Subsequent sudo apt-get update leads nowhere.

Turns out there is a bug report for gnome-terminal on this: [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/534225](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/534225)

They say a workaround is to add to .bashrc:

export no_proxy=$(echo $no_proxy | sed 's/,$//')

Could KDE be affected too?

---

### Post by nushoin on 2010-06-08
> **sjoerd.vanderveen said:**
> [EDITED]

Experiencing same issue un Kubuntu 10.04.
Even more strange: when trying to by-pass KDE and set the proxy in a terminal, the definition of the environment variable http_proxy does not seem to be used:

export http_proxy=http://<username>:<password>@<proxyIP>:<port>

Subsequent sudo apt-get update leads nowhere.

Turns out there is a bug report for gnome-terminal on this: [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/534225](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/534225)

They say a workaround is to add to .bashrc:

export no_proxy=$(echo $no_proxy | sed 's/,$//')

Could KDE be affected too?

what you would like to do after you set the http_proxy environment variable, is

**sudo -E** apt-get update

also use 'sudo -E' whenever you try to install any package, e.g.

sudo -E apt-get install firefox

---

### Post by binojvj on 2011-03-09
Have the same problem in my Kubuntu 10.10.
As a result no way to update package manager and other system core apps.
But can use Firefox by directly giving the proxy settings to Firefox
Edit-> Preferences-> "Advanced"[Last Tab]-> "Network" [2nd Sub Tab]-> "Settings" [Radio Button]-> "Manual Proxy Configuration"

**So some one please help us for this critical issue.**

---

### Post by Skilly on 2011-11-06
Does entering your proxy authentication details in /etc/apt/apt.conf help?

---

### Post by udippel on 2011-11-06
> **Skilly said:**
> Does entering your proxy authentication details in /etc/apt/apt.conf help?

Yes. Though I hate to say 'yes' to your question, since that wasn't what the bug is all about. As of today, and 11.10 (Oneiric), there is no way to enter username and password in that same applet. 
Does anyone in here read and squash bug reports? is what one could ask (oneself).

There is a rather difficult story behind this, and it involves NTLMv2-proxies as well. For NTLMv2, the answer to your question would still be 'no', and since many organisations implement these in our days ('Microsoft Forefront'), it is NOT the 'Year-of-the-Linux-Desktop'. It can't be, if you cannot update / install any PC within the LAN of an organisation. (There is a corresponding bug filed for one and a half year; no further activity.)

---

