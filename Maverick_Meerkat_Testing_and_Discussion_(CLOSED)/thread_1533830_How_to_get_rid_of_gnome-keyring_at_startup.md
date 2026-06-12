---
title: "How to get rid of gnome-keyring at startup"
date: 2010-07-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-07-18
I do not wish to use password login. If i autologin i am still asked to enter gnome-keyring password for internet. Is there a way to disable it? I am using Dell E1505 and Meerkat. I have tried [http://www.noob2geek.com/how-to/how-to-disable-gnome-keyring-in-ubuntu-10-04/](http://www.noob2geek.com/how-to/how-to-disable-gnome-keyring-in-ubuntu-10-04/) I have also tried wicd but it does not pick up hidden network.

Thanks.

---

### Post by VMC on 2010-07-18
This is the one [reference]("http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/") I always refer to, if that's what your referring to.

---

### Post by donniezazen on 2010-07-18
> **VMC said:**
> This is the one [reference]("http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/") I always refer to, if that's what your referring to.

Thanks this is what i was looking for.

---

### Post by Mr. Picklesworth on 2010-07-19
If you just don't want to enter your password, you can remove the keyring password. This makes it unencrypted, of course, but you keep all the other benefits and you won't be bothered when lots of software starts using the keyring in the near future.

Open the Passwords and Encryption Keys preferences (seahorse), and under the Passwords section right click the login keyring. Choose Change Password and leave the new password field blank.

---

### Post by donniezazen on 2010-07-19
> **Mr. Picklesworth said:**
> If you just don't want to enter your password, you can remove the keyring password. This makes it unencrypted, of course, but you keep all the other benefits and you won't be bothered when lots of software starts using the keyring in the near future.

Open the Passwords and Encryption Keys preferences (seahorse), and under the Passwords section right click the login keyring. Choose Change Password and leave the new password field blank.

Thanks. So according to above post the whole keyring is turned off and according to you suggestion only keyring login password will be disabled.

---

### Post by cariboo on 2010-07-19
The reason the keyring ask you for a password, is because you use auto-login, if you create a blank password, the keyring still runs, and your private keys are still available. 

The only problem with that is, that someone that knows what they are doing, can change your keyring password to something they only know, then your keys are useless.

---

### Post by ranch hand on 2010-07-19
> **Chauncellor said:**
> Are there any plans in the future to play nice with autologin?
What you are doing is opening a vast hole in your security.  If, by "playing nice with auto login" is to do something similar, I certainly hope not.

Just because the most insecure OS in the world does it that way does not mean it is a good idea.

Try using a password login and you will not have this problem or a security hole.  It doesn't hurt a bit.

---

### Post by donniezazen on 2010-07-20
> **ranch hand said:**
> What you are doing is opening a vast hole in your security.  If, by "playing nice with auto login" is to do something similar, I certainly hope not.

Just because the most insecure OS in the world does it that way does not mean it is a good idea.

Try using a password login and you will not have this problem or a security hole.  It doesn't hurt a bit.

My system is physically secure so i do not want to have passwords. I want my system to be secure from online attacks. If i have auto login and no gnome-keyring for getting through wifi, does that make my system prone to online/software attacks?

---

### Post by ranch hand on 2010-07-20
Of coarse it does.  It opens all your files to anyone or any thing that can get access to them and that includes things like auto installers.

Admittedly there are probably not a lot of Linux auto installers prowling the internet.  With out a password you may as well just log in as root because that is pretty much what you are setting up.

---

### Post by donniezazen on 2010-07-20
> **ranch hand said:**
> Of coarse it does.  It opens all your files to anyone or any thing that can get access to them and that includes things like auto installers.

Admittedly there are probably not a lot of Linux auto installers prowling the internet.  With out a password you may as well just log in as root because that is pretty much what you are setting up.

I only require that i do not have to enter password when i login. If it works in a way that you auto login and whole system is open then its a major security flaw. It should always require password when attempting to install some software.

---

### Post by ranch hand on 2010-07-20
Yup, that is where it gets dicey.   The way it is set up, even with the somewhat limited permissions you have with sudo, the way you are setting up with no keyring password leaves you pretty much in a sudo permissions position at all times.

This really is not secure.

I,personally, do not like auto login.  If you have to give a password to enter your keyring I would do that.  For your network connection that sounds a little silly to me too.

I would be looking at just changing that by it self if that is possible.  I know that in your System>Administration>Users and Groups you can set the permissions on users.  One of those is the ability to connect.   This may make it tough to get that enabled with an auto login because the system does not really know who you are until you log in.

One of the reasons for protecting the network in this manner is limiting the ability of an out side party getting remote access to your box so it really does make sense.

There should be a way to get around that if it really bothers you though.  I have no idea what it is but I would be looking really hard at the possibilities in System>Preferences>Startup Applications.  You can add things there and it might be possible to add "sudo <whatever hooks you up>.  You may still have to enter a password though as that is not a protected set up tool.

---

### Post by Mr. Picklesworth on 2010-07-20
> **ranch hand said:**
> Yup, that is where it gets dicey.   The way it is set up, even with the somewhat limited permissions you have with sudo, the way you are setting up with no keyring password leaves you pretty much in a sudo permissions position at all times.

The keyring is an (usually) encrypted store for your own personal passwords and secret keys, such as for networks, VPNs and user accounts on web sites. It is quite different, and entirely detached from, sudo and PolicyKit (which are about authenticating as a given user on the current machine).

Of course, by not having a password for your keyring it isn't encrypted in any meaningful way. However, the passwords being provided definitely have no technical connection with gaining admin rights on a machine. (Except for that natural possibility that most people use the same password in many different places).

Auto-login doesn't, either. sudo has a grace period, but logging in does not trigger it.

Having said that, you are at this point open for a knowledgeable / determined / quick-learning attacker who is physically present (or otherwise is logged in as you and can access ~/.gnome2/keyrings) to rather easily gain access to your stored passwords and your personal information. Everyone has a different opinion on whether that one is worth being concerned about :)

---

### Post by ELD on 2010-07-20
Seems ranch hand has been getting a little confused between the keyring for your general passwords and the actual main sudo passwords and such :P

---

