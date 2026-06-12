---
title: "Synaptic and autoconfig. proxy script"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by rbaleksandar on 2010-05-24
Hi, guys.

  Using Ubuntu 9.10. I got a problem with the wired connection. I managed to fix it more or less. But now after I did about 2 days ago an **apt-get update**, I can't update through the Update Manager, nor install packages through the Synaptic Package Manager, nor install video drivers anymore. Using the terminal works: apt-get install, apt-get update and apt-get upgrade. I'm using a proxy (I'm connected to the network of my university, which uses a proxy) and a autoconfiguration script ***.PAC**. I've never encountered such a problem - to be able to surf or use the terminal, but not the update/synaptic/divers manager. So I looked on the internet and found out that Synaptic has it's own network settings and doesn't care what proxy I've set in the Network Proxy. I don't recall ever having such a problem. I don't recall configuring the network preferences of Synaptic either (I just discovered them :D). Another thing worth mentioning - I can use Synaptic and Update Manager ONLY if I run them from the terminal WITH sudo.

```
sudo synaptic
```
and
```
sudo update-manager
```

 Only when doing so, the managers are able to connect to the internet. If I run only

```
synaptic
```
and
```
update-manager
```

 and after being prompted for administrative privileges I enter the admin's password, they don't connect. :confused: So what I think happens is that Synaptic/Update Manager/Drivers Manager use somehow different network configuration than the one set in Network Proxy. Terminal on the other hand takes the proxy-settings directly from Network Proxy. The weird thing is that using terminal to call Synaptic for example make Synaptic accept the Network Proxy's settings. LOL

  I looked in a couple of threads, where this ~/.bashrc was mentioned and adding **export http_proxy="xxxx.yyyyyy.zzz"** at the end of the file. But I still can't figure out what to do exactly. People say that after adding it, one should 'run it'. Dunno what they mean by that really. It's not a script, it's not something executable.

  So can someone help me solve this problem? I'd appreciate it very much. ^^

---

### Post by Linfreak on 2010-07-29
Try adding,

Acquire::http::Proxy "http://nokes.nokia.com:8080";

to a new file /etc/apt/apt.conf.d/proxy and do,

sudo apt-get update

and for running .bashrc do,

source ~/.bashrc

but its better to put the export command in /etc/profile as that reflects for all users.

Cheers,
Siva

---

