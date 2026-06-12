---
title: "Nautilus: &quot;Unable to mount location Failed to retrieve shared list from server&quot;"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by hayhursm on 2011-03-08
Hello,

I believe this has already been addressed but I cannot seem to find a straight solution from any of the forums or a web search.  It seems Nautilus in Ubuntu 10.04 has a bug that prevents it from mounting shared folders via Samba.  For instance if I type this command in terminal: "findsmb" I can see all of my Ubuntu machines running Samba.  If I go to Nautilus, click Network and then click the same machines that "findsmb" discovered, I get the "Unable to mount location" error.  However, if I open Nautilus, press "Ctrl L" to bring up the address bar and type smb://"IP Address Of Samba Machine" then I can finally access the shared folders on that machine and the machine is mounted in the left pane of Nautilus.  Is there a solution to this problem or must I wait for a new version of Nautilus to come out?  As always any help is greatly appreciated!!!

---

### Post by hayhursm on 2011-03-10
Bump

---

### Post by hayhursm on 2011-03-16
Bump

---

### Post by hayhursm on 2011-03-22
Bump

Can anyone help me out?

---

### Post by hayhursm on 2011-03-24
Anyone??

---

### Post by uncledodat on 2011-03-27
Hey, man wish i could help. I'm having the same problem with no answers or gurus to advise.(Unable to mount location Failed to retrieve shared list from server") But i have made so progress since my last "bump" that has still gone unanswered. However, i have managed to pick up a uPnp share from the up stairs xbox (original) on the down stairs xbox (original) as well as the xbox 360. Problem still remains with ubuntu desktop and that where most of my media lives. I really weird that everything on the network sees each other except ubuntu desktop I have a laptop with ubuntu on it im gonna try that one and see what going on there. Best of luck. If you figure it out please dont forget to post I am stumped on this this and to many forums are just not answering the problem.

---

### Post by hayhursm on 2011-03-27
> **uncledodat said:**
> Hey, man wish i could help. I'm having the same problem with no answers or gurus to advise.(Unable to mount location Failed to retrieve shared list from server") But i have made so progress since my last "bump" that has still gone unanswered. However, i have managed to pick up a uPnp share from the up stairs xbox (original) on the down stairs xbox (original) as well as the xbox 360. Problem still remains with ubuntu desktop and that where most of my media lives. I really weird that everything on the network sees each other except ubuntu desktop I have a laptop with ubuntu on it im gonna try that one and see what going on there. Best of luck. If you figure it out please dont forget to post I am stumped on this this and to many forums are just not answering the problem.

I feel your pain.  From what I've gathered I believe it's definitely a Nautilus bug and not Ubuntu itself.  In the mean time, you can manually mount the Samba share by **opening Nautilus**, hit **Ctrl & L** and type this in the Nautilus address bar: **smb://"IPAdressOfMachine/PathToSharedFolder"** It should then bring up the username and password prompt if you have one set.

---

### Post by gordintoronto on 2011-03-27
I often use Nautilus in 10.04 to mount shared folders, with no problem whatsoever. I select the Place, Network, then double-click: Windows Network, the workgroup, the computer, the share. I access both Ubuntu and Windows shares using this method.

---

### Post by hayhursm on 2011-03-28
> **gordintoronto said:**
> I often use Nautilus in 10.04 to mount shared folders, with no problem whatsoever. I select the Place, Network, then double-click: Windows Network, the workgroup, the computer, the share. I access both Ubuntu and Windows shares using this method.

It's just like anything else in Ubuntu...for some it works great and for others it doesn't.  For example, when I installed Maverick on my laptop it would just boot to a blank screen, yet others have great success with it.  So its the same thing with Nautilus, why won't it auto mount the share folders??? I have no idea...I guess that's why we're here.

---

### Post by atari_gods on 2011-03-28
Chalk another one up to the list of people suck on this one.

