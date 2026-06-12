---
title: "Remote Desktop (for work)"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by StartedTheFire on 2010-01-07
I recently got ubuntu on my desktop computer. Its hard drive had crashed so I had it repaired, and I didn't want to have to renew my antivirus program, whatever it was I had, and I really didn't want to let my mom pay for it. So I got ubuntu and it's already infinitely less annoying and more streamlined, although I still don't know what I'm doing. My mom is totally against it and thinks it's weird and stupid that something could be better than windows. Because windows is normal and everyone has it.

Anyway, she needs to connect to her remote desktop at work. She says that with the windows client all she had to do was put in the IP address and absolutely no more information, and then it would connect and she would log in as she would if she was using her work computer. 

However, when we try the equivalent ubuntu program, it asks for a username, password, domain name, et cetera. Nobody ever told her what to put in these fields apparently, but I find it really weird that all that would be required to connect to a server is the IP address, even if it is ultimately password protected. 

So how do I do this? 

Please help I don't want to have to go back to windows over this....

---

### Post by DGortze380 on 2010-01-07
Open the terminal server client

Enter just the IP and hit connect.

She should be prompted for her Username and Password (probably the same one she uses when she's actually at work).

---

### Post by gradinaruvasile on 2010-01-07
Just the IP is suffice. The rest is required only in specific scenarios.

Also, there is a Remote Desktop client that is far better, has more features and most of all, faster than the default client included in Ubuntu and is more like the Windows client (it has that floating toolbar too). Also, it supports VNC/SSH too.

It is called Remmina:

[https://launchpad.net/~llyzs/+archive/ppa](https://launchpad.net/~llyzs/+archive/ppa)

Read the install instructions on the page.

---

### Post by StartedTheFire on 2010-01-07
Well whenever I do that I instantly get an error message that just says "an error has occured." 

Also, where is there even a download link on that site?

---

### Post by diablo75 on 2010-01-07
Chances are that, since your mom is a die hard Windows user, the remote desktop service running on her work computer uses the Windows Remote Desktop Protocol (RDP) instead of VNC.  I'm not certain, but I think when you open Terminal Server Client, it will let you specify the intended protocol including RDP... but I might be wrong.

Edit:  If Terminal Server Client doesn't provide the option for RDP, try installing the rdesktop package.  You can click System>Administration>Synaptic Package Manager and search for "rdesktop", then check it (Mark for Installation).  Then click the apply button at the top.  I don't know if this program adds a shortcut to your Applications menu anywhere, but if you can't find one, you can run the program from a terminal and it should prompt you for any information it needs to establish a connection with the remote PC.

---

### Post by mocoloco on 2010-01-08
I've found [gnome-rdp]("apt:gnome-rdp") to be a great client.

---

### Post by gradinaruvasile on 2010-01-08
> **StartedTheFire said:**
> Well whenever I do that I instantly get an error message that just says "an error has occured." 

Also, where is there even a download link on that site?

And you can download individual files and install them but adding the whole repository is better because the program will be automatically updated.
Here are the basics:

Open  a terminal, type:

sudo gedit /etc/apt/sources.list

Add to the end of the file (this adds that repository to your list):

deb [http://ppa.launchpad.net/llyzs/ppa/ubuntu](http://ppa.launchpad.net/llyzs/ppa/ubuntu) karmic main 

Save, quit. Then type 2 consecutive commands (for registering the repositories gpg key):

gpg --keyserver keyserver.ubuntu.com --recv 5A0FA8F1
gpg --export --armor 5A0FA8F1 | sudo apt-key add -

And install the program:

sudo apt-get update && sudo apt-get install remmina

You can launch it from the internet menu.

---

