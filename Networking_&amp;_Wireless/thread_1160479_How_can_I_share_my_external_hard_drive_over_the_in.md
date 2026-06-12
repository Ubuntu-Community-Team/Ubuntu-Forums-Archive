---
title: "How can I share my external hard drive over the internet?"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by ninjapirate89 on 2009-05-15
I'm going to visit family in another state in a few days and I'm wondering if there is a way I can share my external hard drive over the internet so I can access it's files from there. If I can't get this set up soon I'll have to just bring my external with me and I'd prefer to just leave it. Can this be done?

BTW - I already have this drive shared on my home network. (Don't know if this is important information or not.)

---

### Post by Peter09 on 2009-05-15
Install opennssh-server on you home machine. If you have a router you will need to forward port number 22 to your home machine. 

Make sure you have a strong password and I advise installing denyhosts as well.

You can then connect from any machine using the ssh protocol

ssh -X<username>@<machine> <command>

---

### Post by ninjapirate89 on 2009-05-15
> **Peter09 said:**
> Install opennssh-server on you home machine. If you have a router you will need to forward port number 22 to your home machine. 

Make sure you have a strong password and I advise installing denyhosts as well.

You can then connect from any machine using the ssh protocol

ssh -X<username>@<machine> <command>

Thanks for the reply. I'm installing openssh-server right now. What does denyhosts do?

---

### Post by Peter09 on 2009-05-15
It stops brute force cracking of your password. Basically if anyone attempts to log in (and fails) more than 5? times without success it bans them outright. You will need this as you will get people trying to get into your machine. A strong password and deny hosts will keep them out.

There are other solutions, such as public/private keys, initially get it going simply, and then develop on from there if you want.

If your remote machine runs Ubuntu you will be able to connect from the Places->Connect to Server menu as well.

---

### Post by ninjapirate89 on 2009-05-15
Thanks. Ok I'm looking at my router's firewall preferences and it looks something like this -

To Allow Users Through the Firewall to Hosted Applications...
1. Select a computer. 
Here it has a dropdown box listing all the devices that connect through my router. I am assuming I select the host computer here (my desktop)
2. Edit firewall settings for this computer:
Here it has two radio buttons. One says Maximum protection and the other says allow individual applications and it has a dropdown box of common applications. It has an entry for SSH Server. Am I right in thinking that I want to add this to the allowed section?

---

### Post by ninjapirate89 on 2009-05-15
Where did you go?

---

### Post by Peter09 on 2009-05-15
Hi,
you need to find where your router allows a protocol, in this case ssh, to be forwarded to an IP address. I do not know the layout of your router so cannot help.

Also, you can test your installation by doing on your home computer....

```
ssh <username>@localhost xterm
```


this should give you an xterminal

If you have more than one machine on your network you can test with

```
ssh <username>@<homemachine> xterm

```

---

### Post by ninjapirate89 on 2009-05-15
Ok here is everything I have done so far:
1. Installed openssh-server and denyhosts on my desktop.
2. Changed my router settings to allow the application SSH Server on port #22. It also lists a public IP address.

I haven't (as far as I know) set a password. Also is there anything I need to install on my laptop?

---

### Post by Peter09 on 2009-05-15
Not sure what a public ip address is in this context. You need to forward to the IP address of your home machine, which should be a static one. If your laptop is running Ubuntu the you should be able to link to it through your internal network without using the router. So initially try in a terminal on your laptop

```
ssh <username>@<homecomputer> xterm
```

---

### Post by ninjapirate89 on 2009-05-15
I typed this in a terminal:
```

ssh ninjapirate@ninjapirate-desktop xterm

```
And this is what it showed:
```

ninjapirate@ninjapirate-laptop:~$ ssh ninjapirate@ninjapirate-desktop xterm
The authenticity of host 'ninjapirate-desktop (192.168.1.68)' can't be established.
RSA key fingerprint is 01:25:15:b0:27:85:30:33:4c:dc:91:9b:24:da:a5:43.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added 'ninjapirate-desktop,192.168.1.68' (RSA) to the list of known hosts.
ninjapirate@ninjapirate-desktop's password: 
xterm Xt error: Can't open display: 
xterm:  DISPLAY is not set


```

Edit -> I wasn't sure what the password would be so I just tried the one I type in for sudo.

---

### Post by Peter09 on 2009-05-15
You forgot the -X

```
ssh -X <username>@<computer> xterm
```

Edit : just realised I forgot the -X in previous posts - apologies

---

### Post by ninjapirate89 on 2009-05-15
I must be close because I tried again with a different password and it just told me flat out that I was denied.

---

### Post by ninjapirate89 on 2009-05-15
> **Peter09 said:**
> You forgot the -X

```
ssh -X <username>@<computer> xterm
```

Edit : just realised I forgot the -X in previous posts - apologies

heh, whoops.
Ok now it's working it brought up a terminal.

---

### Post by Peter09 on 2009-05-15
Yes - you are there - the -X allows the system to forward the X commands to you.

You can also try

```
ssh -X <username>@<computer> nautilus
```

---

### Post by Peter09 on 2009-05-15
Using Connect to server uses a slightly different command called scp. You will be able to transfer files with that.

---

### Post by Peter09 on 2009-05-15
To test your router configuration try

```
ssh -X <username>@<your external IP address> xterm
```

---

### Post by ninjapirate89 on 2009-05-15
Thank you very much. One more thing, using this do I have to copy the files over to my computer to use them or can it access them directly? For example can I just open an audio file in vlc and have it stream or do I have to copy it to my laptop first?

Edit -> This is weird. I just noticed that the wallpaper on my laptop changed to the one from my desktop by itself. Is it supposed to do that?

---

### Post by Peter09 on 2009-05-15
I don't know - but I am guessing that it would be best to copy. I think it would likely play on your home machines audio, but never tried it. Experiment. There are applications like NXfree which run on top of ssh which would do that. 

Note two things:

Your home machine needs a static IP else if it changes the router set up is wrong and you need to have a fixed external IP so that you can make an external connection.

---

### Post by Peter09 on 2009-05-15
Wallpaper - never seen that - are you sure you did not transfer it somehow? Spooky;)

---

### Post by ninjapirate89 on 2009-05-15
Sorry to bother again but I can't figure out how I can copy files. I can't just copy them from the terminal because that terminal has no connection to my laptop. I also tried opening nautilus through the ssh and also opening nautilus on my laptop to just copy from one location to the other and that didn't work. Any ideas? 

Edit -> Sorry if that ^ sounds confusing.

---

### Post by Peter09 on 2009-05-15
There is a command line from a terminal call scp, however the easiest way is to do is is  to go to

Places->Connect to Server

select ssh and fill in the server and user name fields. Once the window opens you can navigate to the directory you want and then drag and drop files onto your desktop.

---

### Post by ninjapirate89 on 2009-05-15
HA! IT WORKS!!!

Thank you very very much. I could hug you right now if you weren't thousands of miles away. Also I just found that doing it that way I can play music without copying it first.

---

### Post by Peter09 on 2009-05-15
Great - enjoy - have a good day.

---

