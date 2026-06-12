---
title: "folder sharing problems"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by jazzerit on 2010-05-19
Hello all.

In ubuntu, when I try to share a folder over lan using either the shares-admin command, or the nautilus sharing window, it will all complete, I can see the folder inside the Network section of the places menu on the other computer, yet, whatever I do, when it comes to the window asking for username, domain and password, it won't accept it, whatever I enter.

So, what I want is a walkthrough, telling me how to create a shared folder, how to configure the username, domain and password for nfs (I don't get the smb option, but I don't need to share with windows), and what to do on the client machine. In case it helps, both computers are connected to a BT Home Hub via a wired interface, and I am guessing the other machine is detected, as I can see the folder and vnc to the computer with computer-name.home, but just cannot access the folders. Looked all over the web. Somebody help! Using ubuntu 10.04.

---

### Post by jazzerit on 2010-05-19
I've decided that this is too much hassle. So, in my search around the internet for help, I found out about using ssh in nautilus. After I'd done apt-get install ssh on both machines, it worked beautifully. This means that now I can log in remotely and copy & paste files.:guitar:

In case anybody else has had trouble with this, follow these instructions

Preparations:
1. find the hostname of the server computer- you can do this by going into a terminal and typing "$HOSTNAME" (all caps, no quotes). Copy the output down for later use.
2. Get the username of the person within whose account the folder resides

Now, we are ready!
First, on the server computer, open the terminal and run the command "sudo apt-get install ssh". This just tells the computer to download the ssh package. Most people know that, though.

Then, open any folder in nautilus type this into the location bar (you can get that up by pressing ctrl+l) and type: "ssh://user@hostname/home/user", replacing the word user with the user whom you wish to access and hostname with the hostname we copied earlier. All this command does is access the specified user on the specified host, and open the folder at their home directory. Then, when the popup box comes up asking for the password, enter it and you should now be in their home folder. Also, it makes a link to their home directory on your desktop. To remove this, you can't just delete it- you have to right-click on it and select unmount. Hope this helps someone!

---

