---
title: "Trouble Connecting to Some Windows Machines"
date: 2005-03-16
forum: Networking &amp; Wireless
---

### Post by mwalt2 on 2005-03-16
I'm new to linux and ubuntu.  I am having some problems connecting to some WinXP computers on my school's network.  There are 2 computers in my lab running WinXP right next to one another.  I am able to connect to 1 computer using samba, but not the other.  Both computers can connect to each other using windows.  They both are set up with the same WinXP firewall settings, etc.  I don't understand why I can see 1 on the network, and not the other one.  I have even disabled the WinXP firewall and/or typing in the IP address of the machine and I still cannot connect to the box.  Does anyone have any ideas why samba only sees 1 of the 2 computers?  Filesharing in Windows works fine for both machines...

---

### Post by wylfing on 2005-03-16
Please provide some more specifics. What exactly do you do and what are the results? Saying you "can't connect" is too vague.

I'm going to take a guess that you are trying to browse to some Windows shares using the Computer > Network route. And one of the computers doesn't show up in the window, and the other one asks for a name and password (or not) and always says you don't have the required priveleges to access the computer. Right so far?

First, make sure you have all the samba goodies installed. Open a terminal and type these commands:
```
sudo apt-get update
sudo apt-get install samba samba-common
```
You may be asked for your password. If so, enter it.

Ok, now try this: Open a Nautilus window by choosing Computer > Home. Type Control-L and enter the address of a shared folder using this format:

smb://computername/sharename

Then click open. It will (probably) ask for a username and password. Type them in and click OK. Did it show the folder contents?

---

### Post by mwalt2 on 2005-03-16
Thanks for the reply.  Samba is installed and updated.  I am using Hoary Preview if that makes any difference.  The error I am getting is "Error Displaying Folder:  The folder contents could not be displayed.   Sorry, couldn't display all contents of "Windows Network:  Computer Name."  It just like if you made up a computer name that is not on a network and tried to connect to it.  I do not see the computer in the Network window of ubuntu nor can I connect to it by typing smb://computer name.  The two windows machines are configured identically (I did the windows installs for both just recently).  The only difference is that the machine I cannot connect to has a gigabit ethernet controller whereas the other only has 10/100.  Ubuntu/Samba act as if the computer does not exist on the network, but everything works fine with Windows networking from several different windows machines.

---

### Post by wylfing on 2005-03-17
What is your network topology? Do all the boxes connect to a hub? If so, the gigabit part shouldn't be relevant. FYI, you will not be able to connect with smb:// unless you specify both the computer name and the share name. The part about 'Sorry, couldn't display all contents of "Windows Network: Computer Name." ' is typical Nautilus samba browsing goofiness. Browing samba shares with Nautilus depends on fickle settings in smb.conf which no one knows how to get right. Focus on connecting directly with smb://

Other things to check/try:
1. Make absolutely sure that all the computers are assigned to the same Windows workgroup.
2. Make absolutely sure there is a shared folder on the computer you want to connect to, and that its permissions are set appropriately. Do not rely on guest logins -- you should be connecting with a real username and password.
3. In your smb.conf, try setting socket options like this:
```
socket options = IPTOS_LOWDELAY TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

```(after changing this type 'sudo /etc/init.d/samba restart' in a terminal)
4. Try typing this on the command line:
```
smbclient -U username -L computername
```where 'username' is the username you're trying to log in as on the remote machine, and 'computername' is the name of the machine you're trying to log in to. It should prompt for a password. Does it display a list of shared folders?

---

