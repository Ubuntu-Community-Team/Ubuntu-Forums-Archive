---
title: "File sharing on xubuntu"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by xob on 2011-01-18
I can't figure out how to share files between two computers. I would expect that I can simply right click on the folder and make it a share folder, but there is no option in xubuntu 10.10
I looked on the Internet and someone suggested Application > System > Folder Sharing, but this also doesn't exist.
Does anyone knows how to do it. This is a basic thing it should be easy to do I think.
Thanx, Rob

---

### Post by canhoto on 2011-10-23
I don't know, but I have exactly the same problem. Did you manage tod o that since then?

---

### Post by Toz on 2011-10-23
Folder sharing, like it exists in ubuntu, doesn't exist in OOB xubuntu. One option is to install **system-config-samba** (along with **samba**) and use it to set up file sharing. Here's a quick how-to:

1. Install samba and system-config-samba from the software centre or from the command line:
```
sudo apt-get install samba system-config-samba
```

2. Fireup system-config-samba. Look for it under the System submenu (titled "Samba")

3. Create the share (File->Add Share or click the plus icon):
- Directory = select directory to share
- Share name = share name
- Description = description
- Writable = to allow users to write to directory
- Visible = to make the share visible while browsing
- Access tab = select who should have access to the share

4. If you have a firewall active, make sure you allow through the samba ports. If using ufw, then from the command line:
```
sudo ufw status verbose
```
...if the status is enabled and ports 137/udp, 138/udp, 139/tcp, 445/tcp are not allowed through, issue the follow command:
```
sudo ufw allow samba
```
...then check to see that all is okay
```
sudo ufw status verbose
```
Otherwise check using your firewall tool.

5. Connect to the share from other computers.

---

### Post by canhoto on 2011-10-24
> **Toz said:**
> Folder sharing, like it exists in ubuntu, doesn't exist in OOB xubuntu. One option is to install **system-config-samba** (along with **samba**) and use it to set up file sharing. Here's a quick how-to:

1. Install samba and system-config-samba from the software centre or from the command line:
```
sudo apt-get install samba system-config-samba
```2. Fireup system-config-samba. Look for it under the System submenu (titled "Samba")

3. Create the share (File->Add Share or click the plus icon):
- Directory = select directory to share
- Share name = share name
- Description = description
- Writable = to allow users to write to directory
- Visible = to make the share visible while browsing
- Access tab = select who should have access to the share

4. If you have a firewall active, make sure you allow through the samba ports. If using ufw, then from the command line:
```
sudo ufw status verbose
```...if the status is enabled and ports 137/udp, 138/udp, 139/tcp, 445/tcp are not allowed through, issue the follow command:
```
sudo ufw allow samba
```...then check to see that all is okay
```
sudo ufw status verbose
```Otherwise check using your firewall tool.

5. Connect to the share from other computers.

I did all that with Samba. The only way I can connect to my Xubuntu is via a ftp client on the other computer. It doesn't appear automatically in the scanned networks, nor via the usual afp before the IP address. My other computer is a mac. I don't know if I should use NFS, but I have several nfs-stuff installed and nothing happens.

---

### Post by Toz on 2011-10-24
Is the samba service running? What does the following say?
```
sudo service smbd status
```

---

### Post by canhoto on 2011-10-24
> **Toz said:**
> Is the samba service running? What does the following say?
```
sudo service smbd status
```

The output was:

> smbd start/running, process 575

---

### Post by Bucky Ball on 2011-10-24
Another way? Install Nautilus on your Xubuntu box, make it the default, open it then click 'Network' in the left panel. You will see all machines on the network (and be able to connect with any of their shared folders/partitions).

I have static IPs on all my machines which makes life a lot easier (for me at least). For the other boxes (I presume yours are running Ubuntu), Places>Connect to server. I have ssh installed so I choose ssh  from the drop down list, insert the IP address of the Xubuntu box, you'll be asked for username and password (for the Xubuntu box), insert them and you're there.

---

