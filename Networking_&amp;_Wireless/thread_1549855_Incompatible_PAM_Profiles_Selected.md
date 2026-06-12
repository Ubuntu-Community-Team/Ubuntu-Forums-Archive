---
title: "Incompatible PAM Profiles Selected"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by Aydos on 2010-08-10
Hello All,

I am a new Linux user and I am running Ubuntu 10.04. I work at the IT dept for a private school that runs all Microsoft stuff, but I wanted to learn Linux. I think it seems useful down the road in my career field since I want to get further into networking.

I have installed Linux and set my machine up the way I like it, but now I am trying to get connected to my domain at work and to my active directory account. I ran and installed Likewise-Open, but I get the following error after installation which results in an authentication failure when I try to log in. I ran all the tests from the site and it is seeing the domain and my computer shows up in AD, but something with PAM is stopping me. Like I said I am new to this. I posted on the likewise forums as well, but they are not always as fast to get back to you as most of the community here.

Here is a copy of my post from the likewise forums.

[I]Hello I am trying to install Likewise Open at work on an Ubuntu 10.04 machine. I am using the .deb installer from the downloads section here to install Likewise Open. 
I am fairly new to Linux so this might be something basic, but after research I hit a road block.

The computer shows up on in AD on our Server 2003 server, but I received the following error after installation and I get an authentication fails error when trying to sign in.

“Incompatable PAM profiles selected.

The follwoing PAM profiles cannot be used together:

Likewise, Winbind NT/Active Directory authentication.

Please select a different set of modules to enable.”

Any help would be appreciated, because I really want to start learning Linux in my work environment.

Thank you.[/I]

---

### Post by Aydos on 2010-08-10
Reviving from the 2nd page in dire need to connect to the domain here at work :)

---

### Post by Aydos on 2010-08-10
Am I really the only one with this problem?

I have tried 3 distros on this laptop on 2 different domains with the same problem.

I hope someone has a solution.

---

### Post by ElwinB on 2010-08-13
There appears to be a better alternative per [http://www.workswithu.com/2010/07/23/active-directory-integration-centrify-express-vs-likewise/](http://www.workswithu.com/2010/07/23/active-directory-integration-centrify-express-vs-likewise/) called Centrify Express ([http://www.centrify.com/express](http://www.centrify.com/express)) that you might want to check out if you still can't get it to work. 
 
E

---

### Post by Aydos on 2010-08-13
Thank you so much for this. I am going to download it and try it.

However, I did resolve my issue with the Incompatible PAM profiles from earlier and join to the AD Domain with Likewise.

Apparently you cannot have Likewise and Winbinds installed at the same time and I had installed WINE prior to Likewise, so I uninstalled Winbinds and the problem was solved.

I do want to see how well this other software works though.

This is a good post for future cases.

---

