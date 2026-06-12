---
title: "SSH setup"
date: 2006-07-16
forum: Networking &amp; Wireless
---

### Post by DigitDuke on 2006-07-16
Hi there,

I'm following a tutorial in Howtoforge's "Perfect setup" series for my Ubuntu Server 6.06.

> Then edit /etc/hosts. Make it look like this:

vi /etc/hosts

```
127.0.0.1       localhost.localdomain localhost
192.168.0.100   server1.example.com     server1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Now run

```
hostname
hostname -f
```

Both should show server1.example.com. If they do not, reboot the system:

```
shutdown -r now
```

Afterwards, run

```
hostname
hostname -f
```

again. Now they should show server1.example.com.

From now on you can use an SSH client such as PuTTY and connect from your workstation to your Ubuntu server and follow the remaining steps from this tutorial. 

Unfortunately, when following this tutorial I have no idea what my hostname should be.  The name of my computer is "digit" but I don't have access to any such thing as a domain name.  Should I put in my public hostname affiliated with my IP?

All answers appreciated,
Friðrik Már

---

### Post by morequarky on 2006-07-16
<SSH SETUP>

Try running "sudo apt-get install ssh"
Enter your password.
Done.

Try "ssh username@localhost"
Enter Password.
Should show that you connected.

Exit to return to original terminal session.
Exit again to close terminal window.

:)

---

### Post by rmjb on 2006-07-16
> **DigitDuke said:**
> 

```
127.0.0.1       localhost.localdomain localhost
192.168.0.100   server1[COLOR="Red"].example.com[/COLOR]     server1
```

Unfortunately, when following this tutorial I have no idea what my hostname should be.  The name of my computer is "digit" but I don't have access to any such thing as a domain name.  Should I put in my public hostname affiliated with my IP?

All answers appreciated,
Friðrik Már

In your case your hostname is "digit". You can set anything for your domain name, i.e. replace .example.com with anything you want. But I would not advise using the public hostname associated with your IP and I wont advise a domain name that would make sense on the internet, i.e. nothing ending in .com, .net, .org and so on.

I have my hostname set to *<mylastname>*.home

- rmjb

---

### Post by DigitDuke on 2006-07-16
Oh, okay.  Thanks a lot, guys, your explanations are appreciated :-)

[QUOTE=rmjb]In your case your hostname is "digit". You can set anything for your domain name, i.e. replace .example.com with anything you want. But I would not advise using the public hostname associated with your IP and I wont advise a domain name that would make sense on the internet, i.e. nothing ending in .com, .net, .org and so on.

I have my hostname set to <mylastname>.home[/QUOTE]

I see.  But does that mean that SSH will only be accessible on my local network?

Regards,
Friðrik Már

---

### Post by rmjb on 2006-07-16
It should be, your router will prevent connections from the internet. If you want to connect from the net you'll need to forward the port, but that's a whole networking and security issue there.

- rmjb

---

### Post by damonc on 2006-09-21
> **rmjb said:**
> In your case your hostname is "digit". You can set anything for your domain name, i.e. replace .example.com with anything you want. But I would not advise using the public hostname associated with your IP and I wont advise a domain name that would make sense on the internet, i.e. nothing ending in .com, .net, .org and so on.

I have my hostname set to *<mylastname>*.home

- rmjb

Hi,
Sorry to revive an old thread, but my question kinda fits.

I am also following the server howto and when it comes to edit the /etc/hosts file I'm getting confused. I named my computer 'jfdc'. 

I have several domains that I want to point to this server (when it's setup). Do i need to include them in the hosts file? Or should I just use the jfdc.example.com as per the tutorial? you talk about making somthing up that won't make sense on the net.

I don't think I fully understand what these lines in /etc/hosts are actually for. Some clarification would be greatly appreciated!

---

### Post by rmjb on 2006-09-21
The lines in the /etc/hosts file just map hostnames to ip addresses for your machine. These lines affect ONLY your machine.

So if you had the following line:

```
192.168.1.5   foo.home   foo
```

When your machine tries to connect to foo (ping, web browse, ssh, anything) or foo.home it will use the ip 192.168.1.5.

Your machine's hostname should also be in the /etc/hosts file along with an entry for localhost. Sometimes they are all on the same line and all map to 127.0.0.1. So in that case the line would like like this:

```
127.0.0.1    localhost    jfdc
```

What you probably should do, if you have a static IP address assigned to your machine, is move 'jfdc' to it's only line with the static ip. So your hosts file would have at least two lines:

```
127.0.0.1    localhost
192.168.1.5  jfdc
```

One thing you should avoid is mapping a host name to more that one ip, thus this is a bad idea:

```
127.0.0.1    localhost    jfdc
192.168.1.5  jfdc
```

In this case name resolution can get confused.

I hope I've cleared up the use of the /etc/hosts file for you.

As for pointing other machines to your machine, the local host file will not achieve this. You'll either need to maintain the hosts file on each machine (bad idea) or set up a simple dns server. dnsmasq is a good simple one that's in the repositories and it serves up entries from the hosts file, so in that case the hosts file for the dns server becomes the hosts file for the network.

- rmjb

---

### Post by damonc on 2006-09-21
rmjb,
thanks, that has helped to clear things up a little for me. I have one more question though. When following the howto forge "perfect setup" tutorial, it says to insert these lines into the /etc/hosts file

```

127.0.0.1       localhost.localdomain localhost
192.168.0.100   server1.example.com     server1
```

I have changed these lines to read

```
127.0.0.1       localhost.localdomain localhost
192.168.0.100   jfdc.example.com     jfdc
```

But your explanation doesn't mention anything about localhost.localdomain. If I understand you correctly, it doesn't matter what values you assign to what IP addresses because the values are simply for accessing machines from within my network. Is that correct?

Can you shed any light on why, when I follow this step in the tutorial:

Now run:

```
hostname
hostname -f
```

Both should show jfdc.example.com. If they do not, reboot the system.

Even after a reboot, running hostname only returns jfdc, instead of jfdc.example.com??

thanks

---

### Post by rmjb on 2006-09-21
localhost.localdomain is sometimes used by programs to access your local PC, so it's handy to have in there.

Also, you shouldn't use example.com as your personal local domain name, you should use something that's not on the internet, like lastname.home or something.

As to why hostname -f does not return the fully qualified domain name (fqdn) I'm not sure. ou can try setting it using Ubuntu's network configuration tool, but check your hosts file after, I think it puts your hostname on two ips and that's not good.

- rmjb

---

### Post by damonc on 2006-09-21
thanks! that's helpful. I will keep trying when I get home from work tonight.

---

