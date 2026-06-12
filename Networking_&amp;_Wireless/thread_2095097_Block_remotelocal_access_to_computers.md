---
title: "Block remote/local access to computers?"
date: 2012-12-15
forum: Networking &amp; Wireless
---

### Post by PDA1 on 2012-12-15
Using Places---->Connect to Server I can enter the IP of computers on my home LAN (while at home) and have access to look at those computers and their contents/files and can transfer files back and forth between them.

I'm a concerned that they could get hacked by some computers users from outside my LAN.  

How can I block access to all of my machines so that I can't even access another computer within my house from my main computer?

I already did the following;

sudo apt-get purge openssh-client

sudo apt-get --purge remove openssh-server

But, I can still access the other in-house computers using Remmina Remote Desktop Client.

Any simple solution you'd recommend?

---

### Post by chadk5utc on 2012-12-15
this is rather broad question and opinions will vary but without knowing much about how you have your network setup we can make suggestions.
increase security on your router as much as possible
if you have a server setup and all other computers behind it/going through it you can set firewall rules.
you can setup firewalls on all computers there by restricting access and services.
you removed ssh server but Im not sure why? if setup properly it can be very robust and very useful. What type internet connection are you using? what type router do you have setup? is your network statically set or do you have DHCP enabled?Be sure to use STRONG passwords

---

### Post by PDA1 on 2012-12-15
No idea how to answer any of your questions except that once I learned how to use the Connect to Server I found it way too easy to access the other computers. All I had to do was enter the IP address of the computer, then User name and Password and I was "in".

The reason I deleted OpenSSH was because I thought that was the program giving me all of the access.

I figured if I could access the computers in my house so easily ....then some hacker on the outside world could do it remotely....just as easily.

I'm going through a wireless router, if that's any help, but to answer your questions....I just don't know the answers.

I think there was a way in ubuntu 10.04 to forbid remote access...but don't really remember.

What should I do now?

---

### Post by chadk5utc on 2012-12-15
I understand what your thinking. remember nothing is 100% secure, however if you take certain precautions you can minimize the hazards to some extent.
This is what I would do and have done and I will try to explain it simply as I can.
Secure the router(Strong Password as it will allow) as its usually the first device exposed to the (WAN)internet then keeping it simple within the router only open or forward ports you know that you need. The router acts as kind of a barrier and allows only what you want through it. Typically unless you forward ports through the router they wont be available outside of it.
 I suggest also reading about firewalls either use UFW on command line or you can use Gufw which is the GUI for it. or use iptables These when properly setup can also help minimize possible attacks making it much more difficult. You can also harden ssh to use key based logins and not allow passwords.

 Personally I am more of a server guy I spend 95% of my time on command line the rest with some GUI or another.

---

### Post by chadk5utc on 2012-12-15
there are tons of great resources available within these forums heres a few to get you started
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