### Post by canhoto on 2011-10-24
> **Bucky Ball said:**
>  make it the default How-to?
>  For the other boxes (I presume yours are running Ubuntu 

They are running Mac OS X ... :neutral:

---

### Post by Toz on 2011-10-24
To continue with the system-config-suggestion, make sure that they are talking using the same protocol. If you've configured samba on ubuntu, make sure the mac has the smb protocol enabled. I'm not mac expert, but as far as I know, the afp protocol won't connect to a samba share.

---

### Post by canhoto on 2011-10-25
> **Toz said:**
> To continue with the system-config-suggestion, make sure that they are talking using the same protocol. If you've configured samba on ubuntu, make sure the mac has the smb protocol enabled. I'm not mac expert, but as far as I know, the afp protocol won't connect to a samba share.

Well, although the Xubuntu doesn't automatically appear on the Mac's list of networks, I can connect to using afp://ip.add.ress !

I don't know if it was because of the Samba configuration, the installation of Nautilus with the sharing permissions of my home folder enabled, the installing of some nfs tools (which I have not even configured)... but it works. I just have to choose the option "connect to server" on my Mac's Finder and it will connect (I have it on my my favorite servers list, so it's quick).

I just ask myself why it doesn't automatically appear the network list of the Finder... but never mind.

Another question: how do you enable screen sharing so that the other computer(s) can connect to your Xubuntu screen?

---

### Post by Toz on 2011-10-25
> **canhoto said:**
> Another question: how do you enable screen sharing so that the other computer(s) can connect to your Xubuntu screen?
In a nutshell, this should work (works on 11.10):

1. Install vino (vnc server)
```
sudo apt-get install vino
```

2. Create vino preferences:
```
vino-preferences
```
...and adjust accordingly

3. Run the vino server:
```
/usr/lib/vino/vino-server
```

4. Make sure there is no firewall in the way.

5. Connect from the MAC using a vnc client - default port is 5900.

If you want to make the vino-server start automatically, add it to your Application Autostarts.

***Security note: vnc is not a secure protocol. If you are in an insecure environment, consider tunneling vnc through ssh.

---

### Post by Bucky Ball on 2011-10-26
> **Toz said:**
>  If you are in an insecure environment, consider tunneling vnc through ssh.

+1. Good idea anyway.

You could do it with SSH as I suggested before and employ some Mac software to communicate. Does Filezilla run on Mac? Putty probably does. There must be a lot of avenues. 

Also as I mentioned, static IPs are going to make your life a lot easier, at least for now, if you are going this way.

---

### Post by JonNicholson on 2012-07-20
Folder sharing with Xubuntu is easy, but the Thunar file manager is not the way to do it.  (I'm using Xubuntu 12.04, but I know this worked for 11.10 also.)

When you install Xubuntu, BOTH Thunar and Nautilus file managers are automatically installed.  Thunar is the selected file manager by default.  To share folders/files, go to the "Applications Menu" in the top-left corner of the screen and click on "Settings", then click on "Settings Manager".  Click on the "Preferred Applications" icon.  Select the "Utilities" tab, and under "File Manager", drop down the list and select "Nautilus".

Summary:  Applications Menu/Settings/Settings Manager/Preferred Applications/Utilities/File Manager, then select Nautilus.

The next step is to go back to the Applications Menu and click on "System", then click on "Synaptic Package Manager".  When Synaptic opens, search for the package named "nautilus-share".  If it is not already installed, install it now.  Close Synaptic when you are finished, then reboot the computer.  When you open a new folder window, right-clicking on any folder will allow you to set the "Sharing Options".

Note:  Any folder icons that you already placed on your desktop using Thunar will remain Thunar objects.  Delete them and create new folder icons with Nautilus, if you want to.

Another note:  If you want to see "Shared Folders" on your Applications Menu, go to Applications Menu/Settings/Main Menu, and in the left column, select "System".  You will see "Shared Folders" in the right column.  Select that, then close the Main Menu window, and "Shared Folders" will thereafter be visible under Applications Menu/Settings.

---

### Post by Toz on 2012-07-20
> **JonNicholson said:**
> Folder sharing with Xubuntu is easy, but the Thunar file manager is not the way to do it.  (I'm using Xubuntu 12.04, but I know this worked for 11.10 also.)

When you install Xubuntu, BOTH Thunar and Nautilus file managers are automatically installed.
No they are not - only thunar is installed in a default Xubuntu install. You must have installed nautilus separately or it was installed as a dependency to something else you installed.
> Thunar is the selected file manager by default.  To share folders/files, go to the "Applications Menu" in the top-left corner of the screen and click on "Settings", then click on "Settings Manager".  Click on the "Preferred Applications" icon.  Select the "Utilities" tab, and under "File Manager", drop down the list and select "Nautilus".

Summary:  Applications Menu/Settings/Settings Manager/Preferred Applications/Utilities/File Manager, then select Nautilus.

The next step is to go back to the Applications Menu and click on "System", then click on "Synaptic Package Manager".  When Synaptic opens, search for the package named "nautilus-share".  If it is not already installed, install it now.  Close Synaptic when you are finished, then reboot the computer.  When you open a new folder window, right-clicking on any folder will allow you to set the "Sharing Options".

Note:  Any folder icons that you already placed on your desktop using Thunar will remain Thunar objects.  Delete them and create new folder icons with Nautilus, if you want to.

Another note:  If you want to see "Shared Folders" on your Applications Menu, go to Applications Menu/Settings/Main Menu, and in the left column, select "System".  You will see "Shared Folders" in the right column.  Select that, then close the Main Menu window, and "Shared Folders" will thereafter be visible under Applications Menu/Settings.
Using nautilus is one way of sharing files - just be careful because nautilus by default will manage your desktop and conflict with xfdesktop4. As mentioned earlier, samba is another way. In addition, gigolo is an option for managing shared folders as well.

Also, this thread is almost 9 months old. Closing. Please create a new thread if you wish to discuss file sharing on Xubuntu.

---

