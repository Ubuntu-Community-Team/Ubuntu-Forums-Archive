---
title: "how to ssh into xxx.xxx.x.xx?"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by Euboon2 on 2010-11-29
i have no problem ssh into a computer with ip addresses of the form "xxx.xxx.xxx.(2 or 3 digits)".

But whenever a computer has ip of the form "xxx.xxx.x.(whatever)", i can't connect to it. Sometimes i have to ask someone on the other end to restart the computer in the hope that the ISP would happen to assign the xxx.xxx.xxx.sth form then ssh works.

Is there any tricks to overcome this?

thanks

---

### Post by Yarui on 2010-11-29
The easiest solution is to just connect to xxx.xxx.00x.0xx

If you add 0s to the front of any of the numbers that are under 3 digits so that they are 3 digits, it's still the same IP address.  If you want to connect to your home router try using 192.168.000.001 or 192.168.001.001, instead of using 192.168.0.1 or 192.168.1.1, you will find that it takes you to the same place.

Edit:  What you are describing isn't normal, by the way.  I can use ssh to access my server on my home network at an address that is in 192.168.0.x,  what ssh software are you using?

---

### Post by Euboon2 on 2010-11-29
Thanks for your suggestion. I currently used debian and ubuntu. Very often that particular computer that I mentioned gave an ip of the form xxx.xxx.x.xxx (from "what is my ip" website). i tried xxx.xxx.00x.xxx in the past but didn't managed to log in. I will give it another try some other day when that computer is up (in case my memory fails me and i didnt sth different).

Thanks

Edit: I ssh from terminal using the default ubuntu/debian installation

---

### Post by Yarui on 2010-11-29
I assume the default ssh client installed with Ubuntu is openSSH.  I don't remember whether I had to install openSSH after I installed Ubuntu or if it was the default.  Just to be safe though, it may be a good idea to attempt to install it.

```
sudo apt-get install openssh-client
```

If you already have it installed, it will just say that 0 files were downloaded and installed, so no harm done.  You can use the following command to connect to an ssh server.

```
ssh 192.168.0.1
```

Replacing the IP with whatever IP you are trying to connect to, of course.  I'm sure you already know this command, I just figure it would be best to say this stuff now just in case.  We don't want to spend days trying to figure out what is going on only to find out you just needed to use a different command.

If you have openSSH installed and you use this command, you should be able to connect to any server.  There may be something weird going on at your end, but most likely if this doesn't work there is something strange going on with the server.  People who run servers almost always want to tell you it's on your end, because things work on their own systems, but it's not uncommon for it to actually be a server issue.

The default SSH port is 22, so it would be a good idea to make sure the server isn't running on a different port.  If, for instance, you were trying to connect to the IP 192.168.0.1 on port 23 you would have to use the following command.

```
ssh 192.168.0.1:23
```

The person running the server also needs to make sure the router ports are forwarded properly so that traffic on the SSH port will be directed to the SSH server, rather than just stopping at the router.  If your friend has been able to successfully connect to his own server, it could just be because he is connecting through his local network and the server isn't yet accessible to the outside world.

---

### Post by wojox on 2010-11-29
Is this Lan or Wan?

---

### Post by Euboon2 on 2010-11-30
Thanks everyone for the responses. I have been using ssh for past two years, but have not had such problems as I usually ssh into my office computer which always has ip of the format xxx.xxx.xxx.xxx

It's only when I need to ssh into someone's computer (oversea) whose ISP assigns a random ip each time the computer restarts.

Not sure about wan or lan.

Anyway that computer has an i7 processor and has ubuntu 10.04 installed with kernel 2.6.35 and has been running fine until a recent update screwed up the pleasant experience. From then on it crashed very often, maybe the updated programs were incompatible with the kernel. Eventually, the recovery option is taken to wipe out ubuntu and restore back to factory condition. I have not find the opportunity to test whether the .00x. works. 

It's unfortunate that linux does not seem to handle i7 QM hardware well even after a year. As could be guessed from the above, the ssh problem is no longer an issue since there's no need to ssh into that computer again.

Thanks nevertheless.

---