I recently finished refurbishing an old desktop I had, in order to make it a Linux machine (the windows was broken and is why it was old, dirty, and unused). I got everything installed nicely, a bit slower than what my laptop does seeing that it's a PIII cpu, and access to the internet was successful. Now, I wanted to use my home wired network to transfer files between the Linux laptop and "new" Linux desktop. What did I find recommended; Samba. So I do the install of the smb and nfs modules and setup the files for sharing, but neither machine can see the others file.

Now I've done more searching through forums and tool-tip pages and the best thing I've found was this:

[URL="http://ubuntuforums.org/showthread.php?t=1705328&highlight=samba+cant+see+others+myself"]http://ubuntuforums.org/showthread.php?t=1705328&highlight=samba+cant+see+others+myself
[/URL]
It sort of addresses this problem, but when I tried the code inside I am back at this threads main issue: "Unable to mount location. Failed to retrieve share list from server."

When I tried your suggestion "smb://IPADDRESS" accessing one computer from the other I could access a share file on the old desktop, BUT I could not access any files on the laptop. The message received when trying to access the laptop files was "Could not display smb://*IPADRESS*  Error: Failed to retrieve share list from server. Please select another viewer and try again."

Working on this problem is very aggravating. We need some answers, and there should be some code patching for all the folks who are still stuck on this.

---

### Post by bab1 on 2011-03-29
> **atari_gods said:**
> Chalk another one up to the list of people suck on this one.

...

...

...

When I tried your suggestion "smb://IPADDRESS" accessing one computer from the other I could access a share file on the old desktop, BUT I could not access any files on the laptop. The message received when trying to access the laptop files was "Could not display smb://*IPADRESS*  Error: Failed to retrieve share list from server. Please select another viewer and try again."

Working on this problem is very aggravating. We need some answers, and there should be some code patching for all the folks who are still stuck on this.

It is an IP address to host (COMPUTER) name issue for sure.  The issue is not a bug but rather the manner in which Samba (actually the SMB protocol) resolves the name to IP address mapping.

This is why you can use the IP address to find the share and can't when using the hostname.  One way to overcome this is making sure that all hostnames are listed (correctly) in each of the /etc/hosts files on your Ubuntu hosts and you can then [COLOR="Blue"]**ping all hosts by name**[/COLOR] [COLOR="Green"]**from all hosts**[/COLOR].  Then you should be able to browse the shares.

The SMB protocol is complicated and very arcane, but very flexible.  It is all we have to use when Windows shares are involved.  As an example going to a Windows share via smb://ipaddres_of _share is different than browsing shares.  Browsing can only be done by name and the direct connection can be done either way.

