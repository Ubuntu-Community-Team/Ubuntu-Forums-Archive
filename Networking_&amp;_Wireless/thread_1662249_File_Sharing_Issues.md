---
title: "File Sharing Issues"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by rfb13 on 2011-01-07
My linux computer is running Ubuntu 10.10.  It is networked with a Vista machine.  The linux machine has Samba installed.  Still I am unable to share files or printers.  The linux machine can ping the Vista machine, but only using a terminal window.  It doesn't work using Network Tools.  The Vista machine can ping the linux machine but the linux machine doesn't show up on the Vista box when Network is clicked.  Both machines have internet access through the router.  Any help is appreciated.

---

### Post by PatchesTheCaveman on 2011-01-07
Try manually connecting to your Linux computer by name.

To do so, press WindowsKey+R and type two backslashes and the name of your Linux computer in the Run dialog that appears. Then click OK/press Enter.  

For instance, if your computer is named *cheesecake*, press WinKey+R and type this:
```
\\cheesecake
```
then press Enter.

Do your file shares appear that way?

---

### Post by rfb13 on 2011-01-08
> **PatchesTheCaveman said:**
> Try manually connecting to your Linux computer by name.

To do so, press WindowsKey+R and type two backslashes and the name of your Linux computer in the Run dialog that appears. Then click OK/press Enter.  

For instance, if your computer is named *cheesecake*, press WinKey+R and type this:
```
\\cheesecake
```
then press Enter.

Do your file shares appear that way?



When I connected as you suggested, a vista window pops up showing my linux Public folder.  That's good.  When I double click on the folder to view the contents another window pops up asking me for my User Name and Password.  I assume it wanted my linux info but when I entered it I got an error message saying "Login Unsuccessful".  I know my computer name is correct by looking it up using uname -a.  I know my password is correct because I'm able to long on to linux with it.  All characters are lower case, so Caps Lock is not an issue (it's off on both machines).  So, what user ID and password is Vista looking for?

---

### Post by rfb13 on 2011-01-08
Well, things have changed somewhat.  I was finally able to get the linux box to see the public folder on the Vista machine.  I had to go to Connect to Server and there use the Windows Share option.  When it asked me for the Server:  I used the name of the Vista computer - that didn't work.  Next I looked up the IP address of the Vista machine and used that when it asked for Server.  That worked.  I was also able to share the printer hooked up to the Vista box.  

Now all that remains is to access the Public folder on the linux machine from the Vista machine.  When I try it still asks for a User Name and PW.  I tried the linux User name and PW  -  nada.  I have no passwords for the Vista machine, so now what?  What is Vista looking for?

---

### Post by PatchesTheCaveman on 2011-01-09
Samba uses a different password store for its usernames and passwords than the main Ubuntu one, because Windows uses a completely different hashing/encryption algorithm for their passwords.  To set your password for file sharing, go to Applications > Accessories > Terminal and type the following command and press Enter:
```
sudo smbpasswd *username*
```
Replace *username* with your actual username.  You will first be prompted for your normal Ubuntu password.  Type that in and press Enter.  You will then be prompted for the password you want to use for file sharing.  It can be the same as your normal password if you like.  Type that in and press Enter.  You will be asked to repeat it.

Once you have done that, try accessing the Linux machine from the Windows one again, using the password you just created (if different from your normal one).

---

### Post by rfb13 on 2011-01-09
PatchesTheCaveman  -  That did the trick.  Thanks for all your help.  It still appears that I have to manually connect from the linux box to the Vista machine every time I boot up, but that is a minor issue compared to not being able to connect at all.  Again, your advise has been right on the mark and much appreciated.

---

