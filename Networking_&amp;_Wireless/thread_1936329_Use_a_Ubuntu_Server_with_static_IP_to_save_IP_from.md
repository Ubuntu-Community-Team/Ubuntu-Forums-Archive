---
title: "Use a Ubuntu Server with static IP to save IP from dynamic Server?"
date: 2012-03-05
forum: Networking &amp; Wireless
---

### Post by Pay87 on 2012-03-05
Hi, I have a little problem that needs some brainstorming (at least for me).
I have two ubuntu servers running. One is a virtual server (for web hosting) with static IP from a hoster. Second one is right next to me and gets a dynamic IP from my ISP.

I don't want to use services like DynDns or No-IP, because I think it should be possible to do it without a extra service.

The server with static IP is running Plesk on it, with several Vhost websites (i have root ssh access). So I think it wouldn't be a good idea to mess around with the DNS settings here (if this is wrong tell me).

So my solution would be to have a password protected php script on the static server, which saves the current ip address when accessing the script. On the dynamic server I would setup a cron task to access this script every 15-30min. The next script simply would give a output of the IP address which is saved.

Also this should do the trick, I thought there might be a better more advanced method to realize this. 

What do you think? With 2 ubuntu servers with full root access there should be some more nicer (maybe safer) options :P:P
I just want to get remote ssh access when my IP changes.. :)

Just one question, assuming I would use DynDns etc. When you SSH to the address, is there a way for the provider to see SSH passwords or other sensitive data?
Because this would be my last choice if everything fails or a backup solution.

---

### Post by Sergius14 on 2012-03-06
A provider or anyone cannot see your password sniffing Internet.

SSH uses passords in a hash form (SHA), which you can see this hash code but not the password. Since this is vulnerable to reverse hash databases, this password/hash is transmitted encrypted with a public key. The private key is the only one to decrypt and see the hash.

Pretty safe if you server is physically secured and the password is long and complex enough to avoid dictionary attacks.

Since there are lots of bots trying dictionary password over Inet, I feel safer blacklisting any IP (at least for a while) when they tries N times a bad password.

Read more about: Hash Algoritms and PKI (Public Key Infraestructure).


Hash codes are mainly used to check if somebody has changed something in a document or file (a single bit change, makes a whole new key).

PKI could be use in both ways: To sign a document (private key signs/encrypt, everybody decrypt and check authenticity) or to protect/hide/HTTPS/SSH/FTPS (public key -everybody- encrypts but only private key decrypts).


About your script: That sounds to me a homebrew DynDNS.... why not DynDNS? What's the difference with your script?

---

### Post by Pay87 on 2012-03-07
Thanks for your post!

---

