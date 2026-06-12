---
title: "seamless ssh through intermediate host?"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by anlag on 2010-09-17
My situation is that I've got a home connection, with a router that my ISP won't let me access (to forward ports etc), and all incoming ports blocked as far as I can tell. I would like to be able to get around this and allow incoming ssh connections to a home PC. To facilitate this I've got an (user) account on a remote shell account, which does not have all its ports blocked and which I'd like to use as an intermediate to ssh into my home machine.

What I've managed so far is to ssh into the shell account (let's say it's on intermediate.host) and tunnel a port back to my home machine (let's call it home.host) by running the following on home.host:

ssh -fNR7777:localhost:22 [email]myuser@intermediate.host[/email]

Then, I can ssh into my home machine from the shell account with a simple:

ssh -p 7777 myuser@localhost

OK, well and good, in principle I can then ssh into the intermediate from anywhere, and from the intermediate ssh into my home machine. BUT, I'm curious if it's possible to make this a seamless procedure so that if I connect on a particular port to the intermediate, it simply puts me onto the home machine directly (with appropriate ssh keys in place, of course.)

One reason is it would be more convenient. Another is I would like to be able to make sftp connections to the home machine from anywhere, which I don't see would be possible with the above method. Still, it should be possible, right?

So three questions basically:

1. Can I somehow make the connection to my home go seamlessly through the intermediate host?
2. Can I do this without root access to the intermediate? (I've only got a regular user account there.)
3. Is there any way to do this so that another person could reach my home machine (say for sftp access) without giving him my login details for the intermediate host? (I would create an own account on the home machine, obviously.)

Sorry that got a bit lengthy, but I wanted to account thoroughly for the situation. Very grateful for any help! 

Cheers.

---

### Post by BkkBonanza on 2010-09-17
You shouldn't need to login to the intermediate host to connect to your home ssh server. As long as the reverse tunnel is up and listening on *:7777 you should be able to do this,

ssh -p 7777 [noparse]homeuser@intermediate.host[/noparse]

it will forward that connect to your home port 22 where it should be answered. The key is that the reverse tunnel has to listen on the public IP, or * for any. It won't accept connects on localhost from the public.
eg. your tunnel should be,
[noparse]
ssh -fNR 7777:publicIP:22 myuser@intermediate.host
[/noparse]
sftp, scp and rsync should all work fine over the tunnel as long as the port is specified. Since Nautilus supports sftp natively you should be able to use sftp://intermediate.host:777/path/to/files to get to them.

ftp(s) on the other hand requires multiple ports tunneled and I'm not sure of the details of how it co-ordinates them since I never use it any more. 

In this case I would say maybe the simplest solution is to set ftp to use a SOCKS proxy and then start ssh on the remote system in -D mode connecting to your intermediate host via ssh. Then the ftp session will appear to your server as though on your home machine.
eg. on remote machine,

ssh -D 8080 -p 7777 [noparse]homeuser@intermediate.host[/noparse]

now tell ftp to use SOCKS5 proxy at localhost:8080 and it should connect via ssh to your home machine and access the LAN as if local. 

BTW the easiest way to handle the port 7777 is to add, (at the end)

Host intermediate.host 
Port 7777

to your /etc/ssh/ssh_config file or ~.ssh/config (if just for you only) and after that you don't need to keep telling things to use that port for that host.

---

### Post by anlag on 2010-09-17
Thanks! But I'm still struggling a bit with understanding how to make the intermediate host open for ssh connections on a non-22 port. This part:

> **BkkBonanza said:**
> The key is that the reverse tunnel has to listen on the public IP, or * for any. It won't accept connects on localhost from the public.
eg. your tunnel should be,
[noparse]
ssh -fNR 7777:publicIP:22 myuser@intermediate.host
[/noparse]

I assume I run that command on my home machine? I tried it with * and it seemed to do the same thing as before. If I use the public IP, is that the public IP of the home machine or of the intermediate?

I'm guessing I'm doing something wrong with that step, because if I try to ssh to the intermediate on port 7777 (hoping to be passed on to the home machine) I just get this:

ssh: connect to host intermediate.host port 7777: Network is unreachable

Don't I need to somehow tell the intermediate machine that when it gets a connection on port 7777 it's an ssh connection? And then, that it should be sent on to my home address?

---

### Post by BkkBonanza on 2010-09-17
> **anlag said:**
> 
I assume I run that command on my home machine? I tried it with * and it seemed to do the same thing as before. If I use the public IP, is that the public IP of the home machine or of the intermediate?

Yes. Public IP of intermediate machine since you're telling it which IP to bind on for listening and it must be that machine's. But I didn't check the docs before and the two things are needed... the syntax is like this,

ssh -fNR *:7777:localhost:22 [email]myuser@intermediate.host[/email]

(the bind address on the host comes first and defaults to localhost when not indicated) and (important!) the **GatewayPorts** option must be enabled in sshd_config on the host. Otherwise it only binds local. It's all in the docs but last time I was going by memory - my mistake.

> **anlag said:**
> 
ssh: connect to host intermediate.host port 7777: Network is unreachable

Make sure a firewall isn't blocking port 7777.
> **anlag said:**
> 
Don't I need to somehow tell the intermediate machine that when it gets a connection on port 7777 it's an ssh connection? And then, that it should be sent on to my home address?
No. It listens on port 7777 and whatever it gets it passes down the tunnel to your machine port 22. It is your sshd that responds, back up the tunnel to go out on 7777 again. It's a dumb tunnel not socks or anything, it just passes data packets each way.

---

### Post by anlag on 2010-09-17
> **BkkBonanza said:**
> and (important!) the **GatewayPorts** option must be enabled in sshd_config on the host.

Ack! Looking in /etc/ssh/sshd_config on the intermediate host, I find this as the only relevant entry:

#GatewayPorts no

Although it's commented out, the man page confirms the suspicion that the default setting is indeed "no". I tried the updated command anyway and it gave me the same "network is unreachable" again. 

Don't suppose there's any way I can do what I want with that intermediate host then?

---

### Post by BkkBonanza on 2010-09-17
After you update that option you have to force sshd to reload it's config. 
Like this,

pkill -HUP sshd

After you do that, then start the ssh tunnel. Then on the host run,

sudo netstat -lntp

to show what processes are listening on what ports. You should see sshd listening on 7777. If not then there is a ssh-sshd config problem. If it is then check what address it is bound to. If that looks right and you still cannot connect then check iptables for firewall blocks.

sudo iptables -vnL

---

### Post by anlag on 2010-09-17
Right, unfortunately that's where I run into the problem that I don't have root access on the intermediate host. I'll try and have a word with the admin of that place though, see if they can do something for me. If not, I'll try to find somewhere else to do it... quite keen on seeing it work now, one way or the other, if only for the satisfaction of knowing how to accomplish it in future cases. ;-)

