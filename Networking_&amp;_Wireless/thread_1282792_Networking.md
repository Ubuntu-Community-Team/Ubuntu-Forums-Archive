---
title: "Networking??"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by Stormspace on 2009-10-04
I've had an Ubuntu server for a couple of years now and I've pretty much been happy with it aside from a nasty upgrade from 8 to 9 that failed. I use it for file sharing and such to Windows clients and it works well.

However I have been using an Ubuntu desktop computer for 6 months and haven't been able to reliably and easily network the two PC's. It seems to me to be a major flaw. Windows networking is light years ahead of Linux in this regard and it's pissing me off. :) Is there an app, or something to make networking between Ubuntu/Linux computers easier. Currently Ubuntu is a great internet only network  client, but networking is a disaster of command line and config file nastiness. 

Help!

---

### Post by Stormspace on 2009-10-13
No one? Nothing?

---

### Post by srt4play on 2009-10-13
Can you be more specific about what you are trying to accomplish? What service(s) are you trying to get working between your ubuntu server and client?

---

### Post by cgb on 2009-10-13
I believe we need more information about what you are trying to accomplish like srt4play said.  Are you just dealing with file sharing or is there more to this?  I deal with networking in my professional life and although I'm sure Ubuntu has it's flaws with networking I don't feel it is anywhere behind what windows provides.

---

### Post by Iowan on 2009-10-13
Linux networking seems pretty painless - it's file sharing that gets complicated... mostly because of the different ways to share.  Because Ubuntu doesn't force (or even default to) a particular sharing method, the user "gets" to choose - which means installing the server component of whatever method (s)he chooses.

---

### Post by Stormspace on 2009-10-14
Just basic file sharing. Don't particularly need shares with user permissions, but if I need to I can create users on the server to access those shares. Currently I have samba shares that work perfectly with Windows clients, it's just this linux client that is giving me fits. I'd prefer a solution that doesn't require editing the fstab file, which I know how to do. Basically I'd like seamless networking to all shares on the network, Windows or Linux and an app that allows me to do that. If both can't be accomplished then at least I'd like to use the Ubuntu server shares as an intermediary.

---

### Post by cgb on 2009-10-14
If your just trying to connect to an smb share on the linux client you could simply go to "Places" and then "Network" on your top bar and search for the networked computer.  Once you browse down and see the folder you would like to connect to you can create a bookmark to this folder if you would like for future ease.  To do this you can simply click on "bookmarks" and "add bookmark".

If you need to have a "mapped" drive as such then yes, fstab would be your best bet for getting that setup.  Below is the code that would need to be entered if this is the case in fstab.

```
//server/share	/some/folder	smbfs	user=someuser,password=somepassword
```

So, yes, if you are trying to create a mapped drive Ubuntu can be a bit more taunting then windows for an average user.

---

### Post by Charlie Tame on 2009-10-14
I can't confirm this but it seems that the version of Samba that comes with 9.04 has some "Issues".

What I have found is that some settings in the default /etc/samba/smb.conf do not "Stick".

Here is what I found works but please be very careful to keep a copy of the original.

Download and install GADMIN Samba using synaptic. First run it will ask if you want to replace smb.conf. Let it do this.


sudo gedit /etc/samba/smb.conf

and amend the workgroup / domain name to whatever you are using on the other machines. Some versions of Windows use "Workgroup", others "Mshome"

Just below that add a line "netbios name  =  (the computer name)

You many want to scan down and comment out the lines that share home directories etc and you probably want to share at least one directory on the machine - GADMIN Samba is not the most intuitive thing to use so for sharing options be prepared to spend a little time reading.

This method fixed all my problems on two 64 bit machines and one 32 bit, and the settings seem to stick. 

You MUST restart Samba for changes to take effect, I suggest you create a launcher on the panel (Select option "In a terminal") and add this line and the one above to make it easier...

sudo /etc/init.d/samba restart

I am certainly not an expert so if anyone spots a serious problem with doing this please feel free to say it.

---

### Post by newb85 on 2009-10-18
If I'm going to install GADMIN samba, I should probably uninstall the samba I already installed, right?  (I'm guessing I'll have conflicts if I don't.)

Also, if I add a mapped drive in the fstab, will I receive error messages whenever that computer is not on the network?  (I'm guessing this won't be an issue, since external media mapped to fstab don't give error messages when not connected.  I just want to make sure.)

---

### Post by newb85 on 2009-10-19
Okay, so I was unable to browse any deeper than "WORKGROUP" until I disabled ufw on the host computer.  I read somewhere that I need to unblock certain ports.  Could someone explain a little about this?  (I really don't know what ports are.)  Is it a good idea to use the default ports, or is it more secure to use different ones?

---

### Post by jtniehof on 2009-10-19
> **newb85 said:**
> Okay, so I was unable to browse any deeper than "WORKGROUP" until I disabled ufw on the host computer.  I read somewhere that I need to unblock certain ports.
Here are my ufw rules to allow samba:
137/udp ALLOW   192.168.1.0/24
138/udp ALLOW   192.168.1.0/24
139/tcp ALLOW   192.168.1.0/24
445/tcp ALLOW   192.168.1.0/24

Note that my (internal) network is 192.168.1.x and the samba shares are restricted to that (i.e. nobody from the Internet has access.) You'd have to change the 192.168.1.0/24 based on your network setup.

---

