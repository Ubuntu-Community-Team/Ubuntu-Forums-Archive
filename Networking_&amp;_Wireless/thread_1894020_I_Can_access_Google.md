---
title: "I Can access Google"
date: 2011-12-11
forum: Networking &amp; Wireless
---

### Post by NBPX on 2011-12-11
When I try to search something in Google I get a page with the following mensage:

> Not Found


The requested URL /search was not found on this server.

Apache/2.2.3 (CentOS) Server at [www.google.com.br](www.google.com.br) Port 80

Details:
-I'm using Kubuntu 11.10.
-I can access other websites
-I can access Google websites in Windows Seven.

Update: When I try to access Google.com.br (brazilan Google webpage) I get the following mensage:
> Atualização obrigatória, caso não inicie automaticamente clique aqui
Meaning:
> Mandatory upgrade, if does not start automatically click here.


The link above is this: [http://google.com.br/Google_Update.exe](http://google.com.br/Google_Update.exe)

Update 2: It look like that I can acess Youtube, Android Market and whatever that is related with Google.

---

### Post by BC59 on 2011-12-11
Try opening Google through its ip : [http://208.69.34.230/](http://208.69.34.230/)

---

### Post by BC59 on 2011-12-11
You have to edit your hosts file and delete any entries like this:

```
O1 - Hosts: 213.175.216.204 google.com www.google.com
O1 - Hosts: 213.175.216.205 mail.google.com
```

The guide how to do it is here:

[http://www.howtogeek.com/howto/27350/beginner-geek-how-to-edit-your-hosts-file/](http://www.howtogeek.com/howto/27350/beginner-geek-how-to-edit-your-hosts-file/)

---

### Post by NBPX on 2011-12-11
> **BC59 said:**
> Try opening Google through its ip : [http://208.69.34.230/](http://208.69.34.230/)

Nothing happens...

Only loading and loading...

---

### Post by NBPX on 2011-12-11
> **BC59 said:**
> You have to edit your hosts file and delete any entries like this:

```
O1 - Hosts: 213.175.216.204 google.com www.google.com
O1 - Hosts: 213.175.216.205 mail.google.com
```

The guide how to do it is here:

[http://www.howtogeek.com/howto/27350/beginner-geek-how-to-edit-your-hosts-file/](http://www.howtogeek.com/howto/27350/beginner-geek-how-to-edit-your-hosts-file/)


You refer to the etc/hosts file? There is no such entries there.

---

### Post by NBPX on 2011-12-11
It's working now! What happened?

---

### Post by BC59 on 2011-12-11
Your hosts file was hijacked by a malware or something like that.

---

### Post by NBPX on 2011-12-11
> **BC59 said:**
> Your hosts file was hijacked by a malware or something like that.

But Linux is not secure?

How can I evaluate the damage that this malware has caused me and how can I find the source of it?

How can I prevent this from happening again and how do I know that there is no more malware on my PC?

---

### Post by BC59 on 2011-12-11
Actually this is a problem of the Internet Browser. Malware uses the browser as troyan horse. Usually in Linux is sufficient using an advertisement blocker, like the adblock. adblock is an extension for Firefox and Chrome. You should install it, to stop the annoying ads and to protect your computer. The malware installed, was not able to harm you or your computer, only was trying to redirect you to a certain website.

---

### Post by sammiev on 2011-12-11
If you are using FF then try the extension Redirect Remover.

---

### Post by NBPX on 2011-12-11
Ok, thanks guys!

> **BC59 said:**
> Usually in Linux is sufficient using an advertisement blocker, like the adblock. adblock is an extension for Firefox and Chrome. You should install it, to stop the annoying ads and to protect your computer. The malware installed, was not able to harm you or your computer, only was trying to redirect you to a certain website.


You are talking abou AdBlock or AdBlock Plus? Both more than 1.000.000 of users. I think they are both reliable.

---

### Post by BC59 on 2011-12-12
> **NBPX said:**
> Ok, thanks guys!




You are talking abou AdBlock or AdBlock Plus? Both more than 1.000.000 of users. I think they are both reliable.

Adblock is a little better.

---

