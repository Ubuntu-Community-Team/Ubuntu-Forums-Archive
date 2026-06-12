---
title: "File transfer between computers using crossover?"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by Slacker20 on 2009-03-05
I'm trying to move a bunch of files from my laptop (Ubuntu 8.10) to my desktop (Ubuntu 8.04) so I can reformat my laptop hard drive.  After following [this]("http://users.bigpond.net.au/hermanzone/p11.htm") and getting everything set up, I can not for the life of me get this to work.  Both computers can ping each other, and both are using static IPs that I assigned.  When I go to Places/Connect to Server from my desktop, I use the following settings:

Service Type: SSH
Server: 192.168.1.107 (my laptop IP)
Port number: 22 
Folder: /home
User Name: brandon
Bookmark Name: filetransfer

Despite successfully being able to ping to my laptop, once I click Connect it says "Can't display location 'sftp://brandon@192.168.1.107/home' Times out when logging in"

What am I doing wrong?

Any help is greatly appreciated,
~Slacker

---

### Post by strife242 on 2009-03-05
My initial guess is that no SSH deamon is installed / running.

Try:
sudo /etc/init.d/sshd start

Or:
sudo apt-get install openssh-server

---

### Post by Slacker20 on 2009-03-05
I'm not sure what the first command is, but I have all installed software

---

### Post by Slacker20 on 2009-03-06
BUMP

These are the packages I already have installed:
- sshfs
- ssh
- openssh-server
- openssh-client
- ssh-askpass-gnome

---

### Post by Iowan on 2009-03-06
[Here]("http://ubuntuforums.org/showthread.php?t=927939") is a similar thread. Unfortunately, it doesn't seem to describe procedure.

Have you tried it from a terminal?
Another [How-To]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/") , and a [help page]("https://help.ubuntu.com/community/SSHFS")

---

### Post by Slacker20 on 2009-03-06
I managed to find enough bits and pieces from different forums and sites that I got it to work last night.

I was trying to move files from my laptop onto my desktop, so on my laptop I ran this command in Terminal:
```
sudo /etc/init.d/ssh start
```

Then on the desktop I ran this command in Terminal:
```
ssh 192.168.1.107
``` (that is the IP of my laptop)

It then asked for the password for my laptop and connected.  From there I had to be sure all the files I wanted to access on my laptop had full sharing privileges (Share folder and allow guest access for people without a user account), and everything worked pretty easily after that.

Hope this helps someone else.

---

### Post by Krelis on 2009-03-30
Okay, honestly I believe this can be done a lot easier. I just moved a bunch of files (20gb+) from one laptop to the other using a _straight_ network cable with nothing in between. I don't know if this is the proper way to do it, but it worked perfectly and even I could do it.

- Set up the shared folder (with right-click->sharing options), install the sharing services if necessary.
- Edit permissions (under properties) if necessary.
- Connect both ends of the (straight)cable to the NIC's.
- Edit the wired network connection under Preferences->Network connections.
- In the "IPv4" settings tab, select "Link-Local Only" as method. Do this on both computers.
- The connection will establish automagically.
- The share can be found in the "Network" location on the other computer.

now, i believe this is all there is to it, but maybe you need to add a samba user using:
```
sudo smbpasswd -a "username"
```

This seemed to work for me with Linux Mint 6 Felicia on one pc (4 year old Compaq Presario v4000 series) and Ubuntu 9.04 Jaunty beta on the other (new Toshiba A350), tried it out as i had no crossover cable or adapter, and wireless was too slow. Also, this gave me the opportunity to make my first post a useful contribution :D, as i didn't find something similar as a solution here yet. I hope this will be useful to some people.

regards,
-Krelis

---

