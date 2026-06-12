---
title: "How do I open an incoming TCP port?"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by neilevan814 on 2009-08-10
I am using the Vuze torrent and I have all yellow lights for my downloads.  Things are downloading and uploading but it says to hav e full access to the internet the incoming TCP port should be opened.  I do not know how to do this.  Can someone help?

---

### Post by dmizer on 2009-08-10
This will probably need to be done on the router: [http://portforward.com/](http://portforward.com/)

---

### Post by neilevan814 on 2009-08-10
Yeah, I went there....and did go to my admin page for my router and open the required port.  The yellow lights turned green for a minute or so and now they are yellow again...what could possibly be happening does some other daaemon or something have control over opening and closing ports?

---

### Post by dmizer on 2009-08-10
Please post the output of:
```
sudo iptables -L
```

---

### Post by neilevan814 on 2009-08-10
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by neilevan814 on 2009-08-10
The lights are green on some things now and yellow on others....It is very strange behavior...Not that it is affecting the performance of Vuze for my purposes, BUT I just wanted to KNOW why this is happening....

---

### Post by dmizer on 2009-08-10
Are you on a DHCP network, and are you sure you have the ports forwarded to the right IP address? Also you should be using Sun java with Vuze. Please post the output of:
```
sudo update-java-alternatives -l
```

---

