---
title: "Sharing folders over wireless network"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by Rifester on 2011-06-18
I have Ubuntu and Xubuntu  11.04 installed.   I would like to be able to share files between two computers on my wireless network.   I am not sure what is the easiest way to do this.   I have read that Gigolo on XFCE makes this very easy but I can't find good documentation...  On the Ubuntu side I looked at personal file sharing  (in system settings) and when I open the setting it tells me I do not have the software installed (see screenshot).  I assume this is where I would set up the access between the two computers...  Am I wrong?   Am I making this more difficult then it really is?   Or is it more difficult then I think it should be?   Appreciate any advice or a link to good instructions, this is something that I have wanted to learn how to do for awhile...

Thanks!

---

### Post by nbound on 2011-06-18
> **Rifester said:**
> I have Ubuntu and Xubuntu  11.04 installed.   I would like to be able to share files between two computers on my wireless network.   I am not sure what is the easiest way to do this.   I have read that Gigolo on XFCE makes this very easy but I can't find good documentation...  On the Ubuntu side I looked at personal file sharing  (in system settings) and when I open the setting it tells me I do not have the software installed (see screenshot).  I assume this is where I would set up the access between the two computers...  Am I wrong?   Am I making this more difficult then it really is?   Or is it more difficult then I think it should be?   Appreciate any advice or a link to good instructions, this is something that I have wanted to learn how to do for awhile...

Thanks!

On the ubuntu side you'll need samba, though the exact package i dont recall, havent shared folders for a few releases now.

---

### Post by Morbius1 on 2011-06-18
Easiest way if you don't care about what the remote user can and cannot have access to:

To connect to the Xubuntu machine from Ubuntu:

_On Xubuntu:_
Install the ssh server:
```
sudo apt-get install openssh-server
```_On Ubuntu:_
Nautilus > File > Connect to Server:
Service type:    ssh
Server:              ip address of Xubuntu
User Name:    user name on Xubuntu
Select "Add Bookmark"

The first time you run you will get a nasty looking error msasage just select: "Log In Anyway"

To connect to the Ubuntu machine from Xubuntu:

_On Ubuntu:_
```
sudo apt-get install openssh-server
```_On Xubuntu:_
You should have Gigolo installed by default if not let us know.

Open Gigollo > Actions > Connect:

Service Type: SSH
Server:             ip address of the Ubuntu machine
User name:     user name on Ubuntu

You will get a mount icon within Gigolo. Right click that and select Bookmark.

---

### Post by Rifester on 2011-06-18
Thanks Morbius1!  From what I can figure, I only need to install openssh-server on one computer correct?  I assume it would act as the server for the network or do I need to install it on both machines?   Appreciate the help!  I have Xubuntu-Desktop installed on top of Unity/11.04 on both machines and will give it a go as soon as I know where to install openssh-server....

---

### Post by Rifester on 2011-06-18
O.K.   I am trying to log into my main computer from my netbook and it is asking me for a password.   Is this the login password for the user on the server/main computer (it won't work) or do I need to set up a password in openssh-server somehow?

---

### Post by Morbius1 on 2011-06-18
> **Rifester said:**
> Thanks Morbius1!  From what I can figure, I only need to install openssh-server on one computer correct?  I assume it would act as the server for the network or do I need to install it on both machines?   Appreciate the help!  I have Xubuntu-Desktop installed on top of Unity/11.04 on both machines and will give it a go as soon as I know where to install openssh-server....
You need to install it on each machine. Server in this context is a misnomer in that each machine will "serve" it's resources to the other. Each machine is both a server and a client to the other.

---

### Post by Morbius1 on 2011-06-18
> **Rifester said:**
> O.K. I am trying to log into my main computer from my netbook and it is asking me for a password. Is this the login password for the user on the server/main computer (it won't work) or do I need to set up a password in openssh-server somehow?
You are logging into the remote machine as the user on that machine. So the username is the one on the server - the password is the one that user uses to login.

---

### Post by Rifester on 2011-06-18
Morbius1, Thank you so much!   I got it working and this will be a great time saver for me!   I really appreciate the help.   I am trying to figure out how to print a document to the computer hooked up to the printer.   I am trying to add a printer to the netbook, selected network printer, entered IP address on the computer where I want to print to but it tells me no printer is found (even though it is there and on).   Any ideas?

---

### Post by Morbius1 on 2011-06-18
On the machine with the printer open up the "Printing" in the menu and right click  the printer > properties > policies > make sure "Shared" is checked.

In the same utility check on Server > Settings > make sure the following is checked: Publish shared printers connected to this system

Now see if the other machine can access it by ip address.

---

### Post by Rifester on 2011-06-18
I was working in the right area...  All boxes are check but I don't see the server settings.   Screenshot attached...

---

### Post by Morbius1 on 2011-06-18
Click "Cancel" and it will come back to "Printing:localhost". then select "Server"

---

### Post by Rifester on 2011-06-18
It is all working, I couldn't find the server setting because of the flipping global menu in Unity.   I thought I was going mad for a minute or two.   Thanks again for all of your help.   I wish I could buy you a cup of tea, or a mug of beer, but I offer my sincere thanks.   I learned a great deal through this process!  :)

Rifester

---

### Post by Morbius1 on 2011-06-18
Well, you certainly don't have to worry about the magical mystery global menu in Xubuntu ;)

---