Thanks a lot for your help in any case. I'll revisit this topic when I've got some more progress.

Oh yeah, no alternative way to do it without root I suppose? I imagine that gateway setting would put a stop to it, pretty much?

---

### Post by BkkBonanza on 2010-09-17
No, you'll need root to change the sshd config and reload it.

You may want to look at **[Amazon EC2]("http://aws.amazon.com/ec2/")**. If you want I can give you a primer on it. You can start an on-demand server node for any brief or long period to do some testing/work, and then shut it down - all using linux commands on your machine. Very low cost if you don't keep them up 24/7. 

For example, running a t1.micro spot instance can cost 0.7 cents/hour (not dollars, cents) and is great for this kind of thing. You need an AWS account but can sign up with a credit card very easily.

Here's how I start and run a remote server as needed, once I've configured the aws perl script from [timkay.com]("http://timkay.com/aws/"), (and setup a key and some config at Amazon control panel),

ec2rsi ami-1234de7b -p 0.01 -t t1.micro
(request spot instance, specify type, ami, max price)
(ami-1234de7b is the ID for an Ubuntu 10.4 machine image)

ec2din 
(check if my instance is ready... may have to repeat for a few minutes)
(will output your instance id and URL for your server)

ssh -i .ssh/myAWSkey.pub ubuntu@aws-URL-from above
(now I'm logged into my instance)
(sudo change sshd config, look around)

(open another local terminal, and type)
ssh -fNR *:7777:localhost:22 ubuntu@aws-URL-from-above

(my tunnel is up, see if I can connect to myself)
ssh -p 7777 me@aws-URL-from-above

Fun!

---

### Post by anlag on 2010-09-17
Hey that does look like fun :) Not sure what a primer is, but why not? Looks worth trying out at any rate.

---

### Post by BkkBonanza on 2010-09-17
A primer would be me just laying out details and steps here. Or I could talk you through it realtime in a chat window. Either way, it's always a bit of fun. 

Realtime would have to start with you signing up at AWS (Amazon Web Services) otherwise you can't get into the AWS Control Panel to create a key etc.

---

### Post by anlag on 2010-09-17
Either way is great with me, though I need to be off for pizza and football for a few hours so can't do real-time chat just now. :-) But I'll look in again later, and try to set up that account. Can take it from there I think, whichever way you prefer it.

Thanks again for all your help.

---

### Post by BkkBonanza on 2010-09-17
I'll lay out the basic steps here for when you get back, and for others who want to try it out...

1. You need an [AWS Account]("http://aws.amazon.com"). That's easy, sign up at their web site using a credit card.

2. Login into your account and check the "Account Activity" section. It should all be fresh starting at zero fees. Click the "Security Credentials" section. You should see a tab called "Access Keys". Later you'll want to copy and paste some values from here so you can use the linux command line tools.

3. Now up at top, click the **Management Console** link. It takes a few seconds to load up. This is where you config and control things. It's more user friendly than linux commands but it's also slower to login in and do things than working at the cmd line.

4. Click the **EC2** tab. Bottom left, click "**Key Pairs**". We'll create an SSH key pair to use for logging into your instances (servers). Click create key pair. Give it a name - I usually just use my own name but whatever you like. Click Create. It will generate a new key for you and prompt to save it locally on your system. Save it.

5. Once it's saved, move it over to your home .ssh directory and set the permissions on it (chmod 400 key.pem). Now it can be used for logins.

6. Back on the console, above Key Pairs, click "**Security Groups**". This is the AWS name for Firewall - where you set the open ports on your server. There should be a default security group. Click that line. In the scroll box below click "**Custom**" and choose **SSH**. This will enter some values, port 22 etc. Click "**Save**" over on the right. Now you have port 22 open for SSH access. Other ports can be managed here too. That's is all for now though.

