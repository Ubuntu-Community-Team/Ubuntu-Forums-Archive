---
title: "DNS Server Resolution in Terminal"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by klauern on 2009-07-02
I'm trying to find a thread that answers this, but I don't think I have the proper l33t5p3@k to find it.  Basically, I'm installing Ubuntu on a corporate network and I am used to ssh'ing into our various servers and domains simply by typing

```
$ ssh servername
```
or
```
$ ssh myuname@servername
```

However, I know that our corporate laptops have alot of proxy configs and probably some setting for DNS so that in reality ssh'ing servername adds 'servername.internal-subnet.com' to all requests.

How can I accomplish the same thing across Ubuntu (specifically Terminal) so that I don't have to type:

```
$ ssh myuname@servername.internal-subnet.com
```

everytime I just mean

```
$ ssh myuname@servername
``` 

?

Is it something I can set in Ubuntu itself, or possibly somewhere in the .bashrc, .profile, or .bash_profile to have our DNS server resolve all servernames and possibly add 


What I've already done:

[LIST=1]
[*]Set Global Network Proxy Settings with our corporate .pac file (by using System->Preferences->Network Proxy and set the Automatic Proxy Configuration Script, and applied System-wide).  Works for Update Manager, Firefox, etc., but I don't think adds anything to DNS resolution in Terminal.
[*]Attempted ssh'ing using fully formed server name with .interna-subnet.com to the end (This works but is clunky.  I have alot of servers and zones, so aliasing all of these would be a pain to keep up-to-date)
[*]opened .bashrc and performed ```
export http_proxy="http://servername.com/proxy.pac"
``` to set the .pac proxy (Doesn't seem to add anything to the Terminal sessiosn that wasn't already accomplished by System->Preferences->Network Proxy)
[/LIST]

---

### Post by computer13137 on 2009-07-02
For the record - I've never done a proxy server, so I completely ignored that part of your post.

You have two options that I can think of.

1) If you run an internal DNS server, just add the hostnames as A records.  Then they should resolve to the servers in question.

2) Edit the /etc/hosts file on every machine you want to use the shortcut with, and manually make a host for the name and IP of the servers you want to connect to that way.

I'll subscribe to this thread in case I can help you further.  But now I've given you something better to take back to Google, and maybe I brought up something you hadn't thought of.

-Kirk

---

### Post by alphacrucis2 on 2009-07-02
> **klauern said:**
> I'm trying to find a thread that answers this, but I don't think I have the proper l33t5p3@k to find it.  Basically, I'm installing Ubuntu on a corporate network and I am used to ssh'ing into our various servers and domains simply by typing

```
$ ssh servername
```
or
```
$ ssh myuname@servername
```

However, I know that our corporate laptops have alot of proxy configs and probably some setting for DNS so that in reality ssh'ing servername adds 'servername.internal-subnet.com' to all requests.

How can I accomplish the same thing across Ubuntu (specifically Terminal) so that I don't have to type:

```
$ ssh myuname@servername.internal-subnet.com
```

everytime I just mean

```
$ ssh myuname@servername
``` 

?



It's nothing to do with proxy servers. All that is happening on the Windows machines is that they are appending a domain suffix. This is a setting in windows under the advanced tcp settings dialog that has a tab headed DNS. One of the section on that tab says something like: "Append the following domain suffixes in order". Yes you can do the same thing in linux by inserting a line to the file /etc/resolv.conf

for example suppose resolv.conf looked like this:

```
nameserver 10.1.1.1
nameserver 10.1.1.2

```

Add a line as below (using you FQDN example):

```

search internal-subnet.com
nameserver 10.1.1.1
nameserver 10.1.1.2

```

---

### Post by superprash2003 on 2009-07-03
editing the hosts file as mentioned earlier is a good option!!

---

### Post by klauern on 2009-07-06
> **alphacrucis2 said:**
> 
for example suppose resolv.conf looked like this:

```
nameserver 10.1.1.1
nameserver 10.1.1.2

```

Add a line as below (using you FQDN example):

```

search internal-subnet.com
nameserver 10.1.1.1
nameserver 10.1.1.2

```

I did add that line

```
search internal-subnet.com
nameserver 10.1.1.1
nameserver 10.1.1.2

```


But now I think i'm dealing with an additional issue adding to the confusion.  With the /etc/resolv.conf file, it seems to get reset every time I restart, even though I'm editing it as root and saving it.  I'm assuming there is some configuration somewhere that redefines /etc/resolv.conf every reboot, so I would probably need to add the "search internal-subnet.com" to that config script.

Any suggestions on where I can make this change?

---

### Post by klauern on 2009-07-06
I did find what I think will be a temporary solution, but I know it's a hack.

I added the line to the /etc/resolv.conf

```
search internal-subdomain.com
nameserver 10.1.1.1
nameserver ....

```

And then chattr'd it +i:
[http://ubuntuforums.org/showthread.php?t=581029](http://ubuntuforums.org/showthread.php?t=581029)

```
$ sudo chattr +i /etc/resolv.conf
```

But I know that this just seems like a cop-out for a real solution.  There has to be a better way to do this than this, so I hope I can find it.

---

