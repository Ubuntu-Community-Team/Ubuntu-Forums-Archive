---
title: "Firefox ---killing me softly"
date: 2012-02-21
forum: Networking &amp; Wireless
---

### Post by 3v3rgr33n on 2012-02-21
Hi

Im a Natty Narwhall user, im having a terrible experience with firefox. I cnt connect to the internet because the following window doesnt pop-up ( [http://www.mediafire.com/i/?qg16k2hstt4pobg](http://www.mediafire.com/i/?qg16k2hstt4pobg) ). I have a wireless connection but can only access the intranet coz' it dazn gv me the option giving it my login details 

Thnx  ](*,)

---

### Post by elliotbeken on 2012-02-21
I had this problem before i tried doing 

Ctrl + F5

Hope this helps

---

### Post by Perkins on 2012-02-21
It looks like your internet connection goes through a proxy.  If that is the case, you should be able to configure the proxy, including the authentication credentials, in System->Preferences->Network Proxy.

---

### Post by 3v3rgr33n on 2012-02-22
> **Perkins said:**
> It looks like your internet connection goes through a proxy.  If that is the case, you should be able to configure the proxy, including the authentication credentials, in System->Preferences->Network Proxy.
  You are a life saver dude!!

>   	 		**Re: Firefox ---killing me softly**
 		I had this problem before i tried doing 

Ctrl + F5

Hope this helps 	
Ctrl+F5 doesnt do anything on the other hand

---

### Post by Perkins on 2012-02-22
No problem.  If you have other programs that don't follow the system settings, and don't have their own proxy settings, the program proxychains out of the repository will intercept TCP communication and force it through the proxy, essentially allowing you to use just about any program with your internet connection.  :)

---

