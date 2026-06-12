---
title: "Connecting 2 Ubuntu systems via SSH works only 50%"
date: 2011-11-20
forum: Networking &amp; Wireless
---

### Post by XEtedBear on 2011-11-20
2 Ubuntu systems: 10.10 and 11.10.

I can connect to 11.10 from 10.10 via 'connect to server', using SSH and port 22

I cannot connect to 10.10 from 11.10 using the same method. I get the error message  'SSH program unexpectedly exited' - to which Google can find no satisfactory explanation (in other words a lot of 'explanations' which are either just plain wrong or don't apply in my context).

10.10 is running ufw; 11.10 is not. Failure still occurs if I disable ufw.

What settings should I be checking?

---

### Post by newbie-user on 2011-11-20
Maybe openssh-server isn't running on the 10.10 machine?

---

### Post by matt_symes on 2011-11-20
Hi

Run ssh with the -vvv switch to get more info on the 11.10.

```
ssh -vvv user@machine
```

Flush all ip rules on the 10.10 machine (case sensitive)
```

sudo iptables -F
```

Kind regards

---

### Post by XEtedBear on 2011-11-21
> **matt_symes said:**
> Hi

Run ssh with the -vvv switch to get more info on the 11.10.

```
ssh -vvv user@machine
```

Flush all ip rules on the 10.10 machine (case sensitive)
```

sudo iptables -F
```

Kind regards

The open ssh server is running on both systems.

Running with the verbose switch on the 11.10 system results in the message: 

```
 ssh: could not resolve hostname <10.10 system_name>: name or service not known 
```

The hosts files on the 2 machines are virtually identical, with the 10.10 system having slightly more information:

10.10:

```

192.168.0.5	<10.10 system_name>	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	<10.10 system_name>	localhost6.localdomain6	localhost6
127.0.1.1	<10.10 system_name>

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
11.10:

```

127.0.0.1	localhost
127.0.1.1	<11.10 system_name>

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```


What conclusion should I draw from this?

---

### Post by matt_symes on 2011-11-21
Hi
[FONT=monospace]
[/FONT]> ssh: could not resolve hostname <10.10 system_name>: name or service not knownThis looks like a lookup issue. 

Can you connect using the IP address of the problematic computer ? You want to make sure you can do that first.

```
ssh user@<IP address>
```

Kind regards

---

### Post by XEtedBear on 2011-11-21
I'm not sure which is the problematic computer......

I cannot connect to 10.10 from 11.10, but I can the other way round. Without any real evidence, I'll assume 11.10 is the problem system. Issuing the suggested command from 11.10 results in a terminal session which appears to be doing nothing - I can type anything into the 'console' and get no result.

If I attempt to close the terminal session I am told that there is still a process running in the terminal.


If I issues the command from the 10.10 system, the result is:
```

The authenticity of host '192.168.0.8 (192.168.0.8)' can't be established.
RSA key fingerprint is xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx.
Are you sure you want to continue connecting (yes/no)? 

```

---

### Post by matt_symes on 2011-11-21
Hi

```
[FONT=monospace]
[/FONT]The authenticity of host '192.168.0.8 (192.168.0.8)' can't be established. 
RSA key fingerprint is xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx. 
Are you sure you want to continue connecting (yes/no)?

```Type yes and see if it will connect. (it should do)

Kind regards

---

### Post by newbie-user on 2011-11-21
Since it seems to be a lookup issue, then you'll want to edit your /etc/hosts file to point the ip addresses to the correct hostnames.  On the 11.10 system, your hosts file should have:

192.168.0.5 <hostname of 10.10 system>

On the 10.10 system, the hosts file should have:

192.168.0.8 <hostname of 11.10 system>


For example, if there is a computer named gateway on the network that has an ip address of 192.168.1.1, and I want to add it to the hosts file on another computer at 192.168.1.3, then the hosts file on 192.168.1.3 would have an added line:

192.168.1.1 gateway

---

### Post by XEtedBear on 2011-11-23
> **newbie-user said:**
> Since it seems to be a lookup issue, then you'll want to edit your /etc/hosts file to point the ip addresses to the correct hostnames.  On the 11.10 system, your hosts file should have:

192.168.0.5 <hostname of 10.10 system>

On the 10.10 system, the hosts file should have:

192.168.0.8 <hostname of 11.10 system>


For example, if there is a computer named gateway on the network that has an ip address of 192.168.1.1, and I want to add it to the hosts file on another computer at 192.168.1.3, then the hosts file on 192.168.1.3 would have an added line:

192.168.1.1 gateway

Sadly this makes no difference to the problem. The 'connect to server' link in Nautilus invokes a connection process which runs for about 3 minutes and then fails with the usual message.



I have been trying for about a month ow to get 2 Ubuntu systems to talk to each other. Surely it can't be this difficult? Or is this a known problem in Ubuntu?

---

### Post by XEtedBear on 2011-11-24
> **matt_symes said:**
> Hi

```
[FONT=monospace]
[/FONT]The authenticity of host '192.168.0.8 (192.168.0.8)' can't be established. 
RSA key fingerprint is xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx. 
Are you sure you want to continue connecting (yes/no)?

```Type yes and see if it will connect. (it should do)

Kind regards

I agree it *should* do.

This is one of those rare incidents where a computer system agrees with a human's view of what should or shouldn't happen - the human opinion is generally irrelevant, in my expereince. For example, no amount of my believing, or insisting, that my 11.10 system *should* connect to my 10.10 system seems to effect this result. This is the problem I wish to solve.

---

### Post by matt_symes on 2011-11-24
Hi

> **XEtedBear said:**
> I agree it *should* do.

This is one of those rare incidents where a computer system agrees with a human's view of what should or shouldn't happen - the human opinion is generally irrelevant, in my expereince. For example, no amount of my believing, or insisting, that my 11.10 system *should* connect to my 10.10 system seems to effect this result. This is the problem I wish to solve.

I am a bit confused by this. Did it not connect when you used the IP address ?
[FONT=monospace]
[/FONT]```
The authenticity of host '192.168.0.8 (192.168.0.8)' can't be established.  
RSA key fingerprint is xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx.  
Are you sure you want to continue connecting (yes/no)?
```

This suggests it had connected.

Kind regards

---

### Post by XEtedBear on 2011-11-24
Oh yes, it connected just fine - that's what my original post said. But that's not the failure I am trying - and failing - to correct.

Actually, upon reflection (and hence this edit), I am being economical with the truth. The connection finally fails because authentication fails: neither a publickey nor a password can be found.

That's a secondary issue, which I will raise in another post that highlights the deficiencies in the community documentation on configuring OpenSSH to use keys rather passwords. This is just an example of the fact that the community documented procedure cannot be followed. However, that is a problem for the second month of so of trying to get Ubuntu to talk unto Ubuntu.

Right now I want to get to the point where 11.10 can connect to 10.10 without a connection time out.

---