The best guide I know of is [**_Samba-3 By Example_**]("http://www.samba.org/samba/docs/man/Samba-Guide/").  Read it all the way through at least once.  The best guide to the parameters in the smb.conf file is from the [**_official documentation_**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").

I have been running Samba on Ubuntu from 7.04 and have been using the same configuration.  It has always worked for browsing and direct access of my Windows shares.

---

### Post by atari_gods on 2011-03-29
Thank you for the suggestions bab1. I had a look at /etc/hosts and it did only show the two 127 addresses it normally has (that is for the desktop, haven't checked the laptop).

Looks like I've got a lot of reading to be starting on.

---

### Post by bab1 on 2011-03-29
> **atari_gods said:**
> Thank you for the suggestions bab1. I had a look at /etc/hosts and it did only show the two 127 addresses it normally has (that is for the desktop, haven't checked the laptop).

Looks like I've got a lot of reading to be starting on.
The /etc/hosts file is a DNS primitive.  By that I mean it was the first use of mapping between hostname and IP address for unix type hosts.

The network range 127.0.0.0/8 (any IP address that starts with 127) is designated for the virtual NIC (e.g. the loopback address).  The hostname should never be the loopback address unless there is no network card (NIC such as: eth or wlan etc).  The hostname should map to the IP address you have assigned to the network card.

Here is my /etc/hosts file:```
bab1@malibu:~$ more /etc/hosts
127.0.0.1	localhost
192.168.1.3	malibu malibu.beach

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

Something to note:  most times you will find the hostnmame  listed as *hostname.domain* first and then just the hostname.  This is not completely correct.  The first name (192.168.1.3 malibu) is the hostname.  Any name used after that is a local net alias (malibu.beach).

Many folks reverse this so they can have FQDN without having a DNS server.

---

### Post by hayhursm on 2011-03-29
> **bab1 said:**
> It is an IP address to host (COMPUTER) name issue for sure.  The issue is not a bug but rather the manner in which Samba (actually the SMB protocol) resolves the name to IP address mapping.

This is why you can use the IP address to find the share and can't when using the hostname.  One way to overcome this is making sure that all hostnames are listed (correctly) in each of the /etc/hosts files on your Ubuntu hosts and you can then [COLOR=Blue]**ping all hosts by name**[/COLOR] [COLOR=Green]**from all hosts**[/COLOR].  Then you should be able to browse the shares.

The SMB protocol is complicated and very arcane, but very flexible.  It is all we have to use when Windows shares are involved.  As an example going to a Windows share via smb://ipaddres_of _share is different than browsing shares.  Browsing can only be done by name and the direct connection can be done either way.

The best guide I know of is [**_Samba-3 By Example_**]("http://www.samba.org/samba/docs/man/Samba-Guide/").  Read it all the way through at least once.  The best guide to the parameters in the smb.conf file is from the [**_official documentation_**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").

I have been running Samba on Ubuntu from 7.04 and have been using the same configuration.  It has always worked for browsing and direct access of my Windows shares.


So on top of creating and defining a: **/etc/samba/lmhosts **file I also need to define all share PC's and their corresponding IP addresses in the **/etc/hosts** file as well?  Is this why Nautilus is not auto mounting when I double click the PC's under Network?

---

### Post by collisionystm on 2011-03-29
If you arent doing any kind of sharing from your ubuntu machine just reinstall samba. 

apt-get purge samba samba-common smbfs

apt-get install samba samba-common smbfs

---

### Post by bab1 on 2011-03-29
> **hayhursm said:**
> So on top of creating and defining a: **/etc/samba/lmhosts **file I also need to define all share PC's and their corresponding IP addresses in the **/etc/hosts** file as well?  Is this why Nautilus is not auto mounting when I double click the PC's under Network?

Maybe...

You can use /etc/lmhosts if you wish for Samba itself. The /etc/lmhosts file maps NETBIOS names to IP address.  Since the *nmbd* daemon will convert the hostname into a NETBIOS name (15 char or less), the /etc/hosts file is more convenient.

I feel that since you need hostname to IP mapping anyway and hostnames become NETBIOS names via the *nmbd* there is no need for the /etc/lmhosts.

I only use the /etc/hosts mapping and Samba works fine for me.

---

### Post by hayhursm on 2011-04-07
> **bab1 said:**
> Maybe...

You can use /etc/lmhosts if you wish for Samba itself. The /etc/lmhosts file maps NETBIOS names to IP address.  Since the *nmbd* daemon will convert the hostname into a NETBIOS name (15 char or less), the /etc/hosts file is more convenient.

I feel that since you need hostname to IP mapping anyway and hostnames become NETBIOS names via the *nmbd* there is no need for the /etc/lmhosts.

I only use the /etc/hosts mapping and Samba works fine for me.

Sorry for taking so long to get back.  I added all PC's sharing via Samba to the **/etc/hosts **file but I still get the error: **Unable to mount location Failed to retrieve share list from server **when I double click on PC under Nautilus/Network.I just don't know what else to do, I guess I will have to manually mount all the PC's via Nautilus address bar each time I want to share files.  :rolleyes:

---

### Post by carl0ski on 2011-05-01
remember you'll often find windows networks do not allow anonymous

try


smb://username: password@ipaddress/

smb://me: password@192.168.1.11

---

### Post by hayhursm on 2011-05-02
> **carl0ski said:**
> remember you'll often find windows networks do not allow anonymous

try


smb://username: password@ipaddress/

smb://me: password@192.168.1.11

I only have Ubuntu machines on my network but regardless the method you suggested does work.  If I go to Nautilus and enter **smb://username: password@ipaddress **in the address bar I can access that particular machine.  However, the original problem was that I cannot just click the icons under Network in Nautilus and access the share folder.  If I do this I always get an: **Unable to mount location Failed to retrieve share list from server** error.

---

### Post by Morbius1 on 2011-05-02
3 possible things you might want to investigate:

[1] nmbd isn't running on any of your machines. Run the following command on all of them and see if you still get the error message:
```
sudo service nmbd restart
```[2] Your machine names are too long.  It has to be 15 characters or less in length. The easiest thing to do is use samba itself to broadcast a smaller name:

Edit /etc/samba/smb.conf as root and add the following line to the [global] section:
```
netbios name = something-less-than-or-equal-to-15-characters-in-length
```[3] Speaking of broadcast, put it first in the methods samba uses to find other machines:

Go back to smb.conf and add another line to the [global] section:
```
name resolve order = bcast host lmhosts wins
```In all cases restart samba:
```
sudo service smbd restart
```Wait a few minutes - seriously - while the network settles down after a samba restart and see if you still get the error message.

---

### Post by hayhursm on 2011-05-02
> **Morbius1 said:**
> 3 possible things you might want to investigate:

[1] nmbd isn't running on any of your machines. Run the following command on all of them and see if you still get the error message:
```
sudo service nmbd restart
```[2] Your machine names are too long.  It has to be 15 characters or less in length. The easiest thing to do is use samba itself to broadcast a smaller name:

Edit /etc/samba/smb.conf as root and add the following line to the [global] section:
```
netbios name = something-less-than-or-equal-to-15-characters-in-length
```[3] Speaking of broadcast, put it first in the methods samba uses to find other machines:

Go back to smb.conf and add another line to the [global] section:
```
name resolve order = bcast host lmhosts wins
```In all cases restart samba:
```
sudo service smbd restart
```Wait a few minutes - seriously - while the network settles down after a samba restart and see if you still get the error message.

Thanks for the info...this might be a problem though, when I try: ```
sudo service nmbd restart
``` I get: ```
nmbd: unrecognized service
```  I guess I failed to mention that I'm running **Samba Version 3.5.6** from: **ppa: polslinux/ppa.  **Or does that matter?

---

### Post by Morbius1 on 2011-05-02
I think as long as you don't have Samba4 installed then you're safe. Do you have the full suite of samba packages installed:

samba
samba-common
samba-common-bin

Either that or you're a Debian user disguised as an Ubuntu user. In which case it's:
```
sudo service samba restart
```

"samba" includes nmbd and smbd in Debian.

---

### Post by hayhursm on 2011-05-02
> **Morbius1 said:**
> 3 possible things you might want to investigate:

[1] nmbd isn't running on any of your machines. Run the following command on all of them and see if you still get the error message:
```
sudo service nmbd restart
```[2] Your machine names are too long.  It has to be 15 characters or less in length. The easiest thing to do is use samba itself to broadcast a smaller name:

Edit /etc/samba/smb.conf as root and add the following line to the [global] section:
```
netbios name = something-less-than-or-equal-to-15-characters-in-length
```[3] Speaking of broadcast, put it first in the methods samba uses to find other machines:

Go back to smb.conf and add another line to the [global] section:
```
name resolve order = bcast host lmhosts wins
```In all cases restart samba:
```
sudo service smbd restart
```Wait a few minutes - seriously - while the network settles down after a samba restart and see if you still get the error message.

Thank you for this but unfortunately it did not work.  I have attached a screen-shot of the error to help depict exactly what I'm seeing.  Could this error be more related to Nautilus than my Samba configuration?

---

### Post by rodheal on 2012-02-21
Hi I'm using Ubuntu 11.10 32bit on a Samsung NP-Q210 laptop and had the same problem. Being new to Ubuntu I thought I'd try installing "Samba" from the Ubuntu software centre, when I looked there was also  "Smb4k" so I installed that as well. Then when I tried to connect to a windows network through the "browse network" tab my "Home Folder" my NAS box had appeared.

I didn't get a chance to try and of the tips but installing those two programs did the trick.

---

