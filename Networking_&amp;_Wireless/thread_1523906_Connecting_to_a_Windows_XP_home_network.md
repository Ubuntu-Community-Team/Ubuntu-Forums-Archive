---
title: "Connecting to a Windows XP home network"
date: 2010-07-04
forum: Networking &amp; Wireless
---

### Post by CHUCKeR_ on 2010-07-04
Well first off sorry to all the seasoned Ubuntu veterans because I'm certain this question has been answered 100's of times before but here it is. 

I have a beefy Win Box desktop that i'm using as a media server and i have a home network setup already using windows xp. I had everything running fine and the PC connects flawlessly to my Bravia TV and both my ps3's so i know the network and sharing settings are setup just fine. Anyways i got tired of all the Windows 7 BS and decided i would once again use Ubuntu on my Toshiba netbook. So the question is how in the heck do i get my Ubuntu netbook to connect to the Desktop? I've tried browsing the fourms but either i'm missing something of just a little slow. What "extensions" would i need to get and how would i go about implementing it from there? Any help would be appreciated and thank you ahead of time for your time....

---

### Post by Roasted on 2010-07-04
Well, first you would need "samba" installed, which is a network protocol that allows Mac/Linux/Windows to all "talk" to each other on the network. I'm not positive if Samba comes pre-installed on newer versions of Ubuntu. If you want to check, fire up terminal and run sudo apt-get install samba, or look up "samba" in Synaptic Package Manager under System - Administration - Synaptic Package Manager.

Secondly, you could try opening up Nautilus, which is Ubuntu's equivalent of Windows Explorer. AKA - your home directory under Places - Home. Then open the location bar by hitting CTRL + L. It should turn to a text box with the current path to the folder you're seeing. Erase that, and try putting in:

smb://path/to/windows/box.

If you connect via IP, put the IP in. If you connect via host name, try the host name. For example, I connect to another Ubuntu server at work so I use smb://ServerName. At home here, I just go by IP, so I do smb://192.168.1.110.

See if that does the trick. :)

---

### Post by Jonners59 on 2010-07-04
In 9.10 and 10.4 I found it as standard.  But still check

I then use Places - Connect to Server

I then select "Windows share" from the server type list.  I then enter the name of the device/machine in 'Server:'  I.e. My Laptop....

Then connect.

this I found to be THE most reliable method of connecting

Once connected I crate Bookmarks for each folder, device, etc I use, though I still find the above the best to get started each session.

Other methods are:

Places - Network - Windows Network......

All the above are NOT 100% and I find they sometimes need several attempts to get them going even re-starts.

Another suggestion, is to change the Work Group you are in.  Not important but it is tidier.  To install use the Ubuntu Software Centre in Applications and either type in the search or go to System Tools and look for Configuration Editor and install it.  Then go in to System Tools - Configuration Editor - System - smb....  Then to the right of Name (workgroup) in value do a right click and select "Edit".  Enter your Workgroup name....  Assuming you use them.

Hope this helps.

---

### Post by Morbius1 on 2010-07-04
If you're trying to access a remote share you really don't have to have Samba installed. That's for creating shares for the remote user to access.
My guess is you've already installed it anyway so .....

Accessing the remote share should work out of the box as described above by jonners59 and Roasted.

If it doesn't you might want to post the output of the following command to see if it produces any useful error messages:
```
smbtree
```

---

