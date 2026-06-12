---
title: "finding other computer contents over network"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by watto_one on 2010-06-03
Hi I'm am trying to setup file sharing over our home network. When I go to Personal File Sharing preferences The message "[COLOR="Red"]This feature cannot be enabled because the required packages are not installed on your system.[/COLOR] I cannot find what packages are required. Please help.

Thanks

---

### Post by theozzlives on 2010-06-03
I couldn't figure that out either. I just use SAMBA.

---

### Post by watto_one on 2010-06-03
I have samba loaded. Is it used in a different way to the other

---

### Post by ajgreeny on 2010-06-03
You can also do it with ssh if all the computers are running ubuntu.

Install openssh-server and openssh-client on all machines.

On each machine right click on the network icon and choose connection information.  Note down the ipaddress of each machine.
Then in your menu, go places > connect to server.
In the top box choose ssh
In the next box type username@ipaddress_of_other_computer.

Put a tick(check) in the add bookmark box.

Choose a name for the other computer.

Click connect.

Type the password of the other machine.

Check the remember password forever box, or not as you prefer.

Repeat process on the other machine.

You will now have a bookmark in your places menu, on each machine that will give you full access to the complete filesystem of the other computer.

---

