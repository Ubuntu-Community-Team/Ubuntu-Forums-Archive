---
title: "Accessing shared files/folders on LAN"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by Chew N Tobacca on 2009-10-06
Hello, I have been an avid Linux/Ubuntu user for some time now. Yesterday, I built up an old computer and installed Linux Mint 6 XFCE on it. I have a hard-wired network set up with 2 machines on it, one with Xubuntu 8.10 (and Windows XP) and the other with Linux Mint 6 XFCE. My goal here is to be able to share files freely back and forth between the two machines. 

I understand my lack of knowledge for networking and file sharing. Setting up the folders to be shared was quite easy, on both OS's. However, I do not know how to access them from the opposing machine. (Yes, I feel like a big idiot.) I can boot to Windows XP and pull the files right off the other machine using 'My Network Places' with no trouble at all. But in Xubuntu I have no idea where/how to access the shared data. I have searched threads forum- and web-wide, and I can't seem to find anything that basic. Now I am stumped.   ](*,)

Surely there is something horribly simple I am missing. Would someone be kind enough to clarify this for me? Thanks in advance.

Chew

---

### Post by jessiebrownjr on 2009-10-06
I need to learn this as well.. I found some other thread where they told the guy to use samba or NFS, but mainly NFS... so if anybody has any guides/tutorials, feel free to share :-)

Im using 2x ubuntu 9.04 boxes. I have xp/vista but I don't admit it... :-):lolflag:

---

### Post by pricetech on 2009-10-06
I'm not familiar with the Xubuntu interface so I'm not sure where to tell you look, but in Ubuntu I go to Places - Connect to Server and type in the IP and sharename after which I am prompted for credentials.

I'm too old to remember details of command line usage but look at the smbmount command.

I hope that's some help anyway.

---

### Post by jessiebrownjr on 2009-10-06
[HTML]http://ubuntuforums.org/showthread.php?t=255872&highlight=mounting+shares[/HTML]

Found this, thanks above poster, that was the command that I needed to know :-)

---

### Post by Chew N Tobacca on 2009-10-06
Not to be a party pooper, but I think I am admitting defeat on this matter. I have put entirely too much frustration into something that should have taken 5 minutes. After damn near 12 hours of messing around, I have gotten nowhere. For sanity's sake, I think I am just going to move files the old-fashioned way. This is getting ridiculous... 

I am well aware that I know nearly nothing of networking and so forth, but this should be easy. All I want is a simple 2-way availablity of data, and apparently it is not that simple. Hate to say it, but shouldn't it "just work"?

Here is the problem I run into:
I can access info on on machine or the other one time (sometimes). After that, the workgroup folder is altogether gone and need to reboot both machines to gain access again (if I am lucky). Most times I can access both machines' shared data from one but not the other, or vice-versa. Doesn't make any sense to me. The knowledge that I DO possess regarding the issue kind of tells me that as long as both machines are on and connected to the network, only the other should appear when I try to access it (not both on one machine and nothing on the other), and I should be able to traffic data both ways. Am I mistaken?

---

### Post by jessiebrownjr on 2009-10-07
Tell me what commands you are doing step by step, I don't know how to do this either but maybe I can feed off of you and start. I don't really know what to even do past the smbmount command.

Wonder why nobody else knows how to do this, maybe they installed ubuntu just to play with mozilla :-)

---

### Post by Chew N Tobacca on 2009-10-07
Upon discovering that the computer I slapped together the other day has USB 1.1 ports only, I thought I would give this another crack. (Plus, I am having a much better day today!)

Originally I was trying some GUI stuff. Seemed pretty simple. XFCE apparently goes ahead and creates its own folder called 'Network' for workgroup stuff in the home directory (i.e. /home/chew/Network). This is a big disaster. Not sure if there is any impact here, but my Linux Mint machine does not connect on its own upon startup. No idea why. Anyway, it was hit and miss. When I could access the data on the other machine, I could never retrieve any of it. Gave me a time-out error every time.

So today I have been trying like hell with the smbmount command. Couldn't connect using the template listed in the turorial. I finally made it work by using the IP address, and I now have accomplished my goal. =D> The steps I used (with the secondary machine, "dave") are as follows:

1. Create a folder to use as a mountpoint (I used /home/dave/chew).
2. In a terminal, type in:
```
sudo smbmount //Creeping-Death/Share /home/dave/chew -o ip=192.168.1.101,password=passwd
```
3. Enter root password (for sudo command)
4. Access the shared info off my primary machine "chew".

And that was that. As indicated in the tutorial from the link above, the 'smbmount' command always runs as root, but you can change that using 'chmod'. When it was all said and done, everything works fine. No surprise that I was making it much harder than it really was... 

Also indicated in the tutorial was the fact the mount was not permanent. Nor do I want it to be. So in my case, I just made a panel shortcut to perform the mount for me.

Thank you all for the feedback. Much appreciated!

Chew

---

