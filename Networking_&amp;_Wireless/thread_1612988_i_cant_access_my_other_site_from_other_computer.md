---
title: "i cant access my other site from other computer"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by maryonmayor on 2010-11-03
hi im running apache2, i have already created a working sites. using virtual name hosting.

but my problem is, i cant access my other sites except my server's localhost from other computer. 

i dont know what seems to be the problem, can you guys point me where to start looking? thanks.

---

### Post by SeijiSensei on 2010-11-03
Have you configured name service for the virtual hosts?  You have to tell the machine with the browser what IP address corresponds to each virtual host.  In your case the IP address will be the same each time.

Do you have one or more domains registered for these hosts?  In the long run, they'll need to be registered in the Domain Name Service.  In the short term you can put entries in the /etc/hosts files on both the server and client to map from virtual hostnames to the shared IP address.

Add an entry in each machines /etc/hosts like this:

```
192.168.101.1     virtual1.example.com virtual2.example.com virtual3.example.com
```

Now any references to one of those hostnames will be pointed to the Apache server at 192.168.101.1.  Because Apache's running named virtual hosting it pays attention to the host name in the URL and picks the corresponding virtual server.

If the client is running Windows, you can find the location of the hosts file [here](http://en.wikipedia.org/wiki/Hosts_%28file%29#Location_in_the_file_system).

---

### Post by maryonmayor on 2010-11-04
here is my hosts file. now when i type amax.local it returns the result of my defaul-site(which is localhost). 

192.168.0.120   amax.local mdp.local
127.0.0.1       localhost
127.0.1.1       maryon-desktop mmayor
127.0.1.4       codeigniter.local
127.0.1.5       amax2.local
127.0.1.6       test.local

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
~                    

i want to access amax.local from other machines from the same network.

---

