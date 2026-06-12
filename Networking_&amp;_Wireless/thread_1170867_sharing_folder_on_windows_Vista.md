---
title: "sharing folder on windows Vista"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by filjoa on 2009-05-26
Hi

I'll like have one folder on my ubunto where I can acess from oders systems like windows Vista and have all permitions, but I don't have sucess.

I think have some problems with samba, but I don't know how I can correct them, someone can help me?

[[IMG]http://img38.imageshack.us/img38/8828/linuxd.th.jpg[/IMG]]("http://img38.imageshack.us/my.php?image=linuxd.jpg")

[[IMG]http://img34.imageshack.us/img34/3391/winc.th.jpg[/IMG]]("http://img34.imageshack.us/my.php?image=winc.jpg")

PS: my login on ubunto is filjoaserver

kind regards

---

### Post by dmizer on 2009-05-26
Are you using Jaunty? If so, please run this command:
```
sudo ufw disable
```
And see if you are able to browse to the share from Vista then.

---

### Post by filjoa on 2009-05-27
Hi

thanks is this the problem.

but appear this "Firewall stopped and disabled on system startup" don't have problem firewall stay disable?

kind regards.

---

### Post by dmizer on 2009-05-27
> **filjoa said:**
> Hi

thanks is this the problem.

but appear this "Firewall stopped and disabled on system startup" don't have problem firewall stay disable?

kind regards.

Do you have a router?

---

### Post by filjoa on 2009-05-27
yes

and firewall stay enable on router... don't need this firewall for more security? because this is an server and stay 24h a day on.

---

### Post by Boondoklife on 2009-05-27
> **filjoa said:**
> yes

and firewall stay enable on router... don't need this firewall for more security? because this is an server and stay 24h a day on.

If both boxes are on the same side of the router, which I would assume so, then the firewall on the router is not an issue. Could you please post the smb.conf file that you are using on the ubuntu box?

---

### Post by dmizer on 2009-05-27
> **filjoa said:**
> and firewall stay enable on router... don't need this firewall for more security?

No. Even if you have web traffic routed to your server, you should still be ok.

---