7. Now over on the left menu, click "**Spot Instances**". An instance is an "up and running server at your command". There are many types based on CPU and memory resources allocated. Faster, higher memory instances cost more. We're going to use a "micro" size "spot" instance because that's the very cheapest for learning on, and is also good for low intensity tasks. "Spot" means we put a "bid" on an instance and as long as the current "market price" doesn't go over that bid, we can keep using our instance. The advantage is that it's much cheaper than a regular price instance. You are also charged for data transferred, but it's cheap too. So let's go...

8. Click the "**Request Spot Instances**" button. Then choose "**Community Instances**". These are pre-built public machine images ready to run. In the entry field next to Images, type **ami-1234de7b** and press enter. This is an Ubuntu 10.4 32 bit image, located in the East US data center. You should see a description show up in the list. (For other handy ready to use Ubuntu images see, [Alestic.com]("http://alestic.com/"). They're one of the main builders of ready-to-use Ubuntu images.) Click the "**Select**" button to the right of the description.

9. Here's where we choose what type of instance to run and how much we'll pay. In the upper middle click the "Instance Type" dropdown box and choose "**Micro**". Then below enter a Max Price of **0.01** (that's 1 cent/hour). Usually Micro  runs at 0.007 but by allowing up to 0.01 we have a bit of breathing room for market variations. Next, click "**Continue**", bottom center.

10. Now you can choose different kernel and ramdisk settings - we don't need to change these. Click "Continue". Next you should see your default "key pair" show in the list. Good. That's the one we just created. Click "Continue". The default "security group" should be selected. Good. That's our default firewall config we just setup. Click "Continue".

11. Here's the details summary. Check it over. Make sure only 1 instance at the 0.01 price will be started for you. This will put in a request to start ONE super cheap Micro server for you at a MAX cost of 1 cent per hour. Ok with that? Click "**Submit**". 

12. Close the info page that pops up, and you should see your pending request in the list. It's waiting to be started usually within a minute or two. You can click the "**Refresh**" button to update the status. When it changes to "**Active**" you can click on the "**Instances**" menu button on the far left, and you should see your running instance listed there. (If not shown then click "Refresh"). Yay!

13. Click the instance line. On the lower panel you will find the details of your instance. The main item of interest is the **Public DNS** value. Mark and **copy that URL** (or just remember the IP value). This is the address where you can login into your hot new server...

14. Open a terminal on your desktop. We're going to login with SSH and the key you saved earlier. Type,

ssh -i .ssh/**yourkey**.pem ubuntu@**paste-the-public-DNS-here**

It should do the normal thing, tell you it hasn't seen this host key before, and give you a prompt on your server. Great. Type a few commands. Install some Ubuntu packages like "htop" with apt-get. Enjoy. This is your server for now.

15. When you're done. Either poweroff (**sudo poweroff**), or logout, and return to the Amazon Console, select your instance line, click "**Instance Actions**", and "**Terminate**". Click "Refresh" until you see the status change to "**Terminated**". Make sure you do this or you will continue to be charged per hour that it runs. At this rate that is $5/month.

16. That was your first exciting adventure into using Amazon EC2 and it cost you less than 1 cent. Of course, now you know how you can experiment with servers on demand, try out various ssh tunnels, alter the sshd_config at will using sudo - you have full root control here. Hope this intro gets you started, and later you manage to get your tunnels happening. 

Part two - how to setup Linux cmd line tools to make this all *fast*. Later... Cheers!

---

### Post by SeijiSensei on 2010-09-17
I'd suggest you look into [OpenVPN]("http://openvpn.net/") as an alternative.  You can set up a simple shared-key arrangement with the home computer as a client and the remote machine as the server (assuming you can see the remote from home).  You will need to designate an arbitrary port on the server machine that is visible to the client at home.  Once you've got it set up, you'll have a full-time encrypted tunnel between the two machines.  You can then simply ssh to the home machine's VPN IP.

Here's an example:

On the client create the file: /etc/openvpn/yourlink.conf

dev tun
remote your.remote.com
ifconfig 10.0.0.2 10.0.0.1
secret /etc/openvpn/myshared.key
port 33333
user nobody
group nogroup
comp-lzo
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key
verb 3

On the server, the file looks identical except it doesn't have the "remote" parameter and the order of the IP addresses in the ifconfig statement will be reversed.  Make sure myshared.key is readable only by root (chmod 0600 /etc/openvpn/myshared.key).

If you need to add routing through the tunnel, you can use the "up" parameter to run a script after the tunnel is created.

---

### Post by anlag on 2010-09-18
> **BkkBonanza said:**
> I'll lay out the basic steps here for when you get back, and for others who want to try it out...

1. ...

Part two - how to setup Linux cmd line tools to make this all *fast*. Later... Cheers!

Great! Done all that, worked like a charm. Only difference is since I'm in Denmark, I used the EU West region for a server based on Ireland rather than across the Atlantic. For the image, I simply went to the Alestic website and picked the directly corresponding EU-based one to the Virginia-based one you mentioned, which I found was ami-38bf954c. It's a little more expensive than the one in the states, but I think I can survive the additional 0.3 cents :-) The data traffic price is the same for both regions, which I think in the long run may be the "bigger" cost.

Keeping the instance up and running for now as I toy with it a bit. Whenever you have the opportunity to post step 2, I'm looking forward to it. This is fun. ;-)


> **SeijiSensei said:**
> I'd suggest you look into [OpenVPN]("http://openvpn.net/") as an alternative.  You can set up a simple shared-key arrangement with the home computer as a client and the remote machine as the server (assuming you can see the remote from home).  You will need to designate an arbitrary port on the server machine that is visible to the client at home.  Once you've got it set up, you'll have a full-time encrypted tunnel between the two machines.  You can then simply ssh to the home machine's VPN IP.

Here's an example:

On the client create the file: /etc/openvpn/yourlink.conf

dev tun
remote your.remote.com
ifconfig 10.0.0.2 10.0.0.1
secret /etc/openvpn/myshared.key
port 33333
user nobody
group nogroup
comp-lzo
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key
verb 3

On the server, the file looks identical except it doesn't have the "remote" parameter and the order of the IP addresses in the ifconfig statement will be reversed.  Make sure myshared.key is readable only by root (chmod 0600 /etc/openvpn/myshared.key).

If you need to add routing through the tunnel, you can use the "up" parameter to run a script after the tunnel is created.

Thanks a lot. I've been meaning to look into OpenVPN as well for some time, if mostly for future use when I live in one place long enough to start setting up the servers I would like... However, it seems the intermediate host I would use doesn't have OpenVPN installed. Also, it seems to me from your instructions I would need root access also to make the settings for it, which unless I could get the admins there to help me out would probably rule out this route under these circumstances. Certainly useful for future use though. Maybe on a cloud instance...

---

### Post by anlag on 2010-09-18
Gave it a shot to set up the tunnel as discussed before. 

Turned on GatewayPorts in sshd_config, and restarted it using pkill. Confirming as follows:

> ubuntu@awshost:~$ grep GatewayPorts /etc/ssh/sshd_config 
GatewayPorts yes
ubuntu@awshost:~$ sudo netstat -lntp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      384/sshd        
tcp        0      0 127.0.0.1:7777          0.0.0.0:*               LISTEN      1258/sshd: ubuntu
tcp6       0      0 :::22                   :::*                    LISTEN      384/sshd        
tcp6       0      0 ::1:7777                :::*                    LISTEN      1258/sshd: ubuntu

It says "LISTEN" on the same line as 7777, don't know if that's sufficient? 

Then creating the tunnel locally:

> myuser@laptop:~$ ssh -i ~/.ssh/mykey.pem -fNR *:7777:localhost:22 [email]ubuntu@myhost.compute.amazonaws.com[/email]

No error message to that, trying to connect on that port:

> myuser@laptop:~$ ssh -i ~/.ssh/mykey.pem -p 7777 [email]ubuntu@myhost.compute.amazonaws.com[/email]
ssh: connect to host myhost.compute.amazonaws.com port 7777: Connection timed out

For some reason it still doesn't work. I assume I still need to use the same key when doing the new connection to 7777... Ran the iptables command too, just in case that helps though it's not telling me much:

> ubuntu@awshost:~$ sudo iptables -vnL
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination        

Any ideas?

---

### Post by BkkBonanza on 2010-09-18
That's great you got all that going. Using an EU West instance is a good idea. You should get better response speed to Denmark.

You also need to alter the "Security Group" you setup on the AWS console (allowing SSH, port 22) and add another custom rule for 7777, to allow connections on that port. Maybe you already tried that. AWS must use some form of hardware firewalling since it doesn't show up in iptables at all (output looks fine, all open).

The netstat output isn't quite right. Instead of 127.0.0.1 for listen address, the 7777 line should be like the 22 line where is says listening on 0.0.0.0. I'm not sure why that is yet. 

Couple more points...

Remember to kill the background processes once you don't want the tunnel open any more, since you can only bind **one at a time** to any port. Starting a second tunnel would likely fail with the first still intact.

One more thing... when you run the tunnel cmd you should be able to see that it is active by checking the ps output as follows,

**ps ax |grep ssh**

(will list running processes with "ssh" in output line).

Added: I fired up my own AWS instance to test this out. At first it didn't work and I started digging more and reading. In the end it was only that I hadn't used sudo to do the pkill. It still closed my connection but it di not actually re-read the sshd_config. So beware, you need,

**sudo pkill -HUP sshd**

You should see the sshd pid value change, indicating it is a new process, when you login again.

Other than that I got the tunnel to show up on 0.0.0.0:7777.

---

### Post by anlag on 2010-09-18
> **BkkBonanza said:**
> You also need to alter the "Security Group" you setup on the AWS console (allowing SSH, port 22) and add another custom rule for 7777, to allow connections on that port. Maybe you already tried that.

D'oh! Missed that one, did it now (with a new session, shut the old one down before.) That does help things a bit...

> The netstat output isn't quite right. Instead of 127.0.0.1 for listen address, the 7777 line should be like the 22 line where is says listening on 0.0.0.0. I'm not sure why that is yet. 


Now with the same tunnel command as previously I got it to be:

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      370/sshd        
tcp        0      0 127.0.0.1:7777          0.0.0.0:*               LISTEN      804/sshd: ubuntu
tcp6       0      0 :::22                   :::*                    LISTEN      370/sshd        
tcp6       0      0 ::1:7777                :::*                    LISTEN      804/sshd: ubuntu

Better, right? At least there's a line up there like the standard 22 sshd line. Still, there's the localhost IP listed only... so tried your latest tunnel command (after killing the first one) which I thought would make it work, since in it you've basically changed localhost for *, so locally:

myuser@laptop:~$ ssh -i ~/.ssh/mykey.pem -fNR *:7777:*:22 [email]ubuntu@myhost.compute.amazonaws.com[/email]

> One more thing... when you run the tunnel cmd you should be able to see that it is active by checking the ps output as follows,

ps ax |grep ssh

(will list running processes with "ssh" in output line).

It's there alright:

18685 ?        Ss     0:00 ssh -i /home/myuser/.ssh/mykey.pem -fNR *:7777:*:22 [email]ubuntu@myhost.compute.amazonaws.com[/email]

In fact going a step further, I tried to use the tunnel from the side of the AWS host:

ubuntu@awshost:~$ ssh -p 7777 myuser@localhost

...and that connects just fine to my home laptop. So the tunnel exists and works, it's still only the matter of making it accessible from a third party. I'll see if I can work it out as well but obviously... any further input is most valued. :)

---

### Post by BkkBonanza on 2010-09-18
See my very recent update to my post above. I added an important pkill comment.

Netstat must show listening on 0.0.0.0:7777 otherwise it is still bound to localhost.
I'm about to modify my security group and see if I can connect to 7777.

Edit:
I just realized I can't easily test this here. I don't have sshd installed on my local machine (and don't really want to install it). Once the tunnel forwards back to your home machine it will still needs sshd listening on port 22 to answer the connection. But I think you already have that.

I did use nmap to do a connection test to port 7777 and that showed it OPEN. Which is good.

---

### Post by anlag on 2010-09-18
Wicked! sudo pkill fixed this:

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      945/sshd        
tcp        0      0 0.0.0.0:7777            0.0.0.0:*               LISTEN      1198/sshd: ubuntu
tcp6       0      0 :::22                   :::*                    LISTEN      945/sshd        

However, trying to log on after that asked me for a password:

[email]myuser@laptop:~/.ssh[/email]$ ssh -i ~/.ssh/mykey.pem -p 7777 [email]ubuntu@myhost.compute.amazonaws.com[/email]
[email]ubuntu@myhost.compute.amazonaws.com[/email]'s password: 

I don't have any password for the ubuntu user obviously, so tried getting around it by creating a pair of rsa keys on the AWS host, passing the public one to my laptop and attempting the connection again but no dice.

Without thinking it would actually work, I tried replacing the username when connecting from home on 7777 to my own local username... and that actually worked. :-) 

[email]myuser@laptop:~/.ssh[/email]$ ssh -i ~/.ssh/mykey.pem -p 7777 [email]myuser@myhost.compute.amazonaws.com[/email]
[email]myuser@myhost.compute.amazonaws.com[/email]'s password: 

Entered my local password as that's really the only one I have, and it connected me to my laptop as desired. Smoothed the process out by adding my own public rsa key to my authorized_keys (bit bizarre that...) and the next time didn't even require password.

...

Just now realized I don't even need the keyfile when doing that connection. So any connection on 7777 to the AWS host is not even logged in on there, but just passed on to my laptop. That's even better than I realized it would work, for instance for setting up SFTP access for others I should only need to make them guest accounts on my machine and tell them the AWS address and port... and make sure they don't pull enough data to cost me a lot of money, but I think at 15 cents per Gb (after the first free one) it should be rather acceptable.

In other words: success! A million thanks, your help has been invaluable.

If you don't mind... for doing this regularly, what can I do to set this up so settings etc are saved on the AWS host between connections? Kind of assuming there's a convenient way to do that, for regular users...

---

### Post by BkkBonanza on 2010-09-18
Ha. Good. I was going to mention that your final connection is actually to YOUR home machine and so that is the one you need the user/pwd/key for.

Setting up your own machine (AMI) on AWS isn't too hard. You can take a snapshot of the instance you have customized and then create a new personal AMI from that. This can be done from the console with a few steps. 

The complaint I have is that the custom AMI uses 15 GB of EBS space so you end being charged for that space monthly. I did manage to get around this in a convoluted way so that only a 1 or 2 GB EBS store is needed. It's a bit of work to do that but not so hard. The Ubuntu image only uses about 750 MB of space so having a 15GB partition is just wasteful since any other EBS (data) partitions can be easily mounted when needed.

I need to do this again myself as I want to keep a backup of my own VPS server stored on AWS. In case of a failure I can fire up the backup and be operational again in minutes.

I can write a tutorial on this process as well. I don't mind because I'm keeping a copy for later when I setup a blog someday. But which first, linux cmd line or snap shotting AMIs?

---

### Post by anlag on 2010-09-18
Great. If it's going to incur a running cost then the minimalistic option is the most interesting one for this purpose. As you say, no sense paying for unused space. :-)

Side note, just tested an external connection from the ssh client of my Android phone running on mobile Internet, worked brilliantly as well.

PS. Marking this topic as SOLVED now as the initial topic has been covered more than thoroughly. DS.

---

### Post by BkkBonanza on 2010-09-19
That's cool about the Android phone having ssh. I'll have to get one of those someday.

Here's a quick rundown on using AWS at the cmd line. There is an ec2-api-tools package in the Ubuntu repos but I much prefer [Tim Kay]("http://timkay.com/aws/")'s perl script. It doesn't need java, doesn't use env vars, and has shortcut cmds. Plus I have made custom edits to use my own defaults.

1. Download Tim's AWS perl script. In your terminal,

**wget [http://github.com/timkay/aws/raw/master/aws](http://github.com/timkay/aws/raw/master/aws)**

If you don't have Curl installed you will need that package,

**sudo apt-get install curl**

2. Run the install command, which will copy it to /usr/bin and create symlinks for the shortcuts.

**sudo perl aws --install**

3. Next you need to login to your AWS account and visit the "Security Credentials" page we saw before. You will need the two values from your "Access Key" - the ID and the KEY. The first is visible in the list and the second you have to click to show, and then copy. Back in terminal create the ~/.awssecret file and enter your ID on the first line, and the secret key on the second line.

**nano ~/.awssecret**

When done it should look like this, (but with your key info),

1B5JYHPQCXW13GWKHAG2
2GAHKWG3+1wxcqyhpj5b1Ggqc0TIxj21DKkidjfz

Save it. Type **aws -h** to see a command summary. Good?

4. Try a test command to see that it can access EC2 without error,

**ec2din**

(this is the shortcut for ec2describe-instances and should return with nothing, since you don't have any running instances)

5. That's it. You're now able to manage EC2 and S3 from the command line. Here's a couple more tips. If you use a region other than US East then you will want to put some default settings in the .awsrc file.

**nano .awsrc**

and enter --region=eu-west-1 (for example). You can also add --simple to enable simpler output style (the tables are sometimes too much). Now you don't have to add the region for every command. Save.

6. Let's try to start a spot instance. 

**ec2rsi ami-1234de7b -p 0.01 -i t1.micro -k MyKey**
(use your choice ami and the name you gave your key on the AWS console)
(this is the shortcut cmd for ec2request-spot-instances)

It should respond with info about the pending request.  You can check on the request with,

**ec2dsir**
(short for ec2describe-spot-instance-requests)

If you're quick you can cancel the request with,

**ec2csir -id-**
(where id is the sir-xxxxx value you see in the responses above)
(short for ec2cancel-spot-instance-requests)

You can check every 15-30 seconds on the status of your instance with,

**ec2din**

When it's up and running it will tell you the instance-id and the publc DNS url.

7. When you're ready to shutdown your instance you can use.

**ec2tin -id-**
(where id is the one given you in ec2din output). 
(short for ec2terminate-instances)

There's quite a variety of other EC2 commands to explore too, but these are the real basic ones (for using spot instances). I manually edited my /usr/bin/aws script to have my default ami, price, key built in so that I only need a simple ec2rsi to start an instance. The script is quite readable and so it's easy to adjust the defaults in the cmd table.

Hope this gets you started with some quick and easy commands to use EC2 instances. I'll post a tutorial on creating a custom AMI later...

---

### Post by anlag on 2010-09-19
Neat, all worked great. Saves all that web interface use. I like it. The only difficulty I had was finding the "Security Credentials" page -- kept looking for it in the EC2 control panel, before finding out I had to go higher up in the hierarchy so to speak.

I'll definitely either edit the existing program or just add my own shell scripts to streamline the procedure a little. The AMI ID numbers could get a little tricky to remember...

By the way, while testing things earlier I set up a dynamic DNS address (on dyndns.org) to point at the EC2 instance, also saving not only time and typing but also making it possible to run the same exact commands for different instances. For example, I was thinking of a script that rsyncs a setup script onto the EC2 instance where it's executed, doing things like editing the sshd_config and making sure it's enabled thus saving me having to even do that "by hand". It would be a cheap kind of way to quickly get a customized and ready to use system, without having to pay even for small storage. Probably won't be practical when the configuration goes beyond a few simple steps, but for this ssh tunnel business it should work well enough I'd think (not tried it yet though, need some sleep now...)

The DNS needs to be edited for each instance of course, to update with the new address, which of course adds a manual step early on in the procedure. Unless I can find a nice way to do that too from the command line (scripted, more or less.)

Still definitely interested in making AMI snapshots though, sounds like it will come in handy one way or the other. I mean I've been thinking of paying for an additional shell account somewhere for various uses, this could provide that both cheaper and with increased functionality. Well impressed so far. Will check back for the next tutorial whenever you have time to write that. No rush, mind you, I've got more than enough to work with for now. (Not to mention actual work, hehe.)

---

### Post by BkkBonanza on 2010-09-19
That's a good idea. You can have a script which starts the instance, polls ec2din for it's running status, logs in and appends the Gateway cfg line, pkill the sshd, then updates the dyndns IP (just use wget with correct parms and user/pwd), then exits. After that every should be ready for the tunnel and it likely only takes a few seconds to init all that.

Actually not too hard, eg. tested but not thoroughly,

```
#!/bin/bash

AMI=ami-1234de7b
KEYNAME=MyKey
KEYFILE=MyKey.pem
DYNUSER=test
DYNPWD=test
DYNHOST=test.dyndns.org

ec2rsi $AMI -p 0.01 -i t1.micro -k $KEYNAME

URL=`ec2din |awk '{print $3}'`
while [ "$URL" = "" ]; do
  echo "."
  sleep 15
  URL=`ec2din |awk '{print $3}'`
done

ssh -i .ssh/$KEYFILE ubuntu@$URL <<-EOF
wget -q --user=$DYNUSER --password=$DYNPWD https://members.dyndns.org/nic/update?hostname=$DYNHOST&
sudo tee -a /etc/ssh/sshd_config >/dev/null <<-CFG
GatewayPorts yes
CFG
sudo pkill -HUP sshd
EOF

ssh -i .ssh/$KEYFILE -fNR *:7777:localhost:22 ubuntu@$URL

export URL
echo $URL

```

---

### Post by anlag on 2010-09-19
Excellent, that script ran just fine. Had a feeling you could do something like that with the dynamic DNS but no idea how... very useful. The script in general is certainly shorter than it would have been had I written it too...

So that sets it up for me just fine. Tried tunneling in through 7777 and works great. The only human intervention I had to do while running the script was to accept the RSA key for the AWS host address. Is there a flag for ssh to tell it to accept this automatically only for this single instance? Had a look at the man page but couldn't find it, it's a bit lengthy though (for good reasons.)

Anyhow, that's not a big deal. Slightly more of a bother is that I can't use the dyndns address directly to ssh into the AWS host, since it has a conflicting fingerprint in ~/.ssh/known_hosts (that of my laptop, presumably) and kicks up a fuss about man-in-the-middle attacks and all. 

Now I really don't want to disable StrictHostKeyChecking, but again I wonder if there might be a just-this-once flag for ssh to tell it to ignore this. Security-wise I don't see that it would add much of a danger since these are always temporary servers and addresses anyway and I'm always looking at a new fingerprint no matter what.

Googled for fixes a bit and found for instance this:

[http://people.uleth.ca/~daniel.odonnell/Blog/using-ssh-to-access-multiple-machines-at-a-single-domain](http://people.uleth.ca/~daniel.odonnell/Blog/using-ssh-to-access-multiple-machines-at-a-single-domain)

In short, the workaround is to script renaming known_hosts before connecting to the conflicting host having it get added as a new key, then merge the new file with the old known_hosts into one. Apparently there's no problem having multiple entries for the same host.

Suppose that would work, though it will spam the known_hosts pretty quickly if I do this a lot so if there's a skip-key-checking option for individual ssh instances I'd think that's still a preferred option.

Or I could just use the full long public DNS for the times I want to connect specifically to the AWS host, but where's the fun in that? :-)


EDIT:

Forgot to say I found and tried another way that should be reasonably convenient too:

[http://www.cyberciti.biz/faq/warning-remote-host-identification-has-changed-error-and-solution/](http://www.cyberciti.biz/faq/warning-remote-host-identification-has-changed-error-and-solution/)

The solution presented there was to use 'ssh-keygen -R serveraddress' to remove any keys for a specific host. Didn't work for me though, as it gave me an error message. Also not sure if that would mean I have to accept the new key for the tunnel through 7777 again.

---

### Post by BkkBonanza on 2010-09-19
Yes, I've run into this and solved it this way...

Create a ~/.ssh/config file for your personal custom config, and add

```
Host *.compute-1.amazonaws.com
StrictHostKeyChecking no
UserKnownHostsFile .ssh/AWSHosts
IdentityFile .ssh/MyKey.pem

```

This says - for these hosts don't prompt for keys and put them in a special file so they don't clog up my "real" host keys. If you add them to the normal file it soon becomes a mish-mash of irrelevant keys. The identity line makes it so you don't have to keep typing it manually for these hosts (use the right filename of course). 

You'll see the host key fingerprint message still but no prompt or wait.

Actually this file is great for specifying non-standard ports for certain hosts too - then you don't have to keep putting -p 7777 to login.

```
Host example.com
Port 7777
```

I've got the "Custom AMI Shrink Tutorial" done. Just testing a bit before posting.

---

### Post by BkkBonanza on 2010-09-19
How to customize a public AMI (15GB EBS size) and shrink to a personal AMI (1GB EBS size).

This process lets you customize the root partition to have your own packages, config and init scripts and then move it to a smaller EBS root volume. If you need more space for data you can always have a second EBS partition that you mount during or after boot. Having a small root partition keeps your storage costs to a minimum when not running.

We can do most of this process from the EC2 console but there is two steps where we will need to login by SSH. Let's get started.

1. Log in to your AWS account and go to the Management Console, EC2 tab.

2. For this step we have to use a "normal" priced instance because the spot instances don't support "stopping" an instance. Stopping is not the same as "terminating". A stopped instance can be resumed where it left off much like a suspend in desktop systems. So first thing we do is click "**Instances**" and then "**Launch Instance**". Select suitable options for the AMI that you want to use as your "base system".

3. Note down it's "**Availability Zone**". Login into your instance with SSH and customize the system as you need. Install packages, configure to your needs and test. 

4. If you used a t1.micro instance - they do not support mounting S3 partitions so you must check /etc/fstab and remove any "extra" mounts (there should only be "/"). If you don't do this then you won't be able to reboot or stop-start the instance.

5. Once you have things the way you like head back to the EC2 console and select your instance and click "**Instance Actions**", "**Stop Instance**". Unlike "Terminate" this will shutdown the instance without losing it's current state. Wait for the instance status to show "stopped".

6. Now we create a second instance to use as a copier. Click "**Launch Instance**" and select options for a t1.micro AMI that we can use to copy files. Make sure it is in the same "**Availability Zone**" as your stopped instance. Wait for the status to show "running".

7. Click the "**Volumes**" menu item, far left. You will see the volume that is attached to your stopped instance. Click "**Detach Volume**" to remove it from your instance.

8. Next we create the small target volume we will migrate onto. Click "**Create Volume**" and select the size you want (1GB is smallest possible). Make sure the "Availability Zone" is the exact same as your stopped instance. "No Snapshot" should be default. Click Create.

9. Both volumes should now be in the list and in an "available" state. Make note of what volume IDs they have for later.

10. Click the volume from your "stopped" instance and click "**Attach Volume**". Choose your running instance (not the stopped one) and enter a device name: **/dev/sdg** - click "**Attach**".

11. Do the same with your new small target volume. Attach it to your running instance and enter device name: **/dev/sdh**. Click "**Attach**".

12. Now both your source and target volumes are attached to your "copy machine". Now login to this machine with SSH.

13. In the terminal run the following commands to copy over the system,

**sudo mkdir /old /new**
**sudo mount /dev/sdg /old**
(make sure you get the right one - check the contents)

**sudo ls -ls /old**
(should have the root from your stopped machine)
(good? now continue)

[B]sudo mkfs.ext3 -F /dev/sdh
sudo mount /dev/sdh /new[/B]
(this formats the volume with ext3 filesystem and mounts it)

**sudo rsync -avx /old/* /new/**
(this will copy all the files over)
(do a visual check that things look as they should in /mnt/new)

[B]sudo umount /new
sudo umount /old[/B]
(unmount the partitions again and we're done)

14. Return to the EC2 console, "**Volumes**" screen. Select and "**Detach Volume**" each of the two volumes you just attached to the running machine. Verify which ones with the IDs you wrote down before.

15. Now select the small new volume and click "**Attach Volume**". Select the "stopped" machine and enter device name: **/dev/sda1** - click "**Attach**".

16. Super! Now we have the new volume attached to our stopped machine containing the same root files as we had originally on our big volume. Go to "**Instances**", select the stopped instance and click "**Instance Actions**", "**Start**".

17. If everything has gone right then you can now login with SSH to your original "custom" machine and make sure it's working correctly (it will have a different IP now, use ec2din to find it). Test it.

18. Finally, we want to snapshot this machine to create your custom AMI. Select the instance and click "**Instance Actions**", "**Create Image (EBS AMI)**". Enter a "name" for your new AMI. Click "**Create**". This starts a pending request to snapshot the running machine - it will take a while...

19. Click on the "**AMIs**" menu item, far left. You should see your pending AMI creation task there (this seems to take forever). After it's done the status will indicate "**available**". I've had this step fail on me once, and I went back and copied again and it worked

That's it!

Once your new AMI is ready you can start new instances (spot or normal) by choosing it as your AMI. It will show up in the "**My AMIs**" tab when launching an instance. If you need to customize it more then you simply make the changes and snapshot it again into a new AMI using the same "**Create Image (EBS AMI)**" action. You won't need to go through this whole detach/copy/attach process again. The Custom AMI that I created here uses 622MB on a 1GB EBS volume, and it works.

Normal instances can be "stopped", and you don't get charged run fees while stopped. This is like having a machine you turn on and off, which remembers it's state. "Terminating" is like reverting the system to it's original AMI state.

Spot instances can't be "stopped" - one of their drawbacks, every time they start "fresh" as the original AMI state.

BTW, You should probably delete left over "volumes" after all this to save on storage fees. You only need the snapshot and your new AMI to launch new instances now.

Have fun!

---

### Post by anlag on 2010-09-20
> **BkkBonanza said:**
> Yes, I've run into this and solved it this way...

Create a ~/.ssh/config file for your personal custom config, and add

```
Host *.compute-1.amazonaws.com
StrictHostKeyChecking no
UserKnownHostsFile .ssh/AWSHosts
IdentityFile .ssh/MyKey.pem

```

This says - for these hosts don't prompt for keys and put them in a special file so they don't clog up my "real" host keys. If you add them to the normal file it soon becomes a mish-mash of irrelevant keys. The identity line makes it so you don't have to keep typing it manually for these hosts (use the right filename of course). 

You'll see the host key fingerprint message still but no prompt or wait.

Actually this file is great for specifying non-standard ports for certain hosts too - then you don't have to keep putting -p 7777 to login.

```
Host example.com
Port 7777
```

I've got the "Custom AMI Shrink Tutorial" done. Just testing a bit before posting.

Great, the address mask for me has to be *.compute.amazonaws.com or some such though. Not compute-1... but the method seems solid. That speeds things up.

I'll try and get on the AMI making tonight, looks good.

---

### Post by BkkBonanza on 2010-09-20
You may want to check this out for a better way to init the instance when launched,

[https://help.ubuntu.com/community/CloudInit](https://help.ubuntu.com/community/CloudInit)

I just came across it because it currently causes micro instances to fail on second start/reboot due to auto adding an s3 volume in /etc/fstab. There is a fix for this problem described here, (near page bottom)

[http://stackoverflow.com/questions/3679156/ec2-small-to-micro-instance-downgrade-problems](http://stackoverflow.com/questions/3679156/ec2-small-to-micro-instance-downgrade-problems)

---

