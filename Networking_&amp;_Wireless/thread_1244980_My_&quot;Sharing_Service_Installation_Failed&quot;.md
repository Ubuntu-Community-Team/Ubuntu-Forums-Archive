---
title: "My &quot;Sharing Service Installation Failed&quot; and also &quot;Package Samba Is Not Available&quot;"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by forbidenpasionfruit on 2009-08-20
Hello everyone!

I am an absolute brand spanker of a newbie here, having taken the "easy" path of Windows all my life, and only installed Ubuntu 9.04 about 4 hours ago. So, I have no knowledge whatsoever of the ins and outs of Ubuntu, or the terminology, etc. But I will give as much detail about my problems, and how I got there, as I can.

First I should say that I have spent the last 3 hours and 50 minutes searching all the forums for an answer and haven't found one that works yet. However please feel free to post links to other threads that may answer my Q's instead of re-typing things!!!

So I bought a brand new desktop (AMD Dual Core 2.6, etc) with no operating system. I got Ubuntu 9.04 and installed it straight onto the computer (called Server) without doing anything else, and didn't change any of the settings during install (except country and time zone etc). There are also no other programs installed or peripherals plugged into the computer.

Then I simply plugged in the LAN cable (which is plugged into an Open brand wireless router/modem/VOIP box), and instantly had access to the internet and the below network things, without touching any settings at all. 

I then tried to navigate my way around a bit, mainly looking for the networking stuff, as this is to be a file server for our office. We currently have two other computers (one desktop, one laptop) both running Vista32 (desktop Ultimate wired, laptop Business wireless) that need to access the files, and be able to run back ups to Server, so I need to be able to open/edit/save/create files and folders, across and from all computers on the network.

So I found Places/Network, and there is a "Windows Network" there, that goes through "MSHOME" and shows both the Vista computers. I am able to access some of the desktop computer's folders and files, but cannot change or create anything. But I receive an "unable to mount location" error when trying to acess the laptop (only just noticed this while posting, so it isn't the reason for this post).

Then I tried to go the other way, and share a folder on Server. I created a folder in "Documents", and right clicked to "Sharing Options". As I read in the other posts, it says "Sharing service is not installed". So I click "Install service". It then says "Sharing service installation failed". 

I then tried the suggestion of $ shares-admin, bringing up the window that says "Sharing services are not installed". I make sure both boxes are ticked, then click "Install service". I type in my password, and it just takes me back to the "Sharing services are not installed" message.

So I tried another suggestion to $ sudo apt-get install samba. I get the following message after doing this:
*Package samba is not available, but is referred to by another package. This may mean that the package is missing, has be obsoleted, or is only available from another source. However the following packages replace it: smbclient samba-common.*

This is where the main problem starts. All the posts I have read so far seem to stop their solution at the above two steps, and don't offer any troubleshooting for if those steps don't work. But I also haven't seen any reply posts that say those solutions don't work!!

So, there it is folks. If anyone can offer any solutions as to how to get past the above errors, or any alternate solutions to getting sharing working (that are easy to understand for a noob!) then I would be very grateful.

Thank you very much for reading!
forbidenpasionfruit

---

### Post by dmizer on 2009-08-20
Make sure you get all of your updates before going much further.

System > administration > update manager

---

### Post by forbidenpasionfruit on 2009-08-20
Hi dmizer,

Thanks for your reply - my post was getting a bit lonely while the others posted today had a lot of replies!

That was something I forgot to mention, but did already do (read in another post) and it needed no updates. And I've just checked it again, and it still says its up to date.

Thanks,
forbidenpasionfruit

---

### Post by dmizer on 2009-08-20
Don't worry, we all know that these message boards are very busy, so many of us go back several days looking for posts without answers.

Please post the output of this command:
```
sudo apt-get update&& sudo apt-get install samba
```

---

### Post by forbidenpasionfruit on 2009-08-20
Oh no, don't worry, I'm certainly not complaining! I don't think I'll ever be able to be any help to anyone on these forums in return so I'm very grateful!

And excuse me but holy *$&%! That first command brought in 31 updates (193 files)!!! Not that I would have ever thought to check the forums to troubleshoot the regular way to check for updates that had no obvious error messages, so thanks.

