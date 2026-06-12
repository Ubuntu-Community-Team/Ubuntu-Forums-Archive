---
title: "Autoconnect OpenVPN client (GUI) THEN afterwards run a script (as root)"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by riahc3 on 2013-03-04
Hello

I have the OpenVPN client installed with the GUI thats next to the clock where you right click on the network connections, it appears, and you connect to the VPN. Now, I want that after I do that and the connection is successful to run a script Ive made as root. How can I configure this?

Thank you

---

### Post by riahc3 on 2013-03-05
Someone has had to do this one time at least...

---

### Post by Whoopie on 2013-03-05
Search for NetworkManager dispatcher script.

---

### Post by riahc3 on 2013-03-05
> **Whoopie said:**
> Search for NetworkManager dispatcher script.

Found this:

[https://wiki.archlinux.org/index.php/NetworkManager#Network_services_with_NetworkManager_dispatcher](https://wiki.archlinux.org/index.php/NetworkManager#Network_services_with_NetworkManager_dispatcher)

So now do I put a script in there and thats it? Or should I do something else?

---

### Post by riahc3 on 2013-03-05
Ok Im getting somewhere....
 
When I throw a script inside there Im running something like this:
 
#!/bin/sh
 interface=$1 status=$2
 case $status in
 up)
 echo hi 
;;
 down)

 ;;
 esac
 

Before that case, Im going to do a "if" that searches for the name of my vpn which I would get using
 
nmcli con status
 
Lets say my vpn is called "helloworld"
 
How would I do a (pseudocode):
 
If in nmcli con status I find the text "helloworld" do
 actions
 end if
 
In a shell script?

---

### Post by riahc3 on 2013-03-06
Again, I find it hard to believe that noone has even thought of trying something like this...

---

### Post by Whoopie on 2013-03-06
> **riahc3 said:**
> Again, I find it hard to believe that noone has even thought of trying something like this...

I find it hard that you're not able to use a search engine. I gave you some hints, now it's up to you to find something appropriate.

---

### Post by riahc3 on 2013-03-06
> **Whoopie said:**
> I find it hard that you're not able to use a search engine. I gave you some hints, now it's up to you to find something appropriate.

Then I sincerarly apoligize for not being able to find it. Ive used search engines and other sites to no avail.

Could you point out some additional information?

Thank you Whoopie.

---

### Post by riahc3 on 2013-03-11
I simply do not find information on how to do this.........maybe I am not using the correct search terms

---

