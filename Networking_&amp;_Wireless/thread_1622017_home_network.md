---
title: "home network"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by mackedo on 2010-11-15
Hey all,
I'm having issues setting up file sharing between two Linux machines.  I've tried the forum cookie cutter answer of "right click folder, sharing options, share, allow others to write and edit, allow guest accounts", but I simply cannot get my two Ubuntu 10.10 machines to see each others shared files.  I HAVE been able to download and use the program "Personal File Sharing", and with it I CAN share the "Shared" folder between both machines.  I'd prefer to learn the correct way to link these two boxes up though, and be able to share more than 1 directory.  Am I missing any programs to complete this link?  Do I need to use Samba?  I've tinkered with it, and I can get both computers to see a workgroup name I set up, but cannot get them to view each other in it.

Any help would be really apprecated :)

---

### Post by mackedo on 2010-11-15
Anyone? :D

---

### Post by grahammechanical on 2010-11-15
I have no idea what to suggest. This is outside my experience. But might I suggest that you remember that the desktop is just another folder according to the Nautilus. It is possible to right click it and give some Sharing Options.

I do not know how these things work. The Places menu shows items for other partitions on the hard disc. Does the other computer show up in the Places side panel? I am just curious. I might want to do something like this myself one day. I am wondering how I would go about it. There is even an icon for Network. It assumes a Windows network but I notice that you can change the label.

Regards.

---

### Post by mackedo on 2010-11-15
> **grahammechanical said:**
> I have no idea what to suggest. This is outside my experience. But might I suggest that you remember that the desktop is just another folder according to the Nautilus. It is possible to right click it and give some Sharing Options.

I do not know how these things work. The Places menu shows items for other partitions on the hard disc. Does the other computer show up in the Places side panel? I am just curious. I might want to do something like this myself one day. I am wondering how I would go about it. There is even an icon for Network. It assumes a Windows network but I notice that you can change the label.

Regards.

Nope, can't see the other computer at all.  From what I read about Personal File Sharing, it sets up a mini-Apache server that broadcasts it's sharing over the network.  Not knowing much about Linux Networks, I have no idea if it leaves any ports open, or if there is any lag in the way it shares the files.  Needless to say: if I could set up a network without needing to set up a miniserver, I'd prefer to do that.

---

### Post by Boondoklife on 2010-11-15
Well I just did it myself on my box and here are the steps:


[LIST=1]
[*]Create a folder
[*]Right click folder
[*]click sharing options
[*]Check share this folder
[*]Check Guest access
[/LIST]
If you wish others to be able to create and delete files then you need to check that box too.

Now if you dont have any of the samba packages installed, it may ask you to install them. Just allow it to and it is good.

One way or another you will be running a mini server, be it ftp, samba, apache, etc. it is just a matter as to what protocal you want. If you are looking for the 'windowsesq' feel then samba is the way to go.

---

### Post by geoffmcc on 2010-11-15
When i had tried out samba I followed this:

[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/")

but now i just use ssh.


Edit: oops, that link was for ubuntu to windows, looking for other.

Edit: [http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/]("http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/")

---

### Post by windowsh8r on 2010-11-15
Have you checked to see that you can ping each computer?  The problem might be a network issue instead of a filesharing issue.  Open a terminal window and type ifconfig.  this will give you the IP address, and then from the other computer type in ping xxx.xxx.xxx.xxx (replacing the x's with the IP address).  If you get returns, then your connections are set up.  If not, then you need to look into your network settings.

---

### Post by jamesjony2 on 2010-11-15
Most families do not either need or could not afford more than one computer.The simplest way - a home network or home area network (HAN) is a residential local area network.Once, home network, mainly the realm of technophiles Two computers are used fine home network. You share files, a printer or other peripheral equipment, and even an Internet connection can use this type of network.

---

### Post by drdos2006 on 2010-11-15
Check out this thread.....
Server software on one machine, client software on the other. 
> 
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 

Addendum:	On the Server machine
Needed to add Group of users on the machine designated as the server. Added the group via Webmin. If Webmin not an option then use terminal on the Server machine: 
sudo addgroup MyGroupName	
Added sharedfiles on server with :	
sudo mkdir  /media/sdb1/sdb1-shared
Needed to change group permissions for /media/sdb1/sdb1-shared:	
sudo chgrp -R  MyGroupName  /media/sdb1/sdb1-shared
//**
On the Client machine: 
Created a directory of sharedfiles with : sudo mkdir /media/sharedfiles
mounted /media/sharedfiles from terminal with : 
sudo mount  <serverIPaddress>:/media/sdb1/sdb1-shared      /media/sharedfiles 
Can also be added to /etc/fstab for automatic mounting.
Copied files as test and it worked.

---

### Post by FDannels on 2010-12-14
I may be new to Linux, but it seems that this is a common functionality that the makers of Ubuntu should have already addressed (i.e. sharing files between multiple Linux machines). Can we get a reply from the authors?

---

### Post by Boondoklife on 2010-12-14
> **FDannels said:**
> I may be new to Linux, but it seems that this is a common functionality that the makers of Ubuntu should have already addressed (i.e. sharing files between multiple Linux machines). Can we get a reply from the authors?

Are you kidding me, there are quite a few ways to share files. You can use FTP, SMB, NFS, SCP, just to name a few. The easiest to get working in my opinion is smb and the steps I used to make a working share are a couple of posts back.

---

### Post by mackedo on 2010-12-14
I did eventually get the networking to work.  When I dug deeper, I found out that I first needed to let my machine recognize and allow the other IP addresses in my network.  So I wound up having to set my router to static IP addresses by NIC, and then I found a piece of software in the database called simply "Network" which allowed me to use the GUI to add the IP addresses.  Once I did that, setting up file sharing with samba and NFS worked perfectly.  Not sure if it's just something unique to me, because all the threads I found simply said "Install Samba, enter workgroup name, ???, Profit", but I never saw anything about having to allow the other network IP addresses as well.  In any event, that is how I got it fixed.  Now if I can get Wine to work at ALL, I can dump my XP partition.

---

### Post by Boondoklife on 2010-12-14
> **mackedo said:**
> I did eventually get the networking to work.  When I dug deeper, I found out that I first needed to let my machine recognize and allow the other IP addresses in my network.  So I wound up having to set my router to static IP addresses by NIC, and then I found a piece of software in the database called simply "Network" which allowed me to use the GUI to add the IP addresses.  Once I did that, setting up file sharing with samba and NFS worked perfectly.  Not sure if it's just something unique to me, because all the threads I found simply said "Install Samba, enter workgroup name, ???, Profit", but I never saw anything about having to allow the other network IP addresses as well.  In any event, that is how I got it fixed.  Now if I can get Wine to work at ALL, I can dump my XP partition.

I am not sure what you mean by allow other network IPs? If you have a firewall running on the ubuntu box and you are trying to browse or share then, yes you would need to add rules to allow this (Note: rules for browsing and sharing are different). As for the workgroup name, this really is not needed in most cases as you will just see two workgroups when you browse the network (using Places -> Network).

There are settings on routers that can foul up the netBIOS part of this equation so if you are looking to just have plug and play functionality you may want to look around your routers config and see if it has any netBIOS or Broadcast filters/blockers.

How are you getting to your shares now? Are you simply typing 'smb://x.x.x.x/share' in the location box?

---

### Post by mackedo on 2010-12-14
No typing involved, actually.  I know that coming from windows, my view on networking is skewed, so my terminalogy might be incorrect.  The way that I share files currently (I switched all machines in my house to Ubuntu, with my computer dual booting XP for the "windows only" jobs), and after adding the IP addresses as I stated earlier, I right click the file, share, read/write permissions, then I go into the network browser, mount the share in question, and do what I need to do.  When I used Mandriva for the week I tried it, I used Samba sharing, but needed to add the IP exceptions as well.  It may very well have to do with my router.  I use wireless NICs, and my router has always been very fussy.

---

### Post by Boondoklife on 2010-12-14
Hmm interesting, did you add them to the hosts section?

---

### Post by mackedo on 2010-12-14
In the networks addon, I believe the area that I added the IP addresses to was called Hosts, yes.  I'm not in front of my machine at the moment otherwise I could give screeshots.

---

### Post by Boondoklife on 2010-12-14
K if you added it to hosts, then it may just be that netBIOS was being killed or filtered out. With the IP in hosts it would basicly not need the netBIOS service as you already know the IP. Check and see if you have a process name nmbd running, that should be providing the netBIOS functionality.

Do you know if your router is able to run DD-WRT or Tomato firmware? If so you could try that as it may resolve your problem.

---

### Post by mackedo on 2010-12-14
I'm unsure if it could, but it would be a moot point anyway: the router (netgear), can't even connect to it's own server to update it's firmware, let alone anything else that might upgrade it's functionality.  I hate this router, I really do, but a new N router is out of my budget currently, and G wireless has left me with a bad taste in my mouth, historically.  Frankly, I'd rather be wired again, and be done with all the headaches of wireless, but that's another story

---

### Post by Boondoklife on 2010-12-14
Out of curiosity, when you get a chance could you post what model is it? Include any revision numbers etc.

---

### Post by mackedo on 2010-12-14
Absolutely.  Did you want the USB NICs models too?

---

### Post by mackedo on 2010-12-14
[http://www.amazon.com/NETGEAR-WNR854T-RangeMax-Wireless-N-Gigabit/dp/B000FGI970/ref=sr_1_36?s=pc&ie=UTF8&qid=1292352167&sr=1-36](http://www.amazon.com/NETGEAR-WNR854T-RangeMax-Wireless-N-Gigabit/dp/B000FGI970/ref=sr_1_36?s=pc&ie=UTF8&qid=1292352167&sr=1-36)
Router.  The Customer reviews pretty much sum up this emmy award winner.
 
[http://www.amazon.com/NETGEAR-WN111-Wireless-N-300-Adapter/dp/B000W8UIZW/ref=pd_bxgy_e_img_b](http://www.amazon.com/NETGEAR-WN111-Wireless-N-300-Adapter/dp/B000W8UIZW/ref=pd_bxgy_e_img_b)
NICs.  I have to say they work fairly well actually.  They were GROSSLY overpriced when I got them new at Walmart, but they are solid little beasties

---

### Post by Boondoklife on 2010-12-14
sure, never can have too much info!

---

### Post by mackedo on 2010-12-14
See above :p

---

### Post by Boondoklife on 2010-12-14
i did a couple of looks and other people have reported the same thing with that router, Did it work ok when you were using windows on the pc's?

Can you post the output of:
```
sudo iptables -L
```

---

### Post by mackedo on 2010-12-14
Can't give you a listing of the command right this second, not at my machine, I'm at work (don't tell kkthx).  
The router worked in Windows, but same issues: drops all the time, needs to be cycled at the drop of a hat, doesn't hold changes occasionally (had to remind it of the IP addresses over a dozen times now), has MAJOR issues finding other machines in the network (sometimes took as long as 5 minutes to recognize anyone else).  I've looked into [http://www.amazon.com/Cisco-Linksys-WRT54GL-Wireless-G-Broadband-Compatible/dp/B000BTL0OA/ref=cm_cr_pr_product_top](http://www.amazon.com/Cisco-Linksys-WRT54GL-Wireless-G-Broadband-Compatible/dp/B000BTL0OA/ref=cm_cr_pr_product_top) however I live in an apartment complex with a lot of wireless traffic around us, and I worry about our signal being polluted.  N, even in this "lovely" router works reasonably well, not sure about G.  In any event: That rotuer has put me off to netgear for the foreseeable future.  If I was in a house that had less Wifi traffic around us, I'd be on the router above right now.  From what I understand, you can hack the firmware in it very easily too.

---

### Post by Boondoklife on 2010-12-14
Well I can tell you that I have setup DD-WRT flashed routers in apartments before and not had a major issue about signal pollution. Your best bet would be to look into getting a router that you can use DD-WRT or Tomato on and just tune your signal to fit between most of the people around you.

Direct rip from my posting in another forum:
> well actually I would not say only use 1, 6 or 11. If you do a site  survey with (insert your favorite app here) and see that there are  people in those ranges then why not use something in between. Me  personally I have people around me all over the spectrum but especially  in 11, 8, 6 and 1; with this in mind I use channel 3 and get great  signal with it.

Each person should tailor their choice to their  area. You are correct that they will overlap but if you have a situation  like mine where 3 is between 6 and 1, then you can use it. As long as  everyone is not online at the same time you should at least get a clean  signal in the 123 or 345 range. Then again if everyone is online at the  same time then in my case it is pretty crazy anyways.

I personally don't have an issue with G as it does what I want, It is not the fastest transfer speed compared to N, but I have not had any issues with it. As for network intensive appliances, I hard wire them into the router if possible.

---

### Post by mackedo on 2010-12-14
I'll have to look into it seriously then.  I bet the difference will be night and day between what I'm using now :D

---

### Post by mackedo on 2010-12-14
In response to your earlier request:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