So, I'll finish downloading and installing this mammoth lot of updates, restart, etc, then try the usual way to share files again and post how I go.

Thanks mate,
pasion
BTW - how do you put that "code" box in the post?

---

### Post by dmizer on 2009-08-20
> **forbidenpasionfruit said:**
> BTW - how do you put that "code" box in the post?

Use [noparse]```
[/noparse] to start, and 
``` to stop like so:
[COLOR="Red"][noparse]```
[/noparse][/COLOR]terminal input[COLOR="Red"]
```[/COLOR]

---

### Post by forbidenpasionfruit on 2009-08-20
Ok, I'm back and joy of joys the right click "Sharing Options" now works! 

I still have the issue of not being able to create anything on the desktop, and the  "unable to mount location" error when trying to access the laptop, as well as neither of them being able to see Server.

However, I've seen a few things in my forum trawling about Ubuntu liking workgroup instead of mshome, etc so I'm happy to re-search the forums for solutions to these "new" problems and test them out before taking up more of your time. 

Will it be ok to post any further questions about this process (in case of failure again!), and/or my success in this thread? Or would I be better off starting a new thread about the specific problem I am having?

And thanks for the [code] code! Awesome!

Thanks again,
pasion

---

### Post by dmizer on 2009-08-20
> **forbidenpasionfruit said:**
> I still have the issue of not being able to create anything on the desktop, and the  "unable to mount location" error when trying to access the laptop, as well as neither of them being able to see Server.

See the 6th link in my sig. :)

---

