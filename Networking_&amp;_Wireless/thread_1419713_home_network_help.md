---
title: "home network help"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by Cabs21 on 2010-03-02
I am looking to set up a home network server on an old PC.  I want to be able to access files on the network hard drive in the PC, stream video or music from the "server", and use the computer as a regular desktop connected to TV as a monitor.  I tried setting up an FTP server and that worked for transferring files but failed to get a good connection for streaming or fast transfers.  Was less then 1MB a second.  I tried setting up a shared folder but ran into several permission errors between the host PC and the laptop that that connected to the shared folder.  I am open to ideas or suggestions I just dont know which way to go with this to get what I want out of it.  I know if can be done just not sure how to do it.  Any help would be great, Thanks in advance.

---

### Post by aromo on 2010-03-02
If you don't have confidential info in your "server" PC, create a share with full permissions to Everyone (assuming it's a Win PC).  Then use Nautilus (Ubuntu's default file browser) to access it.  You shouldn't run into permission problems if you granted full permissions to Everyone.

---

### Post by Cabs21 on 2010-03-02
forgot to mention this will be an ubuntu 9.10 32-bit install on the server PC.  I am not using any windows OSs at all.  Only issue would be with my fiance's MacBook Pro but if that does not work I can live with that.  I want it to work between Ubuntu machines.

---

### Post by pricetech on 2010-03-02
SSH ??  That would be my choice.  Just make sure it's installed on the server and client both, then connect using the "Connect to Server" applet under "Places".

---

### Post by Neezer on 2010-03-02
> **pricetech said:**
> SSH ??  That would be my choice.  Just make sure it's installed on the server and client both, then connect using the "Connect to Server" applet under "Places".

That is what I use. I have a 32 bit server with 9.10 on it. It doesn't connect directly to the tv, but plays my media files (pictures, movies, songs) through my ps3 using mediatomb.

SSH was an easy setup with the guides here.
I used this guide and it worked great for me.
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

On the windows side, I set up my fiance with a program called winscp to get ssh file transfers working on her xp laptop. it is actually a nice program. It allows you to use ssh protocol and security with a double paned window for drag and drop file transfers between windows and ubuntu.

Using the Places -> connect to server also is a snap to set up to use the ssh protocol for secure transfers. It makes it so secure file transfers are easy.

I have noticed that the transfer speed is a touch slower when using the GUI version of the ssh transfer as opposed to using scp.

As for your transfer rates, are both machines wired into the network? If so, what is the speed of the slowest network card in the mix? If they are wireless, you'll suffer. When I do wired transfers on my lan, I usually get about 10-12 MB/s When I use wireless, It is about 2.5 - 3.

Wireless speeds can be flaky at best, and down right terrible some times. I'm not sure what it is.

good luck. Hope I helped.


PS: if you do end up going the ssh route, make sure you do RSA key encryption, and not a password. if you use a password you are much more vulnerable to attacks.

---

### Post by Cabs21 on 2010-03-02
Thank you for all your suggestions.  It sounds like SSH is the way to go.  I am planing on using the "server" as a media center for my TV and the TV acting as a monitor for the computer, while at the same time allowing me to stream movies, music, and data to my laptops so I can upload data onto the "server" without a physical connection or by the use of thumb drives.  The server computer will be hard wired into the network in the final setup but for not I am testing the set-up on an old laptop.  Thanks again.

---

### Post by Neezer on 2010-03-02
> **Cabs21 said:**
> Thank you for all your suggestions.  It sounds like SSH is the way to go.  I am planing on using the "server" as a media center for my TV and the TV acting as a monitor for the computer, while at the same time allowing me to stream movies, music, and data to my laptops so I can upload data onto the "server" without a physical connection or by the use of thumb drives.  The server computer will be hard wired into the network in the final setup but for not I am testing the set-up on an old laptop.  Thanks again.

What do you mean by server? if you are just going to play movies on the computer and have them display on the tv (monitor), that isn't quite a server. Do you have something that will play the media files that are on the server? ps3, xbox, etc? If you do, you won't need to connect to the TV as a monitor, you can just have a headless server sitting somewhere with an ethernet cable plugged into it. 

good luck and let us know if you have any other problems. Remember that if you are going the ssh route, if you open it up to the world (port forwarding on your router) you really should be using key authentication as opposed to a password. the guide I linked above will walk you through setting it up.

---

### Post by Cabs21 on 2010-03-02
ok.  I want the PC to be use connected to the TV as a monitor to function as a regular computer so i dont need to connect my laptop to the TV anymore to watch movies from my laptop on my tv.  That is an easy set-up and I know what to do for that.  I will also be using a wireless mouse and Keyboard to make it easier to work with.  

The other thing I want this PC to do is share all of the media files and data on the PC can be accessed from my laptop.  Example,  I want to watch a movie from my portable HDD.  I connect it to the "server" PC and watch it on my TV from my couch.(very relaxing) Now I am in the other room and want to watch a show from the HDD on my laptop cause my fiance is watching something on TV.  I just connect to the server and stream the file straight to my laptop or if its small enough just copy it to my laptop HDD then delete it when I am done.

My plan is to have a local network where I share all of my media files on this network so anyone connected to it can use the them.

I have a xbox 360 that i can use but am not planning on it yet.

---

### Post by Neezer on 2010-03-02
Ok, then you can forget anything i said about mediatomb. You won't need it. You can stream video with vlc player. so if you store the video on the server you can use the connect to server feature with an ssh connection to browse the files on your server and just double click on it. vlc will open in right up on your laptop...

so you'll want vlc on both your server (to play movies on your tv) and on you laptop (to stream movies from the server to your laptop).

I assume you have a router at home...as long as you don't forward any ports on the router, your ssh port on the server won't be in jeopardy...I think. You should clarify that.

---

### Post by Cabs21 on 2010-03-02
> **Neezer said:**
> Ok, then you can forget anything i said about mediatomb. You won't need it. You can stream video with vlc player. so if you store the video on the server you can use the connect to server feature with an ssh connection to browse the files on your server and just double click on it. vlc will open in right up on your laptop...

so you'll want vlc on both your server (to play movies on your tv) and on you laptop (to stream movies from the server to your laptop).

I assume you have a router at home...as long as you don't forward any ports on the router, your ssh port on the server won't be in jeopardy...I think. You should clarify that.

Ok I also want to share files between computers other then just streaming.  I have VLC on any PC I use, I wouldn't use anything else.  Question with the VLC streaming, could I do this from anywhere or do I have to be in my home network.  I port forward only one port that is very high up for torrent sharing reasons.  Do you think this will be an issue? The port is higher then 60000.

---

### Post by Neezer on 2010-03-02
You'll have to open another port for the ssh. I would recommend not using the default port 22. Just configure your router to forward both ports. before you open up your computer to the internet on the new port make sure you have your ssh key up and running. you should be able to test this out by just doing it on your lan at first. then test out the port forwarding by opening up the port forward and try to access it from outside of your lan.

You should be able to stream with vlc from outside of your lan, but speed could be an issue. I did it once and it worked great, but another time i tried my connection wasn't fast enough for smooth playing.

---

### Post by Cabs21 on 2010-03-03
i dont know much about ssh.  Do you know any sites i could learn about it first before I start setting up port forwarding and ssh keys, so that i dont freak my computer out and it never wants to go on the internet again because of me.

---

### Post by Neezer on 2010-03-03
> **Cabs21 said:**
> i dont know much about ssh.  Do you know any sites i could learn about it first before I start setting up port forwarding and ssh keys, so that i dont freak my computer out and it never wants to go on the internet again because of me.

My advice is start small. Make sure you can connect on your LAN first with a password. then try with a key. if you cannot log in with the key at least you have acces to the machine so you can change it back to password, or change settings on it.

Then once you have that all set up, you can go to trying to connect to your server from outside of your LAN.

Here is a great guide that I used extensively to get going. Make sure you understand what you are going to do before you do it. And don't experiment with connection security if you don't have physical access to the ssh server. If you change security settings you have to restart the ssh daemon for the changes to take effect (this will boot you from your current ssh session). If you made a mistake in the configuration you won't be able to log back in until you can physically access the server and change the settings.

good luck. post here if you have any more questions, and feel free to PM if you want.

anyways, here is the guide that I used. Lots of good stuff in it 
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

