---
title: "Lost LAN after upgrade to 9.10"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by rsnow on 2010-02-26
I have 2 machines with ubuntu (now 9.10) and 2 with XP. After upgrading the ubuntu machines to 9.10 my wired LAN does not let me connect between the linux and MS machines. They did before the upgrade. Where and what should I check to see why the ubuntu machines cannot connect to each other or to the XP machines?

I have looked at the network connections and it shows 'auto eth0', last used 'never'. I select the auto eth0 and click on the edit tab and the wired tab shows a MAC address and MTU is set to automatic. The 802.1x Security tab shows it not checked and grayed out. The ipv4 settings tab shows 'automatic'. The ipv6 settings tab shows 'ignore'.

When I click on the Places/Network, the Windows Network icon comes up. When I click on it, I get the MSHOME icon and the WORKGROUP icon. When I click on either of them I get message saying "Opening MSHOME" and then the message 'unable to mount, failed to retrieve share list from server'. The same thing happens when I click the WORKGROUP icon.

---

### Post by jase07 on 2010-02-26
i have the same problem. ive been posting to other forums and no one can rally solve this

---

### Post by soldier_of_light_army on 2010-02-26
>> my wired LAN does not let me connect between the linux and MS machines

now if that meant that you are not able to connect to internet or LAN, it can be fixed in two ways:

1) the network card drivers were installed ok, they just need to be restarted: if this is the case, just follow the steps here:
[http://absolutebeginnerubuntulinux.blogspot.com/2010/02/some-common-tips-for-everyday-use.html]("http://absolutebeginnerubuntulinux.blogspot.com/2010/02/some-common-tips-for-everyday-use.html") 

2) the network card drivers need to re-installed: if the above method failed, then probably this is the case. Then you need to know who was the manufacturer and download the drivers from there.

---

### Post by rsnow on 2010-02-26
My machines connect through a Linksys DSL router with a 4 port switch. All machines are able to connect to internet through this device. I am just having a problem getting all machines to be able to interact with each other.

Now here is a new development: for some reason(?) I am now able to see and connect to one of the ubuntu machines from my MS machines but cannot reach the other ubuntu machine. Neither of the Ubuntus can see or connect to either of the MS machines. Both MS machines can see and connect to each other. The Ubuntu machines cannot see or connect with each other.

Does 9.10 use Samba? I thought I read somewhere that they quit using it. If so, what are they using?

---

### Post by rsnow on 2010-02-26
SOLA

I went to the link you posted and did the command line thing and from I could tell eth0 was working.

---

### Post by soldier_of_light_army on 2010-02-26
rsonw, looks like you don't have Samba installed. Yes, Samba is present in 9.10. 

run this command to check if you have samba:
dpkg -s samba

If it says, you have samba installed (get rid of it and do a re-install)
to uninstall (if you had samba) do this...but skip this step if you dont have it:
sudo apt-get purge samba

then do a samba install:
sudo apt-get install samba

you should now be able to share folders across windows/mac computers.

However, if your Windows/Mac computers are part of a network,  you will need to edit samba config file to add that workgroup name. For example, lets assume the workgroup name is ANDROMEDA.
Now do this:
gksudo gedit /etc/samba/smb.conf 

search for "workgroup =" (without the quotes)

you should see a line like this: workgroup = WORKGROUP

replace WORKGROUP with ANDROMEDA

save and close gedit. Now it should  work.

---

### Post by Iowan on 2010-02-27
> **rsnow said:**
> 
I have looked at the network connections and it shows 'auto eth0', last used 'never'. There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/447067") for this - my Karmic machine has the same issue.
I've had some success using the "Connect to Server" option, but it means you need to know where the connection  is (browsing doesn't seem to work as well...)

---

### Post by rsnow on 2010-02-28
Iowan - I read the bug report and that is exactly what I get when I go to Network Connections and click on wired connection.

SOLA - I followed your instructions. The dpkg -s showed Samba was installed. I uninstalled and re-installed like you said. I did the gedit on smb.conf and changed WORKGROUP to MSHOME.  I also checked on the other 9.10 machine's smb.conf file and it has MSHOME as its workgroup.

On both machines now when I click on Places/Network I get the message, "Opening MSHOME - You can stop this operation by clicking cancel." After a long pause another message comes up saying, "Unable to mount location. Failed to retrieve share list from server." 

When I use Windows Explorer on my XP machine I can see and access the files on one of the 9.10 machines but not the other.

I appreciate your help. I wish I could report better results.

---

### Post by rsnow on 2010-03-01
Update: One 9.10 machine continues as stated above. However, for some unknown (to me) reason the other one now sees all the machines on the lan but it still cannot access their shared files.
It keeps coming up with the "Unable to mount..." message.

Another thing: the machine that still cannot see any others has a smb.conf file and a smb.conf.ucb.dist file in the samba folder. They both contain the same data.

---

### Post by rsnow on 2010-03-06
I might as well close this for all the good it is doing. Thanks to the 2 responders who tried to help. Someday Linux will catch up with the other guys but I probably won't live that long.

---

