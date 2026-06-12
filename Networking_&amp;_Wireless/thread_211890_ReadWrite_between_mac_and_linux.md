---
title: "Read/Write between mac and linux"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by Majdaa on 2006-07-09
Hi, I recently purchased a 20"imac and i have it setup right to the left of my ubuntu box.

I have my ubuntu box setup as a public web server, and basically, i want to be able to edit my sites (which preside on ubuntu) on my mac.

Here's what i've done and what i have accomplished (Note that i don't know what i'm doing for the most part)

1) i installed smbfs (or something like that) and samba from synaptic.
2) i went to System>Administration>Shared Folders, then i clicked on Add, then i chose a path for it, then i chose SMB from "Share With", then i put "www" for the name, then i enabled "Allow browsing folder" then in "General Windows Sharing Settings" i chose "Do not user WINS server"
3)then on my mac, i went to System Preferences>Sharing>then i checked Personal File Sharing and Windows Sharing. I had firewall disabled too....


Now when i go to test it out and i click on Finder>Network>Mshome>Majd-Ubuntu>Connect, i am confronted with a popup that lists the shared folders and has the buttons authenticate and OK. when i press ok, i have to enter a username and password. So i put in the username and password to the linux account who is the owner of the shared folder.

After doing all that, i get an error message that says "The alias "Majd-Ubuntu" could not be opened, because the original item cannot be found".




I'd appreciate any help...

---

### Post by simonn on 2006-07-09
Why not use ssh?

---

### Post by gruepig on 2006-07-09
Not sure if this is the problem you are having, but the username and password are the samba username and password, not your ubuntu login username and password.  If you didn't set a samba password, you can do so with 'smbpasswd -a <username>' (substituting in a username).

Or, as already suggested, use ssh.

---

### Post by Majdaa on 2006-07-09
first of all, thanks gruepig, that fixed it.

on a second note, well, to be honest, i'm not sure exactly what ssh is or what it does. From what i've read, it is a secure way to access a computer remotely. But that's not _exactly_ what i need, i just need a quick way to edit files on another computer on my lan, i didn't use ftp because i didn't want to upload/download all the time, i just want to save and refresh.

can ssh do that? if so, is there a resource you can point me to?

---

