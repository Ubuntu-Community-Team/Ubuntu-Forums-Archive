---
title: "No Samba Shares on 8.10"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by tebbens on 2009-01-26
I'm not able to view network samba shares via (Places > Network & Places > Connect to a Server) from a fresh install of 8.10.

Places > Network shows: Windows Network > WORKGROUP (but then nothing inside)
Places > Connect to a server shows: Cannot display location "smb://192.168.1.60/" No application is registered as handling this file.

Although I CAN see the shares using smbclient -L 192.168.1.60

A new install of 8.10 has samba-common, smbclient, nautilus-share, libsmbclient.
Do I need to install samba, smbfs or samba-tools or should this be working ?

Thanks !

---

### Post by Iowan on 2009-01-26
Standard installation *should* have (what I call) Samba-client.  To share files TO Windows would require installing the Samba-server. 
[This]("http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html") How-To might help - at least to see if shares *can* be accessed.

---

### Post by tebbens on 2009-01-30
> **Iowan said:**
> Standard installation *should* have (what I call) Samba-client.  To share files TO Windows would require installing the Samba-server. 
[This]("http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html") How-To might help - at least to see if shares *can* be accessed.


I have to bump this thread again.... something is not right.

On a new install of 8.10 I can view remote samba shares via smbclient & smbtree, but nothing in Nautilus (Places > Network or Places > Connect to a server).

Is a fresh installed Ubuntu Desktop (specifically 8.10) able to view Samba/Windows shares on the local network via Nautilus ???

---

### Post by Iowan on 2009-01-30
Did it work via the Places->Computer "Go to"  smb://x.x.x.x method in the [link]("http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html")?

---

### Post by FishRCynic on 2009-01-30
i have had no problem viewing them via the network in nautilus until i updated today.  i made the mistake of updating a hardy to intrepid an hour ago and have the same problem.  were you able to view them prior to today's updates?

---

### Post by FishRCynic on 2009-01-30
interesting - no longer viewable in hardy amd64, intrepid amd64 or intrepid server x86 (ubuntu desktop installed) - samba configurations unchanged - but get nautilus cannot handle "network" locations  (even as root)

---

### Post by FishRCynic on 2009-01-30
> **Iowan said:**
> Did it work via the Places->Computer "Go to"  smb://x.x.x.x method in the [link]("http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html")?

this works but was never necessary before

it used to be point and click - now its point type and click - i preferred it just point and click

---

### Post by Mriswithe on 2009-02-04
I just wanted to say, fairly fresh install of 8.10 I can see my network computers up to the point of seeing the folders (by way of clicking on network, going to windows network -> workgroup -> the selecting the windows computer then the shared folder. Once I click on the shared folder it sticks with an open window that says "Opening "name of folder"" then after about 45 seconds says unable to mount location.

If I go by IP address then I can access everything just fine and it has very quick response time whereas if I do it through the network selection there is a bit of delay between choosing something and seeing what is in the folder. This isn't a fix of the problem but it does allow me to access my files. Thought I would share my experiences.

---

### Post by Iowan on 2009-02-04
I haven't tried it, but see if [this]("http://www.sigmundvoid.com/2007/08/netbios-names-and-ubuntu/") helps access by name.

---

### Post by posterlion on 2009-02-04
I've been going through this problem for the last week myself. I've read many of the posts on this forum and have not found any post that addresses the problem directly.

Many posts recommend changing samba settings. Samba is used to present Linux shares to Windows not the other way around. Other posts recommend turning off password protection, but this is not a solution, it is merely a work-around.

Ubuntu should be able to recognize a Windows share immediately after it has been installed with zero modifications.

I've done quite a bit of research and have determined that this problem was introduced in version 8.04 and has carried through into 8.10 as well, but not in exactly the same way.

I would like to point out that this problem is not specific to USB shares. It is a problem with all WINDOWS shares. In my test lab I am using work group networks, not domains. I have four machines involved in my testing:

poster0 - Windows XP Professional
poster1 - Windows Vista Home Premium
poster2 - Ubuntu 7.10, 8.04, and 8.10
Barb - Windows XP Home.

The network is a wireless access point using DHCP.

Ubuntu 7.10 works perfectly with XP and Vista. If the share is a public share (USB or otherwise) you can get to it. If the share is password protected, then Ubuntu prompts the user user for credentials. If the credentials can be authenticated the share will be presented.

Ubuntu 8.04 will prompt for a password on a public XP share (which is an invalid response). The credentials are not authenticated (at least I don't think so) because if the user simply hits the cancel button at the credentials prompt, the share will be displayed. Windows Vista shares cannot be displayed period.

Ubuntu 8.10 fixes the invalid credentials prompt for XP shares and XP shares are displayed, but Vista shares (public or protected) can not be displayed.

Later on . . .

I found a way to connect to my Vista shares, although it is not ideal. I think I am on the right track to resoving this issue.

After you select NETWORK from PLACES, click on the button that has an illustration of a paper and pencil (toggle between button and text-based location bar).

Then you can type in the path to your share. Mine is smb://poster1/public

I pressed enter after typing in the path and I was presented with a credentials box. Knowing that the share was public I decided to click cancel and then the share was presented.

I did this test with 8.04 which as I already reported, should not display a credentials box for a public share.

Give this a try and report back on your results.

And then . . .

There is one valid reason that I have found for editing the /etc/samba/smb.conf file.

The default workgroup parameter in Ubuntu 7.10 is MSHOME. However, beginning with Ubuntu 8.04 the default value changed from MSHOME to WORKGROUP. I assume this change was made because the default value in Windows Vista was changed from the XP default of MSHOME to WORKGROUP.

I changed my smb.conf file from WORKGROUP to MSHOME which is my networks workgroup name.

After restarting, the credentials box displays MSHOME instead of WORKGROUP when I connect to my Vista shares.

To edit this file you must open a terminal window from APPLICATIONS => ACCESSORIES => TERMINAL

once inside the terminal window type:

sudo gedit /etc/samba/smb.conf

Change the workgroup parameter to the workgroup of your network. For example, my workgroup is MSHOME so I changed my smb.conf file to look like:

workgroup = MSHOME

Don't forget to save your changes then either reboot your machine or recycle your samba service. Afterwards, any time a credentials box is displayed the workgroup field will contain the workgroup of your network.

I have decided to investigate the remaining smb.conf entries to see if the resolution for this problem can indeed be solved with additional changes to this file.

And Now . . .

I have combed through all the entries in the smb.conf files, comparing version 7.10 with 8.04, but have found no additional parameter that might help this situation.

poster . . .

---

### Post by FishRCynic on 2009-02-08
had to install wins server and configure all pcs to use it
(and in windows netbios over tcp)

fixed a lot of things in networking for more than just ubuntu.

---

