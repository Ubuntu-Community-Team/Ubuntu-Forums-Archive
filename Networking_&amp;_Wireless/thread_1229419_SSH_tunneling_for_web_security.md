---
title: "SSH tunneling for web security?"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by billdotson on 2009-08-02
So, I have seen two or three different howto's telling the reader how to use SSH to encrypt web browsing as well as other network traffic such as bittorrent, etc. I have even heard of some claiming that they could SSH to a certain secure proxy and make it where your respective ISP couldn't see your downloads or really anything else (all they would know is your IP since they give it to you).

Is the last statement accurate; is that even possible? Some people use the SSH tunneling to encrypt their connection because they don't want the IT guys at school checking watching them check their bank account, others pirate (i.e. *steal* music, others "pirate" games they have bought but don't want to have to install a rootkit on their PC to play it (Crysis Warhead with SecuROM 7 anyone?) but the way to set it up I would assume is the same.

Basically what I want to do is have it where I can encrypt and hide all traffic on all ports when I am online. I want as few people as possible to see what I am doing. With this SSH tunnel I assume that the server is going to be the one with all the information to look at so I don't suppose having a SSH server running on my home network would really make much difference. So, basically I would have to have a server out of my home network and preferably one where my information would be secure. I guess the only real way to have this be 100% secure is to SSH into a proxy that is it's own ISP ([http://itmanagement.earthweb.com/erp/article.php/615281](http://itmanagement.earthweb.com/erp/article.php/615281)) or (this might work, but would probably be slow) a proxy in another country (could be it's own ISP there too). Those options probably aren't very realistic however.

Any input would be appreciated.

Thanks.

---

### Post by easybake on 2009-08-02
The real question is.. what the hell are you doing?! jk. But you seem to have it pretty much figured out. Using a server located in your home to ssh wouldn't really hide what you were doing from your ISP (assuming it is *your* ISP the machine is connected to).


Have you looked into TOR (the onion router)?


EDIT: I've read your post a few times and can't actually get a good grasp of what you are trying to figure out.

---

### Post by firen on 2009-08-02
Let me put your question this way, let's say you are sitting in your office/college/school and you dont want IT Guys ( Guys like me :) ) look at your confidential data such as Bank login and other confidential browsing you might be doing ( Most of the bank website use SSL anyways ) .

You can install SSH server on one of your Home PC. Once it is accessible from internet you can make a SSH tunnel from your work place ( , college, school ) and browse securely.

Hope it helps.

---

### Post by easybake on 2009-08-03
Ahh okie dokie. The way I would suggest would be to use the awesome feature of x forwarding. What it does, is allow a GUI program to run on the server and send all the x11 information to your remote computer.

If you did this you could start Firefox on the server, but the program would actually show up on your remote computer.

The main complication here would be that in order to work, both the server and the remote need to be running x11 environments, like Linux. It won't work if your server is Linux and your remote is running Windows.

```
ssh -X <remotehost>
firefox -no-remote
```

---

### Post by billdotson on 2009-08-03
Basically just don't want anybody snooping on my web traffic or any of my downloads or anything. I don't like being spied on, regardless of what I ma doing.

For remote desktop though I figured out how to do that in a pretty secure way last year. Basically I connected to my PC at home with TightVNC, and tunneled the connection through an SSH connection that required RSA2 authentication public and private keys. I am fairly certain I was told by somewhere that TightVNC is somewhat encrypted itself anyway so that would mean I had two layers of encryption going. Basically I set openssh up in Cygwin for Windows and just normal ssh in Linux and had portable and tightvnc on my flash drive. Tried it from school and it worked well.

---

### Post by dmizer on 2009-08-03
You should not try to use VNC to access your remote computer, it causes a huge amount of network overhead and is likely to raise eyebrows.

If you just want anonomyous browsing, you can either use TOR as suggested earlier, or you can tunnel your web traffic through SSH socks proxy. Since you already have Cygwin, just use a command like this:
```
ssh -D 1080 remote-user@remote-ip
```
Then edit Firefox preferences > advanced > network > settings. Change to "manual proxy configuration" and next to SOCKS, enter: localhost for the "Host" and 1080 for the port. Make sure Socks V5 is selected, and click OK.

Now all your web traffic encrypted and pushed through your home server (you can verify it by checking your WAN IP address at [www.whatismyip.com](www.whatismyip.com) before and after you've configured your socks proxy). Something to note though, is that your DNS queries will not go through the SSH tunnel, so I suggest using alternative DNS servers like [OpenDNS](www.opendns.com). Alternatively, I suggest configuring a VPN.

---

