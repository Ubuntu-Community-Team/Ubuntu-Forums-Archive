---
title: "Samba suddenly does not detect windows computer (and vice versa) on my network"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by maitrebart on 2009-02-20
Hi,

since I installed 8.04 few weeks ago I could enjoy samba and transfer files between my 2 computers (ubuntu <--> windows) on my home network.

All of a sudden, yesterday, neither was able to detect the other one, without upgrading ubuntu nor windows or changing anything on my router.

However, I know I ran a couple of security programs (tiger, chkrootkit) to detect if I had a possible breach with ubuntu. I'm under the impression that they may have altered my samba configuration, though I thought they would only indicate me possible security flaws. (or probably that is indeed what they did and something else broke samba?)

Here are the info I know:

- Samba is still installed (and even reinstalled). Grepping for smb with "ps ax" gives 2 smbd entries.
- I can ping each other computer by their name and ip on both computers.
- I have a couple of shared directories on both computers. I can see them locally on each computer, but I can no more see them remotely from the other computer.
- I even had installed putty on windows and sshd on ubuntu and it was working. Now putty can no more detect ubuntu's.
- If I do smbtree it returns nothing.
- If I enter ubuntu computer's host name or ip in windows explorer, it fails to detect my ubuntu computer (but I used to see my computers in Favorite Network Places).
- In nautilus, clicking on Network then Windows Network (smb:///) gives nothing (but I used to see my computers before).

I wonder if it exists some kind of automatic samba configuration tool (something like what ran at ubuntu's installation) in order to avoid messing around with tricky samba configuration files?

Otherwise I think I will have to rely on specific and detailed instructions from all you!

Thanks.

---

### Post by maitrebart on 2009-02-20
Here are some outputs:

% smbclient -L //marge -U bart

Domain=[MARGE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC distant
	Shared Documents Disk      
Domain=[MARGE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
	G$              Disk      Partage par d	F$              Disk      Partage par d	ADMIN$          Disk      Administration 	C$              Disk      Partage par d
	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------

% smbclient //marge/C$ -U bart

Domain=[MARGE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
tree connect failed: NT_STATUS_ACCESS_DENIED

---

### Post by maitrebart on 2009-02-20
Something promising: the following seems to work (same as previous except for the $):

% smbclient //marge/C
 
Domain=[MARGE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \> dir
  AUTOEXEC.BAT                        A        0  Sat Jan 10 18:22:04 2009
  CONFIG.SYS                          A        0  Sat Jan 10 18:22:04 2009
  Games                              DH        0  Sun Feb  1 23:10:07 2009
  IO.SYS                           AHSR        0  Sat Jan 10 18:22:04 2009
  MSDOS.SYS                        AHSR        0  Sat Jan 10 18:22:04 2009
  pagefile.sys                      AHS 3488649216  Fri Feb 20 06:03:44 2009
  RECYCLER                          DHS        0  Wed Jan 21 07:06:05 2009
  Shared Documents                    D        0  Sat Jan 20 16:54:29 2007
  System Volume Information         DHS        0  Sat Jan 10 18:27:48 2009
  zip                                 D        0  Sat Jan 31 00:01:41 2009

		38158 blocks of size 2097152. 26893 blocks available

Still, I cannot see my windows computer in nautilus.

---

### Post by Florida Cracker on 2009-02-20
Give this a try
sudo gedit /ect/nsswitch.conf
go down to hosts:files line and insert wins in front of dns.
(hosts:files ################# wins dns ######)
This worked for me.

---

### Post by maitrebart on 2009-02-20
I just found that I can connect using File|Connect To Server... in nautilus.
I can access most of the listed shares, but none of the ...$ shares. But I don't really mind.

So the problem is around the Network Servers entry in nautilus. It lists nothing. Also still not able to see any share in windows explorer.

---

### Post by maitrebart on 2009-02-20
> **Florida Cracker said:**
> Give this a try
sudo gedit /ect/nsswitch.conf
go down to hosts:files line and insert wins in front of dns.
(hosts:files ################# wins dns ######)
This worked for me.

I changed the line but it does not work.
However I'll leave it there in case I have to reboot in order for it to become active.
Thanks.

---

### Post by maitrebart on 2009-02-20
Interesting: If I click Network Servers in nautilus, I get the Windows Network icon only with network:/// in the location bar (it used to have a couple of icons there before). Then if I click Windows Network I get no icon and smb:/// in the location bar (I used to have 1 or 2 icons there before). HowWhoever, if I specify smb://marge in the location bar, I get the shares on that computer.

So the problem seems to be linked to Network Servers (network://) not being able to list computers on the network.

I must be close to a solution!

---

### Post by maitrebart on 2009-02-21
After googling around for few hours, I found out that it was caused by a change in the iptables. I guess running tiger and chkrootkit altered my iptables.

For a solution, see this thread:

[http://ubuntuforums.org/showthread.php?t=1076038]("http://ubuntuforums.org/showthread.php?t=1076038")

but make sure you have exactly the same problem.

I would recommend to check the following before:
- Check that you can ping each other computer.
- Check that samba is working (with smbclient or with smb://... in nautilus) so that ubuntu can access windows shares.

In my case, windows could not even detect my ubuntu box.

Good luck!

---

