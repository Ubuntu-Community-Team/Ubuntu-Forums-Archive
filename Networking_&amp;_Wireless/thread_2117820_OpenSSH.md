---
title: "OpenSSH"
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by Rae8iesi on 2013-02-19
Hello,

I recently purchased an old (but still functional) Dell Server, and then put Ubuntu Server edition onto it. It has been my first time with it and I have having loads of fun learning the command line stuff.

The reason I bought the server was to use it as an SSH Tunnel for my friends and I. I got the OpenSSH Server running on it and have managed to connect to it from other computers (Windows) using Putty. I haven't tried connecting to the server from outside of the network, but I'm guessing you just forward the port for the server and type in the external IP of the network instead of the internal IP. Please correct me if I am wrong.

I am just testing it with the computers at home, and have made 3 accounts (for my friends), these account don't have admin access so they can't do anything (that my friend's are capable of doing) but tunnel.

I know this has been a bit long winded, but here are my 2 questions:

1) Is there anyway to monitor (from my admin account) what is going on? I mean, who is currently logged on, who is consuming the most bandwidth being used by each user, the amount of data downloaded from each user, etc. (I know this is a lot, but so far the possibilities of Ubuntu seem limitless, so it's worth asking!)

2) Is there any way of controlling my friends? I mean, if I find out they are viewing inappropriate websites, etc, can I ban them? Or limit their bandwidth if they are slowing the connection down?

Thanks in advance, and any advise, whether is pertain to these questions or not would be much appreciated,
-Oliver

---

### Post by The Cog on 2013-02-19
>  I'm guessing you just forward the port for the server and type in the external IP of the network instead of the internal IP.Yes. I think it's UDP port 1194 that you must forward.

Do you plan to simply route them back to the internet, or to provide a proxy web server for them?

EDIT:
That's what happens when I answer posts while I have a cold. You wrote OpenSSH tunnel and I read OpenVPN tunnel. So I end up writing rubbish. Please ignore this post.

---

### Post by TheFu on 2013-02-19
> **The Cog said:**
> Yes. I think it's UDP port 1194 that you must forward.

Do you plan to simply route them back to the internet, or to provide a proxy web server for them?

Last time I checked, tunneling a port over ssh was was selected by the person setting up the tunnel.  Only the specific port where ssh listened was under the admin control. That is usually 22/tcp, but I never simply forward that port from public IPs.  Use your router to do forwarding AND port translation. Pick a high port on the router, but forward it to server:22 like always.  That way you don't need to change any defaults internally and normal ssh security techniques work without changing the internal port setup.

Monitoring what other people are doing on UNIX/Linux is easy, if you know the commands.  Sadly, I can't tell you the commands to use here, since there are a mix completely dependent on what you want to monitor.  **ps, vmstat, lsof**,and many others will do that.  I'd suggest that read** UNIX Power Tools** from O'Reilly to get a feel.

You can ban a user easy.  Lock their user account.

You can throttle a user easily, use iptables.

I wouldn't allow people to tunnel through my servers unless they were paying, we had a legal contract that prohibited illegal use, and I was 100% positive they wouldn't use it for porn or copyright violations.

If they have a shell on the box, then local root-escalations are possible on many Linux systems. The community is much more concerned about remote access and remote root access, which is much worse, but there have been some ingenious local root escalations over the years.

BTW, buying a server for an ssh tunnel seems like overkill. I hope you plan to do something else with it.  A $75 Atom-based mini-PC or $22 ARM device can easily provide an ssh tunnel.

I hope you are using key-based authentication, **not passwords**, and have **fail2ban** or similar running too.  There's no need for anyone without credentials to get free password cracking access forever.

---

### Post by Rae8iesi on 2013-02-19
Thanks for the replies! I have changed the default ports on internal machines to a custom port because I have having issues with Port 22 for some reason. 

Could you possibly give me a quick command to lock their accounts? I have just discovered how to delete an account, but it is slightly inconvenient to delete and remake accounts when something happens!

They will be paying me. And thanks for the advise, I should probably draw up some sort of contract. I wasn't going to buy a dedicated one originally, but I found 3 Dell PowerEdge 2650's on eBay for 15 GBP! And I know they are very outdated not, but I'm going to use one of them for SOCKS Tunneling.

I want to use keys, but I have no idea how they work. And how to use them. And I don't know if I really want to use them because if I'm going to be "renting" spaces on the server off then it might back slightly inconvenient to be passing around keys. All my passwords are over 35 chars, random, and with letters and numbers. I know that's not as secure as keys, but will those passwords suffice?

And what is fail2ban?

Thanks again,
-Oliver

---

