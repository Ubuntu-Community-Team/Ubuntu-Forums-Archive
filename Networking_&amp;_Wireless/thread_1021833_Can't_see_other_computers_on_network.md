---
title: "Can't see other computers on network"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by Yellowbelly on 2008-12-26
I got a new laptop so there's a bunch of stuff I need to transfer on to it. Of course it has vista on it like nearly every other computer on the network...except 1 mac that's my brothers. I've tried messing with shared folders but neither windows nor linux can detect the other and I really have no idea where to start.

The laptop is one of those tiny asus n10ja1 so it doesn't have an optical drive. I'm thinking about putting linux on it anyway, so should I do this via wubi? Would that be the best way? And then the computers could see each other right?

---

### Post by Zackie on 2008-12-26
I'm in the same boat... I have two XP Pro computers networked together and i'm on my Linux Box 8.10... How would i be able to see the others on the network? In my network i just see windows network then double click on that and i don't see other computers... Any Ideas on what i would need to do on either computers or my own?


Thanks,


Zackie...:guitar:

---

### Post by namdung on 2008-12-26
Are the PCs able to ping each other?

---

### Post by Zackie on 2008-12-26
The Windows XP ones are but i'm not able to see them on my Linux box.

---

### Post by Yellowbelly on 2008-12-26
> **namdung said:**
> Are the PCs able to ping each other?

um, i dunno. I don't know where to begin with this.

---

### Post by caleb12 on 2008-12-26
make sure samba and winbind are installed and started. The easiest way to find out on a linux box is by opening a terminal (alt+F2 and type: gnome-terminal or konsole) 

Then type:

sudo /etc/init.d/samba start 
sudo /etc/init.d/winbind start

If it says file doesn't exist, then it needs to be installed.. so...

sudo apt-get install samba
sudo apt-get install winbind 

Then issue the first two commands to get start the services. They should start automatically on boot as well. 

Then see about clicking on network in Nautilus, you may also want to use the actual IP of the computer as well to test. 

As far as Macs go, big pain in the ***... I have two at my house here (my girl likes macs) and I have the utter most problems locating them with either afp or samba (windows or apple file sharing). I generally end up starting the FTP server on the Mac machine and use that to transfer files... or thumb drives work great too... lol...

---

### Post by DGortze380 on 2008-12-26
> **Zackie said:**
> The Windows XP ones are but i'm not able to see them on my Linux box.

This is a problem...

First to answer the original question.. you'll need to configure Samba to share between windows and linux. Google for a howto, it's not that hard.

Now... You sai dyou couldn't 'see' the windows machines from ubuntu, but we asked if you could PING the machine... 

go to a windows machine. Click Start -> Run. Type cmd and press enter.

Type: ipconfig /all
press enter
Note your current IP address.

Go to the linux machine.
Open a terminal from the accessories menu.
Use the following command [replace anything in brackets] and post the output:
ping [IP Address of Windows Box]

---

### Post by albinootje on 2008-12-26
> **Yellowbelly said:**
> um, i dunno. I don't know where to begin with this.

1) Find out what the ip-addresses are on the other machines
  in XP : ipconfig (in a DOS-box :)
  in MacOSX : ifconfig (in a terminal [-> Applications -> Utilities]

2) start ping from your Linux box in a terminal :
```

ping -c3 192.168.1.101

```

---

### Post by jonandrews on 2008-12-27
Have a look at my step-by step networking guides. They are written for people more familiar with Windows who want to network with Ubuntu.

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by Yellowbelly on 2008-12-27
Ok, here's the weird thing. It seems like I already have most things working correctly. Once I shared some folders, windows did pick it up. No surprises here. The problem is that I can't access it from windows...or even ubuntu. I try to open up the shared folders and it asks for the username and password, of course. I put it in and . . . wrong user name and password! I am so confused. So, I try the root and the root password and I GOT IN! Unfortunately the next folder I clicked on asked for another password so I gave it the same root pw... and no go. I tried my ubuntu login pw because I changed some permissions on the drive recently and still no go. I went back to try it again and now root won't work or it says something like check the permissions or log out because only 1 person can get in this thing. (I guess I'm trying to access it from bother vista and ubuntu comps to see if it works). The thing is though, I tried it in ubuntu and NOTHING works. Not even root.

edit: I try again. What should be the right password gets that multiple users can't be connected message. The same when I throw random crappy usernames and passwords that shouldn't be close to working. Also, when I put in root and its password, somehow it says that it's the wrong username in password when THAT should be the one to work.

---

### Post by albinootje on 2008-12-27
> **Yellowbelly said:**
> Ok, here's the weird thing. It seems like I already have most things working correctly. Once I shared some folders, windows did pick it up. No surprises here. The problem is that I can't access it from windows...or even ubuntu. I try to open up the shared folders and it asks for the username and password, of course. I put it in and . . . wrong user name and password! I am so confused. So, I try the root and the root password and I GOT IN! Unfortunately the next folder I clicked on asked for another password so I gave it the same root pw... and no go. I tried my ubuntu login pw because I changed some permissions on the drive recently and still no go. I went back to try it again and now root won't work or it says something like check the permissions or log out because only 1 person can get in this thing. (I guess I'm trying to access it from bother vista and ubuntu comps to see if it works). The thing is though, I tried it in ubuntu and NOTHING works. Not even root.

edit: I try again. What should be the right password gets that multiple users can't be connected message. The same when I throw random crappy usernames and passwords that shouldn't be close to working. Also, when I put in root and its password, somehow it says that it's the wrong username in password when THAT should be the one to work.

What do you mean from Ubuntu to Ubuntu ?
From another Ubuntu machine to your Ubuntu machine, or on your Ubuntu machine to localhost ?

Are the machines all in the same WORKGROUP ?
Did you test with the "enable guest access" in the Ubuntu "Sharing Options" already ?
Are you using firewall software on those machines, and if so, did you open ports 135/137 and 445 to both ways ?

Can you install "smbclient" on the Ubuntu machine(s) and post the output of :
```

dpkg -l|grep samba
dpkg -l|grep nautilus-share
lsb_release -a
testparm

```
--> hit <enter>
```

smbclient -L localhost

```
--> no password needed, hit <enter>

---