### Post by forbidenpasionfruit on 2009-08-20
Ok will do (incidentally I did check it out before I posted, but I couldn't make it work at the time!). I've just changed our Windows computers to workgroup and all computers can see each other (another victory!), but still no permissions to create or edit. 

So fingers crossed the success will continue!

---

### Post by forbidenpasionfruit on 2009-11-01
Hello again, I'm back on this similar line of trouble now, after an updated install of 9.10. 

I have been through all the instructions in dmizers sig 6 link ([http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)) now and arrived at this part:

```

sudo ufw allow proto udp to any port 137 from 192.168.1.0/255

```It says - ERROR: Bad source address.

Now I didn't know if that meant the 255 part, but since our network's IPV4 Default Gateway is .254, I tried 255 first, then 254 and got the same error anyway.

In addition, I was also having an issue installing the gufw, but for some reason the install process now works after following the same instructions ([http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149))  and installing winbind!! (I'm only posting this as it may help someone else out!)

Now that gufw is installed and running, I have looked on the forums for how to actually create rules (as in, click this, type this, save, restart, etc) but I haven't found anything yet - mostly they just say "...use gufw to add your rules." (sorry, complete windows noob here).

So, I tried setting it to "Allow" by default to see what would happen. The result was that I can now see the Karmic computer and files from my Vista computers, but can only see itself from the Karmic computer.

I also then re-tried the above ufw allow code but received the same error as mentioned above.

So I guess I still need some assistance with this, as my main goal is to have the networking working peacefully between Karmic and Vista x 2 as Karmic was bought for our file "server" and back up computer!!

Thanks again!

---

### Post by forbidenpasionfruit on 2009-11-03
I have also now started to work out some of the rules to add (such as the udp), but when I look at the logs it seems to show a rule for connecting TO one IP address FROM the other, instead of it being a range. 

In any case, that obviously didn't work!

Again, any further suggestions would be great!

Cheers.

---

### Post by forbidenpasionfruit on 2009-11-14
Hi guys,

Just wondering if anyone's had any luck with an answer to this prob?

Cheers.

---

### Post by dmizer on 2009-11-15
What's the output of:
```
sudo iptables -L
```

---

### Post by forbidenpasionfruit on 2009-11-30
Hi again,

Sorry for the delay - I moved on to other projects in the meantime!

Here is the result of your request:

```

server@server-desktop:~$ sudo iptables -L
[sudo] password for server: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         

```

I've read a few forum posts on how to change these things, but I'm just so new to this that I don't want to stuff everything up more!

Thanks for your continued help.

Cheers.

---

### Post by dmizer on 2009-11-30
Is there some specific reason why you need a local software firewall?

In most cases, when your computer is in a network where file sharing takes place, there is already an active firewall, and a local software firewall is both unnecessary duplication and likely to cause this kind of interference.

Try completely disabling the firewall and see if your situation improves. If it does, I highly suggest you evaluate your network to see if there is a real need for a local software firewall.

---

### Post by forbidenpasionfruit on 2009-11-30
Well we have two Windows computers on the local and internet network, so the firewall/anti-virus is, unfortunately, needed on them. But from what I've read I know I don't need an additional one on on Linux. I was under the impression that the things I've been doing were to the protection that is written in to the Linux code, hence my not wanting to fiddle with it too much!

And I have now just shut the software down on the Windows computers completely but it didnt change the problem - the Ubuntu computer still says "Unable to mount location" when trying to access the network.

:(

---

### Post by forbidenpasionfruit on 2010-01-15
Hi,

Just checking to see if there's any new info on this problem?

Cheers.

---

### Post by dmizer on 2010-01-15
Sorry, this one fell through the cracks.

You should completely disable and/or remove the firewall in place on the Ubuntu computer. It's GUFW, and can be found in the Administration menu.

---

### Post by forbidenpasionfruit on 2010-02-01
Thanks for getting back to me, and no worries about the reply. We've just had to reformat both out Vista comps due to serious hacking on our off site web server :( so just trying to catch up with everything now. 

Well, it is currently set to allow all, and sometimes we can access the Ubuntu comp and sometimes not. We also can't cut our files from it, and other random issues like that.

There seems to be nothing we can do about those issues as they occur between the Vista computers as well. We have never been able to get a network between computers that just *works*!!

Since the Ubuntu comp will have ALL our files on it, and will be getting automatice back ups from our computers as well, I guess I still want to know if disabling/removing the firewall will leave the computer completely vulnerable (I would assume so), because if so, we'll probably have to jump back on the Microsux band wagon for now :(. 

Cheers.

---

### Post by dmizer on 2010-02-01
> **forbidenpasionfruit said:**
> Thanks for getting back to me, and no worries about the reply. We've just had to reformat both out Vista comps due to serious hacking on our off site web server :( so just trying to catch up with everything now. 

Well, it is currently set to allow all, and sometimes we can access the Ubuntu comp and sometimes not. We also can't cut our files from it, and other random issues like that.

There seems to be nothing we can do about those issues as they occur between the Vista computers as well. We have never been able to get a network between computers that just *works*!!

Since the Ubuntu comp will have ALL our files on it, and will be getting automatice back ups from our computers as well, I guess I still want to know if disabling/removing the firewall will leave the computer completely vulnerable (I would assume so), because if so, we'll probably have to jump back on the Microsux band wagon for now :(. 

Cheers.

This post: [http://ubuntuforums.org/showpost.php?p=8416933&postcount=14](http://ubuntuforums.org/showpost.php?p=8416933&postcount=14) tells me that your firewall is indeed NOT configured to allow all and is most likely the cause of all of your problems. I highly suggest disabling it unless you have a very very good reason to use it.

Things to think about:
1) If you're sharing files over samba, that probably means you're on a LAN with only indirect (usually via a firewalled gateway ... AKA "router") access to the Internet. Since a gateway is most often also a firewall, this means that a firewall on your server is most likely redundant.
2) A LAN is generally considered a "trusted" network, which means that all LAN traffic (with the exception of wireless) is considered safe. If you do not consider your LAN traffic to be safe, you should seriously consider how wise it is to use any kind of unsecured (like Samba and NFS) LAN file sharing at all, Linux, Windows or otherwise.
3) The only reason I can see you needing a local software firewall is if you're using a laptop which is going to be regularly used on unsecured networks or have unfettered access to the WAN as with a Mobile broadband or dial up internet connection. In those cases, you shouldn't have holes poked in your firewall for SAMBA access anyway.

If you're running on a firewalled LAN, odds are you do not need a firewall for any of your LAN computers, Linux, Windows, or Mac. Plus, since you indicated you've already been hacked (I assume you were running software firewalls on your Vista machines), you probably can see how futile it is to run a local software firewall anyway.

---

