---
title: "Remote Shell"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by sanubie on 2009-04-21
I have a few computers at home all connected through my wireless linksys router. Linux is very intriguing to me. I love it. Linux taught me a lot about computers. One thing I've been wondering about lately is the ability to login to remote shell within my network, and control the computer on the other side. Now obviously I could probably do this easier if all my computers were running Linux. But one of them is running Mac. It's an older 10.3..something model. But I was playing around with it the other day and discovered the terminal. It appears to work just like the shell I'm used to already. Would it be possible to ssh to the mac on my network and get access to a remote shell? How would I go about doing this? I'm not sure how to interact with the computers on my network.

---

### Post by skintythe1andonly on 2009-04-21
ssh-server is already installed in your mac as far as i am aware (leopard anyways), you should be able to login straight away.

simply go to the terminal and type (assuming you have ssh-client installed)

```
ssh mac_username@mac_local_ip
```

i have found logging into a mac a lot slower than to another pc running linux. The problem with macs though is that a lot of their software in GUI based meanwhile in linux everything can be done from the command line

---

### Post by sanubie on 2009-04-21
> **skintythe1andonly said:**
> ssh-server is already installed in your mac as far as i am aware (leopard anyways), you should be able to login straight away.

simply go to the terminal and type (assuming you have ssh-client installed)

```
ssh mac_username@mac_local_ip
```

i have found logging into a mac a lot slower than to another pc running linux. The problem with macs though is that a lot of their software in GUI based meanwhile in linux everything can be done from the command line

Yea, but how do I set up the public key/private key? And when I check in my browser we all have the same IP address. Is that normal? I tried logging into my Linksys router a hundred times -- to see if I could assign IP's to the computers on my network. But the default password just doesn't work.

---

### Post by skintythe1andonly on 2009-04-22
I think you mean you all have the same external ip that your ISP has assigned to you. That is what you need if you want to login from outside your local network. That would be the next step. Your router should assign a local ip for your local network. It is generally something like 192.168.x.x. On my home network I have 192.168.0.1 as my router, 192.168.0.2 as a network hard drive and so on.

you should be able to see the value on each computer by typing ```
ifconfig
``` on linux and mac machines, and ```
ipconfig/all
``` from the command line on windows machines

When you first login, its keys are setup automatically. I dont know too much about how to configure them but know there is loads of info about it if you look. You generally dont need to worry about it for a small network. Where it will come into play is if you want to lock it down so only certain machines can login, or if you want to create a shortcut instead of using an ip address, or if the machine assigned to that ip changes.

---

### Post by sanubie on 2009-04-23
Okay, for some reason it is not working. I have a Linksys router, and I am now able to access the admin web tool, but I'm not sure what I'm looking for. 

I went to Google and typed in What is my IP, and tried that with the ssh command, but it doesn't work. For example: 

ssh mac_admin@mac_local_IP address here

but then it responds with 

```
Could not resolve hostname mac_local_IP-address-here: Name or service not known.
```

I also entered the command

```
ifconfig
```

It comes back with something. But I'm not sure what I'm supposed to use. There should be 3 computers on my network. All I see is Link encap:Ethernet, something, something, inet, something addr, inet6 addr, etc. I have no idea what to use here.

---

### Post by SmoothDetonator on 2009-04-23
First, let's go over internal and external ip addressing.  If you go to whatismyip.com, you will see an ip address that is assigned to you by your ISP provider.  This external ip address will be the same for every computer within your home network.  The ip address you need is the internal ip address.  This is probably assigned by your router.  Each computer on your network should have a diferent internal ip address.

Now, go to your mac, fire up the command line, and type in the following:
```
ifconfig
```Hopefully, you will see a lot of code that begins with something similar to the lines below:
```

eth0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
         inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0

```Look for the address following "inet addr:".  Write this down.  Here, the example is 192.168.1.100.  In most cases, your address should look very similar, such as 192.168.1.101 or 192.168.0.100.

 Now, go to your computer running ubuntu.  You will need the ip address from above that you wrote down.  Now, let's assume your address is 192.168.1.100 and the username you use for your mac is mac_admin.  If these were true you would type in:
```

ssh mac_admin@192.168.1.100.

```As you'll notice this follows the same format that skintythe1andonly gave you:
> 
     Code:
     ssh mac_username@mac_local_ip 
You just need to insert your own 'mac_username' and 'mac_local_ip'

---

### Post by sanubie on 2009-04-24
Thanks a lot for you guys help! I have almost got this squared away. But now I'm having another problem. It asks for a password, I put in my password. That didn't work. I tried another one, and then the prompt changed. It asked for the mac password. Well, I know I'm entering the right password for the mac, but it doesn't work. Am I doing something wrong?

It says: 

> Permission denied (publickey,gssapi-keyex,gssapi-with-mic,password,keyboard-interactive).

wow... there's some weird things happening. It does the same thing no matter what I type. The prompt just changes, I suppose to tell me what password I should be entering. For the hell of it, I tried entering the password all in caps. This time it did something different. It said: 

> Read from socket failed: Connection reset by peer

What is the deal here?

---

### Post by SmoothDetonator on 2009-04-24
For some reason, the ssh host (your mac machine) is not allowing access.  Make sure that you are not logging in as root.  That can cause problems.  The answer to your problem will probably be in your ssh_config file.  This should be found in your /etc/ssh directory.  Look for something in that file regarding authentication, such as RSAAuthentication, which should be yes.  I'm not sure if that is your problem, but if you would like to post your ssh_config file, I'm sure someone can point you in the right direction.

---

