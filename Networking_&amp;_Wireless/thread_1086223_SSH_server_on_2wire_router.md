---
title: "SSH server on 2wire router"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by killjoy123987 on 2009-03-03
I have a 2wire 2701HG-G Gateway router and I am trying to set up a SSH server. I have openSSH-server and the ssh client installed and have had no problem testing the yourname@localhost connection but when i try to connect using my IP it just hangs. I have tried to port foreward but no matter what it still just hangs. im not sure but i think it may be waiting for a response thats being blocked. any help is appreciated thanks.

---

### Post by drjimmy42 on 2009-03-03
Are you setting up an ssh server on an ubuntu box attached to the server?  
From where are you trying to connect with an ssh client?
Paste in the commands you are using in each case, I'm not sure what you mean by "trying to connect with my IP".

---

### Post by killjoy123987 on 2009-03-03
when it works i type 
```
ssh yourname@localhost
```
and when it hangs and doesnt do anything i type 
```
ssh yourname@xx.xx.xxx.xxx.xx
```
where instead of the x's i put my IP address

I am trying to connect from the computer same computer both times which is the computer im hosting the server on

---

### Post by drjimmy42 on 2009-03-03
Is the ip address you are using your external ip address or the one assigned to your ubuntu box by your router?  If its the internal one its most likely a 192.168.*.* sort of address.

If you are trying the internal one, it should still work.  In that case try adding a -v to ssh to see where it hangs up.

If you are trying your external address assigned to your router by your ISP, then you need to forward port 22 on your router to the local ip address of your ubuntu box.  right now traffic shows up at port 22 on your router and it tells it to go away.

---

### Post by killjoy123987 on 2009-03-03
I have already port forewarded port 22 on my router but it still doesn't work

```
Myname@Myname-desktop:~$ sudo ssh Myname@70.27.168.56 -v
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 70.27.168.56 [70.27.168.56] port 22.
```
at the risk of getting hacked there is what i got and then it stops and doesnt do anything

---

### Post by drjimmy42 on 2009-03-03
Can you ping that address?
You might try nmap (apt-get install nmap) to scan the ports of that ip address and see what appears open from the outside.  Most routers won't respond to ping so use nmap with the -P0 option.

Do you have any other ports forwarded on your router?  Are they working correctly?

---

### Post by killjoy123987 on 2009-03-03
```
Starting Nmap 4.62 ( http://nmap.org ) at 2009-03-03 21:53 EST
All 1715 scanned ports on bas3-barrie18-1176217656.dsl.bell.ca (70.27.168.56) are filtered

Nmap done: 1 IP address (1 host up) scanned in 36.977 seconds
jeremy@jeremy-desktop:~$ 

```

is what i got from nmap

the only other port thats foreworded was my utorrent from windows and i believe it worked correctly

---

### Post by drjimmy42 on 2009-03-03
It appears as though port forwarding is not working.  If the port were open you would see something like this.
> 
~> nmap -P0 myhost.com

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2009-03-03 21:57 EST
Interesting ports on myhost.com (x.x.z.y):
Not shown: 1696 closed ports
PORT    STATE SERVICE
22/tcp open  ssh

Nmap finished: 1 IP address (1 host up) scanned in 3.031 seconds

You might check the doc for your router to make sure you have port forwarding set up correctly.

---

### Post by killjoy123987 on 2009-03-04
To port foreward i used the turorial for ssh on [http://portforward.com/]("http://portforward.com/")
i looked at the bellsupport and they used the same method

---

### Post by drjimmy42 on 2009-03-04
I'm not sure what could be wrong, but according to nmap, that port is not open. Even if it were open and no one was listening it would show something.

---

### Post by killjoy123987 on 2009-03-04
Hey I got it to work. It turns out i wasn't port forewarding the right computer. when i did it to my computer it all worked. Thanks for all the help.

---

### Post by mjramon on 2012-06-12
> **killjoy123987 said:**
> Hey I got it to work. It turns out i wasn't port forewarding the right computer. when i did it to my computer it all worked. Thanks for all the help.
 Can you tell us, how do you solve the problem?, please, regards.

---

### Post by efflandt on 2012-06-12
Something to note is that many broadband routers (or by default when Linux itself is a masquerade router) do not route LAN2LAN via public IP (possibly to prevent IP spoofing).

I have a 2Wire 2701HG-B (DSL wireless/router/modem), and have connected ssh in through it from the internet.  But I have had no reason to try locally connecting through my public IP when I can connect directly to LAN IP.  So I was not sure if the 2Wire blocks LAN2LAN via PPPoE IP.

---

### Post by madverb on 2012-06-12
Nevermind.

---