### Post by The Cog on 2013-02-20
Sorry for the wrong post earlier.

The quickest way to lock an account is 
```
sudo passwd -l username
```
but this won't throw the user off or disconnect his existing connections, just prevent him logging in again. I don't know of a good way to forcibly disconnect anyone except maybe
```
sudo killall -9 -u username
```

I can't think of an easy way to control what they're looking at unless you run a proxy and have them use that (will work for web browsing only). You can use iptables to block http (port 80) on a per-user basis with the --uid-owner qualifier.

---

### Post by TheFu on 2013-02-20
> **crowoy said:**
> Thanks for the replies! I have changed the default ports on internal machines to a custom port because I have having issues with Port 22 for some reason. 

That is scary. Could it be that someone has already highjacked the box?  I'd want to figure out the exact issue around port 22 before doing anything else.  **lsof** will help you figure out which program/process has port 22 open.

> **crowoy said:**
> Could you possibly give me a quick command to lock their accounts? I have just discovered how to delete an account, but it is slightly inconvenient to delete and remake accounts when something happens!

**$ man passwd**
tells me that** passwd -l** doesn't prevent other authentication methods from working. If they are coming in using ssh, then to lock them out, you need to either delete the account or **sudo usermod --expiredate 1 **. Read that man page for details. BTW, I did not know the answer to this - only by carefully reading the man page for passwd, did I see the issue.

> **crowoy said:**
>  They will be paying me. And thanks for the advise, I should probably draw up some sort of contract. I wasn't going to buy a dedicated one originally, but I found 3 Dell PowerEdge 2650's on eBay for 15 GBP! And I know they are very outdated not, but I'm going to use one of them for SOCKS Tunneling.

I suspect that you would have preferred to have (3) US$100 atom boxes instead after you see the power/cooling bills.  Then there is the noise issue.

> **crowoy said:**
>  I want to use keys, but I have no idea how they work. And how to use them. And I don't know if I really want to use them because if I'm going to be "renting" spaces on the server off then it might back slightly inconvenient to be passing around keys. All my passwords are over 35 chars, random, and with letters and numbers. I know that's not as secure as keys, but will those passwords suffice?

Keys are more convenient than passwords AND more secure. That doesn't happen very often in life - where the more secure solution is also the more convenient one.  There are subtleties of using keys on a commercial offering that I won't try to explain ... just that you want to provide them with their private key and install their public key into their ~/.ssh/ directory. This way, you never need to give them a password to your box. Just keys are used. It is a beautiful thing.  If I were doing this, I'd create the keys with a passphrase too - really long, so you know they don't share it easily. Of course, anyone with a little gpg/openssl knowledge can strip the passphrase off the key, so it will only protect you from abuses until they realize that fact.

Check out **ssh-copy-id** for how to easily push keys to remote systems.  **ssh-keygen** is how you create keys. 2K keys or larger, please.

You probably want an ssh-primer first.  I find that learning by watching youtube is often helpful.

> **crowoy said:**
>  And what is fail2ban?
Google will explain the details.
**sudo apt-get install fail2ban**
**man fail2ban **
will install and explain the complete fail2ban system. Since you've elected to change ssh from port 22, you'll need to read the man page.

Sorry to send you to read the man pages so much (RTFM), but all that you want to know is inside there. Use the **apropos **command to search all the man pages, when you don't know exactly what you are seeking.  

*Give a man a fish .... teach a man to fish ... *

---

### Post by kevdog on 2013-02-20
What you are asking to do is rather difficult.

You should first probably create a linux jail for both of your users -- that would limit the executables that could be run from both of their accounts. 

In order to block websites and restrict content, I'd recommend two options:
#1 - A properly setup firewall (iptables or ufw (gufw if you want it gui).  This probably more protects your machine, but it can also block various ports
#2 - Configuration of a web proxy such as squid -- this would be the actual blocking mechanism where various websites could be altered.

---

### Post by TheFu on 2013-02-20
> **kevdog said:**
> What you are asking to do is rather difficult.

You should first probably create a linux jail for both of your users -- that would limit the executables that could be run from both of their accounts. 

In order to block websites and restrict content, I'd recommend two options:
#1 - A properly setup firewall (iptables or ufw (gufw if you want it gui).  This probably more protects your machine, but it can also block various ports
#2 - Configuration of a web proxy such as squid -- this would be the actual blocking mechanism where various websites could be altered.

+1 - anytime you allow someone remote shell access into your server (like with ssh), you are asking for lots of pain.  If you just want to provide a remote proxy service over a VPN, perhaps OpenVPN would be a better solution?  It will have lower network overhead than ssh over TCP, since OpenVPN can use UDP too.

