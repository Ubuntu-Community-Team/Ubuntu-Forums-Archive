---
title: "Connecting Ubuntu to my corporate network"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by pierolinux on 2010-01-05
Hi there,
    I work for a big corporation and here we use windows. I have partitioned my laptop to use linux when I need it, but of course when I am logged in Ubuntu I cannot access the corporate network: services, email, internet.

I was wondering if there is a way to join my linux to the rest of the network. I do not have certificates and/or a user profile, but I think I can use the ones I have when I'm logged in windows (I have administrator rights).

Questions:
- Since I have completely no access to the remote servers and I want to use my windows user... Is the above possible at all?
- If yes, how and where do I find my user information in windows? (especially the authentication certificates) and how do I reuse/import them in ubuntu?
- What program would you recommend to authenticate my Ubuntu to the network? (I heard Likewise is good... what do you think?)

[Disclaimer]: Suggestions like: "please use Cygwin" or "Get yourself VMWare" would not do the job, since I am doing this partly to learn something new... :P

Thank you in advance for your help

---

### Post by shairozan on 2010-01-05
Hey there, 

This all depends on what your administrator has setup in the active directory. It can be customized to allow for network login and access, but generally is not the case. In the case where your network doesn't actively support using Linux, you'll want to try to setup your connections separately, and some of them just plain might not work. 

The first is email. I assume since you said you cannot connect because it is a Microsoft Exchange account. Evolution supports this setup, but you will require some information including the OWA URL which can be provided by your network adminsitrator. 

Regarding your certificate, the easiest thing to do will be to ask your admin for the cert. You can't find it in the list without knowing what your domain is and then what server performs the signing. 

Your username will be the same one you login to windows with and your password will be the same. You can still access network shares, etc by using that username and password. For example, if your domain is abbreviated by egl, username is bob and pass is bobpassword, then you would do the following to connect to a machine:

(1) Click Places
(2) Click Connect to server
(3) Select "Windows Share" as service type
(4) Insert the name or IP of the destination machine in the server field
(5) Insert the name of the folder you want to access on the remote machine
(6) Enter bob in username
(7) Enter egl in domain
(8) Once you hit OK, it will prompt you for the password. Enter it, in this test case it would be bobpassword. This will allow you access to that directory. 

There are a myriad of other ways to achieve the above 8 steps, including auto-mounting important directories, but that involves playing with fstab. The best resource you have for this is your IT staff, as they are the ones who define the policies for access and know all of the details you require.

---

