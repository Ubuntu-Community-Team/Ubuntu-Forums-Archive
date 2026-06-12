---
title: "Home file server situation... please help"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by frotzed on 2011-07-31
I've set up a PC installed with Ubuntu 11.04 on my home network, given it the name "server" and given it a static IP of 192.168.1.200.  I've created a file in the home directory called "Public" and set it to be shared with everyone, basically a chmod 0777 situation.  

Now, how do I connect, or map out that folder from another ubuntu 11.04 machine?  

I know how to do it in Windows, just hit "run" and type in "\\server" and blamo, I can see everything that's shared on that machine.  I can't figure out how to do this with Ubuntu.  Please help.

---

### Post by e79 on 2011-07-31
You should be able to see your server by going to :
[B]
Places --> Network --> workgroup --> server --> share[/B]  (or something similar)

Another way would be to go to :

**Places --> 'Connect to Server'** and enter the required connexion information.

or in a 'path bar' (in Nautilus, go to  View --> Location)

**smb://server/share**

But prior to do it, you might want to install 'CIFS/smbfs' to avoid problems :

```
sudo apt-get install smbfs
```Hope this helps

---

### Post by drdos2006 on 2011-07-31
Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop and run the server as a virtual machine using Virtualbox.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb
###  	web site is here: http://sourceforge.net/projects/webadmin/files/webmin/1.550/webmin_1.550_all.deb
Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by frotzed on 2011-07-31
Still not working.

I when I open Network the only thing I see is "Windows Network." Then when I double click it I get an error, "Unable to mount location.  Failed to retrieve share list from server"

If I go to smb://server/public or smb://192.168.1.200 I get an error also, "Could not display "smb://server/". 

@drdos2006: I certainly appreciate the input, but that tutorial is quite a bit beyond what I need.  I'm not looking to set up a real server, just trying to let two Ubuntu computers share a folder.

I can't imagine this should be this difficult to accomplish.  I'm only looking to create a simple file sharing scenario.

Edit: I can ping my server in terminal, so I know my computer can "see" it.  But why can't it connect to the shared folder?

---

### Post by frotzed on 2011-07-31
Well, I resolved the issue... and learned quite a bit in the process.  I had about given up but it's not in me to let a machine win.  I took the advice of drdos2006 and installed WebMin [via this tutorial]("http://secretengineer.com/?p=788").

WebMin simplified the process _immensely_ and I'm now a huge fan.  Thanks for the help.

---

### Post by e79 on 2011-07-31
I'm glad you could solve your issue,

Cheers

---

