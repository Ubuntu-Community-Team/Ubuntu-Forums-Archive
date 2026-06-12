---
title: "Cannot Browse Win 7 Share"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by fleamour on 2010-02-18
Hi

I could not get XP & latest Karmic Xubuntu to network.  But now I can browse Xubuntu share/s from Win 7 but not vice versa (I cannot browse Windows 7 shares from Xubuntu laptop.)  How would I accomplish this?

Thanks.

---

### Post by johnson.d on 2010-02-19
If you have live sign in assistant installed in your windows 7 installation, you can probably try uninstalling it and try again. You can also check the firewall settings in Windows 7.

Please post the method of connecting to windows 7 machine, like browsing through the network computers or mounting it through the command line.

---

### Post by fleamour on 2010-02-19
I am talking really basic here, like where do I start browsing my Windows network from within Xubuntu.

I've been going to System >Remote Filesystems (Gigolo) >Choose a bookmark to connect to >Service type >Windows Share & this is where I get stuck.

What do I enter in Server/Share fields?

I've now added my PCMCIA MAC code to Comodo firewall permissions, so should be allowed through.

---

### Post by lost_soul on 2010-02-19
In windows 7, you have to be in "Home" for other computers to be able to see u.
One more thing, try entering the Window share via SMB and the computer's IP address not its hostname, maybe u have a DNS issue here.

---

### Post by johnson.d on 2010-02-23
You have to enter the hostname or the ip-address of the Windows 7 machine in the server field. At the Share field you have to enter the share name of the folder that has been shared.

---

### Post by fleamour on 2010-07-14
Hmmmm, been a while since I had a bash at this.

I have disabled password protected sharing on 7 machine & have tried connecting via Gigilo with these settings:

Service type:  Windows Share
Server: ASRock (have tried lower case/sentence case/other combo's)
Share:  Users/fleamour/Music

Then connect & it asks for password & keeps asking for password, even though I am entering the correct HomeGroup password.

I have even tried ipconfig /all on 7 machine entering the IPv4 address in server field.

No joy!

What gives?!?  Maybe Redmond HATE linux?

---

### Post by fleamour on 2010-07-14
> **lost_soul said:**
> In windows 7, you have to be in "Home" for other computers to be able to see u.

Can you explain?

---

### Post by dmizer on 2010-07-14
Please see the 6th link in my sig. Including the Win 7 specific information.

---

### Post by cavalier911 on 2010-07-14
Group Everyone does not require username and password
Right Click the drive or folder you want to share in Windows Explorer
Choose properties,Security tab,Group or Usernames,Add button,type Everyone
in the Enter the object names to select box,click OK button,
With Everyone highlighted,click the checkbox by the permissions you desire in the Permissions for Everyone box,click apply button,click ok,Ok to close drive/folder name properties of your share.

---

### Post by fleamour on 2010-07-15
@dmizer

"Then, go to 'Change adapter settings', right click on your connection and select 'properties'."

Not seeing this option anywhere?

---

### Post by dmizer on 2010-07-15
> **fleamour said:**
> @dmizer

"Then, go to 'Change adapter settings', right click on your connection and select 'properties'."

Not seeing this option anywhere?

It is on the far left side of the Network and Sharing window second item down on the list.

Edit, added screenshot

---

### Post by fleamour on 2010-07-15
Ah thanks, those options are in order.

---

### Post by dmizer on 2010-07-15
> **fleamour said:**
> Ah thanks, those options are in order.

Good, now what did Windows show for the pathname?

---

### Post by fleamour on 2010-07-15
Am I being thick?  Where is the shared folder?  Anyways, I shared music folder located in music Library, path:

\\ASROCK\Music

---

### Post by dmizer on 2010-07-15
> **fleamour said:**
> Am I being thick?  Where is the shared folder?  Anyways, I shared music folder located in music Library, path:

\\ASROCK\Music

Good. Now, in Ubuntu, go to: Places > connect to Server
Change the "Service type" to "Windows share"
In the "Server" field, type: ASROCK
In the "Share" field, type: Music
In the "User Name" field, enter your WINDOWS username.
Put a checkmark next to "Add Bookmark" if you want the share to appear in Nautilus when you open it up.

Then click "Connect". It will ask you for your password. Type your Windows user's password. If there is no password for your Windows computer, then leave it blank.

---

### Post by fleamour on 2010-07-15
Gigolo still keeps repeatedly asking for password but I do not have one on Windows account, maybe if I add one it'll work?

I have actioned all your tweaks with "Problem 3 - Jaunty/Karmic" breaking my networking, I am using development Maverick release.

Also, about adding a Win account the same name & password as my linux account, both the Windows admin & Xubuntu admin accounts are user: fleamour, but by adding the same password it still fails to connect.

---

### Post by dmizer on 2010-07-15
Are you absolutely positive you have no firewall in place on the Windows or Xubuntu machines?

---

### Post by fleamour on 2010-07-17
I have Windows 7 Ultimate running Comodo Internet Security, but I disabled before trying to connect.  Xubuntu Maverick Meerkat reports Chain INPUT (policy ACCEPT) via "sudo iptables -L".

---

### Post by dmizer on 2010-07-17
Open up gconf-editor via terminal
```
gconf-editor
```
Go to: system -> smb
Edit the work group so that the workgroup name matches the work group your Windows machine is listed on. Reboot, and test again.

---

### Post by fleamour on 2010-07-18
I tried editing smb key in gconf but it did not stick on reboot?

---

### Post by fleamour on 2010-07-18
Ah, I just edited value, how do I edit name?

---

### Post by fleamour on 2010-07-21
I cannot seem to edit existing greyed out workgroup key but have created a new key & set as default.  However a warning appears that the key has no schema with Key name/owner & Short/Long description fields blank.

---

### Post by fleamour on 2010-07-29
@ dmizer, my most humble apologies!  

Nothing in your guide was gonna work so long as I had Windows Live Sign-in Assistant installed.  I assumed I did not have this installed as default on my 7 tower...

Anyway, working through your steps soon had me up & running.

Thanks.

---

### Post by fleamour on 2010-07-29
Right, now get this I can see share within Gigolo but double clicking does not open selected folder to browse share?

---

### Post by Morbius1 on 2010-07-29
Hope nobody minds if I jump in for a second. I noticed you are using Xubuntu. For Gigolo to work correctly you need to have the following package installed:
```
gvfs-fuse
```and make sure that this option in gigolo is set:

Launch gigolo then go to Edit > Preferences > General Tab > 

File Manager: gvfs-open

---

### Post by fleamour on 2010-07-30
I can now access share through gvfs but folder is blank.  Usually all share permissions are inherited from parent folder, at least that is the way it works within Windows, no?

---

### Post by fleamour on 2010-07-30
OK.  Seems that dumping all my music into the Public Folder enables me to share my music collection.  Not sure where the public folder came from or why I cannot share other folders, but it's working.

---

