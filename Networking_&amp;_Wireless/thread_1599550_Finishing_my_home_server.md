---
title: "Finishing my home server"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by Sarah13 on 2010-10-17
I'm a complete beginner at this, so any input is appreciated.

I am trying to setup my home server. It's on an old PC using Ubuntu 10.4 Desktop edition. I want to be able to save files to this server from my Macbook (10.5.8 ), as well as edit them. These files will all be web development files, mostly HTML and PHP. I want my mac to be able to see this server, connect to it, and have read/write privileges to it. It's basically going to be my web development server for web pages in progress.

I use my wireless router for my internet. The linux computer is hardlined to the router, while my Mac only uses the wireless. My router assigns IP's dynamically.

So far I have installed Apache 2, PHP 5, and Mysql on the machine. Because my router assigns dynamic IPs, I set up the ubuntu machine with dynDNS. So now on the ubuntu machine I can go to it's IP address and view the content there through a browser (ie it's working correctly). And due to DynDNS, I have an URL that I can access on my mac. I can move pages to and from, and create sub-directories within the server if I am on the ubuntu machine. 

However, the ubuntu machine is the only one to have read/write privileges. Right now only root as permission to edit the www folder. I need to change that.

I enabled port forwarding HTTP service through port 80, which allowed me to setup the dynDNS. Now would I setup an FTP service so that I can transfer files back and forth from my mac to the server? Or do I need to get the permissions squared away first? I'm not sure where to go from here.

---

### Post by CharlesA on 2010-10-17
If you are accessing the machine from inside the network, you don't need to bother with Dyndns, as that is only for if you are trying to access the server from the internet and you don't have a static external ip.

You don't need to mess with port forwarding at all if you are just wanting to access the machine locally.

Instead of FTP, I would suggest using SFTP (part of SSH), since SFTP is a whole lot simpler to set up and is more secure then FTP.

Also, I think you can use SSHFS with OSX, but I am not sure. That would probably work best for accessing files.

---

### Post by Sarah13 on 2010-10-18
Thanks so much for your help! I setup OpenSSH on the linux machine, and MacFUSE on Mac. It allowed me to mount the server as a filesystem, which was great, but I'm not quite there yet.

I can see some of the file structure of my linux machine on my mac (such as movies and documents) but I need access to var/www/ unless I want to tell the server to move the default directory.

I'm assuming this is a permissions issue? I think only root has /www permission. What would be the best way to fix this?

---

### Post by CharlesA on 2010-10-18
It's probably a permission issue. You should be able to read any thing that is in /var/www tho.

Here are the permissions on my machine:
```
drwxr-xr-x 3 root root 4096 2010-08-25 19:38 /var/www
```

So, root only has write access, but everyone has read access. You could probably chown it to your username and it would work ok. There might be an easier way, I don't know.

---

### Post by Sarah13 on 2010-10-18
Alright, I've gotten the permissions issue fixed, at least on the linux side. I used ```
$ sudo chown -R $USER:$USER /var/www
```

All fixed, I pointed Macfusion to /var/www and it works beautifully. Excuse my utterly basic networking questions, but is there anything I should be doing to secure this network? After I loaded the right programs, I connected right into the linux machine. Is there a way of seeing who the authorized users are to the server so I can make sure it's just my laptop that can access it? And because I've set up this server through the IP address on my home network, I wouldn't be able to access OpenSSH outside of my home network, correct? Unless I setup keys?

---

### Post by CharlesA on 2010-10-18
Like I said earlier, don't bother with port forwarding if you are only going to be accessing the files locally.

If you don't have anything accessible from the internet the defaults should be fine.

---

### Post by Sarah13 on 2010-10-18
Well, the majority of the time I'll be working from within the home network. I needed to get the home server set up, that was the priority. However the ultimate goal would be to be able to access and write to the server from anywhere. That way I can show the pages that are in progress to my the people I'm designing them for. I'm not using any sensitive info - it's all design based, so while security isn't a huge issue (no logins, passwords, other sensitive data) I would like to make it as secure as I can. 

I haven't looked into it yet, but I'm assuming I would need to create keys in OpenSSH to verify that my macbook has r/w access?

---

### Post by CharlesA on 2010-10-18
I would use key auth with SSH and have that one open to the internet. You can create a tunnel to access the web server from the outside, so that one isn't directly accessible to the internet.

I'm not sure if you can use keys with a mac, since I don't have one, but if you are able to use keys, you can do it that way (keys instead of passwords)

---

