---
title: "How can I stream music from Ubuntu to my radio with uPnP?"
date: 2016-04-01
forum: Multimedia Software
---

### Post by warren3 on 2016-04-01
Hi.

I have bought a Pure One Flow radio.  I would like to stream AAC files from my Ubuntu home PC to my radio using uPnP.  What is the best way to do this?

Thanks.

---

### Post by SeijiSensei on 2016-04-01
I use minidlna.  It's a cinch to set up and works well to stream audio and video.

[https://help.ubuntu.com/community/MiniDLNA](https://help.ubuntu.com/community/MiniDLNA)

---

### Post by warren3 on 2016-04-02
I need a newbie guide to setting it up.

Can anyone recommend one?

---

### Post by SeijiSensei on 2016-04-02
I thought that guide was fairly clear myself, but here goes:

1) Install minidlna from the repositories either with the graphical software manager or from the command prompt with
```
sudo apt-get install minidlna
```

2) Open a terminal and edit minidlna.conf with the command "sudo nano /etc/minidlna.conf".  Follow the instructions in that file and add media_dir lines to point to where your music and video files are stored.  For instance, if you have your music in /home/warren/Music, you would add the line
```
media_dir=A,/home/warren/Music
```
The "A" indicates these are audio files. Save the configuration file by holding down the Ctrl key and typing X.  Answer yes when prompted.

3) Either reboot, or restart the minidlna server with the command "sudo service minidlna restart".  It will scan the directory and begin serving the files it finds.

---

### Post by warren3 on 2016-04-02
Hi.

Thanks for your help.

I tried that but it is not working.  Do I need to forward a port or something?  I'm using Ubuntu desktop not server.

Thanks.[[COLOR=#000000][URL="http://ubuntuforums.org/member.php?u=698195"][COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=698195")[/COLOR][/URL]

---

### Post by SeijiSensei on 2016-04-02
DLNA only works on the local network.  You cannot access a DLNA server from outside the network as far as I know.  So you shouldn't need to forward any ports.  Can you not see the server from your network?

Have an Android phone with wifi on the same network as the server?  Try installing the BubbleUPnP app from the Google Play store and see if that sees the server.  I use that with MXPlayer to stream videos to phones and tablets in my house.  My LG TV also has a DLNA client; it, too, can see the minidlna server.  If you have PS3 on the network, it should see the server as well. (I suspect that's also true for XBox 360, but we don't have one of those.)

It doesn't matter whether you use a server or a desktop version; my copy of minidlna is running on a Kubuntu 14.04 desktop.

Do you see any errors in /var/log/minidlna.log? Another test you can try is to run the command
```
telnet ip.addr.of.server 8200
```
on the server, or better yet on another Linux machine on your network.  Replace ip.addr.of.server with the server's IP address.  You should get a result like this:
```

$ telnet 192.168.100.39 8200
Trying 192.168.100.39...
Connected to 192.168.100.39.
Escape character is '^]'.

```
It will hang at that point.  Hold down Ctrl and type "]", then "quit" at the prompt to exit.  If it replies with "Connected" then the server is listening.

---

### Post by warren3 on 2016-04-02
Hi.

minidlna does not want to run now.  I am getting this in the log:

[2016/04/03 00:05:38] minidlna.c:463: warn: Unable to change pidfile /run/minidlna/minidlna.pid ownership: Operation not permitted

Thanks.

---

### Post by warren3 on 2016-04-03
Hi.

I got it sorted!  I followed a guide on You Tube yesterday that changed a lot of stuff in the config file.  So I changed it back to stock and only edited what you told me too and I can see the folder on my pure one flow radio.  I'm just listening to a bit of Parliament as we speak just to test it!

I have a few more questions about minidlna.  If I keep my music folder visible on my network it won't be a security issue will it (I don't run a firewall on Ubuntu I just use my router firewall)?   I take it minidlna doesn't automatically start again after a reboot?  What is the command line to start minidlna?  Can I have minidlna to run on boot?

Thanks.

---

### Post by SeijiSensei on 2016-04-03
When you installed minidlna Ubuntu set up the files required to start it automatically at boot.  (It does this for any server "daemon.")  You'll see an entry in /etc/rc2.d that is a symbolic link to /etc/init.d/minidlna.  The existence of that link puts minidlna in the queue of programs to start at boot.

I don't see much of a security issue since access is limited to the local network.  If someone can connect to your router and get an IP address from it, then it would be a security problem, but a much bigger problem than just whether they can see minidlna.

Glad you got it sorted out.  If you want to be a good neighbor, post a comment at YouTube saying that that video led you astray.

---

### Post by warren3 on 2016-04-03
Hi.

Thanks for clarification.  

I have one more question.  I have a second hard drive in my PC with all my data on it.  I have a big AAC folder with my entire music library in lossy format.  When I edit the conf file and point to this folder minidlna does not like it - it doesn't work.  

My 2nd hard drive is called Data.  I put in this comment:

media_dir=A,/media/warren/Data/AAC 512

Is this the correct path for the folder?

edit - saying that its 90GB the AAC 512 folder.  How long would it take to build the database?

---

### Post by SeijiSensei on 2016-04-03
What does the "512" mean?  Is the folder actually called "AAC 512"?  Embedded spaces in file and directory names are always problematic.  Rename it to AAC_512 or some other name without a space in it and try that.

It might work if you embed the name in quotation marks, but why bother?  Just get rid of the space.

I think building the database is more a function of the number of entries than the sizes of the files themselves.

---

### Post by warren3 on 2016-04-05
Hi.

I have looked around and it is a permissions issue.  It look a bit too long winded for me to sort out so I might leave it until I do a fresh install of 16.04 LTS.  I don't want to mess up my install at the moment by doing something silly :(

Thanks for your time helping me SeijiSensei!

:D :D

---

