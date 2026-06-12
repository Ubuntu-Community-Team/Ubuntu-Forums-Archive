---
title: "Can't See Windows Computers..."
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by chessnerd on 2009-05-25
Alright, after loading on Ubuntu, I had 5 days were everything was going great on my network. Ubuntu was able to see all of the Windows computers and I was able to access and use the shared folder on the main Windows comp, but then there was a hiccup in the home network and, after fixing it so the Windows computers would work again, Ubuntu can't see any of the Windows computers, wireless or wired, on the network. The Windows computers, however, can still see the Linux one. I've read dozens of forum posts and how-tos involving the opposite problem (where Windows can't see Linux) but I haven't come across a post where this problem arose and a solution was found.

I have Samba installed, and I also installed pyNeighborhood in the hopes that that might do something, but the Windows computers remain invisible. The default Ubuntu settings allowed it to see the Windows computers. So is there a way I could revert the network to the default settings? Or are there any other ideas about how I could get Ubuntu working again?

---

### Post by Mosaab on 2009-05-25
I had this problem 2 days ago..

try to ping  any computer from your linux box .. if it doesnt work .. or it pings something else in the internet. 

do the following:

```
sudo gedit /etc/nsswitch.conf
```

look for a line starts with hosts:. if the line doesnt contain the word "wins" change the line to:

```
hosts: files dns wins
```

try to ping a computer with its name.
hope it works.

---

### Post by dmizer on 2009-05-25
Here's a more in depth look at the problem, with solutions: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

> **Mosaab said:**
> ```
hosts: files dns wins
```
This should be:
```
hosts: files wins dns
```
Order is important. For people using DNS services with typo correction, the typo correction search page counts as a resolve so WINS is never queried unless you put it in front of DNS.

---

### Post by Mosaab on 2009-05-25
> **dmizer said:**
> Order is important. For people using DNS services with typo correction, the typo correction search page counts as a resolve so WINS is never queried unless you put it in front of DNS.

What you say is logical, but in my machine I have wins the last one. and it works fine.
maybe it will look in the host file first and the it will look in dns IF you have a dns server with the same subnet mask and then wins .. I am not sure . I am not experienced with this I just solved my problem today.

---

### Post by dmizer on 2009-05-25
> **Mosaab said:**
> What you say is logical, but in my machine I have wins the last one. and it works fine.
maybe it will look in the host file first and the it will look in dns IF you have a dns server with the same subnet mask and then wins .. I am not sure . I am not experienced with this I just solved my problem today.

Because your ISP is not using typo correction in their DNS yet. Resolving WINS after DNS may also cause some wait time while DNS times out before attempting to resolve WINS.

More information on typo-correction in DNS servers here: [http://ubuntuforums.org/showpost.php?p=7255859&postcount=15](http://ubuntuforums.org/showpost.php?p=7255859&postcount=15)

I'm not saying that it doesn't work for you, and that putting it at the end won't work for others. But if you're going to start providing this solution to other people, it's important to give the correct order because typo-correction is a problem quite frequently.

---

### Post by Mosaab on 2009-05-25
yes.

I guess I better edit my file too.

thanks

---

### Post by chessnerd on 2009-05-25
Alright, I got back home (I was over at my aunt's for Memorial Day when I posted originally) and I tried out the solution (with both orders) but I still can't see any Windows computers. If it helps, the nsswitch.conf file now reads like this:
> passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
Is there anything else I should change?

Next, I'm afraid that I don't exactly know how to ping computers. I read some of the man page about the ping command and I tried it like this:
```
ping *computerName*
```
Is that right or should it be something else?

Also, while I can see the Linux computer from the Windows computers, I can't access my Linux computer from them. When I try to connect it gives me an error which reads: "Windows sent the request to the DNS server and the server responded that the name was unknown." Could this also help to explain the fact that I can't see the Windows computers and/or might it be I have to do something on the Windows end to get this to work?

---

### Post by dmizer on 2009-05-25
> **chessnerd said:**
> When I try to connect it gives me an error which reads: "Windows sent the request to the DNS server and the server responded that the name was unknown." Could this also help to explain the fact that I can't see the Windows computers and/or might it be I have to do something on the Windows end to get this to work?

Yes, as discussed above, /etc/nsswitch.conf should look like this:
```
passwd: compat
group: compat
shadow: compat

hosts: files [COLOR="Red"]wins[/COLOR] dns
networks: files

protocols: db files
services: db files
ethers: db files
rpc: db files

netgroup: nis 
```
With wins in front of dns. After making this edit, you will need to reboot, or restart networking.

If you are STILL unable to browse to your Windows computers, please see this howto: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by chessnerd on 2009-05-25
As I mentioned, I tried BOTH setups (with wins before and after dns) and wins after was the second setup I tried, so it was still there. I tried this process again with both but I still couldn't see the Windows computers. So, I looked at [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149) and I discovered something interesting when checking to see if the Ubuntu workgroup was still WORKGROUP. 

smb.conf is empty. 

Might that be the problem?

Is there a way to restore smb.conf to it's original state?

---

### Post by dmizer on 2009-05-25
That happened because I made a mistake in the howto :(

You should be editing /etc/samba/smb.conf (the howto originally said /etc/smb/smb.conf)

Also, before you edit smb.conf make sure that winbind is installed.
```
sudo aptitude install winbind
```

---

### Post by chessnerd on 2009-05-25
Okay, I found the actual smb.conf file and it is fine, but when I tried to install winblind it came back with an error that read: "Can't find any package whose name or description matched "winblind"" and nothing was installed.

Opps, typo on my end now... but "winbind" didn't work either...

---

### Post by dmizer on 2009-05-25
Not winblind, winbind ;)

---

### Post by dmizer on 2009-05-25
> **chessnerd said:**
> but "winbind" didn't work either...

You got an error? What do you mean by "didn't work"?

---

### Post by chessnerd on 2009-05-25
I checked Synaptic because no error came up, it just didn't install anything, and winbind was already installed.

---

### Post by dmizer on 2009-05-25
Okay, then can you ping your other computer by name now?

```
ping windows-computer
```

Replace "windows-computer" with your Windows computer's actual name

---

### Post by chessnerd on 2009-05-25
I'm afraid I can't ping any of the computers on my network. I'm gonna try a reboot again to see if the changes will take after that.

---

### Post by chessnerd on 2009-05-25
No dice on the reboot. Still can't see or ping any computers. I tried both of them, but to clarify, do you type in the computer's "full name" or the "computer description"? I'm figuring it's the full name, but I just want to be sure.

---

### Post by chessnerd on 2009-05-25
Well, I have to call it quits for the night.

I did the solution for all four of the problems (I thought for sure I would get it with that last one because the network problems occured around the time I ran Firestarter, but the problem happened to all of the computers at once, not just the Linux one, so I don't think that Firestarter was the culprit.)

I'll take a look at the CIFS tutorial and the "best Samba server howto" in your sig tomorrow night to see if they can help me and I'm thinking I'll go to the library to pick up a copy of "Networking for Dummies" to see if that has any useful info. (I've come to respect those guides since "Linux for Dummies" helped me learn basic Linux skills like the file system and CLI back in March.)

I may not have won this battle, but I will win the war! ;)

---

### Post by dmizer on 2009-05-25
Your problem is still very likely related to Firestarter. The directions in my howto do not give any instructions for configuring Firestarter. Also, just closing the Firestarter GUI applet doesn't actually stop Firestarter. You have to either manually select the stop firewall command, or completely uninstall Firestarter.

I highly suggest removing Firestarter and using the UFW instead. There is a nice GUI frontend for it: [http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html](http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html)
or, if you're using Jaunty, it's installed by default.

---

