---
title: "SSH security, how paranoid?"
date: 2011-08-24
forum: Networking &amp; Wireless
---

### Post by mikeym on 2011-08-24
Hi, I'm considering opening up my SSH to the internet for the first time and I'm wondering how paranoid I need to be.

I've secure 4096 bit RSA keys set up and not *root* or password logins allowed. I've tried setting up *denyhosts* but it doesn't seem to actually make a difference when only secure key logons are allowed and I can't get the other feature I would like working to work which is sending me an email when someone is trying to log in.

Do people actually try and repeatedly log in when using keys? If so how to I email myself?

Lastly I was also planning on using *Cryptknock* to disguise my ports. 

Am I being too paranoid, paranoid enough or too lax?

---

### Post by e79 on 2011-08-24
You cannot get too paranoid regarding security imho. Have you thought about implementing a VPN server (like [OpenVPN]("http://openvpn.net/index.php/open-source/overview.html")) so that you wouldn't need to expose your SSH on the net ?

But so far your concept of securing SSH is good and valid.

For emails sent upon SSH connections, have a look [here]("http://www.nettipsdb.com/2011/05/alert-on-ssh-user-login/").

Just my 0.02$

---

### Post by mikeym on 2011-08-24
Hi **e79**,

Thanks for the $2/100. I've decided against a VPN as managing the constantly changing IPs with providers here would be too much hassle. 

Currently I've dropped *DenyHosts* as it looks like its getting phased out from linux along with tcp wrappers which it relies on. I've tried the ominously named *Fail2Ban* and come to the conclusion that these don't actually help as long as you're using only Key authentication. They don't seem to catch anything. 

I've added some rules to iptables (through UFW which I use). to drop too many connection attempts to my ssh port and that works for Keys as well but fails to email me. Shame I can't find something like *Fail2Ban* for use with Keys.

---

### Post by mikeym on 2011-08-24
```

-A INPUT -i eth0 -p tcp -m tcp --dport ssh -m state --state NEW -m recent --update --seconds 60 --hitcount 6 --name DEFAULT --rsource -j DROP 
-A INPUT -i eth0 -p tcp -m tcp --dport ssh -m state --state NEW -m recent --set --name DEFAULT --rsource 

```

Could anyone tell me how to log the above iptables rules?

(PS) They're supposed to be the rules from [here](http://www.reddit.com/r/linux/comments/bvtrt/fail2ban_and_ssh_public_key_authetication/).

---

### Post by Derek Karpinski on 2011-08-24
> **mikeym said:**
> I've decided against a VPN as managing the constantly changing IPs with providers here would be too much hassle.
 
Sign up for a free dyndns account, and change one line in your OpenVPN client config file, and you're done.

---

### Post by sbraz on 2011-08-24
use a random ssh port (1028+)for the server, change it everytime before you logoff.

fake ssh servers, looping into a locked vm.

---

### Post by mikeym on 2011-08-25
I'm not going to mess with a fake ssh (cool idea, I quite like one suggestion I found of just having a ssh authentication that pretended to check against a password but always denied as a time waster, seems like it would leave you with a lot of traffic though). My port is already non-standard and I've used basic port knocking (knockd) to mask it a bit more. 

I gave up with iptables (I always do) and tried to fix the problem with Fail2ban, which was that attempts to login using SSH Keys were not getting logged so Fail2Ban had nothing to work with.

I discovered that OpenSSH defaults to NOT logging Key based Authentication attempts! This can be changed by setting:

**/etc/ssh/sshd_config**```

LogLevel VERBOSE

```

Fail2Ban then seems to pick it up for me.

Conclusion: Be more paranoid than sony.

---

### Post by atca on 2011-09-04
Not quite what you want but after reading your post I decided to set up an email alert when someone successfully connects to my SSH box, I wanted a very simple solution...

[http://confoundedtech.blogspot.com/2011/09/set-up-email-alert-for-ssh-connections.html](http://confoundedtech.blogspot.com/2011/09/set-up-email-alert-for-ssh-connections.html)

The only downside is the password for the smtp server is stored in plain text on the server.

---

