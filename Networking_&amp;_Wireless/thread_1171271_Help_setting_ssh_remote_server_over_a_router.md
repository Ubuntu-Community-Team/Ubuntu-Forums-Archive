---
title: "Help setting ssh remote server over a router?"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by sekura on 2009-05-27
Ok, here's a tricky one (to me at least).
I set up my SSH server. I set up my passphrase.
I am connected over a router. I set up my NAT: 
Say, the server listens on 3456. I set it up so that the Private port is 3456 and the Public port is let's say 3666. 
I mention that everything i did was from the same computer (don't have another one to try on, nor another internet connection).

So, the correct command for logging into the remote server, in this case should be:
ssh -p 3666 <wan-ip>
That means that it tries to connect to the router on 3666, which Forwards it to the local computer (this one), on port 3456, which is what my sshdaemon in listening.

but :
```
me@my-pc:~$ ssh -v -p 3666 86.x.x.x
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 86.x.x.x [86.x.x.x] port 3666.
debug1: connect to address 86.x.x.x port 3666: Connection refused
ssh: connect to host 86.x.x.x port 3666: **Connection refused**
```why?

Further info:
- canyouseeme.org sees my service on 3666
- if I connect to the LAN IP, it works
- (and this is the most annoying) if i set up the BOTH the Private Port and the Public Port of the Router forwarding to 3456, and ssh using -p 3456, IT WORKS!... 
- (along with this one) if i set Private Port tu 3666 and PUBLIC port to 3456, and use -p 3456 .... it works.. (although canyouseeme.org doesnt even see a service on 3456 now)

I fail to see the logic here. Is it because i'm running commands from the same computer, and from the inside of the network i'm trying to acces via my router?

---

### Post by superprash2003 on 2009-05-27
do you have firestarter or anything similar installed?

---

### Post by Boondoklife on 2009-05-27
This may just be a routing issue, try to connect [http://www.serfish.com/console/index.jsp](http://www.serfish.com/console/index.jsp)

---

### Post by sekura on 2009-05-27
No i don't have firestarter or any other firewall installed:).
Thanks maletek. It works trough that site :) So that must mean it's set up correctly.

And one more question regarding the public and private keys: if i want, for example, to connect from another pc (untrusted one, like a public one, or school) to mine, what i actually have to do is generate an ssh key on that computer, and send the public key to my home pc?
But if don't do that , then the ssh connection will just resort to asking me my account password (like in the case of the site you gave me)... So there's no real gain in using public+private keys, unless you "PasswordAuthentication no" in your sshd_config... And this tiny bit of info i found on too few sites regardin ssh... So then the "hacker" can just forget about keys, and just try breaking my user password. Am i missing something?

---

### Post by Boondoklife on 2009-05-27
Ok time for me to put my tin foil hat back on. Lets see if you use RSA keys to login then you are still prompted for a password to the key, unless you dont put one on the key. But in that case the black hatter only need to copy your RSA key to login to your system.

Personally I would just create an account that you will use only for ssh and make sure it does not have sudo access. Or you could setup one time use keys.

Lastly for those of us who shine our hat every day, you could setup your fire wall to deny connection attempts from multiple logins in a certain time frame. Maybe even look up port knocking.

---

### Post by sekura on 2009-05-27
Well yes i use RSA. But i have read, RSA keys work by having the Private one on the computer from where you're connecting, and the Public one listed on the remote computer. 
Well in the case of the Serfish console (the link), i bet they didnt generate no keys, neither send me any public ones. 
And obviously, the console resorted to asking me my password (as in user password, not RSA pass-phrase). And upon adding "PasswordAuthentification no" in sshd_config, i couldn't connect at all trough Serfish (which shows my point that RSA keys are useless without disabling PasswordAuthentification).

Tnx for the reply btw :) Sory if i'm being too hyped, i'm new to this kinda' stuff and i just vacuum everything i can find.

---

### Post by MJBoa on 2009-05-27
So you're saying your router settings that you've exposed 3666 and set any connections to that port to forward to your local machine at 3456 and it doesn't work. And when you forward 3456 to 3456 it works. Along with 3456 to 3666? The last one doesn't even seem to make sense, if I'm understanding correctly. Somebody connects to your WAN:3456, you tell your router to forward it to 3666 but it connects to your computer on 3456 anyway? That seems like it's not forwarding correctly, at least when you are connecting from inside the WAN. 3666>3456: no 3456>3456: yes 3456>3666: yes. Looks like it's just forwarding each port to the same one on your machine.

---

### Post by albinootje on 2009-05-27
> **sekura said:**
>  I fail to see the logic here.
Perhaps your ISP has certain ports blocked.

---

### Post by sekura on 2009-05-27
> **MJBoa said:**
> Along with 3456 to 3666? The last one doesn't even seem to make sense, if I'm understanding correctly. [...] 3666>3456: no 3456>3456: yes 3456>3666: yes. Looks like it's just forwarding each port to the same one on your machine.

I agree with you:). But that only happens when connecting from inside the network. If i use canyouseeme.org for these 3 cases, 3666 > 3456 is ok, 3456 > 3456 is ok, and 3456 > 3666 is not ok. And plus, it works if i connect from the link posted by maletek. 
It might just be a bug in the router, or some subtle factor i'm not aware of. Anyways, who needs to connect from inside to the inside via the outside? :P

---