Using squid as a proxy and filter is not hard, but it is hard to prevent someone knowledgeable about networking from getting around if squid is on the same machine where they have an account.  I suppose some complex iptables configs might be able to accomplish this too, but I'd rather just have the proxy running on another box, set it as the default gateway and block all other internet traffic from the machine where user accounts work except the VPN.   Network architecture is a big part of security.

---

### Post by Rae8iesi on 2013-02-20
Thanks again everyone for all the replies!

I have made quite a lot of progress on the server. I finally have managed to get it to work on Port 22, I don't know why it wasn't working, but after shutting down other machines on the network, it worked! (Probably not the most conventional way of doing it!) But now, when I port forward my router for non-LAN access, I will hopefully be about to have requests coming into a port, and translated to port 22 for my server.

I didn't realise that you could just **man** something to find out about it, very useful, thanks!

I am still working on the whole keys thing, but hopefully will get those set up. Although I am still a bit baffled as to how I am supposed to get them off the server and say, onto a memory stick. I have Google'd it and most of the explanations involve LOADS of commands I don't know.

I considered having a VPN (say, through LogMeIn Hamachi) and then running some sort of Proxy through it (say, Privoxy). However, I don't really know if that will work, if it will be secure and encrypted, and whether I will be able to take it into school, all on one memory stick and connect to it. Because if it comes down to just me using the SSH Tunnel inside of school, I want to be able to have a portable Firefox (with proxy settings configured), then click a .bat file which will run Putty (also portable) and connect to the server at home, which I don't think would be possible with a VPN + Proxy because the school has loads of system restrictions.

I just have a quick question on the client side of things. I mentioned that I wanted to run a .bat file to execute a connection using Putty, the reason for this is that Putty doesn't save all the information I want it to (It saves Sessions, but does not save the D9000 in Tunnelling or Proxy settings (which the school have)). I noticed that I could make a .bat file that looked something like this:

**sudo putty -D 9000 -p 12345 username@server**

To connect. However, I was wondering how you would integrate a key and HTTP/HTTPS proxy into that .bat file. If you have any ideas (or alternatives), then please let me know.

Thanks again for everything,
-Oliver Crow

---

### Post by TheFu on 2013-02-21
> **crowoy said:**
> I am still working on the whole keys thing, but hopefully will get those set up. Although I am still a bit baffled as to how I am supposed to get them off the server and say, onto a memory stick. I have Google'd it and most of the explanations involve LOADS of commands I don't know.

```
$ man cp
```Don't over think this.

Whenever you see a command that you don't know - use the **man** command to understand it.

> **crowoy said:**
>  I considered having a VPN (say, through LogMeIn Hamachi) and then running some sort of Proxy through it (say, Privoxy). However, I don't really know if that will work, if it will be secure and encrypted, and whether I will be able to take it into school, all on one memory stick and connect to it. Because if it comes down to just me using the SSH Tunnel inside of school, I want to be able to have a portable Firefox (with proxy settings configured), then click a .bat file which will run Putty (also portable) and connect to the server at home, which I don't think would be possible with a VPN + Proxy because the school has loads of system restrictions.

This is the first time you mentioned coming from a school network.  I double ssh tunnels will work either if openvpn doesn't work.  Often, the only way around it is to setup whatever listener (ssh, vpn, whatever) on port 443 which they probably will not filter, though they should filter any traffic going to non-static ISP ranges.

> **crowoy said:**
>  I just have a quick question on the client side of things. I mentioned that I wanted to run a .bat file to execute a connection using Putty, the reason for this is that Putty doesn't save all the information I want it to (It saves Sessions, but does not save the D9000 in Tunnelling or Proxy settings (which the school have)). I noticed that I could make a .bat file that looked something like this:

**sudo putty -D 9000 -p 12345 username@server**

To connect. However, I was wondering how you would integrate a key and HTTP/HTTPS proxy into that .bat file. If you have any ideas (or alternatives), then please let me know.

When we suggest using a VPN, we are really suggesting that YOU run an OpenVPN server on your new "server" and allow access from outside clients. 

Sorry, I can't help with putty issues. Don't use it, but I did about 5 yrs ago and the keys worked as did saving the tunnel settings.  Perhaps you just need to read the man page for putty?

Lastly, there is absolutely ZERO reason to use sudo with putty.
* sudo is on Linux, not windows
* putty does not need administrative rights to run
* using sudo too much, especially when not needed can screw up your linux system file permissions. **Understanding file permissions is critical to running a secure Linux computer.**  Linux is designed as a multi-user OS from the ground up. It isn't like MS-Windwos where you never really needed to understand permissions.

---

