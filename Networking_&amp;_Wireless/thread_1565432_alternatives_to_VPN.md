---
title: "alternatives to VPN?"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by itscrawford on 2010-08-31
hi all

i'm trying to crate a VPN like connection between my Ubuntu desktop and  my apple laptop.

i require a serves that allows me to reed and right to my home folders and media devises and get around local fire walls and network monitoring tools.

i have already have a FTP server set up.

i have looked into VPN a lot but i find it complex and a lil overkill for a single user.

any suggestions of a good alternative to VPN for a single user system?

thx , i have just change to Ubuntu from PcLinuxOS so bare with me as i get use to the little changes

---

### Post by BkkBonanza on 2010-09-01
By far the best and easiest method is to use SSH as it is usually already installed.

Whichever system you want to access has to be running ssh server (sshd). Usually that is a simple package install but I'm not sure of the steps on Apple.

From Nautilus in Ubuntu is supports ssh already. You just give it a path with user@machine:/path/to/files and it will use ssh to connect and let you browse the files.

There are various other ways to use ssh as proxy and tunnels but the exact commands depend on what you want to do. It's very powerful.

Using ssh -D (SOCKS proxy) is quite similar to a VPN and has some advantages too. Easier to config, and IMO better security.

---

### Post by scorp123 on 2010-09-01
> **BkkBonaza said:**
>  Usually that is a simple package install but I'm not sure of the steps on Apple. Mac OS X has sshd already installed ... you just need to activate it.

***Apple menu (upper left corner) > System Preferences ... > Sharing*** 

... and when you're there put a tick on:

***[x]  Remote Login***

... and adjust the part that says: ***"Allow access for ... "***, e.g. the user supposed to login via SSH must be in that list or else SSH logins will fail. If the user account is missing just hit the "+" icon and add the right account.

That's it. Takes like 5 mouse clicks to activate it.

---

### Post by scorp123 on 2010-09-01
Here is a screenshot ... just tick the "Remote Login" option ... taddaaaa, and ssh logins will be activated.

---

### Post by scorp123 on 2010-09-01
> **itscrawford said:**
>  i'm trying to crate a VPN like connection between my Ubuntu desktop and  my apple laptop.

Remobo comes to my mind again ...
[http://www.remobo.com/](http://www.remobo.com/)

They offer a VPN client for Windows, Mac OS X and Linux. The Linux client was pretty bad a few months ago when I tried it but now it seems they corrected the issues? I did not yet have the time to play with this again but if "ease of use" is high on your list I'd suggest you give this a try?

**_EDIT:_**

I just tried it. 1 x Linux PC in office #1, 1 x Linux PC at home, 1 x MacBook Pro in office #2 ... and it worked tip top. Each system gets a 7.x.x.x IP address and I can easily SSH and SFTP between them, no matter where they are or that there are a truckload of firewalls between me and them.

There is a screenshot from MacOS X showing my other 2 x Linux PC's as "buddies" attached to this message ... take a look.

As I am one of the admins here where I work I can pretty much do what I want when I want ... but if you try this from your workplace I suggest you ask your administrators first, not every admin likes it when and if their users circumvent the company firewalls, so you better ask for permission first, just in case. Using services such as 'Remobo' might easily be interpreted as 'opening backdoors' into the company network ... just to make sure nobody gets into trouble.

But it definitely does work tip top between Linux and Mac OS X with SSH. Other network protocols (e.g. SAMBA?) probably will work too but I didn't test that.

---

### Post by itscrawford on 2010-09-01
hay guys

than x SSH complty slipped my mined and is a excellent idea so i will be moving into deploying it in a few hours :)

in response to asking my admin their is a open wifi avbill where i work  but to reduce traffic there is a lot of firewall but is independent from the organisation closed net work.

i will update as things go along

---

### Post by itscrawford on 2010-09-08
hay every one 

i have tried alot of things with very little succes :(

i think i have bitten off more than i can chew so im gonna put this on the back burner for a whille

---

