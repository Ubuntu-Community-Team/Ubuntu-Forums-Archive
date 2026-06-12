---
title: "Samba makes me want to pull my hair out"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by PoopyTheJ on 2009-03-24
I cannot get my windows computer to see, much less connect to my Ubuntu 8.04 computer which is running Samba, I think. I've tried using the right click share this folder option, I've tried going into the Samba documentation to get my network running to no luck. I'm hoping someone here has an easy to follow way of setting up and getting Samba to work on my network. When trying to connect to the Samba drive, I've tried mapping the drive in windows and using the network neighborhood to get file sharing to work all to no avail. Any ideas, or good tutorials on setting up a simple file share for Ubuntu?

---

### Post by andrewwg94 on 2009-03-24
yes it's very annoying. there should atleast be a GUI for samba. it's very weird because i can't connect to another ubuntu computer, but when i log into windows on the same computer, i can see my ubuntu computer just fine.

---

### Post by inobe on 2009-03-24
it really isn't that difficult, i have setup at least 14 networks including my own......

if you can see the windows computer' your off to a great start !

the question is' the steps you used to view ubuntu's shares ?

---

### Post by dixonstalbert on 2009-03-24
There is lots of guides  posted  in ubuntuforums about setting Windows peer to peer network (ie standard home network), unfortunately the 
threads are now hundreds of posts long when you run into problems.

You could end up bald by the time you read them all to see if they apply to your problem.

 Try following the initial post in one of the guides to get you started , then try these diagnotic steps and post back: 



1. Try temporarily disabling all firewalls in Windows (assuming your network connects via a router). Also disable any firewalls if you set them up in Ubuntu

2. set up a share in ubuntu and set up a share in windows. Goto Places > network in ubuntu and see if it can see its own network share and Network Neighbourhood in Windows and see if it can see its own share. Shares can take up to 40 minutes to appear in a home network.

3. open Firefox or other browser in ubuntu and type in ip address/sharename of a shared folder on Windows computer; i.e if you mapped My Documents in Windows and gave it a network name of "windocs"
and if Run>cmd>> ipconfig/all reports Windows computers IP address is 192.168.0.2, you would type in address bar
```
smb://192.168.0.2/windocs
```

browser should return directory on windows computer. (There is a bug with Nautilus with displaying windows shares properly. this will get around the bug if it is effecting your network.

good luck.
I had Samba working fine with my home network, then my Mcafee Antivirus Software in Windows computer had an automatic update a few monthes ago that reconfigured my Windows firewall settings that blocked samba. I spent hours fiddling with my Ubuntu samba settings until I realized what the problem was.

---

### Post by rplantz on 2009-03-25
I've been in this business since declaring "computers" as one of my specialties in electrical engineering at Berkeley in 1960. I spent the last 21 years of my working career as a CS professor. When my students would express frustration, I would point to my bald head and say, "This is not hereditary."

---

### Post by BkkBonanza on 2009-03-25
I'm not sure what you've done so far. Keep in mind that by default Ubuntu has smb client installed and should be able to see shares on other machines. But smb server is not installed by default - you need to install it. I believe I did that by going to desktop menu, System->Administration->Services and enabling the "Folder Sharing Service" (Samba). I don't recall now. But I'll give it a try and then report back here how to get this working.

For viewing other machines you should be able to type an address like,

smb://192.168.0.103/

into Nautilus and get something. If you have DNS or names in your /etc/hosts file then names will work instead of an ip.

---

### Post by BkkBonanza on 2009-03-25
Ok. I just did this. I'll assume from nothing but you may have done these steps.
Install samba by typing,

sudo aptitude install samba
(you can also do this in the gui using Synpatics)

Then go to System->Administration->Services and enable the "Folder Sharing" (samba) service. Otherwise samba isn't running.

Now open a file browser window in Nautilus and choose File System in Places.
Right click on a folder (I chose /torrents in my trial) and select "Sharing Options"

Enable the check marks for "Share this folder" and "Guest Access". Give a share name for your folder.

Now go to the Nautilus address bar and type, 

smb://localhost/your_share_name_here

You should see your folder contents. If not, then we need to get this working before we get will see it on other machines. 

You can also use Nautilus Places->Network and select Windows Network, then HOME, etc until you find your share.

---

### Post by BkkBonanza on 2009-03-25
I also just turned on and tested from my WinXP machine. Choosing Explorer and Network Places the share on my Ubuntu machine showed up there right away.

I wasn't using Samba for sharing from Ubuntu before today so I believe this is all you _"should"_ need to do. No editing of smb.conf for just basic guest access.

Now configuring user permissions and all that is another story but first get the basics working.

---

### Post by inobe on 2009-03-25
here's the official documentation

[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

i suggest scrolling down to accessing files from windows if ubuntu can see windows shares.

---

### Post by robinz77 on 2009-03-25
There should be netbios name service enabled from the ubuntu side in smb.conf( wins is the same in windows) to be able to discover it automatically. Also windows need to know where the wins server is (edit the network interface setting - wins server). And also firewall may block the ports on which samba and netbios listening. Try netstat -t to discover them

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable it's WINS
# Server
;   wins support = yes

try to run \\ip-or-hostname\\shared_folder in windows
sbmclient \\ip-or-hostname\\shared_folder in linux

---

### Post by PoopyTheJ on 2009-03-27
Ok, I apologize we've been a bit crazy here since posting, I've installed samba server and enabled the folder sharing service. I can see get and put files onto my Windows XP machine from Ubuntu, however the Ubuntu machine which is where everything is stored I cannot access. When I put in smb://localhost/shared (on the ubuntu machine) I get a password prompt. My username is in the box however my password doesn't work. Ummm think that's it so far. Tahnks for the replies I oughta actually be around now family emergencies have resolved themselves.

---

### Post by PoopyTheJ on 2009-03-27
robinz77 - netstat-t shows...

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        4      0 poopythej-desktop:48621 192.168.0.1:netbios-ssn ESTABLISHED
tcp        4      0 poopythej-desktop:39837 192.168.0.1:netbios-ssn ESTABLISHED
tcp        4      0 poopythej-desktop:48620 192.168.0.1:netbios-ssn ESTABLISHED
tcp6       0      0 localhost:www           localhost:35949         TIME_WAIT

---

